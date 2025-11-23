# Arquitecturas desacopladas

> Esta clase abarca el módulo 13 del curso de AWS Cloud Architecting

## Objetivos

- Distinguir arquitecturas con alto y bajo acoplamiento.
- Comprender el funcionamiento y los casos de uso de Amazon Simple Queue Service (Amazon SQS).
- Comprender el funcionamiento e identificar cuándo usar Amazon Notification Service (Amazon SNS).
- Describir Amazon MQ.
- Desacoplar cargas de trabajo con Amazon SQS.

### Objetivos de un arquitecto de nube

- Identificar cuellos de botella potenciales para que la arquitectura escale en la medida que aumenta el tráfico.
- Limitar el impacto de las fallas para que las fallas de los componentes no produzcan la caída de la aplicación.
- Implementar arquitecturas que permitan aplicar cambios a un componente sin afectar a los demás, para minimizar las bajas por mantenimiento.

> Todo lo que hace esta clase es ofrecerte servicios para desacoplar arquitecturas, que al final del día son colas de mensajería (MQ, SQS, SNS, etc.). No sé qué tanto hay que profundizar en cada uno.\
> Te puede llegar a interesar que tenés SDKs para cada uno, o que soportan un cierto tamaño de mensajes, sumado al caso de uso particular de cada uno.\
> No le dedicaría una clase entera, les adjunto el PDF:

<embed src="../presentations/Nube con AWS - Clase 12.pdf" type="application/pdf" width="100%" height="600px" />