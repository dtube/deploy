# Dtube Deployment Ansible Scripts

This repo is currently in live usage and *aims* to follow Ansible best practice for rapid dtube node deployment.

Inventory file looks like the below for production deployment

    [saver]
    saver1.d.tube
    [upldr]
    upldr[1:6].d.tube
    [upldrg]
    upldrg[1:4].d.tube
    [snap]
    snap1.d.tube
    [zabbix]

All hosts should be running debian 9 (Stretch) excluding upldrg hosts which run debian 8 (Jessie)


Nodes can be provisioned using:

    ansible-playbook -i TARGET ./site.yaml -b --become-method=su -K 

Then by entering the root password for the host.

Target can be replaced with an intermediary inventory file for situations where numerous machines are being built. 

The host is then ready to be managed using

  ansible-playbook ./site.yaml -b

This will use the 'dabbott' to login, sudo to root and then perform actions as needed.
