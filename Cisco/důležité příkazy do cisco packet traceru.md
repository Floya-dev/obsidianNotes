realne situace - dostanu switch, nastavim hesla, vzdaleny pristup, odnesu do serverovny, pak si s tim hraju na dalku

==hostname *input*== // set hostname, musíš být v global configuration mode
==show ip interface brief== // ukáže ti jaké máš porty na routeru, musíš být v privileged exec mode
==show running-config== // ukaze stare prikazy co si zadal // musis byt v priviliged exec modu
==interface *port*== // začneš configurovat port, musíš být v global configuration mode
==ip address *ip* *mask*== // setupne ip dresu pro GT na určitém portu, musíš být v interface configu
==no shutdown== // zapne port, musíš být v interface configu
==ip dhcp pool *name*== // config dhcp // musíš být v global configuration mode
==ip dhcp excluded-address *ip*== // exclude ip / v global config
==ip dhcp excluded-address *ip start* *ip end*== // exclude ip range // global config
==dns-server *dns server ip*== // nastaví ip pro dns server // v dhcp config
==network *ip* *mask*== // nastaví na jaké síti (podle ip=id sítě) bude dhcp zaplé
==default-router *ip*== // nastaví default router pro dhcp (ip = router id) // dhcp config

==username *name* secret *pass*== // nastavi uzivatele a jeho heslo // global config
==enable secret *pass*== // zapne hesla // global config

==line console 0== // zacnes configovat console port // global config
==login local== // zapnes vyzadovani hesla na potru // v port configu

==interface vlan 1== // config vlan 1 na switchi // global config
==ip address *ip* *mask*== // pridam na vlan ipinu // interface config

**telnet enable**
==line vty *num 0-16*== // config virtual terminal // global config
==login local== // zapne vyzadovani hesla // v port configu

==write== // zapise running-config do do startup-configu // v priviliged exec mode
==show startup-config== // ukaze startup-config // v priviliged exec mode

==copy startup-config tftp:== // zkopiruje startup-config na server // v priviliged exec mode

==show vlan brief== // ukaze vlany
![[MicrosoftTeams-image.png]]

ssh enable
switch
- hostname
- interface vlan
- no shutdown
- show ip interface brief
- zaheslovat secret
- udelat uzivatele - username cisco secret cisco
- pro ssh potrebujes domenu a certifikat (hostname a domena)
- ip domain-name 
- line console0
- login local
- exit
- line vty 0 15
- login local
- exit
- ted to bude vyzadovat user a heslo kdyz resetnes tty
- configure terminal
- crypto key generate rsa
- aspon 1024 bits
- show crypto key mypubkey rsa
- line vty 0 15
- transport input ssh
