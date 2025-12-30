# hiberus_test

# 📦 Modelo de Órdenes y Productos – Symfony + Doctrine ORM

Este repositorio contiene la definición del **modelo de datos** para un sistema básico de **gestión de pedidos**, desarrollado en **Symfony** utilizando **Doctrine ORM**.

El modelo está orientado a representar:
- Órdenes de clientes
- Productos disponibles
- Ítems asociados a cada orden

---

## 🧩 Entidades del Sistema

El sistema está compuesto por **tres entidades principales**:

1. **CustomerOrder** → Representa una orden de compra
2. **OrderItem** → Representa los productos incluidos en una orden
3. **Producto** → Representa los productos disponibles en el sistema

---

## 📘 CustomerOrder (Orden de Cliente)

Entidad que representa una **orden de compra** realizada por un cliente.

### Campos principales
| Campo | Tipo | Descripción |
|------|------|-------------|
| `id` | int | Identificador único |
| `total` | decimal | Total monetario de la orden |
| `status` | string | Estado de la orden (pendiente, pagado) |
| `createdAt` | DateTimeImmutable | Fecha de creación |


## 📙 OrderItem (Detalle de Orden)

Entidad intermedia que representa **cada producto dentro de una orden**.

### Campos principales
| Campo | Tipo | Descripción |
|------|------|-------------|
| `id` | int | Identificador único |
| `cantidad` | int | Cantidad del producto |
| `price_uni` | decimal | Precio unitario al momento de la compra |
| `producto` | ManyToOne | Producto asociado |
| `order_item` | ManyToOne | Orden asociada |

## 📕 Producto

Entidad que representa los **productos disponibles** para la venta.

### Campos principales
| Campo | Tipo | Descripción |
|------|------|-------------|
| `id` | int | Identificador único |
| `name` | string | Nombre del producto |
| `description` | string | Descripción |
| `price` | decimal | Precio actual |
| `stock` | int | Stock disponible |

# 🛒 Sistema de Órdenes y Productos  
Symfony + React+ Doctrine ORM + Docker Compose
Este proyecto implementa un **sistema básico de gestión de órdenes y productos**, desarrollado con **Symfony**, **React**, **Doctrine ORM** y **MySQL**, ejecutado en un entorno **Dockerizado**.

## 📋 Requisitos Previos

Asegúrate de tener instalado en tu máquina:
- Docker 
- Docker Compose
- Git

---
### 1️⃣ Levantar los contenedores
docker-compose up

### 2️⃣ Migracion de data
docker compose exec backend sh
php bin/console make:migration
php bin/console doctrine:migrations:migrate --no-interaction

### 3️⃣ Migracion de data para test
docker compose exec backend sh
php bin/console doctrine:database:create --env=test
php bin/console doctrine:migrations:migrate --env=test -n

### 4️⃣ Ejecutar Pruebas Unitarias
php bin/phpunit

### 5️⃣Generar reporte
php bin/phpunit --testdox-html var/log/phpunit-report.html

### 6️⃣ Bajar contenedores
docker compose down

### Coleccion de Postamn
https://.postman.co/workspace/My-Workspace~47fc3954-2b3f-4a29-84dc-f26b2d69eb0b/collection/43667179-7bccef75-eed3-43a2-874a-01c13793f2ae?action=share&creator=43667179



