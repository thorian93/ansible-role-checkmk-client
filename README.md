# Ansible Role: Checkmk Client

 This role sets up the Checkmk Agent on Debian/Ubuntu, RHEL/CentOS and Fedora servers. 

[![Ansible Role: Webserver](https://img.shields.io/ansible/role/55241?style=flat-square)](https://galaxy.ansible.com/CaffeineCollective/ansible-role-checkmk-client)
[![Ansible Role: Webserver](https://img.shields.io/ansible/quality/55241?style=flat-square)](https://galaxy.ansible.com/CaffeineCollective/ansible-role-checkmk-client)
[![Ansible Role: Webserver](https://img.shields.io/ansible/role/d/55241?style=flat-square)](https://galaxy.ansible.com/CaffeineCollective/ansible-role-checkmk-client)

## Here be Dragons!

Actually no dragons here (yet).

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

    - hosts: foobar
      roles:
        - role: ansible-role-checkmk-client
          become: yes

## Role Variables

Available variables are listed below, along with default values (see `vars/Debian.yml` and `vars/RedHat.yml`):

    checkmk_client_url: "https://{{ inventory_hostname }}"

The base URL of the monitoring server on which the client will be monitored.

    checkmk_client_site: 'main'

The Checkmk site in which the client will be monitored.

    checkmk_client_version: '2.0.0p5'

The client version to install. This has to match the server version.

    checkmk_client_plugins_builtin:
      - name: $NAME
        interval: $INTERVAL

A list of plugins and their execution interval. See `defaults/main.yml` for the builtin list.

## Dependencies

None.

## OS Compatibility

This role ensures that it is not used against unsupported or untested operating systems by checking, if the right distribution name and major version number are present in a dedicated variable named like `<role-name>_stable_os`. You can find the variable in the role's default variable file at `defaults/main.yml`:

    role_stable_os:
      - Debian 10
      - Ubuntu 18
      - CentOS 7
      - Fedora 30

If the combination of distribution and major version number do not match the target system, the role will fail. To allow the role to work add the distribution name and major version name to that variable and you are good to go. But please test the new combination first!

Kudos to [HarryHarcourt](https://github.com/HarryHarcourt) for this idea!

## Example Playbook

    ---
    - name: "Run role."
      hosts: all
      become: yes
      roles:
        - ansible-role-checkmk-client

## Contributing

Please feel free to open issues if you find any bugs, problems or if you see room for improvement. Also feel free to contact me anytime if you want to ask or discuss something.

## Disclaimer

This role is provided AS IS and I can and will not guarantee that the role works as intended, nor can I be accountable for any damage or misconfiguration done by this role. Study the role thoroughly before using it.

## License

MIT

## Author Information

This role was created in 2021 by [Thorian93](http://thorian93.de/).
