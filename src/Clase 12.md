# Arquitecturas desacopladas

> Esta clase abarca el módulo 13 del curso de AWS Cloud Architecting

![Imagen 2-1](images/clase_12_page2_img1.png)

![Imagen 2-2](images/clase_12_page2_img2.png)

![Imagen 2-3](images/clase_12_page2_img3.png)

### Objetivos

- Distinguir arquitecturas con alto y bajo acoplamiento.

- Comprender el funcionamiento y los casos de uso de Amazon

Simple Queue Service (Amazon SQS).

- Comprender el funcionamiento e identificar cuándo usar Amazon

Notification Service (Amazon SNS).

- Describir Amazon MQ.

- Desacoplar cargas de trabajo con Amazon SQS.

![Imagen 3-1](images/clase_12_page3_img1.png)

![Imagen 3-2](images/clase_12_page3_img2.png)

![Imagen 3-3](images/clase_12_page3_img3.png)

Objetivos

### De un arquitecto de nube

- Identificar cuellos de botella potenciales para que la

arquitectura escale en la medida que aumenta el tráfico.

- Limitar el impacto de las fallas para que las fallas de los

componentes no produzcan la caída de la aplicación.

- Implementar arquitecturas que permitan aplicar cambios a

un componente sin afectar a los demás, para minimizar las

bajas por mantenimiento.

![Imagen 4-1](images/clase_12_page4_img1.png)

![Imagen 4-2](images/clase_12_page4_img2.png)

![Imagen 4-3](images/clase_12_page4_img3.png)

Acoplamiento

![Imagen 5-1](images/clase_12_page5_img1.png)

![Imagen 5-2](images/clase_12_page5_img2.png)

![Imagen 5-3](images/clase_12_page5_img3.png)

Acoplamiento fuerte en arquitecturas de tres capas

Comunicación directa entre el

Comunicación sincrónica (enviar o

servidor web y el servidor de

esperar respuestas).

aplicación.

Web client Web server on Application server Database on

Amazon EC2 on Amazon EC2 Amazon RDS

Desafío: si falla el servidor de aplicación,

deja de funcionar la infraestructura.

Desafío: reducir la escala requiere

actualizar el código.

Application server

on Amazon EC2

![Imagen 6-1](images/clase_12_page6_img1.png)

![Imagen 6-2](images/clase_12_page6_img2.png)

![Imagen 6-3](images/clase_12_page6_img3.png)

![Imagen 6-4](images/clase_12_page6_img4.png)

![Imagen 6-5](images/clase_12_page6_img5.png)

![Imagen 6-6](images/clase_12_page6_img6.png)

![Imagen 6-7](images/clase_12_page6_img7.png)

![Imagen 6-8](images/clase_12_page6_img8.png)

![Imagen 6-9](images/clase_12_page6_img9.png)

![Imagen 6-10](images/clase_12_page6_img10.png)

![Imagen 6-11](images/clase_12_page6_img11.png)

![Imagen 6-12](images/clase_12_page6_img12.png)

![Imagen 6-13](images/clase_12_page6_img13.png)

![Imagen 6-14](images/clase_12_page6_img14.png)

![Imagen 6-15](images/clase_12_page6_img15.png)

![Imagen 6-16](images/clase_12_page6_img16.png)

![Imagen 6-17](images/clase_12_page6_img17.png)

![Imagen 6-18](images/clase_12_page6_img18.png)

![Imagen 6-19](images/clase_12_page6_img19.png)

![Imagen 6-20](images/clase_12_page6_img20.png)

### El acoplamiento dificulta el escalamiento

Una caída de la aplicación tiene impacto en todos los web servers.

Web tier Application tier Database tier

Web server Application server

instance 1 instance 1

Web client Web server

Database on

Route 53

instance 2

Amazon RDS

instance

Web server

Application server

instance 3

instance 2

Cada nuevo servidor requiere múltiples conexiones que deben ser actualizadas en el

código.

![Imagen 7-1](images/clase_12_page7_img1.png)

![Imagen 7-2](images/clase_12_page7_img2.png)

![Imagen 7-3](images/clase_12_page7_img3.png)

![Imagen 7-4](images/clase_12_page7_img4.png)

![Imagen 7-5](images/clase_12_page7_img5.png)

![Imagen 7-6](images/clase_12_page7_img6.png)

![Imagen 7-7](images/clase_12_page7_img7.png)

![Imagen 7-8](images/clase_12_page7_img8.png)

![Imagen 7-9](images/clase_12_page7_img9.png)

![Imagen 7-10](images/clase_12_page7_img10.png)

![Imagen 7-11](images/clase_12_page7_img11.png)

![Imagen 7-12](images/clase_12_page7_img12.png)

![Imagen 7-13](images/clase_12_page7_img13.png)

![Imagen 7-14](images/clase_12_page7_img14.png)

![Imagen 7-15](images/clase_12_page7_img15.png)

Acoplamiento débil

Manejo y ruteo automático de cargas

Web tier Application tier Database tier

de trabajo.

Web server

instance 1

Application server

1 2

instance 1

Web server

instance 2

Web client

Database on

Route 53 Application Load Application Load

Amazon RDS

Balancer 1 Balancer 2

instance

## (ALB1) (ALB2)

Web server

instance 3

Application server

instance 2

Agregar un nuevo servidor web

New web server

requiere solo dos conexiones.

instance

![Imagen 8-1](images/clase_12_page8_img1.png)

![Imagen 8-2](images/clase_12_page8_img2.png)

![Imagen 8-3](images/clase_12_page8_img3.png)

![Imagen 8-4](images/clase_12_page8_img4.png)

![Imagen 8-5](images/clase_12_page8_img5.png)

![Imagen 8-6](images/clase_12_page8_img6.png)

![Imagen 8-7](images/clase_12_page8_img7.png)

![Imagen 8-8](images/clase_12_page8_img8.png)

![Imagen 8-9](images/clase_12_page8_img9.png)

![Imagen 8-10](images/clase_12_page8_img10.png)

![Imagen 8-11](images/clase_12_page8_img11.png)

![Imagen 8-12](images/clase_12_page8_img12.png)

![Imagen 8-13](images/clase_12_page8_img13.png)

![Imagen 8-14](images/clase_12_page8_img14.png)

![Imagen 8-15](images/clase_12_page8_img15.png)

![Imagen 8-16](images/clase_12_page8_img16.png)

![Imagen 8-17](images/clase_12_page8_img17.png)

![Imagen 8-18](images/clase_12_page8_img18.png)

![Imagen 8-19](images/clase_12_page8_img19.png)

![Imagen 8-20](images/clase_12_page8_img20.png)

![Imagen 8-21](images/clase_12_page8_img21.png)

Acoplamiento fuerte dentro de una aplicación

Web tier Application tier Database tier

Application server instance

Web application

Procesar transacciones

financieras.

Web server

instance 1

Tratar imágenes.

Database on

Application Load

Amazon RDS

Balancer 2

instance

Web server (ALB2)

Realizar cálculos.

instance 2

Desafío: la falla de una función afecta a toda la aplicación.

![Imagen 9-1](images/clase_12_page9_img1.png)

![Imagen 9-2](images/clase_12_page9_img2.png)

![Imagen 9-3](images/clase_12_page9_img3.png)

![Imagen 9-4](images/clase_12_page9_img4.png)

![Imagen 9-5](images/clase_12_page9_img5.png)

![Imagen 9-6](images/clase_12_page9_img6.png)

![Imagen 9-7](images/clase_12_page9_img7.png)

![Imagen 9-8](images/clase_12_page9_img8.png)

![Imagen 9-9](images/clase_12_page9_img9.png)

![Imagen 9-10](images/clase_12_page9_img10.png)

Acoplamiento débil: microservicios

Web tier Application tier Database tier

Application server

instance 1

Microservicio

financiero

Application server

Microservicio de

instance 3

Web server transcoding

Microservicio

instance 1

Database on

financiero

Amazon RDS

Microservicio de instance

Application Load

Application server cálculo

Balancer 2

instance 2

Web server (ALB2)

Microservicio

Microservicio de

instance 2

financiero

cálculo

Microservicio de

transcoding

![Imagen 10-1](images/clase_12_page10_img1.png)

![Imagen 10-2](images/clase_12_page10_img2.png)

![Imagen 10-3](images/clase_12_page10_img3.png)

![Imagen 10-4](images/clase_12_page10_img4.png)

![Imagen 10-5](images/clase_12_page10_img5.png)

![Imagen 10-6](images/clase_12_page10_img6.png)

![Imagen 10-7](images/clase_12_page10_img7.png)

![Imagen 10-8](images/clase_12_page10_img8.png)

![Imagen 10-9](images/clase_12_page10_img9.png)

![Imagen 10-10](images/clase_12_page10_img10.png)

SQS y SNS

Application tier

2

Application server

1

instance 1

Microservicio

SQS queue

Transcoding

financiero

consumer app

Application server

server instance

Microservicio

instance 3

Transcoding

Microservicio

financiero

Microservicio de

Application Load

Application server cálculo

Balancer 2 SNS topic

instance 2

## (ALB2)

Microservicio

Microservicio de

financiero

cálculo

Microservicio Email

3

Transcoding notification

![Imagen 11-1](images/clase_12_page11_img1.png)

![Imagen 11-2](images/clase_12_page11_img2.png)

![Imagen 11-3](images/clase_12_page11_img3.png)

![Imagen 11-4](images/clase_12_page11_img4.png)

![Imagen 11-5](images/clase_12_page11_img5.png)

![Imagen 11-6](images/clase_12_page11_img6.png)

![Imagen 11-7](images/clase_12_page11_img7.png)

![Imagen 11-8](images/clase_12_page11_img8.png)

![Imagen 11-9](images/clase_12_page11_img9.png)

![Imagen 11-10](images/clase_12_page11_img10.png)

![Imagen 11-11](images/clase_12_page11_img11.png)

![Imagen 11-12](images/clase_12_page11_img12.png)

![Imagen 11-13](images/clase_12_page11_img13.png)

![Imagen 11-14](images/clase_12_page11_img14.png)

Amazon MQ

AWS Cloud

Corporate

data center

Image producer

Amazon MQ

Transcoding

application server

broker

consumer application

server instance

Amazon EFS

![Imagen 12-1](images/clase_12_page12_img1.png)

![Imagen 12-2](images/clase_12_page12_img2.png)

![Imagen 12-3](images/clase_12_page12_img3.png)

![Imagen 12-4](images/clase_12_page12_img4.png)

![Imagen 12-5](images/clase_12_page12_img5.png)

![Imagen 12-6](images/clase_12_page12_img6.png)

![Imagen 12-7](images/clase_12_page12_img7.png)

![Imagen 12-8](images/clase_12_page12_img8.png)

![Imagen 12-9](images/clase_12_page12_img9.png)

### Amazon MQ

El acoplamiento débil resuelve problemas de integración y se puede lograr

mediante soluciones sincrónicas y asincrónicas.

Synchronous

### Asynchronous

Infrastructure level Application level Queue based Topic based

ELB Amazon SQS Amazon MQ Amazon SNS

Arquitectura de

microservicios

![Imagen 13-1](images/clase_12_page13_img1.png)

![Imagen 13-2](images/clase_12_page13_img2.png)

![Imagen 13-3](images/clase_12_page13_img3.png)

![Imagen 13-4](images/clase_12_page13_img4.png)

![Imagen 13-5](images/clase_12_page13_img5.png)

![Imagen 13-6](images/clase_12_page13_img6.png)

![Imagen 13-7](images/clase_12_page13_img7.png)

![Imagen 13-8](images/clase_12_page13_img8.png)

### Resumen

### Los sistemas fuertemente acoplados son difíciles de escalar, e

introducen puntos únicos de falla y cuellos de botella.

### Una arquitectura débilmente acoplada elimina las dependencias

directas entre componentes relacionados y brinda escalabilidad y

resiliencia.

### Las soluciones débilmente acopladas dividen las capas de la

infraestructura o las funciones de la aplicación. Típicamente,

introducen un componente intermedio entre ellas.

Las soluciones débilmente acopladas pueden ser sincrónicas o

asincrónicas:

### ELB es un ejemplo de solución sincrónica

Amazon SQS, Amazon SNS, y Amazon MQ son ejemplos de soluciones

asincrónicas.

![Imagen 14-1](images/clase_12_page14_img1.png)

![Imagen 14-2](images/clase_12_page14_img2.png)

![Imagen 14-3](images/clase_12_page14_img3.png)

Amazon SQS

![Imagen 15-1](images/clase_12_page15_img1.png)

![Imagen 15-2](images/clase_12_page15_img2.png)

![Imagen 15-3](images/clase_12_page15_img3.png)

### Amazon SQS

Se pueden desacoplar las aplicaciones de manera asincrónica, mediante

mensajería punto a punto.

Una aplicación (“productora”) envía un mensaje a una única aplicación receptora

(“consumidora”).

Se utiliza una cola de mensajes para desacoplar las aplicaciones.

Pull mechanism

Message

Put message Get message

Producer Consumer

Message queue

![Imagen 16-1](images/clase_12_page16_img1.png)

![Imagen 16-2](images/clase_12_page16_img2.png)

![Imagen 16-3](images/clase_12_page16_img3.png)

![Imagen 16-4](images/clase_12_page16_img4.png)

![Imagen 16-5](images/clase_12_page16_img5.png)

![Imagen 16-6](images/clase_12_page16_img6.png)

![Imagen 16-7](images/clase_12_page16_img7.png)

![Imagen 16-8](images/clase_12_page16_img8.png)

![Imagen 16-9](images/clase_12_page16_img9.png)

![Imagen 16-10](images/clase_12_page16_img10.png)

Amazon SQS

Servicio de colas de mensajería administrado por

## AWS

Ayuda a integrar y desacoplar sistemas de software

distribuidos y componentes de aplicación.

Brinda funciones de colas de mensajería de alta

disponibilidad, seguras y durables.

Tiene una consola de administración (AWS

Amazon

Management Console) y una API de web services

## SQS

![Imagen 17-1](images/clase_12_page17_img1.png)

![Imagen 17-2](images/clase_12_page17_img2.png)

![Imagen 17-3](images/clase_12_page17_img3.png)

![Imagen 17-4](images/clase_12_page17_img4.png)

Amazon SQS

Características y beneficios

Administrado Confiabilidad Seguridad Escalabilidad

No Envía grandes Envío seguro Escalamiento

necesitamos

cantidades de de datos elástico

administrar la

datos sin sensibles entre basado en el

infraestructura

pérdida de aplicaciones. uso.

ni el software

mensajes.

de mensajería.

![Imagen 18-1](images/clase_12_page18_img1.png)

![Imagen 18-2](images/clase_12_page18_img2.png)

![Imagen 18-3](images/clase_12_page18_img3.png)

Amazon SQS

Componentes

Longitud máxima: 256 KB.

Se mantiene en la cola hasta que es borrado explícitamente, o supera el

tiempo de retención de la cola.

### Mensaje

### Amazon SQS ofrece dos tipos de cola: estándar y first-in-first-out (FIFO)

Los parámetros de la cola se pueden configurar. Por ejemplo:

- Período de retención de mensajes

### Cola

- Timeout de visibilidad

- Tiempo de espera de recepción de mensajes (short polling vs. long polling)

Se puede asociar una DLQ (dead-letter queue) a cualquier cola.

Una DLQ almacena mensajes que no pudieron ser consumidos con

éxito.

## DLQ

![Imagen 19-1](images/clase_12_page19_img1.png)

![Imagen 19-2](images/clase_12_page19_img2.png)

![Imagen 19-3](images/clase_12_page19_img3.png)

![Imagen 19-4](images/clase_12_page19_img4.png)

![Imagen 19-5](images/clase_12_page19_img5.png)

![Imagen 19-6](images/clase_12_page19_img6.png)

Amazon SQS

### Ejemplo de desacoplamiento

Producer application tier Consumer application tier

Instance 1

Order capture

Instance 4

application

Amazon SQS Order fulfillment

application

Instance 2

Messages Messages

Order capture

application

Instance 5

Customer order

## ALB

queue

(Application tier) Order fulfillment

Instance 3 application

Order capture

application

Dead-letter

queue

![Imagen 20-1](images/clase_12_page20_img1.png)

![Imagen 20-2](images/clase_12_page20_img2.png)

![Imagen 20-3](images/clase_12_page20_img3.png)

![Imagen 20-4](images/clase_12_page20_img4.png)

![Imagen 20-5](images/clase_12_page20_img5.png)

![Imagen 20-6](images/clase_12_page20_img6.png)

![Imagen 20-7](images/clase_12_page20_img7.png)

![Imagen 20-8](images/clase_12_page20_img8.png)

![Imagen 20-9](images/clase_12_page20_img9.png)

![Imagen 20-10](images/clase_12_page20_img10.png)

![Imagen 20-11](images/clase_12_page20_img11.png)

![Imagen 20-12](images/clase_12_page20_img12.png)

![Imagen 20-13](images/clase_12_page20_img13.png)

![Imagen 20-14](images/clase_12_page20_img14.png)

Amazon SQS

Tipos de colas

Estándar

### Messages Messages

- Se entrega al menos una vez

- Se ordena según el major esfuerzo

3 2 1 2 3 1 3

Standard • Throughput casi ilimitado

queue

## FIFO

- Entrega FIFO

### Messages Messages • Se procesa exactamente una vez

- Throughput alto

3 2 1 3 2 1

FIFO queue

![Imagen 21-1](images/clase_12_page21_img1.png)

![Imagen 21-2](images/clase_12_page21_img2.png)

![Imagen 21-3](images/clase_12_page21_img3.png)

![Imagen 21-4](images/clase_12_page21_img4.png)

![Imagen 21-5](images/clase_12_page21_img5.png)

![Imagen 21-6](images/clase_12_page21_img6.png)

![Imagen 21-7](images/clase_12_page21_img7.png)

![Imagen 21-8](images/clase_12_page21_img8.png)

![Imagen 21-9](images/clase_12_page21_img9.png)

![Imagen 21-10](images/clase_12_page21_img10.png)

![Imagen 21-11](images/clase_12_page21_img11.png)

![Imagen 21-12](images/clase_12_page21_img12.png)

![Imagen 21-13](images/clase_12_page21_img13.png)

![Imagen 21-14](images/clase_12_page21_img14.png)

![Imagen 21-15](images/clase_12_page21_img15.png)

![Imagen 21-16](images/clase_12_page21_img16.png)

![Imagen 21-17](images/clase_12_page21_img17.png)

![Imagen 21-18](images/clase_12_page21_img18.png)

Amazon SQS

Tiempo de espera

Short polling Long polling

Receive message Receive message

wait time = 0 wait time > 0

Consumer Consumer

Queue Queue

![Imagen 22-1](images/clase_12_page22_img1.png)

![Imagen 22-2](images/clase_12_page22_img2.png)

![Imagen 22-3](images/clase_12_page22_img3.png)

![Imagen 22-4](images/clase_12_page22_img4.png)

![Imagen 22-5](images/clase_12_page22_img5.png)

![Imagen 22-6](images/clase_12_page22_img6.png)

![Imagen 22-7](images/clase_12_page22_img7.png)

![Imagen 22-8](images/clase_12_page22_img8.png)

Amazon SQS

Visibilidad

Ajustar el time-out de visibilidad

Consumer instances

1

1 2

Queue

3

3 2 1

![Imagen 23-1](images/clase_12_page23_img1.png)

![Imagen 23-2](images/clase_12_page23_img2.png)

![Imagen 23-3](images/clase_12_page23_img3.png)

![Imagen 23-4](images/clase_12_page23_img4.png)

![Imagen 23-5](images/clase_12_page23_img5.png)

![Imagen 23-6](images/clase_12_page23_img6.png)

![Imagen 23-7](images/clase_12_page23_img7.png)

![Imagen 23-8](images/clase_12_page23_img8.png)

![Imagen 23-9](images/clase_12_page23_img9.png)

![Imagen 23-10](images/clase_12_page23_img10.png)

![Imagen 23-11](images/clase_12_page23_img11.png)

![Imagen 23-12](images/clase_12_page23_img12.png)

![Imagen 23-13](images/clase_12_page23_img13.png)

![Imagen 23-14](images/clase_12_page23_img14.png)

![Imagen 23-15](images/clase_12_page23_img15.png)

Amazon SQS

Funcionamiento de las colas de mensajes

SQS queue servers and messages

1

Send

Queue

message

Producer Consumer

SQS queue servers and messages

0

5

Visibility

2

timeout

Receive

clock

Queue message 40

Producer Consumer

SQS queue servers

0

Visibility

3

timeout

Delete

Queue message 40 25 clock

Producer Consumer

![Imagen 24-1](images/clase_12_page24_img1.png)

![Imagen 24-2](images/clase_12_page24_img2.png)

![Imagen 24-3](images/clase_12_page24_img3.png)

![Imagen 24-4](images/clase_12_page24_img4.png)

![Imagen 24-5](images/clase_12_page24_img5.png)

![Imagen 24-6](images/clase_12_page24_img6.png)

![Imagen 24-7](images/clase_12_page24_img7.png)

![Imagen 24-8](images/clase_12_page24_img8.png)

![Imagen 24-9](images/clase_12_page24_img9.png)

![Imagen 24-10](images/clase_12_page24_img10.png)

![Imagen 24-11](images/clase_12_page24_img11.png)

![Imagen 24-12](images/clase_12_page24_img12.png)

![Imagen 24-13](images/clase_12_page24_img13.png)

![Imagen 24-14](images/clase_12_page24_img14.png)

![Imagen 24-15](images/clase_12_page24_img15.png)

![Imagen 24-16](images/clase_12_page24_img16.png)

![Imagen 24-17](images/clase_12_page24_img17.png)

![Imagen 24-18](images/clase_12_page24_img18.png)

![Imagen 24-19](images/clase_12_page24_img19.png)

![Imagen 24-20](images/clase_12_page24_img20.png)

![Imagen 24-21](images/clase_12_page24_img21.png)

![Imagen 24-22](images/clase_12_page24_img22.png)

![Imagen 24-23](images/clase_12_page24_img23.png)

![Imagen 24-24](images/clase_12_page24_img24.png)

![Imagen 24-25](images/clase_12_page24_img25.png)

![Imagen 24-26](images/clase_12_page24_img26.png)

![Imagen 24-27](images/clase_12_page24_img27.png)

![Imagen 24-28](images/clase_12_page24_img28.png)

![Imagen 24-29](images/clase_12_page24_img29.png)

![Imagen 24-30](images/clase_12_page24_img30.png)

![Imagen 24-31](images/clase_12_page24_img31.png)

![Imagen 24-32](images/clase_12_page24_img32.png)

![Imagen 24-33](images/clase_12_page24_img33.png)

![Imagen 24-34](images/clase_12_page24_img34.png)

![Imagen 24-35](images/clase_12_page24_img35.png)

![Imagen 24-36](images/clase_12_page24_img36.png)

![Imagen 24-37](images/clase_12_page24_img37.png)

Amazon SQS

Casos de uso

### Colas de trabajo Buffers y operaciones batch

### Desacoplar componentes de una Crear un buffer para protegerse de

aplicación distribuida que procesan la picos de tráfico o acumular cargas

misma cantidad de trabajo a distinta

para procesarlas en forma batch.

velocidad

### Reducir la carga de requerimientos Activar el auto scaling

### Encolar los requerimientos para separar Las colas SQS se pueden usar para

las operaciones lentas de las funciones ayudar a determinar la carga de una

interactivas aplicación e invocar acciones de

escalamiento.

![Imagen 25-1](images/clase_12_page25_img1.png)

![Imagen 25-2](images/clase_12_page25_img2.png)

### Resumen

### Amazon SQS es un servicio administrado de mensajería que

puede ayudar a desacoplar componentes de una aplicación.

Amazon SQS admite colas estándar y FIFO.

Los mensajes no procesados se pueden mandar a una cola DLQ

(dead-letter queue).

### El long polling ayuda a reducir el costo de Amazon SQS porque

disminuye la cantidad de respuestas vacías a un requerimiento.

### Un “productor” envía un mensaje a la cola. Un “consumidor” lo

procesa y lo borra de la cola, dentro del período de visibilidad.

![Imagen 26-1](images/clase_12_page26_img1.png)

![Imagen 26-2](images/clase_12_page26_img2.png)

![Imagen 26-3](images/clase_12_page26_img3.png)

Amazon SNS

![Imagen 27-1](images/clase_12_page27_img1.png)

![Imagen 27-2](images/clase_12_page27_img2.png)

![Imagen 27-3](images/clase_12_page27_img3.png)

### Publicación y suscripción a servicios de mensajería

Se pueden desacoplar aplicaciones de manera asincrónica mediante mensajería de

publicación/suscripción (pub/sub).

Se utiliza cuando la aplicación manda un mensaje a múltiples aplicaciones receptoras de

las que no tiene conocimiento.

La aplicación que envía el mensaje es un publisher.

La aplicación receptora se llama subscriber.

La mensajería pub/sub usa un tema (topic) para desacoplar las aplicaciones.

3

Topic

Message Subscriber 1

Message

Publish message Push

Message

mechanism

Publisher Subscriber 2

2

1

Subscriber 3

![Imagen 28-1](images/clase_12_page28_img1.png)

![Imagen 28-2](images/clase_12_page28_img2.png)

![Imagen 28-3](images/clase_12_page28_img3.png)

![Imagen 28-4](images/clase_12_page28_img4.png)

![Imagen 28-5](images/clase_12_page28_img5.png)

![Imagen 28-6](images/clase_12_page28_img6.png)

![Imagen 28-7](images/clase_12_page28_img7.png)

![Imagen 28-8](images/clase_12_page28_img8.png)

![Imagen 28-9](images/clase_12_page28_img9.png)

![Imagen 28-10](images/clase_12_page28_img10.png)

![Imagen 28-11](images/clase_12_page28_img11.png)

![Imagen 28-12](images/clase_12_page28_img12.png)

![Imagen 28-13](images/clase_12_page28_img13.png)

Amazon SNS

### Tipos de suscriptores

- Dirección de correo electrónico

### Message

- Receptor de mensajes de telefonía

móvil

### Subscriber 1

- Endpoint de notificaciones móviles

de tipo push

### Message Message

- Endpoints HTTP o HTTPS

Topic

### Publisher Subscriber 2 • Funciones AWS Lambda

- Cola de SQS

### Message

- Stream de Amazon Kinesis Data

Firehose

Subscriber 3

![Imagen 29-1](images/clase_12_page29_img1.png)

![Imagen 29-2](images/clase_12_page29_img2.png)

![Imagen 29-3](images/clase_12_page29_img3.png)

![Imagen 29-4](images/clase_12_page29_img4.png)

![Imagen 29-5](images/clase_12_page29_img5.png)

![Imagen 29-6](images/clase_12_page29_img6.png)

![Imagen 29-7](images/clase_12_page29_img7.png)

![Imagen 29-8](images/clase_12_page29_img8.png)

![Imagen 29-9](images/clase_12_page29_img9.png)

![Imagen 29-10](images/clase_12_page29_img10.png)

![Imagen 29-11](images/clase_12_page29_img11.png)

![Imagen 29-12](images/clase_12_page29_img12.png)

Amazon SNS

### Casos de uso

Notificación de alertas Notificación de correo Notificaciones push en

de aplicaciones y electrónico y mensaje móviles

sistemas. de texto.

![Imagen 30-1](images/clase_12_page30_img1.png)

![Imagen 30-2](images/clase_12_page30_img2.png)

![Imagen 30-3](images/clase_12_page30_img3.png)

![Imagen 30-4](images/clase_12_page30_img4.png)

![Imagen 30-5](images/clase_12_page30_img5.png)

![Imagen 30-6](images/clase_12_page30_img6.png)

Uso de Amazon SQS con Amazon SNS

AWS Cloud

Thumbnail application

Generate

Auto Scaling group

thumbnail

1 2 3 4 5

queue

Event

Mobile sizing application

Image notification

Upload

Size for

Mobile S3 bucket for Image S3 bucket for

mobile

client uploaded uploaded converted

queue Auto Scaling group

images notification images

topic

Web sizing application

Size for web

queue

Auto Scaling group

![Imagen 31-1](images/clase_12_page31_img1.png)

![Imagen 31-2](images/clase_12_page31_img2.png)

![Imagen 31-3](images/clase_12_page31_img3.png)

![Imagen 31-4](images/clase_12_page31_img4.png)

![Imagen 31-5](images/clase_12_page31_img5.png)

![Imagen 31-6](images/clase_12_page31_img6.png)

![Imagen 31-7](images/clase_12_page31_img7.png)

![Imagen 31-8](images/clase_12_page31_img8.png)

![Imagen 31-9](images/clase_12_page31_img9.png)

![Imagen 31-10](images/clase_12_page31_img10.png)

![Imagen 31-11](images/clase_12_page31_img11.png)

![Imagen 31-12](images/clase_12_page31_img12.png)

![Imagen 31-13](images/clase_12_page31_img13.png)

![Imagen 31-14](images/clase_12_page31_img14.png)

![Imagen 31-15](images/clase_12_page31_img15.png)

![Imagen 31-16](images/clase_12_page31_img16.png)

![Imagen 31-17](images/clase_12_page31_img17.png)

![Imagen 31-18](images/clase_12_page31_img18.png)

![Imagen 31-19](images/clase_12_page31_img19.png)

![Imagen 31-20](images/clase_12_page31_img20.png)

![Imagen 31-21](images/clase_12_page31_img21.png)

![Imagen 31-22](images/clase_12_page31_img22.png)

![Imagen 31-23](images/clase_12_page31_img23.png)

![Imagen 31-24](images/clase_12_page31_img24.png)

Amazon SNS

Consideraciones

Publicación de mensajes Entrega de mensajes

Se puede usar un tema estándar

Una publicación por vez

cuando no importa el orden de los

No se pueden recuperar mensajes.

mensajes

Si hay que respetar un orden exacto,

se usan temas FIFO.

La política de entrega de mensajes

de un endpoint HTTP o HTTPS permite

controlar el comportamiento de los

reintentos.

![Imagen 32-1](images/clase_12_page32_img1.png)

![Imagen 32-2](images/clase_12_page32_img2.png)

![Imagen 32-3](images/clase_12_page32_img3.png)

Amazon SNS y Amazon SQS

Comparación

### Amazon SNS Amazon SQS

Modelo de mensajería Publisher-Subscriber Producer-Consumer

Modelo de distribución Uno a muchos Uno a uno

Mecanismo de entrega Push (pasivo) Pull (activo)

Persistencia del

No Yes

mensaje

![Imagen 33-1](images/clase_12_page33_img1.png)

![Imagen 33-2](images/clase_12_page33_img2.png)

![Imagen 33-3](images/clase_12_page33_img3.png)

### Resumen

Amazon SNS es un servicio web que se puede usar para configurar,

operar y enviar notificaciones.

Amazon SNS aplica el paradigma de mensajería pub/sub.

Para usar Amazon SNS, se crea un tema, se agregan suscriptores y

se publican mensajes.

### Se pueden usar temas para desacoplar los publicadores de los

suscriptores y enviar mensajes a múltiples receptores a la vez.

Los servicios de AWS pueden publicar mensajes en un tema de SNS

para invocar flujos manejados por eventos.

![Imagen 34-1](images/clase_12_page34_img1.png)

![Imagen 34-2](images/clase_12_page34_img2.png)

Amazon MQ

Desacoplamiento en soluciones híbridas

![Imagen 35-1](images/clase_12_page35_img1.png)

![Imagen 35-2](images/clase_12_page35_img2.png)

![Imagen 35-3](images/clase_12_page35_img3.png)

Amazon MQ

Servicio de mensajería administrado por AWS

Facilita la creación, operación y gestión de una

herramienta de mensajería Apache ActiveMQ o

RabbitMQ en la nube de AWS

### Brinda una solución basada en colas y en temas

Permite que las aplicaciones y los componentes se

comunicen mediante distintos lenguajes, sistemas

Amazon MQ

operativos y protocolos de mensajería.

![Imagen 36-1](images/clase_12_page36_img1.png)

![Imagen 36-2](images/clase_12_page36_img2.png)

![Imagen 36-3](images/clase_12_page36_img3.png)

![Imagen 36-4](images/clase_12_page36_img4.png)

Amazon MQ

Caso de uso: instalación híbrida

Corporate data center AWS Cloud

Availability Zone

Message Message Message Message

Message Amazon MQ Message

producer broker consumer

Amazon EBS

![Imagen 37-1](images/clase_12_page37_img1.png)

![Imagen 37-2](images/clase_12_page37_img2.png)

![Imagen 37-3](images/clase_12_page37_img3.png)

![Imagen 37-4](images/clase_12_page37_img4.png)

![Imagen 37-5](images/clase_12_page37_img5.png)

![Imagen 37-6](images/clase_12_page37_img6.png)

![Imagen 37-7](images/clase_12_page37_img7.png)

![Imagen 37-8](images/clase_12_page37_img8.png)

![Imagen 37-9](images/clase_12_page37_img9.png)

![Imagen 37-10](images/clase_12_page37_img10.png)

![Imagen 37-11](images/clase_12_page37_img11.png)

![Imagen 37-12](images/clase_12_page37_img12.png)

![Imagen 37-13](images/clase_12_page37_img13.png)

Amazon SNS, SQS o MQ

¿Cuál es la mejor en cada caso?

### Amazon SQS Amazon SNS Amazon MQ

- Aplicaciones híbridas

### Aplicaciones centradas en

Aplicación Aplicaciones nativas de nube • Migración de broker de

nube

mensajes

Modelo de • Producer-Consumer

Producer-Consumer Publisher-Subscriber

mensajería • Publisher-Subscriber

### Programming API Amazon SQS API Amazon SNS API APIs estándar de la industria

- Por hora

### Modelo de precios Por solicitud Por solicitud

- Por GB

![Imagen 38-1](images/clase_12_page38_img1.png)

![Imagen 38-2](images/clase_12_page38_img2.png)

![Imagen 38-3](images/clase_12_page38_img3.png)

### Resumen

### Amazon MQ es un servicio gestionado que se puede usar para definer y

operar en la nube las soluciones de mensajería Apache ActiveMQ y

RabbitMQ.

Amazon MQ es compatible con los protocolos y estándares abiertos de

mensajería.

Se puede usar para integrar ambientes on-premises con la nube.

Se puede usar para migrar soluciones de mensajería existentes a la nube.

![Imagen 39-1](images/clase_12_page39_img1.png)

![Imagen 39-2](images/clase_12_page39_img2.png)

![Imagen 39-3](images/clase_12_page39_img3.png)

Módulo 13

Resumen

Distinguir arquitecturas fuertemente y débilmente

acopladas.

Identificar cómo funcionan y cuándo usar Amazon SQS y

Amazon SNS.

Describir Amazon MQ.

Desacoplar cargas de trabajo usando Amazon SQS.

![Imagen 40-1](images/clase_12_page40_img1.png)

![Imagen 40-2](images/clase_12_page40_img2.png)

![Imagen 40-3](images/clase_12_page40_img3.png)

Módulo 13

### Pregunta de práctica

### A company must perform asynchronous processing and implement Amazon Simple Queue Service

(Amazon SQS) as part of a decoupled architecture. The company wants to ensure that the number of

empty responses from polling requests is kept to a minimum.

What should a solutions architect do to ensure that empty responses are reduced?

Identifiquemos las palabras o frases clave:

SQS queue

Empty responses kept to a minimum

![Imagen 41-1](images/clase_12_page41_img1.png)

![Imagen 41-2](images/clase_12_page41_img2.png)

![Imagen 41-3](images/clase_12_page41_img3.png)

Módulo 13

### Pregunta de práctica

### A company must perform asynchronous processing and implement Amazon Simple Queue Service

(Amazon SQS) as part of a decoupled architecture. The company wants to ensure that the number of

empty responses from polling requests is kept to a minimum.

What should a solutions architect do to ensure that empty responses are reduced?

### Choice Response

A Increase the maximum message retention period for the queue.

B Increase the maximum receives for the redrive policy for the queue.

C Increase the default visibility timeout for the queue.

D Increase the receive message wait time for the queue.

![Imagen 42-1](images/clase_12_page42_img1.png)

![Imagen 42-2](images/clase_12_page42_img2.png)

![Imagen 42-3](images/clase_12_page42_img3.png)

Módulo 13

### Pregunta de práctica

### A company must perform asynchronous processing and implement Amazon Simple Queue Service

(Amazon SQS) as part of a decoupled architecture. The company wants to ensure that the number of

empty responses from polling requests is kept to a minimum.

What should a solutions architect do to ensure that empty responses are reduced?

### Choice Response

D Increase the receive message wait time for the queue.

![Imagen 43-1](images/clase_12_page43_img1.png)

![Imagen 43-2](images/clase_12_page43_img2.png)

![Imagen 43-3](images/clase_12_page43_img3.png)

Muchas gracias.

www.austral.edu.ar

![Imagen 44-1](images/clase_12_page44_img1.png)

![Imagen 44-2](images/clase_12_page44_img2.png)

![Imagen 44-3](images/clase_12_page44_img3.png)
