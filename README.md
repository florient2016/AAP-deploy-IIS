# IIS Deployment via Ansible Automation Platform

## Overview
This playbook deploys Internet Information Services (IIS) on Windows servers in the Finance department's DEV environment.

## Prerequisites
- Ansible Automation Platform (AAP)
- Windows servers with WinRM enabled
- Target hosts tagged with `dept_finance`, `env_dev`, and `windows`

## Features Installed
- Web Server core components
- HTTP support (default documents, static content, error handling)
- Logging and monitoring modules
- Performance features (compression)
- Security modules

## Usage
```bash
ansible-playbook main.yml
```

## Inventory Requirements
Target hosts must match the group pattern: `dept_finance:&env_dev:&windows`

## What It Does
1. Uninstalls existing IIS (ensures idempotency)
2. Installs IIS features and management tools
3. Creates IIS root directory (`C:\inetpub\wwwroot`)
4. Deploys default static page (`index.html`)
5. Starts W3SVC service with auto-startup enabled
6. Validates HTTP connectivity on port 80

## Validation
The playbook performs a local HTTP GET request to verify successful deployment.

## Notes
- Reboot tasks are commented out; uncomment if required in your environment
- Default page includes French language support