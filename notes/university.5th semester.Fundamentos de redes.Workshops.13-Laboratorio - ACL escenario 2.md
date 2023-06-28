---
id: y7m3vfbqd2m8fhfleaqj5fi
title: 13-Laboratorio - ACL escenario 2
desc: ''
updated: 1687723056515
created: 1686508036530
---

1. Configure la ACL extendida.

	> Configuración global.

	- `RTA`

		- `access-list 199 permit tcp 10.101.117.32 0.0.0.15 10.101.117.0 0.0.0.31 eq telnet`.
		- `access-list 199 permit icmp any any`.

2. Aplique la ACL extendida.

	> Configuración global.

	- `RTA`
		- `int g0/2`.
		- `ip access-group 199 out`.

3. Preguntas de reflexión.

	- ¿Cómo pudo la PCA omitir la lista de acceso 199 y acceder al SWC mediante Telnet?

		La PCA nunca accedió estrictamente a SWC, fue SWB quien lo hizo, es decir, PCA utilizo a SWB como "puente" para acceder a SWC.

	- ¿Qué se podría haber hecho para evitar que la PCA acceda indirectamente al SWC y, al mismo tiempo, permitir el acceso de la PCB al SWC por Telnet?

		Como primer regla de la ACL bloquear el acceso de SWB a SWC.

		- `access-list 199 deny tcp host 10.101.117.34 host 10.101.117.2 eq telnet`.
