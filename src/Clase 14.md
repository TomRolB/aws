# Planeamiento para desastres

> Esta clase abarca el módulo 16 del curso de AWS Cloud Architecting

![Imagen 2-1](images/clase_15_page2_img1.png)

![Imagen 2-2](images/clase_15_page2_img2.png)

![Imagen 2-3](images/clase_15_page2_img3.png)

### Objetivos

Identificar estrategias de planificación de actividades ante desastres,

incluyendo los recovery point objective (RPO) y los recovery time

objective (RTO) sobre la base de los requerimientos de negocio.

Identificar las categorías de servicios de planeamiento para desastres

de AWS.

Describir los patrones comunes para la recuperación ante desastres y

cómo implementarlos.

Aplicar los principios del AWS Well-Architected Framework al diseño de

un plan de recuperación ante desastres.

![Imagen 3-1](images/clase_15_page3_img1.png)

![Imagen 3-2](images/clase_15_page3_img2.png)

![Imagen 3-3](images/clase_15_page3_img3.png)

Objetivos

### De un arquitecto de nube

### Diseñar arquitecturas que mitigan el riesgo ante desastres y

permiten una recuperación oportuna cuando suceden, para

contribuir a minimizar el impacto de un desastre en el negocio.

### Considerar las necesidades de negocio para aplicar patrones

de recuperación ante desastres que balanceen el costo, la

pérdida de datos y el tiempo de recuperación.

![Imagen 4-1](images/clase_15_page4_img1.png)

![Imagen 4-2](images/clase_15_page4_img2.png)

![Imagen 4-3](images/clase_15_page4_img3.png)

Estrategias de recuperación

![Imagen 5-1](images/clase_15_page5_img1.png)

![Imagen 5-2](images/clase_15_page5_img2.png)

![Imagen 5-3](images/clase_15_page5_img3.png)

### Escala de eventos

### Eventos de menor escala Eventos a gran escala Evento global

Caída de servidor Múltiples recursos no Falla generalizada

disponibles en una que afecta a múltiples

Availability Zone. usuarios y sistemas.

![Imagen 6-1](images/clase_15_page6_img1.png)

![Imagen 6-2](images/clase_15_page6_img2.png)

![Imagen 6-3](images/clase_15_page6_img3.png)

![Imagen 6-4](images/clase_15_page6_img4.png)

![Imagen 6-5](images/clase_15_page6_img5.png)

![Imagen 6-6](images/clase_15_page6_img6.png)

Estrategias de continuidad

### Fault tolerance Backup Disaster recovery

### Minimizar la frecuencia Asegurar la existencia Recuperar los datos y

de situaciones que de un plan de backup reestablecer las

dejan los datos no para gestionar los datos aplicaciones después

disponibles. ante desastres. de un desastre.

![Imagen 7-1](images/clase_15_page7_img1.png)

![Imagen 7-2](images/clase_15_page7_img2.png)

![Imagen 7-3](images/clase_15_page7_img3.png)

![Imagen 7-4](images/clase_15_page7_img4.png)

![Imagen 7-5](images/clase_15_page7_img5.png)

![Imagen 7-6](images/clase_15_page7_img6.png)

Estrategias de continuidad

Dependencia del Pérdida de datos Ubicación Costo

tiempo geográfica

¿El nivel de

¿Con qué ¿Qué cantidad ¿Tiene impacto

costos es acorde

velocidad de datos en varias

al impacto en el

debemos toleramos regiones?

negocio y a los

recuperar los perder? ¿Qué

¿Las distintas

riesgos?

servicios para tipos de datos

regiones

minimizar el podemos

requieren

impacto? perder?

medidas de

recuperación

distintas?

![Imagen 8-1](images/clase_15_page8_img1.png)

![Imagen 8-2](images/clase_15_page8_img2.png)

![Imagen 8-3](images/clase_15_page8_img3.png)

![Imagen 8-4](images/clase_15_page8_img4.png)

![Imagen 8-5](images/clase_15_page8_img5.png)

![Imagen 8-6](images/clase_15_page8_img6.png)

![Imagen 8-7](images/clase_15_page8_img7.png)

### Determinación del RPO

Es la pérdida de datos máxima que resulta aceptable, medida en

tiempo.

¿Con qué frecuencia debemos resguardar los

datos?

8 hours or fewer RPO

Time

[ data loss ]

Last backup Disaster strikes

![Imagen 9-1](images/clase_15_page9_img1.png)

![Imagen 9-2](images/clase_15_page9_img2.png)

![Imagen 9-3](images/clase_15_page9_img3.png)

![Imagen 9-4](images/clase_15_page9_img4.png)

![Imagen 9-5](images/clase_15_page9_img5.png)

### Determinación del RPO

Determinar que una Usar los patrones Calcular el RPO

pérdida máxima de existentes para aceptable de 8

800 registros es determinar que no horas.

aceptable para tu se crean más de

aplicación. 100 registros por

hora.

### Con esta información, podemos ver que, si a las 10 pm se produce un desastre, el

sistema debería poder recuperar toda la información que estaba en el sistema antes

de las 2pm

![Imagen 10-1](images/clase_15_page10_img1.png)

![Imagen 10-2](images/clase_15_page10_img2.png)

![Imagen 10-3](images/clase_15_page10_img3.png)

![Imagen 10-4](images/clase_15_page10_img4.png)

![Imagen 10-5](images/clase_15_page10_img5.png)

![Imagen 10-6](images/clase_15_page10_img6.png)

### Determinación del RTO

RTO es el tiempo máximo de indisponibilidad de un proceso después de

que se produce un desastre.

¿Cuán rápido deben recuperarse los datos y

aplicaciones?

8 hours or fewer RPO 1 hour RTO

Time

[ data loss ] [ down time ]

Último backup Desastre Datos y

aplicaciones

recuperados

![Imagen 11-1](images/clase_15_page11_img1.png)

![Imagen 11-2](images/clase_15_page11_img2.png)

![Imagen 11-3](images/clase_15_page11_img3.png)

![Imagen 11-4](images/clase_15_page11_img4.png)

![Imagen 11-5](images/clase_15_page11_img5.png)

![Imagen 11-6](images/clase_15_page11_img6.png)

### Determinación del RTO

### Determinar que un servicio El negocio calcula que Calcular un RTO aceptable

de tickets para un show después de 2 horas de de 2 horas.

musical se debe restaurar caída, comenzará a

dentro de dos horas. perder ganancias por

ventas perdidas.

Sobre la base de esta información, si un desastre ocurre a las 9 p.m., el Sistema se

debería poder recuperar antes de las 11 pm.

![Imagen 12-1](images/clase_15_page12_img1.png)

![Imagen 12-2](images/clase_15_page12_img2.png)

![Imagen 12-3](images/clase_15_page12_img3.png)

![Imagen 12-4](images/clase_15_page12_img4.png)

![Imagen 12-5](images/clase_15_page12_img5.png)

![Imagen 12-6](images/clase_15_page12_img6.png)

### Preparación para el BCP

Un plan de continuidad de negocios (BCP) es un Sistema

para la prevención y la recuperación respecto de

amenazas potenciales para una compañía.

Un BCP está conformado por:

- Business Impact Analysis

- Evaluación de riesgos

- Disaster Recovery Plan

- RPO y RTO evaluados y definidos

![Imagen 13-1](images/clase_15_page13_img1.png)

![Imagen 13-2](images/clase_15_page13_img2.png)

![Imagen 13-3](images/clase_15_page13_img3.png)

### Resumen

Puede haber fallas en cualquier momento y en cualquier escala.

Un plan de recuperación contribuye a reducir el impacto de un

desastre sobre el negocio y los clientes.

El RPO es la pérdida de datos máxima aceptable luego de un

incidente de pérdida de datos.

### El RTO es el tiempo que una aplicación, sistema o proceso puede

estar caído sin provocar un daño significativo al negocio.

Un BCP permite prevenir y recuperar incidentes potenciales.

![Imagen 14-1](images/clase_15_page14_img1.png)

![Imagen 14-2](images/clase_15_page14_img2.png)

![Imagen 14-3](images/clase_15_page14_img3.png)

AWS Disaster Recovery Planning

![Imagen 15-1](images/clase_15_page15_img1.png)

![Imagen 15-2](images/clase_15_page15_img2.png)

![Imagen 15-3](images/clase_15_page15_img3.png)

DRP en más de una región

Region 1 Region 2

### Storage Compute Database Storage Compute Database

Networking & Management & Networking & Management &

Content Governance Content Governance

Delivery Delivery

![Imagen 16-1](images/clase_15_page16_img1.png)

![Imagen 16-2](images/clase_15_page16_img2.png)

![Imagen 16-3](images/clase_15_page16_img3.png)

![Imagen 16-4](images/clase_15_page16_img4.png)

![Imagen 16-5](images/clase_15_page16_img5.png)

![Imagen 16-6](images/clase_15_page16_img6.png)

![Imagen 16-7](images/clase_15_page16_img7.png)

![Imagen 16-8](images/clase_15_page16_img8.png)

![Imagen 16-9](images/clase_15_page16_img9.png)

![Imagen 16-10](images/clase_15_page16_img10.png)

![Imagen 16-11](images/clase_15_page16_img11.png)

![Imagen 16-12](images/clase_15_page16_img12.png)

![Imagen 16-13](images/clase_15_page16_img13.png)

![Imagen 16-14](images/clase_15_page16_img14.png)

![Imagen 16-15](images/clase_15_page16_img15.png)

Almacenamiento y backups

On-premises AWS Cloud

data center

Tape

Amazon EBS EBS Volume

Gateway

AWS DataSync

File

gateway

AWS Direct Connect Amazon EFS Amazon FSx for

Windows File Server

## AWS

Storage Gateway

Volume

Gateway

Amazon S3 Amazon S3

Glacier

DataSync

agent

![Imagen 17-1](images/clase_15_page17_img1.png)

![Imagen 17-2](images/clase_15_page17_img2.png)

![Imagen 17-3](images/clase_15_page17_img3.png)

![Imagen 17-4](images/clase_15_page17_img4.png)

![Imagen 17-5](images/clase_15_page17_img5.png)

![Imagen 17-6](images/clase_15_page17_img6.png)

![Imagen 17-7](images/clase_15_page17_img7.png)

![Imagen 17-8](images/clase_15_page17_img8.png)

![Imagen 17-9](images/clase_15_page17_img9.png)

![Imagen 17-10](images/clase_15_page17_img10.png)

![Imagen 17-11](images/clase_15_page17_img11.png)

![Imagen 17-12](images/clase_15_page17_img12.png)

![Imagen 17-13](images/clase_15_page17_img13.png)

![Imagen 17-14](images/clase_15_page17_img14.png)

![Imagen 17-15](images/clase_15_page17_img15.png)

![Imagen 17-16](images/clase_15_page17_img16.png)

![Imagen 17-17](images/clase_15_page17_img17.png)

![Imagen 17-18](images/clase_15_page17_img18.png)

Réplica entre regiones

AWS Cloud

Region A Region B

Source S3 bucket Destination

(replication S3 bucket

configured)

![Imagen 18-1](images/clase_15_page18_img1.png)

![Imagen 18-2](images/clase_15_page18_img2.png)

![Imagen 18-3](images/clase_15_page18_img3.png)

![Imagen 18-4](images/clase_15_page18_img4.png)

![Imagen 18-5](images/clase_15_page18_img5.png)

![Imagen 18-6](images/clase_15_page18_img6.png)

![Imagen 18-7](images/clase_15_page18_img7.png)

![Imagen 18-8](images/clase_15_page18_img8.png)

Snapshots de volúmenes de EBS

AWS Cloud

Region A Region B

Source Snapshot Copy of

EBS volume stored in snapshot

Amazon S3

![Imagen 19-1](images/clase_15_page19_img1.png)

![Imagen 19-2](images/clase_15_page19_img2.png)

![Imagen 19-3](images/clase_15_page19_img3.png)

![Imagen 19-4](images/clase_15_page19_img4.png)

![Imagen 19-5](images/clase_15_page19_img5.png)

![Imagen 19-6](images/clase_15_page19_img6.png)

![Imagen 19-7](images/clase_15_page19_img7.png)

![Imagen 19-8](images/clase_15_page19_img8.png)

![Imagen 19-9](images/clase_15_page19_img9.png)

Réplica de file servers

AWS Cloud

On-premises

Region A Region B

data center

Source

Source AWS Destination AWS

AWS Direct

file system

Amazon EFS or DataSync Amazon EFS or DataSync

Connect

Amazon FSx Amazon FSx

(optional)

![Imagen 20-1](images/clase_15_page20_img1.png)

![Imagen 20-2](images/clase_15_page20_img2.png)

![Imagen 20-3](images/clase_15_page20_img3.png)

![Imagen 20-4](images/clase_15_page20_img4.png)

![Imagen 20-5](images/clase_15_page20_img5.png)

![Imagen 20-6](images/clase_15_page20_img6.png)

![Imagen 20-7](images/clase_15_page20_img7.png)

![Imagen 20-8](images/clase_15_page20_img8.png)

![Imagen 20-9](images/clase_15_page20_img9.png)

![Imagen 20-10](images/clase_15_page20_img10.png)

![Imagen 20-11](images/clase_15_page20_img11.png)

![Imagen 20-12](images/clase_15_page20_img12.png)

![Imagen 20-13](images/clase_15_page20_img13.png)

### Recuperación de infraestructura

Es posible obtener e iniciar nuevas instancias y contenedores en pocos minutos

Custom AMIs (Golden Custom container

AMIs) images

Amazon Elastic Container Service cluster

Auto Scaling group

## EC2 EC2 EC2 ECS ECS ECS ECS

Instance 1 Instance 2 Instance 3 Container 1 Container 2 Container 3 Container 4

![Imagen 21-1](images/clase_15_page21_img1.png)

![Imagen 21-2](images/clase_15_page21_img2.png)

![Imagen 21-3](images/clase_15_page21_img3.png)

![Imagen 21-4](images/clase_15_page21_img4.png)

![Imagen 21-5](images/clase_15_page21_img5.png)

![Imagen 21-6](images/clase_15_page21_img6.png)

![Imagen 21-7](images/clase_15_page21_img7.png)

![Imagen 21-8](images/clase_15_page21_img8.png)

![Imagen 21-9](images/clase_15_page21_img9.png)

![Imagen 21-10](images/clase_15_page21_img10.png)

![Imagen 21-11](images/clase_15_page21_img11.png)

![Imagen 21-12](images/clase_15_page21_img12.png)

![Imagen 21-13](images/clase_15_page21_img13.png)

![Imagen 21-14](images/clase_15_page21_img14.png)

Uso de EventBridge para failover

Primary Region Route 53 Secondary Region

Alarm

1

Global Amazon

endpoint Route 53

alarm health Amazon

check EventBridge

Failover

PutEvents

Global Orders

Event 2

endpoint event

producer

Global managed

bus

endpoint rule

Event Archiv

consumers e

![Imagen 22-1](images/clase_15_page22_img1.png)

![Imagen 22-2](images/clase_15_page22_img2.png)

![Imagen 22-3](images/clase_15_page22_img3.png)

![Imagen 22-4](images/clase_15_page22_img4.png)

![Imagen 22-5](images/clase_15_page22_img5.png)

![Imagen 22-6](images/clase_15_page22_img6.png)

![Imagen 22-7](images/clase_15_page22_img7.png)

![Imagen 22-8](images/clase_15_page22_img8.png)

![Imagen 22-9](images/clase_15_page22_img9.png)

![Imagen 22-10](images/clase_15_page22_img10.png)

![Imagen 22-11](images/clase_15_page22_img11.png)

![Imagen 22-12](images/clase_15_page22_img12.png)

![Imagen 22-13](images/clase_15_page22_img13.png)

![Imagen 22-14](images/clase_15_page22_img14.png)

![Imagen 22-15](images/clase_15_page22_img15.png)

Diseño para la resiliencia y recuperación

Route 53 ELB Amazon VPN AWS Direct Connect

### Balanceo de Provee Provee acceso Conexión

carga basado distribución de seguro a la red dedicada que

en DNS tráfico on-premise no depende de

desde la VPC de internet

Brinda failover Facilita la

Amazon a través

básico entre los implementación

de una VPN

endpoints o los de recuperación

sitios de S3 ante desastres

![Imagen 23-1](images/clase_15_page23_img1.png)

![Imagen 23-2](images/clase_15_page23_img2.png)

![Imagen 23-3](images/clase_15_page23_img3.png)

![Imagen 23-4](images/clase_15_page23_img4.png)

![Imagen 23-5](images/clase_15_page23_img5.png)

![Imagen 23-6](images/clase_15_page23_img6.png)

![Imagen 23-7](images/clase_15_page23_img7.png)

Recuperación de bases de datos

### Amazon RDS DynamoDB

Guardar un snapshot en una región Hacer backups de tablas completas.

separada.

### Usar point-in-time-recovery para

Usar read replicas e implementaciones restaurar tablas.

Multi-AZ.

Crear backups.

Retener backups automáticos.

Usar tablas globales para construir una

base de datos multi-región.

![Imagen 24-1](images/clase_15_page24_img1.png)

![Imagen 24-2](images/clase_15_page24_img2.png)

![Imagen 24-3](images/clase_15_page24_img3.png)

![Imagen 24-4](images/clase_15_page24_img4.png)

![Imagen 24-5](images/clase_15_page24_img5.png)

Réplicas y reinstalaciones

### CloudFormation

Usar templates para implementar colecciones de recursos

rápidamente según la necesidad.

Duplicar los ambientes de producción en una nueva región o

VPC más rápidamente.

![Imagen 25-1](images/clase_15_page25_img1.png)

![Imagen 25-2](images/clase_15_page25_img2.png)

![Imagen 25-3](images/clase_15_page25_img3.png)

![Imagen 25-4](images/clase_15_page25_img4.png)

Réplicas y reinstalaciones

Backup and Pilot light Warm standby Multi-site

restore

Cada patrón se aplica a un escenario diferente (RPO, RTO y costos).

![Imagen 26-1](images/clase_15_page26_img1.png)

![Imagen 26-2](images/clase_15_page26_img2.png)

![Imagen 26-3](images/clase_15_page26_img3.png)

![Imagen 26-4](images/clase_15_page26_img4.png)

![Imagen 26-5](images/clase_15_page26_img5.png)

![Imagen 26-6](images/clase_15_page26_img6.png)

![Imagen 26-7](images/clase_15_page26_img7.png)

![Imagen 26-8](images/clase_15_page26_img8.png)

![Imagen 26-9](images/clase_15_page26_img9.png)

Backup & restore

AWS Cloud

Region

30-day 90-day

lifecycle policy lifecycle policy

Backup

Amazon S3 Amazon S3 Glacier

S3 Standard

Standard-IA Flexible Retrieval

bucket

Restoring from point in time

Restore

Amazon S3 Glacier S3 Standard

Flexible Retrieval bucket

![Imagen 27-1](images/clase_15_page27_img1.png)

![Imagen 27-2](images/clase_15_page27_img2.png)

![Imagen 27-3](images/clase_15_page27_img3.png)

![Imagen 27-4](images/clase_15_page27_img4.png)

![Imagen 27-5](images/clase_15_page27_img5.png)

![Imagen 27-6](images/clase_15_page27_img6.png)

![Imagen 27-7](images/clase_15_page27_img7.png)

![Imagen 27-8](images/clase_15_page27_img8.png)

![Imagen 27-9](images/clase_15_page27_img9.png)

![Imagen 27-10](images/clase_15_page27_img10.png)

![Imagen 27-11](images/clase_15_page27_img11.png)

![Imagen 27-12](images/clase_15_page27_img12.png)

![Imagen 27-13](images/clase_15_page27_img13.png)

![Imagen 27-14](images/clase_15_page27_img14.png)

![Imagen 27-15](images/clase_15_page27_img15.png)

![Imagen 27-16](images/clase_15_page27_img16.png)

AWS Storage Gateway

On premises data AWS Cloud

center

Amazon EBS EBS Volume

Tape Gateway

## AWS

DataSync

File Gateway

AWS Direct Connect Amazon EFS Amazon FSx for

Windows File Server

AWS Storage

Gateway

Volume Gateway

Amazon S3 Amazon S3

Glacier

DataSync agent

![Imagen 28-1](images/clase_15_page28_img1.png)

![Imagen 28-2](images/clase_15_page28_img2.png)

![Imagen 28-3](images/clase_15_page28_img3.png)

![Imagen 28-4](images/clase_15_page28_img4.png)

![Imagen 28-5](images/clase_15_page28_img5.png)

![Imagen 28-6](images/clase_15_page28_img6.png)

![Imagen 28-7](images/clase_15_page28_img7.png)

![Imagen 28-8](images/clase_15_page28_img8.png)

![Imagen 28-9](images/clase_15_page28_img9.png)

![Imagen 28-10](images/clase_15_page28_img10.png)

![Imagen 28-11](images/clase_15_page28_img11.png)

![Imagen 28-12](images/clase_15_page28_img12.png)

![Imagen 28-13](images/clase_15_page28_img13.png)

![Imagen 28-14](images/clase_15_page28_img14.png)

![Imagen 28-15](images/clase_15_page28_img15.png)

![Imagen 28-16](images/clase_15_page28_img16.png)

![Imagen 28-17](images/clase_15_page28_img17.png)

![Imagen 28-18](images/clase_15_page28_img18.png)

AWS Storage Gateway

### Preparación En caso de desastre

Crear backups de los sistemas Recuperar las copias de

actuales. seguridad de S3.

Almacenar los resguardos en Restaurar la infraestructura

Amazon S3. necesaria.

Documentar los procedimientos Recuperar los sistemas a partir de

de restauración. los backups.

Redirigir el tráfico al nuevo

sistema.

![Imagen 29-1](images/clase_15_page29_img1.png)

![Imagen 29-2](images/clase_15_page29_img2.png)

![Imagen 29-3](images/clase_15_page29_img3.png)

![Imagen 29-4](images/clase_15_page29_img4.png)

![Imagen 29-5](images/clase_15_page29_img5.png)

Luz piloto

Region

www.example.co

On-premises or AWS Cloud

m

AWS Cloud

Primary Secondar

Web

y Minimal

Web servers server

Web server

servers

Route 53

active in

hosted zone

Web

case of

server

In case of failover

primary failure App server

App servers

Data replication

Secondary

Primary database

database

![Imagen 30-1](images/clase_15_page30_img1.png)

![Imagen 30-2](images/clase_15_page30_img2.png)

![Imagen 30-3](images/clase_15_page30_img3.png)

![Imagen 30-4](images/clase_15_page30_img4.png)

![Imagen 30-5](images/clase_15_page30_img5.png)

![Imagen 30-6](images/clase_15_page30_img6.png)

![Imagen 30-7](images/clase_15_page30_img7.png)

![Imagen 30-8](images/clase_15_page30_img8.png)

![Imagen 30-9](images/clase_15_page30_img9.png)

![Imagen 30-10](images/clase_15_page30_img10.png)

![Imagen 30-11](images/clase_15_page30_img11.png)

![Imagen 30-12](images/clase_15_page30_img12.png)

![Imagen 30-13](images/clase_15_page30_img13.png)

![Imagen 30-14](images/clase_15_page30_img14.png)

![Imagen 30-15](images/clase_15_page30_img15.png)

Luz piloto

### Fase de preparación En caso de desastre

### Se configuran instancias de EC2 Habilite los recursos necesarios para

para replica los servicios. el conjunto de datos principal

replicado.

Se crean y mantienen AMIs de los

servidores más importantes, que

A continuación, escale el sistema

necesitan recuperación rápida.

según sea necesario para gestionar

el tráfico de producción actual.

Se ejecutan, prueban y actualizan

regularmente esos servidores.

Cambie al nuevo sistema.

![Imagen 31-1](images/clase_15_page31_img1.png)

![Imagen 31-2](images/clase_15_page31_img2.png)

![Imagen 31-3](images/clase_15_page31_img3.png)

![Imagen 31-4](images/clase_15_page31_img4.png)

![Imagen 31-5](images/clase_15_page31_img5.png)

Warm stand by

Region

www.example.co

On-premises or AWS Cloud

m

AWS Cloud

Auto scaling

group

Primary Secondar

y

Web servers

Web server

Low

Route 53

capacity

Auto

hosted zone

scaling

In case of group

primary failure

App servers

Web server

Data replication

Primary DB Secondary DB

![Imagen 32-1](images/clase_15_page32_img1.png)

![Imagen 32-2](images/clase_15_page32_img2.png)

![Imagen 32-3](images/clase_15_page32_img3.png)

![Imagen 32-4](images/clase_15_page32_img4.png)

![Imagen 32-5](images/clase_15_page32_img5.png)

![Imagen 32-6](images/clase_15_page32_img6.png)

![Imagen 32-7](images/clase_15_page32_img7.png)

![Imagen 32-8](images/clase_15_page32_img8.png)

![Imagen 32-9](images/clase_15_page32_img9.png)

![Imagen 32-10](images/clase_15_page32_img10.png)

![Imagen 32-11](images/clase_15_page32_img11.png)

![Imagen 32-12](images/clase_15_page32_img12.png)

![Imagen 32-13](images/clase_15_page32_img13.png)

![Imagen 32-14](images/clase_15_page32_img14.png)

![Imagen 32-15](images/clase_15_page32_img15.png)

![Imagen 32-16](images/clase_15_page32_img16.png)

![Imagen 32-17](images/clase_15_page32_img17.png)

Warm stand by

### Preparación En caso de desastre

Similar al piloto. La carga más crítica de producción

se carga inmediatamente.

### Tiene todos los componentes

necesarios funcionando 24/7, pero Escalar el sistema para administrar

no están escalados el tráfico de toda la carga de producción

producción. (automáticamente)

Se deben realizar pruebas continuas

de los componentes.

![Imagen 33-1](images/clase_15_page33_img1.png)

![Imagen 33-2](images/clase_15_page33_img2.png)

![Imagen 33-3](images/clase_15_page33_img3.png)

![Imagen 33-4](images/clase_15_page33_img4.png)

![Imagen 33-5](images/clase_15_page33_img5.png)

Patrones multisitio

Region

www.example.co

On-premises or AWS Cloud

m

AWS Cloud

Auto

scaling

group

Primary Secondary

Full

Web servers Web servers

capacity

Route 53

always

Auto

hosted zone

running

scaling

In case of group

primary failure

App servers

App servers

Data replication

Primary DB Secondary DB

![Imagen 34-1](images/clase_15_page34_img1.png)

![Imagen 34-2](images/clase_15_page34_img2.png)

![Imagen 34-3](images/clase_15_page34_img3.png)

![Imagen 34-4](images/clase_15_page34_img4.png)

![Imagen 34-5](images/clase_15_page34_img5.png)

![Imagen 34-6](images/clase_15_page34_img6.png)

![Imagen 34-7](images/clase_15_page34_img7.png)

![Imagen 34-8](images/clase_15_page34_img8.png)

![Imagen 34-9](images/clase_15_page34_img9.png)

![Imagen 34-10](images/clase_15_page34_img10.png)

![Imagen 34-11](images/clase_15_page34_img11.png)

![Imagen 34-12](images/clase_15_page34_img12.png)

![Imagen 34-13](images/clase_15_page34_img13.png)

![Imagen 34-14](images/clase_15_page34_img14.png)

![Imagen 34-15](images/clase_15_page34_img15.png)

![Imagen 34-16](images/clase_15_page34_img16.png)

![Imagen 34-17](images/clase_15_page34_img17.png)

Patrones multisitio

### Preparación En caso de desastre

Similar al warm standby. Failover inmediato de toda la

carga de producción.

Está configurado para escalar

automáticamente para soportar

las cargas de producción.

Hay que evaluar los costos de

este tipo de implementación en

función de la criticidad del

sistema.

![Imagen 35-1](images/clase_15_page35_img1.png)

![Imagen 35-2](images/clase_15_page35_img2.png)

![Imagen 35-3](images/clase_15_page35_img3.png)

![Imagen 35-4](images/clase_15_page35_img4.png)

![Imagen 35-5](images/clase_15_page35_img5.png)

### Patrones de recuperación ante desastres

Backup and restore Pilot light Warm standby Multi-site

### Costo

### Soluciones con Soluciones que Soluciones que Soluciones que

### RTO/RPO en lapsos requieren RTO y RPO requieren RTO y RPO requieren RTO and

de horas en el orden de en el orden de RPO prácticamente

decenas de minutos minutos en tiempo real.

### Casos de uso de

menor prioridad Servicios principales Servicios críticos Failover automático

para el negocio a un duplicado que

Soluciones: Amazon Escalamiento de

está en ejecución.

S3, Storage recursos de AWS

Gateway

![Imagen 36-1](images/clase_15_page36_img1.png)

![Imagen 36-2](images/clase_15_page36_img2.png)

![Imagen 36-3](images/clase_15_page36_img3.png)

![Imagen 36-4](images/clase_15_page36_img4.png)

![Imagen 36-5](images/clase_15_page36_img5.png)

![Imagen 36-6](images/clase_15_page36_img6.png)

![Imagen 36-7](images/clase_15_page36_img7.png)

### Prácticas y ejercicios de continuidad

Asegurar que los resguardos, snapshots y AMIs están siendo creados y que se pueden

usar para recuperar los datos.

Controlar el Sistema de monitoreo.

Establecer RTO y RPO, y trabajar para mejorar la performance cuando sea posible.

more RTO Cost

less

Backup and Pilot light Warm standby Multi-site

restore

![Imagen 37-1](images/clase_15_page37_img1.png)

![Imagen 37-2](images/clase_15_page37_img2.png)

![Imagen 37-3](images/clase_15_page37_img3.png)

AWS Well-Architected Framework

Aplicado a la continuidad de negocio

![Imagen 38-1](images/clase_15_page38_img1.png)

![Imagen 38-2](images/clase_15_page38_img2.png)

![Imagen 38-3](images/clase_15_page38_img3.png)

Well-Architected Framework

![Imagen 39-1](images/clase_15_page39_img1.png)

![Imagen 39-2](images/clase_15_page39_img2.png)

![Imagen 39-3](images/clase_15_page39_img3.png)

![Imagen 39-4](images/clase_15_page39_img4.png)

![Imagen 39-5](images/clase_15_page39_img5.png)

![Imagen 39-6](images/clase_15_page39_img6.png)

Planificación de failover

Buena práctica

Definir los objetivos de recuperación, en

términos de caída y pérdida de datos.

Usar estrategias de recuperación

definidas para cumplir los objetivos de

recuperación.

Probar la implementación de

recuperación ante desastres para validar

la implementación.

![Imagen 40-1](images/clase_15_page40_img1.png)

![Imagen 40-2](images/clase_15_page40_img2.png)

![Imagen 40-3](images/clase_15_page40_img3.png)

![Imagen 40-4](images/clase_15_page40_img4.png)

Gestión de incidentes

Buena práctica

Definir un plan de comunicación a los

clientes para las caídas.

![Imagen 41-1](images/clase_15_page41_img1.png)

![Imagen 41-2](images/clase_15_page41_img2.png)

![Imagen 41-3](images/clase_15_page41_img3.png)

![Imagen 41-4](images/clase_15_page41_img4.png)

Gestión de accesos

Buena práctica

Establecer un proceso de acceso en

emergencia.

![Imagen 42-1](images/clase_15_page42_img1.png)

![Imagen 42-2](images/clase_15_page42_img2.png)

![Imagen 42-3](images/clase_15_page42_img3.png)

![Imagen 42-4](images/clase_15_page42_img4.png)

### Resumen

### Identificar estrategias de planificación de continuidad, incluyendo el

RPO y RTO sobre la base de los requerimientos de negocio.

Reconocer la planificación de desastre para categorías de servicio de

## AWS.

Describir patrones comunes para la aplicación de una estrategia de

backup y recuperación y cómo implementarlas.

Usar los principos del AWS Well-Architected Framework para diseñar un

plan de recuperación ante desastres.

![Imagen 43-1](images/clase_15_page43_img1.png)

![Imagen 43-2](images/clase_15_page43_img2.png)

![Imagen 43-3](images/clase_15_page43_img3.png)

Módulo 16

### Pregunta de práctica

A solutions architect must create a disaster recovery (DR) solution for a company's business-critical

applications. The maximum acceptable amount of data loss is 7 minutes. The DR solution also requires the

deployment of a completely functional version of the applications to handle the majority of traffic

immediately, and then scale up to full capacity over time. Which disaster recovery pattern would provide

the most cost-effective solution?

Identifiquemos las palabras o frases clave:

The following are the key words and phrases:

- Business-critical

- Functional version of the applications

- Handle the majority of traffic immediately

- Cost-effective

![Imagen 44-1](images/clase_15_page44_img1.png)

![Imagen 44-2](images/clase_15_page44_img2.png)

![Imagen 44-3](images/clase_15_page44_img3.png)

Módulo 16

### Pregunta de práctica

A solutions architect must create a disaster recovery (DR) solution for a company's business-critical

applications. The maximum acceptable amount of data loss is 7 minutes. The DR solution also requires the

deployment of a completely functional version of the applications to handle the majority of traffic

immediately, and then scale up to full capacity over time. Which disaster recovery pattern would provide

the most cost-effective solution?

Choice Response

A Backup and restore

B Pilot light

C Warm standby

D Multi-site

![Imagen 45-1](images/clase_15_page45_img1.png)

![Imagen 45-2](images/clase_15_page45_img2.png)

![Imagen 45-3](images/clase_15_page45_img3.png)

Módulo 16

### Pregunta de práctica

A solutions architect must create a disaster recovery (DR) solution for a company's business-critical

applications. The maximum acceptable amount of data loss is 7 minutes. The DR solution also requires the

deployment of a completely functional version of the applications to handle the majority of traffic

immediately, and then scale up to full capacity over time. Which disaster recovery pattern would provide

the most cost-effective solution?

Choice Response

C Warm standby

![Imagen 46-1](images/clase_15_page46_img1.png)

![Imagen 46-2](images/clase_15_page46_img2.png)

![Imagen 46-3](images/clase_15_page46_img3.png)

Muchas gracias.

www.austral.edu.ar

![Imagen 47-1](images/clase_15_page47_img1.png)

![Imagen 47-2](images/clase_15_page47_img2.png)

![Imagen 47-3](images/clase_15_page47_img3.png)
