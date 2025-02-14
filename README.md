private void updateUserProfile(String name, String phoneNumber) {
    String userId = mAuth.getCurrentUser().getUid();
    Map<String, Object> userProfile = new HashMap<>();
    userProfile.put("name", name);
    userProfile.put("phoneNumber", phoneNumber);

    db.collection("users").document(userId)
        .update(userProfile)
        .addOnSuccessListener(aVoid -> {
            Toast.makeText(WalletActivity.this, "Profile updated successfully.", Toast.LENGTH_SHORT).show();
        })
        .addOnFailureListener(e -> {
            Toast.makeText(WalletActivity.this, "Failed to update profile.", Toast.LENGTH_SHORT).show();
        });
}