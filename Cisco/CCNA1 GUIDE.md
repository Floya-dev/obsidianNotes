- subnety musi jit velikostne sestupne
	- pokud ti 2 vysli se stejnou velikosti, jeden udelej vetsi, jinak ti to fungovat nebude
- loopback bude nejmensi subnet (cili posledni)
- pozorne sleduje zadani
- do zapisu kazdeho subnetu napis: Gateway (router), Broadcast (nejvyssi adresa), Id (nula) a rozsah uzivatelsky ip adres (pouzitelnych)
**ROUTER**
`enable`
`configure terminal`
`hostname [input]`
`interface [input port 1]`
	`ip address [ip of router on that subnet] [mask]`
	`no shutdown`
	`exit`
`interface [input port 2]`
	`ip address [ip of router on that subnet] [mask]`
	`no shutdown`
	`exit`
`interface loopback 0`
	`ip address [ip of router on that subnet] [mask]`
	`no shutdown`
	`exit`
`ip dhcp pool [input name of subnet 1]`
	`network [id of desired subnet] [mask of desired subnet]`
	`default-router [ip of router on desired subnet]`
	`exit`
`ip dhcp pool [input name of subnet 2]`
	`network [id of desired subnet] [mask of desired subnet]`
	`default-router [ip of router on desired subnet]`
	`exit`
`ip dhcp exclude-address [ip of server]`
`ip dhcp exclude-address [ip of router]`
`ip dhcp exclude-address [start of ip range] [end of ip range]`
`ip dhcp exclude-address [ip of router on 2nd subnet]`
`ip dhcp exclude-address [start of ip range on 2nd subnet] [end of ip range]`
`username [input] secret [input]`
`enable secret [input]`
`ip domain-name [input domain, for example: cisco.com]`
`line console 0`
	`login local`
	`exit`
`crypto key generate rsa`
	`1024`
`line vty 0 15`
	`login local`
	`transport input ssh`
	`exit`
`exit`
`write`
`copy startup-config tftp:`
	`[input ip of server]`
	`[input name]`

**SWITCH**
`enable`
`configure terminal`
`hostname [input]`
`interface vlan 1`
	`ip address [ip for switch on subnet] [mask of subnet]`
	`no shutdown`
	`exit`
`ip default-gateway [input router ip on that subnet]`
`username [input] secret [password]`
`enable secret [password]`
`ip domain-name [input domain, for example: cisco.com]`
`line console 0`
	`login local`
	`exit`
`line vty 0 15`
	`login local`
	`exit`
`crypto key generate rsa`
	`1024`
`line vty 0 15`
	`transport input ssh`
	`exit`
`exit`
`write`
``copy startup-config tftp:`
	`[input ip of server]`
	`[input name]`

**common problems and their troubleshooting**
bro proste si zkontroluj ze si spravne zadal ipiny a masky


**changelog**
22/05.00 - added dhcp exclude on second subnet
22/05.01 - changed loopback number to 0 (cuz yuh)
22/05.02 - fixed secret on router ssh
22/05.10 - fixed switch config - was missing default-router
