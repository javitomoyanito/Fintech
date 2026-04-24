Sistema de Procesamiento de Transacciones Fintech (Audit-Ready)
Descripción del Proyecto
Este sistema ha sido diseñado para gestionar el ciclo de vida completo de las transacciones de pago de una entidad financiera. Dado que la integridad de los datos es crítica, el sistema se centra en tres pilares fundamentales:

Inmutabilidad: Registro de transacciones mediante un modelo de "solo lectura/inserción" para evitar alteraciones.

Cumplimiento ACID: Garantía de atomicidad, consistencia, aislamiento y durabilidad en cada operación.

Auditoría Histórica: Capacidad de reconstruir estados financieros en cualquier punto del tiempo para reportes regulatorios mensuales.

Arquitectura Seleccionada: Lakehouse
Se ha optado por una arquitectura Data Lakehouse, la cual combina la flexibilidad y el bajo costo de un Data Lake con las capacidades de gestión de datos y transacciones ACID de un Data Warehouse.

Esta arquitectura permite:

-Capa Bronce (Raw): Almacenamiento inmutable de los logs de transacciones originales.

-Capa Plata (Cleansed): Datos validados y tipados con soporte para viajes en el tiempo (time travel).

-Capa Oro (Curated): Agregaciones optimizadas para los reportes regulatorios mensuales.

Requisitos y Configuración del Entorno Técnico
Para levantar y desarrollar en este proyecto, se requieren las siguientes herramientas:

Entorno de Ejecución:

Docker & Docker Compose: Para la orquestación de servicios y contenedores.

Python 3.10+: Lenguaje principal para el procesamiento de datos.

Almacenamiento y Procesamiento:

PostgreSQL: Utilizado para metadatos o como fuente transaccional inicial.

Apache Spark / Delta Lake: Motor para el procesamiento distribuido y la gestión de tablas con soporte ACID.

MinIO / AWS S3: Almacenamiento de objetos para el Data Lake.

Control de Versiones:

Git: Para el seguimiento del código y scripts de infraestructura.

Instrucciones de Instalación
Clonar el repositorio:

git clone https://github.com/usuario/fintech-lakehouse-system.git
cd fintech-lakehouse-system

Configurar variables de entorno:
Crea un archivo .env basado en el ejemplo proporcionado:
    cp .env.example .env

Levantar la infraestructura con Docker:
    docker-compose up -d

Instalar dependencias de Python (entorno virtual):
    python -m venv venv
    source venv/bin/activate 
    pip install -r requirements.txt

Ejecutar migraciones iniciales:
    python manage.py setup_lakehouse


Estructura del Repositorio
├── .docker/
├── documentos/
├── scripts/
├── src/
│   ├── ingestion/
│   ├── procesamiento/
│   ├── reportes/
│   └── utilidades/
├── pruebas/
├── docker-compose.yml
├── requerimientos.txt
└── README.md           