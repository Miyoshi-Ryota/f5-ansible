.. raw:: html

   <!--
   Copyright 2015-2019 F5 Networks Inc.

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
   -->

Ansible F5
==========


What this fork aims to do
-----------------------------
This fork provides a `bigip_command` module for F5OS-A.

Official module for F5OS, https://github.com/F5Networks/f5-ansible-f5os, does not provide
a `bigip_command` or `f5os_command` or similar module to run simply commands via ssh.

This fork modify the `bigip_command` module to support F5OS-A.


Install from GitHub
----------------------

.. code:: shell
   ansible-galaxy collection install git+https://github.com/Miyoshi-Ryota/f5-ansible.git#ansible_collections/f5networks/f5_modules


Tested situations
---------------------

* F5OS-A 1.5.1
* ansible 2.10.12 and python 3.9.6 in controller

.. code:: yaml
  - name: collect config
    var:
      ansible_user: admin
      ansible_password: secret
      ansible_connection: local
      ansible_network_os: bigip
    f5networks.f5_modules.bigip_command:
      commands:
        - show running-config
      provider:
        password: "{{ ansible_password }}"
        user: "{{ ansible_user }}"
        server: "{{ inventory_hostname }}"
        transport: cli
        server_port: 22
        validate_certs: false
    register: result
    delegate_to: localhost


Copyright
---------

Copyright 2017-2022 F5 Networks Inc.


License
-------

GPL V3
~~~~~~

This License does not grant permission to use the trade names, trademarks, service marks, or product names of the Licensor, except as required for reasonable and customary use in describing the origin of the Work.

See `License`_.
