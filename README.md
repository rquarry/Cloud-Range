# ESXi-Range

## Networking:

(insert diagram here)

Host-only LAN:
```
New-VirtualVwitch -Name Lan1
New-VirtualPortGroup -VirtualSwitch LAN1 -Name ‘Range LAN 1’
```
Network with WAN to local physical network:
```
New-VirtualVwitch -Name 'VM WAN'
New-VirtualPortGroup -VirtualSwitch 'VM WAN' -Name ‘Range LAN 1’
```

## Hosts:

Make new LAN host:
```
new-vm -VM (name of clone) -Name host1 -VMHost (ESXi hostname)
```

