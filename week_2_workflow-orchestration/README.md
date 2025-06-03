# Workflow Orchestration with Kestra

This week’s focus is on mastering workflow orchestration using **Kestra**.

Kestra is an open-source, event-driven orchestration platform that makes it easy to build and manage both scheduled and event-based workflows. It leverages **Infrastructure as Code (IaC)** principles, enabling developers and data engineers to define powerful, reliable workflows with minimal YAML.

## Why Kestra?

- **Open-source and extensible**
- **Supports both scheduled and event-driven tasks**
- **Easy-to-write YAML-based configurations**
- **Scales for modern data and process orchestration needs**

# Setup
Instructions can be fine [here](https://kestra.io/docs/installation/docker-compose?clid=eyJpIjoiV2d3SW9XcWFWZ3F4ZWtsWVlvdW5wIiwiaCI6IiIsInAiOiIvZGUtem9vbWNhbXAvZG9ja2VyLWNvbXBvc2UiLCJ0IjoxNzQ4NTMxODQwfQ.ORX7JkNLzWnPjL5dw2rs1YmmYHcrWg34v6PT1jUdtKw#download-the-docker-compose-file)

If you're on Windows, use the following command to donwload docker-compose.yaml file for Kestra setup:

```bash
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/kestra-io/kestra/develop/docker-compose.yml" -OutFile "docker-compose.yml"
```

# Launch Kestra
Use the following command to start the Kestra server:

```bash
docker-compose up -d
```
Open the URL http://localhost:8080 in your browser to launch the UI.
