# Acuario 3D

Un acuario 3D interactivo que corre entero en el navegador. Son dos archivos y nada más: `Acuario 3D.html` y `three.min.js`. No necesita instalación, servidor ni conexión a internet.

## Cómo usarlo

Abrí `Acuario 3D.html` con el `three.min.js` en la misma carpeta. Nada más.

- **Tocar el agua** asusta a los peces: sale un anillo de onda y se dispersan.
- **Arrastrar** gira la cámara alrededor del tanque.
- **Pellizcar** (o la rueda del mouse) acerca y aleja.
- **Flechas del teclado** también mueven la cámara, y **+ / -** acercan y alejan.
- **Alimentar** tira comida y los peces la persiguen.
- **Más / Menos peces** ajustan la cantidad en el momento.
- **Noche / Día** cambia la iluminación del acuario.
- **Foto** descarga una imagen del acuario.

Los botones de arriba (noche y foto) y la cantidad de peces quedan guardados, así que al volver se abre como lo dejaste.

## Qué hay adentro

Todo se genera por código: el fondo marino, las algas que se mecen con la corriente, los rayos de luz que entran desde arriba, las burbujas, las rocas y el coral. Los peces nadan por su cuenta con un comportamiento de bando simple: se mantienen juntos, se separan si se apretujan y reaccionan a la comida y al susto.

Hay ocho variedades con colores, tamaños y velocidades distintas.

## Notas técnicas

- Hecho con **three.js r128**, guardado localmente en `three.min.js` para que funcione sin internet.
- Los peces se dibujan con **InstancedMesh**, así que aunque haya más de cien el costo de dibujo sigue siendo bajo.
- El comportamiento de bando usa una **rejilla espacial**: cada pez solo mira a los vecinos cercanos, no a todos.
- El bucle de animación **no reserva memoria en cada frame**, que es lo que suele producir tirones.
- Si el equipo no da abasto, el programa **baja la cantidad de peces y la resolución solo**, para mantener la animación fluida.
- Se **pausa** cuando la pestaña queda oculta y se reanuda al volver.
- Si el navegador no tiene WebGL, muestra un aviso en lugar de una pantalla en negro.

## Para tocar el código

Está pensado para ser claro y no depender de herramientas de compilación.

- Cantidad máxima de peces: `MAXFISH`.
- Cantidad inicial y según el equipo: `DEFAULT_FISH` y `lowEnd`.
- Tamaño del tanque: `BX`, `BY`, `BZ`.
- Especies y su peso: el arreglo `SP`.
- Paletas de iluminación: `PAL`.

`three.min.js` está fijado en la r128. Si lo actualizás, revisá que sigan funcionando `InstancedMesh`, `Points` y `Raycaster`.
