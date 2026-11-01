# Evidence index

The images in `../screenshots/` were **cropped from the supplied original images or directly extracted from images embedded in the supplied internship PDF**. They have not been recreated by an image model. Captions distinguish captured UI from independently validated outcomes.

| File | Provenance | Supports | Cannot independently prove |
|---|---|---|---|
| `01-hci-topology.png` | Uploaded Sangfor HCI topology screenshot | Lab VM/virtual-network arrangement | Exact internal addressing or production deployment |
| `02-ngfw-security-zones.png` | Uploaded NGFW physical interfaces, **address column excluded** | Zone separation and physical interface planning | Effective absence of open cross-zone paths |
| `03-ngfw-firewall-policy.png` | Uploaded NGFW access policy | Configured allow and deny rules, hit counts | That all paths were least-privilege; earlier broad allow exists |
| `04-wazuh-attack-dashboard.png` | Uploaded alert-level / ATT&CK charts | Dashboard visualizations | Accuracy of alerts or cause of activity spikes |
| `05-cis-ubuntu-assessment.png` | Uploaded Wazuh SCA screenshot | 46% CIS benchmark baseline | A later successful remediation |
| `06-gemini-ai-analysis.png` | Uploaded `data.ai_analysis` screenshot | Example AI-written explanation | Verified incident attribution |
| `07-shuffle-enrichment-workflow.png` | Uploaded Shuffle workflow screenshot | Enrichment / case / email workflow design | Successful execution or automatic firewall blocking |
| `08-web-shell-alerts.png` | Embedded in report, PDF page 24, fig. 6.4 | 486 Wazuh level-12 web-shell categorized alerts | Unique compromised hosts / true positives |
| `09-custom-ad-detection-rules.png` | Embedded in report, PDF page 28, fig. 6.12 | Wazuh custom rule definitions | Real DCSync success |
| `10-kerberos-test-evidence.png` | Embedded in report, PDF page 27, fig. 6.10 | Lab service-ticket investigation | Password extraction |
| `11-thehive-test-environment.png` | Embedded in report, PDF page 33, fig. 8.2 | TheHive UI setup | A completed case lifecycle |

## Materials deliberately omitted

- **Docker Swarm terminal screenshot:** included an exposed `docker swarm join --token ...` value. Never commit it; rotate/revoke the token if the cluster still exists.
- **Original 36-page internship PDF:** contains employer network details and potentially sensitive configuration/identifiers. It remains an offline source, not a public repository artifact.
- **Complete NGFW object table and raw interface addressing:** omitted or cropped to limit organizational infrastructure exposure.
- **Sangfor endpoint security screenshot showing historic 2021 detections:** not enough context to attribute these historical events to the 2026 internship, so excluded from project results.
- **Duplicates of the same Gemini output:** only one copy retained.

Even sanitized screenshots can reveal an organization's architecture. **Get ACT's permission to publish screenshots.**
