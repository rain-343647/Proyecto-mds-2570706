# Proyecto-mds-2570706
# Sistema de Control para Tren Electromagnético con Arduino

## Descripción General

Este repositorio contiene el código fuente, los esquemas electrónicos y la documentación técnica de un **sistema de control de propulsión y frenado para un tren electromagnético a escala**, gestionado mediante un microcontrolador **Arduino**.

El proyecto implementa un sistema de conmutación electromagnética secuencial para impulsar el vehículo a lo largo de la vía, integrando una arquitectura de seguridad crítica basada en interrupciones por hardware (**Hardware Interrupts**) para gestionar un **Botón de Parada de Emergencia (E-Stop)** con tiempo de respuesta determinista y latencia mínima.

## Objetivos del Proyecto

* **Control de Propulsión Electromagnética:** Gestionar la activación y desactivación sincronizada de electroimanes de vía (estatores) para generar fuerzas de atracción y repulsión continuas.
* **Seguridad Funcional (Fail-Safe):** Implementar un mecanismo de parada de emergencia prioritario que interrumpa inmediatamente el suministro energético hacia las bobinas y active el protocolo de frenado.
* **Modularidad y Escalabilidad:** Diseñar un firmware estructurado bajo máquinas de estados finitos (FSM) que permita escalar el número de tramos de vía o integrar telemetría en futuras versiones.

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
