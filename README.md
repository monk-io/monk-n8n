# N8N & Monk
This repository contains Monk.io template to deploy N8N either locally or on cloud of your choice (AWS, GCP, Azure, Digital Ocean).

# Prerequisites
- [Install Monk](https://docs.monk.io/docs/get-monk)
- [Register and Login Monk](https://docs.monk.io/docs/acc-and-auth)
- [Add Cloud Provider](https://docs.monk.io/docs/cloud-provider)
- [Add Instance](https://docs.monk.io/docs/multi-cloud)

#### Make sure monkd is running.
```bash
foo@bar:~$ monk status
daemon: ready
auth: logged in
not connected to cluster
```

## Clone Repository
```bash
git clone https://github.com/monk-io/monk-n8n
```

## Load Template
```bash
cd monk-n8n
monk load MANIFEST
```


#### Let's take a look at the themes I have installed.
```bash
foo@bar:~$ monk list monk-n8n
✔ Got the list
Type      Template        Repository  Version  Tags
runnable  monk-n8n/n8n    local       -        -
group     monk-n8n/stack  local       -        -
```

## Deploy Stack
```bash
foo@bar:~$ monk run monk-n8n/stack
✔ Starting the job: local/monk-n8n/stack... DONE
✔ Preparing nodes DONE
✔ Checking/pulling images...
✔ [================================================] 100% n8nio/n8n:latest mnk
✔ Checking/pulling images DONE
✔ Started local/monk-n8n/stack

🔩 templates/local/monk-n8n/stack
 └─🧊 Peer mnk
    └─🔩 templates/local/monk-n8n/n8n
       └─📦 b12a25fbbf3e0aecf4d10ce39eaeda07-local-monk-n8n-n8n-monk-n8n
          ├─🧩 n8nio/n8n:latest
          ├─💾 /var/lib/monkd/volumes/n8n -> /home/node/.n8n
          └─🔌 open 13.49.137.107:8085 (0.0.0.0:8085) -> 8085

💡 You can inspect and manage your above stack with these commands:
	monk logs (-f) local/monk-n8n/stack - Inspect logs
	monk shell     local/monk-n8n/stack - Connect to the container's shell
	monk do        local/monk-n8n/stack/action_name - Run defined action (if exists)
💡 Check monk help for more!
```
## Check web gui

`http://13.49.137.107:8085/`



## Variables
The variables are in `stack.yml` file. You can quickly setup by editing the values here.

| Variable                     	| Description                               	|
|------------------------------	|-------------------------------------------	|
| monk_basic_auth_active                    | n8n basic auth enable, Default: true 	               |
| monk_basic_auth_user                    | n8n basic auth user, Default: monk 	               |
| monk_basic_auth_password                    | n8n basic auth password, Default: monk 	               |
| monk_n8n_hostname                    | n8n hostname, Default: n8n.monk.io 	               |
| monk_n8n_port                    | n8n port, Default: 8085 	               |
| monk_n8n_http_protocol                    | n8n http protocol, Default: http 	               |
| monk_n8n_environment_type                    | n8n environment type, Default: prodcution 	               |
| monk_n8n_webhook_url                    | n8n web hook url, Default: n8n.monk.io 	               |
| monk_n8n_timezone                    | n8n timezone, Default: UTC 	               |



## Stop, remove and clean up workloads and templates

```bash
monk purge    monk-n8n
monk purge -x monk-n8n
```

