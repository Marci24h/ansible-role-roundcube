# ansible-role-roundcube

[![Build Status](https://github.com/systemli/ansible-role-roundcube/workflows/Integration/badge.svg?branch=main)](https://github.com/systemli/ansible-role-roundcube/actions?query=workflow%3AIntegration)

Install and configure Roundcube.
This includes configuration of the Roundcube Getmail and Enigma Plugin.
You can choose a custom skin `larry-custom` that has additional links to accout settings.

## Dependencies

You need to install a web and database server before using this role.
Also, you need to configure the webserver to to deliver vhost `{{ roundcube_domain }}`.

## Role Variables

see `defaults/main.yml`

For the first run, please set `roundcube_enable_installer: true`.
Afterwards, you can run the installer at `{{ roundcube_domain }}/installer`.

## Download

Download latest release with `ansible-galaxy`

$ ansible-galaxy install systemli.roundcube

## Example Playbook

```
- hosts: servers
  roles:
    - { role: systemli.roundcube }
```

## License

GPL

## Author Information

https://www.systemli.org


## Fork
This is a fork of the nice role [systemli/ansible-role-roundcube](https://github.com/systemli/ansible-role-roundcube)
The goal is to keep the role as simple as possible and use it on my webserver for our family members.

The webserver is running multiple php versions and is set up using the following roles:
* geerlingguy.php-versions
* geerlingguy.mysql
* geerlingguy.nginx

These are some changes that have been made:
* removed `mcrypt tasks` Not sure if we need mcrypt because it so not listed in the [REQUIREMENTS](https://github.com/roundcube/roundcubemail/blob/release-1.6/INSTALL)
* removed getmail
* replaced cronjob by systemd service & timer
* managesieve config
* added tags
