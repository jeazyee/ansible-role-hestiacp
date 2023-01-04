Ansible Role HestiaCP<br>[![Build Status](https://app.travis-ci.com/jeazyee/ansible-role-hestiacp.svg?branch=master)](https://app.travis-ci.com/jeazyee/ansible-role-hestiacp)
=========

This ansible role lets you install hestiacp, add desired php versions, and create a hostname certificate in one rush. 

For more informations about hestiacp head over to the awesome guys at <a href="https://github.com/hestiacp/hestiacp"> hestiacp/hestiacp</a>.

Contents
-----------
- [Requirements](#requirements)
- [Role Variables](#role-variables)
- [Dependencies](#dependencies)
- [Example Playbook](#example-playbook)
- [License](#license)
- [Author Information](#author-information)

Requirements
------------
No special requirements.

The requirements for the hosts are like those of hestiacp. You can find the requirements for the hosts on <a href="https://www.hestiacp.com">the project homepage</a>.

Role Variables
--------------
Configurations as in defaults/main.yml

    # hestia admin configs
    # recommended to put this into vaul.yml of host_vars or group_vars
    # Initial details of hestiacp admin user
    hestia_admin_mail: admin@example.com
    hestia_admin_pw: P@ssword123

    # Install flags for hestiacp install script
    # values 'yes' or 'no'
    hestia_install_flags: 
      apache: 'no'
      phpfpm: 'yes'
      multiphp: 'no'
      vsftpd: 'yes'
      proftpd: 'no'
      named: 'no'
      mysql: 'yes'
      postgresql: 'no'
      exim: 'no'
      dovecot: 'no'
      sieve: 'no'
      clamav: 'no'
      spamassassin: 'no'
      iptables: 'yes'
      fail2ban: 'yes'
      quota: 'yes'
      api: 'yes'
      port: '8083'
      lang: 'en'

    # Install additional php versions.
    # Checks if it is already is installed, so you can list all desired php versions.
    # Only gets installed when installer_flag is set to: --multiplephp no
    hestia_additional_php:
      - 7.4
      - 8.0
      - 8.1

    # should hestia generate a letsencrypt cert for the hostname
    hestia_generate_ssl: false

Dependencies
------------

None.

Example Playbook
----------------

Nothing special when it comes to usage of this role. Make sure you have overwritten the variables of defaults/main.yml with your desired values.

    - hosts: servers
      roles:
         - { role: jeazyee.hestiacp }

License
-------

The license of Hestia Control Panel applies. The Hestia Control Panel is licensed under GPL v3 license, and is based on the VestaCP project.

Author Information
------------------

This Ansible Role was created in 2021 by <a href="https://github.com/jeazyee">Jitendra Bodmann</a>, owner of <a href="https://www.wedima.de">wedima</a>.
