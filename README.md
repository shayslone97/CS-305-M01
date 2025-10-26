# CS-305-M01
•	Briefly summarize your client, Artemis Financial, and its software requirements. Who was the client? What issue did the company want you to address?
Client: Artemis Financial, a consulting company specializing in developing individualized financial plans for its customers.
Issue: Artemis Financial sought to modernize its public web interface implement the most current and effective software security to protect sensitive client data and financial information. The core issue was: Ensuring secure communications and data integrity.
Specific Requirements: The company required the implementation of a file verification step in their web application to ensure data integrity during transfer, and secure communication mechanisms, which implied migrating the application from HTTP to HTTPS.
•	What did you do well when you found your client’s software security vulnerabilities? Why is it important to code securely? What value does software security add to a company’s overall well-being?
My primary strength was the systematic application of static analysis testing and adherence to secure coding principles. 

Comprehensive Review: I reviewed the existing code base for known security weaknesses.

Dependency-Check Usage: Utilizing a tool like Dependency-Check allowed me to quickly identify any known vulnerabilities in third-party libraries, ensuring that the foundation of the refactored application was secure. This proactive approach ensures we don't build on a compromised base.
Secure coding is paramount because vulnerabilities are exploitable entry points for attackers. If code is not written securely, any attacker can compromise data confidentiality (stealing client records), integrity (tampering with financial plans), or availability (denial of service). Secure coding transforms the application from a liability into a trustworthy asset, preserving the client's financial data and integrity.
Software security adds immense value to a company's overall well-being:
Trust and Reputation: For a financial company like Artemis, client trust is its most valuable asset. Security builds and maintains this reputation. A data breach could be catastrophic.
Regulatory Compliance: It ensures compliance with financial industry regulations and avoiding massive fines and legal penalties.
Financial Health: The cost of implementing security upfront is significantly less than the cost of a data breach. Security acts as a critical form of risk management. Secure coding is paramount because vulnerabilities are exploitable entry points for attackers. If code is not written securely, any attacker can compromise data confidentiality (stealing client records), integrity (tampering with financial plans), or availability (denial of service). Secure coding transforms the application from a liability into a trustworthy asset, preserving the client's financial data and integrity.
Software security adds immense value to a company's overall well-being:
Trust and Reputation: For a financial company like Artemis, client trust is its most valuable asset. Security builds and maintains this reputation. A data breach could be catastrophic.
Regulatory Compliance: It ensures compliance with financial industry regulations avoiding massive fines and legal penalties.
Financial Health: The cost of implementing security upfront is significantly less than the cost of a data breach. Security acts as a critical form of risk management.

•	Which part of the vulnerability assessment was challenging or helpful to you?
The most challenging part of the vulnerability assessment was ensuring that the legacy code's existing structure could cleanly integrate modern security protocols without breaking existing functionality. Specifically, correctly configuring the Java Keytool and the application properties to deploy the certificate and enforce HTTPS across all endpoints required careful troubleshooting and a deep understanding of the server configuration, rather than just code logic.
The most helpful part was the initial static analysis and functional testing. Manually reviewing the code and identifying areas of weak encryption/missing data verification made the path forward for refactoring extremely clear, allowing me to focus efforts on implementing the checksum verification and the HTTPS configuration.

•	How did you increase layers of security? In the future, what would you use to assess vulnerabilities and decide which mitigation techniques to use?
I increased layers of security by implementing the following controls:
Transport Layer Security (Confidentiality): Converting the communication protocol from insecure HTTP to HTTPS using a self-signed certificate (generated via Java Keytool). This encrypts all data transmitted between the client browser and the server.
Data Integrity (Integrity): Implementing a cryptographic hash algorithm (SHA-256) to generate a checksum for transferred data. This allows Artemis Financial to verify that the file has not been tampered with during transmission.
B. Future Vulnerability Assessment Tools
In the future, I would use a layered approach combining different testing methodologies:
Dynamic Application Security Testing (DAST): Tools like OWASP ZAP or Burp Suite to actively test the running application by mimicking a malicious attacker. This finds flaws in configuration, authentication, and session management.
Interactive Application Security Testing (IAST): Tools that combine SAST and DAST, running within the application during testing to provide real-time vulnerability feedback and context, which is highly efficient in an agile environment.
Penetration Testing: Engaging third-party security experts to perform a targeted, manual audit of the application's entire security posture.


Functionality: The refactoring focused on two main areas:
o	Checksum Verification: Adding new methods to calculate and verify the hash (checksum) against the original data. Functional testing involved passing a unique data string and confirming that the calculated hash matched the expected output, and then verifying that the verification step correctly passed or failed.
o	HTTPS Protocol: Updating the application properties to listen on port 8443 and include the certificate keystore details. Functionality was confirmed by accessing the /hash endpoint using https://localhost:8443/hash.
Security: The application was made secure by:
o	Deploying a strong cryptographic hash algorithm (SHA-256) for data integrity.
o	Implementing HTTPS for secure transport communication.


•	How did you make certain the code and software application were functional and secure? After refactoring the code, how did you check to see whether you introduced new vulnerabilities?
After refactoring, I checked for newly introduced vulnerabilities using the secondary static testing process with the Dependency-Check tool. This tool scans the project's dependencies against known Common Vulnerabilities and Exposures (CVEs). Since I focused only on adding secure coding practices and configuration (using Java's built-in secure APIs and standard server settings), the static analysis validated that I did not introduce any new, vulnerable third-party libraries or configuration issues.
•	What resources, tools, or coding practices did you use that might be helpful in future assignments or tasks?
The most valuable resources and practices used that will be helpful in future assignments include:
Dependency-Check/SAST Tooling: The practice of automating security checks on dependencies and code against known CVEs should be a mandatory step in any deployment pipeline.
Cryptographic API Usage: The experience of integrating and correctly using a standard hash function (like SHA-256) and understanding the requirements for key management and certificate generation (Java Keytool) is crucial for any secure application development.
Secure Configuration Management: The clear understanding of how to configure an application server to enforce HTTPS and use appropriate security settings is directly reusable in most web development projects.
Secure Coding Guidelines: Adherence to principles like Defense in Depth (adding multiple security layers) and Principle of Least Privilege (though primarily applied at the OS level, conceptually applies to code access) are foundational practices.


•	Employers sometimes ask for examples of work that you have successfully completed to show your skills, knowledge, and experience. What might you show future employers from this assignment?

	Skill/Knowledge Demonstrated
Refactored Code Base	Ability to apply secure coding principles, implement cryptographic hashing (checksum), and configure TLS/HTTPS for secure communications.
Java Keytool Certificate Generation Screenshot	Expertise in key management and certificate generation, a fundamental task in securing modern web applications.
Secure Communications Screenshot (HTTPS://localhost:8443/hash)	Proven skill in converting an application from an insecure protocol (HTTP) to a secure one (HTTPS), demonstrating transport layer security implementation.
Dependency-Check Output Report Screenshot	Ability to use industry-standard static analysis tools (SAST) to verify code security, manage dependencies, and ensure compliance with security protocols.
Practices for Secure Software Report	Written communication skills demonstrating the ability to analyze a security problem, justify technical solutions, and articulate the business value of security to a client.

Referring to the standard vulnerability assessment process flow, I addressed security at the Design/Architecture Review stage (by mandating HTTPS) and the Secure Coding/Code Review stage (by implementing the SHA-256 checksum). My process involved:
Vulnerability Identification: Found the use of HTTP and lack of data integrity verification.
Mitigation Design: Chose to implement HTTPS via TLS/SSL and SHA-256 hashing.
Refactoring and Implementation: Updated application properties and added new hash-generating methods.
Verification: Used functional testing and Dependency-Check to ensure both functionality and security compliance were achieved.
I applied industry standard best practices to mitigate known security vulnerabilities:
Maintaining Existing Security: I ensured that any existing validation or input sanitization was preserved. 
Value of Applying Best Practices: The value of applying industry standard practices (like OWASP Top 10 mitigation, Defense in Depth, and using well-vetted cryptographic standards) is twofold:
o	Standardization: It ensures the application's security is reliable and understandable by any other security professional.
o	Proactive Defense: It prevents the most common and damaging attacks, reducing the business risk for Artemis Financial and ensuring their longevity and profitability. The peace of mind that comes from using tested, proven methodologies like HTTPS for transport is invaluable to a company's overall well-being.
