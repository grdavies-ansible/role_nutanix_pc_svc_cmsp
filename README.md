# Nutanix Role to manage the CMSP service within Prism Central

This Ansible role enables MSP (Micro Service Platform) Prism Central. Nutanix Microservices Infrastructure (sometimes referred to as MSP) provides a common framework and services to deploy the container-based services associated with Prism Central based components like Flow Virtual Networking and Objects. It deploys services like Identity and Access Management (IAM), Load Balancing (LB), and Virtual Private Networking (VPN). Such services are packaged in containers as microservices and the control plane for the microservices platform enables microservices infrastructure. MSP is enabled by default on PC.2022.9.x but needs to be enabled on any prior release, once enabled MSP cannot be disabled. For further details please refer to https://portal.nutanix.com/page/documents/details?targetId=Prism-Central-Guide:mul-cmsp-overview-pc-c.html 

> NOTE: Please be sure to read the MSP deployment guide and pre-requisites before enabling this feature. 

## Role Variables

| Variable                                      | Required | Default                        | Choices                                                                         | Comments                                                                                                                                           |
|-----------------------------------------------|----------|--------------------------------|---------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| role_nutanix_pc_svc_cmsp_host                 | yes      |                                |                                                                                 | The IP address or FQDN for the Prism (Element or Central) to which you want to connect.                                                            |
| role_nutanix_pc_svc_cmsp_host_username        | yes      |                                |                                                                                 | A valid username with appropriate rights to access the Nutanix API.                                                                                |
| role_nutanix_pc_svc_cmsp_host_password        | yes      |                                |                                                                                 | A valid password for the supplied username.                                                                                                        |
| role_nutanix_pc_svc_cmsp_host_port            | no       | 9440                           |                                                                                 | The Prism TCP port.                                                                                                                                |
| role_nutanix_pc_svc_cmsp_host_validate_certs  | no       | no                             | yes / no                                                                        | Whether to check if Prism UI certificates are valid.                                                                                               |
| role_nutanix_pc_svc_cmsp_enable               | no       | no                             | yes / no                                                                        | Whether to enable CMSP or not.                                                                                                                     |
| role_nutanix_pc_svc_cmsp_domain_name          | no       | prism-central.cluster.local    |                                                                                 |                                                                                                                                                    |
| role_nutanix_pc_svc_cmsp_network_type         | no       | kPrivateNetwork                |                                                                                 |                                                                                                                                                    |
| role_nutanix_pc_svc_cmsp_default_gateway      | no       | 192.168.5.1                    |                                                                                 |                                                                                                                                                    |
| role_nutanix_pc_svc_cmsp_subnet_mask          | no       | 255.255.255.0                  |                                                                                 |                                                                                                                                                    |
| role_nutanix_pc_svc_cmsp_ip_block_list        | no       | ["192.168.5.2 192.168.5.64", ] |                                                                                 |                                                                                                                                                    |

## Dependencies

- grdavies.nutanix_role_nutanix_init_api
- grdavies.role_nutanix_prism_monitor_task

## Example Playbook

```
- hosts: localhost
  gather_facts: false
  roles:
    - role: grdavies.role_nutanix_pc_svc_cmsp
  vars:
    role_nutanix_pc_svc_cmsp_host: 10.38.185.37
    role_nutanix_pc_svc_cmsp_host_password: admin
    role_nutanix_pc_svc_cmsp_host_username: nx2Tech165!
    role_nutanix_pc_svc_cmsp_enable: true
```

## License

See LICENSE.md

## Author Information

Ross Davies
