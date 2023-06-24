---
id: sd6aa2573ij3x7hob3oify5
title: 9-Laboratorio - Enrutamiento entre VLAN
desc: ''
updated: 1686154053236
created: 1684524158131
---

- S1

    > Configuración global.

    - `vlan <vlan number>`
    - `name <vlan name>`

    - `int range fastEthernet 0/<start>-<end>`
    - `switchport mode access`
    - `switchport access vlan <vlan number>`

    - `int gigabitEthernet 0/1`
    - `switchport mode trunk`
    - `switchport trunk native vlan 88`
    - `switchport trunk allowed vlan 10,20,30,99`

    - `int vlan 99`
    - `ip add 172.25.99.10 255.255.255.0`
    - `ip default-gateway 172.25.99.1`

- `R1`

    - `int g 0/0`
    - `no shutdown`
    - `ip add 172.25.25.2 255.255.255.252`
    - `int g 0/0.<vlan number>`
    - `encapsulation dot1Q <vlan number>`
    - `ip add <ip> <mask>`
