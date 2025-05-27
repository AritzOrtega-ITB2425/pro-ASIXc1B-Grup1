# pro-ASIXc1B-Grup1

![InnovateTech.PNG](assets/img/InnovateTech.PNG)

Repositorio oficial del proyecto transversal del Grupo 1.

---

## Índice:

- [1. Propuesta de CPD](#1-propuesta-de-cpd)
- [2. Implantación de los servicios de audio y vídeo](#2-implantación-de-los-servicios-de-audio-y-vídeo)
- [3. Diseño e implementación de una base de datos](#3-diseño-e-implementación-de-una-base-de-datos)
- Sostenibilidad (Nota: Este parece un punto general, si es un apartado específico, habría que crearlo y enlazarlo)

Manuales:
-
  - [BBDD](manuales/SMB%20y%20Monitoreo%20%28manual%29.pdf)
  - [Audio y Video](manuales/SMB%20y%20Monitoreo%20%28manual%29.pdf)
  - [SMB y Monitoreo](manuales/SMB%20y%20Monitoreo%20%28manual%29.pdf)
  - [DNS](manuales/SMB%20y%20Monitoreo%20%28manual%29.pdf)
  - [Web](manuales/SMB%20y%20Monitoreo%20%28manual%29.pdf)

---

## 1. Propuesta de CPD

Propuesta para el Centro de Procesamiento de Datos (CPD) de InnovateTech, enfocada en eficiencia, seguridad y sostenibilidad.

### 1.1. Ubicación física

*   **Localización:** **Innovation Dock, Stavanger, Noruega**. Elegida por el clima favorable (refrigeración natural), economía en crecimiento y apoyo a proyectos sostenibles.
    ![Innovation Dock Stavanger](assets/img/cpd/innovation_dock_stavanger.png)
*   **Climatización:**
    *   Sistema: Suelo técnico para flujo de aire frío exterior, aprovechando el clima local.
    *   Temperatura: 18-23°C, controlada por sensores con alertas.
    *   Humedad: Controlada por el mismo sensor de temperatura.
    *   Limpieza del aire: Sistemas de purificación en conductos.
*   **Identificación de la sala:** Acceso restringido mediante tarjetas individuales por coste, fiabilidad y facilidad de gestión.
*   **Distribución y gestión del cableado:** Topología en estrella desde el rack de comunicaciones. Tipos: UTP Cat6A (LAN), Fibra OM4/SM (interconexión racks), HDMI/DP (monitores), Alimentación. Todo etiquetado.
*   **Suelo y techo técnico:** Diseño para optimizar el flujo de aire (pasillos fríos/calientes), facilitando la refrigeración natural y la extracción de aire caliente.
*   **Estructuración de los racks (mínimo 2, proponemos 3):**
    1.  **Rack Servicios Principales:** DNS, BBDD, WEB, Audio/Vídeo, SMB/Monitorización.
    2.  **Rack Backups:** Soporte para los servicios principales, con réplicas distribuidas.
    3.  **Rack Comunicaciones:** Switches, Routers, Paneles de parcheo para la red local.
    *   Modelo Rack: **APC - AR3100B2 armario rack 42U**.

### 1.2. Infraestructura IT

*   **Servidores:** 9 servidores en total en la sede de Noruega (5 principales, 4 de soporte).
    *   Rack 1: 5 servidores principales (DNS, BBDD, WEB, Audio/Video, SMB/Monitorización).
    *   Rack 2: 4 servidores de soporte.
*   **Especificaciones de los servidores:**

    | Servidor              | CPU             | RAM       | Disco principal                |
    | --------------------- | --------------- | --------- | ------------------------------ |
    | DNS                   | 2-4 núcleos     | 4 GB      | SSD 120 GB                     |
    | BBDD                  | 8 núcleos       | 32-64 GB  | 2x SSD 1TB + 2x SSD 5TB RAID   |
    | WEB                   | 4 núcleos       | 8-16 GB   | SSD 220 GB                     |
    | Audio/Video           | 8 núcleos + GPU | 32 GB     | SSD 1 TB + HDD 2TB             |
    | SMB + Monitorización  | 4 núcleos       | 16 GB     | SSD + RAID de HDDs (2-4 TB)    |
*   **Justificación:** Especificaciones adaptadas a la carga y criticidad de cada servicio (alta disponibilidad para DNS, RAM/IO para BBDD, GPU para vídeo, etc.).
*   **Servidores en el extranjero (CDN):** Réplicas en ubicaciones estratégicas (EE. UU., México, Alemania, etc.) para una Content Delivery Network eficiente.
*   **Soporte en la nube:** Colaboración con marcas globales (ATO, OperaGX, etc. - rol a definir: clientes/partners).
    ![Distribución Sala CPD Racks](assets/img/cpd/distribucion_sala_racks.png)

### 1.3. Infraestructura eléctrica

*   **SAI (Sistema de Alimentación Ininterrumpida):** Modelo **Eaton 9PX 5000i HotSwap**.
    *   Características clave: Doble conversión en línea, hasta 98% de eficiencia, función HotSwap (mantenimiento sin interrupción), pantalla LCD, gestión remota.
    *   Beneficios: Protección fiable, continuidad del servicio, reducción de costes operativos y huella de carbono.
    ![Eaton 9PX Frontal](assets/img/cpd/eaton_9px_frontal.png)

### 1.4. Seguridad física y lógica

*   **Física:**
    *   Control de acceso: Puertas con tarjeta y cortinas laminares.
    *   Videovigilancia: Cámaras estratégicas.
    *   Prevención de incendios: Paredes de lana de roca, detectores de humo, extintores de polvo ABC.
    *   Vías de evacuación: Señalizadas y claras.
    ![Plano Seguridad CPD](assets/img/cpd/plano_seguridad_cpd.png)
*   **Lógica:**
    *   Acceso: Autorización por contraseñas robustas y mínimos privilegios.
    *   Firewalls: Perimetrales y a nivel de host si es necesario.
    *   Monitorización: Servidor dedicado (incluye S3 Gateway).
    *   Backups: NAS centralizado para copias de seguridad.
    *   RAIDs: DNS (RAID1), BBDD (RAID10), WEB (RAID1), Audio/Vídeo (RAID5/6), SMB/Monitorización (RAID6/1).
*   **Prevención de riesgos laborales:** Evaluación de riesgos, formación específica (eléctricos, mecánicos, ergonómicos, incendios), señalización clara, EPIs.

### 1.5. Sostenibilidad

Enfoque integral para minimizar el impacto ambiental y maximizar la eficiencia operativa.
*   **Optimización consumo energético:** Equipos de bajo consumo (SAI Eaton 9PX), dimensionamiento adecuado de servidores.
*   **Energía verde:** Análisis para contratar proveedores de energía renovable.
*   **Ahorro en cableado:** Diseño en estrella para minimizar longitud y material.
*   **Refrigeración natural:** Aprovechamiento del clima de Noruega y diseño de la sala (suelo/techo técnico, pasillos fríos/calientes).
*   **Parada selectiva de equipos:** Políticas para modos de bajo consumo o parada en periodos de baja actividad.

### 1.6. Implementación del CPD en la nube AWS (Consideraciones)

Se contempla el uso de servicios cloud, con AWS como principal referente inicial para ciertos servicios o como parte de la estrategia híbrida o de backup.

### 1.7. Comparativa de eficiencia energética con proveedores de nube

Investigación sobre las prácticas de sostenibilidad y eficiencia de los principales proveedores:

*   **AWS:** CPDs propios optimizados, PUE ~1.1, objetivo 100% renovable para 2025 (90% actual). Herramientas como Customer Carbon Footprint.
*   **Microsoft Azure:** IA para optimizar consumo, PUE ~1.125. Objetivo 100% renovable para 2025, carbon negative para 2030. Herramienta: Microsoft Sustainability Calculator.
*   **Google Cloud Platform (GCP):** Pioneros en sostenibilidad, PUE ~1.1. Neutrales en carbono desde 2007, objetivo energía libre de carbono 24/7 para 2030.

**Tabla Comparativa Resumida:**

| Característica                     | AWS                             | Azure                         | Google Cloud                     |
| ---------------------------------- | ------------------------------- | ----------------------------- | -------------------------------- |
| Energía 100% renovable (prevista)  | 2025                            | 2025                          | Ya cumple, + obj. 24/7 (2030)  |
| Emisiones netas de carbono         | 2040 (net-zero)                 | 2030 (carbon negative)        | Desde 2007 (neutral)            |
| PUE Medio                          | ~1.1-1.2                        | ~1.125                        | ~1.1                             |

**Conclusiones:** Los tres tienen fuertes compromisos. GCP destaca en neutralidad de carbono. AWS en infraestructura extensa. Azure en integración corporativa.

**Leyenda:**
*   **PUE (Power Usage Effectiveness):** Métrica de eficiencia energética. Un valor cercano a 1.0 indica mayor eficiencia.

---

## 2. Implantación de los servicios de audio y vídeo

*(Contenido de este apartado a desarrollar)*

---

## 3. Diseño e implementación de una base de datos

*(Contenido de este apartado a desarrollar)*

---