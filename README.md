# VFXs

## 1. Tipos de VFX

1. Particle system
2. Mesh
3. Flipbook
4. Shader
5. Híbridos

## 2. Principios de VFX

1. Gameplay
   - Se refiere a saber el propósito del VFX antes de crearlo, o sea, para qué será, ¿será un proyectil? ¿Un AOE de daño o de curación? ¿Uno ambiental? ¿De un personaje? También es importante saber sobre el juego para el que se hará, cómo funciona, sus mecánicas, el personaje que lo llevará, etc. En resumen, se necesitará extraer la mayor cantidad de información posible del juego.

2. Timing
   - Anticipación: Carga 🔄
     - Si tarda poco en cargar, da la sensación de que no hay manera de evitarlo, pero si tarda mucho, es lo contrario.
   - Clímax: Explosión 💥
   - Disipación: Desvanecimiento de las secuelas ✨
     - Si tarda en disiparse, da la sensación de aturdimiento o de que el ataque tarda en hacer efecto.

3. Shape
   - Comunica la intención del VFX, o sea, determina si el ataque es peligroso o no y ¿qué tipo de daño hace?, ¿daña?, ¿cura?, ¿envenena?, ¿es un potenciador?
     - =▶ Es peligroso
     - =O No es peligroso o causa un estado alterado como aturdimiento o congelamiento
   - Por ejemplo, si el VFX es un orbe verde flotando tranquilamente, no es dañino y sirve para recuperar HP.
   - La paleta de colores da más significado.

4. Contrast
   - El contraste crea un punto focal que atrae la atención del jugador en cuestión de milisegundos, por ejemplo, en un proyectil, la parte más llamativa será la cabeza de este.
   - También se usa para describir la importancia de las habilidades de un personaje, es decir, sus ataques más básicos tienen menos contraste (menos brillantes) y los poderosos más (más brillantes).
![2 Gray Scale Contrast](https://github.com/bryantchacon/vfx/assets/36392260/5df6b3c2-13ea-4806-89ee-132875257d06)
![3 Color contrast](https://github.com/bryantchacon/vfx/assets/36392260/1c030522-c350-4c9f-9ce7-490506cdab07)

5. Color / Theme
   - Una buena paleta de colores funciona porque los colores tienen contraste entre sí.
   - Se ordenan del más oscuro al más claro.
![4 Linear Palettes](https://github.com/bryantchacon/vfx/assets/36392260/d2a8ec42-8696-47ae-a498-33fe6f77bcc1)
![5 Combined Palettes](https://github.com/bryantchacon/vfx/assets/36392260/cb28681d-0960-4aff-834c-c03113501a8d)

## 3. Preproducción
1. Saber el objetivo del VFX
   - Saber que hará el VFX en el juego.

2. Donde obtener referencias
   - Artstation
   - Pinterest
   - YouTube
   - Real-Time VFX

3. Tecnical Research
   - Investigar técnicas de cómo crear VFXs

4. Sketching
   - Hacer sketches de como será el VFX, (no es necesario ser un ilustrador pro).


## 4. Producción de VFXs


## 5. Performance
![BatchesCall_Graphic_BadExample](https://github.com/bryantchacon/vfx/assets/36392260/29ef947b-9cac-4c67-b233-9bf5aeb9717d)
![BatchesCall_Graphic_GoodExample](https://github.com/bryantchacon/vfx/assets/36392260/a42f330f-3def-4256-915f-f64a29825860)

   - La optimización de Batches (draw calls) se puede hacer solo cuando los particle systems tienen el mismo material.

   - Para reducir más los batches los particle systems que usen meshes deben ir en un order layer diferente de los demás que no usan meshes y así no se rompan los draw call.


## 6. VFX Graph
|**PARTICLE SYSTEM (CPU)**||**VFX GRAPH (GPU)**||
| :-: | :-: | :- | :- |
|**PROS**|**CONS**|**PROS**|**CONS**|
|<p>- Buenas colisiones en físicas</p><p></p><p>- Generación y control de luces</p><p></p><p>- Funciona en cualquier plataforma</p><p></p><p>- Workflow rápido</p>|<p>- Miles de partículas</p><p></p><p>- Propiedades de shaders (No muy sencillo)</p>|<p>- Millones de partículas</p><p></p><p>- Procesamiento paralelo</p><p></p><p>- Propiedades de shaders (Sencillo)</p><p></p><p>- Crear decals fácilmente</p><p></p><p>- Heat distortion (HDRP only ?)</p><p></p><p>- Parámetros modificables</p><p></p><p>- Modular</p>|<p>- Malas colisiones en físicas</p><p></p><p>- No tiene luces (por ahora)</p><p></p><p>- No funciona en cualquier plataforma (aun)</p><p></p><p>- Workflow lento</p>|


## 7. Partes de VFX Graph
1. Spawn: Maneja la cantidad de partículas por segundo y si se generaran constantemente o como una ráfaga, etc.

2. Initialize Particle: Maneja la capacidad del sistema de partículas, y como se inicializa CADA una, además de su velocidad, lifetime, etc.

3. Udate Particle: Actualiza constantemente los atributos de la partícula después de inicializarla, etc. Funciona como el Update() de C# en Unity.

4. Output Particle Quad: Renderiza la partícula y controla su apariencia, como su orientación, tamaño y color a travéz del tiempo, y da control directo en las propiedades del shader, etc.

![VFX Graph](https://github.com/bryantchacon/vfx/assets/36392260/4cb52df7-8adc-4f06-8f7b-fe0f02075f58)


> Unity 2021.3.4f1
