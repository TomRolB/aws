# Arquitecturas serverless y microservicios

> Esta clase abarca el módulo 14 del curso de AWS Cloud Architecting

![Imagen 2-1](images/clase_13_page2_img1.png)

![Imagen 2-2](images/clase_13_page2_img2.png)

![Imagen 2-3](images/clase_13_page2_img3.png)

Objetivos

Definir arquitecturas serverless.

Identificar las características de los microservicios.

Diseñar una solución serverless con AWS Lambda.

Definir cómo se usan los contenedores en AWS.

Describir los tipos de flujo que soportan las AWS Step Functions.

Describir una arquitectura común para el Amazon API Gateway.

Aplicar los principios del AWS Well-Architected Framework para

construir arquitecturas serverless.

![Imagen 3-1](images/clase_13_page3_img1.png)

![Imagen 3-2](images/clase_13_page3_img2.png)

![Imagen 3-3](images/clase_13_page3_img3.png)

Objetivos

### De un arquitecto de nube

### Reconocer cuándo usar arquitecturas serverless en AWS y

qué servicios elegir, de acuerdo con el caso de uso.

### Implementar arquitecturas guiadas por eventos con

microservicios para construir arquitecturas de microservicios

escalables y resilientes.

### Conocer cuándo usar herramientas de orquestación para

que la arquitectura de microservicios trate las fallas con una

intervención manual mínima.

![Imagen 4-1](images/clase_13_page4_img1.png)

![Imagen 4-2](images/clase_13_page4_img2.png)

![Imagen 4-3](images/clase_13_page4_img3.png)

Soluciones serverless

![Imagen 5-1](images/clase_13_page5_img1.png)

![Imagen 5-2](images/clase_13_page5_img2.png)

![Imagen 5-3](images/clase_13_page5_img3.png)

Diseño de una aplicación web en una VPC

![Imagen 6-1](images/clase_13_page6_img1.png)

![Imagen 6-2](images/clase_13_page6_img2.png)

![Imagen 6-3](images/clase_13_page6_img3.png)

![Imagen 6-4](images/clase_13_page6_img4.png)

Beneficios de AWS serverless

No requiere Escalamiento

administrar servidores continuo

Se paga por el valor Alta disponibilidad

del servicio desde el diseño

Adecuado para arquitecturas

orientadas a eventos y microservicios

![Imagen 7-1](images/clase_13_page7_img1.png)

![Imagen 7-2](images/clase_13_page7_img2.png)

![Imagen 7-3](images/clase_13_page7_img3.png)

![Imagen 7-4](images/clase_13_page7_img4.png)

![Imagen 7-5](images/clase_13_page7_img5.png)

![Imagen 7-6](images/clase_13_page7_img6.png)

![Imagen 7-7](images/clase_13_page7_img7.png)

![Imagen 7-8](images/clase_13_page7_img8.png)

Servicios serverless de AWS

Compute Application integration Data stores

AWS AppSync

Amazon API Amazon S3 Amazon EFS

AWS Fargate

AWS Lambda and

Gateway

Lambda@Edge

Authentication

Amazon Amazon Neptune

DynamoDB Serverless

Amazon Cognito

Amazon Simple Amazon Simple

Web hosting

Notification Service Queue Service

(Amazon SNS) (Amazon SQS)

Amazon Aurora

Serverless Amazon Redshift

AWS Amplify Serverless

Amazon AWS Step

Content delivery

EventBridge Functions

Amazon OpenSearch

Serverless

![Imagen 8-1](images/clase_13_page8_img1.png)

![Imagen 8-2](images/clase_13_page8_img2.png)

![Imagen 8-3](images/clase_13_page8_img3.png)

![Imagen 8-4](images/clase_13_page8_img4.png)

![Imagen 8-5](images/clase_13_page8_img5.png)

![Imagen 8-6](images/clase_13_page8_img6.png)

![Imagen 8-7](images/clase_13_page8_img7.png)

![Imagen 8-8](images/clase_13_page8_img8.png)

![Imagen 8-9](images/clase_13_page8_img9.png)

![Imagen 8-10](images/clase_13_page8_img10.png)

![Imagen 8-11](images/clase_13_page8_img11.png)

![Imagen 8-12](images/clase_13_page8_img12.png)

![Imagen 8-13](images/clase_13_page8_img13.png)

![Imagen 8-14](images/clase_13_page8_img14.png)

![Imagen 8-15](images/clase_13_page8_img15.png)

![Imagen 8-16](images/clase_13_page8_img16.png)

![Imagen 8-17](images/clase_13_page8_img17.png)

![Imagen 8-18](images/clase_13_page8_img18.png)

![Imagen 8-19](images/clase_13_page8_img19.png)

![Imagen 8-20](images/clase_13_page8_img20.png)

![Imagen 8-21](images/clase_13_page8_img21.png)

Aplicación web usando servicios serverless

![Imagen 9-1](images/clase_13_page9_img1.png)

![Imagen 9-2](images/clase_13_page9_img2.png)

![Imagen 9-3](images/clase_13_page9_img3.png)

![Imagen 9-4](images/clase_13_page9_img4.png)

### Resumen

Los servicios serverless AWS tienen los siguientes beneficios:

- No es necesario administrar servidores

- Se paga por el valor del servicio

- Tienen escalamiento continuo

- Son tolerantes a fallas por diseño

Estos servicios son adecuados para arquitecturas orientadas a

eventos y microservicios.

![Imagen 10-1](images/clase_13_page10_img1.png)

![Imagen 10-2](images/clase_13_page10_img2.png)

![Imagen 10-3](images/clase_13_page10_img3.png)

Arquitectura de microservicios

serverless

![Imagen 11-1](images/clase_13_page11_img1.png)

![Imagen 11-2](images/clase_13_page11_img2.png)

![Imagen 11-3](images/clase_13_page11_img3.png)

Microservicios

Características

### Autónomo Especializado

### Se puede desarrollar e implementar Realiza una única función de

sin afectar a otros microservicios negocio, resolviendo un problema

específico.

Escala de manera independiente

Pertenece a un equipo de desarrollo

No comparte código con otros

pequeño que selecciona

microservicios

herramientas de desarrollo

### Se comunica mediante APIs bien

Es stateless

definidas

Tiene su propio almacenamiento de

datos

![Imagen 12-1](images/clase_13_page12_img1.png)

![Imagen 12-2](images/clase_13_page12_img2.png)

![Imagen 12-3](images/clase_13_page12_img3.png)

![Imagen 12-4](images/clase_13_page12_img4.png)

Comparación

Monolithic application Microservice application

User service

Users

Topics

Topic service

Messages

Message service

![Imagen 13-1](images/clase_13_page13_img1.png)

![Imagen 13-2](images/clase_13_page13_img2.png)

![Imagen 13-3](images/clase_13_page13_img3.png)

![Imagen 13-4](images/clase_13_page13_img4.png)

![Imagen 13-5](images/clase_13_page13_img5.png)

![Imagen 13-6](images/clase_13_page13_img6.png)

![Imagen 13-7](images/clase_13_page13_img7.png)

![Imagen 13-8](images/clase_13_page13_img8.png)

![Imagen 13-9](images/clase_13_page13_img9.png)

Microservicios

Beneficios

Agilidad Código reutilizable Escalamiento

flexible

Libertad Resiliencia Implementación

tecnológica simplificada

![Imagen 14-1](images/clase_13_page14_img1.png)

![Imagen 14-2](images/clase_13_page14_img2.png)

![Imagen 14-3](images/clase_13_page14_img3.png)

![Imagen 14-4](images/clase_13_page14_img4.png)

![Imagen 14-5](images/clase_13_page14_img5.png)

![Imagen 14-6](images/clase_13_page14_img6.png)

![Imagen 14-7](images/clase_13_page14_img7.png)

![Imagen 14-8](images/clase_13_page14_img8.png)

![Imagen 14-9](images/clase_13_page14_img9.png)

Patrones de microservicios serverless en AWS

### RESTful APIs Contenedores Streaming

Amazon API Gateway Amazon API Gateway Application Load Amazon Kinesis

Balancer

## AWS AWS

Lambda Lambda

AWS Fargate

![Imagen 15-1](images/clase_13_page15_img1.png)

![Imagen 15-2](images/clase_13_page15_img2.png)

![Imagen 15-3](images/clase_13_page15_img3.png)

![Imagen 15-4](images/clase_13_page15_img4.png)

![Imagen 15-5](images/clase_13_page15_img5.png)

![Imagen 15-6](images/clase_13_page15_img6.png)

![Imagen 15-7](images/clase_13_page15_img7.png)

![Imagen 15-8](images/clase_13_page15_img8.png)

![Imagen 15-9](images/clase_13_page15_img9.png)

![Imagen 15-10](images/clase_13_page15_img10.png)

![Imagen 15-11](images/clase_13_page15_img11.png)

![Imagen 15-12](images/clase_13_page15_img12.png)

![Imagen 15-13](images/clase_13_page15_img13.png)

Microservicios en una arquitectura web

serverless

![Imagen 16-1](images/clase_13_page16_img1.png)

![Imagen 16-2](images/clase_13_page16_img2.png)

![Imagen 16-3](images/clase_13_page16_img3.png)

![Imagen 16-4](images/clase_13_page16_img4.png)

### Resumen

Las aplicaciones basadas en microservicios están compuestas

por servicios autónomos y especializados.

### Los microservicios tienen ventajas como: agilidad, reutilización

de código, escalamiento flexible, resiliencia, etc.

### Los microservicios pueden formar parte de una arquitectura de

tres capas, operando en las capas de datos y aplicación.

![Imagen 17-1](images/clase_13_page17_img1.png)

![Imagen 17-2](images/clase_13_page17_img2.png)

![Imagen 17-3](images/clase_13_page17_img3.png)

Arquitecturas serverless con

AWS Lambda

![Imagen 18-1](images/clase_13_page18_img1.png)

![Imagen 18-2](images/clase_13_page18_img2.png)

![Imagen 18-3](images/clase_13_page18_img3.png)

Comparación de tareas operacionales

Tareas Servidor en una VPC Serverless

Configurar una instancia Yes No

Actualizar el sistema operativo Yes No

Instalar la plataforma de aplicación Yes No

### Construir e implementar aplicaciones Yes Yes

### Configurar el escalamiento y el balanceo de carga Yes No

Proteger y monitorear instancias continuamente Yes No

Monitorear y mantener las aplicaciones Yes Yes

![Imagen 19-1](images/clase_13_page19_img1.png)

![Imagen 19-2](images/clase_13_page19_img2.png)

![Imagen 19-3](images/clase_13_page19_img3.png)

AWS Lambda

AWS Lambda permite ejecutar funciones de código

sin crear ni gestionar servidores.

Las funciones Lambda son configurables respecto

de: lenguaje de ejecución, cantidad de memoria y

duración.

AWS Lambda Una función puede durar15 minutos como máximo.

Las funciones se implementan como archivos .zip o

imágenes de contenedores.

![Imagen 20-1](images/clase_13_page20_img1.png)

![Imagen 20-2](images/clase_13_page20_img2.png)

![Imagen 20-3](images/clase_13_page20_img3.png)

![Imagen 20-4](images/clase_13_page20_img4.png)

Funciones Lambda

Ubicaciones

En un cache regional de Amazon

En el servicio AWS Lambda

CloudFront

![Imagen 21-1](images/clase_13_page21_img1.png)

![Imagen 21-2](images/clase_13_page21_img2.png)

![Imagen 21-3](images/clase_13_page21_img3.png)

![Imagen 21-4](images/clase_13_page21_img4.png)

![Imagen 21-5](images/clase_13_page21_img5.png)

Conectar una función Lambda a una VPC

![Imagen 22-1](images/clase_13_page22_img1.png)

![Imagen 22-2](images/clase_13_page22_img2.png)

![Imagen 22-3](images/clase_13_page22_img3.png)

![Imagen 22-4](images/clase_13_page22_img4.png)

### Escenarios para usar funciones Lambda

### Procesamiento sincrónico Procesamiento asincrónico Procesamiento de streaming

- Aplicaciones web • Eventos programados Aplicaciones de streaming

- Servicios web • Mensajes en colas

- Microservicios • Transformación de

imagen o video

- Inferencias de machine

learning • Triggers de servicios de

## AWS

![Imagen 23-1](images/clase_13_page23_img1.png)

![Imagen 23-2](images/clase_13_page23_img2.png)

![Imagen 23-3](images/clase_13_page23_img3.png)

![Imagen 23-4](images/clase_13_page23_img4.png)

![Imagen 23-5](images/clase_13_page23_img5.png)

![Imagen 23-6](images/clase_13_page23_img6.png)

Funciones Lambda sincrónicas

Llamadas

### Usando un API Gateway

Usando la URL de la función Lambda desde una API externa

![Imagen 24-1](images/clase_13_page24_img1.png)

![Imagen 24-2](images/clase_13_page24_img2.png)

![Imagen 24-3](images/clase_13_page24_img3.png)

![Imagen 24-4](images/clase_13_page24_img4.png)

![Imagen 24-5](images/clase_13_page24_img5.png)

Funciones Lambda asincrónicas

Llamadas

Trigger de un servicio de AWS

Evento programado

![Imagen 25-1](images/clase_13_page25_img1.png)

![Imagen 25-2](images/clase_13_page25_img2.png)

![Imagen 25-3](images/clase_13_page25_img3.png)

![Imagen 25-4](images/clase_13_page25_img4.png)

![Imagen 25-5](images/clase_13_page25_img5.png)

Streaming y colas

Source mapping

![Imagen 26-1](images/clase_13_page26_img1.png)

![Imagen 26-2](images/clase_13_page26_img2.png)

![Imagen 26-3](images/clase_13_page26_img3.png)

![Imagen 26-4](images/clase_13_page26_img4.png)

Handler de una función Lambda en Python

![Imagen 27-1](images/clase_13_page27_img1.png)

![Imagen 27-2](images/clase_13_page27_img2.png)

![Imagen 27-3](images/clase_13_page27_img3.png)

Capas de funciones lambda

Sin capas Con capas

![Imagen 28-1](images/clase_13_page28_img1.png)

![Imagen 28-2](images/clase_13_page28_img2.png)

![Imagen 28-3](images/clase_13_page28_img3.png)

![Imagen 28-4](images/clase_13_page28_img4.png)

### Resumen

AWS Lambda es un servicio que permite ejecutar funciones de código sin crear ni administrar

servidores.

### Una función Lambda puede ejecutarse dentro de una VPC que pertenece al servicio de AWS

Lambda o como una Lambda@Edge en una cache regional de Amazon CloudFront.

Una función Lambda se puede configurar para que se conecte a una VPC y acceda a los

servicios que se ejecutan en ella.

Se puede llamar a una función Lambda de manera sincrónica, asincrónica, y mapeando fuentes

de eventos (para colas y streams).

### Las capas de Lambda permiten armar paquetes de dependencias o rutinas que pueden ser

reutilizadas por todas las funciones Lambda de la región.

![Imagen 29-1](images/clase_13_page29_img1.png)

![Imagen 29-2](images/clase_13_page29_img2.png)

![Imagen 29-3](images/clase_13_page29_img3.png)

Contenedores en AWS

![Imagen 30-1](images/clase_13_page30_img1.png)

![Imagen 30-2](images/clase_13_page30_img2.png)

![Imagen 30-3](images/clase_13_page30_img3.png)

Contenedores

### Casos de uso vs funciones lambda

Más de 15 minutos Aplicaciones que usan Costo Migración de

mucha memoria contenedores legacy

### AWS Lambda tiene un Las cargas de trabajo

### Los contenedores

Los contenedores

límite de 15 minutos de que exceden los 10 GB

pueden ejecutarse de

pueden ayudar a

duración para la de memoria no son

manera continua con

migrar aplicaciones

ejecución de apropiadas para

costo fijo.

legacy que se

funciones. funciones lambda.

ejecutan on-premises

El precio de una

o en instancias de EC2.

función lambda

aumenta con la

cantidad de

ejecuciones, la

duración y la memoria

utilizada.

![Imagen 31-1](images/clase_13_page31_img1.png)

![Imagen 31-2](images/clase_13_page31_img2.png)

![Imagen 31-3](images/clase_13_page31_img3.png)

![Imagen 31-4](images/clase_13_page31_img4.png)

![Imagen 31-5](images/clase_13_page31_img5.png)

![Imagen 31-6](images/clase_13_page31_img6.png)

![Imagen 31-7](images/clase_13_page31_img7.png)

Contenedores

Beneficios

Máquinas virtuales Contenedores

Container App 1 with App 2 with

package dependencies dependencies

Container engine

Host operating system (OS)

Host infrastructure

![Imagen 32-1](images/clase_13_page32_img1.png)

![Imagen 32-2](images/clase_13_page32_img2.png)

![Imagen 32-3](images/clase_13_page32_img3.png)

![Imagen 32-4](images/clase_13_page32_img4.png)

Contenedores

Casos de uso

Aplicaciones con

Procesamiento batch

microservicios

Escalar modelos de Estandarizar aplicaciones

machine learning (ML) de arquitectura híbrida

Migrar aplicaciones a la

nube

![Imagen 33-1](images/clase_13_page33_img1.png)

![Imagen 33-2](images/clase_13_page33_img2.png)

![Imagen 33-3](images/clase_13_page33_img3.png)

![Imagen 33-4](images/clase_13_page33_img4.png)

![Imagen 33-5](images/clase_13_page33_img5.png)

![Imagen 33-6](images/clase_13_page33_img6.png)

![Imagen 33-7](images/clase_13_page33_img7.png)

![Imagen 33-8](images/clase_13_page33_img8.png)

Contenedores

Docker containers

Container repository Container orchestration

Compute platform

Build Upload Pull

Dockerfile Container

Deployed containers

Container image

image

![Imagen 34-1](images/clase_13_page34_img1.png)

![Imagen 34-2](images/clase_13_page34_img2.png)

![Imagen 34-3](images/clase_13_page34_img3.png)

![Imagen 34-4](images/clase_13_page34_img4.png)

![Imagen 34-5](images/clase_13_page34_img5.png)

![Imagen 34-6](images/clase_13_page34_img6.png)

![Imagen 34-7](images/clase_13_page34_img7.png)

Servicios de contenedores en AWS

Registro Orquestación Cómputo

Amazon Elastic Compute Cloud

Amazon Elastic Container Amazon Elastic Container

(Amazon EC2)

Registry (Amazon ECR) Service (Amazon ECS)

AWS Fargate

Amazon Elastic Kubernetes

Service (Amazon EKS)

AWS Lambda

![Imagen 35-1](images/clase_13_page35_img1.png)

![Imagen 35-2](images/clase_13_page35_img2.png)

![Imagen 35-3](images/clase_13_page35_img3.png)

![Imagen 35-4](images/clase_13_page35_img4.png)

![Imagen 35-5](images/clase_13_page35_img5.png)

![Imagen 35-6](images/clase_13_page35_img6.png)

![Imagen 35-7](images/clase_13_page35_img7.png)

![Imagen 35-8](images/clase_13_page35_img8.png)

![Imagen 35-9](images/clase_13_page35_img9.png)

### Beneficios de AWS Fargate

### Sin gestión de Facturación por Escalamiento Adecuado para

clusters o servidores segundo automático equipos nuevos

No hay que Pago por uso Escalamiento No requiere

crear ni automático de conocimiento

mantener tareas según el profundo de la

servidores. uso de CPU, tecnología de

memoria u otras contenedores.

No necesitamos

métricas.

optimizar clusters.

![Imagen 36-1](images/clase_13_page36_img1.png)

![Imagen 36-2](images/clase_13_page36_img2.png)

![Imagen 36-3](images/clase_13_page36_img3.png)

![Imagen 36-4](images/clase_13_page36_img4.png)

![Imagen 36-5](images/clase_13_page36_img5.png)

![Imagen 36-6](images/clase_13_page36_img6.png)

![Imagen 36-7](images/clase_13_page36_img7.png)

Amazon ECS

Implementación y ejecución de contenedores

Amazon ECR Amazon ECS cluster

AWS Fargate

registry

Node 1

Front-end

Container 1 application

Task Task

definition 1 Node 2

Container 2

Container

image 1

Amazon EC2

Instance node

Application

Container 3 Load

Container Service

Task

Balancer

image 2

definition 2

Container 4

![Imagen 37-1](images/clase_13_page37_img1.png)

![Imagen 37-2](images/clase_13_page37_img2.png)

![Imagen 37-3](images/clase_13_page37_img3.png)

![Imagen 37-4](images/clase_13_page37_img4.png)

![Imagen 37-5](images/clase_13_page37_img5.png)

![Imagen 37-6](images/clase_13_page37_img6.png)

![Imagen 37-7](images/clase_13_page37_img7.png)

![Imagen 37-8](images/clase_13_page37_img8.png)

![Imagen 37-9](images/clase_13_page37_img9.png)

![Imagen 37-10](images/clase_13_page37_img10.png)

![Imagen 37-11](images/clase_13_page37_img11.png)

![Imagen 37-12](images/clase_13_page37_img12.png)

![Imagen 37-13](images/clase_13_page37_img13.png)

![Imagen 37-14](images/clase_13_page37_img14.png)

![Imagen 37-15](images/clase_13_page37_img15.png)

![Imagen 37-16](images/clase_13_page37_img16.png)

![Imagen 37-17](images/clase_13_page37_img17.png)

![Imagen 37-18](images/clase_13_page37_img18.png)

![Imagen 37-19](images/clase_13_page37_img19.png)

![Imagen 37-20](images/clase_13_page37_img20.png)

Amazon EKS

Implementación y ejecución de contenedores

Amazon Amazon EKS cluster

ECR registry

AWS Fargate

Node 1

Front-end

Pod 1 application

Container 1

Container PodSpec

image 1

Amazon EC2

Service

Application

Instance node 2

Load

Balancer

Pod 2

Container 2 Container 3

Container

Deployment and

image 2

ReplicaSet

![Imagen 38-1](images/clase_13_page38_img1.png)

![Imagen 38-2](images/clase_13_page38_img2.png)

![Imagen 38-3](images/clase_13_page38_img3.png)

![Imagen 38-4](images/clase_13_page38_img4.png)

![Imagen 38-5](images/clase_13_page38_img5.png)

![Imagen 38-6](images/clase_13_page38_img6.png)

![Imagen 38-7](images/clase_13_page38_img7.png)

![Imagen 38-8](images/clase_13_page38_img8.png)

![Imagen 38-9](images/clase_13_page38_img9.png)

![Imagen 38-10](images/clase_13_page38_img10.png)

![Imagen 38-11](images/clase_13_page38_img11.png)

![Imagen 38-12](images/clase_13_page38_img12.png)

![Imagen 38-13](images/clase_13_page38_img13.png)

![Imagen 38-14](images/clase_13_page38_img14.png)

![Imagen 38-15](images/clase_13_page38_img15.png)

![Imagen 38-16](images/clase_13_page38_img16.png)

![Imagen 38-17](images/clase_13_page38_img17.png)

![Imagen 38-18](images/clase_13_page38_img18.png)

Amazon EKS y Amazon ECS

Diferencias

### Tema Amazon ECS Amazon EKS

Simplifica la creación y el Provee mayor control sobre los

### Complejidad

mantenimiento de clusters clusters, pero la interfaz es compleja

Configuración manual de los grupos de

Escalamiento Escalamiento automático a demanda

autoescalamiento

### Herramientas Amazon ECS Kubernetes

### Experiencia del Nuevo en la arquitectura de Familiarizado con la arquitectura y los

equipo contenedores procesos de control de Kubernetes

![Imagen 39-1](images/clase_13_page39_img1.png)

![Imagen 39-2](images/clase_13_page39_img2.png)

![Imagen 39-3](images/clase_13_page39_img3.png)

Contenedores

### Resumen

### Los contenedores son una mejor solución que las funciones Lambda cuando

la aplicación requiere recursos que exceden los límites de servicio de AWS

### Lambda

Amazon ECR proporciona un servicio de repositorio de imágenes de

contenedores.

Amazon ECS es un servicio de orquestación de contenedores con

herramientas propias de AWS.

Amazon EKS es un servicio de orquestación de contenedores con

herramientas de Kubernetes.

AWS Fargate administra nodos serverless y se puede implementar en clusters

de Amazon ECS o Amazon EKS.

![Imagen 40-1](images/clase_13_page40_img1.png)

![Imagen 40-2](images/clase_13_page40_img2.png)

![Imagen 40-3](images/clase_13_page40_img3.png)

AWS Step Functions

![Imagen 41-1](images/clase_13_page41_img1.png)

![Imagen 41-2](images/clase_13_page41_img2.png)

![Imagen 41-3](images/clase_13_page41_img3.png)

Microservicios

Desafíos

### Dependencias Escenarios de error Coordinación

Administrar las Ejecutar reintentos luego Escalar la aplicación

dependencias entre de errores o timeouts

Mantener el estado de

microservicios

microservicios stateless

Encadenar los

Pasar datos entre

microservicios en

microservicios

secuencia o en paralelo

Monitoreo y resolución de

problemas

![Imagen 42-1](images/clase_13_page42_img1.png)

![Imagen 42-2](images/clase_13_page42_img2.png)

![Imagen 42-3](images/clase_13_page42_img3.png)

![Imagen 42-4](images/clase_13_page42_img4.png)

![Imagen 42-5](images/clase_13_page42_img5.png)

![Imagen 42-6](images/clase_13_page42_img6.png)

### AWS Step Functions

Servicio de orquestación serverless que maneja flujos

entre distintos servicios de AWS

### Tiene máquinas de estado (workflows) que contienen

una serie de estados dependientes de eventos (pasos)

Gestiona el estado, los checkpoints y los reinicios de

Step

cada workflow

Functions

Tiene funciones para el tratamiento de errores

### Puede transferir datos entre estados

Los estados pueden filtrar y manipular datos

![Imagen 43-1](images/clase_13_page43_img1.png)

![Imagen 43-2](images/clase_13_page43_img2.png)

![Imagen 43-3](images/clase_13_page43_img3.png)

![Imagen 43-4](images/clase_13_page43_img4.png)

Flujos estándar o exprés

Criterio Standard Workflows Express Workflows

### Duración Larga Breve, sin actividades

Métricas Historia completa en la consola Resultados en logs de CloudWatch

Procesamiento Asincrónico Sincrónico o asincrónico

Sincrónico: al menos una vez

Modelo de

Exactamente una vez

ejecución

Asincrónico: Como máximo, una vez

Progreso de la Sin persistencia del estado en cada

Se persiste en cada transición de estado

máquina de estado transición de estado

Por cantidad y duración de llamadas

Precios Por cantidad de transiciones de estado

por workflow

![Imagen 44-1](images/clase_13_page44_img1.png)

![Imagen 44-2](images/clase_13_page44_img2.png)

![Imagen 44-3](images/clase_13_page44_img3.png)

Step Functions

### Casos de uso

Orquestar Procesamiento Machine learning Automatización

microservicios de datos (ML) de seguridad

![Imagen 45-1](images/clase_13_page45_img1.png)

![Imagen 45-2](images/clase_13_page45_img2.png)

![Imagen 45-3](images/clase_13_page45_img3.png)

![Imagen 45-4](images/clase_13_page45_img4.png)

![Imagen 45-5](images/clase_13_page45_img5.png)

![Imagen 45-6](images/clase_13_page45_img6.png)

![Imagen 45-7](images/clase_13_page45_img7.png)

Coordinación de estados

Task A

Task A Task B Task A

try{…}

Task B catch{…}

finally{…}

Task C Task C

### Gestión de errores

Ejecución secuencial Ejecución en paralelo (try-catch-finally)

Task A Task A Task A

Task A Task A

Task B Task B Task B

Reiteración de tareas

Task B ? Task C

fallidas

Task C Task C Task C

Elegir tarea según los

Procesar tareas sobre registros

datos

de datos en paralelo

![Imagen 46-1](images/clase_13_page46_img1.png)

![Imagen 46-2](images/clase_13_page46_img2.png)

![Imagen 46-3](images/clase_13_page46_img3.png)

### Tipos de estado

### Estados de trabajo Estados de transición Estados de detención

### Task: se integra con Choice: Agrega Success: Detiene la

servicios de AWS condiciones para ejecución y la marca

controlar el flujo hacia el como exitosa

Activity: Realiza una tarea

estado siguiente

en cualquier lugar Fail: Detiene la ejecución y

Parallel: Agrega ramas de la marca como fallida

Pass: Pasa o filtra datos

máquinas de estado

de entrada al estado End parameter: Detiene la

anidadas en una

siguiente ejecución

máquina de estado

Wait: Demora el flujo por

Map: Separa el flujo de

un período especificado

cada registro de datos en

State has wait for

ejecuciones de data sets

callback state option:

que corren en paralelo

Pausa el flujo y espera el

retorno

![Imagen 47-1](images/clase_13_page47_img1.png)

![Imagen 47-2](images/clase_13_page47_img2.png)

![Imagen 47-3](images/clase_13_page47_img3.png)

Ejemplo

Start

Wait for callback token

Recommend stock trade Request human approval

No

Any stock to trade?

Yes

Email to approver

Yes

Human approval required?

Approve or deny

No callback

Yes No

Trade stock transaction Trade approved?

No

Was transaction successful?

### Yes

No recommendations Trade successful Trade unsuccessful Trade not approved

En

d

![Imagen 48-1](images/clase_13_page48_img1.png)

![Imagen 48-2](images/clase_13_page48_img2.png)

![Imagen 48-3](images/clase_13_page48_img3.png)

![Imagen 48-4](images/clase_13_page48_img4.png)

![Imagen 48-5](images/clase_13_page48_img5.png)

![Imagen 48-6](images/clase_13_page48_img6.png)

![Imagen 48-7](images/clase_13_page48_img7.png)

![Imagen 48-8](images/clase_13_page48_img8.png)

![Imagen 48-9](images/clase_13_page48_img9.png)

![Imagen 48-10](images/clase_13_page48_img10.png)

![Imagen 48-11](images/clase_13_page48_img11.png)

![Imagen 48-12](images/clase_13_page48_img12.png)

![Imagen 48-13](images/clase_13_page48_img13.png)

![Imagen 48-14](images/clase_13_page48_img14.png)

![Imagen 48-15](images/clase_13_page48_img15.png)

![Imagen 48-16](images/clase_13_page48_img16.png)

![Imagen 48-17](images/clase_13_page48_img17.png)

### Resumen

AWS Step Functions es un servicio de orquestación serverless que

maneja flujos entre múltiples servicios de AWS.

Una máquina de estados (workflow) es una serie de estados (pasos)

manejados por eventos.

Una máquina de estado de Step Functions es una colección de

estados definidos en el Amazon States Language.

Los estados se pueden agrupar en tres categorías: trabajo,

transición y detención.

### El estado de una tarea puede llamar a un servicio de AWS o

generar una solicitud a una actividad en cualquier servicio que

tenga una conexión HTTP.

![Imagen 49-1](images/clase_13_page49_img1.png)

![Imagen 49-2](images/clase_13_page49_img2.png)

![Imagen 49-3](images/clase_13_page49_img3.png)

Amazon API Gateway

![Imagen 50-1](images/clase_13_page50_img1.png)

![Imagen 50-2](images/clase_13_page50_img2.png)

![Imagen 50-3](images/clase_13_page50_img3.png)

### Ventajas de las API

Estandarizar la Proteger los microservicios Monetizar las API y

comunicación entre apps

registrar estadísticas

### Estandarizar la conexión Decidir cuándo requerir Registrar el acceso de

entre aplicaciones autorización clientes para gestionar la

desarrolladas en distintos facturación

Verificar los formatos de las

lenguajes

solicitudes. Generar estadísticas de uso

Ocultar la complejidad de por cliente

Manejar la cantidad de

la implementación

solicitudes.

Restringir el acceso a

recursos

![Imagen 51-1](images/clase_13_page51_img1.png)

![Imagen 51-2](images/clase_13_page51_img2.png)

![Imagen 51-3](images/clase_13_page51_img3.png)

![Imagen 51-4](images/clase_13_page51_img4.png)

![Imagen 51-5](images/clase_13_page51_img5.png)

![Imagen 51-6](images/clase_13_page51_img6.png)

### API Gateway

Permite crear, publicar y mantener APIs de tipo REST,

### HTTP, y WebSocket

Gestión de tráfico, autorización y control de acceso a

recursos configurables

Brinda acceso a servicios de AWS y a endpoints de

acceso público

## API

Mantiene múltiples versiones de una API de

Gateway

aplicación

Establece planes de uso por cliente para monetizar y

controlar el uso de las APIs

Puede mantener un cache de respuestas comunes

![Imagen 52-1](images/clase_13_page52_img1.png)

![Imagen 52-2](images/clase_13_page52_img2.png)

![Imagen 52-3](images/clase_13_page52_img3.png)

![Imagen 52-4](images/clase_13_page52_img4.png)

Tipos de API

### REST APIs HTTP APIs WebSocket APIs

Colección de rutas y Colección de rutas y Colección de rutas de

métodos métodos WebSocket

Para aplicaciones que Para microservicios Para aplicaciones en

requieren funciones de tiempo real

Menor latencia y menor

administración de API

costo que las API REST Establece una sesión entre

Permite cross-origin el cliente y los servicios de

Soporta CORS

resource sharing (CORS) backend

Stateless

Stateless Stateful

![Imagen 53-1](images/clase_13_page53_img1.png)

![Imagen 53-2](images/clase_13_page53_img2.png)

![Imagen 53-3](images/clase_13_page53_img3.png)

API Gateway

Integración con backend

VPC link using

Region

Customer VPC

REST or HTTP API

Amazon Cognito Lambda function

Network Load Balancer

Application Load Balancer

Publicly

VPC links using

routable Amazon API Gateway

## HTTP API

## HTTP

AWS service

endpoint

First-class HTTP API integrations

Amazon Amazon

Amazon SQS Amazon Kinesis AWS Step

EventBridge DynamoDB

queue Data Streams Functions

event table

state machine

![Imagen 54-1](images/clase_13_page54_img1.png)

![Imagen 54-2](images/clase_13_page54_img2.png)

![Imagen 54-3](images/clase_13_page54_img3.png)

![Imagen 54-4](images/clase_13_page54_img4.png)

![Imagen 54-5](images/clase_13_page54_img5.png)

![Imagen 54-6](images/clase_13_page54_img6.png)

![Imagen 54-7](images/clase_13_page54_img7.png)

![Imagen 54-8](images/clase_13_page54_img8.png)

![Imagen 54-9](images/clase_13_page54_img9.png)

![Imagen 54-10](images/clase_13_page54_img10.png)

![Imagen 54-11](images/clase_13_page54_img11.png)

![Imagen 54-12](images/clase_13_page54_img12.png)

![Imagen 54-13](images/clase_13_page54_img13.png)

![Imagen 54-14](images/clase_13_page54_img14.png)

![Imagen 54-15](images/clase_13_page54_img15.png)

![Imagen 54-16](images/clase_13_page54_img16.png)

![Imagen 54-17](images/clase_13_page54_img17.png)

![Imagen 54-18](images/clase_13_page54_img18.png)

![Imagen 54-19](images/clase_13_page54_img19.png)

![Imagen 54-20](images/clase_13_page54_img20.png)

![Imagen 54-21](images/clase_13_page54_img21.png)

![Imagen 54-22](images/clase_13_page54_img22.png)

### Actividad. API Gateway

### Descomponer una aplicación monolítica en microservicios

Aplicación monolítica Aplicaciones basadas en servicios

Shopping

Shopping cart service

cart

Payment Payment service

Delivery Delivery service

![Imagen 55-1](images/clase_13_page55_img1.png)

![Imagen 55-2](images/clase_13_page55_img2.png)

![Imagen 55-3](images/clase_13_page55_img3.png)

![Imagen 55-4](images/clase_13_page55_img4.png)

![Imagen 55-5](images/clase_13_page55_img5.png)

![Imagen 55-6](images/clase_13_page55_img6.png)

![Imagen 55-7](images/clase_13_page55_img7.png)

![Imagen 55-8](images/clase_13_page55_img8.png)

![Imagen 55-9](images/clase_13_page55_img9.png)

Solución: microservicio carrito

Amazon API Lambda shopping Amazon DynamoDB

Gateway shopping cart function shopping cart table

website HTTP API

![Imagen 56-1](images/clase_13_page56_img1.png)

![Imagen 56-2](images/clase_13_page56_img2.png)

![Imagen 56-3](images/clase_13_page56_img3.png)

![Imagen 56-4](images/clase_13_page56_img4.png)

![Imagen 56-5](images/clase_13_page56_img5.png)

![Imagen 56-6](images/clase_13_page56_img6.png)

Solución: microservicio de pago

Customer VPC

EC2 instance

nodes

Application Load ECS Payment Banking API

Amazon API

Balancer containers

Gateway shopping

website HTTP API

DynamoDB payment table

![Imagen 57-1](images/clase_13_page57_img1.png)

![Imagen 57-2](images/clase_13_page57_img2.png)

![Imagen 57-3](images/clase_13_page57_img3.png)

![Imagen 57-4](images/clase_13_page57_img4.png)

![Imagen 57-5](images/clase_13_page57_img5.png)

![Imagen 57-6](images/clase_13_page57_img6.png)

![Imagen 57-7](images/clase_13_page57_img7.png)

![Imagen 57-8](images/clase_13_page57_img8.png)

![Imagen 57-9](images/clase_13_page57_img9.png)

![Imagen 57-10](images/clase_13_page57_img10.png)

### Solución: microservicio de circuito de distribución

AWS Step Functions Standard Workflow delivery state machine

### Start

Amazon API Request order delivery and wait for callback

Gateway HTTP API

No

Order delivered? Mark order as cancelled

Yes

Mark order as delivered Send delivery cancelled

Send delivery confirmation Request payment refund

Inventory and Delivery

application

Delivery successful Delivery unsuccessful

Callback

End

![Imagen 58-1](images/clase_13_page58_img1.png)

![Imagen 58-2](images/clase_13_page58_img2.png)

![Imagen 58-3](images/clase_13_page58_img3.png)

![Imagen 58-4](images/clase_13_page58_img4.png)

![Imagen 58-5](images/clase_13_page58_img5.png)

![Imagen 58-6](images/clase_13_page58_img6.png)

![Imagen 58-7](images/clase_13_page58_img7.png)

![Imagen 58-8](images/clase_13_page58_img8.png)

![Imagen 58-9](images/clase_13_page58_img9.png)

![Imagen 58-10](images/clase_13_page58_img10.png)

![Imagen 58-11](images/clase_13_page58_img11.png)

![Imagen 58-12](images/clase_13_page58_img12.png)

![Imagen 58-13](images/clase_13_page58_img13.png)

![Imagen 58-14](images/clase_13_page58_img14.png)

![Imagen 58-15](images/clase_13_page58_img15.png)

### Resumen

### Amazon API Gateway permite crear, publicar y mantener APIs de aplicación

Proporciona acceso a servicios de AWS y a endpoints de acceso público.

Las API REST se usan cuando se requiere control y administración total de las

APIs.

Las APIs HTTP se usa cuando la prioridad es lograr una menor latencia y menor

costo.

Las APIs WebSocket se usan para aplicaciones en tiempo real que requieren

una sesión activa.

![Imagen 59-1](images/clase_13_page59_img1.png)

![Imagen 59-2](images/clase_13_page59_img2.png)

![Imagen 59-3](images/clase_13_page59_img3.png)

AWS Well-Architected Framework

![Imagen 60-1](images/clase_13_page60_img1.png)

![Imagen 60-2](images/clase_13_page60_img2.png)

![Imagen 60-3](images/clase_13_page60_img3.png)

AWS Well-Architected

Serverless Applications

![Imagen 61-1](images/clase_13_page61_img1.png)

![Imagen 61-2](images/clase_13_page61_img2.png)

![Imagen 61-3](images/clase_13_page61_img3.png)

![Imagen 61-4](images/clase_13_page61_img4.png)

![Imagen 61-5](images/clase_13_page61_img5.png)

![Imagen 61-6](images/clase_13_page61_img6.png)

![Imagen 61-7](images/clase_13_page61_img7.png)

Buena práctica: gestión de fallas

Buena práctica

Usar mecanismos DLQ para retener,

investigar y volver a ejecutar

transacciones fallidas.

Ejecutar un roll back de las transacciones

fallidas.

![Imagen 62-1](images/clase_13_page62_img1.png)

![Imagen 62-2](images/clase_13_page62_img2.png)

![Imagen 62-3](images/clase_13_page62_img3.png)

![Imagen 62-4](images/clase_13_page62_img4.png)

Buena práctica: IAM

Buena práctica

Controlar el acceso a las API

Controlar el acceso a la aplicación

serverless

![Imagen 63-1](images/clase_13_page63_img1.png)

![Imagen 63-2](images/clase_13_page63_img2.png)

![Imagen 63-3](images/clase_13_page63_img3.png)

![Imagen 63-4](images/clase_13_page63_img4.png)

Buena práctica: Protección de datos

Buena práctica

Cifrar los datos en tránsito y en reposo

Implementar seguridad de aplicaciones

en las cargas de trabajo

![Imagen 64-1](images/clase_13_page64_img1.png)

![Imagen 64-2](images/clase_13_page64_img2.png)

![Imagen 64-3](images/clase_13_page64_img3.png)

![Imagen 64-4](images/clase_13_page64_img4.png)

Buena práctica: Selección

Buena práctica

Optimizar el rendimiento de la

aplicación

![Imagen 65-1](images/clase_13_page65_img1.png)

![Imagen 65-2](images/clase_13_page65_img2.png)

![Imagen 65-3](images/clase_13_page65_img3.png)

![Imagen 65-4](images/clase_13_page65_img4.png)

Buena práctica: Costos de recursos

Buena práctica

Optimizar el costo de la aplicación

Usar integraciones de AWS

![Imagen 66-1](images/clase_13_page66_img1.png)

![Imagen 66-2](images/clase_13_page66_img2.png)

![Imagen 66-3](images/clase_13_page66_img3.png)

![Imagen 66-4](images/clase_13_page66_img4.png)

### Resumen

Usar mecanismos DLQ para retener, investigar y volver a ejecutar

transacciones fallidas.

Ejecutar roll back de transacciones fallidas.

Controlar el acceso a las API serverless.

Controlar el acceso a la aplicación serverless.

Cifrar los datos en tránsito y en reposo.

Implementar seguridad de aplicaciones en las cargas de trabajo.

Optimizar la performance de las aplicaciones serverless.

Optimizar el costo de aplicación.

Cuando estén disponibles, usar integraciones directas de AWS.

![Imagen 67-1](images/clase_13_page67_img1.png)

![Imagen 67-2](images/clase_13_page67_img2.png)

![Imagen 67-3](images/clase_13_page67_img3.png)

Módulo 14

### Pregunta de práctica

### What is the most effective use of Amazon Elastic Container Service (Amazon ECS) when refactoring a

monolithic application to use a microservice architecture?

Identifiquemos las palabras o frases clave:

The following are the key words and phrases:

- Amazon ECS

- refactoring a monolith

- microservice architecture

![Imagen 68-1](images/clase_13_page68_img1.png)

![Imagen 68-2](images/clase_13_page68_img2.png)

![Imagen 68-3](images/clase_13_page68_img3.png)

Módulo 14

### Pregunta de práctica

### What is the most effective use of Amazon Elastic Container Service (Amazon ECS) when refactoring a

monolithic application to use a microservice architecture?

### Choice Response

Create services that each provide a distinct function of the application, and run multiple services in a single container that

## A

Amazon ECS manages.

B Port the application to a new image, and run it in a container that Amazon ECS manages.

C Refactor the application and centralize common functions to create a smaller code footprint.

Create services that each provide a distinct function of the application, and run each service in a separate container that

## D

Amazon ECS manages.

![Imagen 69-1](images/clase_13_page69_img1.png)

![Imagen 69-2](images/clase_13_page69_img2.png)

![Imagen 69-3](images/clase_13_page69_img3.png)

Módulo 14

### Pregunta de práctica

### What is the most effective use of Amazon Elastic Container Service (Amazon ECS) when refactoring a

monolithic application to use a microservice architecture?

### Choice Response

Create services that each provide a distinct function of the application, and run each service in a separate container that

## D

Amazon ECS manages.

![Imagen 70-1](images/clase_13_page70_img1.png)

![Imagen 70-2](images/clase_13_page70_img2.png)

![Imagen 70-3](images/clase_13_page70_img3.png)

Muchas gracias.

www.austral.edu.ar

![Imagen 71-1](images/clase_13_page71_img1.png)

![Imagen 71-2](images/clase_13_page71_img2.png)

![Imagen 71-3](images/clase_13_page71_img3.png)
