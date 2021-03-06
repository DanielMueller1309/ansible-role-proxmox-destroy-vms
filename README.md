## DanielMueller1309.proxmox_destroy_vms
### Beschreibung
Stoppe und Lösche alle in den dafür zuständigem Dictionary aufgeführten VMs auf dem Proxmox Host.
- Zu Beginn wird ``cloud-init`` und das ebenfalls benötigte Programm ``proxmoxer`` heruntergelade.
- Danach löscht das Proxmox_Modul die VMs mit vorgegebenen Einstellungen aus dem Dictionary

### Works on:
- [x] Debian (Version 10)
- [ ] Debian (Version 11)

### Variables + Defaults
#Static vars for VMs:
```yml
#static vars for vms:
vm_api_token_id: 'ci4pve' # the token to use the api
vm_api_token_secret: "{{ lookup('keepass', 'ci4pve', 'password') }}" # secret to token id
vm_api_host: 'pve' # hostname of the api host, most same as node
vm_api_user: 'root@pam' # the token to use the api
vm_api_password: 'hallowelt' # the password of the api user f.E. root
```
###### unique VM settings
have to set in ´vms´ list and not in static vars

```yml
vms:
  - vm_name: testvm1 # name of the vm
    vm_vmid: 101 # vm id
    vm_state: 'present' #only can be set here in list not in static area
  - vm_name: testvm2
    vm_vmid: 102
    vm_state: 'present'
  - vm_name: testvm3
    vm_vmid: 103
    vm_state: 'absent'
```

