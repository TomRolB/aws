# Arquitecturas serverless y microservicios

> Esta clase abarca el módulo 14 del curso de AWS Cloud Architecting

## Objetivos

- Definir arquitecturas serverless.
- Identificar las características de los microservicios.
- Diseñar una solución serverless con AWS Lambda.
- Definir cómo se usan los contenedores en AWS.
- Describir los tipos de flujo que soportan las AWS Step Functions.
- Describir una arquitectura común para el Amazon API Gateway.
- Aplicar los principios del AWS Well-Architected Framework para construir arquitecturas serverless.

### De un arquitecto de nube

- Reconocer cuándo usar arquitecturas serverless en AWS y qué servicios elegir, de acuerdo con el caso de uso.
- Implementar arquitecturas guiadas por eventos con microservicios para construir arquitecturas de microservicios escalables y resilientes.
- Conocer cuándo usar herramientas de orquestación para que la arquitectura de microservicios trate las fallas con una intervención manual mínima.

## Soluciones serverless

### Diseño de una aplicación web en una VPC

![Diseño de una app web](./images/Clase%2013/web-app-design-on-vpc.png)

### Beneficios de AWS serverless

- No requiere administrar servidores
- Se paga por el valor del servicio
- Escalamiento continuo
- Alta disponibilidad desde el diseño
- Adecuado para arquitecturas orientadas a eventos y microservicios

### Servicios serverless de AWS

![Serverless](./images/Clase%2013/serverless-services.png)

### Aplicación web usando servicios serverless
```mermaid
flowchart TD
    %% --- Nodes ---
    Client(💻 Browser<br/>client)

    %% Top Row
    R53(🛡️ Amazon<br/>Route 53):::purple
    CF(🌐 Amazon<br/>CloudFront):::purple
    S3(🪣 Amazon S3):::green
    
    %% Middle/Bottom Rows
    Cognito(🪪 Amazon<br/>Cognito):::red
    APIGW(🚪 Amazon<br/>API Gateway):::pink
    Lambda(⚡ AWS Lambda):::orange
    Dynamo(💽 Amazon<br/>DynamoDB):::purple

    %% Tier Labels (Dark Green Boxes)
    WebTier[Web tier]:::tier
    AppTier[App tier]:::tier
    DataTier[Data tier]:::tier

    %% --- Connections ---

    %% 1. Web Content Flow
    Client -->|DNS lookup| R53
    R53 -->|DNS lookup| CF
    Client -->|Website entry point| CF
    CF --> S3
    WebTier --> S3

    %% 2. Authentication Flow
    Client <-->|Authentication| Cognito
    AppTier --> Cognito

    %% 3. API & Data Flow
    Client -->|API requests| APIGW
    APIGW <--> Cognito
    APIGW <--> Lambda
    AppTier --> Lambda
    Lambda <--> Dynamo
    DataTier --> Dynamo

    %% --- Styling Classes ---
    %% Purple (Networking & DB)
    classDef purple fill:#8c4fff,stroke:#fff,stroke-width:2px,color:white,rx:5,ry:5;
    
    %% Green (Storage)
    classDef green fill:#6cae3e,stroke:#fff,stroke-width:2px,color:white,rx:5,ry:5;
    
    %% Red (Cognito)
    classDef red fill:#dd344c,stroke:#fff,stroke-width:2px,color:white,rx:5,ry:5;
    
    %% Pink (API Gateway - distinct red/pink in AWS)
    classDef pink fill:#e01e5a,stroke:#fff,stroke-width:2px,color:white,rx:5,ry:5;
    
    %% Orange (Compute)
    classDef orange fill:#e68a00,stroke:#fff,stroke-width:2px,color:white,rx:5,ry:5;

    %% Tier Labels (Dark Green, Rectangle)
    classDef tier fill:#1a4742,stroke:none,color:white,shape:rect;
```
## Arquitectura de microservicios serverless

| Autónomo                                                              | Especializado                                                                         |
| --------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| Se puede desarrollar e implementar sin afectar a otros microservicios | Realiza una única función de negocio, resolviendo un problema específico              |
| Escala de manera independiente                                        | Pertenece a un equipo de desarrollo pequeño que selecciona herramientas de desarrollo |
| No comparte código con otros microservicios                           | Es stateless                                                                          |
| Se comunica mediante APIs bien definidas                              | Tiene su propio almacenamiento de datos                                               |

### Beneficios
- Agilidad 
- Código reutilizable
- Escalamiento flexible
- Libertad tecnológica
- Resiliencia
- Implementación simplificada

### Patrones de microservicios serverless en AWS

#### RESTful APIs

```mermaid
flowchart TD

    %% --- Nodes ---
    APIGW["🚪 Amazon API Gateway"]
    Lambda["⚡ AWS Lambda"]
    DB["💽 Database"]

    %% --- Connections ---
    APIGW <--> Lambda
    Lambda --> DB

    %% --- Styles ---
    classDef header fill:#438dd5,stroke:none,color:white,font-weight:bold,font-size:18px;
    classDef pink fill:#e01e5a,stroke:none,color:white,font-weight:bold,rx:5,ry:5;
    classDef orange fill:#e68a00,stroke:none,color:white,font-weight:bold,rx:5,ry:5;
    classDef dark fill:#232f3e,stroke:none,color:white,font-weight:bold,rx:5,ry:5;

    %% Assign classes explicitly at the end
    class TitleNode header;
    class APIGW pink;
    class Lambda orange;
    class DB dark;
```
#### Containers

```mermaid
flowchart TD

    %% --- Top Row ---
    subgraph TopRow [" "]
        direction LR
        APIGW["🚪 Amazon API Gateway"]:::pink
        ALB["⚖️ Application Load Balancer"]:::purple
    end

    %% --- Bottom Row ---
    subgraph BottomRow [" "]
        direction LR
        DB["💽 Database"]:::dark
        Fargate["📦 AWS Fargate"]:::orange
    end

    %% --- Connections ---
    APIGW <--> ALB
    ALB <--> Fargate
    Fargate <--> DB

    %% --- Styles ---
    classDef header fill:#438dd5,stroke:none,color:white,font-weight:bold,font-size:18px,shape:rect;
    classDef pink fill:#e01e5a,stroke:none,color:white,font-weight:bold,rx:5,ry:5;
    classDef orange fill:#e68a00,stroke:none,color:white,font-weight:bold,rx:5,ry:5;
    classDef purple fill:#8c4fff,stroke:none,color:white,font-weight:bold,rx:5,ry:5;
    classDef dark fill:#232f3e,stroke:none,color:white,font-weight:bold,rx:5,ry:5;
    
    %% Hide subgraph borders
    style TopRow fill:none,stroke:none
    style BottomRow fill:none,stroke:none
```

#### Streaming
```mermaid
flowchart TD

    %% --- Nodes ---
    Kinesis["🌊 Amazon Kinesis"]:::purple
    Lambda["⚡ AWS Lambda"]:::orange
    DB["💽 Database"]:::dark

    %% --- Connections ---
    Kinesis <--> Lambda
    Lambda <--> DB

    %% --- Styles ---
    classDef header fill:#438dd5,stroke:none,color:white,font-weight:bold,font-size:18px,shape:rect;
    classDef orange fill:#e68a00,stroke:none,color:white,font-weight:bold,rx:5,ry:5;
    classDef purple fill:#8c4fff,stroke:none,color:white,font-weight:bold,rx:5,ry:5;
    classDef dark fill:#232f3e,stroke:none,color:white,font-weight:bold,rx:5,ry:5;
```


### Microservicios en una arquitectura web serverless
![Microservicios en web app](./images/Clase%2013/microservices-web-app.png)


## Arquitecturas serverless con AWS Lambda

| Tareas                                            | Servidor en una VPC | Serverless |
| ------------------------------------------------- | ------------------- | ---------- |
| Configurar una instancia                          | Yes                 | No         |
| Actualizar el sistema operativo                   | Yes                 | No         |
| Instalar la plataforma de aplicación              | Yes                 | No         |
| Construir e implementar aplicaciones              | Yes                 | Yes        |
| Configurar el escalamiento y el balanceo de carga | Yes                 | No         |
| Proteger y monitorear instancias continuamente    | Yes                 | No         |
| Monitorear y mantener las aplicaciones            | Yes                 | Yes        |

### AWS Lambda

- AWS Lambda permite ejecutar funciones de código sin crear ni gestionar servidores.
- Las funciones Lambda son configurables respecto de: lenguaje de ejecución, cantidad de memoria y duración.
- Una función puede durar 15 minutos como máximo.
- Las funciones se implementan como archivos .zip o imágenes de contenedores.

### Funciones Lambda - Ubicaciones

**En el servicio AWS Lambda**
![Lambda](./images/Clase%2013/lambda.png)

**En un cache regional de Amazon CloudFront**

![CloudFront](./images/Clase%2013/cloudfront.png)

### Conectar una función Lambda a una VPC
![Lambda VPC](./images/Clase%2013/connect-lambda-to-vpc.png)

### Escenarios para usar funciones Lambda

| Procesamiento sincrónico        | Procesamiento asincrónico        | Procesamiento de streaming |
| ------------------------------- | -------------------------------- | -------------------------- |
| Aplicaciones web                | Eventos programados              | Aplicaciones de streaming  |
| Servicios web                   | Mensajes en colas                |                            |
| Microservicios                  | Transformación de imagen o video |                            |
| Inferencias de machine learning | Triggers de servicios de AWS     |                            |

### Funciones Lambda sincrónicas

#### Usando un API Gateway
```mermaid
flowchart LR

    %% --- Nodes ---
    Client["💻<br>Browser client"]
    APIGW["🚪<br>Amazon API<br>Gateway"]
    L_Service["⚡<br>AWS Lambda<br>service"]
    L_Func(("⚡<br>AWS Lambda<br>function"))
    AWS["☁️<br>AWS<br>service"]

    %% Forward Request
    Client -->|"API request"| APIGW
    APIGW --> L_Service
    L_Service -->|"Invoke"| L_Func
    L_Func --> AWS

    %% Backward Response
    AWS -.-> L_Func
    L_Func -.->|"API response"| L_Service
    L_Service -.-> APIGW
    APIGW -.-> Client

    %% --- Styles ---
    classDef header fill:#438dd5,stroke:none,color:white,font-weight:bold,font-size:18px
    classDef pink fill:#e01e5a,stroke:none,color:white,font-weight:bold
    classDef orangeSquare fill:#e68a00,stroke:none,color:white,font-weight:bold
    classDef orangeCircle fill:#fff,stroke:#e68a00,stroke-width:3px,color:#e68a00,font-weight:bold
    classDef dark fill:#232f3e,stroke:none,color:white,font-weight:bold

    %% Explicit Class Assignment (No semicolons)
    class TitleNode header
    class APIGW pink
    class L_Service orangeSquare
    class L_Func orangeCircle
    class AWS dark
```

#### Usando la URL de la función Lambda desde una API externa

```mermaid
flowchart LR

    %% --- Nodes ---
    Client["💻<br>Browser client"]
    L_Service["⚡<br>AWS Lambda<br>service"]:::orangeSquare
    L_Func(("⚡<br>AWS Lambda<br>function")):::orangeCircle
    AWS["☁️<br>AWS<br>service"]:::dark

    %% --- Connections ---

    %% Forward Request
    Client -->|"URL request"| L_Service
    L_Service -->|"Invoke"| L_Func
    L_Func --> AWS

    %% Backward Response
    AWS -.-> L_Func
    L_Func -.->|"URL response"| L_Service
    L_Service -.-> Client

    %% --- Styles ---
    classDef header fill:#438dd5,stroke:none,color:white,font-weight:bold,font-size:18px;
    classDef orangeSquare fill:#e68a00,stroke:none,color:white,font-weight:bold;
    classDef orangeCircle fill:#fff,stroke:#e68a00,stroke-width:3px,color:#e68a00,font-weight:bold;
    classDef dark fill:#232f3e,stroke:none,color:white,font-weight:bold;

    class Title header;
    class L_Service orangeSquare;
    class L_Func orangeCircle;
    class AWS dark;
```

### Funciones Lambda asincrónicas

#### Trigger de un servicio de AWS
```mermaid
flowchart LR

    %% --- Nodes ---
    Start(( ))
    
    S3["🪣<br>Amazon Simple<br>Storage Service<br>(Amazon S3) bucket"]
    L_Service["⚡<br>AWS Lambda<br>service"]
    Int_Queue["📥<br>Lambda<br>internal<br>queue"]
    L_Func(("⚡<br>AWS Lambda<br>function"))
    SQS["📨<br>Amazon Simple Queue<br>Service (Amazon SQS)<br>error queue"]
    
    Start -->|"Upload object"| S3
    S3 -->|"Trigger"| L_Service
    L_Service --> Int_Queue
    Int_Queue --> L_Func
    L_Func -->|"Error<br>destination"| SQS

    %% --- Styles ---
    classDef header fill:#438dd5,stroke:none,color:white,font-weight:bold,font-size:18px
    classDef hidden display:none
    classDef green fill:#fff,stroke:#6cae3e,stroke-width:2px,color:#000
    classDef orangeSquare fill:#e68a00,stroke:none,color:white,font-weight:bold
    classDef orangeBorder fill:#fff,stroke:#e68a00,stroke-width:2px,color:#000
    classDef orangeCircle fill:#fff,stroke:#e68a00,stroke-width:3px,color:#e68a00,font-weight:bold
    classDef pinkBorder fill:#fff,stroke:#e01e5a,stroke-width:2px,color:#000

    %% Explicit Class Assignment
    class TitleNode header
    class Start hidden
    class S3 green
    class L_Service orangeSquare
    class Int_Queue orangeBorder
    class L_Func orangeCircle
    class SQS pinkBorder
```


#### Evento programado
```mermaid
flowchart LR

    %% --- Nodes ---
    EB["🏵️<br>Amazon<br>EventBridge"]
    L_Service["⚡<br>AWS Lambda<br>service"]
    Int_Queue["📥<br>Lambda<br>internal<br>queue"]
    L_Func(("⚡<br>AWS Lambda<br>function"))
    SQS["📨<br>Amazon SQS<br>error queue"]

    %% --- Connections ---
    
    EB -->|"Scheduled<br>event"| L_Service
    L_Service --> Int_Queue
    Int_Queue --> L_Func
    L_Func -->|"Error<br>destination"| SQS

    %% --- Styles ---
    classDef header fill:#438dd5,stroke:none,color:white,font-weight:bold,font-size:18px
    classDef pinkSquare fill:#e01e5a,stroke:none,color:white,font-weight:bold
    classDef orangeSquare fill:#e68a00,stroke:none,color:white,font-weight:bold
    classDef orangeBorder fill:#fff,stroke:#e68a00,stroke-width:2px,color:#000
    classDef orangeCircle fill:#fff,stroke:#e68a00,stroke-width:3px,color:#e68a00,font-weight:bold
    classDef pinkBorder fill:#fff,stroke:#e01e5a,stroke-width:2px,color:#000

    %% Explicit Class Assignment
    class TitleNode header
    class EB pinkSquare
    class L_Service orangeSquare
    class Int_Queue orangeBorder
    class L_Func orangeCircle
    class SQS pinkBorder
```

### Streaming y colas - Source mapping

```mermaid
flowchart LR
    %% --- Nodes ---
    DDB["🟣<br>Amazon DynamoDB<br>stream"]:::purpleBorder
    L_Service["⚡<br>AWS Lambda<br>service"]:::orangeSquare
    L_Func(("⚡<br>AWS Lambda<br>function")):::orangeCircle
    SQS["📨<br>Amazon SQS<br>error queue"]:::pinkBorder

    %% --- Connections ---
    %% Polling Loop
    L_Service -->|"Poll for events"| DDB
    DDB -->|"Events"| L_Service
    
    %% Invocation Flow
    L_Service -->|"Invoke"| L_Func
    L_Func -->|"Error destination"| SQS

    %% --- Styles ---
    classDef purpleBorder fill:#fff,stroke:#8c4fff,stroke-width:2px,color:#000
    classDef orangeSquare fill:#e68a00,stroke:none,color:white,font-weight:bold
    classDef orangeCircle fill:#fff,stroke:#e68a00,stroke-width:3px,color:#e68a00,font-weight:bold
    classDef pinkBorder fill:#fff,stroke:#e01e5a,stroke-width:2px,color:#000

    %% Explicit Class Assignment
    class DDB purpleBorder
    class L_Service orangeSquare
    class L_Func orangeCircle
    class SQS pinkBorder
```

### Handler de una función Lambda en Python
```py
import json

def lambda_handler(event, context):
    length=event['length']
    width=event['width']

    area = calculate_area(length, width)

    data = {"area": area}
    return json.dumps(data)

def calculate_area(length, width):
    return length*width
```
- **Line 2**: Event object is a JSON document containing input data and invoking service data
- **Line 2**: Context object provides methods and properties about function runtime and invocation.
- **Line 7**: `json.dumps(data)` returns result as a JSON document.
- **Lines 8 and 9**: Business logic method

### Capas de funciones lambda

![Capas de Lambda](./images/Clase%2013/lambda-layers.png)

## Contenedores en AWS

### Casos de uso vs funciones lambda

| Más de 15 minutos                                                                    | Aplicaciones que usan mucha memoria                                                             | Costo                                                                                                                                                                             | Migración de contenedores legacy                                                                                |
| ------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| AWS Lambda tiene un límite de 15 minutos de duración para la ejecución de funciones. | Las cargas de trabajo que exceden los 10 GB de memoria no son apropiadas para funciones lambda. | Los contenedores pueden ejecutarse de manera continua con costo fijo. El precio de una función lambda aumenta con la cantidad de ejecuciones, la duración y la memoria utilizada. | Los contenedores pueden ayudar a migrar aplicaciones legacy que se ejecutan on-premises o en instancias de EC2. |

### Beneficios

![Contenedores vs. VMs](./images/Clase%2013/containers-vs-vm.png)

### Casos de uso
- Aplicaciones con microservicios
- Procesamiento batch
- Escalar modelos de machine learning (ML)
- Estandarizar aplicaciones de arquitectura híbrida
- Migrar aplicaciones a la nube

### Docker containers

![Docker containers](./images/Clase%2013/docker-containers.png)

### Servicios de contenedores en AWS

| Registro                                       | Orquestación                                   | Cómputo                                   |
| ---------------------------------------------- | ---------------------------------------------- | ----------------------------------------- |
| Amazon Elastic Container Registry (Amazon ECR) | Amazon Elastic Container Service (Amazon ECS)  | Amazon Elastic Compute Cloud (Amazon EC2) |
|                                                | Amazon Elastic Kubernetes Service (Amazon EKS) | AWS Fargate                               |
|                                                |                                                | AWS Lambda                                |

### Beneficios de AWS Fargate

| Sin gestión de clusters o servidores                                               | Facturación por segundo | Escalamiento automático                                                            | Adecuado para equipos nuevos                                          |
| ---------------------------------------------------------------------------------- | ----------------------- | ---------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| • No hay que crear ni mantener servidores.<br>• No necesitamos optimizar clusters. | • Pago por uso          | • Escalamiento automático de tareas según el uso de CPU, memoria u otras métricas. | • No requiere conocimiento profundo de la tecnología de contenedores. |

### Amazon ECS

#### Implementación y ejecución de contenedores

![Implementación de ECS](./images/Clase%2013/ecs-implementation.png)

### Amazon EKS

#### Implementación y ejecución de contenedores

![Implementación de EKS](./images/Clase%2013/eks-implementation.png)

### Amazon EKS y Amazon ECS - Diferencias

| Tema                   | Amazon ECS                                             | Amazon EKS                                                                 |
| ---------------------- | ------------------------------------------------------ | -------------------------------------------------------------------------- |
| Complejidad            | Simplifica la creación y el mantenimiento de clusters. | Provee mayor control sobre los clusters, pero la interfaz es compleja.     |
| Escalamiento           | Escalamiento automático a demanda.                     | Configuración manual de los grupos de autoescalamiento.                    |
| Herramientas           | Amazon ECS                                             | Kubernetes                                                                 |
| Experiencia del equipo | Nuevo en la arquitectura de contenedores.              | Familiarizado con la arquitectura y los procesos de control de Kubernetes. |

## AWS Step Functions

### Microservicios - Desafíos

| Dependencias                                                                                                     | Escenarios de error                               | Coordinación                                                                                                                                               |
| ---------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| • Administrar las dependencias entre microservicios<br>• Encadenar los microservicios en secuencia o en paralelo | • Ejecutar reintentos luego de errores o timeouts | • Escalar la aplicación<br>• Mantener el estado de microservicios stateless<br>• Pasar datos entre microservicios<br>• Monitoreo y resolución de problemas |

### AWS Step Functions

- Servicio de orquestación serverless que maneja flujos entre distintos servicios de AWS
- Tiene máquinas de estado (workflows) que contienen una serie de estados dependientes de eventos (pasos)
- Gestiona el estado, los checkpoints y los reinicios de cada workflow
- Tiene funciones para el tratamiento de errores
- Puede transferir datos entre estados
- Los estados pueden filtrar y manipular datos

### Flujos estándar o exprés

| Criterio                         | Standard Workflows                       | Express Workflows                                                     |
| -------------------------------- | ---------------------------------------- | --------------------------------------------------------------------- |
| Duración                         | Larga                                    | Breve, sin actividades                                                |
| Métricas                         | Historia completa en la consola          | Resultados en logs de CloudWatch                                      |
| Procesamiento                    | Asincrónico                              | Sincrónico o asincrónico                                              |
| Modelo de ejecución              | Exactamente una vez                      | • Sincrónico: al menos una vez<br>• Asincrónico: Como máximo, una vez |
| Progreso de la máquina de estado | Se persiste en cada transición de estado | Sin persistencia del estado en cada transición de estado              |
| Precios                          | Por cantidad de transiciones de estado   | Por cantidad y duración de llamadas por workflow                      |

### Casos de uso

- Orquestar microservicios
- Procesamiento de datos
- Machine Learning (ML)
- Automatización de seguridad

### Coordinación de estados

**Ejecución secuencial**
```mermaid
flowchart TD

    %% --- Nodes ---
    A[Task A]:::box
    B[Task B]:::box
    C[Task C]:::box

    %% --- Connections ---
    A --> B
    B --> C

    %% --- Styles ---
    classDef box fill:#34495e,stroke:none,color:white,font-weight:bold,rx:5,ry:5
    classDef title fill:none,stroke:none,color:#000080,font-size:18px,font-weight:bold

    class A,B,C box
    class TitleNode title
```

**Ejecución en paralelo**
```mermaid
flowchart TD

    %% --- Nodes ---
    subgraph Container [ ]
        direction LR
        A[Task A]:::box
        B[Task B]:::box
    end
    
    C[Task C]:::box

    %% --- Connections ---
    Container --> C

    %% --- Styles ---
    classDef box fill:#34495e,stroke:none,color:white,font-weight:bold,rx:5,ry:5
    classDef title fill:none,stroke:none,color:#000080,font-size:18px,font-weight:bold

    class A,B,C box
    class TitleNode title
    
    %% Style the subgraph to look like the white box with border
    style Container fill:#fff,stroke:#34495e,stroke-width:1px,rx:10,ry:10
```

**Gestión de errores**
```mermaid
flowchart TD

    %% --- Nodes ---
    %% Using <br/> for multiline text inside the node
    A["Task A<br>try{...}<br>catch{...}<br>finally{...}"]:::box

    %% --- Styles ---
    classDef box fill:#34495e,stroke:none,color:white,font-weight:bold,rx:10,ry:10,text-align:left
    classDef title fill:none,stroke:none,color:#000080,font-size:18px,font-weight:bold

    class A box
    class TitleNode title
```

**Elegir tarea según los datos**
```mermaid
flowchart TD

    %% --- Nodes ---
    A[Task A]:::box
    Dec{?}:::diamond
    B[Task B]:::box
    C[Task C]:::box

    %% --- Connections ---
    A --> Dec
    Dec --> B
    Dec --> C

    %% --- Styles ---
    classDef box fill:#34495e,stroke:none,color:white,font-weight:bold,rx:5,ry:5
    classDef diamond fill:#34495e,stroke:none,color:white,font-weight:bold
    classDef title fill:none,stroke:none,color:#000080,font-size:18px,font-weight:bold

    class A,B,C box
    class Dec diamond
    class TitleNode title
```

**Procesar tareas en paralelo (Map)**
```mermaid
flowchart TD

    %% --- Main Container ---
    subgraph MapState [ ]
        direction LR
        
        %% Column 1
        subgraph Col1 [ ]
             direction TB
             A1[Task A]:::box
             B1[Task B]:::box
             C1[Task C]:::box
             A1-->B1-->C1
        end

        %% Column 2
        subgraph Col2 [ ]
             direction TB
             A2[Task A]:::box
             B2[Task B]:::box
             C2[Task C]:::box
             A2-->B2-->C2
        end

        %% Column 3
        subgraph Col3 [ ]
             direction TB
             A3[Task A]:::box
             B3[Task B]:::box
             C3[Task C]:::box
             A3-->B3-->C3
        end
    end

    %% --- Alignment ---

    %% --- Styles ---
    classDef box fill:#34495e,stroke:none,color:white,font-weight:bold,rx:5,ry:5
    classDef title fill:none,stroke:none,color:#000080,font-size:18px,font-weight:bold

    class A1,B1,C1,A2,B2,C2,A3,B3,C3 box
    class TitleNode title
    
    %% Style the containers
    style MapState fill:#fff,stroke:#34495e,stroke-width:1px,rx:10,ry:10
    style Col1 fill:none,stroke:none
    style Col2 fill:none,stroke:none
    style Col3 fill:none,stroke:none
```

**Reiteración de tareas fallidas**
```mermaid
flowchart TD

    %% --- Nodes ---
    A[Task A]:::box

    %% --- Connections ---
    %% Creating a loop back to itself
    A --> A

    %% --- Alignment ---

    %% --- Styles ---
    classDef box fill:#34495e,stroke:none,color:white,font-weight:bold,rx:5,ry:5
    classDef title fill:none,stroke:none,color:#000080,font-size:18px,font-weight:bold

    class A box
```


### Tipos de estado

| Estados de trabajo                                                               | Estados de transición                                                                                 | Estados de detención                                      |
| -------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| **Task**: Se integra con servicios de AWS                                        | **Choice**: Agrega condiciones para controlar el flujo hacia el estado siguiente                      | **Success**: Detiene la ejecución y la marca como exitosa |
| **Activity**: Realiza una tarea en cualquier lugar                               | **Parallel**: Agrega ramas de máquinas de estado anidadas en una máquina de estado                    | **Fail**: Detiene la ejecución y la marca como fallida    |
| **Pass**: Pasa o filtra datos de entrada al estado siguiente                     | **Map**: Separa el flujo de cada registro de datos en ejecuciones de data sets que corren en paralelo | **End parameter**: Detiene la ejecución                   |
| **Wait**: Demora el flujo por un período especificado                            |                                                                                                       |                                                           |
| **State has wait for callback state option**: Pausa el flujo y espera el retorno |                                                                                                       |                                                           |

### Ejemplo

```mermaid
flowchart TD
    %% --- Start / End ---
    Start([Start])
    End([End])

    %% --- Action Nodes ---
    Recommend["⚡ Recommend stock trade"]
    Trade["⚡ Trade stock transaction"]
    
    %% --- The Callback Section ---
    subgraph Callback ["Wait for callback token"]
        direction TB
        ReqApproval["⚙️ Request human approval"]
        Email["📧 Email to approver"]
        ReqApproval --> Email
    end

    %% --- Decision Nodes ---
    Dec_Stock{"❓ Any stock to trade?"}
    Dec_Human{"❓ Human approval required?"}
    Dec_Approved{"❓ Trade approved?"}
    Dec_Vas{"❓ Vas transaction successful?"}

    %% --- Result Nodes ---
    Res_NoRecs("✅ No recommendations")
    Res_Success("✅ Trade successful")
    Res_Fail("❌ Trade unsuccessful")
    Res_Denied("❌ Trade not approved")

    %% --- Connections ---
    
    %% Main Flow
    Start --> Recommend
    Recommend --> Dec_Stock
    
    %% Path: No Stock
    Dec_Stock -- No --> Res_NoRecs
    Res_NoRecs --> End

    %% Path: Yes Stock
    Dec_Stock -- Yes --> Dec_Human
    
    %% Path: Approval Logic
    Dec_Human -- Yes --> ReqApproval
    Email -->|"Approve or deny<br>callback"| Dec_Approved
    
    Dec_Approved -- No --> Res_Denied
    Res_Denied --> End

    %% Path: To Trade (via Approval YES or Human Req NO)
    Dec_Human -- No --> Trade
    Dec_Approved -- Yes --> Trade

    %% Path: Transaction Logic
    Trade --> Dec_Vas
    Dec_Vas -- Yes --> Res_Success
    Dec_Vas -- No --> Res_Fail
    
    Res_Success --> End
    Res_Fail --> End

    %% --- Styling ---
    
    %% General Styles
    classDef default fill:#fff,stroke:#333,stroke-width:1px;
    
    %% Action Nodes (Rectangles with Blue Border)
    classDef action fill:#fff,stroke:#3c6eb4,stroke-width:2px,color:#000;
    class Recommend,Trade,ReqApproval,Email action;

    %% Decision Nodes (Diamonds)
    classDef decision fill:#fff,stroke:#3c6eb4,stroke-width:2px,color:#000;
    class Dec_Stock,Dec_Human,Dec_Approved,Dec_Vas decision;

    %% Result Nodes (Rounded with color)
    classDef result fill:#fff,stroke:#3c6eb4,stroke-width:2px,color:#000,rx:5,ry:5;
    class Res_NoRecs,Res_Success,Res_Fail,Res_Denied result;

    %% Callback Header Style (Blue background)
    classDef subgraphHeader fill:#3c6eb4,stroke:none,color:white,font-weight:bold;
    style Callback fill:#f0f8ff,stroke:#3c6eb4,stroke-dasharray: 5 5
```

## Amazon API Gateway

### Ventajas de las API

| Estandarizar la comunicación entre apps                                                                                             | Proteger los microservicios                                                                                                                                        | Monetizar las API y registrar estadísticas                                                                   |
| ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| • Estandarizar la conexión entre aplicaciones desarrolladas en distintos lenguajes<br>• Ocultar la complejidad de la implementación | • Decidir cuándo requerir autorización<br>• Verificar los formatos de las solicitudes<br>• Manejar la cantidad de solicitudes<br>• Restringir el acceso a recursos | • Registrar el acceso de clientes para gestionar la facturación<br>• Generar estadísticas de uso por cliente |

### API Gateway

- Permite crear, publicar y mantener APIs de tipo REST, HTTP, y WebSocket
- Gestión de tráfico, autorización y control de acceso a recursos configurables
- Brinda acceso a servicios de AWS y a endpoints de acceso público
- Mantiene múltiples versiones de una API deaplicación
- Establece planes de uso por cliente para monetizar y controlar el uso de las APIs
- Puede mantener un cache de respuestas comunes


### Tipos de API

| REST APIs                                                                                                                                                               | HTTP APIs                                                                                                                                   | WebSocket APIs                                                                                                                                              |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| • Colección de rutas y métodos<br>• Para aplicaciones que requieren funciones de administración de API<br>• Permite cross-origin resource sharing (CORS)<br>• Stateless | • Colección de rutas y métodos<br>• Para microservicios<br>• Menor latencia y menor costo que las API REST<br>• Soporta CORS<br>• Stateless | • Colección de rutas de WebSocket<br>• Para aplicaciones en tiempo real<br>• Establece una sesión entre el cliente y los servicios de backend<br>• Stateful |

### Integración con backend
![Integración](./images/Clase%2013/api-gateway-integration.png)

## AWS Well-Architected Framework

- Reliability
    - Usar mecanismos DLQ para retener, investigar y volver a ejecutar transacciones fallidas
    - Ejecutar un roll back de las transacciones fallidas
- Security
    - Controlar el acceso a las API
    - Controlar el acceso a la aplicación serverless
    - Cifrar los datos en tránsito y en reposo
    - Implementar seguridad de aplicaciones en las cargas de trabajo
- Performance Efficiency
  - Optimizar el rendimiento de la aplicación
- Cost Optimization
    - Optimizar el costo de la aplicación
    - Usar integraciones de AWS