# Nutanix Role to manage the CMSP service within Prism Central

This Ansible role enables MSP (Micro Service Platform) Prism Central. Nutanix Microservices Infrastructure (sometimes referred to as MSP) provides a common framework and services to deploy the container-based services associated with Prism Central based components like Flow Virtual Networking and Objects. It deploys services like Identity and Access Management (IAM), Load Balancing (LB), and Virtual Private Networking (VPN). Such services are packaged in containers as microservices and the control plane for the microservices platform enables microservices infrastructure. MSP is enabled by default on PC.2022.9.x but needs to be enabled on any prior release, once enabled MSP cannot be disabled. For further details please refer to https://portal.nutanix.com/page/documents/details?targetId=Prism-Central-Guide:mul-cmsp-overview-pc-c.html 

> NOTE: Please be sure to read the MSP deployment guide and pre-requisites before enabling this feature. 

## Role Variables

| Variable                     | Required | Default                        | Choices                                                                         | Comments                                                                                                                                           |
|------------------------------|----------|--------------------------------|---------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| nutanix_host                 | yes      |                                |                                                                                 | The IP address or FQDN for the Prism (Element or Central) to which you want to connect.                                                            |
| nutanix_username             | yes      |                                |                                                                                 | A valid username with appropriate rights to access the Nutanix API.                                                                                |
| nutanix_password             | yes      |                                |                                                                                 | A valid password for the supplied username.                                                                                                        |
| nutanix_port                 | no       | 9440                           |                                                                                 | The Prism TCP port.                                                                                                                                |
| validate_certs               | no       | no                             | yes / no                                                                        | Whether to check if Prism UI certificates are valid.                                                                                               |
| enable_cmsp                  | no       | no                             | yes / no                                                                        | Whether to enable CMSP or not.                                                                                                                     |
| cmsp_domain_name             | no       | prism-central.cluster.local    |                                                                                 |                                                                                                                                                    |
| cmsp_network_default_gateway | no       | 192.168.5.1                    |                                                                                 |                                                                                                                                                    |
| cmsp_network_type            | no       | kPrivateNetwork                |                                                                                 |                                                                                                                                                    |
| cmsp_subnet_mask             | no       | 255.255.255.0                  |                                                                                 |                                                                                                                                                    |
| cmsp_platform_ip_block_list  | no       | ["192.168.5.2 192.168.5.64", ] |                                                                                 |                                                                                                                                                    |

## Dependencies

- grdavies.nutanix_role_nutanix_init_api

## Example Playbook

```
- hosts: localhost
  gather_facts: false
  roles:
    - role: grdavies.role_nutanix_pc_svc_cmsp
  vars:
    nutanix_host: 10.38.185.37
    nutanix_password: admin
    nutanix_username: nx2Tech165!
    enable_cmsp: yes
```

## License

See LICENSE.md

## Author Information

Ross Davies
