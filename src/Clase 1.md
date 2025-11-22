# Introducción a la nube

> Esta clase abarca los módulos 1 y 2 del curso de AWS Cloud Architecting

## Objetivos de la materia

- Conocer y aplicar los principios y las buenas prácticas de arquitectura para el diseño de soluciones basadas en la nube.
- Diseñar soluciones que consideren los beneficios y los riesgos asociados a los diferentes modelos de servicio.
- Conocer y utilizar servicios de AWS para crear una infraestructura escalable, confiable y con alta disponibilidad.
- Identificar y aplicar servicios de AWS para brindar seguridad a las soluciones.
- Comprender los costos de implementación en función de distintos escenarios.

## Conceptos fundamentales

### ¿Qué es la nube?

__Definición__:
Es un modelo que permite el acceso a demanda, conveniente y desde cualquier lugar a un conjunto compartido y configurable de recursos tecnológicos, que pueden ponerse rápidamente a disposición, con un esfuerzo o una interacción mínima con el proveedor.

![Cloud Computing](./images/Clase%201/cloud-computing.png)

__Características__:

- On-demand self-service
- Broad network access
- Resource pooling
- Rapid elasticity
- Measured service

## Modelos de servicio

### Responsabilidad compartida
![Modelos de servicio](./images/Clase%201/service-models.png)


## Modelos de implementación

| Tipo        | Descripción                                                                     |
| ----------- | ------------------------------------------------------------------------------- |
| **Pública** | Dispuesta por un proveedor de servicios de nube para uso del público en general |
| **Privada** | Usada por una única organización                                                |
| **Híbrida** | Compuesta por dos o más redes de diferente tipo, conectadas entre sí            |

## Arquitecto de nube

| Planificar                                                | Investigar                                                | Construir                                                                              |
| --------------------------------------------------------- | --------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| Definir la estrategia                                     | Evaluar los servicios en función de las cargas de trabajo | Diseñar el plan de transformación                                                      |
| Analizar las soluciones que se adaptan al caso de negocio | Revisar las arquitecturas existentes                      | Gestionar la adopción de nube y la migración                                           |
| Seleccionar la tecnología apropiada para cada solución    | Diseñar prototipos                                        | Brindar documentación, procesos y herramientas a los desarrolladores                   |
|                                                           | Mantenerse actualizado y conocer las nuevas tecnologías   | Aplicar buenas prácticas para optimizar costos, performance, confiabilidad y seguridad |

## Well-architected framework
[Documentación del framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)

### Pilares

![Pilares](./images/Clase%201/well-architected-framework-pillars.png)

__**Operational Excellence**__

**¿Nuestra arquitectura funciona correctamente? ¿Es capaz de continuar funcionando?**

**Capacidad de:**

- Soportar el desarrollo
- Ejecutar procesos y cargas de trabajo de manera efectiva
- Brindar información sobre las operaciones
- Mejorar continuamente los procesos y procedimientos de soporte para aportar valor al negocio

**Ejemplos:** Operaciones como código, cambios pequeños y frecuentes, usar servicios administrados por AWS

__**Security**__

**¿El sistema funciona únicamente como esperamos?**

**Capacidad de utilizar las soluciones de nube para:**

- Proteger los datos
- Proteger los sistemas
- Proteger los activos

**Ejemplos:** Mantener la trazabilidad, aplicar seguridad en capas, cifrar datos en tránsito y en reposo, gestionar accesos

__**Reliability**__

**¿El sistema funciona de manera consistente y es capaz de recuperarse rápidamente?**

**Capacidad de la implementación y de las cargas de trabajo para:**

- Operar correctamente y obtener resultados consistentes
- Ser probado fácilmente

**Ejemplos:** Automatizar la recuperación ante fallas, realizar pruebas sobre los procedimientos de recuperación, mantener la trazabilidad, aplicar seguridad en capas, cifrar datos en tránsito y en reposo, gestionar accesos

__**Performance Efficiency**__

**Quitar los cuellos de botella, reducir el desperdicio**

**Capacidad para:**

- Usar correctamente los recursos
- Mantener la eficiencia frente al escalamiento de la demanda

**Ejemplos:** Usar arquitecturas serverless, hacer implementaciones globales usando distintas regiones de AWS, experimentar

__**Cost Optimization**__

**Gastar solo lo que corresponde**

**Capacidad para:**

- Ejecutar sistemas que brinden valor al negocio
- Operar al menor precio posible

**Ejemplos:** Adoptar un modelo de consumo, medir la eficiencia, permitir que AWS maneje la carga de la infraestructura

__**Sustainability**__

**Minimizar el impacto ambiental**

**Capacidad para:**

- Reducir el consumo de energía
- Aumentar la eficiencia de todos los componentes
- Maximizar el beneficio de los componentes en uso
- Minimizar el total de recursos requeridos

**Ejemplos:** Comprender el impacto, maximizar el uso de recursos, usar recursos gestionados por AWS

## Well-architected Tool

### Pilares

- Provee un proceso consistente para medir la arquitectura
- Permite evaluar nuestro grado de alineación con el WAF
- Ayuda a documentar las decisiones
- Ofrece recomendaciones para optimizar las cargas de trabajo
- Ayuda a diseñar soluciones confiables, seguras, eficientes y de costo adecuado

## Principios de diseño

- Escalabilidad
- Automatizar la creación, terminación y configuración de recursos
- IaC: Automatizar la implementación, detener los recursos fuera de uso, mejorar las pruebas (recursos "descartables")
- Desacoplar de los componentes de la arquitectura
- Diseñar servicios, no servidores
- Elegir la solución de base de datos adecuada a la carga de trabajo
- Evitar puntos únicos de falla
- Optimizar costos
- Usar soluciones de caché
- Asegurar todas las capas de la infraestructura

## Infraestructura de AWS

- Regiones
  - Es un área geográfica completamente separada en la que existen data centers de AWS. Proveen el mayor grado de estabilidad y tolerancia a errores, y permiten ejecutar cargas de trabajo en distintos lugares del mundo.
  - ![Regiones](./images/Clase%201/regions.png)
- Zonas de disponibilidad
  - Es una ubicación aislada y específica dentro de una región que posee su propia implementación de redundancia de energía, redes y conectividad de baja latencia. Separada físicamente para reducir el impacto de desastres.
  - ![AZ](./images/Clase%201/az.png)
- Edge Locations
  - Son data centers de AWS destinados a reducir la latencia en la provisión de servicios. Se encuentran más cerca de los usuarios finales que las Regiones y las AZ. Conformados por Puntos de presencia (Points of Presence) y cachés de borde regionales (Regional edge caches).

## Responsabilidades

### Shared Responsibility Model
![Responsabilidad compartida](./images/Clase%201/shared-responsibility.png)

La seguridad en la nube es responsabilidad del cliente
> Por las dudas, es la parte azul

- Cifrado de datos
- Copias de respaldo
- Control de acceso y autorización
- Gestión de la infraestructura contratada (sistemas operativos, redes, bases de datos)

La seguridad de la nube es responsabilidad de AWS
> Para sorpresa de nadie, es la parte naranja
- Software que soporta los servicios de AWS
- Seguridad física y redundancia
- Mantenimiento del hardware destinado a los servicios
- Infraestructura global (regiones, AZs, edge locations)