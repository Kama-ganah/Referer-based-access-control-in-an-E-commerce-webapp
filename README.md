# Overview
During an assessment of the application’s administrative functionality, I identified a high-severity access control vulnerability caused by reliance on the HTTP Referer header for authorization. The system allowed role changes based on the presence of a specific Referer value rather than enforcing proper server-side checks. By forging the Referer header, a low-privileged user was able to escalate their privileges to administrator.

# Steps Undertaken

Step 1: Logged in as an administrator to observe normal behavior for role promotion requests.

Step 2: Captured the admin role modification request using Burp Suite and examined HTTP headers.

Step 3: Opened a new session as a regular user and attempted the same request, receiving an "Unauthorized" response.

Step 4: Replayed the request in Burp Repeater, manually adding the Referer header mimicking the admin panel.

Step 5: Confirmed that the request succeeded and the regular user was upgraded to administrator.

# Conclusion

This assessment confirmed a critical access control bypass due to trust in client-controlled headers. Exploitation allowed privilege escalation to administrative roles, enabling full access to sensitive functionality. Proper server-side authorization checks and session-based role enforcement are essential to prevent abuse.
