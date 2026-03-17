<div align='center'>
  <h1> Backend & APIs </h1>
  <h2> When to Use a Backend? </h2>
</div>

# Table of Contents

- [No Backend Required](#no-backend-required)
- [Backend Required](#backend-required)

# No Backend Required

If the app is static (e.g., HTML/CSS/JavaScript) and runs entirely on the client side. Static files can be stored on **AWS S3** and served via **CloudFront**, or hosted (stored + served) via **AWS Amplify**.

The frontend code can directly consume third-party APIs (e.g., Stripe, Google Maps) and remain static (no backend).

# Backend Required

If the app needs server-side logic or stateful processing.

Examples:
- Saving and fetching user data (credit card information, shopping orders, invoices) from a database you control.
- Serving protected content (auth, role-based access).
- Running business logic that cannot be safely executed on the client.
