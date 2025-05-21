# Sentinel-Event-Log-Analysis

## 📘 **Overview**  
This project focuses on detecting **suspicious login activity** in Windows-based systems by analyzing event logs ingested into **Microsoft Sentinel**. The main objective is to identify **brute-force login attempts** by looking for repeated failed login attempts from the same accounts within short time windows — a common early indicator of malicious activity.

---

## 🧰 **Tools & Environment**

- **Microsoft Sentinel** (Azure-based SIEM)  
- **Windows Virtual Machines** generating SecurityEvent logs  
- **Kusto Query Language (KQL)** for log queries and analysis  

---

### ✅ **Step 1: Detecting Brute-Force Login Attempts**

 > - Queried **failed login events** (`EventID 4625`) from multiple accounts.  
 > - Grouped failed attempts by **Account, Device, and 1-hour time bins**.  
 > - Filtered to highlight accounts with **unusually high failed login counts**.

  ### 🔍 **Outcome:**  
  - Over **9,000 failed login attempts** were detected from the **`\ADMINISTRATOR`** account on the Windows VM **SOC-FW-RDP**. Additionally, nearly **2,000 attempts** targeted the **`\admin`** account, and over **1,700 attempts** hit the 
  **`\administrator`** account on the **SHIR-Hive** VM.

  ### 💡 **Insight:**  
   These findings reveal a clear pattern of **brute-force activity**, focusing primarily on **administrative accounts**. This underscores the importance of:  
 > - Implementing **strong password policies**  
 > - Enforcing **account lockout** after multiple failed attempts    
 > - Continuously **monitoring authentication logs** for suspicious behavior  

![Brute Force Login Attempts](images/brute_force_login.png)

---

### ✅ Step 2: Successful Login After Failures

  > After detecting brute-force login attempts, I ran a query to check whether any of those accounts eventually logged in successfully — a strong signal of potential compromise.

  ### 🔍 **Outcome:**  
  - The query returned **no results**, indicating that none of the accounts experiencing suspected brute-force login attempts successfully logged in afterward during the observed time frame.

  ### 💡 **Insight:**  
  - This strongly suggests that, despite multiple failed attempts, these accounts were **not compromised**. This insight helps SOC teams focus on confirmed breaches and avoid false alarms, improving incident response efficiency.

