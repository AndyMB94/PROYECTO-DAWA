# 🏥 Sistema de Gestión Farmacéutica - FarmaSys

## 📋 Descripción

Sistema completo de gestión farmacéutica desarrollado con arquitectura full-stack que permite administrar laboratorios y medicamentos de manera eficiente. Implementa un CRUD completo con relaciones entre entidades y una interfaz moderna y responsiva.

## 🛠️ Tecnologías Utilizadas

### Backend
- **Node.js** - Entorno de ejecución
- **Express.js** - Framework web
- **Sequelize** - ORM para base de datos
- **MySQL** - Base de datos relacional
- **CORS** - Habilitación de peticiones cross-origin
- **dotenv** - Gestión de variables de entorno

### Frontend
- **Next.js 15** - Framework de React con App Router
- **TypeScript** - Tipado estático
- **Tailwind CSS** - Framework de estilos
- **Lucide React** - Librería de iconos
- **React Hooks** - Gestión de estado

## 🏗️ Arquitectura del Proyecto

```
SEMANA 15 - EXTRA/
├── backend-farmacia/           # Servidor Backend
│   ├── controllers/           # Lógica de negocio
│   │   ├── laboratorioController.js
│   │   └── medicamentoController.js
│   ├── models/               # Modelos de datos
│   │   ├── index.js         # Relaciones
│   │   ├── laboratorio.js
│   │   └── medicamento.js
│   ├── routes/              # Definición de rutas
│   │   ├── laboratorioRoutes.js
│   │   └── medicamentoRoutes.js
│   ├── .env                 # Variables de entorno
│   ├── db.js               # Configuración de BD
│   ├── index.js            # Servidor principal
│   └── package.json        # Dependencias
│
└── frontend-farmacia/          # Aplicación Frontend
    ├── src/
    │   ├── app/               # Páginas (App Router)
    │   │   ├── laboratorios/  # Gestión de laboratorios
    │   │   ├── medicamentos/  # Gestión de medicamentos
    │   │   └── page.tsx      # Página principal
    │   └── lib/
    │       └── api.js        # Funciones de API
    └── package.json          # Dependencias
```

## 🗄️ Modelo de Base de Datos

### Entidades Principales

**Laboratorio**
- `codLab` (PK) - Código único del laboratorio
- `razonSocial` - Nombre de la empresa
- `direccion` - Dirección física
- `telefono` - Número de contacto
- `email` - Correo electrónico
- `contacto` - Persona responsable

**Medicamento**
- `codMedicamento` (PK) - Código único del medicamento
- `descripcionMed` - Nombre y descripción
- `fechaFabricacion` - Fecha de fabricación
- `fechaVencimiento` - Fecha de vencimiento
- `presentacion` - Forma farmacéutica
- `stock` - Cantidad disponible
- `precioVentaUni` - Precio unitario
- `precioVentaPres` - Precio por presentación
- `codLab` (FK) - Referencia al laboratorio

### Relaciones
- **Laboratorio** 1:N **Medicamento** (Un laboratorio puede fabricar múltiples medicamentos)

## 🚀 Instalación y Configuración

### Prerequisitos
- Node.js (v18 o superior)
- MySQL Server
- npm o yarn

### 1. Clonar el repositorio
```bash
git clone https://github.com/AndyMB94/PROYECTO-DAWA.git
cd "SEMANA 15 - EXTRA"
```

### 2. Configurar Backend

```bash
cd backend-farmacia
npm install
```

Crear archivo `.env`:
```env
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=tu_password
DB_NAME=bd_farmacia
DB_PORT=3307
```

Crear base de datos:
```sql
CREATE DATABASE bd_farmacia;
```

### 3. Configurar Frontend

```bash
cd ../frontend-farmacia
npm install
```

## 🏃‍♂️ Ejecución

### Iniciar Backend (Puerto 3002)
```bash
cd backend-farmacia
node index.js
```

### Iniciar Frontend (Puerto 3000)
```bash
cd frontend-farmacia
npm run dev
```

## 📱 Funcionalidades

### Gestión de Laboratorios
- ✅ Listar todos los laboratorios
- ✅ Crear nuevo laboratorio
- ✅ Editar información del laboratorio
- ✅ Eliminar laboratorio
- ✅ Validación de campos obligatorios

### Gestión de Medicamentos
- ✅ Listar medicamentos con información del laboratorio
- ✅ Crear nuevo medicamento
- ✅ Editar información del medicamento
- ✅ Eliminar medicamento
- ✅ Indicadores visuales de stock
- ✅ Alertas de vencimiento
- ✅ Validación de fechas y precios

### Características Adicionales
- 🎨 Interfaz moderna y responsiva
- 🔄 Relaciones entre entidades
- ⚡ Carga dinámica de datos
- 🛡️ Validaciones en frontend y backend
- 📊 Indicadores visuales de estado

## 🌐 API Endpoints

### Laboratorios
- `GET /api/laboratorios` - Obtener todos los laboratorios
- `GET /api/laboratorios/:id` - Obtener laboratorio específico
- `POST /api/laboratorios` - Crear nuevo laboratorio
- `PUT /api/laboratorios/:id` - Actualizar laboratorio
- `DELETE /api/laboratorios/:id` - Eliminar laboratorio

### Medicamentos
- `GET /api/medicamentos` - Obtener todos los medicamentos
- `GET /api/medicamentos/:id` - Obtener medicamento específico
- `POST /api/medicamentos` - Crear nuevo medicamento
- `PUT /api/medicamentos/:id` - Actualizar medicamento
- `DELETE /api/medicamentos/:id` - Eliminar medicamento

## 🧪 Pruebas con Postman

### Ejemplo - Crear Laboratorio
```json
POST http://localhost:3002/api/laboratorios
Content-Type: application/json

{
  "razonSocial": "Laboratorios Bayer",
  "direccion": "Av. Principal 123",
  "telefono": "987654321",
  "email": "contacto@bayer.com",
  "contacto": "Dr. García"
}
```

### Ejemplo - Crear Medicamento
```json
POST http://localhost:3002/api/medicamentos
Content-Type: application/json

{
  "descripcionMed": "Paracetamol 500mg",
  "fechaFabricacion": "2024-01-15",
  "fechaVencimiento": "2026-01-15",
  "presentacion": "Tabletas",
  "stock": 100,
  "precioVentaUni": 2.50,
  "precioVentaPres": 25.00,
  "codLab": 1
}
```

## 📸 Capturas de Pantalla

El sistema incluye:
- 🏠 Dashboard principal con navegación intuitiva
- 📋 Listados con tarjetas informativas
- 📝 Formularios modernos con validación
- 🔔 Alertas y notificaciones
- 📱 Diseño completamente responsivo

## 👨‍💻 Desarrollo

### Estructura de Desarrollo
- **MVC** en backend (Modelo-Vista-Controlador)
- **Componentes funcionales** en React
- **Hooks** para gestión de estado
- **API REST** para comunicación
- **Responsive Design** con Tailwind CSS

### Buenas Prácticas Implementadas
- ✅ Separación de responsabilidades
- ✅ Validación de datos
- ✅ Manejo de errores
- ✅ Código modular y reutilizable
- ✅ Nomenclatura consistente

## 🔧 Configuración de Desarrollo

### Variables de Entorno Requeridas
```env
DB_HOST=localhost          # Host de la base de datos
DB_USER=root              # Usuario de MySQL
DB_PASSWORD=tu_password   # Contraseña de MySQL
DB_NAME=bd_farmacia      # Nombre de la base de datos
DB_PORT=3307             # Puerto de MySQL
```

## 📝 Licencia

Este proyecto fue desarrollado como parte del curso de **Desarrollo de Aplicaciones Web Avanzado** - Laboratorio 15.

## 👥 Contribución

Para contribuir al proyecto:
1. Fork el repositorio
2. Crea una rama para tu feature (`git checkout -b feature/nueva-funcionalidad`)
3. Commit tus cambios (`git commit -m 'Agregar nueva funcionalidad'`)
4. Push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Abre un Pull Request

## 📞 Contacto

Si tienes preguntas o sugerencias sobre el proyecto, no dudes en contactarme.

---

**Desarrollado con ❤️ usando Node.js, Next.js y mucho café ☕**