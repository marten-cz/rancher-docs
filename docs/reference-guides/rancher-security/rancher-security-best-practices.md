---
title: Rancher Security Best Practices
---

<head>
  <link rel="canonical" href="https://ranchermanager.docs.rancher.com/reference-guides/rancher-security/rancher-security-best-practices"/>
</head>

### Restrict Public Access to /version and /rancherversion Path

The upstream (local) Rancher instance provides information about the Rancher version it is running and the Go version that was used to build it. That information is accessible via the `/version` path, which is used for tasks such as automating version bumps, or confirming that a deployment was successful. The upstream instance also provides Rancher version information accessible via the `/rancherversion` path.

Adversaries can misuse this information to identify the running Rancher version and cross-relate it with potential bugs to exploit. If your upstream Rancher instance is publicly available on the web, use a Layer 7 firewall to block `/version` and `/rancherversion`.

See [OWASP Web Application Security Testing - Enumerate Infrastructure and Application Admin Interfaces](https://owasp.org/www-project-web-security-testing-guide/stable/4-Web_Application_Security_Testing/02-Configuration_and_Deployment_Management_Testing/05-Enumerate_Infrastructure_and_Application_Admin_Interfaces.html) for more information on protecting your server.

### Session Management

Some environments may require additional security controls for session management. For example, you may want to limit users' concurrent active sessions or restrict which geolocations those sessions can be initiated from. Such features are not supported by Rancher out of the box. 

If you require such features, combine Layer 7 firewalls with [external authentication providers](../../pages-for-subheaders/authentication-config.md#external-vs-local-authentication).
