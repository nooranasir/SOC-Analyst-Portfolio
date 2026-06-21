# Case 01 – Phishing URL Detected Investigation

## Incident Overview

**Alert Name:** SOC141 – Phishing URL Detected

**Date/Time:** March 22, 2021, 09:23 PM

**Severity Level:** Security Analyst

**Status:** Confirmed Malicious

**Action Taken:** Endpoint Contained

---

## Executive Summary

A security alert was generated after a user attempted to access a suspicious URL that was later identified as malicious through threat intelligence enrichment. Further investigation revealed the presence of a suspicious process running on the affected endpoint. Analysis of the associated file hash confirmed malicious activity. The endpoint was isolated to prevent further compromise.

---

## Alert Details

| Field                | Value                                                                                  |
| -------------------- | -------------------------------------------------------------------------------------- |
| Source Address       | 172.16.17.49                                                                           |
| Source Hostname      | EmilyComp                                                                              |
| Destination Address  | 91.189.114.8                                                                           |
| Destination Hostname | mogagrocol.ru                                                                          |
| User                 | ellie                                                                                  |
| Request URL          | http://mogagrocol.ru/wp-content/plugins/akismet/fv/index.php?email=ellie@letsdefend.io |
| User Agent           | Mozilla/5.0 (Windows NT 6.1; Win64; x64) Chrome/79.0.3945.88                           |
| Device Action        | Allowed                                                                                |

---

## Investigation Process

### Step 1: Alert Review

The investigation began by reviewing the alert details provided by the SIEM. The destination domain appeared suspicious and required further validation through threat intelligence sources.
<img width="688" height="323" alt="image" src="https://github.com/user-attachments/assets/775ed3c8-9ff8-44af-8abe-9406020b2dbf" />


---

### Step 2: Log Analysis

Log Management was used to review communications originating from the source IP address:

172.16.17.49

The logs confirmed that the user attempted to access the suspicious URL on March 22, 2021 at 09:23 PM.

Key findings:

* Source Address: 172.16.17.49
* Destination Address: 91.189.114.8
* User: ellie
* User Agent: Mozilla Browser
* Request Status: Allowed
  <img width="698" height="444" alt="image" src="https://github.com/user-attachments/assets/119a52ee-178d-4abb-a1b9-fc0d1181c015" />


---

### Step 3: Threat Intelligence Enrichment

The suspicious URL was analyzed using external threat intelligence platforms.

Sources consulted:

* VirusTotal - <img width="829" height="403" alt="image" src="https://github.com/user-attachments/assets/7e819767-d76e-421d-b683-a14b9981bbb4" />

* Hybrid Analysis - <img width="804" height="339" alt="image" src="https://github.com/user-attachments/assets/d75ca572-b32b-41a0-86a6-ca270c8995cb" />


Results:

* Multiple security vendors classified the URL as malicious.
* Independent threat intelligence sources produced consistent results.

Conclusion:

The URL was confirmed malicious.

---

### Step 4: Endpoint Investigation

The affected endpoint (EmilyComp) was examined through the Endpoint Security console.
<img width="692" height="320" alt="image" src="https://github.com/user-attachments/assets/fb1b6c1a-9c55-41a7-ac0c-e6e0e87f47f7" />


During the investigation:

* A suspicious running process was identified.
* The file hash associated with the process was extracted.-<img width="587" height="124" alt="image" src="https://github.com/user-attachments/assets/498b51a5-031d-4755-a04b-0af8664eaac5" />

* The hash was submitted to VirusTotal for analysis.

Result:

The file hash was identified as malicious by security vendor.
VirusTotal-<img width="929" height="482" alt="image" src="https://github.com/user-attachments/assets/7fb97679-91f2-42fd-9256-3cd313eedec6" />


This increased confidence that the endpoint had been exposed to malicious activity.

---

### Step 5: Containment

Based on the findings:

* The endpoint was isolated using the Endpoint Security platform.
* Containment was performed to prevent lateral movement and additional communication with malicious infrastructure.

Status:

Containment Successful.
<img width="689" height="317" alt="image" src="https://github.com/user-attachments/assets/2558d626-e4ff-4c7b-9ea1-fb846aef639f" />


---

## Indicators of Compromise (IOCs)

### IP Addresses

* 91.189.114.8

### Domain

* mogagrocol.ru

### URL

* http://mogagrocol.ru/wp-content/plugins/akismet/fv/index.php?email=ellie@letsdefend.io

---

## MITRE ATT&CK Mapping

| Technique | Description              |
| --------- | ------------------------ |
| T1566     | Phishing                 |
| T1204     | User Execution           |
| T1583     | Malicious Infrastructure |

---

## Impact Assessment

The user successfully accessed a malicious URL and the request was not blocked. Subsequent endpoint analysis revealed a malicious process, indicating potential compromise of the affected system.

---

## Remediation

* Endpoint isolated from the network.
* Malicious indicators documented.
* Threat intelligence evidence collected.
* Investigation completed according to incident response playbook.

---

## Lessons Learned

* URL reputation checks should be performed immediately when phishing alerts are generated.
* Endpoint analysis is critical even when initial evidence only indicates URL access.
* Threat intelligence enrichment improves confidence during triage and investigation.

---

## Final Verdict

<img width="724" height="416" alt="image" src="https://github.com/user-attachments/assets/66b0e936-0243-4ef8-8a4c-8daf35fa4dc4" />

The alert was determined to be a true positive.

The user accessed a malicious URL, and endpoint investigation revealed a malicious process associated with the incident. The affected host was successfully contained to prevent further compromise.


