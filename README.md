# N8N & Monk

This repository contains Monk.io template to deploy N8N either locally or on cloud of your choice (AWS, GCP, Azure, Digital Ocean).

## Prerequisites

- [Install Monk](https://docs.monk.io/docs/get-monk)
- [Register and Login Monk](https://docs.monk.io/docs/acc-and-auth)
- [Add Cloud Provider](https://docs.monk.io/docs/cloud-provider)
- [Add Instance](https://docs.monk.io/docs/multi-cloud)

## Make sure monkd is running

```bash
foo@bar:~$ monk status
daemon: ready
auth: logged in
not connected to cluster
```

## Clone Repository

```bash
git clone https://github.com/monk-io/n8n
```

## Load Template

```bash
cd n8n
monk load MANIFEST
```

```bash
✔ Got the list
Type      Template  Repository  Version  Tags
runnable  n8n/base  local       -        Workflow automation, Integration, API, Node.js, No-code, Productivity, Data automation, Cloud automation, Business automation, Webhooks, Open-source, Workflow management, Data synchronization, Event-driven automation, Task automation
runnable  n8n/n8n   local       -        Workflow automation, Integration, API, Node.js, No-code, Productivity, Data automation, Cloud automation, Business automation, Webhooks, Open-source, Workflow management, Data synchronization, Event-driven automation, Task automation
```

## Deploy Stack

```bash
foo@bar:~$ monk run n8n/n8n
✔ Starting the run job: local/n8n/n8n... DONE
✔ Preparing nodes DONE
✔ Checking/pulling images DONE
✔ Starting containers DONE
✔ New container local-9a01e5682f434f481b63508b5d-local-n8n-n8n-n8n created DONE
✔ Started local/n8n/n8n
🔩 templates/local/n8n/n8n
 └─🧊 Peer local
    └─🔩 templates/local/n8n/n8n
       └─📦 local-9a01e5682f434f481b63508b5d-local-n8n-n8n-n8n running
          ├─🧩 n8nio/n8n:latest
          └─💾 /var/lib/monkd/volumes/n8n -> /home/node/.n8n

💡 You can inspect and manage your above stack with these commands:
        monk logs (-f) local/n8n/n8n - Inspect logs
        monk shell     local/n8n/n8n - Connect to the container's shell
        monk do        local/n8n/n8n/action_name - Run defined action (if exists)
💡 Check monk help for more!
```

## Check web gui

`http://<server_ip>:8085/`

## Variables

The variables are in `stack.yml` file. You can quickly setup by editing the values here.

| Variable                  | Description             | Default     |
| ------------------------- | ----------------------- | ----------- |
| monk_basic_auth_active    | n8n basic auth enable   | true        |
| monk_basic_auth_user      | n8n basic auth user     | monk        |
| monk_basic_auth_password  | n8n basic auth password | monk        |
| monk_n8n_hostname         | n8n hostname            | n8n.monk.io |
| monk_n8n_port             | n8n port                | 8085        |
| monk_n8n_http_protocol    | n8n http protocol       | http        |
| monk_n8n_environment_type | n8n environment type    | production  |
| monk_n8n_webhook_url      | n8n web hook url        | n8n.monk.io |
| monk_n8n_timezone         | n8n timezone            | UTC         |

## Stop, remove and clean up workloads and templates

```bash
monk purge    n8n
monk purge -x n8n
```
