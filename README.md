# Clickjacking POC Tester

A simple HTML page to test whether a website is vulnerable to **Clickjacking (UI Redressing)** and to capture a proof of concept for reporting.

## How it works

The page loads a target URL inside an `<iframe>`. If the target does not send
`X-Frame-Options` or a CSP `frame-ancestors` header, the site can be framed
by any third-party page, making it potentially vulnerable to clickjacking.

## Usage

1. Open `index.html` in your browser.
2. Enter the target URL (e.g. `https://example.com/account`).
3. Click **Load in iframe**.
4. Observe the result:
   - **Page renders inside the frame** → likely vulnerable.
   - **Frame is blank / console shows "Refused to display in a frame"** → protected.
5. Take a screenshot as evidence for your report.

## Remediation

Recommend the following to the site owner:

- `X-Frame-Options: DENY` (or `SAMEORIGIN`)
- `Content-Security-Policy: frame-ancestors 'none'` (or `'self'`)
- Frame-busting JavaScript only as a secondary defense

## References

- [OWASP: Clickjacking](https://owasp.org/www-community/attacks/Clickjacking)
- [OWASP Clickjacking Defense Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Clickjacking_Defense_Cheat_Sheet.html)

## Disclaimer

This tool is for **educational purposes and authorized security testing only**.
Only test systems you own or have explicit written permission to test.
The author is not responsible for misuse.
