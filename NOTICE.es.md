# Aviso

*(English: [NOTICE.md](NOTICE.md))*

## Sin afiliación

Esto es un proyecto de aficionados, no oficial y sin ánimo de lucro. **No está afiliado a
Capcom ni a Arika**, ni a ninguna de sus filiales, ni cuenta con su respaldo o su aprobación;
tampoco está afiliado a los autores del framework
[PSXRecomp](https://github.com/RetroPortingToolKit/psxrecomp) ni a los del
[proyecto del juego](https://github.com/strider973/Street-Fighter-EX2-Plus-Recompiled) sobre el
que corre este mod. *Street Fighter*, *Street Fighter EX2 Plus* y todos los nombres, personajes
y marcas relacionados son propiedad de sus respectivos titulares, y aquí se usan únicamente
para identificar el juego con el que este mod es compatible.

Aquí no se vende nada y no se monetiza nada.

## Lo que este repositorio no distribuye

Ni ROM. Ni imagen del disco. Ni BIOS. Ni ejecutable compilado. Ni imagen de disco parcheada. Ni
arte, ni audio, ni música, ni las letras del juego. Para jugar hace falta **tu propia copia
legítima** del juego y una compilación del proyecto del juego que funcione, y este repositorio
no da ninguna de las dos, ni puede darlas. Por sí solo, nada de lo que hay aquí produce un
juego jugable.

## Lo que sí contiene de la obra original

Un paquete declarativo de parches, y nada más. Cada uno de sus 979 parches declara los **bytes
que espera encontrar** en un desplazamiento antes de escribir nada: esa comprobación es
justamente lo que hace que el paquete se niegue a aplicarse sobre un volcado que no es el suyo
en vez de estropearlo. Esos bytes citados suman **23.330 bytes en total**, y son cadenas de la
interfaz: `MODE SELECT`, `PRACTICE`, `VITALITY` y parecidas. Ni código ejecutable, ni arte, ni
audio.

El paquete guarda además el **SHA-256** del disco, que es una huella y no contenido, y es lo
que ata cada parche a la edición correcta del juego.

Las capturas de `docs/images/` están para documentar **qué cambia el mod**: todas enseñan
interfaz traducida, que es el trabajo, y el arte del juego es el fondo sobre el que
inevitablemente va. La regla que se aplica es que una captura se gana su sitio enseñando el
trabajo, así que la pantalla de título —que es sobre todo el logotipo y la marca de Capcom y no
enseña nada que haya hecho este mod— no está. Lo que queda sigue siendo propiedad de sus
respectivos titulares.

## Retirada y contacto

Si tienes derechos sobre este material y quieres que algo de aquí se retire o se cambie,
escribe a **jajdpmail@gmail.com** diciendo a qué te opones y en calidad de qué escribes.

Las peticiones de los titulares de derechos se atienden: se quita la parte en disputa, o se
retira el repositorio entero, sin discutirlo, y recibirás una respuesta confirmándolo. No hace
falta ningún aviso ni trámite legal más allá de ese correo para llegar a quien mantiene esto.
