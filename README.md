# Acuario 3D

Un acuario 3D interactivo en un solo archivo. Es todo `Acuario 3D.html`: abrís ese archivo con el navegador y funciona. No necesita instalación, servidor, conexión a internet ni nada más.

## Cómo usarlo

Doble toque sobre `Acuario 3D.html` (o "abrir con" el navegador) y listo.

- **Tocar el agua** asusta a los peces: sale un anillo de onda y se dispersan.
- **Arrastrar** gira la cámara alrededor del tanque.
- **Pellizcar** (o la rueda del mouse) acerca y aleja.
- **Flechas del teclado** también mueven la cámara, y **+ / -** acercan y alejan.
- **Alimentar** tira comida y los peces la persiguen.
- **Más / Menos peces** ajustan la cantidad en el momento.
- **Noche / Día** cambia la iluminación del acuario.
- **Foto** descarga una imagen del acuario.

El modo noche y la cantidad de peces quedan guardados, así que al volver se abre como lo dejaste.

## Qué hay adentro

Todo se genera por código: el fondo marino, las algas que se mecen con la corriente, los rayos de luz que entran desde arriba, las burbujas, las rocas y el coral. Los peces nadan por su cuenta con un comportamiento de bando simple: se mantienen juntos, se separan si se apretujan y reaccionan a la comida y al susto.

Hay ocho variedades con colores, tamaños y velocidades distintas.

## Notas técnicas

- Hecho con **three.js r128**, incrustado dentro del propio HTML para que el archivo funcione solo.
- Los peces se dibujan con **InstancedMesh**, así que aunque haya más de cien el costo de dibujo sigue siendo bajo.
- El comportamiento de bando usa una **rejilla espacial**: cada pez solo mira a los vecinos cercanos, no a todos.
- El bucle de animación **no reserva memoria en cada frame**, que es lo que suele producir tirones.
- Si el equipo no da abasto, el programa **baja la cantidad de peces y la resolución solo**, para mantener la animación fluida.
- Se **pausa** cuando la pestaña queda oculta y se reanuda al volver.
- Si el navegador no tiene WebGL, muestra un aviso en lugar de una pantalla en negro.

## Para tocar el código

El archivo tiene el three.js incrustado arriba (un bloque largo de una sola línea); el código del acuario está en el último `<script>`, al final del archivo. Está pensado para ser claro y no depender de herramientas de compilación.

- Cantidad máxima de peces: `MAXFISH`.
- Cantidad inicial y según el equipo: `DEFAULT_FISH` y `lowEnd`.
- Tamaño del tanque: `BX`, `BY`, `BZ`.
- Especies y su peso: el arreglo `SP`.
- Paletas de iluminación: `PAL`.
