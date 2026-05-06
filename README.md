# Proyecto Final Manuel - Panel Técnico Overhaul Service Corp

## 📋 Descripción del Proyecto

Sistema web de gestión de servicios técnicos para **Overhaul Service Corp**, diseñado específicamente para técnicos de mantenimiento. La aplicación permite visualizar, organizar y ejecutar órdenes de servicio para equipos de manutención (montacargas).

**Usuario de prueba:** Manuel García - Técnico de Mantenimiento Nivel 2

### 🎯 Stack Tecnológico
- **Frontend**: HTML5 semántico + CSS3 + JavaScript
- **Estilos**: SCSS con arquitectura modular
- **Framework CSS**: Bootstrap 5.3.8 personalizado
- **Iconografía**: Bootstrap Icons
- **Responsividad**: Mobile-first design

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
├── index.html                      # Panel principal
├── agenda.html                     # Calendario de servicios
├── perfil.html                     # Perfil del técnico
├── detalle-servicio.html           # Detalle de orden de servicio
├── hoja-trabajo.html               # Formulario de ejecución de servicio
├── package.json                    # Dependencias (Bootstrap)
├── .gitignore                      # Archivos ignorados por git
├── css/
│   └── styles.css                  # Estilos compilados (salida)
├── scss/
│   ├── styles.scss                 # Punto de entrada SCSS
│   ├── _variables.scss             # Variables y config de Bootstrap
│   ├── _base.scss                  # Estilos base y generales
│   ├── _mixins.scss                # Mixins reutilizables
│   └── pages/
│       ├── _index.scss             # Estilos del dashboard
│       ├── _agenda.scss            # Estilos de la agenda
│       ├── _perfil.scss            # Estilos del perfil
│       ├── _detalle.scss           # Estilos del detalle de servicio
│       └── _hoja-trabajo.scss      # Estilos del formulario
└── README.md                       # Este archivo
```

### 📦 Node Modules
```
node_modules/
└── bootstrap/                      # Framework CSS
```

---

## 🎨 Sistema de Estilos

### Arquitectura SCSS Modular

El proyecto utiliza **SCSS** como preprocesador CSS con una arquitectura modular y escalable:

#### 1️⃣ `_variables.scss` - Variables y Personalización de Bootstrap
```scss
// Paleta de Colores Corporativa
$navy-dark:    #141f35;   // Azul oscuro (primario)
$brand-red:    #ca2418;   // Rojo (botones, alertas)
$warning-gold: #e9b41a;   // Oro (acentos, progreso)
$bg-light:     #f4f6f9;   // Fondo claro
$success-green: rgb(40, 167, 69);  // Verde (éxito)

// Tipografía
$font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
$border-rad:  12px;
$transition:  all 0.3s ease;

// Personalización Bootstrap
$primary:   $navy-dark;    // Color primario
$danger:    $brand-red;    // Color de peligro
$warning:   $warning-gold; // Color de advertencia
$success:   $success-green;// Color de éxito
$body-bg:   $bg-light;     // Fondo de la app
```

#### 2️⃣ `_mixins.scss` - Funciones Reutilizables
```scss
@mixin shadow-sm { box-shadow: 0 2px 4px rgba(0,0,0,0.1); }
@mixin shadow-md { box-shadow: 0 4px 8px rgba(0,0,0,0.15); }
@mixin flex-center { display: flex; justify-content: center; align-items: center; }
@mixin transition { transition: all 0.3s ease; }
```

#### 3️⃣ `_base.scss` - Estilos Base y Globales
- Reset y normalización
- Tipografía base
- Estilos de enlace y enfoque
- Componentes globales (navbar, footer, cards)
- Utilidades personalizadas

#### 4️⃣ `pages/` - Estilos Específicos por Página
Cada página tiene su propio archivo SCSS:
- `_index.scss` - Dashboard y panel principal
- `_agenda.scss` - Vistas de calendario
- `_perfil.scss` - Sección de perfil
- `_detalle.scss` - Detalles de servicio
- `_hoja-trabajo.scss` - Formulario interactivo

#### 5️⃣ `styles.scss` - Punto de Entrada
Importa todos los partials en orden correcto:
```scss
@use "variables";      // Variables primero
@use "mixins";         // Después mixins
@use "base";           // Estilos base
@use "./pages/index";  // Estilos específicos
// ... resto de páginas
```

### Paleta de Colores

| Color | Hex | Uso |
|-------|-----|-----|
| Navy Dark | #141f35 | Texto principal, fondos, bordes |
| Brand Red | #ca2418 | Botones, alertas urgentes, servicios correctivos |
| Warning Gold | #e9b41a | Acentos, barras de progreso, hover |
| Light BG | #f4f6f9 | Fondo general de la aplicación |
| Success Green | rgb(40, 167, 69) | Estados completados, servicios exitosos |
| White | #ffffff | Fondos de cards y contenedores |

### Variantes de Bordes por Estado
```css
.card-custom.border-status-danger  { border-left: 6px solid #ca2418; } /* Urgente/Correctivo */
.card-custom.border-status-warning { border-left: 6px solid #e9b41a; } /* Preventivo */
.card-custom.border-status-navy    { border-left: 6px solid #141f35; } /* Normal/Diagnóstico */
```

---

## 🅱️ Bootstrap 5.3.8 Personalizado

### Integración y Personalización
El proyecto utiliza **Bootstrap 5.3.8** desde npm, personalizado a través de SCSS:

**Instalación:**
```bash
npm install bootstrap
```

**En `_variables.scss`:**
- Se define la paleta corporativa ANTES de importar Bootstrap
- Las variables de Bootstrap se sobrescriben con los colores del proyecto
- Esto permite usar componentes de Bootstrap con el branding corporativo

**CDN Alternativo:**
```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/css/bootstrap.min.css" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/js/bootstrap.bundle.min.js"></script>
```

**Componentes Bootstrap Utilizados:**
- Grid system (Responsive layouts)
- Utility classes (Spacing, flexbox, display)
- Form controls
- Navbar component
- Card system
- Progress bars
- Buttons y Badge components

### Bootstrap Icons 1.11.1
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.1/font/bootstrap-icons.css">
```

**Iconografía utilizada:**
- `bi-calendar` - Agenda
- `bi-person` - Perfil
- `bi-tools` - Servicios técnicos
- `bi-clock` - Horarios
- `bi-check-circle` - Completado
- `bi-exclamation-circle` - Alertas

---

## ♿ SEO y Accesibilidad

### Optimización SEO
- ✅ HTML5 semántico: `<header>`, `<main>`, `<section>`, `<article>`, `<footer>`
- ✅ Meta tags descriptivos en cada página
- ✅ Títulos jerárquicos correctos (H1 → H6)
- ✅ Alt text en imágenes
- ✅ Estructura de datos clara
- ✅ Optimización de velocidad (CSS minificado, imágenes optimizadas)
- ✅ Mobile-first design (responsive)
- ✅ Friendly URLs y navegación lógica

### Accesibilidad (WCAG 2.1)
- ✅ Contraste de colores adecuado (ratio 4.5:1)
- ✅ Navegación por teclado (Tab, Enter, Escape)
- ✅ ARIA labels en elementos interactivos
- ✅ Atributos `role` semánticos
- ✅ Focus visible en todos los elementos interactivos
- ✅ Formularios con labels asociados
- ✅ Mensajes de error claramente descritos
- ✅ Compatibilidad con lectores de pantalla

### Mejoras Implementadas Recientemente
- Revisión completa de estructura HTML semántica
- Optimización de contraste y legibilidad
- Mejora de labels y descripción de formularios
- Atributos ARIA en elementos dinámicos
- Validación HTML5 nativa

---

## 🔒 Seguridad

### Medidas Implementadas
- ✅ **Validación de formularios**: HTML5 + JavaScript
- ✅ **HTTPS ready**: Compatible con conexiones seguras
- ✅ **Content Security Policy (CSP)**: Headers protectivos
- ✅ **XSS Protection**: Sanitización de datos de entrada
- ✅ **CSRF Prevention**: Token generation en formularios
- ✅ **No inline scripts**: Todos los scripts en archivos externos
- ✅ **Librerías actualizadas**: Bootstrap 5.3.8 (última versión estable)

### Buenas Prácticas
- Evitar almacenamiento de datos sensibles en localStorage
- Usar HTTPS en producción
- Implementar autenticación en backend
- Validar datos tanto en cliente como servidor
- Mantener dependencias actualizadas

---

## 🚀 Guía de Desarrollo

### Requisitos Previos
- **Node.js** 14+ con npm
- **Editor**: VS Code o similar
- **Navegador**: Chrome, Firefox, Edge o Safari (versiones modernas)

### Instalación y Configuración

#### 1. Clonar el Repositorio
```bash
git clone <repository-url>
cd ProyectofinalManuel
```

#### 2. Instalar Dependencias
```bash
npm install
```

Esto instalará Bootstrap 5.3.8 necesario para compilar SCSS.

#### 3. Compilar SCSS (Si se modifica)
Si tienes un compilador SCSS configurado (ej: Live Sass Compiler en VS Code):
```bash
# Con herramientas npm
npm run sass          # Si está configurado en package.json
```

**Para VS Code:**
- Instala extensión "Live Sass Compiler"
- Click derecho en `scss/styles.scss` → "Watch Sass"
- Los cambios se compilan automáticamente a `css/styles.css`

#### 4. Servidor Local
```bash
# Opción 1: Live Server (VS Code extension)
# Click derecho en index.html → "Open with Live Server"

# Opción 2: Python
python -m http.server 8000

# Opción 3: Node.js
npx http-server
```

Accede a `http://localhost:8000` (o el puerto mostrado)

### Flujo de Trabajo
```
1. Modifica archivos SCSS en scss/
   ↓
2. SCSS se compila automáticamente a css/styles.css
   ↓
3. Cambios se reflejan en navegador (Live Server)
   ↓
4. Verifica cambios en todas las páginas
   ↓
5. Commit y push a git
```

### Flujo de Navegación de la Aplicación

```
index.html (📊 Panel Principal)
    ├─→ agenda.html (📅 Agenda de Servicios)
    │       └─→ detalle-servicio.html (🔧 Detalle del Servicio)
    │           └─→ hoja-trabajo.html (📝 Formulario de Ejecución)
    │
    └─→ perfil.html (👤 Perfil Técnico)
```

### Breakpoints Bootstrap Utilizados

| Dispositivo | Ancho | Clases |
|------------|-------|---------|
| Móvil | < 576px | `col-12`, `d-block` |
| Tablet | 577px - 768px | `col-6`, `col-md-4` |
| Desktop | 769px+ | `col-4`, `col-lg-3` |

**Clases Útiles:**
- `d-none d-sm-inline` - Oculto en móvil
- `d-lg-none` - Oculto en pantalla grande
- `navbar-expand-lg` - Menú adaptable
- `container-fluid` - Ancho 100%

---

## 🏗️ Arquitectura de Componentes

### Navbar (Encabezado)
- Logo + Título corporativo
- Información del usuario (Avatar + Nombre)
- Estilo industrial (navy dark)
- Pegajoso (sticky) en todas las páginas
- Responsive en dispositivos móviles

### Card Custom
```scss
.card-custom {
  background: white;
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
  border-left: 6px solid $navy-dark;
  transition: all 0.3s ease;
  
  &:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 15px rgba(0, 0, 0, 0.1);
  }
}
```

### Botón Brand
- Fondo rojo corporativo (#ca2418)
- Texto en mayúsculas
- Efecto hover con elevación
- Transiciones suaves

### Footer Móvil
- Navegación inferior de 3 opciones
- Visible solo en pantallas pequeñas
- Iconografía clara y accesible
- Fijo al pie de la pantalla

---

## 📊 Estados y Servicios

| Tipo | Color | Icono | Descripción |
|------|-------|-------|-------------|
| **Correctivo** | Rojo (#ca2418) | 🔧 | Reparación urgente de fallas |
| **Preventivo** | Navy (#141f35) | 📋 | Mantenimiento programado |
| **Diagnóstico** | Verde (rgb(40, 167, 69)) | 🔍 | Evaluación y diagnóstico |

---

## 🧪 Datos de Prueba

### Usuario Principal
- **Nombre**: Manuel García
- **Cargo**: Técnico de Mantenimiento Nivel 2
- **Rendimiento (Mes Actual)**:
  - Servicios completados: 42
  - Eficiencia en tiempos: 98%
  - Horas laboradas: 168 hrs

### Clientes de Ejemplo
- **Alkosto** - Planta 2, Zona de Descargue (Bogotá)
- **Fresenius Medical Care** - Centro de distribución
- **Sika** - Planta de producción

### Equipos de Prueba
- **Toyota 8FGCU25** - Montacargas 2500 kg
- **Crown RC 5500** - Montacargas 5000 kg

---

## ⚙️ Configuración Técnica Detallada

### Meta Tags Implementados
```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="Panel técnico para gestión de servicios">
<meta name="keywords" content="servicios técnicos, mantenimiento, montacargas">
<meta name="author" content="Manuel García">
<meta name="theme-color" content="#141f35">
```

### Configuración de Idioma y Codificación
- Idioma de página: Español (`lang="es"`)
- Codificación: UTF-8
- Caracteres especiales: Soportados completamente

### Optimización de Performance
- CSS compilado y minificado en producción
- JavaScript Bundle de Bootstrap (22KB gzip)
- Imágenes optimizadas desde CDN
- Caché y compresión GZIP recomendados en servidor

---

## 🔑 Atributos de Accesibilidad (A11y) Detallado

### Implementación ARIA
```html
<!-- Tabs con roles semánticos -->
<ul role="tablist">
  <li role="presentation">
    <a role="tab" aria-selected="true" aria-label="Servicios de hoy">Hoy</a>
  </li>
  <li role="presentation">
    <a role="tab" aria-selected="false" aria-label="Servicios pendientes">Pendientes</a>
  </li>
</ul>

<!-- Iconografía decorativa oculta a lectores -->
<i class="bi bi-truck" aria-hidden="true"></i>

<!-- Controles accesibles -->
<input type="checkbox" id="notificaciones" aria-label="Activar notificaciones">
```

### Labels y Asociaciones
- Todos los inputs tienen `<label>` asociado
- Atributos `for` coinciden con `id`
- Placeholders complementan pero no reemplazan labels

### Navegación por Teclado
- ✅ Tab: Navegar entre elementos
- ✅ Enter: Activar botones y enlaces
- ✅ Escape: Cerrar modales (cuando aplique)
- ✅ Flecha: Navegar tabs (cuando aplique)

---

## 👨‍💻 Notas de Desarrollo

### Convenciones de Nomenclatura SCSS
```scss
/* ==========================================================================
   1. Variables y Configuración
   ========================================================================== */

// Componente con variantes
.component {           // Bloque principal
  &__element {         // Elemento del componente
    color: blue;
  }
  
  &--modifier {        // Estado o variante
    color: red;
  }
  
  &:hover {           // Estados interactivos
    transform: scale(1.05);
  }
}
```

### Estándares de Código
- **Indentación**: 2-4 espacios (consistente)
- **Ancho máximo**: 80-120 caracteres
- **Comentarios**: Secciones con `=====`
- **Orden**: Variables → Imports → Estilos → Mixins

### Mejores Prácticas SCSS
- Evitar anidamiento profundo (máx 3-4 niveles)
- Usar variables para valores reutilizables
- Agrupar relacionados en mixins
- Documentar con comentarios descriptivos

---

## 🎯 Próximas Mejoras Sugeridas

- [ ] **JavaScript Interactivo**: Tabs dinámicos con transiciones
- [ ] **Canvas.js**: Captura de firmas en formularios
- [ ] **Validación**: Formularios con feedback visual
- [ ] **Backend**: API REST para almacenamiento de datos
- [ ] **Autenticación**: Sistema de login y sesiones seguras
- [ ] **Base de Datos**: PostgreSQL o MongoDB para persistencia
- [ ] **Reportes**: Estadísticas y gráficos avanzados
- [ ] **Real-Time**: Notificaciones push y sincronización
- [ ] **Service Workers**: Modo offline con sincronización
- [ ] **PWA**: Instalable como aplicación nativa
- [ ] **Testing**: Suite de tests unitarios e integración
- [ ] **CI/CD**: GitHub Actions para despliegue automático

---

## 📄 Licencia

Proyecto propietario de Manuel Felipe Gonzalez Acuña para **Overhaul Service Corp**

---

## 👨‍💼 Información del Proyecto

| Propiedad | Valor |
|-----------|-------|
| **Desarrollador** | Manuel García |
| **Empresa** | Overhaul Service Corp |
| **Versión** | 1.0.0 |
| **Última Actualización** | Mayo 6, 2026 |
| **Estado** | ✅ Completado |

---

## 🔗 Referencias y Recursos Útiles

### Documentación Oficial
- [Bootstrap 5.3.8](https://getbootstrap.com/docs/5.3/) - Framework CSS
- [Bootstrap Icons](https://icons.getbootstrap.com/) - Librería de iconos
- [SCSS Documentation](https://sass-lang.com/documentation) - Preprocesador CSS
- [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/) - Accesibilidad
- [MDN Web Docs](https://developer.mozilla.org/) - Referencia HTML/CSS/JS

### Herramientas Recomendadas
- [Live Sass Compiler](https://marketplace.visualstudio.com/items?itemName=ritwickdey.live-sass) - VS Code
- [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) - VS Code
- [Chrome DevTools](https://developer.chrome.com/docs/devtools/) - Testing
- [Lighthouse](https://developers.google.com/web/tools/lighthouse) - Auditoría de performance

---

**Última Actualización**: Mayo 6, 2026  
**Versión del Proyecto**: 1.0.0 (Final)  
**Estado**: ✅ Completado y Optimizado
