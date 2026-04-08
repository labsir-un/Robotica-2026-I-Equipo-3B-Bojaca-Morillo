<div align="center">
<picture>
    <source srcset="https://imgur.com/5bYAzsb.png" media="(prefers-color-scheme: dark)">
    <source srcset="https://imgur.com/Os03JoE.png" media="(prefers-color-scheme: light)">
    <img src="https://imgur.com/Os03JoE.png" alt="Escudo UNAL" width="350px">
</picture>

<h3>Curso de Robótica 2026-I</h3>

<h1>Compilado de Informes de Laboratorio de Robótica</h1>

<h2>Profesores: <br>Pedro Fabián Cárdenas Herrera <br> Manuel Felipe Carranza Montenegro</h2>

<h4>Nombre Integrante 1<br>
    Nombre Integrante 2<br>
    Nombre Integrante 3</h4>

<p>
  <img alt="Ubuntu 24.04 LTS" src="https://img.shields.io/badge/Ubuntu-24.04%20LTS-E95420?logo=ubuntu&logoColor=white">
  <img alt="ROS 2 Jazzy" src="https://img.shields.io/badge/ROS%202-Jazzy-22314E?logo=ros&logoColor=white">
  <img alt="ABB" src="https://img.shields.io/badge/ABB-robotics-5E8D5A?logo=ABB&logoColor=white">
  <img alt="RobotStudio" src="https://img.shields.io/badge/RobotStudio-2022-41C9D0?logo=robotstudio&logoColor=white">
  <img alt="Yaskawa" src="https://img.shields.io/badge/Yaskawa-Robotics-FFE500?logo=Yaskawa&logoColor=black">
  <img alt="RoboDK" src="https://img.shields.io/badge/RoboDK-Simulation-0092F3?logo=RoboDK&logoColor=white">
  <img alt="EPSON" src="https://img.shields.io/badge/EPSON-Robotics-00B0B9?logo=Epson&logoColor=white">
  <img alt="Robotis Dynamixel" src="https://img.shields.io/badge/Robotis%20Dynamixel-Servos-FF6600?logo=robotis&logoColor=white">
  <img alt="Python" src="https://img.shields.io/badge/Python-Programming-3776AB?logo=python&logoColor=white">
  <img alt="C" src="https://img.shields.io/badge/C-Programming-A8B9CC?logo=c&logoColor=white">
  <img alt="Intel" src="https://img.shields.io/badge/Intel-Processors-0071C5?logo=intel&logoColor=white">
  <img alt="Matlab" src="https://img.shields.io/badge/Matlab-Software-0076A8?logo=matlab&logoColor=white">
  <img alt="Visual Studio Code" src="https://img.shields.io/badge/Visual%20Studio%20Code-Editor-007ACC?logo=visualstudiocode&logoColor=white">
</p>
</div>

---

## Descripción

Este repositorio corresponde al desarrollo de las actividades del curso de **Robótica 2026-I**.  
Aquí se documentan los laboratorios, avances, resultados y la presentación de los integrantes del equipo.

---

## Objetivos del repositorio

- Organizar el desarrollo de los laboratorios del curso.
- Documentar procedimientos, resultados y evidencias.
- Presentar formalmente a los integrantes del equipo.
- Mantener una estructura clara y ordenada para la evaluación.

---

## Integrantes del equipo

### Integrante 1
<div align="center">
  <img src="./assets/integrantes/integrante1.jpg" alt="Foto integrante 1" style="border-radius: 50%; width: 180px;"><br>
</div>

- **Nombre completo:** Nombre Apellido
- **Carrera:** Ingeniería Mecatrónica
- **Correo institucional:** nombre@unal.edu.co
- **Usuario de GitHub:** [usuariogithub](https://github.com/usuariogithub)
- **Rol en el equipo:** Ej. Integración ROS 2, documentación, simulación
- **Intereses:** Robótica móvil, visión artificial, automatización
- **Descripción breve:**  
  Escribe aquí una breve presentación personal y académica del integrante.

---

### Integrante 2
<div align="center">
     <img src="./assets/integrantes/integrante2.jpg" alt="Foto integrante 2" style="border-radius: 50%;<img width="391" height="626" alt="Captura de pantalla 2026-04-01 200146" src="https://github.com/user-attachments/assets/7c16a57b-bad2-457f-859a-fac801ad0f4b" />
 width: 180px;"><br>
</div>
```mermaid
---
config:
  theme: redux
---
flowchart TB
    n1(["Inicio"]) --> n2["Iniciar ROS2"]
    n2 --> n3["Crear nodo <br><code>TurtleWriter</code>"]
    n3 --> n4["Crear publicador de<br>velocidad <code>/turtle1/cmd_vel</code>"]
    n4 --> n5["Crear suscriptor de pose<br><code>/turtle1/pose</code>"]
    n5 --> n6["Crear clientes de servicios <br><code>teleport_absolute</code>, <code>set_pen</code>"]
    n6 --> n7["Esperar a recibir la primera <br>pose de la tortuga"]
    n7 --> n8["Mover tortuga a posición inicial"]
    
    %% Conexión al hilo de teclado (paralelo)
    n7 --- n15(["Bucle de lectura<br>teclado"])
    
    %% Flujo principal
    n8 --> n9["Inicializar variables de renglones y conteo de letras"]
    n9 --> n10["Crear y arrancar hilo de lectura de teclado"]
    n10 --> n11["Ejecutar bucle de ROS 2"]
    n11 --> n12{"¿Se solicita cierre ?"}
    n12 -- Sí --> n13["Destruir nodo y cerrar ROS 2"]
    n13 --> n14(["FIN"])
    n12 -- NO --> n7
    
    %% Hilo de Teclado
    n15 --> n16["Leer tecla del usuario (<code>get_key</code>)"]
    n16 --> n17["Convertir tecla a mayúscula"]
    n17 --> n18{"¿Nodo ocupado (<code>busy</code> = True)?"}
    n18 -- Si --> n19["Ignorar tecla / esperar siguiente tecla"]
    n18 -- NO --> n20{"¿Tecla es una letra válida (J, N, G, A, C, P, M, E, B)?"}
    n19 --> n18
    n20 -- NO --> n21["Ignorar tecla / volver a leer"]
    n20 -- Sí --> n22["Marcar nodo como ocupado (<code>busy = True</code>)"]
    n21 --> n16 
    
    %% Ejecución de Dibujo
    n22 --> n23["Mostrar mensaje: Dibujando [letra]..."]
    n23 --> n24["Llamar función de dibujo<br>draw_"]
    n24 --> n25(["Funcion draw_"])
    n25 --> n27["Marcar nodo como libre (<code>busy = False</code>)"]
    n27 --> n26["Mostrar mensaje: Letra [letra] lista."]
    n26 --> n16
    
    %% Subflujo de la Función draw_ (Dentro de 25)
    subgraph Proceso de Dibujo
        n25 --> n28["Guardar posición inicial de la letra"]
        n28 --> n29["Configurar pluma: levantar o bajar"]
        n29 --> n30["Ejecutar secuencia de movimientos lineales ( <code>move_line</code> )"]
        n30 --> n31["Ejecutar giros necesarios (<code>rotate</code>)"]
        n31 --> n32["Completar la forma de la letra"]
        n32 --> n33["Llamar a <code>finish_letter(...)</code>"]
    end
    
    %% Flujo de finish_letter (Subflujo de 33)
    subgraph Finalizar Letra
        n33 --> n36(["Funcion finish_letter"])
        n36 --> n34["Levantar pluma"]
        n34 --> n35["Incrementar contador de letras en la línea actual"]
        n35 --> n37{"¿Contador de letras ≥ 4?"}
    end
    
    %% Salto de Línea
    n37 -- SÍ --> n38["Mostrar mensaje “Salto de línea”"] 
    n38 --> n39["Reiniciar contador de letras a 0"]
    n39 --> n40["Incrementar número de renglón (<code>current_line += 1</code>)"]
    n40 --> n41["Calcular nueva posición de inicio de renglón"]
    n41 --> n44
    
    %% No Salto de Línea
    n37 -- NO --> n42["Calcular nueva posición en X para la siguiente letra"]
    n42 --> n43["Mantener la misma altura (<code>start_y</code>)"]
    n43 --> n44["Teletransportar tortuga a nueva posición de inicio de letra"]
    
    %% Continuación
    n44 --> n45["Bajar pluma de nuevo para la próxima letra"]
    n45 --> n25
    
    %% Estilos (Solo para asegurar formas y bordes, sin forzar el color de fondo)
    style n12 shape:diamond
    style n18 shape:diamond
    style n20 shape:diamond
    style n37 shape:diamond
    
    style n1, n14, n15, n25, n36 rx:100,ry:100
```

- **Nombre completo:** Maria Fernanda Morillo Tovar
- **Carrera:** Ingeniería Mecatrónica
- **Correo institucional:** mmorillot@unal.edu.co
- **Usuario de GitHub:** [mmorillot](https://github.com/mmorillot)
- **Rol en el equipo:** Ej. Modelado, programación, control
- **Intereses:** Control de robots, manipulación
- **Descripción breve:**
  Actualmente estoy en décimo semestre de Ingeniería. Me interesa el área de control de robots, especialmente entender cómo funcionan y cómo se pueden hacer más precisos. También me llama la atención la parte de manipulación. Me gusta aprender cosas nuevas y seguir mejorando en temas relacionados con la robótica.


---
<div align="center">
     Diagrama de flujo de acciones del robot.
</div>
<p align="center">
<img width="419" height="672" alt="image" src="https://github.com/user-attachments/assets/2f3d15df-65fb-41ce-8a59-1bb9fa741272" />
</p>


