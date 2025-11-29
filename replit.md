# **Web Security Vulnerability Lab**



##### **Overview**



**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



A comprehensive web vulnerability scanner and demonstration platform built with Flask. This educational tool helps identify common web security flaws including CSRF, IDOR, SQL Injection, XSS, and Subdomain Enumeration.



**Current Status**: Fully operational and ready for use in the Replit environment.



##### **Recent Changes (November 29, 2025)**



**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



* Configured for Replit environment with proper host/port binding (0.0.0.0:5000)
* Fixed Python dependency issues (removed Windows-specific pywin32 package)
* Fixed code bugs:

1. SQL injection scanner parameter handling (line 138)
2. URL variable initialization in subdomain checker (line 355)

* Added Gunicorn for production-ready deployment
* Configured autoscale deployment for optimal performance
* Set debug mode to False for production readiness





##### **Project Architecture**



###### **Technology Stack**



* **Backend Framework**: Flask 3.1.2
* **Async Processing**: aiohttp, asyncio for concurrent scanning
* **Web Scraping**: BeautifulSoup4, requests
* **Production Server**: Gunicorn 23.0.0
* **Security Tools**: Custom vulnerability scanners

&nbsp;



##### **Directory Structure**



.

├── app.py                  # Main Flask application with all scanner logic

├── requirements.txt        # Python dependencies

├── static/

│   └── css/

│       └── style.css      # Application styling

└── templates/

&nbsp;   ├── index.html         # Dashboard (main tool selection page)

&nbsp;   ├── login.html         # Login page (root route)

&nbsp;   ├── tool\_page.html     # Individual tool interface

&nbsp;   ├── results\_page.html  # CSRF scan results

&nbsp;   ├── idor\_results\_page.html    # IDOR scan results

&nbsp;   ├── sqli\_results\_page.html    # SQL injection scan results

&nbsp;   ├── xss\_adv\_results\_page.html # XSS scan results

&nbsp;   └── subdomain\_results\_page.html # Subdomain scan results



##### **Features**

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



###### **1. CSRF Form Scanner**



* Passive scanner that checks web forms for CSRF protection tokens
* Validates common CSRF token naming patterns
* Checks security headers (X-Frame-Options, CSP, etc.)



###### **2. IDOR Scanner**



* Tests for Insecure Direct Object References
* Iterates through ID ranges in URL templates
* Compares responses to detect unauthorized access



###### **3. SQL Injection Scanner**



* Async-based testing with multiple payload types
* Boolean-based, error-based, and time-based detection
* Tests all URL parameters automatically



###### **4. Advanced XSS Scanner**



* Uses polyglot payloads with unique token tracing
* Tests both GET and POST parameters
* Optional form crawling for comprehensive coverage
* Concurrent testing with configurable worker threads



###### **5. Passive Subdomain Enumerator**



* Queries Certificate Transparency logs (crt.sh)
* Active validation of discovered subdomains
* Checks both HTTPS and HTTP protocols
* Concurrent connection testing



##### **Development Configuration**

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



###### **Running Locally (Development)**



The application is configured to run on 0.0.0.0:5000 with debug mode disabled for security.



**Workflow**: Flask Application



* Command: python app.py
* Port: 5000
* Output: webview



###### **Deployment (Production)**



Configured for autoscale deployment using Gunicorn:



* Server: Gunicorn with --reuse-port for better performance
* Binding: 0.0.0.0:5000
* Deployment Type: Autoscale (stateless web application)



###### **Important Notes**

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**

###### 

###### **Security \& Usage**



⚠️ **Educational Use Only**: This tool is designed for authorized security testing and educational purposes only. Never use it on servers you don't own or have explicit permission to test.



###### **Dependencies**



All dependencies are specified in requirements.txt. The project uses:



* Async HTTP client (aiohttp) for performance
* Multiple pwntools dependencies (for educational security research)
* BeautifulSoup4 for HTML parsing
* Flask and Werkzeug for the web framework



###### **Environment**



* Python 3.11
* No database required (stateless application)
* No environment variables needed for basic operation
* All scanners use external targets provided by users



###### **User Preferences**

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



None specified yet.



###### **Known Issues**

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



* Some LSP warnings about import resolution (cosmetic, dependencies are installed correctly)
* Development server warnings in production (resolved by using Gunicorn in deployment)
