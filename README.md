# Plataforma E-Commerce — Aplicación Web Administrativa

Este repositorio contiene la **Aplicación Web Administrativa** desarrollada para la gestión del comercio electrónico, permitiendo al personal administrativo controlar productos, categorías, pedidos y asignación de entregas.

---
- **Integrantes del Equipo:**
  - José Armando Abarca Sánchez[cite: 1]
  - Isaac Alejandro Padrón Becerra[cite: 1]
  - Jorge Alexis Ramos Equihua[cite: 1]
  - Leticia Guadalupe[cite: 1]

---

## Tecnologías Utilizadas
- **Framework Frontend:** Angular (TypeScript)[cite: 1]
- **Lógica de Estado y Peticiones:** RxJS + `HttpClientModule`
- **Estilos:** CSS3 / Bootstrap / Tailwind CSS
- **Arquitectura:** Cliente-Servidor desacoplada mediante consumo de API REST Backend[cite: 5, 10]
---

## Perfil de Usuario y Requerimientos Cubiertos

### Perfil: Administrador[cite: 7]
Es el usuario encargado de gestionar la operación del comercio desde la consola web[cite: 7].

#### Requerimientos Funcionales Implementados (RF-ADM)[cite: 9]:
- **RF-ADM-01 (Autenticación Administrativa):** Acceso seguro mediante credenciales de perfil elevado[cite: 9].
- **RF-ADM-03 (Gestión de Categorías):** Crear, editar, listar y desactivar categorías de productos[cite: 9].
- **RF-ADM-04 (Gestión de Productos):** Alta de productos, modificación de precios, imágenes, descripciones y control de stock[cite: 9].
- **RF-ADM-05 (Consulta General de Pedidos):** Visualización de pedidos registrados filtrados por estado, fecha o cliente[cite: 9].
- **RF-ADM-06 (Asignación de Pedidos):** Asignación manual de pedidos a repartidores disponibles[cite: 9].
- **RF-ADM-07 (Control Manual de Estados):** Modificación del estado de los pedidos ante contingencias o cancelaciones[cite: 9].
- **RF-ADM-08 (Reportes e Información de Ventas):** Dashboard e informes de ventas y flujo operacional[cite: 10].

#### Requerimientos No Funcionales (RNF-ADM)[cite: 10]:
- **RNF-ADM-01:** Compatibilidad multiplataforma en navegadores (Chrome, Firefox, Edge, Safari)[cite: 10].
- **RNF-ADM-02:** Usabilidad operativa con mensajes de confirmación/error tras cada acción[cite: 10].
- **RNF-ADM-03:** Control de acceso estricto mediante tokens JWT para impedir accesos no autorizados[cite: 10].

---

## 🔗 Identificación del Backend y API Centralizada

La consola web se comunica con la API Backend mediante servicios centralizados de Angular[cite: 5, 10]:

- **Tipo de API:** RESTful API sobre protocolo HTTPS[cite: 5, 10]
- **Ubicación del Servicio en Código:** `src/app/services/api.service.ts`
- **Configuración de variables de entorno:** `src/environments/environment.ts`
- **URL Base (Desarrollo):** `http://localhost:3000/api`
- **Endpoints principales consumidos por la Web:**
  - `POST /api/auth/login` — Autenticación de administrador y recepción de token JWT[cite: 9, 10].
  - `GET / POST / PUT / DELETE /api/categorias` — CRUD de categorías[cite: 9].
  - `GET / POST / PUT / DELETE /api/productos` — CRUD y actualización de stock de productos[cite: 9].
  - `GET /api/pedidos` — Listado y filtrado de pedidos[cite: 9].
  - `PUT /api/pedidos/:id/asignar` — Asignación de pedido a un repartidor[cite: 9].
  - `PUT /api/pedidos/:id/estado` — Modificación manual de estados del pedido[cite: 9].
  - `GET /api/reportes/ventas` — Obtención de métricas e informes operacionales[cite: 10].

---

## 📁 Estructura del Proyecto

```text
proyecto-web/
├── src/
│   ├── app/
│   │   ├── components/         # Módulos de administración (Productos, Pedidos, Categorías)
│   │   ├── models/             # Interfaces de datos TypeScript (Producto, Pedido, Usuario)
│   │   ├── services/           # ApiService con HttpClient para consumo del Backend
│   │   ├── guards/             # Protección de rutas para el perfil Administrador
│   │   ├── app.component.ts
│   │   └── app.routes.ts       # Configuración de rutas administrativas
│   ├── assets/                 # Logotipos y recursos estáticos
│   ├── environments/           # URLs de conexión al Backend
│   └── main.ts
├── angular.json
├── package.json
└── README.md
