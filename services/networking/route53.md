<div align='center'>
  <h1> 3. Networking </h1>
  <h2> Amazon Route 53 (DNS) </h2>
</div>

# Table of Contents

- [Amazon Route 53](#route-53)
- [Registry vs Registrar](#registry-vs-registrar)

# [Amazon Route 53](https://aws.amazon.com/route53/)

Amazon Route 53 can be used to register a new `domain name`.


# Registry vs Registrar

- Domain Name Registry: Manages top-level domains (gTLDs or ccTLD).
  - Verisign for `.com` generic TLD (gTLD).
  - Nic.br for `.br` country-code TLD (ccTLD).

- Domain Name Registrar: Interface with users to register domain names on their behalf with the registry.
  - [Registro.br](https://registro.br/) is both a domain registrar and the registry operator.
  - [Amazon Route 53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/domain-register.html) is a domain registrar and DNS provider.
  - [Cloudflare](https://www.cloudflare.com/) is a domain registrar and DNS provider.