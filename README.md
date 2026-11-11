# TP-FINAL-GRUPO-3-BLASCO
BOMBA DE INFUSION AUTOMATIZADA CON MONITOREO DE SEGURIDAD

Este proyecto consiste en el desarrollo de un prototipo de bomba de infusion de jeringa controlada mediante el microcontrolador PIC16F887. El sistema permite el control lineal de dosificacion de fluidos, seguimiento de volumen en tiempo real mediante un potenciometro deslizable (ADC), interfaz local con displays multiplexados y control/monitoreo remoto via comunicacion serie (UART).

La PC se comunica con la bomba a través del protocolo UART serie (9600 8N1).

Comandos UART Disponibles
'S': Start — Inicia la infusión.
'P': Pause — Detiene el motor e interrumpe la infusión.
'R': Rewind — Activa el rebobinado (retroceso) hacia el origen.


COMPONENTES:
Microcontrolador: PIC16F887
Actuador: Motor paso a paso NEMA 17 (TEAC Sinano)
Driver de Motor: A4988
Sensores:
Potenciómetro tipo slider (Mapeo ADC de volumen de jeringa 0-10 mL)
Microswitch fin de carrera (Seguridad final de jeringa)
Visualización Local: 2x Displays de 7 segmentos (Cátodo común) + 2x Transistores NPN
Comunicación: Módulo conversor USB a UART / RS232
Mecánica: Varilla roscada T8 + tuerca de avance + 1 varilla lisa de guiado

