# Servicios de Bases de Datos

## Consideraciones al elegir una Base de Datos

* **Escalabilidad**: no solamente escalar "para arriba", sino también evitar escalar innecesariamente para minimizar costos.

* **Almacenamiento**: tener en cuenta el tamaño total de los datos

* **Características de los datos**: incluye lo siguiente:
	* Modelo de los datos: relacional, estructurado, semiestructurado, etc.
	* Forma de acceso a los datos
	* Latencia de acceso aceptada
	* Tamaño específico de los registros (diferente del tamaño total mencionado anteriormente), si fuera necesario

* **Durabilidad**: acá entran tanto la durabilidad en sí como la disponibilidad (por alguna razón)
	* Durabilidad: garantía de que no se pierdan los datos
	* Disponibilidad: acceder a los datos cuando los necesito.
	* Ambos dependen del caso de negocio. Usualmente datos más críticos requieren mayor durabilidad, por ejemplo


### Opciones de Amazon

![AWS Database Services](./images/Clase%205/aws-database-services.png)

### ¿De qué se encarga AWS?

En la tabla se ve de qué tenés que encargarte según el caso:

![Responsibilities](./images/Clase%205/responsibilities.png)

### Planeamiento de la capacidad de la BD

Es necesario ir prediciendo la capacidad que vamos a necesitar y actuar en consecuencia. En ese sentido, podemos escalar de dos formas:
1. **Escalado vertical**: aumentar recursos de hardware. Es costoso e implica downtime.
2. **Escalado horizontal**: aumentar el número de servidores en los que corre la BD. En este caso no se requiere downtime; la capacidad se agrega con la BD en funcionamiento.

## Amazon RDS
<img src="./images/Clase%205/amazon-rds-logo.png" align="right" width="150" style="margin-left: 15px;">

* Es un servicio de bases de datos relacionales gestionadas por AWS, para desplegarlas y escalarlas
* Soporta múltiples motores de BD
* Usa volúmenes de **Amazon Elastic Block Store (Amazon EBS)** para el guardado de la BD y sus logs.
* Se encarga de varias tareas relacionadas a la BD

### Beneficios

![RDS Benefits](./images/Clase%205/rds-benefits.png)

* **Baja barrera administrativa**: no tenés que proveer tu propia infraestructura o instalar el software de BD
* **Altamente escalable**: se puede hacer scale-up o scale-down de los recursos de cómputo y de memoria. Para esto, RDS provee distintos tipos de instancias.
* **Disponible y durable**: se pueden configurar backups automáticos, snapshots y reemplazos automáticos del host. 
	* Con la opción *Multi-AZ deployment*, se puede tener una réplica sincronizada de la BD en otra Availability Zone.
	* Para cargas de lectura altas, se puede tener réplicas de lectura
* **Seguro y compliant**: es posible aislar la BD usando **Amazon Virtual Private Cloud (Amazon VPC)**, estableciendo así una conexión a tu propia infraestructura mediante una VPN. 
	* Adicionalmente, Amazon provee configuraciones de firewalls, ACLs, encripción en transporte y en almacenamiento, etc.

### Arquitectura

![Architecture](./images/Clase%205/architecture.png)

## Aurora
<img src="./images/Clase%205/amazon-aurora-logo.png" align="right" width="150" style="margin-left: 15px;">

* Es un **Relational DataBase Management System (RDBMS)** en la nube con compatibilidad completa con MySQL y PostgreSQL
* Está gestionado por Amazon RDS
* Provee alta performance y disponibilidad por 1/10 del costo
	* Es hasta 5 veces más rápido que BDs MySQL estándar y 3 veces más rápido que BDs PostgreSQL estándar
* Ofrece Multi-AZ deployments mediante Aurora Replicas
	* El límite es de 15 réplicas de lectura de baja latencia, y de 3 availability zones

### Clusters de Aurora

![Aurora Clusters](./images/Clase%205/aurora-clusters.png)

### Aurora Serverless

* Es una configuración on-demand de auto scaling para Aurora
* Provee scaling automático y granular
* Útil para distintos escenarios:
	* Cargas de trabajo variables: Aurora escala automáticamente ante picos de uso
	* Nuevas aplicaciones: si no se sabe qué tamaño se necesita, con el scaling automático se resuelve 
	* Desarrollo y testing: mientras los desarrolladores no estén usando la base de datos de su instancia de testing, simplemente baja a la capacidad mínima
	* Planeamiento de capacidad: se puede simular la carga de trabajo contra Aurora y ver cuánto las BDs realmente escalan

## Tipos de instancias de EC2 para RDS

![Instance types](./images/Clase%205/instance-types.png)

* **General purpose** (familias T y M): para cargas de trabajo intensivas en CPU o para usos de CPU moderados.
* **Memory-optimized** (familias R y X): para cargas de trabajo intensivas en queries o conexiones a la BD.

## Buenas prácticas de Amazon RDS

![RDS Best Practices](./images/Clase%205/rds-best-practices.png)

## Amazon RDS Proxy

Es un proxy de BD para RDS completamente gestionado por AWS, con alta disponibilidad.
* **Más escalable**: genera pools de conexiones y las comparte para una mejor escalabilidad
* **Más resiliente**: reduce los tiempos de failover para Aurora y RDS al menos hasta un 66% para bases de datos Multi-AZ de RDS
> El *failover* es la transmisión de operaciones desde una BD qué falló hasta una BD que está operativa
* **Más seguro**: fuerza autenticación mediante **IAM** y guarda las credenciales en **AWS Secrets Manager**.
### Escalabilidad

Esencialmente, per se, en definitiva, no sé si me explico, lo que hace RDS Proxy es lo siguiente:
1. Se sitúa entre la base de datos y todas las aplicaciones que interactúan con ella
2. Detecta conexiones que no se están usando para transmitir datos y las reutiliza para otras aplicaciones
3. Así, la BD recibe menos conexiones y no se satura su memoria

### Disponibilidad

1. Ante un fallo, RDS Proxy preserva las conexiones que no estén realizando una transacción, y también aquellas nuevas
2. Las transacciones se encolan
3. Cuando la nueva instancia está disponible, se le pasan todas las transacciones disponibles

### Seguridad

Se utiliza IAM para comprobar que la aplicación tiene acceso a la BD. Luego, RDS Proxy pide a AWS Secrets Manager las credenciales para acceder a base de datos.

## Backups

| **Características**             | **Automated Backups**                                                                                                                                  | **Database Snapshots**                                                                        |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------- |
| **Caso de Uso**                 | Restaurar una instancia de una BD a un punto en el tiempo específico.                                                                                  | Respaldar una instancia en un estado conocido, y luego restaurarla a ese estado específico.   |
| **Frecuencia de Backup**        | Diariamente durante tu _backup window_ (los _transaction logs_ se capturan cada 5 minutos).                                                            | Iniciado por el usuario (con la frecuencia que el usuario elija).                             |
| **Período de Retención**        | El valor por defecto es 7 días, pero puede configurarse hasta 35 días. Los backups pueden eliminarse automáticamente después del período de retención. | Se mantienen hasta que el usuario los elimine explícitamente.                                 |
| **Compartir con otras cuentas** | No se pueden compartir (necesitan copiarse primero a un snapshot manual).                                                                              | Se pueden compartir (los snapshots compartidos pueden ser copiados por otras cuentas de AWS). |
* Se puede configurar la instancia de RDS para replicar snapshots y logs de transacciones a una región específica.
* También se pueden crear réplicas de lectura a otras regiones, ya sea por backup, para mayor disponibilidad de lecturas, para migrar un data center a otra región, etc.

## DynamoDB
<img src="./images/Clase%205/dynamo-db-logo.png" align="right" width="150" style="margin-left: 15px;">

* Base de datos NoSQL serverless, completamente gestionada por AWS
* Soporta datos key-value y documentales. Su esquema es flexible, por lo cual cada ítem puede tener distintos atributos.
* Su performance es de milisegundos y escala para proveer mayor capacidad
* Se utiliza cuando se necesita velocidad, escalabilidad y durabilidad
* Casos de uso: aplicaciones, almacenamiento de metadata, plataformas de gaming (sesiones, leaderboards, etc.)

### Features

* Seguridad
	* Provee índices secundarios para acceder los datos con flexibilidad
	* Soporta eventos con **DynamoDB Streams**
	* Replicación multi-región
* Seguridad y reliability
	* Encripción *at rest*
	* Point-in-time recovery
	* Control de accesos granular

### Estructura de datos

![Dynamo Data Structure](./images/Clase%205/dynamo-data-structure.png)

Ejemplo de una tabla:

![Dynamo Sample](./images/Clase%205/dynamo-sample.png)

La partition key determina a qué partición va cada ítem según la siguiente lógica:
1. Se hashea la partition key
2. Cada partición tiene un rango de hashes
3. El ítem va a la partición en cuyo rango cae el nuevo hash

> Dynamo no es lo mismo que MemoryDB (Redis). Uno opera principalmente en disco y el otro en memoria, respectivamente.

### Índices secundarios

#### 1. Global Secondary Index (GSI)

Es una **copia asincrónica** y reorganizada de una tabla. Es "Global" porque te permite consultar toda la base de datos cruzando particiones.
    
- **Funcionamiento:** Cambiás la **Partition Key**. Esto permite particionar los datos por ese valor. Por ejemplo, si tu tabla base está particionada por `DeviceID`, podés crear un GSI particionado por `Temperature`.
    
- **Consistencia:** Siempre es **Eventual Consistency**. Como los datos tienen que replicarse de la tabla original al índice (un proceso físico de copia a otro nodo), hay un _delay_ de milisegundos.   
#### 2. Local Secondary Index (LSI)

Es una **vista alternativa** dentro de la misma partición física. Es "Local" porque el alcance de la búsqueda está limitado a una única Partition Key.
    
- **Funcionamiento:** Mantenés la **misma Partition Key** que la tabla base, pero cambiás la **Sort Key**. Sirve para reordenar los datos dentro de un mismo "grupo".
    
- **Consistencia:** Permite **Strong Consistency**. Como el índice vive en el mismo disco que los datos originales, podés pedir leer el dato exacto al instante de la escritura.

### Replicación 

Por defecto, se replican los datos en múltiples AZ, pero también es posible replicarlos entre regiones con ***global tables***. Una global table es un conjunto de ***replica tables***, pudiendo tener cada réplica en una región distinta. 

### Buenas prácticas

Prácticas preventivas:
* Usar IAM roles para autenticar el acceso
* Usar IAM policies de DynamoDB para autorización base
* Usar IAM policy conditions para control granular
* Usar un VPC endpoint y policies para el acceso a Dynamo

Prácticas de detección:
* Usar **AWS CloudTrail** para monitorear el uso de AWS KMS keys
* Monitorear operaciones de DynamoDB con CloudTrail
* Monitorear la configuración de DynamoDB con **AWS Config**
* Monitorear la compliance de DynamoDB

## Purpose-built Databases

### Amazon Redshift
<img src="./images/Clase%205/redshift-logo.png" align="right" width="150" style="margin-left: 15px;">

* BD de Warehousing completamente gestionada por Amazon, que puede llegar a manejar petabytes de cargas de trabajo para analíticas
* Utiliza almacenamiento columnar
* Soporta **Amazon Redshift Serverless**
* Utilizado para Online Analytics Processing (OLAP)
* Soporta conexiones con varias aplicaciones, incluyendo aquellas de BI, datos, reportes, etc.

### Otras BDs

![Purpose Built Services](./images/Clase%205/purpose-built-services.png)

La opción a elegir depende del caso de negocio:
* **DocumentDB**: se tiene una feature donde cada usuario introduce información con distinto formato
* **Keyspaces**: el workload es write-heavy, con lo cual la base de datos columnar ayuda, ya que cada escritura es un *append* que no hace ningún checkeo de restricciones.
* **MemoryDB**: se requiere manejar datos muy dinámicos y muchas queries, por lo cual es conveniente acceder los datos desde memoria sin introducir latencia por operaciones a disco. Entonces sirve, por ejemplo, para perfiles de usuario en retail, leaderboards en gaming y transacciones bancarias.
* **Neptune**: se tiene datasets muy conectados y se quiere encontrar conexiones en esos datos. Se quiere navegar estas conexiones y filtrar los resultados en función de ciertas variables. Por ejemplo, para motores de recomendación, detección de fraude, grafos de conocimiento, descubrimiento de medicamentos y seguridad de redes.
* **Timestream**: es necesario identificar tendencias y patrones en el tiempo para tomar decisiones. Por ejemplo, para analizar datos de sensores IoT, para monitorear métricas de salud, de uso, de tráfico de red, etc.
* **QLDB**: se requiere guardar datos para auditoria y compliance. Mediante una base de datos *ledger*, se obtienen garantías de inmutabilidad y verificación criptográfica, aunque con un overhead de tiempo de ejecución. Sirve, por ejemplo, para guardar transacciones bancarias, para registrar el estado de los lotes de un producto, etc.

## AWS DMS
<img src="./images/Clase%205/dms-logo.png" align="right" width="150" style="margin-left: 15px;">

* Servicio de migraciones y replicación gestionado por AWS
* Ayuda a mover BDs existentes y workloads de analíticas a AWS, e incluso desde dentro de AWS
* Soporte para la mayoría de bases de datos open source
* Replica datos a demanda o de forma programada para replicar cambios
* No se puede utilizar para migrar una BD on-premise a otra on-premise

Existen dos tipos de migraciones:
* **Homogéneas**: la base de datos de origen y de destino usa el mismo motor
* **Heterogéneas**: los motores son distintos

### Herramientas para migraciones heterogéneas

* **AWS DMS Fleet Advisor**: automatiza el discovery de tus BDs on-premise para construir un inventario de las mismas.
* **AWS Schema Conversion Tool**: convierte el schema de origen y código SQL en otro schema y otro código equivalente de destino
* **AWS DMS Schema Conversion:** es un servicio de conversión y análisis de schemas que se encuentra disponible dentro de workflows de AWS DMS


## Buenas prácticas para WAF

Se pueden aplicar los pilares del AWS Well-Architected Framework (WAF) de la siguiente forma:

### Performance Efficiency

* Evaluar cómo los trade-offs impactan en los clientes y en la eficiencia de la arquitectura. Por ejemplo, si vamos a usar key-value store, considerar cómo la consistencia eventual afecta a los clientes.
* Usar un enfoque data-driven para elecciones de arquitectura
* Tener en cuenta el costo en la toma de decisiones.

### Seguridad

* Gestionar las claves de forma segura, incluyendo el almacenamiento, la rotación y el control de acceso de las claves.
* Forzar la encripción de los datos *at-rest*, principalmente sacando provecho de AWS KMS, que ya está automáticamente integrado en servicios como RDS y DynamoDB.

### Optimización de costos

* Seleccionar el tipo de recurso, el tamaño y la cantidad basándose en los datos: por ejemplo, determinar si la tarea es intensiva en cómputo, memoria, throughput (tamaño de los datos dividido el tiempo que tardan en llegar) o escritura.



