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
New-VirtualPortGroup -VirtualSwitch 'VM WAN' -Name ‘WAN’
```

## Hosts:

Make VM to serve as cloneable targets: 
1. One associated with LAN
2. One associated with WAN

Make new LAN host:
```
new-vm -VM (name of LAN clone target) -Name hostX -VMHost (ESXi hostname)
```
Make new WAN host:

*NOTE:* ```new-networkadapter``` command many need ```-MacAddress '00:50:56:a1:00:00'``` or similar. 

```
new-vm -VM (name of WAN clone target) -Name hostX -VMHost (ESXi hostname)

Get-VM hostX | New-NetworkAdapter -NetworkName "Lan 1" -WakeOnLan -StartConnected -Type e1000
