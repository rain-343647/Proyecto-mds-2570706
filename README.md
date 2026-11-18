# Proyecto-mds-2570706
# Sistema de Control para Tren Electromagnético con Arduino

## Descripción General

Este repositorio contiene el código fuente, los esquemas electrónicos y la documentación técnica de un **sistema de control de propulsión y frenado para un tren electromagnético a escala**, gestionado mediante un microcontrolador **Arduino**.

El proyecto implementa un sistema de conmutación electromagnética secuencial para impulsar el vehículo a lo largo de la vía, integrando una arquitectura de seguridad crítica basada en interrupciones por hardware (**Hardware Interrupts**) para gestionar un **Botón de Parada de Emergencia (E-Stop)** con tiempo de respuesta determinista y latencia mínima.

## Objetivos del Proyecto

* **Control de Propulsión Electromagnética:** Gestionar la activación y desactivación sincronizada de electroimanes de vía (estatores) para generar fuerzas de atracción y repulsión continuas.
* **Seguridad Funcional (Fail-Safe):** Implementar un mecanismo de parada de emergencia prioritario que interrumpa inmediatamente el suministro energético hacia las bobinas y active el protocolo de frenado.
* **Modularidad y Escalabilidad:** Diseñar un firmware estructurado bajo máquinas de estados finitos (FSM) que permita escalar el número de tramos de vía o integrar telemetría en futuras versiones.
¡Por supuesto! Vamos a integrar esos conceptos de gestión ágil (Épicas, Historias de Usuario, Criterios de aceptación con Gherkin y DoD) en el contexto de un proyecto fascinante: **el diseño y desarrollo de un Tren Electromagnético (Maglev)**.

Aquí tienes una propuesta estructurada lista para tu matriz y backlog:



## Sistema de Transporte Electromagnético

##  1. Definición de Épicas y Backlog (Matriz de Priorización - WSJF)

| ID Épica | Épica | Descripción | Valor de Negocio | Criticidad / Urgencia | Esfuerzo / Tamaño | **Puntuación WSJF** |
| --- | --- | --- | --- | --- | --- | --- |
| **EPI-01** | **Levitación Magnética (Maglev)** | Sistema de sustentación por campos magnéticos para eliminar la fricción física con los rieles. | 9 | 9 | 5 | 3.6 (Alta) |
| **EPI-02** | **Propulsión Lineal** | Motor síncrono lineal (LSM) para aceleración y frenado regenerativo eficiente. | 9 | 8 | 5 | 3.4 (Alta) |
| **EPI-03** | **Gestión de Energía y Vacío** | Optimización del consumo energético y sellado de sección tubular (opcional para alta velocidad). | 7 | 6 | 8 | 1.6 |
| **EPI-04** | **Seguridad y Control de Pasajeros** | Sistema de frenado de emergencia redundante, evacuación y monitoreo de cabina. | 10 | 10 | 3 | 6.6 (Máxima) |

---

##  2. Desglose en Historias de Usuario (HU), Tareas Técnicas (HT) y Requisitos No Funcionales (NFR)

###  : Levitación Magnética (EPI-01)

1. Como operador del sistema, quiero enviar corriente eléctrica a los electroimanes para lograr que el tren se eleve sobre el riel guía.
2. Como sistema de seguridad, quiero medir la distancia entre el chasis y la vía para mantenerla en el rango óptimo de 10 mm.
3. Como sistema de control, quiero compensar automáticamente las variaciones de carga de los vagones para evitar sacudidas durante el trayecto.
4. Como operador, quiero activar los patines mecánicos si la corriente principal cae para detener el tren de forma segura.
5. Como maquinista, quiero aumentar la frecuencia magnética del estátor para acelerar el tren progresivamente sin fricción mecánica.
6. Como sistema de tracción, quiero bloquear la propulsión si el tren no está levitando para evitar daños catastróficos en la vía.
7. Como sistema eléctrico, quiero recuperar la energía cinética durante la desaceleración para mejorar la eficiencia energética general.
8. Como desarrollador, quiero crear una rama exclusiva basada en mi código para aislar mis cambios de la rama principal.
9. Como estudiante, quiero crear y configurar mi archivo individual con mis datos personales para certificar la autoría de mis commits.
10. Como desarrollador, quiero abrir un Pull Request desde mi fork para enviar mis modificaciones al repositorio principal del profesor.
11. Como mantenedor del proyecto, quiero revisar las diferencias de los archivos para aprobar y fusionar el código de forma segura.
12. Como colaborador, quiero utilizar la opción de sincronización del fork para mantener mi repositorio al día con los aportes del equipo.
13. Como programador, quiero editar manualmente los marcadores de conflicto para unificar las modificaciones concurrentes sin perder lógica.
14. Como desarrollador, quiero aplicar un commit específico de otra rama usando git cherry-pick para rescatar código útil rápidamente.
15. Como mantenedor del proyecto, quiero eliminar las ramas ya fusionadas para mantener el repositorio ordenado y navegable.



---

##  3. Criterios de Aceptación 

Validemos una de las funcionalidades clave del sistema de control del tren:

Característica: Frenado regenerativo y de emergencia
  Como sistema de control central del tren Maglev
  Quiero activar los frenos magnéticos de emergencia ante una pérdida súbita de potencia
  Para detener el tren de manera segura y proteger a los pasajeros

  Escenario: Activación de frenos de emergencia por fallo de energía
    Dado que el tren circula a una velocidad crucero de 400 km/h
    Y se detecta una caída total en la red de suministro eléctrico principal
    Cuando el sistema de respaldo activa los frenos de corrientes parásitas (Eddy currents)
    Entonces el tren debe desacelerar de forma controlada sin superar los 1.5 G de fuerza de frenado para los pasajeros
    Y el tren debe detenerse por completo dentro de la zona de frenado designada
    Y las puertas de emergencia deben desbloquearse automáticamente al detenerse.




## ✅ 4. Definición de Terminado - DoD (Criterios INVEST)

Para asegurar que cada Historia de Usuario relacionada con el tren cumpla con los estándares de calidad antes de pasar a producción o pruebas físicas, se aplica el marco **INVEST** en el DoD:

* [I] **Independiente (Independent):** La HU puede desarrollarse y probarse sin depender de futuros despliegues de otras épicas.
* [N] **Negotiable (Negociable):** Los detalles de interfaz y umbrales de velocidad fueron conversados y acordados con el equipo de ingeniería mecánica y de control.
* [V] **Valiosa (Valuable):** Aporta valor directo a la seguridad o eficiencia operativa del tren Maglev.
* [E] **Estimable (Estimable):** El equipo de hardware y software ha dimensionado el esfuerzo en Story Points (ej. 5 u 8 puntos).
* [S] **Pequeña (Small):** Se puede completar dentro de un ciclo de Sprint de 2 semanas.
* [T] **Testendible (Testable):** Cuenta con criterios de aceptación claros validados mediante simulaciones de campo magnético y pruebas en banco de pruebas físico.

## Arquitectura del Sistema

El sistema se divide en tres subsistemas principales:

1. **Unidad de Procesamiento y Control (Arduino):** Ejecuta la lógica de control, monitorea los sensores de posición y gestiona las interrupciones de seguridad.
2. **Etapa de Potencia y Conmutación:** Compuesta por transistores MOSFET de canal N (o módulos de relés de estado sólido) y diodos *flyback* para aislar el microcontrolador de las cargas inductivas de alto amperaje de las bobinas.
3. **Subsistema de Seguridad (E-Stop):** Circuito físico conectado a un pin de interrupción externa (`INT0` / `INT1`), configurado con resistencia *pull-up* interna y filtrado *antirrebote* (debounce) por hardware/software.

### Diagrama de Bloques

```text
+-----------------------------------+
|      Fuente de Alimentación       |
|   (Lógica: 5V | Potencia: 12V+)   |
+-----------------+-----------------+
                  |
       +----------+----------+
       |                     |
       v                     v
+------+------+       +------+------+
|   Arduino   |       |   Etapa de  |
|   (Control) |======>|   Potencia  |
+------+------+  PWM/ |  (MOSFETs)  |
       ^        Digital+------+------+
       |                     |
+------+------+              v
|  Botón de   |       +------+------+
| Parada (ISR)|       | Electroimán |
+-------------+       |  (Vía/Tren) |
                      +-------------+
```

El software de control está diseñado bajo un enfoque modular orientado a objetos, dividido en cuatro capas funcionales independientes para facilitar el desarrollo colaborativo y las pruebas unitarias

```text
+-----------------------------------------------------------------------------+
|                  CAPA 4: INTERFAZ Y TELEMETRÍA (HMI / Logs)                 |
|  - Monitoreo en tiempo real (velocidad, brecha de aire, consumo energético) |
|  - Registro de eventos, alertas críticas y diagnóstico de subsistemas       |
+-----------------------------------------------------------------------------+
                                      ^
                                      | (Lectura de estado / Comandos)
                                      v
+-----------------------------------------------------------------------------+
|               CAPA 3: NÚCLEO DE COORDINACIÓN (MaglevCore)                   |
|  - Máquina de Estados Finitos (FSM): REPOSO -> LEVITANDO -> EN_MARCHA       |
|  - Enclavamiento de Seguridad (Interlock): Bloquea tracción si no levita    |
+-----------------------------------------------------------------------------+
                     ^                                   ^
                     | (Control EMS)                     | (Control LSM)
                     v                                   v
+---------------------------------------+ +-----------------------------------+
|    CAPA 2A: SUBSISTEMA LEVITACIÓN     | |    CAPA 2B: SUBSISTEMA TRACCIÓN   |
|     (LevitationController - EMS)      | |    (PropulsionController - LSM)   |
|  - Regulación de corriente (I)        | |  - Control de frecuencia del      |
|  - Cálculo de fuerza (F = k * I^2)    | |    estátor y aceleración lineal   |
|  - Control PID de brecha (10.0 mm)    | |  - Frenado regenerativo (kWh)     |
+---------------------------------------+ +-----------------------------------+
                     ^                                   ^
                     | (Señales PWM / Lectura)           | (Fases Trifásicas)
                     v                                   v
+-----------------------------------------------------------------------------+
|                 CAPA 1: ABSTRACCIÓN DE HARDWARE (HAL / Planta)              |
|  - Sensores inductivos de distancia (Air Gap) y sensores de corriente       |
|  - Electroimanes de guía, estátor lineal en vía y patines de emergencia     |
+-----------------------------------------------------------------------------+
```