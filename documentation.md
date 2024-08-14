# Documentation: Session Hijacking Attack Using XSS and Cookie Editor: A Step-by-Step Guide

## Introduction

This document provides a comprehensive guide on how a session hijacking attack was performed on `testphp.vulnweb.com` using a Cross-Site Scripting (XSS) vulnerability. The attack involves capturing the session cookie via an XSS payload and manually injecting it using a cookie editor to hijack the session. This documentation explains each step of the attack, discusses the associated vulnerabilities, and provides mitigation strategies to prevent such attacks.

## Prerequisites

Before replicating the steps in this guide, ensure you have the following:

- A browser (Firefox or Chrome) with a cookie editor extension installed (e.g., "EditThisCookie" for Chrome or "Cookie-Editor" for Firefox).
- Basic knowledge of XSS, HTTP requests, and cookie handling.

## Steps to Perform the Attack

### 1. Identifying the XSS Vulnerability

Cross-site scripting (XSS) is a vulnerability that occurs when an application allows users to inject malicious scripts into web pages. These scripts can capture sensitive information like session cookies.

**Instructions:**

1. Navigate to `testphp.vulnweb.com`.
2. Locate a search option or any input field reflecting user input on the page.
3. Enter the following script in the input field:
    ```HTML
    <script>alert(document.cookie)</script>
    ```
4. Submit the form.

**Outcome:**

If the application is vulnerable, an alert box will display the current session's cookie (e.g., `PHPSESSID=abc123xyz;`).

### 2. Capturing the Session Cookie

The script `<script>alert(document.cookie)</script>` is a simple XSS payload. When executed, it displays the session cookie in an alert box.

**Instructions:**

1. After submitting the XSS payload, copy the session cookie from the alert box for use in the hijacking attempt.

### 3. Open a New Browser Instance or Incognito Mode

To ensure that no existing session cookies interfere with the attack, open a new browser window or incognito/private mode.

**Instructions:**

1. Open a new incognito/private window or a different browser.
2. Navigate to `testphp.vulnweb.com` without logging in.

### 4. Manually Add the Captured Cookie Using the Cookie Editor

A cookie editor allows you to modify, add, or delete cookies for a specific site.

**Instructions:**

1. Open the cookie editor extension from your browser’s toolbar.
2. Click the `+` icon to add a new cookie.
3. Enter the following details:
    - **Name**: `PHPSESSID`
    - **Value**: (Paste the stolen session ID)
    - **Domain**: `testphp.vulnweb.com`
    - **Path**: `/`
4. Save the changes.

### 5. Reload the Page to Hijack the Session

Reloading the page sends the modified cookie to the server, allowing you to hijack the session.

**Instructions:**

1. Reload the `testphp.vulnweb.com` page in the browser where you added the cookie.
2. If successful, you will be logged in as the user associated with the session ID.

### 6. Verify and Document the Hijacked Session

It's essential to document the process and verify the successful hijack.

**Instructions:**

1. Navigate through `testphp.vulnweb.com` to access user-specific areas.
2. Take screenshots of the XSS alert, the cookie editor before and after modification, and the results after reloading the page.
3. Document any actions you could perform that confirm the session hijacking.

## Mitigation Recommendations

### 1. Sanitize User Inputs
Ensure all user inputs are sanitized and encoded before rendering them on the page to prevent XSS.

### 2. Use Secure Cookies
Set the `HttpOnly` and `Secure` flags on cookies to prevent unauthorized access.

### 3. Implement Content Security Policy (CSP)
A CSP can mitigate XSS by restricting the sources from which scripts can be loaded.

### 4. Session Expiration and Regeneration
Ensure sessions expire after inactivity and regenerate session IDs upon login to reduce the risk of session fixation and hijacking.

## Conclusion

This documentation outlines the process of performing a session hijacking attack using XSS and a cookie editor. By understanding the method and its implications, organizations can secure their web applications against such threats. Always conduct these activities in ethical and legal environments to ensure responsible security practices.

