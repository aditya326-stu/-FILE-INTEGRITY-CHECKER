# -FILE-INTEGRITY-CHECKER

COMPANY NAME : CODETECH IT SOLUTION

NAME : ADITYA KUMAR DHARA

INTERN ID : CT04DZ243

DOMAIN : CYBER SECURITY AND ETHICAL  HACKING

MENTOR : NEELA SANTOSH

The task given here is about developing a file integrity checker using Python. In the field of cybersecurity and data protection, ensuring that files have not been altered without authorization is an essential requirement. File integrity checking is a technique used to monitor changes in files by generating hash values for them. A hash value, also known as a checksum or digital fingerprint, is a unique string generated from the contents of a file using cryptographic hash functions like SHA-256. If even a single character in the file changes, the generated hash will be completely different, which makes this method highly reliable for detecting modifications.

In this task, the script provided is built with Python’s hashlib library to calculate SHA-256 hash values. The way it works is straightforward yet powerful. For each file that needs to be monitored, the program reads its contents in chunks and passes them through the hashing function. This prevents memory overload when working with large files. The resulting hash value is then stored so it can be compared later during subsequent checks. If the file remains unchanged, the hash generated in future checks will remain the same. However, if the file is altered in any way, the new hash will differ from the previously stored one, allowing the tool to raise an alert.

To make the tool functional across different sessions, the program saves hash values into a JSON file named `file_hashes.json`. JSON is chosen here because it is lightweight, human-readable, and easy to parse with Python. The program maintains the state of each file across executions by saving previously calculated hashes. Whenever the tool is run again, it first loads the stored hashes and then recalculates fresh ones for the monitored files. It then compares both sets of values to determine whether any changes have occurred. If a file has been modified, the script outputs an alert message. If the file is unchanged, it confirms that as well. Additionally, if a new file is introduced that was not previously monitored, the script identifies it as newly added. After this comparison, the program updates the JSON file with the latest hash values so that the new state becomes the reference for future checks.

This project has strong real-world applications. Organizations can use such file integrity checkers to detect unauthorized tampering, accidental modifications, or even malicious changes caused by malware. For instance, in system administration and server management, log files, configuration files, and critical executables can be continuously monitored for suspicious changes. Since the system relies on cryptographic hashing, it provides a high level of assurance that the files are secure from silent alterations.

The tool is also easily extendable. While it currently focuses on SHA-256, one could incorporate other algorithms like SHA-1 or MD5, although these are weaker and less secure. Real-time monitoring could be added by combining the script with libraries like `watchdog`, which can trigger automatic re-checks whenever files are modified. The tool could also be integrated into larger security frameworks to provide continuous auditing.

Overall, the file integrity checker is a simple but effective security utility that ensures file safety by leveraging the reliability of cryptographic hashes. By storing and comparing hash values, it creates a trustworthy way to detect any changes in files, making it a crucial part of cybersecurity practices. This task demonstrates how programming and cryptography can come together to protect sensitive information and maintain trust in data integrity.

