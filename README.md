import com.razorpay.Checkout;
import org.json.JSONObject;

private void initiatePayment(double amount) {
    Checkout checkout = new Checkout();
    checkout.setKeyID("YOUR_RAZORPAY_KEY");

    try {
        JSONObject options = new JSONObject();
        options.put("name", "Your App Name");
        options.put("description", "Payment for transaction");
        options.put("image", "https://example.com/your_logo.png");
        options.put("amount", amount * 100);  // Amount in paise (cents)
        options.put("currency", "INR");

        checkout.open(WalletActivity.this, options);
    } catch (Exception e) {
        e.printStackTrace();
    }
}