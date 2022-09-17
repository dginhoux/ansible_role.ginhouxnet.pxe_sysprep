Ansible Role : dginhoux.pxe_sysprep
=========

This ansible role create sysprep files for autoinstall linux distrib, it currently support :
-- debian stretch, buster, bullseye
-- fedora 32, 33, 34, 35, 36
-- centos 7, 8

Adding distributions and versions is very easier, because each version has two templates, one for bios boot setup and on for uefi64 boot setup.
There a list with sysprep file to create, one for entry for each machine.



Requirements
------------

This role require a supported platform defined in `meta/main.yml`.
It will skip node with unsupported platform ; this behaviour can be bypassed by settings this variable `asserts_bypass=True`.


Role Variables
--------------

Necessary variables are defined on `defaults/main.yml`



Dependencies
------------

none


Example Playbook
----------------



License
-------

BSD


Author Information
------------------

https://github.com/dginhoux/
