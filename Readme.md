# HC

:warning: WIP project :warning:

## Required

Those roles require RedHat like OS
<!---
Disable ipv6
=> /etc/sysctl.conf

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1

apply:
sysctl -p
-->

## Steps for deploy kubernetes

1. Configure ansible locally
2. Copy your SSH public key into remote ~/.ssh/authorized_keys server user homepath (ssh-copy-id)
3. Set your server IP/Hostname(if DNS set) into hosts file under [k8s_masters]/[k8s_nodes] section
4. Modify roles/kubernetes/templates/hosts.j2 to match your hostname
5. Modify ansible.cfg and set your private_key_file path
6. Modify metallb_service_range in defaults/main.yml and uncomment shell part of "Initialyze kubernetes on master (~5 min)" in tasks/kubernetes.yml if you want to set a specify network/service cidr
7. Run this ansible playbook
`ansible-playbook playbook.yml -i hosts`
