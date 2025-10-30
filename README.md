# monaco-project

Monaco (Configuration-as-Code = disaster recovery and consistent re-creation)
Monaco is the native CLI tool for “Configuration as Code” (CaC) for Dynatrace: you define configurations (tags, dashboards, alerts, etc) in YAML/JSON files, version them, deploy them automatically
Typical commands:
•	monaco deploy (to push config)
•	monaco download (to fetch existing config into files)
•	monaco delete, monaco generate etc
How to get started – checklist
Here’s a step‐by‐step starter plan:
### 1.	Install Monaco CLI 
o	Grab the latest release from GitHub repo GitHub+1
o	Ensure you have access to your Dynatrace environment and generate an API token or OAuth credentials as required
```bash
curl -L https://github.com/Dynatrace/dynatrace-configuration-as-code/releases/latest/download/monaco-linux-amd64 -o monaco-linux-amd64
mv monaco-linux-amd64 monaco
chmod +x Monaco
sudo mv monaco /usr/local/bin/
monaco
```

### 🧩Set API token environment variable
Make sure you’ve created a Dynatrace API token with these scopes:
```yaml
ReadConfig
WriteConfig
settings.read
settings.write
(optional) ReadSyntheticData if you want to pull monitors too.
```
### 2. Download the configuration (Optional)
create a folder like 
mkdir monaco-project
create a file manifest.yaml
```yaml
manifestVersion: 1.0
projects: []
environmentGroups:
  - name: default
    environments:
      - name: my-dt-env
        url: https://odg17023.live.dynatrace.com
        auth:
          token:
            name: DT_API_TOKEN
```
To Download the existing configuration
```yaml
export DT_API_TOKEN="dt0c01.xxxxxx"  ( Create Access Token)
monaco download   --manifest manifest.yaml   --environment my-dt-env   --api auto-tag,management-zone,synthetic-monitor,dashboard,alerting-profile,notification,anomaly-detection-metrics,anomaly-detection-services,calculated-metrics-service   --output-folder projects
```
To Run the Deployment
```yaml
monaco  deploy --dry-run manifest.yaml
monaco deploy manifest.yaml
```


