# Sentinel-Event-Log-Analysis

🔍Suspicious Login:

Step 1: 🚫 Brute-Force Login Attempts

I began the investigation by identifying repeated failed login attempts against accounts within a narrow time window, which is often indicative of a brute-force attack.

🔍 Outcome:
Multiple accounts experienced a high volume of failed login attempts within the same hour:
Over 9,000 failed login attempts were detected from the \ADMINISTRATOR account on a Windows-based system (SOC-FW-RDP). Additionally, nearly 2,000 failed attempts were made using the \admin account and over 1,700 attempts using the \administrator account on another Windows VM (SHIR-Hive). Other generic accounts such as \USER also experienced elevated failed login attempts, further suggesting a potential brute-force attack campaign.

🧠 Insight:
This login pattern strongly suggests a brute-force attack, with thousands of failed login attempts against administrative and generic accounts. Notably:

Administrator-level accounts like \ADMINISTRATOR, \admin, and \administrator were targeted heavily.

Generic/default accounts (\USER, \TEST, \SERVER) were also probed, indicating a broad login spray.

These findings reinforce the need for:

Strong password policies

Account lockout mechanisms

Disabling unused/default accounts

Monitoring authentication logs continuously
