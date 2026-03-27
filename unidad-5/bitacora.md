# Unidad 5
## Bitácora de proceso de aprendizaje

¿Qué es el encapsulamiento para ti? Describe una situación en la que te haya sido útil o donde hayas visto su importancia.

¿Qué es la herencia? ¿Por qué un programador decidiría usarla? Da un ejemplo simple.

¿Qué es el polimorfismo? Describe con tus palabras qué significa que un código sea “polimórfico”.

## Actividad 2
Analisis:

Estructura general
- "ofApp" es la clase principal que maneja la aplicación (setup, update, draw, eventos).
- Existe un vector "particles" que almacena punteros a objetos derivados de la clase abstracta "Particle".
- Cada ciclo (update) se encarga de:
  - Actualizar todas las partículas.
  - Revisar si alguna debe explotar (shouldExplode) o si ya está muerta (isDead).
  - En caso de explotar, se generan nuevas partículas de explosión (CircularExplosion, RandomExplosion, StarExplosion).

Clase "Particle"
- Es abstracta: define la interfaz (update, draw, isDead).
- Tiene métodos virtuales que las subclases deben implementar.
- Esto permite que "particles" pueda contener diferentes tipos de partículas sin importar su implementación.

 "RisingParticle"
- Se crea desde la parte inferior de la pantalla y sube con una velocidad inicial.
- Tiene un tiempo de vida (lifetime) y una condición de explosión (exploded).
- Cuando llega a cierta altura o se acaba su tiempo, marca "shouldExplode = true".

 "ExplosionParticle"
- Clase base para las explosiones.
- Maneja posición, velocidad, color, tiempo de vida y tamaño.
- Se encarga de actualizar la posición y desvanecer el color con el tiempo.

Tipos de explosión 
- "CircularExplosion": partículas salen en círculo.
- "RandomExplosion": partículas salen en direcciones aleatorias, dibujadas como rectángulos.
- "StarExplosion": partículas salen en forma de estrella con líneas radiales.




## Bitácora de aplicación 




## Bitácora de reflexión
