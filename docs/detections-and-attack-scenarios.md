# Detection engineering and controlled attack scenarios

All scenarios below were run in a **lab** with assets intentionally configured for validation. This document is evidence-based and does not constitute instructions for attacks against third-party systems.

## 1. Authentication brute force

- Test: multiple login attempts using Hydra from Kali against lab services.
- Telemetry: authentication failure events correlated in Wazuh.
- Response: the report describes a Shuffle workflow receiving a level-12 alert and creating a TheHive case.
- Evidence boundary: **2,445** authentication failures is a dashboard total for the selected test period, **not** a count of distinct brute-force incidents. Exact time-to-block and a full firewall block audit are not included.

**ATT&CK:** T1110 (Brute Force).

## 2. DVWA upload, web shell and reverse shell

- Test: vulnerable application file upload, web-shell placement, and an Ncat reverse-shell exercise.
- Host/network data: Wazuh host telemetry and Suricata IDS alerts.
- Result: the report contains a session screenshot showing `uid=0` in the controlled lab and **486** high-severity Wazuh alerts in the Web Shell category for a scenario window.
- Caution: a highlighted Suricata alert was logged for traffic going toward the **Wazuh manager**, so the particular IDS hit must not be represented as independently confirming the reverse shell. The source report explicitly leaves packet-level correlation open.

**ATT&CK:** T1505.003 (Web Shell), T1059 (Command and Scripting Interpreter).

## 3. Kerberoasting-indicator detection

- Domain: isolated Windows Server 2022 AD lab; test service account with an SPN.
- Test: a user requested a service ticket using the test domain and inspected it with `klist`.
- Signal: Windows **event 4769**, ticket encryption type **RC4** (`0x17`).
- Wazuh: custom rule **100103**, level **12**, mapped to **T1558.003**.
- Limit: RC4 service-ticket events alone can occur in legitimate activity. The rule is an indicator that should be correlated with user/device baselines and unusual request patterns.

Evidence: `../screenshots/09-custom-ad-detection-rules.png`, `../screenshots/10-kerberos-test-evidence.png`.

## 4. DCSync-like directory activity (simulation only)

- Test: lab LDAP query designed to simulate suspicious directory access activity.
- Signal: Windows **event 4662** and replication-related directory property logic.
- Wazuh: custom rule **100104**, level **12**, mapped to **T1003.006**.
- **Important:** No real replication request or password-hash extraction was performed. Do not describe this as a confirmed DCSync exploit or as validated detection of a real DCSync attack.

## Other controls

- Wazuh FIM monitored selected registry modifications on the Windows Server 2022 domain controller.
- Wazuh security configuration assessment evaluated the Ubuntu 24.04 CIS Benchmark, producing an initial **46%** result (125 passed, 145 failed, 9 N/A).
- Dashboards exposed ATT&CK categories and levels; ATT&CK mapping is a classification of observed rule hits, not independent evidence of true-positive attack attribution.

## Improving detection quality (future work)

- Recreate the custom rules from the original Wazuh `local_rules.xml` export, review logic and test against known true positives and benign baselines.
- Add controlled PCAP validation for the reverse-shell IDS signature.
- Track a reviewed alert dataset to calculate precision, false-positive rate, and per-scenario detection performance. None were measured in the provided report.
