### **What is access control?**
-  Access control is the application of constraints on who or what is authorized to perform actions or access resources. In the context of web applications, access control is dependent on authentication and session management:
	- **Authentication** confirms that the user is who they say they are.
	- **Session management** identifies which subsequent HTTP requests are being made by that same user.
	- **Access control** determines whether the user is allowed to carry out the action that they are attempting to perform.

- Access control is basically a concept where the system controls what the user can access based on the permissions allowed in their accounts or roles. For example, a student can only access certain permissions in a schools portal like checking their grades, finishing assignments, answering quizzes, etc. While a teachers access are creating assignments, grading a students work etc.

---
## **Vertical privilege escalation**
- If a user can gain access to functionality that they are not permitted to access then this is vertical privilege escalation. For example, if a non-administrative user can gain access to an admin page where they can delete user accounts, then this is vertical privilege escalation.

---
## **Unprotected functionality**
- **What it is:** Sensitive admin pages exist on the server, but the app fails to check if the user requesting them is actually an admin.
- **Why it happens:** Developers hide the link from regular users' UI, assuming "if they can't see the link, they won't find the page" (Security through Obscurity).
- **How attackers find it:**
    - Direct URL typing (e.g., `/admin`)
    - Public files like `robots.txt`
    - Brute-forcing URLs using wordlists (dirb/gobuster)

Simply hiding an admin button in the web page isn't security. If the server doesn't check _who_ is asking for `/admin`, any normal user can just type the URL directly into their address bar and gain admin powers.

Attackers discover these hidden URLs by checking `robots.txt` or brute-forcing paths with wordlists.

---
## **Unprotected functionality - Continued**
- **Security by Obscurity:** Trying to protect admin pages by giving them random/unpredictable URLs instead of enforcing server-side checks.
- **Why it fails:** Frontend JavaScript sent to normal users often contains the hidden URL (e.g., inside conditional `if (isAdmin)` UI code), making it easy to find by viewing source code.
- Developers try to hide admin pages by using long, random URLs (like `/administrator-panel-yb556`). However, they often leak this exact URL inside frontend JavaScript code. Even if regular users can't see the "Admin" button on the page, they can inspect the page's source code, find the secret URL, and navigate straight to it.

---
## **Parameter-based access control methods**
- **Concept:** The app determines your role at login, but stores that role in a location the user can control/edit.
- **Where it gets stored:**
    - Cookies (e.g., `Admin=true`)
    - Hidden HTML form fields
    - URL query parameters (e.g., `?role=1` or `?admin=true`)
- **The Flaw:** The server trusts client-side values without validating them on the backend.
- **How it's exploited:** The attacker manually changes the parameter (e.g., changing `admin=false` to `admin=true` in Burp Suite or the browser) to escalate privileges.
- Storing user roles in client-editable locations (cookies, hidden fields, URL parameters).
- Users can inspect or intercept requests and change role values (e.g., `role=0` $\rightarrow$ `role=1`) to gain admin rights.

---
## **Horizontal privilege escalation**
- **What it is:** Accessing resources or data belonging to **another user at the same permission level** (e.g., User A viewing User B's account).
- **How it happens (IDOR):** The app uses a user-controlled parameter (like `?id=123`) to fetch data directly from the database without checking if the logged-in user actually owns that data.
- **How attackers exploit it:**
    - Changing predictable IDs in URLs/requests (e.g., changing `?id=123` to `?id=124`).
    - **Unpredictable IDs (GUIDs):** Even if the app uses long random IDs instead of numbers, attackers can often find other users' GUIDs leaked elsewhere on the site (e.g., in public profiles, messages, or product reviews) and swap them in.
- Staying at the same role level, but jumping sideways into another user's private data.
- **Key Term — IDOR (Insecure Direct Object Reference):** When user input (like `id=123`) points directly to a database record with zero ownership verification.
- **Bypassing GUIDs:** Random IDs stop simple guessing, _unless_ those GUIDs are exposed in public features (comments, posts, API responses) where an attacker can copy them.