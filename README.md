# README

An Ansible role for setting up a minimal certificate authority (CA) with a selfsigned root certificate.

An example play:
```yaml
- hosts: ca
  become: yes  
  
  vars:
    root_key_password_file: '{{ inventory_dir ~ "/secrets/ca/root-key-password" }}'
 
  roles:
  - role: ./ansible-role-ca
    vars:
      ca_dir: /usr/local/share/ca/1
      key_password_file: '{{ root_key_password_file }}'
      subject:
        country_code: '{{ country_code }}'
        locality_name: '{{ locality_name }}'
        organization_name: '{{ organization_name }}'
        organizational_unit_name: '{{ organizational_unit_name }}'
        email_address: '{{ ca_email }}'
        common_name: 'VPN CA 1'
  
```
