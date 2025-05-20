# Sentinel-Event-Log-Analysis

Suspicious Login:
Step 1: 🚫 Brute-Force Login Attempts
I began the investigation by identifying repeated failed login attempts against accounts within a narrow time window, which is often indicative of a brute-force attack.

🔍 Outcome:
Multiple accounts experienced a high volume of failed login attempts within the same hour:

Account	Device	Time	Failed Attempts
\ADMINISTRATOR	SOC-FW-RDP	5/20/2025, 10:00 PM UTC	9997
\admin	SHIR-Hive	5/20/2025, 10:00 PM UTC	1988
\administrator	SHIR-Hive	5/20/2025, 10:00 PM UTC	1740
\USER	SOC-FW-RDP	5/20/2025, 10:00 PM UTC	269
\TEST	SOC-FW-RDP	5/20/2025, 10:00 PM UTC	263
\SERVER	SOC-FW-RDP	5/20/2025, 10:00 PM UTC	240

🧠 Insight:
This login pattern strongly suggests a brute-force attack, with thousands of failed login attempts against administrative and generic accounts. Notably:

Administrator-level accounts like \ADMINISTRATOR, \admin, and \administrator were targeted heavily.

Generic/default accounts (\USER, \TEST, \SERVER) were also probed, indicating a broad login spray.

These findings reinforce the need for:

Strong password policies

Account lockout mechanisms

Disabling unused/default accounts

Monitoring authentication logs continuously
