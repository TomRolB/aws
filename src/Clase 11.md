# Cacheo de contenidos

> Esta clase abarca el módulo 12 del curso de AWS Cloud Architecting

## Objetivos

* Determinar cuándo y cómo es necesario proveer un acceso más rápido a los contenidos para balancear el rendimiento, el costo y la actualización de datos 
* Incorporar servicios de content delivery network (CDN) al diseño de la arquitectura para distribuir contenido estático de manera segura y eficiente 
* Seleccionar una estrategia de caché en memoria que permita reducir la latencia de red y limitar la sobrecarga de la base de datos

## ¿Por qué cachear?

Solemos cachear porque necesitamos:
* Optimizar el almacenamiento de datos de acceso frecuente
* Aumentar la respuesta a las solicitudes de datos
* Reducir la necesidad de acceso a la capa de almacenamiento subyacente, que es más lenta

Una analogía muy sencilla es que, si busco una herramienta, puedo tener un depósito de herramientas que me evite tener que ir hasta la ferretería

![Analogy](./images/Clase%2011/analogy.png)

## Ventajas y desventajas

| Beneficios                                      | Desafíos                                                                                                       |
| ----------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| Reduce la latencia de respuesta                 | Requiere mayor trabajo de diseño                                                                               |
| Menor costo                                     | Según el caso de negocio, se debe determinar cómo implementar el cache y cómo tratar los datos desactualizados |
| Alivia la carga en la fuente de datos de origen |                                                                                                                |
| Brinda una performance predecible               |                                                                                                                |
| Aumenta la disponibilidad                       |                                                                                                                |
## CloudFront
<img src="./images/Clase%2011/cloudfront-logo.png" align="right" width="150" style="margin-left: 15px;">

* Servicio de CDN que brinda contenido en todo el mundo, de manera segura, con baja latencia y alta velocidad de transferencia.
* Provee el contenido a través de ubicaciones de proximidad (edge locations)
* Mejora la resiliencia de las aplicaciones respecto de los ataques de denegación distribuida de servicios (DDOS), mediante el uso de servicios como AWS Shield y AWS WAF
* En este caso, hablamos de **caching estático**

### Componentes
* **Edge locations**: 
	* Más numerosos y cercanos a los usuarios
	* Tienen caches más pequeños
	* Ayudan a asegurar que el contenido más popular se provea rápidamente
* **Regional edge caches**
	* Son menos, están más lejos de los usuarios
	* Son más grandes
	* Ayudan cuando el contenido no es tan popular

![Cloudfront Components](./images/Clase%2011/cloudfront-components.png)

### Funcionamiento

![Cloudfront Flow](./images/Clase%2011/cloudfront-flow.png)

### Configuración

Una distribución de CloudFront se configura con los siguientes pasos:

1. Especificar una ubicación de origen
2. Configurar la distribución
3. CloudFront queda disponible
4. CloudFront envía la configuración de la distribución a los *edge locations*

### Controles sobre el cache

- **Definir un valor máximo de TTL**: Un valor bajo reduce la duración del contenido del cache.
- **Versionar contenido**: Busca inmediatamente las nuevas versiones del contenido.
- **Definir encabezados de control**: Brinda un control preciso sobre la expiración de archivos individuales.
- **Usar mensajes para invalidar contenido**: Fuerza a CloudFront a marcar el contenido como expirado.

### Caso de uso: streaming de video

![Cloudfront Streaming Use Case](./images/Clase%2011/cloudfront-streaming-use-case.png)

### Mitigación de DDoS

* El monitoreo y la mitigación están incluidos en **Amazon Route 53** cuando redirige tráfico a CloudFront
* CloudFront puede crear una ACL de acceso en AWS WAF que configura reglas para analizar las solicitudes entrantes y bloquear amenazas antes de que lleguen a los servidores.
* Las mitigaciones de Shield DDoS solo permiten que el tráfico válido llegue a CloudFront

## ElastiCache
<img src="./images/Clase%2011/elasticache-logo.png" align="right" width="150" style="margin-left: 15px;">

* Es un servicio administrado de **almacenamiento de datos en memoria**, con una latencia en el orden de milisegundos 
* Se ubica **entre una aplicación y el almacenamiento** de datos original 
* **Reduce la latencia** de acceso y **facilita la carga** de bases de datos y aplicaciones 
* Brinda un cache en memoria de **alta performance a buen costo** 
* Compatible con soluciones open source como **Redis y Memcached**

### ¿Cuándo utilizarlo?

* Cuando nos preocupa el tiempo de respuesta hacia los clientes
* Cuando tenemos un gran volumen de solicitudes que sobrecargan la BD
* Para reducir el costo de la BD (en los casos donde operar contra la BD implique un costo económico grande)

### Redis vs Memcached

|                 Memcached                  |                        Redis                        |
| :----------------------------------------: | :-------------------------------------------------: |
|    ![Elasticache Memcached Logo](./images/Clase%2011/elasticache-memcached-logo.png)     |           ![Elasticache Redis Logo](./images/Clase%2011/elasticache-redis-logo.png)           |
|            Modelos más básicos             |            Usar tipos de datos complejos            |
| Ejecutar nodos grandes con múltiples hilos |      Proveer persistencia al almacén de claves      |
| Escalar horizontalmente con Auto Discovery |      Ordenar o clasificar datasets en memoria       |
|                                            | Brindar alta disponibilidad con failover automático |
|                                            |   Soportar mensajería de publicación/suscripción    |

### Componentes

![Elasticache Structure](./images/Clase%2011/elasticache-structure.png)

### Time To Live (TTL)

* En cada escritura se registra un valor de TTL
* El TTL especifica cuántos segundos o milisegundos tarda la clave en vencer
* Si los datos del cache están vencidos, la aplicación se los solicita a la BD

## Estrategias para tratar con datos desactualizados

|**Features**|**Lazy Loading**|**Write-Through**|
|---|---|---|
|**Patrón**|Actualiza el cache después de una solicitud de datos|Actualiza el cache automáticamente cuando se aplica un cambio en el origen|
|**Ventaja**|El cache contiene solo la información que la aplicación requiere|El cache está actualizado con la base principal (los datos más frecuentes estarán actualizados en el cache)|
|**Desventaja**|Requiere una estrategia por programa para asegurar que el cache esté actualizado|Aumenta el costo y almacena en memoria datos que podrían ser innecesarios|
#### Lazy Loading

![Lazy Loading Strat](./images/Clase%2011/lazy-loading-strat.png)
#### Write-through

![Write Through Strat](./images/Clase%2011/write-through-strat.png)

## Buenas prácticas para WAF

Las siguientes son prácticas recomendadas para cumplir con los pilares del **Well-Architected Framework (WAF)**:

### Performance efficiency

* Implementar patrones de acceso a datos que utilicen funciones de cache
* Implementar estrategias para mejorar la performance de las queries

### Reliability

* Usar conectividad de alta disponibilidad para las cargas expuestas en endpoints públicos

### Optimización en el tiempo

* Modelar las transferencias de datos
* Seleccionar componentes que optimicen los costos de transferencias de datos
* Implementar servicios para reducir los costos de transferencia.
