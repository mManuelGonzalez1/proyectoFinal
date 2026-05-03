# Proyecto Final Manuel - Panel Técnico Overhaul Service Corp

## 📋 Descripción del Proyecto

Sistema web de gestión de servicios técnicos para **Overhaul Service Corp**, diseñado específicamente para técnicos de mantenimiento. La aplicación permite visualizar, organizar y ejecutar órdenes de servicio para equipos de manutención (montacargas).

**Usuario de prueba:** Manuel García - Técnico de Mantenimiento Nivel 2

---

## ✨ Características Principales

### 🏠 Panel Principal (Index)
- **Dashboard con resumen operativo**: Vista general del día
- **Indicadores de rendimiento**: 
  - Servicios programados para hoy
  - Servicios pendientes
  - Horas laboradas
  - Barra de progreso de jornada
- **Siguiente servicio asignado**: Detalle rápido del próximo servicio
- **Servicios pendientes**: Listado de tareas pendientes

### 📅 Agenda (Agenda.html)
- **Navegación por períodos**: Hoy, Mañana, Pendientes
- **Tarjetas de servicio**: Información condensada de cada servicio
  - Tipo de servicio (Correctivo, Preventivo, Diagnóstico)
  - Ubicación del cliente
  - Equipo asignado
  - Hora programada
- **Colores por estado**:
  - 🔴 Rojo: Correctivo/Urgente
  - 🔵 Azul: Preventivo
  - 🟢 Verde: Diagnóstico

### 👤 Perfil Técnico (Perfil.html)
- **Información del técnico**: Nombre, foto, cargo
- **Rendimiento mensual**: 
  - Servicios completados
  - Eficiencia en tiempos
- **Configuración personal**:
  - Editar datos personales
  - Cambiar contraseña
  - Preferencias de comunicación
  - Notificaciones (toggle)
- **Cerrar sesión**

### 🔧 Detalles del Servicio (Detalle-servicio.html)
- **Información del cliente**: Nombre, ubicación, contacto
- **Datos técnicos del equipo**:
  - Marca y modelo
  - Serial del equipo
  - Horómetro
  - Tipo de combustible
- **Reporte del cliente**: Descripción del problema
- **Acceso a hoja de trabajo**

### 📝 Hoja de Trabajo (Hoja-trabajo.html)
Formulario interactivo para registrar la ejecución del servicio con:
- **Información General**:
  - Tipo de servicio
  - Horómetro actual
- **Checklist de Inspección**:
  - Estado de ruedas
  - Nivel de aceite
  - Nivel de agua de batería
- **Repuestos Utilizados**: Tabla dinámica con descripción y cantidad
- **Observaciones**: Campo de texto libre para notas técnicas
- **Firma de Conformidad**: Espacio para captura de firma (Canvas JS)
- **Nombre del receptor**: Campo de entrada

---

## 🗂️ Estructura del Proyecto

```
ProyectofinalManuel/
├── index.html                  # Panel principal
├── agenda.html                 # Calendario de servicios
├── perfil.html                 # Perfil del técnico
├── detalle-servicio.html       # Detalle de orden de servicio
├── hoja-trabajo.html           # Formulario de ejecución de servicio
├── css/
│   └── styles.css              # Estilos compilados
├── scss/
│   └── styles.scss             # Fuente de estilos (SCSS)
└── README.md                   # Este archivo
```

---

## 🎨 Sistema de Estilos

### Arquitectura SCSS
El proyecto utiliza **SCSS** como preprocesador CSS con la siguiente organización:

#### 1️⃣ Variables y Configuración Base
```scss
// Colores principales
$navy-dark:    #141f35;   // Azul oscuro (primario)
$brand-red:    #ca2418;   // Rojo (botones, alertas)
$warning-gold: #e9b41a;   // Oro (acentos)
$bg-light:     #f4f6f9;   // Fondo claro

// Tipografía
$font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
$border-rad:  12px;
$transition:  all 0.3s ease;
```

#### 2️⃣ Mixins Reutilizables
- `@mixin shadow-sm`: Sombra sutil (cards)
- `@mixin shadow-md`: Sombra media (navbar, footer)
- `@mixin flex-center`: Flexbox centrado

#### 3️⃣ Componentes CSS

| Componente | Clase | Uso |
|-----------|-------|-----|
| Navbar | `.navbar` | Encabezado pegajoso |
| Cards | `.card-custom` | Contenedores principales |
| Botones | `.btn-brand` | Botones de acción |
| Footer | `.footer` | Navegación inferior móvil |
| Progress | `.progress-custom` | Barras de progreso |

### Paleta de Colores

| Color | Hex | Uso |
|-------|-----|-----|
| Navy Dark | #141f35 | Texto, fondos, bordes principales |
| Brand Red | #ca2418 | Botones, alertas urgentes |
| Warning Gold | #e9b41a | Acentos, progreso, hover |
| Light BG | #f4f6f9 | Fondo general |
| White | #ffffff | Fondos de cards |

### Variantes de Bordes (Status)
```css
.card-custom.border-status-danger  { border-left: 6px solid #ca2418; } /* Urgente */
.card-custom.border-status-warning { border-left: 6px solid #e9b41a; } /* Preventivo */
.card-custom.border-status-navy    { border-left: 6px solid #141f35; } /* Normal */
```

---

## 📦 Dependencias Externas

### CDN Utilizadas

#### Bootstrap 5.3.0
```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
```
**Uso**: Grid, componentes, utilidades de espaciado y flexbox

#### Bootstrap Icons 1.11.1
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.1/font/bootstrap-icons.css">
```
**Uso**: Iconografía (herramientas, calendario, personas, etc.)

#### Avatars Dinámicos
```
https://ui-avatars.com/api/?name=Manuel+G&background=141f35&color=fff&size=100
```
**Uso**: Fotos de perfil personalizadas

---

## 🚀 Guía de Desarrollo

### Requisitos
- Navegador moderno (Chrome, Firefox, Edge, Safari)
- Editor de código (VS Code recomendado)
- Live Server o similar para desarrollar localmente

### Flujo de Navegación

```
index.html (Panel Principal)
    ↓
├─→ agenda.html (Ver agenda de servicios)
│       ↓
│   detalle-servicio.html (Ver detalles)
│       ↓
│   hoja-trabajo.html (Ejecutar servicio)
│
└─→ perfil.html (Datos del técnico)
```

### Estructura HTML Semántica

Cada página utiliza elementos semánticos:
- `<header>`: Barra de navegación
- `<main>`: Contenido principal
- `<section>`: Agrupación lógica de contenido
- `<article>`: Tarjetas de servicio
- `<footer>`: Navegación móvil

### Responsividad

#### Breakpoints Bootstrap utilizados:
- `col-12`: Ancho completo (móvil)
- `col-6 col-md-4`: Media pantalla en móvil, 1/3 en tablet
- `d-none d-sm-inline`: Oculto en móvil
- `d-lg-none`: Oculto en pantalla grande

#### Clases Personalizadas:
- `.navbar-expand-lg`: Navbar adaptable
- `.container-fluid`: Ancho 100%
- `.py-4`, `.mb-4`: Utilidades de espaciado

---

## 🔑 Atributos de Accesibilidad (A11y)

El proyecto implementa estándares WCAG 2.1:

### ARIA Roles y Atributos
```html
<!-- Tabs de navegación -->
<ul role="tablist">
  <li role="presentation">
    <a role="tab" aria-selected="true" aria-label="Ver servicios de hoy">
  </li>
</ul>

<!-- Elementos decorativos -->
<i class="bi bi-truck" aria-hidden="true"></i>

<!-- Controles -->
<input type="checkbox" id="notifications-switch" aria-label="Activar notificaciones">
```

### Labels y Placeholders
```html
<label for="serviceType">Tipo de Servicio</label>
<input id="serviceType" name="serviceType" placeholder="Ej: 4530">
```

---

## 📐 Componentes Principales

### Navbar Industrial
- Logo + Título del sitio
- Información del usuario (nombre + avatar)
- Background navy dark
- Sticky (pegajoso)

### Card Custom
```scss
.card-custom {
  background: white;
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
  transition: all 0.3s ease;
}
```

### Botón Brand
```scss
.btn-brand {
  background-color: #ca2418;
  text-transform: uppercase;
  letter-spacing: 1px;
  transition: transform 0.3s ease;
  
  &:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 15px rgba(0, 0, 0, 0.1);
  }
}
```

### Footer Móvil
Navegación de 3 opciones visible solo en pantallas pequeñas (`d-lg-none`):
- Inicio
- Agenda
- Perfil

---

## 🔄 Estados de los Servicios

| Tipo | Color | Icono | Uso |
|------|-------|-------|-----|
| Correctivo | Rojo (#ca2418) | 🔧 | Reparación de fallas |
| Preventivo | Primario (#141f35) | 📋 | Mantenimiento programado |
| Diagnóstico | Éxito Verde | 🔍 | Evaluación del equipo |

---

## 📱 Información de Dispositivos

### Tamaños Soportados
- 📱 Móvil: 320px - 576px
- 📱 Tablet: 577px - 768px
- 💻 Desktop: 769px+

### Optimizaciones Móviles
- Footer pegajoso con navegación principal
- Tarjetas apiladas verticalmente
- Padding adaptativo
- Tamaño de fuente responsive

---

## 🔐 Datos de Prueba

### Técnico Principal
- **Nombre**: Manuel García
- **Cargo**: Técnico de Mantenimiento Nivel 2
- **Rendimiento (Abril)**:
  - Servicios completados: 42
  - Eficiencia en tiempos: 98%

### Clientes de Ejemplo
- **Alkosto** - Planta 2, Zona de Descargue
- **Fresenius Medical Care**
- **Sika**

### Equipos Ejemplo
- **Toyota 8FGCU25** (Montacargas)
- **Crown RC 5500** (Montacargas)

---

## ⚙️ Configuración Técnica

### Meta Tags
```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Panel Técnico - Overhaul Service</title>
```

### Idioma
- Página en español (`lang="es"`)
- Textos con acentos y caracteres especiales

### Performance
- CSS compilado (minificado en producción)
- JS Bundle de Bootstrap incluido
- Imágenes externas desde CDN

---

## 🎯 Próximas Mejoras Sugeridas

- [ ] Implementar Canvas.js para captura de firmas
- [ ] Agregar JavaScript para interactividad de tabs
- [ ] Validación de formularios en hoja-trabajo.html
- [ ] Backend de almacenamiento de datos
- [ ] Autenticación de usuario
- [ ] Reportes y estadísticas avanzadas
- [ ] Notificaciones en tiempo real
- [ ] Offline-first con Service Workers

---

## 👨‍💻 Notas de Desarrollo

### Convenciones de Nomenclatura CSS
```scss
// BEM Modificado con SCSS Nesting
.component-name {          // Bloque
  &__element {             // Elemento
    color: blue;
  }
  
  &--modifier {            // Modificador
    color: red;
  }
}
```

### Espacios en Blanco
- Indentación: 4 espacios
- Separación entre secciones: comentarios con `=====`
- Máximo 80 caracteres de ancho recomendado

### Comentarios
```scss
/* ==========================================================================
   Título de Sección
   ========================================================================== */
```

---

## 📄 Licencia

Proyecto propietario de Manuel García para Overhaul Service Corp.

---

## 📞 Contacto

**Desarrollador**: Manuel García  
**Empresa**: Overhaul Service Corp  
**Fecha de Creación**: 2026

---

## 🔗 Referencias Útiles

- [Bootstrap 5 Documentation](https://getbootstrap.com/docs/5.3/)
- [Bootstrap Icons](https://icons.getbootstrap.com/)
- [SCSS Documentation](https://sass-lang.com/documentation)
- [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)
- [MDN Web Docs](https://developer.mozilla.org/)

---

**Último actualizado**: Mayo 3, 2026  
**Versión**: 1.0.0
