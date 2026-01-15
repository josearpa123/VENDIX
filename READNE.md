🧾 Sistema de Gestión de Ventas – Plataforma SaaS

Plataforma SaaS de gestión de ventas orientada a pequeños y medianos negocios en Colombia.
El sistema centraliza ventas, inventario, clientes, pagos electrónicos y facturación, bajo un enfoque multi-negocio (multi-tenant) y de bajo costo de infraestructura.

Este repositorio contiene backend y frontend, organizados por carpetas y preparados para desarrollo local con Docker antes del despliegue a producción.

🎯 Objetivo del proyecto

Permitir a distintos comercios:

Registrar ventas físicas y digitales

Controlar inventario en tiempo real

Aceptar pagos electrónicos

Prepararse para facturación electrónica DIAN

Consultar reportes y métricas clave

Operar desde una aplicación web responsive

El proyecto inicia como MVP y evoluciona de forma modular.

🧠 Enfoque técnico
Capa	Tecnología
Backend	Laravel (PHP 8.2+)
Frontend	React (Vite)
Autenticación	Laravel Sanctum
Base de datos	MySQL / PostgreSQL
Infraestructura local	Docker + Docker Compose
Producción	VPS económico (Linux)
Arquitectura	API REST + Web SPA
Multi-negocio	Single DB + tenant_id
🧩 Segmentos de negocio objetivo

Ferreterías

Tiendas de ropa y calzado

Minimercados / tiendas de barrio

Emprendimientos y pequeños negocios

📁 Estructura del repositorio
/
├── backend/                 # API Laravel
│   ├── app/
│   ├── database/
│   ├── routes/
│   ├── storage/
│   ├── .env.example
│   └── artisan
│
├── frontend/                # Web React (POS + Admin)
│   ├── src/
│   ├── public/
│   ├── .env.example
│   └── vite.config.js
│
├── docker/                  # Configuración Docker
│   ├── nginx/
│   ├── php/
│   └── mysql/
│
├── docker-compose.yml       # Orquestación local
├── README.md

🔐 Autenticación y roles

Autenticación por Bearer Token

Roles:

admin → administrador del comercio

seller → vendedor

Cada usuario pertenece a un comercio (tenant)

🧱 Multi-negocio (Multi-tenant)

Estrategia: Single Database + tenant_id

Middleware asegura aislamiento por comercio

Preparado para escalar a múltiples esquemas o servicios

🛒 Módulos del sistema
📦 Inventario

Productos por unidad, peso o medida

Variantes (talla, color)

Movimientos de inventario

Alertas de stock bajo

🧾 Ventas (POS)

Registro rápido de ventas

Carrito de productos

Descuentos

Ventas mixtas (efectivo + electrónico)

💳 Pagos electrónicos

Integración con pasarelas colombianas

Estados de pago automáticos

Webhooks y conciliación

Asociación pago ↔ venta

🧾 Facturación

Documento interno (MVP)

Documento equivalente

Preparado para integración DIAN

📊 Reportes

Ventas diarias y mensuales

Productos más vendidos

Clientes frecuentes

Resumen de caja

🐳 Desarrollo local con Docker (obligatorio)

Todo el proyecto se ejecuta localmente con Docker para asegurar:

Entornos idénticos entre desarrolladores

Evitar problemas de versiones

Facilidad de despliegue posterior a VPS

Requisitos

Docker

Docker Compose

🚀 Levantar el proyecto localmente
1️⃣ Clonar repositorio
git clone https://github.com/tu-org/ventas-saas.git
cd ventas-saas

2️⃣ Variables de entorno
cp backend/.env.example backend/.env
cp frontend/.env.example frontend/.env


Configurar las variables según entorno local.

3️⃣ Levantar contenedores
docker-compose up -d --build


Servicios levantados:

Servicio	URL
Backend API	http://localhost:8000

Frontend Web	http://localhost:5173

Base de datos	localhost:3306
4️⃣ Migraciones (solo primera vez)
docker-compose exec backend php artisan migrate

🧪 Desarrollo

El frontend consume la API vía VITE_API_URL

Autenticación vía tokens

CORS habilitado para entorno local

Hot reload activo en frontend

📦 Flujo recomendado de trabajo
Docker local
   ↓
Validación MVP
   ↓
Optimización
   ↓
Deploy a VPS (producción)

🔒 Seguridad y buenas prácticas

Validación estricta de datos

Control de acceso por roles

Idempotencia en pagos

Registro de eventos críticos

Separación frontend / backend

📌 Estado del proyecto

🟡 En desarrollo – MVP
Enfoque actual:

Autenticación

Multi-tenant

Ventas

Inventario

Pagos electrónicos

📄 Licencia

Proyecto privado.
Licenciamiento comercial a definir.

🤝 Equipo

Backend: Laravel / PHP

Frontend: React

Enfoque: SaaS ligero, escalable y accesible

🛠 Próximos pasos

Dockerización completa de servicios

POS optimizado para ventas rápidas

Integración pasarela de pagos (Wompi)

Facturación electrónica DIAN (fase 2)
