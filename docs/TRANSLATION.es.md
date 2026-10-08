# Notas de la traducción

Por qué el español de este mod dice lo que dice. Casi todas las decisiones vienen impuestas
por el juego: el hueco que deja cada cadena, las letras que tiene la fuente y el sitio fijo
desde donde dibuja.

*(This document is Spanish-only: it is about the Spanish wording itself. The technical side is
summarised in the [README](../README.md).)*

## 1. Dónde viven los textos

Street Fighter EX2 Plus guarda sus textos de interfaz como **cadenas ASCII sin comprimir**, en
dos sitios:

- **el ejecutable** (`SLUS_011.05`, que se carga en `0x80130000`): los avisos del arranque y
  de la configuración de botones;
- **los módulos del disco** que carga para cada pantalla: el menú, las opciones, la pausa, el
  entrenamiento, los resultados y los mensajes de la tarjeta de memoria.

El mismo texto aparece muchas veces, uno por pantalla que lo usa: «PRESS START BUTTON TO
EXIT.» está en **trece** sitios. Por eso el paquete tiene 979 parches para 302 textos: hay que
cambiar **todas** las apariciones o la pantalla que falte se queda en inglés.

Los menús se dibujan **letra a letra** con una fuente propia del juego. Los rótulos grandes
—STAGE, PLAYER SELECT, VITALITY, VS— **no son texto**: son imágenes, y se tratan aparte (§5).

## 2. El hueco manda

Cada cadena tiene una reserva: su largo más el NUL, redondeado a cuatro. El español tiene que
caber ahí. Y hay campos de **ancho fijo** que el juego no pinta más allá: las entradas del menú
principal son de diez caracteres y los títulos de modo, de catorce.

De ahí salen varias decisiones que, fuera de contexto, parecen caprichos:

| Original | Español | Por qué |
|---|---|---|
| `BONUS GAME` | `MINIJUEGOS` | Diez justos. «JUEGO EXTRA» salía cortado como «JUEGO EXTR» |
| `TRIAL MODE` | `DESAFIOS` | «MODO PRUEBA» no cabía, y «DESAFÍOS» describe mejor el modo |
| `PAUSE MENU EXIT` | `SEGUIR JUGANDO` | «SALIR DEL MENÚ DE PAUSA» no cabe ni de lejos |
| `RESTART` | `REPETIR` | «REINICIAR» no entra en el campo |
| `MAX DAMAGE` | `MAYOR GOLPE` | Once caracteres; «DAÑO MÁXIMO» lleva eñe (§3) |

## 3. Lo que la letra no tiene

La fuente de los menús **no tiene tildes, ni eñe, ni `¡`, ni `¿`**:

- las **tildes se pliegan**: en el disco se escribe `PRACTICA`, `DESAFIOS`, `REPETICION`;
- la **eñe se rechaza**. «DANO» por «DAÑO» no es aceptable, así que se busca otra palabra:
  `DAMAGE` es **FUERZA DE GOLPE**, no «DAÑO»;
- las **minúsculas sueltas y los signos** `|`, `~`, `{`, `#`, `&`, `<>` son **iconos de
  botones**, no letras: se conservan tal cual. Donde el original deja huecos para un icono
  («PRESS   BUTTON»), el español ocupa lo mismo y los huecos no se mueven.

La fuente de los **mensajes de la tarjeta de memoria** es otra: tiene minúsculas y tildes, y
los mensajes se traducen línea a línea conservando su marca de final. Ahí sí se lee español
normal: *«Esta MEMORY CARD no …»*, y «MEMORY CARD» se queda porque es el nombre del aparato
tal como lo rotulaba Sony.

## 4. El juego no centra el texto

Lo dibuja desde una posición fija, calculada para el inglés. Una cadena más corta se iría a la
izquierda, y una más larga se saldría. Por eso cada texto declara cómo se coloca:

| Forma | Qué hace | Ejemplo |
|---|---|---|
| centro | Conserva el centro del original y rellena hasta su largo | `  PULSA START PARA SALIR.  ` |
| derecha | Alinea a la derecha, como los valores de las opciones | `   OFF` |
| izquierda | Misma sangría que el original y relleno detrás | `MODO DIRECTOR ` |
| línea | Para la tarjeta: respeta la marca de final de línea | `Esta MEMORY CARD no             @` |

Los espacios de los ejemplos **son parte de la traducción**, no un descuido del formato.

## 5. Los rótulos dibujados

Cuatro cosas de la pantalla no son texto sino imágenes, y se rehicieron píxel a píxel
**componiéndolas con las letras del propio juego**, para que no desentonen con el resto del
arte:

- **FASE 1** (2, 3…) en vez de `STAGE 1`, el rótulo dorado de antes de cada pelea;
- **ELIGE PERS.** en vez de `PLAYER SELECT`, una palabra en cada uno de los dos sprites del
  rótulo. (La cadena de texto equivalente, que es otro recurso distinto, dice **ELIGE
  LUCHADOR**: el mismo rótulo puede estar dos veces en el juego, dibujado y escrito.)
- **ENERGIA** en vez de `VITALITY` en la barra de vida. «VITALIDAD» no cabía, y esa hoja de
  letras no tiene «D»;
- los punteros y las placas: **1J** y **2J** en vez de `1P` y `2P`, y el marcador
  **00 VIC 00** en vez de `00 WIN 00`.

![Los rótulos compuestos con las letras del juego](images/rotulos-es.png)

## 6. Lo que se queda en inglés, a propósito

| Qué | Por qué |
|---|---|
| Luchadores, escenarios, músicas y golpes | Nombres propios; además, muchos están dibujados |
| HIT, DAMAGE, TOTAL, REVERSAL, GUARD BREAK del marcador | Jerga del marcador, dibujada como imágenes |
| GAME OVER, TIME ATTACK, RANKING | Imágenes, no texto |
| **CP**, el lado de la máquina | Vale igual en español: «computadora» |
| MEMORY CARD | Es el nombre del accesorio |

## 7. Un error de traducción

Si ves una pantalla en inglés que debería estar traducida, una palabra cortada o un texto
descolocado, abre una incidencia contando **en qué pantalla** y, si puedes, con una captura.
Los finales del arcade son el sitio donde más probable es que quede algo: no se han recorrido.
