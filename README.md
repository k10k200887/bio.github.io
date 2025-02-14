@Override
public void onPaymentSuccess(String razorpayPaymentId) {
    // Handle successful payment and update the balance
    Toast.makeText(WalletActivity.this, "Payment Successful", Toast.LENGTH_SHORT).show();
}

@Override
public void onPaymentError(int code, String response) {
    // Handle payment failure
    Toast.makeText(WalletActivity.this, "Payment Failed", Toast.LENGTH_SHORT).show();
}