ginhouxnet.pxe_sysprep
=========

This ansible role create sysprep files for autoinstall linux distrib, it currently support :
-- debian stretch, buster, bullseye
-- fedora 32, 33, 34, 35, 36
-- centos 7, 8

Adding distributions and versions is very easier, because each version has two templates, one for bios boot setup and on for uefi64 boot setup.
There a list with sysprep file to create, one for entry for each machine.



Requirements
------------

This ansible role will only run on identified OS defined on meta/main.yml


Role Variables
--------------

View defaults/main.yml 




Dependencies
------------




Example Playbook
----------------



License
-------

BSD


Author Information
------------------

Dany GINHOUX
