# Unidad 5
## Bitácora de proceso de aprendizaje

¿Qué es el encapsulamiento para ti? Describe una situación en la que te haya sido útil o donde hayas visto su importancia.

¿Qué es la herencia? ¿Por qué un programador decidiría usarla? Da un ejemplo simple.

¿Qué es el polimorfismo? Describe con tus palabras qué significa que un código sea “polimórfico”.

## Actividad 2
Analisis:

Estructura general
-"ofApp" es la clase principal que maneja la aplicación (setup, update, draw, eventos).
-Existe un vector "particles" que almacena punteros a objetos derivados de la clase abstracta "Particle".
- Cada ciclo (update) se encarga de:
  - Actualizar todas las partículas.
  - Revisar si alguna debe explotar (shouldExplode) o si ya está muerta (isDead).
  - En caso de explotar, se generan nuevas partículas de explosión (CircularExplosion, RandomExplosion, StarExplosion).

Clase "Particle"
-Es abstracta: define la interfaz (update, draw, isDead).
- Tiene métodos virtuales que las subclases deben implementar.
- Esto permite que "particles" pueda contener diferentes tipos de partículas sin importar su implementación.

 "RisingParticle"
- Se crea desde la parte inferior de la pantalla y sube con una velocidad inicial.
-Tiene un tiempo de vida (lifetime) y una condición de explosión (exploded).
-Cuando llega a cierta altura o se acaba su tiempo, marca "shouldExplode = true".

 "ExplosionParticle"
- Clase base para las explosiones.
- Maneja posición, velocidad, color, tiempo de vida y tamaño.
-Se encarga de actualizar la posición y desvanecer el color con el tiempo.

Tipos de explosión 
- "CircularExplosion": partículas salen en círculo.
-"RandomExplosion": partículas salen en direcciones aleatorias, dibujadas como rectángulos.
- "StarExplosion": partículas salen en forma de estrella con líneas radiales.




## Bitácora de aplicación 

Evidencia 1: Herencia en Memoria 

Para "BouncingParticle"

<img width="907" height="135" alt="Captura de pantalla 2026-03-27 105348" src="https://github.com/user-attachments/assets/13df92c0-c503-4914-b574-f659102a2ec9" />

"BouncingParticle" Hereda directamente de la clase "Particle" su estructura. 

Primero aparece la estructura de Particle

<img width="921" height="189" alt="Captura de pantalla 2026-03-27 111046" src="https://github.com/user-attachments/assets/48796f1d-acc7-46f7-bf6b-7685b548dbe3" />

<img width="908" height="160" alt="Captura de pantalla 2026-03-27 111518" src="https://github.com/user-attachments/assets/1ff8a0c6-edfe-4493-affa-5653926603b6" />

Luego aparecen los campos de BouncingParticle junto a la estructura heredada. 

Evidencia 2: v_table 

<img width="898" height="210" alt="Captura de pantalla 2026-03-27 112229" src="https://github.com/user-attachments/assets/2672708a-0026-46d1-9b81-f4aa55cf0f1b" />

<img width="897" height="208" alt="Captura de pantalla 2026-03-27 112336" src="https://github.com/user-attachments/assets/ab07bc03-a9a3-4bb7-b286-7f76aef1e093" />

Inspeccionamos la v_table de BouncingParticle (añadido) y RisingParticle 

Evidencia 3: Polimorfismo en tiempo de ejecución 

<img width="924" height="207" alt="Captura de pantalla 2026-03-27 114439" src="https://github.com/user-attachments/assets/069e35e3-47fe-451d-b6ef-b6fd3c249af9" />

Evidencia 4: 

<img width="904" height="209" alt="Captura de pantalla 2026-03-27 115229" src="https://github.com/user-attachments/assets/bf6bc8fe-92b7-401d-b13b-0abd51e210c6" />

Evidencia 5:

Evidencia 7:

<img width="958" height="739" alt="Captura de pantalla 2026-03-27 122557" src="https://github.com/user-attachments/assets/ab422231-ed8c-41ca-8c6a-a69634c29e2c" />

<img width="1019" height="746" alt="Captura de pantalla 2026-03-27 122622" src="https://github.com/user-attachments/assets/bdc2944f-9fcc-43e4-985c-9be88c0e287a" />


## Bitácora de reflexión
