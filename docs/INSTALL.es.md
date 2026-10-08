# Instalar el mod en español

*(English: [INSTALL.md](INSTALL.md))*

## Antes de empezar

Hace falta un proyecto PSXRecomp de Street Fighter EX2 Plus que ya funcione en tu máquina, y
tu propio volcado del disco NTSC-U.

El paquete está atado a ese volcado. Comprueba el tuyo antes que nada:

```
SHA-256  f12ab8cb7a7af9599fe805f3c1405a051f22810305d2005b107c042316aa936f
```

```powershell
# Windows
certutil -hashfile "Street Fighter EX2 Plus (USA).bin" SHA256
```

```sh
# Linux / macOS
sha256sum "Street Fighter EX2 Plus (USA).bin"
```

Si tu huella es otra, el mod no se aplicará. Mira *Si algo no sale bien*, más abajo.

## 1. Copiar el paquete

Copia la carpeta de modo que este archivo quede junto al ejecutable del juego:

```
<carpeta del juego>/mods/packages/sfex2p.es/1.0.0/manifest.toml
```

Y ya está: no hay nada que compilar ni que generar. No cambies el nombre de las carpetas: el
id y la versión del paquete **son** la ruta.

## 2. Encenderlo

Arranca el juego. En el lanzador, en **Mods**, el grupo **Localization** trae ahora **Menú en
español**, encendido de fábrica. Pulsa **PLAY**.

![La lista de Mods del lanzador](images/pc-lanzador-mods.png)

## 3. Comprobarlo

El título tiene que decir **PULSA START**, y el menú, **ELIGE MODO**. Después:

| Pantalla | Qué se ve |
|---|---|
| Menú principal | **ELIGE MODO**, y entre las entradas PRACTICA, OPCIONES y MINIJUEGOS |
| Lista de modos | MODO ARCADE, MODO VERSUS, ENTRENAMIENTO, MODO DESAFIO, MODO DIRECTOR |
| Antes de pelear | **FASE 1** en el rótulo dorado, no «STAGE 1» |
| Elegir luchador | **ELIGE PERS.** en el rótulo dorado y **ELIGE LUCHADOR** como texto (son dos recursos distintos) |
| Pantalla de versus | punteros **1J** / **2J**, **ENERGIA** en la barra, **00 VIC 00** en el marcador y **2J PRESIONE START** |
| Pausa | SEGUIR JUGANDO, REPETIR, SALIR |
| Tarjeta de memoria | español con tildes: esa letra sí las tiene |

![La pantalla de resultados en español](images/pc-resultados-es.png)

## 4. Apagarlo

Desmarca **Menú en español** en el lanzador: el juego vuelve al inglés en el acto, sin
reinstalar nada. Las partidas guardadas no se ven afectadas
(`save_compatibility = "shared"`).

Para quitarlo del todo, borra la carpeta `mods/packages/sfex2p.es/`.

## Consolas y otros empaquetados UWP

En una compilación UWP (por ejemplo una Xbox en modo desarrollador) el paquete no se instala
aparte: se copia dentro del paquete de la aplicación, junto al ejecutable, y viaja con él; el
runtime lo lleva a su carpeta de datos en cada arranque. Para actualizar la traducción se
instala una versión nueva del paquete de la aplicación.

## Si algo no sale bien

| Síntoma | Causa |
|---|---|
| La opción no aparece en el lanzador | El paquete no está junto al ejecutable, o le cambiaron el nombre a alguna carpeta. La ruta tiene que ser exactamente `mods/packages/sfex2p.es/1.0.0/manifest.toml`. |
| Aparece pero no se deja encender, o el juego no arranca | La huella del disco no coincide con `disc_sha256`. Otro volcado, otra revisión u otra región: este paquete es solo para el NTSC-U `SLUS-01105`. |
| Los menús están en español pero una pantalla sigue en inglés | O es a propósito (los nombres propios y los rótulos dibujados se quedan en inglés) o es una pantalla que no se recorrió: los finales del arcade están sin revisar. Se agradece el aviso. |
| Faltan tildes en los menús | Es a propósito: la letra de los menús no tiene tildes ni eñe. La de la tarjeta de memoria sí, y las usa. |
