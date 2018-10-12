# Ansible Role: BIG-IQ Register DCD

Performs a series of steps needed to register a BIG-IQ provisioned as a Data Collection
Device (DCD) to a BIG-IQ provisioned as a Configuration Management (CM) device.

## Requirements

None.

## Role Variables

Available variables are listed below. For their default values, see `defaults/main.yml`:

    register_dcd_cm_server: localhost
    register_dcd_cm_server_port: 443
    register_dcd_cm_user: admin
    register_dcd_cm_password: secret
    register_dcd_cm_validate_certs: false
    register_dcd_cm_transport: rest
    register_dcd_cm_timeout: 120

Establishes initial connection to your BIG-IQ. These values are substituted into
your ``provider`` module parameter. These values should be the connection parameters
for the **CM BIG-IP** device.

    register_dcd_dcd_user: admin
    
Username to use when logging in to the DCD device. This value is sent to the CM device
during DCD node registration. The CM needs to communicate with the DCD device to register
it. This credential is required to do that.

    register_dcd_dcd_password: secret

Password of the user used to connect to DCD device. This value is sent to the CM device
during DCD node registration. The CM needs to communicate with the DCD device to register
it. This credential is required to do that.

## Dependencies

None.

## Example Playbook

    - name: Register DCD to CM BIG-IQ
      hosts: dcds
      vars_files:
        - vars/main.yml
      roles:
        - { role: f5devcentral.register_dcd }

*Inside `vars/main.yml`*:

    f5_server: bigiq-cm01.domain.org
    f5_password: secret

## License

Apache

## Author Information

This role was created in 2018 by [Tim Rupp](https://github.com/caphrim007).
