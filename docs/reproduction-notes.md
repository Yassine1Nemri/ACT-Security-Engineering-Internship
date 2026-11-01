# Reproduction notes (design-level only)

This repository documents a historical lab. It does **not** include a complete deployment automation package or verified raw configurations. Do not mistake the architecture diagram for a running environment.

## High-level lab rebuild plan

1. Provision an **isolated virtualization environment** with sufficient CPU, memory and storage for a small Windows Server AD test domain, Linux web server, a Wazuh manager/indexer/dashboard, and SIEM clients.
2. Implement separate **test LAN, DMZ, SOC and attacker segments** using a firewall you are authorized to operate. Route only explicitly required management and event-ingestion traffic between zones.
3. Deploy Wazuh components following current vendor guidance; install agents on endpoint and server VMs. The historical report shows three distinct VMs and a separate uploaded screenshot shows Docker Swarm exploration. Do not assume these represent one definitive deployment specification.
4. Enable Windows audit policy for Kerberos service tickets and directory-service access; configure Wazuh data ingestion and FIM. Install a **Suricata IDS on a permitted test point** and verify alert forwarding to Wazuh.
5. **Recreate and unit-test** AD detection logic from validated exports (Windows event 4769 RC4 indicators; event 4662 directory access). Do not blindly treat every match as malicious.
6. Configure a test-only **Gemini enrichment** service that removes sensitive data, handles timeouts/rate limits, and preserves the raw record for analyst review.
7. Design Shuffle test workflows with TheHive; if firewall containment is added, require explicit validation, TTL/rollback and authorization boundaries before any automatic blocks.
8. Perform **authorized lab simulations only**, compare original telemetry with alerts, and collect evidence for true/false positives.

## Missing original inputs

The user-provided materials did not include original `ossec.conf`, `local_rules.xml`, Suricata rule files, firewall exports, SOAR workflow JSON, installation scripts or the Gemini enrichment script text. Screenshots of snippets are evidence but are **not** a trustworthy machine-readable source export. Add these as separate **reviewed, sanitized files** only if you still have them and are authorized to publish them.
