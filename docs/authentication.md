# Paywaz Public API — Authentication (Preview)

This document provides an overview of how authentication will function for the
Paywaz Public API.  
As Paywaz is currently operating in stealth mode, the flows and structures
described here are **preliminary** and intended for planning and integration
readiness only.

Production authentication details — including key issuance, scopes, JWT
structures, and endpoint availability — will be finalized as Paywaz moves into
public release.

---

## Overview

All requests to the Paywaz Public API require authentication.

The authentication model is built around:

- **API Keys** — uniquely identifying a merchant or partner  
- **JWT Tokens** — short-lived tokens used for secure, stateless request auth  
- **Non-Custodial Signing** (optional) — cryptographic confirmation of requests
  originating from a merchant-controlled wallet  
- **Role-Based Access Scopes** — ensuring that keys are limited to the correct
  merchant and permission set  

The authentication layer is designed to be **secure, lightweight**, and
compatible with:

- Server-side applications  
- Web and mobile clients  
- POS devices  
- Third-party ecommerce or integration platforms  

---

## API Keys (Merchant Credentials)

Each merchant integrating with Paywaz receives:

- A **Public API Key** – safe to embed client-side for initializing sessions  
- A **Secret API Key** – used for server-to-server calls  

### Example (conceptual):
