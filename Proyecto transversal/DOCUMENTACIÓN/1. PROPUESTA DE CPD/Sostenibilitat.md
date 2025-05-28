**Caso 1: Escenario "Real" (Instancias Cloud AWS en us-east-1)**

**1- Recursos empleados:**  
Servicios desplegados: 5 instancias Amazon EC2 (t2.micro, t2.large, t3.large) en us-east-1.  
Recursos consumidos (potencia estimada activa):  
t2.micro: \~0.01 kW 1 vCPU 1 GiB Memoria  
t2.large: \~0.04 kW 2 vCPU 8 GiB Memoria  
t3.large: \~0.05 kW 2 vCPU 8 GiB Memoria  
Previsión de uso: \~720 horas/mes por instancia.

\----------------------------------------------------------------------------------------------------

**2- Estimación del consumo energético y la huella de carbono (AWS us-east-1):**

A. Consumo energético de las instancias (mensual):

- Base de datos (t2.micro): 1.3 kWh/mes  
- Audio y video (t2.large): 5.2 kWh/mes  
- DNS (t2.micro): 1.3 kWh/mes  
- WEB (t2.micro): 1.3 kWh/mes  
- NFS y monitoreo (t3.large): 6.5 kWh/mes

Consumo energético total estimado de instancias: 15.6 kWh/mes

B. Consumo energético del tráfico de streaming (ejemplo):  
Suponiendo 100 GB/mes y 0.06 kWh/GB \= 6 kWh/mes.

C. Consumo energético total mensual estimado (Instancias \+ Ejemplo Streaming):  
15.6 kWh \+ 6 kWh \= 21.6 kWh/mes.

D. Conversión a emisiones (kg CO2 eq.):

Factor de emisión para AWS us-east-1: \~0.35 kg CO2eq/kWh.  
Huella de carbono instancias: 15.6 kWh/mes \* 0.35 \= 5.46 kg CO2eq/mes.  
Huella de carbono streaming (ejemplo): 6 kWh/mes \* 0.35 \= 2.1 kg CO2eq/mes.  
Huella de carbono total estimada mensual (AWS): 7.56 kg CO2eq/mes.

\----------------------------------------------------------------------------------------------------

**3- Propuesta de medidas de reducción u optimización (AWS):**  
**Horas de funcionamiento**: Ya limitado; analizar si se puede reducir más.  
**Regiones/Energía renovable**: AWS se compromete a 100% renovable para 2025\. Evaluar regiones con menor huella si la latencia lo permite.  
**Optimización de Instancias**: Usar AWS Compute Optimizer, considerar instancias Graviton, implementar Auto Scaling.

**Caso 2: Escenario "Teórico" (CPD On-Premise en Noruega)**

**1- Identificar los recursos empleados:**

Infraestructura IT: 9 Servidores físicos (5 principales, 4 soporte) en 3 racks. Switches, patches, routers.

Especificaciones Servidores Principales:

- DNS: 2-4 núcleos, 4GB RAM, SSD 120GB  
- BBDD: 8 núcleos, 32-64GB RAM, SSDs en RAID  
- WEB: 4 núcleos, 8-16GB RAM, SSD 220GB  
- Audio/Video: 8 núcleos \+ GPU, 32GB RAM, SSD \+ HDD  
- NFS \+ Monitoraje: 4 núcleos, 16GB RAM, SSD \+ RAID HDDs

**Infraestructura Eléctrica**: SAI Eaton 9PX 5000i (eficiencia 98%), alimentación redundante.  
**Infraestructura de Refrigeración**: Ubicación en Noruega (clima frío), suelo técnico, pasillos fríos/calientes, aire frío exterior.  
**Previsión de uso**: \~720 horas/mes para servidores.

\----------------------------------------------------------------------------------------------------

2- Estimar el consumo energético y la huella de carbono (CPD Noruega):

A. Consumo energético IT (Servidores \+ Red):  
Potencia IT total estimada: \~1.15 kW.  
Consumo energético IT mensual: 1.15 kW \* 130 h/mes \= 149.5 kWh/mes.

B. Pérdidas del SAI (Eaton 9PX 5000i):  
Pérdidas del SAI mensuales: \~3.05 kWh/mes.  
Energía total para IT \+ SAI: \~152.55 kWh/mes.

C. Consumo del sistema de refrigeración (PUE):  
PUE estimado (gracias a Noruega y diseño): 1.18.  
Energía total del CPD mensual: 152.55 kWh/mes \* 1.18 \= \~180.01 kWh/mes.

D. Consumo energético del tráfico de streaming (ejemplo):  
Suponiendo 100 GB/mes y 0.06 kWh/GB \= 6 kWh/mes.  
Nueva Energía total CPD (con streaming): \~187.23 kWh/mes.

E. Conversión a emisiones (kg CO2 eq.)  
Factor de emisión para Noruega (red muy limpia, principalmente hidroeléctrica): \~0.015 kg CO2eq/kWh.  
Huella de carbono total estimada mensual (CPD Noruega, con ejemplo streaming:  
187.23 kWh/mes \* 0.015 kg CO2eq/kWh \= \~2.81 kg CO2eq/mes.  
(Sin streaming: \~2.70 kg CO2eq/mes.

F. Resumen Huella de Carbono Mensual Estimada (CPD Noruega:  
Sin streaming: \~2.70 kg CO2eq/mes.  
Con ejemplo de 100GB streaming: \~2.81 kg CO2eq/mes.

\----------------------------------------------------------------------------------------------------

**3- Propuesta de medidas de reducción u optimización (CPD Noruega):**

Para el diseño y la futura operación de nuestro CPD, hemos integrado la sostenibilidad como un eje fundamental. Nuestras decisiones se han orientado a minimizar el impacto ambiental y asegurar una eficiencia operativa a largo plazo.

**Optimización del Consumo Energético**: Para optimizar el consumo de energía, hemos tomado diversas medidas clave. En primer lugar, hemos seleccionado equipos de bajo consumo energético, como es el caso del sistema **SAI Eaton 9PX** que incorporaremos, el cual ofrece una eficiencia de hasta el **98%**, reduciendo así las pérdidas energéticas. Adicionalmente, hemos dimensionado los servidores de acuerdo con las necesidades específicas de cada servicio, evitando el sobredimensionamiento y el consecuente derroche de recursos.

**Uso de Energía Verde para el CPD**: Consideramos crucial fomentar el uso de energía verde para nuestro CPD. Por ello, estamos analizando activamente la contratación con proveedores que garanticen un suministro proveniente de fuentes renovables. Nuestro objetivo es alimentar las instalaciones con energía limpia en la medida de lo posible, con el fin de reducir nuestra huella de carbono asociada al consumo eléctrico.

**Ahorro en Longitud de Cableado**: En la planificación de la infraestructura física del CPD, hemos diseñado una distribución del cableado pensada para la eficiencia. Hemos optado por una topología en estrella que parte del rack de comunicaciones principal hacia los demás racks. Esta configuración nos permite minimizar la longitud total del cableado necesario, lo cual no solo implica un ahorro de material, sino que también facilita una mejor gestión térmica y reduce las posibles pérdidas de señal o energía.

**Sistemas de Circulación de Aire que Aprovechan Condiciones Naturales**: La elección de Noruega como ubicación para nuestro CPD nos ofrece la ventaja de un clima favorable para la refrigeración. Hemos diseñado la sala con un suelo técnico elevado y un techo técnico que facilita la canalización del aire frío del exterior. Este sistema, combinado con la estrategia de pasillos fríos y calientes, nos permitirá aprovechar al máximo las condiciones naturales para la refrigeración, disminuyendo así la necesidad de sistemas de climatización mecánica y su elevado consumo energético.

**Parada de Equipos de Comunicaciones en Ausencia de Carga**: Para los equipos de red y comunicaciones, hemos establecido políticas de gestión energética inteligente. Cuando la operativa lo permita y no se comprometa la disponibilidad de los servicios, configuraremos estos dispositivos para que entren en modos de bajo consumo o lleven a cabo una parada selectiva de componentes durante los periodos de baja o nula actividad. Esto nos asegurará un uso más racional de la energía.