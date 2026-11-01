# Before making this repository public

This project was carried out in an employer-managed environment. A private portfolio ZIP is **not** the same as permission to disclose organizational configuration.

- [ ] Obtain **ACT's explicit permission** to publish any infrastructure screenshots, firewall policy details and company attribution.
- [ ] Prefer synthetic examples and simple architecture diagrams if screenshots are not cleared for release.
- [ ] Review every screenshot at **full resolution**, not only thumbnail size: inspect IPs, usernames, hostnames, domains, support details, session tokens, browser URLs, customer identifiers and license data.
- [ ] Never publish the uploaded screenshot containing a **Docker Swarm join token**; rotate the token if the cluster is live (`docker swarm join-token --rotate worker`, administered by the authorized operator).
- [ ] Do not commit real Gemini/Sangfor/TheHive/Shuffle API tokens, certificates, secrets, .env files, firewall exports or SSH keys.
- [ ] Do not commit the original internship report until distribution rights and sensitive contents have been reviewed.
- [ ] Do not claim validated automatic firewall blocking without a Wazuh alert → Shuffle execution → NGFW rule creation → TheHive case evidence chain.
- [ ] Do not claim the unmeasured 30% false-positive reduction.
- [ ] Confirm all screenshots and example logs are free of personal data.
- [ ] Make the repository **private first**; ask for release approval before switching to public.

**Suggested GitHub description:** `Security Operations Center PoC on Sangfor HCI — Wazuh, Suricata, MITRE ATT&CK detections, AI-assisted triage and Shuffle/TheHive workflows.`

**Suggested topics:** `soc`, `wazuh`, `suricata`, `detection-engineering`, `mitre-attack`, `sangfor`, `soar`, `thehive`, `shuffle`, `cybersecurity`, `blue-team`, `security-operations`.
