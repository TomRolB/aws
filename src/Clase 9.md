# Monitoreo, elasticidad y alta disponibilidad

> Esta clase abarca el módulo 10 del curso de AWS Cloud Architecting

## Objetivos

- Examinar el uso de Amazon CloudWatch y Amazon EventBridge para monitorear métricas y facilitar las notificaciones.
- Usar Amazon EC2 Auto Scaling para promover la elasticidad y crear entornos de alta disponibilidad.
- Determinar la estrategia para escalar los recursos de bases de datos
- Identificar estratégicas de balanceo de carga para crear entornos de alta disponibilidad.
- Usar Amazon Route 53 para la contingencia de DNS
- Aplicar los principios del AWS Well-Architected Framework para diseñar sistemas con alta disponibilidad

## Monitoreo de recursos

Se pueden monitorear tres tipos de métricas:
1. **Operational health**: determinan si el ambiente de la aplicación está corriendo bien
2. **Resource utilization**: miden el uso de los componentes de la aplicación para asegurarse de que no se estén infra o sobreutilizando
3. **Application performance**: muestran si la demanda de la aplicación está siendo satisfecha

## CloudWatch
<img src="./images/Clase%209/cloudwatch-logo.png" align="right" width="150" style="margin-left: 15px;">

* Recolecta y mantiene registro de métricas para servicios de AWS entre regiones en un repositorio de métricas
* Recolecta logs usando **Amazon CloudWatch Logs**
* Soporta métricas built-in y custom
* Calcula estadísticas a partir de métricas y las muestra en gráficos
* Provee alarmas para que arquitecturas basadas en eventos puedan responder a ellas
* Provee notificaciones para hacer cambios a recursos monitorizados

### Métricas y logs

- **Centralización de Logs:** CloudWatch Logs permite recolectar, almacenar y acceder a logs de múltiples fuentes (EC2, CloudTrail, VPC, On-premise) en un único flujo ordenado cronológicamente.
    
- **Capacidades de Análisis:** Podés ejecutar **Queries** sobre los logs, filtrar por patrones de error, enmascarar datos sensibles y archivarlos por seguridad. Una función clave es **generar métricas a partir de logs** (Log-based metrics).

### Alarmas

* Una alarma observa una métrica en un período específico y ejecuta una o más **acciones** basándose en cuál el valor de la métrica en relación a un *threshold*. 
* La acción se envía a un topic de **Amazon SNS** o a una **Auto Scaling policy**. 
* Para que una acción se active, el estado que dispara la acción debe mantenerse durante un tiempo (es decir, no se activan ni bien se supera el threshold) 

### Dashboards

CloudWatch soporta dashboards automáticos y custom para mostrar métricas y ver alarmas.

![Cloudwatch Dashboards](./images/Clase%209/cloudwatch-dashboards.png)

## EventBridge

<img src="./images/Clase%209/eventbridge-logo.png" align="right" width="150" style="margin-left: 15px;">

* Procesa eventos con un *event bus* o un *pipe*. Estos eventos pueden ser una activación de una alarma de CloudWatch.
	* Los *pipes* son integraciones punto a punto entre un origen y un destino
	* Los *event buses* son routers que reciven eventos y opcionalmente los entregan a uno o más destinos
* Realiza decisiones de routing con reglas configurables
	* Las reglas corren basándose en si coincide un patrón de evento o en un tiempo predefinido con **Amazon EventBridge Scheduler**.
	* Los destinos pueden estar en otra cuenta de AWS, en otra región, o ambos

### Event bus

Ejemplo de funcionamiento de un event bus:

![Event Bus Example](./images/Clase%209/event-bus-example.png)

Ejemplo del formato de un evento:

```json
{
	"source": ["aws.ec2"],
	"detail-type": ["EC2 Instance State-change Notification"],
	"detail": {
		"state": ["terminated"]
	}
}
```

## Monitoreo de costos de recursos

![Cost Monitoring Services](./images/Clase%209/cost-monitoring-services.png)

* **AWS Cost Explorer**: ayuda a visualizar, entender y gestionar tus costos y uso de AWS con granularidad diaria o mensual.
* **AWS Budgets**: ayuda a establecer presupuestos personalizados que alertan cuando tus costos o tu uso excede (o *está pronosticado que excederá*) el monto presupuestado.
* **AWS Cost and Usage Report**: contiene el mayor conjunto de datos disponibles sobre costos y uso de AWS, incluyendo metadatos adicionales sobre servicios de AWS, pricing y reservas.

## Arquitecturas reactivas

Las aplicaciones necesitan manejar grandes cantidades de datos con respuestas de milisegundos, al mismo tiempo que tienen que soportar un uptime cercano al 100%. Para esto, se puede implementar una aplicación que sea elástica, resiliente, responsiva y message-driven
* **Elastic scaling**: mecanismo para escalar los recursos de una aplicación dinámicamente. Se agregan o quitan recursos para reaccionar a cambios y para evitar downtime o cuellos de botella.
* **Responsive**: las aplicaciones deberían responder a tiempo y con la menor latencia posible, incluso ante cargas de trabajo variables
* **Resilient**: mantenerse responsivo ante una falla y/o recuperarse ante cargas altas, ataques y fallas de cualquiera de los componentes.
* **Message-driven**: una de las características más importante. Garantiza bajo acoplamiento, aislamiento y transparencia de ubicación (acceder a los datos más allá de donde estén)

## Scaling

* **Escalado vertical**: cambiar las especificaciones de un recurso individual. 
	* EC2 permite parar una instancia y cambiar a un tipo de instancia con mayor RAM, CPU, I/O o capacidad de red. 
	* En este caso, AWS transmite los datos a la nueva instancia
	* Tiene un límite, porque está atado al hardware, y no es del todo eficiente. Tampoco sigue un enfoque de alta disponibilidad
* **Escalado horizontal**: agregar o sacar recursos disponibles para la aplicación.
	* **Scale out**: agregar recursos
	* **Scale in**: finalizar recursos
	* Las aplicaciones y/o los datos se transmiten automáticamente a los recursos agregados

### Amazon EC2 Auto Scaling


<img src="./images/Clase%209/autoscaling-logo.png" align="right" width="150" style="margin-left: 15px;">

* Gestiona **Amazon EC2 Auto Scaling groups**: colecciones de instancias de EC2 que pueden estar en distintas Availability Zones
* Lanza o retira instancias configuradas por *launch templates*
	* Una *launch template* es una configuración versionable que funciona como blueprint para crear una instancia automáticamente
* Hace resizing basándose en eventos de *scaling policies*, *load balancer health check notifications* o *scheduled actions*
	* También es posible definir *predictive policies*, que escalan en base a patrones de tráfico, aplicando machine learning
	* Puede incluso remover instancias no saludables
* Se integra con **Elastic Load Balancing (ELB)** para enviar nuevos registros de instancias y recibir notificaciones de salud
* Balancea el número de instancias entre AZs
* Está disponible sin costos
* En resumen, provee una mejor tolerancia a fallos, una mejor disponibilidad y un mejor manejo de costos

### Otras opciones de auto scaling

![Other Autoscaling Options](./images/Clase%209/other-autoscaling-options.png)

* **AWS Auto Scaling**: se usa un plan para configurar el auto scaling para un **conjunto de servicios distintos**. Se encuentra disponible para servicios de AWS como Aurora, EC2 Auto Scaling, Elastic Container Service (ECS) y DynamoDB
* **AWS Application Auto Scaling**: escala servicios **individualmente**. Incluye los servicios anteriores y también Lambda, SageMaker y ElastiCache for Redis.

## Scaling de bases de datos

| **Scaling**             | **Aurora**                                   | **Aurora Serverless**                                                                                                                    | **Amazon RDS**                                                                         | **DynamoDB**                                                                                                            |
| ----------------------- | -------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| **Qué permite escalar** | Cluster                                      | Cluster                                                                                                                                  | Base de datos                                                                          | Tabla                                                                                                                   |
| **Escalado vertical**   | Clase o tamaño de la instancia               | Límites de throughput (ACU) del clúster, con cada _Reader_ y _Writer_ siendo escalado automáticamente dentro de los límites configurados | • Clase o tamaño de la instancia<br><br>• Auto scaling de almacenamiento de Amazon RDS | N/A                                                                                                                     |
| **Escalado horizontal** | Aurora Auto Scaling para réplicas de lectura | • Réplicas Multi-AZ<br><br>• Réplicas de lectura (_Reader_)                                                                              | Bases de datos de réplica de lectura                                                   | • Modo _On-demand_<br><br>• Modo _Provisioned_ con Application Auto Scaling<br><br>• Índices secundarios globales (GSI) |
| **Gestionado por AWS**  | Escalado de almacenamiento                   | Escalado de almacenamiento                                                                                                               | N/A                                                                                    | Escalado de almacenamiento                                                                                              |

## Elastic Load Balancing (ELB)

<img src="./images/Clase%209/elb-logo.png" align="right" width="150" style="margin-left: 15px;">

* Distribuye tráfico entre múltiples targets en una o más AZs
* Puede recibir tráfico público o privado
* Monitorea la salud de targets registrados con health checks
* Rutea tráfico solamente a targets saludables
* Escala basándose en el tráfico entrante
* Resuelve el problema de *single point of failure* para instancias de EC2 y containers 

### Tipos de load balancers

| **Característica**           | **Application Load Balancer (ALB)**                                                    | **Network Load Balancer (NLB)**                                                         | **Gateway Load Balancer (GWLB)**                                                               | **Classic Load Balancer (CLB)**                                              |
| ---------------------------- | -------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| **1. Tipo de Tráfico / Uso** | Se usa para tráfico **HTTP y HTTPS**.                                                  | Se usa para descarga de TLS (_TLS offloading_), **UDP** y direcciones **IP estáticas**. | Se usa para flotas de **appliances virtuales** de terceros usando el protocolo GENEVE.         | Se usa para redes **EC2-Classic** de generación anterior.                    |
| **2. Capa OSI**              | Opera en la **Capa 7** (Capa de Aplicación).                                           | Opera en la **Capa 4** (Capa de Transporte).                                            | Opera en la **Capa 3** (Capa de Red).                                                          | Opera en las **Capas 3 y 7** (Transporte y Aplicación).                      |
| **3. Escenario / Ventaja**   | Se usa para arquitecturas de **aplicaciones** modernas (microservicios, contenedores). | Se usa para **millones de solicitudes** por segundo con **latencia ultra baja**.        | Se usa para mejorar la seguridad, el cumplimiento (_compliance_) y los controles de políticas. | Se usa **solo** si actualizar a otros balanceadores de carga no es factible. |
### Componentes de un load balancer

![Load Balancer Components](./images/Clase%209/load-balancer-components.png)

* Las **reglas** incluyen una prioridad, una o más acciones y una o más condiciones, que si se cumplen, ejecutan dichas acciones.
* El load balancer va realizando health checks a los **targets** y dirige las requests a aquellos que se encuentran saludables. 

## Route 53


<img src="./images/Clase%209/route53-logo.png" align="right" width="150" style="margin-left: 15px;">

* Servicio DNS que gestiona dominios y provee *hosted zones*
	* Una *hosted zone* es un contenedor de registros que incluye información de cómo se quiere rutear tráfico para un dominio y sus subdominios
* Provee servers autoritativos para resolución por DNS
* Permite comprar dominios
* Realiza routing DNS a endpoints saludables
* Realiza health checks contra IP adresses o dominios para gestionar failovers de AZs o regiones.
* Puede monitorear alarmas de CloudWatch
* Soporta múltiples opciones de routing

### DNS lookup con Route 53

![Route53 DNS Lookup](./images/Clase%209/route53-dns-lookup.png)

### Políticas de routing

![Routing Policies](./images/Clase%209/routing-policies.png)

- **Simple**: Enruta el tráfico hacia un único recurso (como un servidor web) sin aplicar reglas especiales ni balanceo.
    
- **Weighted**: Distribuye el tráfico entre múltiples recursos según un porcentaje o "peso" específico asignado a cada uno.
    
- **Latency**: Dirige al usuario hacia la región de AWS que le ofrezca la respuesta más rápida.
    
- **Failover**: Envía tráfico a un recurso primario y cambia automáticamente a uno secundario (backup) si el primero falla.
    
- **Geoproximity**: Enruta basado en la distancia física entre el usuario y el recurso, ajustable mediante un "sesgo" (bias) para expandir o reducir el alcance.
    
- **Geolocation**: Decide el destino basándose en el origen geográfico exacto del usuario (país, continente o estado) para localizar contenido o restringirlo.
    
- **Multivalue answer**: Devuelve hasta 8 registros saludables seleccionados al azar en respuesta a una consulta DNS para aumentar la disponibilidad.
    
- **IP-based**: Permite enrutar el tráfico basándose en bloques de direcciones IP (CIDR) específicos de los clientes para un control granular.

### Hosted zones públicas y privadas

![Hosted Zones](./images/Clase%209/hosted-zones.png)

## Buenas prácticas para WAF

Las siguientes son prácticas recomendadas para cumplir con los pilares del **Well-Architected Framework (WAF)**:

### Reliability

* Desplegar la carga de trabajo en múltiples lugares
* Automatizar la recuperación para componentes que estén restringidos a una sola ubicación
* Realizar failover a recursos saludables
* Enviar notificaciones cuando existen eventos que impactan en la disponibilidad

### Performance efficiency

* Escalar los recursos de cómputo dinámicamente