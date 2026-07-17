<p>
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=700&size=22&duration=2400&pause=600&color=7F5AF0&center=true&vCenter=true&width=600&lines=Gabriel+Eduardo+Bojaca+Munar">
</p>
<p>
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=700&size=22&duration=2400&pause=600&color=7F5AF0&center=true&vCenter=true&width=600&lines=Maria+Fernanda+Morillo+Tovar">
</p>

## Descripcion 
Con base en los requerimientos del laboratorio, la solución debe integrar el control de las articulaciones del Phantom X Pincher X100 mediante ROS 2 Jazzy, implementando las diferentes actividades solicitadas: movimientos individuales, simultáneos y secuenciales, interpolación de trayectorias, cinemática directa e inversa, enseñanza y repetición de poses, trazado de figuras y una coreografía robótica. Todo el sistema debe respetar los límites seguros de cada articulación, validar las posiciones antes de ejecutarlas y permitir la interacción tanto en RViz como con el robot físico. La arquitectura desarrollada recibe comandos del usuario, verifica que las configuraciones sean alcanzables y seguras, calcula la trayectoria o la solución de cinemática correspondiente, ejecuta el movimiento del manipulador y retroalimenta el estado del robot para continuar con la siguiente acción hasta finalizar la tarea.

## Diagrama de flujo 

```mermaid
flowchart TD
    A([Inicio]) --> B[Inicializar ROS 2 y conectar Phantom X Pincher X100]
    B --> C[Ubicar robot en posición segura]
    C --> D[Recibir comando del usuario]

    D --> E{¿Tipo de operación?}

    E -->|Movimiento articular| F[Validar límites articulares]
    E -->|Cinemática directa| G[Calcular posición cartesiana]
    E -->|Cinemática inversa| H[Calcular configuración articular]
    E -->|Trayectoria| I[Generar interpolación]
    E -->|Repetición de poses| J[Cargar poses desde YAML]
    E -->|Dibujar/Coreografía| K[Generar secuencia de puntos]

    F --> L[Enviar posiciones a los servomotores]
    G --> L
    H --> M{¿Solución válida?}
    M -->|Sí| L
    M -->|No| N[Mostrar error de punto no alcanzable]
    N --> D

    I --> L
    J --> L
    K --> H

    L --> O[Monitorear estado del robot]
    O --> P{¿Movimiento completado?}

    P -->|No| O
    P -->|Sí| Q{¿Existen más acciones?}

    Q -->|Sí| D
    Q -->|No| R[Regresar a posición segura]
    R --> S([Fin])
```
