# Arquitecturas de Nube con AWS - Universidad Austral

> Material completo del curso Arquitecturas de Nube con AWS, Universidad Austral, año 2025

## Sobre este repositorio

Este repositorio contiene el material completo del curso **Arquitecturas de Nube con AWS** de la Universidad Austral, cursado durante el año 2025. El contenido está organizado en formato de libro digital utilizando [mdBook](https://rust-lang.github.io/mdBook/), facilitando el estudio y la comprensión de los servicios y arquitecturas de Amazon Web Services.

## Contenido

### Clases Teórico-Prácticas

El curso incluye 14 clases que cubren los aspectos fundamentales de AWS:

- **Clase 1**: Introducción a la computación en la nube y AWS
- **Clase 2**: Fundamentos de AWS - IAM y conceptos básicos
- **Clase 3**: Servicios de cómputo - EC2
- **Clase 4**: Almacenamiento en AWS - S3, EBS, EFS
- **Clase 5**: Redes en AWS - VPC, Subredes, y Enrutamiento
- **Clase 6**: Bases de datos en AWS - RDS, DynamoDB
- **Clase 7**: Balanceo de carga y autoescalado
- **Clase 8**: Contenedores y orquestación - ECS, EKS
- **Clase 9**: Servicios serverless - Lambda, API Gateway
- **Clase 10**: Monitoreo y logging - CloudWatch, CloudTrail
- **Clase 11**: DevOps en AWS - CodePipeline, CodeBuild
- **Clase 12**: Seguridad avanzada en AWS
- **Clase 13**: Arquitecturas de referencia y mejores prácticas
- **Clase 14**: Planeamiento para desastres

### Recursos Adicionales

- **AWS CLI**: Guía práctica de uso de la interfaz de línea de comandos de AWS
- **Ejemplos de código**: Implementaciones prácticas con Python y boto3

### Estructura del repositorio

```
aws/
├── book/                    # Carpeta generada con el libro compilado
├── src/                     # Contenido del curso
│   ├── SUMMARY.md          # Índice del libro
│   ├── chapter_1.md        # Introducción
│   ├── Clase 1.md          # Introducción a la nube y AWS
│   ├── Clase 2.md          # IAM y fundamentos
│   ├── Clase 3.md          # EC2
│   ├── Clase 4.md          # Almacenamiento
│   ├── Clase 5.md          # Redes y VPC
│   ├── Clase 6.md          # Bases de datos
│   ├── Clase 7.md          # Load balancing y autoscaling
│   ├── Clase 8.md          # Contenedores
│   ├── Clase 9.md          # Serverless
│   ├── Clase 10.md         # Monitoreo
│   ├── Clase 11.md         # DevOps
│   ├── Clase 12.md         # Seguridad
│   ├── Clase 13.md         # Arquitecturas
│   ├── Clase 14.md         # Disaster Recovery
│   ├── CLI.md              # Guía de AWS CLI
│   ├── images/             # Imágenes extraídas de las presentaciones
│   ├── presentations/      # PDFs originales de las presentaciones
│   └── examples/           # Ejemplos de código
├── book.toml               # Configuración de mdBook
└── README.md               # Este archivo
```

## Cómo usar este repositorio

### Para estudiar

1. **Visualizar el libro**: Accede al contenido en formato web ejecutando:
   ```bash
   mdbook serve
   ```
   Luego abre `http://localhost:3000` en tu navegador

2. **Leer offline**: Navega directamente por los archivos `.md` en el directorio `src/`

3. **Orden recomendado**: Sigue la secuencia de clases desde la 1 hasta la 15 para un aprendizaje progresivo

### Para desarrolladores

- **Requisitos previos**: Instalar mdBook
  ```bash
  cargo install mdbook
  ```

- **Generar el libro**:
  ```bash
  mdbook build
  ```

- **Ejemplos de código**: Los ejemplos prácticos en `src/examples/` están listos para ejecutar con Python 3 y las dependencias especificadas en `pyproject.toml`
  - Hay algunos ejemplos seteados con `uv` como herramienta de building

### Para contribuir

- Si encontrás errores o mejoras, no dudes en crear un issue o pull request
- Las correcciones y ampliaciones son bienvenidas

## Temas principales

### Computación

- Amazon EC2: instancias, tipos, configuración
- AMI y launch templates
- Auto Scaling Groups
- Elastic Load Balancing (ALB, NLB)

### Almacenamiento

- Amazon S3: buckets, políticas, versionado
- Amazon EBS: volúmenes y snapshots
- Amazon EFS: sistemas de archivos compartidos
- Amazon FSx: soluciones de archivos administradas

### Redes

- Amazon VPC: Virtual Private Cloud
- Subredes públicas y privadas
- Security Groups y NACLs
- VPN y Direct Connect

### Bases de Datos

- Amazon RDS: bases de datos relacionales administradas
- Amazon DynamoDB: base de datos NoSQL
- Amazon Aurora: base de datos compatible con MySQL/PostgreSQL
- Estrategias de backup y recuperación

### Contenedores y Serverless

- Amazon ECS y EKS: orquestación de contenedores
- AWS Lambda: funciones serverless
- API Gateway: gestión de APIs
- AWS Fargate: contenedores sin servidor

### Monitoreo y DevOps

- Amazon CloudWatch: métricas y logs
- AWS CloudTrail: auditoría de acciones
- AWS CodePipeline: integración continua
- AWS CodeBuild y CodeDeploy

### Seguridad

- IAM: usuarios, grupos, roles y políticas
- AWS KMS: gestión de claves
- AWS Secrets Manager
- Best practices de seguridad

### Arquitecturas

- Patrones de arquitectura bien diseñados
- Alta disponibilidad y escalabilidad
- Disaster Recovery y Business Continuity
- Optimización de costos

## Notas importantes

- Este material contiene las presentaciones del curso transcriptas a formato Markdown
- El contenido está actualizado con las prácticas y servicios de AWS vigentes en 2025
- Los PDFs originales se mantienen en `src/presentations/` para referencia
- Compatible con mdBook para una experiencia de lectura optimizada

---

**Docentes**: Fernando Lichtschein, Mora Villa Abrille  
**Materia**: Arquitecturas de Nube con AWS  
**Universidad**: Universidad Austral  
**Año**: 2025

