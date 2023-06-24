---
id: 4kgaizndlajmi0jbc1tlper
title: 5-Taller - Subnetting sin VLSM
desc: ''
updated: 1686336755232
created: 1682285667013
---

| Clase |              Rango              | Máscara de red | Cantidad de redes | Cantidad de host |
|:-----:|:-------------------------------:|:--------------:|:-----------------:|:----------------:|
|   A   |     0.0.0.0/8 a 127.0.0.0/8     |   255.0.0.0    |       $2^8$       |   $2^{24} - 2$   |
|   B   |  128.0.0.0/16 a 191.255.0.0/16  |  255.255.0.0   |     $2^{16}$      |   $2^{16} - 2$   |
|   C   | 192.0.0.0/24 a 223.255.255.0/24 | 255.255.255.0  |     $2^{24}$      |    $2^8 - 2$     |
|   D   |                                 |                |                   |                  |

1. ¿Cuántas IP de host tiene una red clase A con máscara por defecto?: $2^{24} - 2$

2. ¿Cuántas IP de host tiene una red clase B con máscara por defecto?: $2^{16} - 2$

3. Cuántas IP de host tiene una red clase C con máscara 255.255.255.240

	$$
	255.255.255.11110000
	$$

	Quedan 4 bits disponibles para los hosts $2^4 - 2 = 14$

4. ¿Cuántas IP de host tiene una red clase B con máscara 255.255.255.240?: las mismas que las de arriba ($2^4 - 2 = 14$).

5. ¿Cuál es la IP de red y de broadcast de la IP 192.168.250.25 255.255.255.0?

	- IP de red

		Haciendo la operación AND entre la IP y su máscara tenemos

		$$
		\begin{array}{lllll}
			  &192.&168.&250.&00011001 \\
			  &255.&255.&255.&00000000 \\
			= &192.&168.&250.&00000000
		\end{array}
		$$

	- IP de broadcast: 192.168.250.255

6. ¿Cuál es la IP de red, la primera ip de host, la Última IP de host y la IP de broadcast de la IP 192.168.35.232 255.255.255.0?

	- IP red

		$$
		\begin{array}{lllll}
			  &192.&168.&35. &11101000 \\
			  &255.&255.&255.&00000000 \\
			= &192.&168.&35. &00000000
		\end{array}
		$$

	- Primera IP host: 192.198.35.1
	- Última IP host: 192.198.35.254
	- IP broadcast: 192.198.35.255

7. ¿Cuál es la IP de red, la primera ip de host, la última IP de host y la IP de broadcast de la IP 172.16.59.252 255.255.0.0?

	- IP red

		$$
		\begin{array}{lllll}
			  &172.&16. &00111011.&11111100\\
			  &255.&255.&00000000.&00000000 \\
			= &172.&16. &00000000.&00000000
		\end{array}
		$$

	- Primera IP host: 172.16.0.1
	- Última ip host: 172.16.0.254
	- IP broadcast: 172.16.0.255

8. ¿Cuántas subredes y cuantos hosts puede tener de una red clase C con máscara /28?

	$$
	255.255.255.11110000
	$$

	> Como es clase C tenemos reservado hasta el tercer octeto para redes.

	- Hosts: $2^4 - 2 = 14$
	- Subredes: $2^4 = 16$

9. ¿Cuántas subredes y cuantos hosts puede tener de una red clase C con máscara /30?

	$$
	255.255.255.11111100
	$$

	> Como es clase C tenemos reservado hasta el tercer octeto para redes.

	- Hosts: $2^2 - 2 = 2$
	- Subredes: $2^6 = 64$

10. ¿Cuántas subredes y cuantos hosts puede tener de una red clase B con máscara /21?

	$$
	255.255.11111000.00000000
	$$

	> Como es clase B tenemos reservado hasta el segundo octeto para redes.

	- Hosts: $2^{11} - 2 = 2046$
	- Subredes: $2^5$

11. ¿Cuántas subredes y cuantos hosts puede tener de una red clase B con máscara /29?

	$$
	255.255.255.11111000
	$$

	> Como es clase B tenemos reservado hasta el segundo octeto para redes.

	- Hosts: $2^3 - 2 = 6$
	- Subredes: $2^{8 + 5} = 2^{13} = 8192$

12. Divida en 4 subredes la red 192.168.40.0/24

	Para saber cuantos bits tomamos prestados resolvemos la siguiente desigualdad:

	$$
	2^n \geq 4 \quad n \geq \lg 4 \quad n \geq 2
	$$

	Vamos a pasar de una red \24 a cuatro \26:

	1. 192.168.40.0/26
	2. 192.168.40.64/26
	3. 192.168.40.128/26
	4. 192.168.40.192/26

13. Divida en 2 subredes la red 172.16.0.0/16

	$$
	2^n \geq 2 \quad n \geq \lg 2 \quad n \geq 1
	$$

	Vamos a pasar de una red \16 a dos \17:

	1. 172.16.0.0/17
	2. 172.16.128.0/17

14. Divida la red 192.168.45.0/24 en subredes de 60 host cada una, ¿cuál es la máscara de subred y las ip de red de cada subred?

	$$
	2^n - 2 \geq 60 \quad n \geq \lg 58 \quad n = 6
	$$

	Como estamos usando 6 bits para identificar los hosts, nos quedarían 26 (32 - 6) para identificar subredes. Luego nos quedarían 2 bits (8 - 6) para las subredes.

	1. 192.168.45.0/26
	2. 192.168.45.64/26
	3. 192.168.45.128/26
	4. 192.168.45.192/26

15. Divida la red 192.168.231.0/24 en subredes de 30 host cada una, ¿cuál es la máscara de subred y las ip de red de cada subred?

	$$
	2^n - 2 \geq 30 \quad n \geq \lg 28 \quad n = 5
	$$

	Como estamos usando 5 bits para identificar los hosts, nos quedarían 27 (32 - 5) para identificar subredes. Luego nos quedarían 3 bits (8 - 5) para las subredes.

	1. 192.168.231.0/27
	2. 192.168.231.32/27
	3. 192.168.231.64/27
	4. 192.168.231.96/27
	5. 192.168.231.128/27
	6. 192.168.231.160/27
	7. 192.168.231.192/27
	8. 192.168.231.224/27

16. Divida la red 172.31.0.0/16 en subredes de 1000 host cada una, ¿cuál es la máscara de subred y las ip de red de cada subred?

	$$
	2^n - 2 \geq 100 \quad n \geq \lg 998 \quad n = 10
	$$

	Como estamos usando 10 bits para identificar los hosts, nos quedarían 22 (32 - 10) para identificar subredes. Luego nos quedarían 6 bits (8 - 2) para las subredes.

	1. 172.31.4.0/22
	2. 172.31.8.0/22
	3. 172.31.12.0/22
	4. 172.31.16.0/22
	5. 172.31.20.0/22...

	- Máscara: 255.255.252.0

17. ¿Cuál es la IP de red, la IP del primer host, la IP del último host y la IP de broadcast de la:

	- 2da subred de 192.168.232.0/25

		Una máscara de 25 corresponde a

		$$
		255.255.255.1 \quad 0000000
		$$

		Como queremos la segunda subred

		$$
		1 = 2 - 1
		$$

		> El 1 es por que empezamos a contar desde el 0.

		El número 1 en binario es 1, entonces nuestra máscara es:

		$$
		255.255.255.1 \quad 0000000
		$$

		- IP red:

			$$
			192.168.232.1 \quad 0000000 = 192.168.232.128
			$$

		- IP primer host: 192.168.232.129/25
		- IP último host: 192.168.232.254/25
		- IP broadcast:

			Llenamos con 1 los espacios de host:

			$$
			192.168.232.1 \quad 1111111 = 192.168.232.255
			$$

	- 3ra subred de 192.168.132.0/26?

		Una máscara de 26 corresponde a

		$$
		255.255.255.11 \quad 000000 = 255.255.255.192
		$$

		Como queremos la 3ra subred

		$$
		2 = 3 - 1
		$$

		El número 2 en binario es 10, entonces nuestra máscara es:

		$$
		255.255.255.10 \quad 000000
		$$

		- IP red:

			$$
			192.168.132.10 \quad 000000 = 192.168.132.128
			$$

		- IP primer host: 192.168.132.128/26
		- IP último host: 192.168.132.190/26
		- IP broadcast:

			$$
			192.168.232.10 \quad 111111 = 192.168.232.191
			$$

	- última subred de 192.168.50.0/29?

		Una máscara de 29 corresponde a

		$$
		255.255.255.11111 \quad 000 = 255.255.255.248
		$$

		- IP red:

			La última red quiere decir que los bits asociados a las subredes están en 1:

			$$
			192.168.50.11111 \quad 000 = 192.168.50.248
			$$

		- IP primer host: 192.168.50.249
		- IP último host: 192.168.50.254
		- IP broadcast:

			$$
			192.168.50.11111 \quad 111 = 192.168.50.255
			$$

	- 6ta subred de 172.18.0.0/19?

		Una máscara de 19 corresponde a

		$$
		255.255.111 \quad 00000.0 = 255.255.224.0
		$$

		Como queremos la 6ta subred

		$$
		5 = 6 - 1
		$$

		El número 5 en binario es 101, entonces nuestra máscara es:

		$$
		255.255.101 \quad 00000.0 = 255.255.160.0
		$$

		- IP red:

			$$
			172.18.101 \quad 00000.0 = 172.18.160.0
			$$

		- IP primer host: 172.18.160.1/19
		- IP último host: 172.18.191.254/19
		- IP broadcast:

			$$
			172.18.101 \quad 11111.11111111 = 172.18.191.255
			$$

	- 4ta subred de 172.23.0.0/20?

		Una máscara de 20 corresponde a

		$$
		255.255.1111 \quad 0000.0 = 255.255.240.0
		$$

		Como queremos la 4ta subred

		$$
		3 = 4 - 1
		$$

		El número 3 en binario es 11, entonces nuestra máscara es:

		$$
		255.255.0010 \quad 0000.0 = 255.255.32.0
		$$

		- IP red:

			$$
			172.23.0010 \quad 0000.0 = 172.18.32.0
			$$

		- IP primer host: 172.18.32.1/20
		- IP último host: 172.18.128.254/20
		- IP broadcast:

			$$
			172.18.0010 \quad 1111.11111111 = 172.18.128.255
			$$

18. Cuál es la IP de red/subred, la IP del primer host, la IP del último host y la IP de broadcast a la que pertenece la siguiente IP:

	- 192.168.24.98/30

		- IP red:

			$$
			\begin{array}{lllll}
				  &192.&168.&24. &01100010 \\
				  &255.&255.&255.&11111100 \\
				= &192.&168.&24. &01100000 = 192.168.24.96
			\end{array}
			$$

		- IP primer host: 192.168.24.97/30
		- IP último host: 192.168.24.99/30
		- IP broadcast:

			$$
			\begin{array}{lllll}
				\neg &255.&255.&255.&11111100 \\
				=    &0.  &0.  &0.   &00000011
			\end{array} \\[10 pt]

			\begin{array}{lllll}
				  &192.&168.&24. &01100000 \\
				  &0.  &0.  &0.  &00000011 \\
				= &192.&168.&24. &01100011 = 192.168.24.99
			\end{array}
			$$

	- 192.168.250.197/26

		- IP red:

			$$
			\begin{array}{lllll}
				  &192.&168.&250.&11000101 \\
				  &255.&255.&255.&11000000 \\
				= &192.&168.&24. &11000000 = 192.168.24.192
			\end{array}
			$$

		- IP primer host: 192.168.250.193/26
		- IP último host: 192.168.250.254/26

		- IP broadcast:

			$$
			\begin{array}{lllll}
				\neg &255.&255.&255.&11000000 \\
				=    &0.  &0.  &0.   &00111111
			\end{array} \\[10 pt]

			\begin{array}{lllll}
				  &192.&168.&24 &.11000000 \\
				  &0.  &0.  &0  &.00111111 \\
				= &192.&168.&24.&11111111 = 192.168.24.255
			\end{array}
			$$

	- 192.168.15.32/29

		- IP red:

			$$
			\begin{array}{lllll}
				  &192.&168.&15. &00100000 \\
				  &255.&255.&255.&11111000 \\
				= &192.&168.&15. &00100000 = 192.168.15.32
			\end{array}
			$$

		- IP primer host: 192.168.15.33/29
		- IP último host: 192.168.15.38/29
		- IP broadcast:

			$$
			\begin{array}{lllll}
				\neg &255.&255.&255.&11111000 \\
				=    &0.   &0.  &0.  &00000111
			\end{array} \\[10 pt]

			\begin{array}{lllll}
				  &192.&168.&15.&00100000 \\
				  &0.  &0.  &0. &00000111 \\
				= &192.&168.&24.&00100111 = 192.168.24.39
			\end{array}
			$$

	- 172.16.19.173/19

		- IP red:

			$$
			\begin{array}{lllll}
				  &172.&16. &00010011.&173 \\
				  &255.&255.&11100000.&0 \\
				= &172.&16. &00000000.&0 = 172.16.0.0
			\end{array}
			$$

		- IP primer host: 172.16.0.1/19
		- IP último host: 172.16.31.254/19
		- IP broadcast:

			$$
			\begin{array}{lllll}
				\neg &255.&255.&11100000.0 \\
				=    &0.  &0.  &00011111.11111111
			\end{array} \\[10 pt]

			\begin{array}{lllll}
				  &172.&16.&00000000.&00000000 \\
				  &0.  &0. &00011111.&11111111 \\
				= &172.&16.&00011111.&11111111 = 172.16.31.255
			\end{array}
			$$

	- 172.31.15.245/20

		- IP red:

			$$
			\begin{array}{lllll}
				  &172.&31. &00001111.&245 \\
				  &255.&255.&11110000.&0 \\
				= &172.&16. &0000000. &0 = 172.31.0.0
			\end{array}
			$$

		- IP primer host: 172.31.0.1/20
		- IP último host: 172.16.15.254/19
		- IP broadcast: 172.16.15.255/19

			$$
			\begin{array}{lllll}
				\neg &255.&255.&11110000.&0 \\
				=   &0.   &0.  &00001111.&11111111
			\end{array} \\[10 pt]

			\begin{array}{lllll}
				  &172.&31.&00000000.&00000000 \\
				  &0.  &0. &00001111.&11111111 \\
				= &172.&31.&00001111.&11111111 = 172.16.15.255
			\end{array}
			$$
