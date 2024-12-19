Monitor Application
Overview
The monitor application reads a list of URLs from a file, processes them, and outputs their status, including redirections and media references. It is designed to simulate a basic HTTP client with the ability to handle both HTTP and HTTPS protocols.

Features
•	URL Status Check: Determines the status of a given URL (e.g., HTTP response codes).
•	Redirection Handling: Detects and follows redirections specified in the HTTP Location header.
•	Media Reference Detection: Identifies media references (e.g., images) in the response and fetches their status.
•	HTTP/HTTPS Support: Automatically determines the appropriate protocol and port.

Requirements
•	Java Development Kit (JDK) 8 or later.
Setup
1.	Clone or download the project to your local machine.
2.	Ensure you have a valid Java environment set up.
3.	Prepare a text file containing a list of URLs, one per line.
   
Usage
Compile the program:
javac monitor.java
Run the program:
java monitor <urls_file>
•	<urls_file>: Path to the text file containing URLs.
Example:
java monitor urls.txt
File Input Format
The input file should contain URLs, one per line, in the following format:
http://example.com
https://example.org

Key Classes and Methods
main
•	Parses command-line arguments and initiates processing of URLs from the input file.
mainHelper
•	Core logic for handling URL requests, including constructing HTTP requests, processing responses, and detecting redirections or media references.
constructHost
•	Extracts the host name from a given URL.
constructPath
•	Determines the path component of the URL.
makeSocket
•	Creates a Socket or SSLSocket based on the protocol (HTTP or HTTPS).
redirected
•	Checks if a response header indicates a redirection.
containsMedia
•	Detects if a response contains media (e.g., <img src> tags).

Example Output
For a URL https://example.com:
URL:https://example.com
Status: 200 OK
Redirected URL:https://redirected.com
Status: 301 Moved Permanently
Referenced URL:https://example.com/image.png
Status: 200 OK

Known Limitations
•	Assumes the input file is well-formed.
•	Limited support for non-standard HTTP headers or edge cases.
•	No timeout handling for slow connections.

Future Enhancements
•	Add support for additional HTTP methods (e.g., POST).
•	Improve error handling for malformed URLs and network issues.
•	Implement parallel processing for faster URL checks.
•	Include user-agent headers for better compatibility with servers.
