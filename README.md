# monaco-project

Monaco (Configuration-as-Code = disaster recovery and consistent re-creation)
Monaco is the native CLI tool for “Configuration as Code” (CaC) for Dynatrace: you define configurations (tags, dashboards, alerts, etc) in YAML/JSON files, version them, deploy them automatically
Typical commands:
•	monaco deploy (to push config)
•	monaco download (to fetch existing config into files)
•	monaco delete, monaco generate etc
How to get started – checklist
Here’s a step‐by‐step starter plan:
1.	Install Monaco CLI
o	Grab the latest release from GitHub repo GitHub+1
o	Ensure you have access to your Dynatrace environment and generate an API token or OAuth credentials as required
```bash
curl -L https://github.com/Dynatrace/dynatrace-configuration-as-code/releases/latest/download/monaco-linux-amd64 -o monaco-linux-amd64
mv monaco-linux-amd64 monaco
chmod +x Monaco
sudo mv monaco /usr/local/bin/
monaco
```
