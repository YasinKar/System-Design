# Chapter 07 - System security

## Authentication & Authorization
Authentication and authorization are crucial for verifying user identities and ensuring they have appropriate access.

### Authentication (Who are you?)
Authentication ensures that the user is who they claim to be.

#### **Common Authentication ‌Methods**
- **OAuth (Open Authorization):** A protocol that allows secure API authorization without exposing credentials. Commonly used for social logins (e.g., "Login with Google").
- **JWT (JSON Web Token):** A compact, self-contained token used for secure information exchange. It's widely used in stateless authentication (e.g., token-based authentication).
- **SSO (Single Sign-On):** Allows users to log in once and access multiple applications without needing to authenticate again (e.g., Google SSO for multiple services).
- **Multi-Factor Authentication (MFA):** Adds extra layers of security beyond passwords, such as OTPs, biometric verification, or security keys.

### Authorization (What are you allowed to do?)
Once authenticated, authorization ensures users have the correct permissions to access specific resources.

#### **Common Authorization ‌Methods**
- **Role-Based Access Control (RBAC):** Users are assigned roles, and roles determine what actions they can perform.
- **Attribute-Based Access Control (ABAC):** Access control is based on attributes such as user role, device type, or location.
- **OAuth Scopes:** Defines specific permissions that applications can request (e.g., "read-only" access to a user’s profile).

## Encryption
Encryption ensures that data remains secure both in transit and at rest.

### Encryption in Transit
- **TLS (Transport Layer Security):** Encrypts data sent between clients and servers. Successor to SSL.
- **HTTPS (HyperText Transfer Protocol Secure):** A secure version of HTTP that encrypts data using TLS to prevent eavesdropping and tampering.

### Encryption at Rest
- **Database Encryptionf:** Encrypts stored data to prevent unauthorized access (e.g., AES-256 encryption in databases).
- **Disk Encryption:** Protects entire storage devices using encryption techniques like BitLocker (Windows) or FileVault (Mac).
  
### End-to-End Encryption (E2EE)
- Ensures that only the sender and recipient can read messages (e.g., WhatsApp, Signal).
- Uses public-private key cryptography (e.g., RSA, ECC).

## Common Vulnerabilities

### SQL Injection (SQLi)
Attackers inject malicious SQL queries to manipulate databases.
**Prevention:** Use prepared statements and ORM frameworks to prevent direct SQL execution.

###  Cross-Site Scripting (XSS)
Attackers inject malicious scripts into web pages, allowing them to steal user data.
**Prevention:** Sanitize user inputs and use Content Security Policy (CSP).

### Cross-Site Request Forgery (CSRF)
Attackers trick users into making unwanted actions (e.g., changing passwords) on trusted sites.
**Prevention:** Use CSRF tokens to verify legitimate requests.

### Web Shell (WSO)
Attackers upload a malicious shell script to a server, gaining unauthorized access.
**Prevention:** Validate file uploads, restrict executable file types, and monitor system files.

## DDoS Protection & Firewalls

### DDoS Protection
A Distributed Denial-of-Service (DDoS) attack overwhelms a server with excessive traffic, causing downtime.

- **Rate Limiting:** Restrict the number of requests from a single IP.
- **CDN (Content Delivery Network):** Distribute traffic across multiple servers to absorb attacks (e.g., Cloudflare, Akamai).
- **Web Application Firewall (WAF):** Protects web applications from malicious traffic and bot attacks.

### Firewalls
Firewalls control incoming and outgoing network traffic based on security rules.

**Network Firewalls:** Protect the internal network from external threats.
**Host-based Firewalls:** Protect individual servers from unauthorized access.
**Next-Gen Firewalls (NGFW):** Combine traditional firewalls with additional security features like deep packet inspection and intrusion prevention.

<br><br> ***author*** : [Yasin Karbasi](https://github.com/YasinKar)
