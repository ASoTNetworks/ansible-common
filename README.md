# ansible-common

Common roles to be used for setting up and configuring servers.

## Playbooks
| Playbook | Description |
|     ---: | :---        |
| `proxmox-provision-vm.yml` | Provisions a VM from Cloud-init template

## Playbook Documentation
### proxmox-provision-vm.yml
Example command:
```
ansible-playbook -i "localhost" proxmox-provision-vm.yml --extra-vars "node=kvm01-tor api_host=proxmox.local api_user=ansible-user@pve api_password=P@ssw0rd clone=ubuntu-16.04 storage=local vm_id=1000 vm_name=vm1.aseriesoftubez.com vm_disk=200G vm_ram=8192 vm_cores=8 vm_cpu=host vm_cpuunits=1024 vm_mac=11:22:33:44:55:66 vm_bridge=vmbr0 vm_vlan=2 vm_ip4=10.0.0.10/24 vm_gw4=10.0.0.1 vm_ip6=fdab:dead:1337:c0de::1/64 vm_gw6=fe80::feed:dead:beef:cafe vm_username=sysadmin vm_sshkey_file=~/.ssh/id_rsa.pub nameserver=1.1.1.1 search_domain=aseriesoftubez.com"
```
| Variable Name | Function |  Comment |
| ------------- | -------- |  ------- |
| `node` | Node name of the Proxmox machine to provision the vm | |
| `api_host` | Proxmox host to connect to | |
| `api_user` | Proxmox user to login as | |
| `api_password` | Password for the Proxmox user | |
| `clone` | Name of the template to clone | Template must be Cloud-init ready |
| `storage` | Defines which storage to store the VM | |
| `vm_id` | Defines the ID of the VM being provisioned | Must be unique from other VMs currently on the system |
| `vm_name` | Defines the hostname of the VM | The hostname must resolve to the IP address or SSH check will fail |
| `vm_disk` | Defines the disk size of the VM | |
| `vm_ram` | Defines the RAM size in Megabyte | |
| `vm_cores` | Defines number of vCPU cores | |
| `vm_cpu` | Defines the CPU type | Type `host` is recommanded |
| `vm_cpuunits` | Defines the CPU unit | Higher CPU unit have higher priority CPU scaling |
| `vm_mac` | Defines the MAC address of the VM | |
| `vm_bridge` | Defines which bridge device to use | |
| `vm_vlan` | Defines the VLAN to use | |
| `vm_ip4` | Sets the IPv4 address | |
| `vm_gw4` | Sets the IPv4 gateway | |
| `vm_ip6` | Sets the IPv6 address | |
| `vm_gw6` | Sets the IPv6 gateway | |
| `vm_username` | Set the default username of the VM | |
| `vm_sshkey_file` | SSH file location | Such as `~/.ssh/id_rsa.pub ` |
| `nameserver` | Sets DNS resolver address | Such as `1.1.1.1` |
| `search_domain` | Sets the search domain | Such as `aseriesoftubez.com` |
