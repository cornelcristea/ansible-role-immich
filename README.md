# Ansible Role: Immich

## Description

Ansible role to deploy **Immich** as docker containers, to have a self-hosted photo and video management solution.

## Requirements

* Docker (must be installed on the target hosts)

## Installation

```bash
ansible-galaxy install cornelcristea.immich
```

## Variables

The role uses the following variables:

| Name | Description | Default |
|---------|-------------|---------|
| `immich_data_volume` | Path for persisting data | `/opt/immich/data` |
| `immich_version` | Version of docker image | *check defaults* |
| `immich_postgres_version` | PostgreSQL version with pgvector extension | *check defaults* |
| `immich_valkey_version` | Valkey (redis-compatible) version | *check defaults* |
| `immich_port` | Web interface port | `2283` |
| `immich_timezone` | Timezone for application | `UTC` |
| `immich_db_name` | Database name | `immich_db` |
| `immich_db_username` | Database username | `dbuser` |
| `immich_db_password` | Database password | `dbpass` |

## Playbook example

```yaml
- name: Deploy Immich
  hosts: servers
  gather_facts: true
  vars:
    immich_db_name: PostgreSQL
  roles:
    - cornelcristea.immich
```

## How to contribute

We welcome contributions! Here’s how you can help improve this role:

1. **Fork the repository**    
  Click the `Fork` button at the top of the repository.

2. **Clone your fork locally**

  ```bash
  git clone https://github.com/cornelcristea/ansible-role-immich.git
  cd ansible-role-immich
  ```

3. **Create a new branch**

  ```bash
  git checkout -b my-feature-branch
  ```

  * Make your changes following Ansible best practices.
  * Add or update tests if applicable.
  * Update the README for any new variables or features.
  * Test your changes:
```bash
ansible-playbook -i test/inventory test/test.yml 
```
 * Run molecule test:
```bash
molecule test
```

4. **Commit and push your changes**

  ```bash
  git add .
  git commit -m "Add feature XYZ"
  git push origin my-feature-branch
  ```

5. **Open a Pull Request (PR)**   
Submit a PR from your branch. Include a clear description of your changes and why they’re needed.

**We appreciate your contributions!**
