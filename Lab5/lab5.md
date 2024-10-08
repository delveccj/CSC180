We will download and install **Metasploitable 2**

**Description**: Metasploitable 2 is one of the most popular intentionally vulnerable VMs designed by Rapid7. It is an excellent starting point for practicing penetration testing, vulnerability exploitation, and learning to identify common security misconfigurations.

**Challenges**: Includes a wide range of vulnerabilities like weak services (e.g., vsftpd, MySQL, PHP), misconfigurations, outdated software, and various security flaws.

**Download**: Metasploitable 2 on SourceForge https://docs.rapid7.com/metasploit/metasploitable-2/

It's a fantastic training ground for pentesting skills. 

Also here are some **medium-hard** picoCTF challenges that will dovetail nicely with the types of tasks and skills you might need for a Hivestorm-style event. These CTF challenges should align with the themes of **cyber defense**, **vulnerability exploitation**, and **system security**.

### **Medium-Hard picoCTF Challenges:**

1. **Forensics: "Sleuthkit Apprentice"**
   - **Description**: This challenge involves file system forensics using tools like `sleuthkit` or `Autopsy`. Participants are asked to investigate a disk image for hidden or deleted files and recover evidence or flags.
   - **Skills Covered**: Forensic analysis, file recovery, disk image exploration.
   - **Why It Fits**: Similar to the vulnerability and defense aspects of Hivestorm, this challenge teaches participants to investigate compromised systems for suspicious or deleted files—important skills for incident response and system hardening.

2. **Cryptography: "Matryoshka Dolls"**
   - **Description**: This is a layered cryptography challenge where you solve multiple levels of encrypted data to retrieve the flag. Each layer involves different cryptographic techniques.
   - **Skills Covered**: Cryptographic analysis, multi-step decryption, problem-solving.
   - **Why It Fits**: In Hivestorm-like competitions, you may need to decipher encrypted messages or recover encrypted data from a compromised system. This challenge sharpens those cryptographic analysis skills.

3. **Binary Exploitation: "Buffer Overflow "**
   - **Description**: This challenge focuses on exploiting a buffer overflow vulnerability in a binary to gain control of the program and retrieve the flag.
   - **Skills Covered**: Binary exploitation, stack overflows, memory manipulation.
   - **Why It Fits**: Buffer overflows are classic vulnerabilities that appear in real-world systems and CTFs alike. This challenge aligns with the exploit development and defensive aspects of Hivestorm events, where securing code from such exploits is key.

4. **Web Exploitation: "SQLiLite"**
   - **Description**: This challenge involves exploiting an SQL injection vulnerability on a web application to gain access to the database and extract the flag.
   - **Skills Covered**: Web security, SQL injection, database exploitation.
   - **Why It Fits**: Many Hivestorm scenarios include web-based vulnerabilities, and SQL injection is a common real-world exploit. This challenge helps participants practice identifying and exploiting web vulnerabilities while understanding how to defend against them.

5. **General Skills: "Permissions"**
   - **Description**: This challenge involves examining a Linux system to identify and fix misconfigurations related to file permissions. The goal is to ensure that permissions are set securely to prevent unauthorized access.
   - **Skills Covered**: System hardening, permissions configuration, Linux file system security.
   - **Why It Fits**: This challenge is directly related to securing Linux systems, which is a core focus of Hivestorm. Understanding proper file permissions and fixing misconfigurations is essential for preventing unauthorized access in a defense-focused environment.

---

### **How These Fit into Hivestorm Training:**
- **Hivestorm** is a collegiate cybersecurity defense competition that focuses on securing vulnerable systems. The key skills tested are vulnerability identification, system hardening, and forensic analysis.
- These picoCTF challenges involve realistic exploitation and defense tasks—such as forensic investigation, fixing misconfigurations, and defending against web and binary exploits—which are crucial for success in a Hivestorm-style event.
  
Using these challenges will help our team develop a well-rounded skill set in both offensive and defensive techniques. Happy practicing!
