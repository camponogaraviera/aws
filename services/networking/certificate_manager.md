<div align='center'>
  <h1> 3. Networking </h1>
  <h2> AWS Certificate Manager (SSL/TLS) </h2>
</div>

# Table of Contents

- [About](#about)
- [Installing an SSL/TLS certificate](#installing-an-ssl-tls-certificate)

---

# About

Use [AWS Certificate Manager (ACM)](https://aws.amazon.com/certificate-manager/) to provision, manage, and deploy public and private SSL/TLS certificates.

Note: HTTPS relies on the TLS protocol (previously on SSL, which is now deprecated) to establish encrypted communication between the client and the server.

- Public Certificate: This certificate is issued by Amazon's public certificate authority (CA) and is recognized by browsers, making it the standard choice for securing public-facing websites. Public certificates issued by AWS ACM are intended for use exclusively with AWS services (CloudFront, Elastic Load Balancing, and API Gateway). ACM does not provide access or allow exporting the private key of publicly trusted certificates. However, you can export the public certificate and its certificate chain (the root and intermediate CAs) using the `GetCertificate API`. Public certificates are free.

- Private Certificate: This option is for internal or private applications where you control the trust settings (e.g., within a corporate network), and it requires setting up a private certificate authority. These certificates are typically not recognized by browsers for public websites and wouldn't automatically show the padlock icon next to the domain name of your website. Private certificates are paid.

# Installing an SSL/TLS certificate

To install an SSL/TLS certificate on a server or third-party provider, the following files are needed:

1. `certificate.crt`: This is your actual SSL certificate issued specifically for your domain.
2. `ca_bundle.crt (certificate chain)`: This is the certificate chain that links your SSL certificate to a trusted root authority. It usually contains one or more intermediate certificates.
3. `private.key`: This is the private key associated with your SSL certificate. Keep this file secure, as it is used to establish a secure connection.

To acquire these files, you should obtain a public SSL certificate from an external certificate authority (CA) that allows you to download both the certificate and private key. Some popular CA options include:

- [Let's Encrypt](https://letsencrypt.org/getting-started/), [SSL For Free](https://www.sslforfree.com), `ZeroSSL`, `Sectigo`, or other paid providers.
- PS: CNAME records (name and value) are typically used for domain verification via DNS validation, and they are not included in the certificate export (not part of the certificate itself).
