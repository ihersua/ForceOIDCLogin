# ForceOIDCLogin

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](LICENSE)

**ForceOIDCLogin** is a Matomo plugin that enforces exclusive authentication through OpenID Connect (OIDC), disabling the standard username and password login. This plugin is ideal for organizations implementing centralized identity management and Single Sign-On (SSO) solutions.

---

## 🚀 Features

- Forces all users to authenticate via OIDC (e.g., Azure AD, Google, Okta).
- Prevents access to the standard Matomo login form.
- Provides an emergency login bypass using a URL parameter (`?normal=1`).
- Lightweight and easy to integrate.

---

## 📦 Installation

1. Upload the plugin to your Matomo `plugins/` directory:

   ```bash
   unzip ForceOIDCLogin.zip -d plugins/
   ```

2. Activate the plugin:

   ```bash
   ./console plugin:activate ForceOIDCLogin
   ```

---

## ⚙️ Configuration

- Ensure your OIDC plugin (e.g., **RebelOIDC**) is properly configured.
- Add the correct **redirect URI** in your Identity Provider (IdP):

  ```
  https://<your-matomo-domain>/index.php?module=RebelOIDC&action=callback&provider=oidc
  ```

- To bypass the forced OIDC login and access the standard login form, use:

  ```
  https://<your-matomo-domain>/index.php?module=Login&action=login&normal=1
  ```

---

## 🛡️ Security Considerations

- Limit the use of the `?normal=1` bypass to specific IP addresses using web server rules or additional security layers.
- Monitor Matomo access logs for usage of the `?normal` parameter.
- Ensure the `RebelOIDC` plugin is always active to maintain proper login functionality.

---

## 📚 License

This project is licensed under the [GNU General Public License v3.0 (GPL-3.0)](LICENSE).
