

## Adversary Behavior Detection Process

### Overview

This document outlines the steps taken when adversary behavior is detected within the system. The process includes enriching detection entities, downloading and analyzing suspicious files, checking their reputation, and taking appropriate response actions based on the severity of the threat.

### Flowchart

![Adversary Behavior Detected](./path/to/your/image.png)

### Steps and Descriptions

1. **Trigger**: The process starts when an adversary behavior is detected. This trigger can come from various detection systems within the network.

2. **Enrich Detection Entities**: Enrich the data related to the detected adversary behavior. This includes gathering additional information about the detection host and the entities involved in the detection.

3. **Download exe File from Detection Host**: Attempt to download the executable file from the detection host for further analysis.

   - **Decision Point - Download Successful?**
     - **Yes**: If the download is successful, proceed to the next step.
     - **No**: If the download fails, display insights on why the download failed.

4. **Delete Downloaded File from SOAR**: Once the file is successfully downloaded, delete the file from the Security Orchestration, Automation, and Response (SOAR) system to prevent duplication and manage storage.

5. **Sandbox File Analysis**: Perform a sandbox analysis on the downloaded file to understand its behavior in a controlled environment.

6. **CTI: Check Hash Reputation**: Utilize Cyber Threat Intelligence (CTI) to check the hash reputation of the file. This helps in determining if the file has been previously identified as malicious.

   - **Decision Point - Malicious Rating (Sandbox, Intel)**
     - **No**: If the file is not rated as malicious, close the detection as a false positive.
     - **Yes**: If the file is rated as malicious, proceed to the next step.

7. **High Severity: Email Notification**: If the file is confirmed to be malicious and of high severity, send an email notification to the security team.

8. **Response Action - Isolate Host**: Isolate the host where the malicious file was detected to prevent further spread and damage.

9. **Remediation Task - Eradication/Recovery**: Perform remediation tasks, which include eradicating the threat and recovering the affected systems.

### Additional Details

- **Enrichment of Detection Entities**: This step involves integrating with various data sources to provide a comprehensive view of the detected entities, including IP addresses, user accounts, and devices.
  
- **Sandbox File Analysis**: Sandbox environments are isolated virtual environments used to execute suspicious files safely. This analysis helps to observe the file's behavior without risking the actual environment.
  
- **Hash Reputation Check**: Checking the hash reputation involves comparing the file’s hash against known databases of malicious files. This step is crucial in identifying previously known threats quickly.

