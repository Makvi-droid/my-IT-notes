## **What is it?**
- also known as directory traversal
- lets an attacker read arbitrary files on the server ( files outside the intended web root directory, like system configs or source code) 
- happens when user input is passed directly into file paths without proper sanitization or validation.

## **How attackers exploit it:**
- Attackers inject directory traversal sequences (`../`) into URL parameters to climb up to the root directory (`/`) and access files anywhere on the server.
- **Mechanism:** They add `../` to input fields or URL parameters (e.g., `?filename=../../../etc/passwd`).
- **The Result:** The server resolves the `../` movements, breaks out of the web folder, and climbs up to the root directory where sensitive system files live.

