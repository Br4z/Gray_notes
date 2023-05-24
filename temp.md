# Cosas para preguntar

## Taller redes

1 (2.2) Desactive la búsqueda de DNS.

Comandos para guardar y descargar archivos del TFTP


# Ejercicio 3

La empresa donde usted labora tiene como política de costos para sus nuevas inversiones, que el pago mensual uniforme no supere una cantidad equivalente a 30000000 COP.

Actualmente, tiene la posibilidad de adquirir un repuesto que se requiere mensualmente y durante los próximos cuatro años, momento en el cual la empresa proyecta, se reemplazara el equipo que lo utiliza. El coso del repuesto es de $4.800 para el primer mes -que se pagara al finalizar el mes- y se espera que aumente debido a la inflación estadounidense en un 0.8% cada mes.

Para realizar el cambio se necesita parar la planta, evento que le costara, 5000000 COP para el primer mese -también pagados al final de periodo- y de allí en adelante aumenta en 480000 COP cada periodo. La rentabilidad esperada de la compañía es del 14.06% AMV en pesos. La TRM de hoy es de 3000 $\frac{COP}{\$}$ y se espera una devaluación del dólar del 0.2% mensual y constante durante los próximos 8 años.

Determine si se debe invertir o no en el proyecto

Primero hayamos algunos datos

- $4 \text{ años} = 48 \text{ meses}$

- $i_m = \frac{14.06\%}{12} \approx 1.17\%$

- $i_{\$}\approx \frac{1.17\% + 1}{1 - 0.2\%} - 1 \approx 1.4\%$

En el proyecto identificamos las siguientes estructuras:

- $(4800,8\%)_{(0 - 48)}$
    $$
    P_{\$} \approx 4800 \left (\frac{ 1 - \left (\frac{(1 + 0.8\%)}{(1 + 1.4\%)} \right )^{48}}{(1.4\% - 0.8\%)} \right ) \approx 198309 \\[10 pt]

    P_{\text{COP}} = P_{\$} * 3000 = 594927000
    $$

- $A/P$

    $$
    A = 594927 \left (\frac{1.17\%(1 + 1.17\%)^{48}}{(1 + 1.17\%)^{48} - 1} \right ) = 16269 * 10^3
    $$

- $(5000,480)_{0 - 48}$

    $$
    A = 5000 + 480 \left (\frac{1}{1.17\%} - \frac{48}{(1 + 1.17\%)^{48} - 1} \right ) \approx 15214 * 10^3
    $$

$$
30000 - (16269 + 15214) = -1483.0
$$

NO se debe invertir en el proyecto.

# Configuracion neovim para detectar espacios finales

```
function! TrimWhitespace()
    let l:save = winsaveview()
    keeppatterns %s/\s\+$//e
    call winrestview(l:save)
endfunction
```