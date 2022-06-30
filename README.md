## Ansible Role: Wazuh-Agent

Ansible role to setup & manage Wazuh-Agent
Some of the highlighting features are:-

  - Setup wazuh agent
  - Enabling FIM over server
  - Enabling user audit informatrion gathering setup over node
  - Enabling system check over servers home directory.
  - Configure N number of aplication in wazuh agent for log aggregation 
 

### Supported OS
- Ubuntu 18 
- Ubuntu 20
- Ubuntu 22

### Requirements

**No third party requirement is needed by this role**

### Roles Variables

Roles variables are categorized into two divisions i.e. Mandatory and Optional.

#### Mandatory Variables

|**Variables**|**Default Values**|**Possible Values**|**Type**|**Description**|
|-------------|------------------|-------------------|--------|---------------|
| WazuhManagerIp | None | Your managers private or public IP address | string | Link agent to manager  |

```
Note: It is recommended to enter private ip in WazuhManagerIp  Variable
```


#### Optional Variables

|**Variables**|**Default Values**|**Possible Values**|**Type**|**Description**|
|-------------|------------------|-------------------|--------|---------------|
| UserAudit | true | <ul><li>true</li><li>false</li></ul> | boolean  | To gather user audit information |
| HomeDirectoryCheck | true | <ul><li>true</li><li>false</li></ul> | boolean | To Check the Home directory|
| AggregationPermission | true | <ul><li>true</li><li>false</li></ul> | boolean | To get application data shipped to manager |
| log_aggregation | None | <ul><li>LogFormat: "apache"</li><li>destination: "/var/log/apache2/error.log"</li></ul> | String | You can add multiple apploication name and its path|



### Usage

The inventory for wazuh_agent role should look like this:-

```ini
[WazuhAgent]
node-1 ansible_host=3.83.154.91

[WazuhAgent:vars]
ansible_ssh_user=ubuntu
```


An example playbook should look like this:-

```yaml
---
- name: wazuh
  hosts: all
  become_user: root
  roles:
   - { role: wazuh_agent }
```

and for running the ansible role, we will use ansible cli.

```shell
ansible-playbook -i tests/inventory tests/test.yml
```
## Authors

**[Varghese Kurian](varghese.palamoottil@opstree.com)**
