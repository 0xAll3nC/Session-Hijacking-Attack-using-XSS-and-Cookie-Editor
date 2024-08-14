# Session Hijacking Attack Using XSS and Cookie Editor

## Overview

This repository contains a detailed guide on how a session hijacking attack was performed on `testphp.vulnweb.com` using a Cross-Site Scripting (XSS) vulnerability to capture the session cookie, followed by manually injecting the cookie using a cookie editor to hijack the session. The documentation also explains the associated vulnerabilities and provides mitigation strategies to secure applications against such attacks.

## Files

- **Session Hijacking Attack Using XSS and Cookie Editor: A Step-by-Step Guide**: This PDF file contains the complete documentation of the attack, including prerequisites, step-by-step instructions, and recommendations for mitigating such vulnerabilities.

## Prerequisites

To replicate the attack as described in the documentation, you will need:

- A browser (Firefox or Chrome) with a cookie editor extension installed (e.g., "EditThisCookie" for Chrome or "Cookie-Editor" for Firefox).
- Basic knowledge of XSS, HTTP requests, and cookie handling.

## Attack Overview

### Steps:
1. **Identifying the XSS Vulnerability**: Inject a simple XSS payload to capture the session cookie.
2. **Capturing the Session Cookie**: Use the captured cookie for session hijacking.
3. **Opening a New Browser Instance**: Use a separate browser session or incognito mode to avoid conflicts.
4. **Manually Adding the Captured Cookie**: Use a cookie editor to inject the stolen session cookie.
5. **Reloading the Page**: Hijack the session by reloading the page.
6. **Verifying the Hijacked Session**: Confirm that the session hijacking was successful.

## Mitigation Recommendations

- **Sanitize User Inputs**: Ensure proper sanitization and encoding of all user inputs to prevent XSS.
- **Use Secure Cookies**: Set `HttpOnly` and `Secure` flags on cookies to protect them from unauthorized access.
- **Implement Content Security Policy (CSP)**: Use CSP to restrict the sources from which scripts can be loaded.
- **Session Expiration and Regeneration**: Ensure sessions expire after inactivity and regenerate session IDs upon login.

## Conclusion

Understanding how such attacks are executed is crucial for securing web applications against similar threats. The documentation provided here outlines the method and its implications, offering steps to mitigate these vulnerabilities effectively.

---

**Note:** Always conduct such activities in ethical and legal environments to ensure responsible security practices.

