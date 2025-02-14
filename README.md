private void viewTransactions() {
    String userId = mAuth.getCurrentUser().getUid();

    db.collection("users").document(userId)
        .collection("transactions")
        .orderBy("timestamp", Query.Direction.DESCENDING)
        .get()
        .addOnSuccessListener(queryDocumentSnapshots -> {
            List<String> transactionHistory = new ArrayList<>();
            for (DocumentSnapshot document : queryDocumentSnapshots) {
                String type = document.getString("type");
                double amount = document.getDouble("amount");
                Timestamp timestamp = document.getTimestamp("timestamp");
                transactionHistory.add(type + ": ₹" + amount + " on " + timestamp.toDate().toString());
            }
            // Display the transactions in a RecyclerView or ListView
            updateTransactionUI(transactionHistory);
        })
        .addOnFailureListener(e -> {
            Toast.makeText(WalletActivity.this, "Failed to load transactions.", Toast.LENGTH_SHORT).show();
        });
}

private void updateTransactionUI(List<String> transactionHistory) {
    // Update the UI with the list of transactions
    // For example, set it in a RecyclerView or ListView
}