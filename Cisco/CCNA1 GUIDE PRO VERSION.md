# DOPORUČUJI SOUBOR STÁHNOUT A OTEVŘÍT V OBSIDIANU NEBO JINÉM PROGRAMU PRO .MD FILY!!

- subnety musí jítt velikostí sestupně
	- pokud ti 2 vyšly se stejnou velikostí, jeden udělej větši
- loopback bude nejmenší subnet (čili poslední)
- pozorně sleduj zadaní
- do zápisu každého subnetu napiš: Gateway (router), Broadcast (nejvysšší adresa), Id (nula) a rozsah uživatelských ip adres (použitelných)

# POČTY
**SUB1/2**
- K poctu zadanych zarizeni pricti 2 (ID, Broadcast) a pocet sitovych zarizeni na siti (routery, switchy)
- Zaokrouhli cislo na cislo ktere je mocninou 2
	- 1 = 2^0
	- 2 = 2^1
	- 4 = 2^2
	- 8 = 2^3
	- 16 = 2^4
	- 32 = 2^5
	- 64 = 2^6
	- 128 = 2^7
	- 256 = 2^8
- Pouzij cislo kterym mocnis (to jest: 0,1,2,3,4,5,6,7,8) to je pocet nul v binarnim zapisu masky
	- napriklad pro cislo 5 = 11111111.11111111.11111111.11100000
	- 8 jednicek = 255
	- Jendicky preved na dvojky a umocni umistenim v poradi
		- To jest (posledni okta) 2^7 + 2^6 + 2^5 = 224
		- Finalni maska bude 255.255.255.224 (pro pocet 32 zarizeni)
Stejne pokracuj u SUB2
**LOOPBACK**
- Spocitej si pocet routeru na siti a pokracuj stejne jako u ostanich subnetu

- - -

# KONFIGURACE
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
	`dns-server [ip of dns server]`
	`exit`
`ip dhcp pool [input name of subnet 2]`
	`network [id of desired subnet] [mask of desired subnet]`
	`default-router [ip of router on desired subnet]`
	`dns-server [ip of dns server]`
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
`copy startup-config tftp:`
	`[input ip of server]`
	`[input name]`

- - -

# common problems and their troubleshooting
bro proste si zkontroluj ze si spravne zadal ipiny a masky
obcas pomaha vypnout a zapnout dhcp na pocitacich, aby si natahali nove ip adresy, router je totiz uplne blby a nedokaze poslat packet ktery rika "hej, novy config tady"

- - -

**changelog**
22/05.00 - added dhcp exclude on second subnet
22/05.01 - changed loopback number to 0 (cuz yuh)
22/05.02 - fixed secret on router ssh
22/05.10 - fixed switch config - was missing default-router
9/06.00 - pridano pocitani
9/06.01 - added dns server config for dhcp
10/06.00 - beautified ✨