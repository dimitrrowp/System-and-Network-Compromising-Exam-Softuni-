# System-and-Network-Compromising-Exam-Softuni-
Exam Objective

    ▪ Perform an offline security assessment based on provided archive.
    ▪ Demonstrate practical exploitation of Active Directory, password spraying, privilege escalation, service misconfigurations, persistence, and hash cracking.
    ▪ Document vulnerabilities, methodology, and steps to compromise systems and services.

<img width="813" height="775" alt="Image" src="https://github.com/user-attachments/assets/afe90476-1ef0-448d-ab58-b0f80c6790d4" />
<img width="813" height="775" alt="Image" src="https://github.com/user-attachments/assets/b8dc3c15-3c1e-4391-b78d-96f480491b10" />
<img width="813" height="775" alt="Image" src="https://github.com/user-attachments/assets/89248282-1ac5-4f63-8bae-ec66022d3190" />
<img width="813" height="775" alt="Image" src="https://github.com/user-attachments/assets/b7f69313-0d6a-4a00-8639-d737b07905d1" />
<img width="813" height="775" alt="Image" src="https://github.com/user-attachments/assets/66495022-ab77-4c87-a94a-d84713e45ccc" />
<img width="813" height="775" alt="Image" src="https://github.com/user-attachments/assets/1f254dfa-fa96-47e1-89f4-139a4180c5ff" />
<img width="813" height="775" alt="Image" src="https://github.com/user-attachments/assets/a23fd2cd-6b13-4983-99f9-c44c45255559" />
<img width="813" height="775" alt="Image" src="https://github.com/user-attachments/assets/32e6d358-d175-46f4-9b9e-e8834e485075" />
<img width="813" height="775" alt="Image" src="https://github.com/user-attachments/assets/0c85a3b6-19b3-4180-978f-effd6366ed9b" />
<img width="813" height="775" alt="Image" src="https://github.com/user-attachments/assets/95c7a391-bc27-4008-b039-f47535d4c296" />
<img width="813" height="775" alt="Image" src="https://github.com/user-attachments/assets/e076c9d0-f4b6-49ed-91d6-e91c73fde50d" />
<img width="813" height="775" alt="Image" src="https://github.com/user-attachments/assets/fed7470e-50d9-44fc-a8bb-8a9e0ba377e7" />
<img width="813" height="775" alt="Image" src="https://github.com/user-attachments/assets/a993ba94-e4a9-47a3-b377-e227d854d66d" />

✅ Step-by-step Summary of My Reconnaissance & Exploitation Process

    🔍 Step 1: Active Directory Enumeration with BloodHound

        Task: Import BloodHound.zip into BloodHound and map Kerberoastable Domain Admin users.

        Findings: Identified SQLSERVICE@CONTROLLER.LOCAL as a member of DOMAIN ADMINS@CONTROLLER.LOCAL.

        Impact: Clear attack path from kerberoastable users to full domain compromise.

    🧭 Step 2: Identify Systems with Unconstrained Delegation

        Task: Analyze BloodHound data for unconstrained delegation.

        Findings: Machine account SVC_ADFS$@CYBER.LOCAL allowed unconstrained delegation.

        Impact: Could enable ticket theft and privilege escalation.

    🧑‍💻 Step 3: Password Spraying Attack

        Task: Analyze winpwn.zip results.

        Findings: Account testuser compromised via username=password spraying (testuser:testuser).

        Impact: Weak credential policy allows trivial compromise.

    🛠 Step 4: Drupal Service Credentials Extraction

        Task: Review linpeas.out output.

        Findings: Located Drupal DB credentials inside /var/www/drupal/sites/default/settings.php →
        ▪ Username: root
        ▪ Password: bug

        Impact: Database takeover possible.

    🧨 Step 5: Persistence via CLI (C2 Implant)

        Task: Establish persistence for C:\Windows\Tasks\updater.exe using shortcut links.

        Methodology: Used PowerShell with WScript.Shell COM object to create .lnk on Desktop.

        Impact: Ensures persistence across reboots/logins.

    🔑 Step 6: Hash Cracking with Hashcat

        Task: Crack hash in hash.txt.

        Methodology: Identified hash as NTLM, used hashcat -m 1000 with rockyou.txt wordlist.

        Findings: Successfully recovered original password.

        Impact: Confidential credentials exposed.

🧰 Tools Used

    BloodHound

    winpwn

    linpeas

    PowerShell / CMD

    hashcat

    rockyou.txt wordlist

📌 Conclusion

    The exam engagement demonstrated multiple real-world attack vectors:
    ▪ Active Directory privilege escalation (Kerberoasting & Delegation)
    ▪ Weak credentials exposed via password spraying
    ▪ Service misconfiguration in Drupal
    ▪ Persistent access through CLI implant shortcuts
    ▪ Password recovery through hash cracking

The assessment confirmed that with chained exploitation, an attacker could gain full domain admin rights, persistence, and database access—successfully achieving the exam objectives.
