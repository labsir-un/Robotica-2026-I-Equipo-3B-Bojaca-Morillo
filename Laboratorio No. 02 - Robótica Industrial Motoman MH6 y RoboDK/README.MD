<!-- ===== EQUIPO ===== -->

<div align="center">

<!-- ================== INTEGRANTE 1 ================== -->

<p>
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=700&size=22&duration=2400&pause=600&color=7F5AF0&center=true&vCenter=true&width=600&lines=Gabriel+Eduardo+Bojaca+Munar">
</p>

<b>Carrera:</b> Ingeniería Mecatrónica <br>
<b>Correo:</b> gbojaca@unal.edu.co <br>
<b>GitHub:</b> <a href="https://github.com/usuariogithub">usuariogithub</a> <br>
<b>Rol:</b> Simulación y documentación <br>
<b>Intereses:</b> Robótica móvil, automatización <br><br>

<p style="max-width:500px;">
Me interesa mucho la simulación y cómo se pueden modelar sistemas mecatrónicos para entender mejor su comportamiento. También me gusta la automatización y la robótica , sobre todo ver cómo funcionan y cómo se pueden mejorar.
</p>

<br><br>

<!-- ================== INTEGRANTE 2 ================== -->
<p>
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=700&size=22&duration=2400&pause=600&color=7F5AF0&center=true&vCenter=true&width=600&lines=Maria+Fernanda+Morillo+Tovar">
</p>


<b>Carrera:</b> Ingeniería Mecatrónica <br>
<b>Correo:</b> mmorillot@unal.edu.co <br>
<b>GitHub:</b> <a href="https://github.com/mmorillot">mmorillot</a> <br>
<b>Rol:</b> Modelado, programación y control <br>
<b>Intereses:</b> Control de robots, manipulación.<br><br>

<p style="max-width:500px;">
Actualmente estoy en décimo semestre de Ingeniería. Me interesa el área de control de robots, especialmente entender cómo funcionan y cómo se pueden hacer más precisos. También me llama la atención la parte de manipulación.
</p>

</div>
# Introducción

En este laboratorio se realizó el análisis y operación del manipulador industrial Motoman MH6, comparándolo con el ABB IRB140 en términos de características técnicas, configuraciones iniciales y modos de operación.  

Además, se trabajó con el software RoboDK para la simulación y ejecución de trayectorias, implementando una trayectoria polar tanto en simulación como en el manipulador físico.

---

# Objetivos

- Comparar las características técnicas del Motoman MH6 y el ABB IRB140.
- Identificar las configuraciones Home1 y Home2 del Motoman MH6.
- Realizar movimientos manuales en distintos modos de operación.
- Configurar velocidades de movimiento manual.
- Comprender el funcionamiento de RoboDK y su comunicación con el robot.
- Implementar una trayectoria polar en RoboDK y ejecutarla físicamente.

---

# Comparación de Manipuladores

| Característica | Motoman MH6 | ABB IRB140 |
|---|---|---|
| Grados de libertad | 6 | 6 |
| Alcance | 1422 mm | 810 mm |
| Carga máxima | 6 kg | 6 kg |
| Repetibilidad | ±0.08 mm | ±0.03 mm |
| Aplicaciones | Soldadura, manipulación, ensamblaje | Pick and place, ensamblaje |
| Tipo de robot | Antropomórfico | Antropomórfico |

---

# Configuraciones Iniciales

## Home1
Descripción de la configuración Home1 del Motoman MH6.

## Home2
Descripción de la configuración Home2 del Motoman MH6.

### Análisis
Explicación de cuál configuración es más conveniente y justificación.

---

# Movimiento Manual del Robot

## Movimiento por Articulaciones
Descripción del procedimiento para mover el robot por articulaciones.

## Movimiento Cartesiano
Descripción del procedimiento para mover el robot en coordenadas cartesianas.

## Traslaciones y Rotaciones
Explicación de movimientos en los ejes:
- X
- Y
- Z
- Rx
- Ry
- Rz

---

# Control de Velocidad

## Niveles de Velocidad
Descripción de los niveles de velocidad disponibles en el Motoman MH6.

## Cambio de Velocidad
Procedimiento para modificar la velocidad manual.

## Visualización
Cómo identificar en pantalla el nivel de velocidad seleccionado.

---

# RoboDK

## Aplicaciones Principales
- Simulación de robots
- Programación offline
- Validación de trayectorias
- Comunicación con robots industriales

## Comunicación con el Manipulador
Explicación de cómo RoboDK se comunica con el Motoman MH6.

## Funcionamiento
Descripción del proceso que realiza RoboDK para mover el manipulador.

---

# Comparación entre RoboDK y RobotStudio

| Característica | RoboDK | RobotStudio |
|---|---|---|
| Compatibilidad | Multimarca | ABB |
| Simulación | Sí | Sí |
| Programación offline | Sí | Sí |
| Facilidad de uso | Alta | Media |
| Aplicación principal | Simulación general | Robots ABB |

## Análisis Personal
Descripción y opinión sobre cada herramienta.

---

# Trayectoria Polar

## Descripción
Explicación de la trayectoria polar implementada.

## Simulación en RoboDK
Inserte imágenes o capturas de la simulación.

## Implementación Física
Descripción de la ejecución en el manipulador Motoman MH6.

---

# Diagrama de Flujo

```mermaid
flowchart TD
    A[Inicio] --> B[Encender Robot]
    B --> C[Configurar RoboDK]
    C --> D[Programar Trayectoria]
    D --> E[Simulación Virtual]
    E --> F[Ejecución Física]
    F --> G[Verificación]
    G --> H[Fin]
