# Acuario 3D

Un acuario 3D interactivo en un solo archivo HTML. Se abre en cualquier navegador, no necesita instalación ni servidor.

## Cómo usarlo

Abrí `Acuario 3D.html` en el navegador y listo. El acuario se llena solo, pero podés meter mano:

- **Tocar el agua** asusta a los peces y se dispersan con el anillo de onda.
- **Arrastrar** gira la cámara alrededor del tanque.
- **Pellizcar** (o la rueda del mouse) acerca y aleja la vista.
- **Alimentar** tira comida al agua y hace que los peces la persigan.

Los botones de abajo permiten sumar o quitar peces en el momento.

## Qué hay adentro

Todo se genera por código: el fondo marino, las algas que se mecen con la corriente, los rayos de luz que entran desde arriba, las burbujas, las rocas y el coral. Los peces navegan por su cuenta con un comportamiento de bando simple: se mantienen juntos, eluden a los demás y responden a la comida y al susto.

Hay varias especies con colores y tamaños distintos, cada una con su propia velocidad y forma de moverse.

## Detalles técnicos

- Hecho con [three.js r128](https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js) vía CDN (se necesita internet la primera vez).
- Un solo `<canvas>` con renderizado WebGL. Los peces se unen en una sola malla por especie para no inflar las llamadas de dibujo.
- Pensado para pantallas táctiles también: respeta el `safe-area` y el `devicePixelRatio`.

## Controles de la simulación

La lógica de bando vive en el bucle principal (`step`). Se puede ajustar:

- Radio del tanque: `BX`, `BY`, `BZ`.
- Número inicial de peces: `addFish()` se llama 36 veces al arrancar.
- Peso de cada especie: el campo `w` de `SP`.

## Notas

- El archivo queda parado en la versión r128 de three.js; si actualizás la librería, revisá que no rompa `points`, `instancedMesh` o la sintaxis del `Raycaster`.
- Fue probado en celulares y en escritorio, en claro y en oscuro.