Role Name
=========

This role enrolls nvm on a machine and installs a npm module for the desired nodeJS version.

Requirements
------------

None.

Role Variables
--------------


nvm_user: "jenkins"
nvm_working_path: "/var/lib/jenkins/"
nvm_dest: "/var/lib/jenkins/.nvm"
nvm_group: "jenkins"
nvm_version: "v0.33.2"
nvm_node_version: "6.11.1"
nvm_npm_pkgs:
  - pkg: npm
    version: "3.10.10"

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: mare.nvm, nvm_user: jenkins, nvm_working_path: ... }


Author Information
------------------

Martin Reinhardt
