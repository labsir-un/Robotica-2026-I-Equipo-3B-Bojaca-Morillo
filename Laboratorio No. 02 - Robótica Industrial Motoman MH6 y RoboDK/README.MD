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


# Laboratorio No. 02 – Robótica Industrial
## Análisis y Operación del Manipulador Motoman MH6 usando RoboDK

---
---

# Introducción

En este laboratorio se trabajó con el manipulador industrial Motoman MH6 utilizando el software RoboDK para programar trayectorias, simular movimientos y ejecutar figuras mediante control cartesiano.

El objetivo principal fue comprender el funcionamiento del robot, los modos de operación manual y la comunicación entre RoboDK y el manipulador físico. Además, se desarrolló una trayectoria polar y un sistema de dibujo automatizado usando listas de coordenadas programadas en Python.

---

# Comparación entre Motoman MH6 y ABB IRB140

| Característica | Motoman MH6 | ABB IRB140 |
|---|---|---|
| Fabricante | Yaskawa Motoman | ABB |
| Grados de libertad | 6 | 6 |
| Carga máxima | 6 kg | 6 kg |
| Alcance | 1422 mm | 810 mm |
| Repetibilidad | ±0.08 mm | ±0.03 mm |
| Aplicación | Soldadura, manipulación | Ensamble y precisión |
| Software | RoboDK | RobotStudio |
| Velocidad | Alta | Media-Alta |

## Análisis

El Motoman MH6 posee un alcance mucho mayor, permitiendo trabajar en áreas industriales más amplias. El ABB IRB140 ofrece mayor precisión y repetibilidad, siendo ideal para aplicaciones académicas y tareas de ensamblaje fino.

---

# Configuraciones Home1 y Home2

## Home1

La posición Home1 corresponde a la posición inicial segura del robot:

- Todas las articulaciones se encuentran alineadas.
- Reduce riesgo de colisiones.
- Facilita la ejecución de programas automáticos.

## Home2

La posición Home2 corresponde a una postura alternativa:

- Cambia orientación de algunos ejes.
- Permite acceder mejor a ciertas zonas de trabajo.

## Mejor configuración

La configuración Home1 es más adecuada debido a que ofrece mayor seguridad y estabilidad para iniciar movimientos automáticos y manuales.

---

# Movimiento manual del Motoman MH6

## Movimiento por articulaciones

Se utiliza el modo:

```python
Joint
```

Permite mover individualmente cada eje del robot.

## Movimiento cartesiano

Se utiliza el modo:

```python
Cartesian
```

Permite mover el TCP del robot en:

- X
- Y
- Z

y también realizar rotaciones:

- Rx
- Ry
- Rz

---

# Control de velocidad

El Motoman MH6 permite modificar la velocidad manual mediante porcentajes visibles en la interfaz.

Ejemplos:

- 10%
- 25%
- 50%
- 100%

## Cambio de velocidad

El cambio se realiza desde el panel de control del robot seleccionando el porcentaje deseado.

---

# Uso de RoboDK

## Aplicaciones principales

RoboDK permite:

- Simular robots industriales.
- Programar trayectorias.
- Validar movimientos.
- Generar código automático.
- Controlar robots físicos.

## Comunicación con el robot

La comunicación se realiza mediante Ethernet y protocolos TCP/IP utilizando drivers compatibles con el controlador Motoman.

RoboDK calcula las trayectorias y envía instrucciones al robot para ejecutar movimientos reales.

---

# Comparación RoboDK vs RobotStudio

| Característica | RoboDK | RobotStudio |
|---|---|---|
| Compatibilidad | Multimarca | ABB |
| Facilidad de uso | Alta | Media |
| Programación offline | Sí | Sí |
| Simulación | Sí | Sí |
| Aplicación | General | Especializada ABB |

## Análisis

RoboDK es una plataforma más flexible y sencilla para programación general de robots industriales, mientras que RobotStudio está enfocado específicamente en robots ABB.

---

# Explicación del código desarrollado

El programa desarrollado en Python utiliza la API de RoboDK para controlar el manipulador Motoman MH6 y ejecutar trayectorias automáticamente.

## Librerías utilizadas

```python
from robodk.robolink import *
from robodk.robomath import *
import math
import time
```

Estas librerías permiten:

- Conectar RoboDK con el robot.
- Realizar transformaciones matemáticas.
- Ejecutar movimientos cartesianos.
- Generar trayectorias polares.

---

# Inicialización del robot

El programa inicia conectándose a RoboDK:

```python
RDK = Robolink()
```

Luego se selecciona el robot:

```python
robot = RDK.ItemUserPick("Selecciona un robot", ITEM_TYPE_ROBOT)
```

Posteriormente se asigna el frame de trabajo:

```python
frame_name = "Frame_from_Target1"
frame = RDK.Item(frame_name, ITEM_TYPE_FRAME)
robot.setPoseFrame(frame)
```

---

# Configuración de velocidad

Se configura la velocidad del robot:

```python
robot.setSpeed(300)
robot.setRounding(1)
```

- `setSpeed(300)` establece velocidad de 300 mm/s.
- `setRounding(1)` suaviza trayectorias.

---

# Movimiento inicial

El robot se mueve primero a Home:

```python
robot.MoveJ([0,0,0,0,0,0])
```

Luego se desplaza a una posición segura:

```python
robot.MoveL(transl(x_dibujo, y_dibujo, z_surface + z_safe))
```

---

# Generación de trayectoria polar

La trayectoria polar se genera usando ecuaciones paramétricas.

## Ecuaciones utilizadas

```python
x = (A * math.cos(t)) / (1 + math.sin(t)**2)
y = (A * math.sin(t) * math.cos(t)) / (1 + math.sin(t)**2)
```

Estas ecuaciones generan una curva polar suave.

## Movimiento del robot

El robot recorre la trayectoria usando:

```python
robot.MoveL(transl(x_rot, y_rot, z_surface))
```

El movimiento lineal permite mantener continuidad en el dibujo.

---

# Sistema de dibujo mediante coordenadas

El arreglo:

```python
posiciones = [...]
```

contiene cientos de coordenadas XYZ utilizadas para dibujar texto y figuras.

Cada coordenada define:

- X → posición horizontal.
- Y → posición vertical.
- Z → altura del marcador.

## Interpretación del eje Z

- `z = 0` → marcador tocando superficie.
- `z = 5` → marcador levantado.

Esto permite simular:

- escritura,
- trazado,
- separación entre letras.

---

# Rotación y offset del dibujo

El programa aplica rotación y desplazamiento usando:

```python
x_rot = y + x_letras
y_rot = x + y_letras
```

Esto permite:

- cambiar orientación del dibujo,
- posicionarlo correctamente en el plano de trabajo.

---

# Ejecución del dibujo

El robot recorre todas las posiciones:

```python
for x, y, z in posiciones:
```

Dependiendo del valor de Z:

- baja para dibujar,
- sube para desplazarse sin marcar.

---

# Finalización

Al terminar:

```python
robot.MoveJ([0,0,0,0,0,0])
```

el robot regresa a Home de manera segura.

---

# Diagrama de flujo

```text
Inicio
   ↓
Conexión con RoboDK
   ↓
Selección del robot
   ↓
Configuración del frame
   ↓
Definición de velocidad
   ↓
Movimiento a Home
   ↓
Generación trayectoria polar
   ↓
Dibujo usando coordenadas
   ↓
Movimiento final seguro
   ↓
Retorno a Home
   ↓
Fin
```

---

# Resultados obtenidos

- Se logró controlar el Motoman MH6 desde RoboDK.
- Se ejecutaron trayectorias cartesianas correctamente.
- El robot dibujó figuras usando listas de coordenadas.
- Se implementó una trayectoria polar funcional.
- Se validó la comunicación entre RoboDK y el manipulador físico.

---

# Conclusiones

- RoboDK facilita la programación y simulación de robots industriales.
- El Motoman MH6 permite ejecutar trayectorias complejas con buena precisión.
- Las trayectorias polares pueden implementarse mediante ecuaciones matemáticas.
- El uso de coordenadas XYZ permite automatizar dibujos y trayectorias.
- La programación offline reduce riesgos antes de ejecutar movimientos reales.

---

# Archivos anexos

- Código Python de RoboDK.
- Video de simulación.
- Evidencia física del robot.
- Capturas de pantalla.
- Trayectoria polar implementada.

---

# Referencias

- Manual Motoman MH6
- Documentación RoboDK
- API RoboDK Python
- Material de laboratorio de Robótica Industrial
- https://www.monografias.com/trabajos33/coordenadas-polares/coordenadas-polares
