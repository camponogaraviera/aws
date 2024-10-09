<div align='center'>
  <h1>Hosting on AWS</h1>
</div>

# Amazon S3

Suitable for static websites with no server-side scripting, only client-side. However, it requires the S3 bucket to be publicly readable (not recommended). It does not provide SSL/TLS certificate for endpoints (HTTPS).

# AWS Amplify Console

Suitable for connecting the frontend of static websites (Angular, ReactJS, Next.js, or Vue.js/Nuxt.js) and mobile applications (kotlin, swift, flutter, react-native) with the backend. Provides SSL/TLS certificate (HTTPS).

# Amazon EC2

Enterprise level for systems that will likely scale with multiple web servers.
