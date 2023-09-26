# Nutanix Role to upload Prism Central release to Prism Element

This Ansible role uploads a Prism Central software image to a Prism Element cluster that can be used when deploying a new Prism Central instance. 

## Requirements

The following roles need to be installed as they are used within this role;

## Input Variables

| Variable                                  | Required | Default         | Choices                                                                         | Comments                                                                                                                                                                                                                                 |
|-------------------------------------------|----------|-----------------|---------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| role_nutanix_pe_upload_pc_host            | yes      |                 |                                                                                 | The IP address or FQDN for the Prism (Element only) to which you want to connect.                                                                                                                                                        |
| role_nutanix_pe_upload_pc_username        | yes      |                 |                                                                                 | A valid username with appropriate rights to access the Nutanix API.                                                                                                                                                                      |
| role_nutanix_pe_upload_pc_password        | yes      |                 |                                                                                 | A valid password for the supplied username.                                                                                                                                                                                              |
| role_nutanix_pe_upload_pc_port            | no       | 9440            |                                                                                 | The Prism TCP port.                                                                                                                                                                                                                      |
| role_nutanix_pe_upload_pc_validate_certs  | no       | false           | true | false                                                                    | Whether to check if Prism UI certificates are valid.                                                                                                                                                                                     |
| role_nutanix_pe_upload_pc_metadata_path   | yes      |                 |                                                                                 | Local path to a Prism Central metadata file. This file can be sourced form the Nutanix support website in the AOS downloads section.                                                                                                     |
| role_nutanix_pe_upload_pc_binary_path     | no       |                 |                                                                                 | Local path to a Prism Central tar file. This file can be sourced form the Nutanix support website in the AOS downloads section. If this value is not supplied the release will be downloaded from the internet.                          |

## Output Variables

None

## Dependencies

- grdavies.role_nutanix_prism_api,1.1.0

## Example Playbook to upload Prism Central 2023.3 to an AOS cluster

```
- hosts: localhost
  gather_facts: false
  roles:
    - role: grdavies.role_nutanix_pe_upload_pc
  vars:
    role_nutanix_pe_upload_pc_host: 10.38.185.37
    role_nutanix_pe_upload_pc_username: admin
    role_nutanix_pe_upload_pc_password: nx2Tech165!
    role_nutanix_pe_upload_pc_metadata_path: /tmp/generated-pc.2023.3-metadata.json
    role_nutanix_pe_upload_pc_binary_path: /tmp/pc.2023.3.tar
```

## Example Playbook to upload Prism Central 2023.3 to an AOS cluster using only metadata file

This example only provides the Prism Central release metadata file. The Prism Central tar file will be downloaded from the portal.

```
- hosts: localhost
  gather_facts: false
  roles:
    - role: grdavies.role_nutanix_pe_upload_pc
  vars:
    role_nutanix_pe_upload_pc_host: 10.38.185.37
    role_nutanix_pe_upload_pc_username: admin
    role_nutanix_pe_upload_pc_password: nx2Tech165!
    role_nutanix_pe_upload_pc_metadata_path: /tmp/generated-pc.2023.3-metadata.json
```

## License

See LICENSE.md

## Author Information

Ross Davies
