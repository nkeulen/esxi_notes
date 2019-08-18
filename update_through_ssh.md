# Updating an esxi host through ssh: 

### allow outgoing http requests:
 esxcli network firewall ruleset set -e true -r httpClient

### see list of images:
 esxcli software sources profile list --depot=https://hostupdate.vmware.com/software/VUM/PRODUCTION/main/vmw-depot-index.xml

### dry run: 
 esxcli software profile update -d https://hostupdate.vmware.com/software/VUM/PRODUCTION/main/vmw-depot-index.xml -p ESXi-6.7.0-8169922-standard --dry-run

### update:
 esxcli software profile update -d https://hostupdate.vmware.com/software/VUM/PRODUCTION/main/vmw-depot-index.xml -p ESXi-6.7.0-8169922-standard

### deny outgoing http requests again:
 esxcli network firewall ruleset set -e false -r httpClient

### reboot:
 reboot
