private void storeTransaction(double amount, String type) {
    String userId = mAuth.getCurrentUser().getUid();
    String transactionId = db.collection("users").document(userId).collection("transactions").document().getId();
    
    Map<String, Object> transaction = new HashMap<>();
    transaction.put("type", type);  // "credit" or "debit"
    transaction.put("amount", amount);
    transaction.put("timestamp", FieldValue.serverTimestamp());

    db.collection("users").document(userId)
        .collection("transactions")
        .document(transactionId)
        .set(transaction)
        .addOnSuccessListener(aVoid -> {
            Toast.makeText(WalletActivity.this, "Transaction recorded.", Toast.LENGTH_SHORT).show();
        })
        .addOnFailureListener(e -> {
            Toast.makeText(WalletActivity.this, "Failed to record transaction.", Toast.LENGTH_SHORT).show();
        });
}