# TP-FINAL-GRUPO-3-BLASCO
BOMBA DE INFUSION AUTOMATIZADA CON MONITOREO DE SEGURIDAD

Este proyecto consiste en el desarrollo de un prototipo de bomba de infusion de jeringa controlada mediante el microcontrolador PIC16F887. El sistema permite el control lineal de dosificacion de fluidos, seguimiento de volumen en tiempo real mediante un potenciometro deslizable (ADC), interfaz local con displays multiplexados y control/monitoreo remoto via comunicacion serie (UART).

La PC se comunica con la bomba a través del protocolo UART serie (9600 8N1).

COMNADOS UART DISPONIBLES:

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

  Mecánica: Varilla roscada M8 + tuerca de avance + 1 varilla lisa de guiado + jeringa 10mL
  

CRITERIOS DE ACEPTACIÓN (DOD)
  - TIMER0: EL refresco de los 2 display de 7 segementos multiplexados funciona mediante interrupción por overflow del Timer0 a una frecuencia imperceptible a la vista sin detener la ejecución del bucle principal ni afectar la velocidad del motor.
  - ADC: el canal RA0/AN0 lee de forma continua la posición del potenciometro tipo slider, convirtiendo la tensión en una escala de volumen de 00 a 10mL que se muestra en tiempo real tanto en los displays como en la telemetría
  - Comunicación serie bidireccional: el módulo EUSART opera a 9600 baudios con recepción asistida por interrupcion (RCIF) sin errores de overrun. Envía telemetría periódica del volumen restante hacia la PC y ejecuta los comandos entrantes de control ('S', 'P' y 'R' mencionados anteriormente)
  - Interrupción externa: al presionar el pulsador de parada de emergencia, el sistema detiene de inmediato el avance del motor, deshabilita la etapa de potencia y activa la alarma sonora sin esperar que termine el ciclo actual del programa
  - Dosificación y control de caudal: el motor paso a paso impulsado por el driver desplaza el émbolo de la jeringa de manera lineal y sin pérdida de pasos, respetando los tiempos de infusión configurados (aproximadamente 2 minutos en modo rápido y 12 minutos en modo lento)
  - Protección mecánica por finales de carrera: Al alcanzar el tope de jeringa vacía, el sistema detiene automáticamente la infusión y pasa a un estado de pausa para evitar daños mecánicos o sobrecorriente.
  - Seguridad eléctrica y térmica: la etapa de potencia (12 V) y la lógica (5 V) comparten masa única con capacitores de desacople. Por su parte, el driver tiene calibrado su voltaje de referencia (0.4 V - 0.5V) y desenergiza las bobinas en estado de reposo para evitar sobrecalentamiento.
