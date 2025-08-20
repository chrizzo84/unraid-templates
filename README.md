# unraid-templates
Storage for Unraid App templates incl. icons

# 🔑 License
This repository is under  GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007 -> See [License](https://raw.githubusercontent.com/chrizzo84/unraid-templates/main/LICENSE?token=GHSAT0AAAAAABXMPMKOUPLGTE3ONEXO7B7KYZSSXZQ)

---
---
# ⚓ Table of contents
1. [Drone CI Gitea](#Drone)
2. [Azure DevOps Pipelines Agent](#Agent)
3. [Ollama UI](#OllamaUI)
4. [AdGuard Buddy](#AdGuardBuddy)
4. [Issues](#Issues)

<div id='Drone'/>

## ⚒️ Drone CI Gitea
The Drone CI template is specially designed for use with Gitea.

### Description:
Drone by [Harness™](https://harness.io/) is a modern Continuous Integration platform that empowers busy teams to automate their build, test and release workflows using a powerful, cloud native pipeline engine. ([Source](https://docs.drone.io)) 

Link to Drone Documentation: https://docs.drone.io

### Variables:
| **Variablename**          | **Required** | **Description**                                                                                                                                                                                                    | **Default**              |
|---------------------------|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|
| HTTP_PORT                 | X            | Container HTTP Port                                                                                                                                                                                                | 9080                     |
| HTTPS_PORT                | X            | Container HTTPS Port                                                                                                                                                                                               | 9443                     |
| DRONE_AGENTS_ENABLED      | X            | Set to true if you want to run server and agent in the same container.                                                                                                                                             | false                    |
| DRONE_GITEA_SERVER        | X            | Gitea Server URL                                                                                                                                                                                                   | empty                    |
| DRONE_GITEA_CLIENT_ID     | X            | Needs to be generated in Gitea -> More info: https://docs.drone.io/server/provider/gitea/                                                                                                                          | empty                    |
| DRONE_GITEA_CLIENT_SECRET | X            | Needs to be generated in Gitea -> More info: https://docs.drone.io/server/provider/gitea/                                                                                                                          | empty                    |
| DRONE_RPC_SECRET          | X            | Create a shared secret to authenticate communication between runners and your central Drone server. Use "openssl rand -hex 16" to generate a key                                                                   | empty                    |
| DRONE_SERVER_HOST         | X            | Your Drone Server URL                                                                                                                                                                                              |                          |
| DRONE_SERVER_PROTO        | X            | Required string value configures the user-facing protocol. This value is used to create webhooks and redirect urls. It has no actual impact on serving traffic. Possible values are "http" or "https".             | empty                    |
| DRONE_GIT_ALWAYS_AUTH     | X            | Optional boolean value. Configures Drone to authenticate when cloning public repositories. This is only required when your source code management system (e.g. GitHub Enterprise) has private mode enabled.        | true                     |
| DRONE_USER_CREATE         | X            | Optional user account that should be created on startup. This should be used to seed the system with an administrative account. It can be a real account (i.e. a real GitHub user) or it can be a machine account. | username:root,admin:true |

---
---

<div id='OllamaUI'/>

## 🧠 Ollama UI
Ollama UI is a clean, user-friendly web interface for managing and exploring Ollama models.

### Description:
OllamaUI: A Unified Experience for Local Large Language Models
OllamaUI represents more than just a user interface; it is the integration of the core Ollama service with a clean and user-friendly graphical interface. This combination provides a seamless platform for managing and interacting with local large language models.
With OllamaUI, you can effortlessly browse both locally installed and remote models. The interface allows for pulling new model variants with clear progress feedback and provides tools to organize your AI workflows efficiently in one central location. It is an ideal solution for anyone seeking a straightforward and effective way to utilize the power of Ollama.
A key feature is the ability to manage other Ollama instances, as the host connection is fully configurable. By setting the the host in the UI you can connect to any Ollama server on your network, allowing for centralized management of multiple, distributed instances.
The underlying Ollama engine continues to function just as it does in the standard container setup, ensuring a consistent and familiar core experience for existing users. The UI acts as an accessible and intuitive layer, simplifying model management and interaction without altering the fundamental capabilities of Ollama.

Project: [OllamaUI on GitHub](https://github.com/chrizzo84/OllamaUI)
Container Repository: `ghcr.io/chrizzo84/ollamaui`

#### Web UI:
`http://[IP]:[PORT:3000]`

#### Requirements:
- For GPU acceleration, the 'Nvidia-Driver' plugin from Community Apps must be installed.

### Variables:
| **Variablename**         | **Required** | **Description**                                              | **Default**                                 |
|-------------------------|--------------|--------------------------------------------------------------|---------------------------------------------|
| Web UI Port             | X            | Port for the Web UI                                          | 3000                                        |
| Ollama API Port         | X            | Port for the Ollama API                                      | 11434                                       |
| Ollama Models Path      | X            | Storage location for the downloaded Ollama models.           | /mnt/user/appdata/OllamaUI/ollama_models    |
| UI Database Path        | X            | Storage location for the user interface database.            | /mnt/user/appdata/OllamaUI/ui_database      |
| PUID                    |              | User ID to run the container as. Default: Unraid 'nobody'.   | 99                                          |
| PGID                    |              | Group ID to run the container as. Default: Unraid 'users'.   | 100                                         |


<div id='Agent'/>

## 🔩 Azure DevOps Pipelines Agent
---
---

Ubuntu 24.04 Azure Pipelines Agent with some preinstalled software.
- OpenJDK17
- OpenJDK11
- OpenJDK 8
- Dotnet 8
- Python3
- npm

### Capabilities:
| Env              | Path                                |
|------------------|-------------------------------------|
| curl             | /usr/bin/curl                       |
| dotnet           | /usr/lib/dotnet/sdk                 |
| git              | /usr/bin/git                        |
| JAVA_HOME_8_X64  | /usr/lib/jvm/java-8-openjdk-amd64   |
| JAVA_HOME_11_X64 | /usr/lib/jvm/java-11-openjdk-amd64  |
| JAVA_HOME_17_X64 | /usr/lib/jvm/java-17-openjdk-amd64  |
| python3          | /usr/bin/python3                    |
| node.js          | /usr/bin/nodejs                     |
| npm              | /usr/bin/npm                     |

### Variables:
| **Variablename** | **Description**                                                                                |
|------------------|------------------------------------------------------------------------------------------------|
| AZP_URL          | Azure DevOps URL                                                                               |
| AZP_TOKEN        | Personal Access Token                                                                          |
| AZP_AGENT_NAME   | Name of the Agent                                                                              |
| AZP_POOL         | Azure DevOps Agent Pool Name - If not filled out Agent will be installed to Default Agent Pool |
| AZP_WORK         | Work folder (default = _work)


### Use Docker within Docker container
Please bind-mount Docker socket.

---
---
<div id='AdGuardBuddy'/>

## 🛡️ AdGuard Buddy
AdGuard Buddy is a simple web frontend for managing multiple AdGuard Home instances from a single dashboard.

### Description:
AdGuard Buddy provides a user-friendly interface to centrally manage several AdGuard Home servers. You can monitor statistics, logs, and synchronize settings between instances. One server acts as the master, and its settings can be synced to others. The Sync view shows when servers are out of sync, so you always know the current status.

Project: [AdGuard Buddy on GitHub](https://github.com/chrizzo84/adguard-buddy)
Container Repository: `ghcr.io/chrizzo84/adguard-buddy:latest`

#### Web UI:
`http://[IP]:[PORT:5050]`

#### Environment Variables:
| **Variable Name**                              | **Required** | **Description**                                      | **Default**                |
|------------------------------------------------|--------------|------------------------------------------------------|----------------------------|
| NEXT_PUBLIC_ADGUARD_BUDDY_ENCRYPTION_KEY       | X            | Used to encrypt/decrypt AdGuard Home passwords       |                            |
| Web UI Port                                    | X            | Port for the web frontend (external)                 | 5050                       |

#### Support & Issues:
If you encounter any problems, please open an issue directly in the [AdGuard Buddy GitHub project](https://github.com/chrizzo84/adguard-buddy/issues).

<div id='Issues'/>

# ⚠️ Issues: <a name="Issues">
If you have any issues please create new Issue [here](https://github.com/chrizzo84/unraid-templates/issues) with a tag.
For example: [Drone] My Problem or [AzPipeline] My Problem

**Please only open issues here that are directly related to the Unraid App template or similar.**


