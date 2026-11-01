# Results, evidence quality and limitations

## Recorded metrics

| Source observation | Value | Caveat |
|---|---:|---|
| Wazuh Threat Hunting events | ~31.8M | Aggregate event volume across the observed campaign |
| Wazuh alerts with severity level ≥12 | 31,641 | Alert records, not unique confirmed incidents |
| Authentication failures | 2,445 | Aggregated failures; not unique brute-force events |
| Authentication successes | 8,750 | Contextual dashboard metric, not evidence of successful intrusion |
| Agent registrations | 5 | Four active in the report snapshot |
| Web-shell scenario | 486 | An example dashboard timeframe |
| CIS Ubuntu 24.04 benchmark | 46% | 125 passed, 145 failed, 9 N/A |

## What was demonstrated

- Working lab segmentation with controlled traffic policies and outbound SNAT.
- Wazuh dashboard visibility into host and Suricata logs.
- Windows AD rule logic targeting Kerberoasting indicators and simulated replication-related access.
- Gemini enrichment accessible inside alert records.
- Visual SOAR workflow integration with TheHive and documented case-creation workflow.

## What the evidence does *not* prove

- **30% fewer false positives.** No before/after counts, confusion matrix, sample labels, or calculation is present in the supplied report.
- **Production readiness or throughput.** Only a small controlled lab with known offensive scenarios was tested.
- **Successful automatic Sangfor IP blocking.** Narrative sections contradict one another, and the supplied images do not show a verified end-to-end containment trace.
- **Real DCSync exploitation.** Only a simulated LDAP access pattern was run.
- **All Suricata possible reverse-shell alerts are true positives.** A highlighted signature points at the Wazuh manager and needs PCAP confirmation.
- **CIS remediation.** A 46% baseline is reported; there is no subsequent score to establish improvement.
- **Public-cloud hybrid deployment.** The implemented infrastructure was private HCI.
- **A response-time improvement.** No controlled measurement was taken.

## Security review note

The supplied NGFW policy screenshot also includes a broad allow rule before the final deny rule. This should be assessed carefully before claiming effective network-wide least privilege. This is a useful lesson from a proof of concept, not a reason to discard the work.

## Next validation milestones

1. Preserve and label a small set of anonymized benign and malicious test events; measure precision and false-positive rate.
2. Verify reverse-shell IDS signatures using PCAP, destination/port correlation and host process information.
3. Replay a full SOAR workflow in a dedicated lab; capture the source alert, Shuffle execution status, Sangfor API response, final rule/object, and TheHive case ID.
4. Remediate selected SCA checks, rerun the same benchmark, and report the new pass/fail distribution.
