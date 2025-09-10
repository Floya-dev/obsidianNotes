1vlan 1 neni nejbezpecnejsi, protoze je prirazena ke kazdemu portu
segmentace site

**virtualni sit**
pouzivame stejnou infrastrukutru, akorat switche a zarizeni dame do jinych VLAN
podle pater, podle pouziti (jeden vlan pro IT, druha vlan pro HR atd.)
kazda ta VLAN ma svoje vlastni ID - 10.0.2.0, 10.0.3.0, 10.0.4.0, daji se subnetovat
az 44 tisic ale primarne se pouziva do 1 tisic
![[Pasted image 20250909135744.png]]

snizujeme napor na sit
vylepsene zabezpeceni
organizace
snizeni nakladu - misto switchu

## typy vlan
default = vlan 1 = defaultni na kazdem zarizeni zapla na portu, not so secure, nejvic proflaknuta, nepouzivej ji, nejde smazat ani prejmenovat, vypni porty
datova = vsechny ostatni
native = fallback vlan
managment = pro spravu sitovich zarizeni, switche, router vlan nema, ssh
voice = pro ip telefony