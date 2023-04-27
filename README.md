# ROLE dginhoux.pxe_sysprep



## DESCRIPTION

This ansible role create sysprep files for autoinstall linux distrib, it currently support :
* debian 
** stretch
** buster
** bullseye
* fedora
** 32
** 33
** 34
** 35
** 36
* centos
** 7
**8

Adding distributions and versions is very easier, because each version has two templates, one for bios boot setup and on for uefi64 boot setup.<br />
There a list with sysprep file to create, one for entry for each machine.<br />
<br />
NOTE : all provided syspreps files set root password at `root`

## REQUIREMENTS

#### SUPPORTED PLATFORMS

This role require a supported platform.<br />
It will skip process with unsupported platform to avoid any compatibility problem.<br />
This behaviour can be bypassed by settings the following variable `asserts_bypass=True`.

| Platform | Versions |
|----------|----------|
| Debian | buster, bullseye |
| Fedora | 33, 34, 35, 36, 37, 38 |
| EL | 7, 8 |

#### ANSIBLE VERSION

Ansible >= 2.13

#### DEPENDENCIES

None.



## INSTALLATION

#### ANSIBLE GALAXY

```shell
ansible-galaxy install dginhoux.pxe_sysprep
```
#### GIT

```shell
git clone https://github.com/dginhoux/ansible_role.pxe_sysprep dginhoux.pxe_sysprep
```


## USAGE

#### EXAMPLE PLAYBOOK

```yaml
- hosts: all
  roles:
    - name: start role dginhoux.pxe_sysprep
      ansible.builtin.include_role:
        name: dginhoux.pxe_sysprep
```


## VARIABLES

#### DEFAULT VARIABLES

Defaults variables defined in `defaults/main.yml` : 

```yaml
---
pxe_deploy_configure_action: generate
# pxe_deploy_configure_action: cleanup

pxe_deploy_menu_folder: /srv/tftp/menu
pxe_deploy_sysprep_folder: /srv/tftp/sysprep
pxe_deploy_tftp_address: pxe.infra.ginhoux.net

pxe_deploy_cleanup: "no"

pxe_deploy:
  - name: srv-swarm-manager1.infra.ginhoux.net
    os: Fedora.36
    partitionning: nolvm-single
    filesystem: ext4
    filesystem_boot: ext2
    vgname: vg0
    disk: sda
    domain: infra.ginhoux.net
    rootpwd: root
    locale: en_US.UTF-8
    kblayout: fr
    timezone: Europe/Paris

pxe_deploy_debian_stretch_mirror_hostname: ftp.fr.debian.org
pxe_deploy_debian_stretch_mirror_directory: /debian
pxe_deploy_debian_stretch_mirror_proxy: ""

pxe_deploy_debian_buster_mirror_hostname: ftp.fr.debian.org
pxe_deploy_debian_buster_mirror_directory: /debian
pxe_deploy_debian_buster_mirror_proxy: ""

pxe_deploy_debian_bullseye_mirror_hostname: ftp.fr.debian.org
pxe_deploy_debian_bullseye_mirror_directory: /debian
pxe_deploy_debian_bullseye_mirror_proxy: ""

pxe_deploy_centos_7_mirror_url: http://mirror.centos.org/centos-7/7/os/x86_64/
pxe_deploy_centos_8_mirror_url: http://mirror.centos.org/centos-8/8/BaseOS/x86_64/os/

pxe_deploy_fedora_32_mirror_url: https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/32/Server/x86_64/os/
pxe_deploy_fedora_33_mirror_url: https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/33/Server/x86_64/os/
pxe_deploy_fedora_34_mirror_url: https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/34/Server/x86_64/os/
pxe_deploy_fedora_35_mirror_url: https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/35/Server/x86_64/os/
pxe_deploy_fedora_36_mirror_url: https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/36/Server/x86_64/os/
```

#### DEFAULT OS SPECIFIC VARIABLES

Those variables files are located in `vars/*.yml` are used to handle OS differences.<br />
One of theses is loaded dynamically during role runtime using the `include_vars` module and set OS specifics variable's.

`NOT USED BY THIS ROLE`



## AUTHOR

Dany GINHOUX - https://github.com/dginhoux



## LICENSE

MIT
