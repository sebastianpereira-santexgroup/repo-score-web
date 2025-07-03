# 🎨 Guía de Diseño - RepoScore

## 🎯 Introducción

Esta guía documenta el sistema de diseño de RepoScore, una plataforma moderna para análisis de repositorios de código. El objetivo es mantener consistencia visual y de experiencia de usuario en toda la aplicación.

---

## 🎨 Sistema de Colores

### Paleta Principal

```css
/* Primarios - Azul */
--primary-50: #eff6ff     /* Fondos muy claros */
--primary-100: #dbeafe    /* Fondos claros */
--primary-200: #bfdbfe    /* Bordes suaves */
--primary-300: #93c5fd    /* Elementos secundarios */
--primary-400: #60a5fa    /* Hover states */
--primary-500: #3b82f6    /* Color principal */
--primary-600: #2563eb    /* Botones y acciones */
--primary-700: #1d4ed8    /* Estados activos */
--primary-800: #1e40af    /* Texto sobre fondos claros */
--primary-900: #1e3a8a    /* Texto principal */
--primary-950: #172554    /* Texto muy oscuro */
```

### Paleta Secundaria - Grises

```css
/* Secundarios - Gris */
--secondary-50: #f8fafc   /* Fondo de página */
--secondary-100: #f1f5f9  /* Fondos de cards */
--secondary-200: #e2e8f0  /* Bordes principales */
--secondary-300: #cbd5e1  /* Bordes de inputs */
--secondary-400: #94a3b8  /* Placeholder text */
--secondary-500: #64748b  /* Texto secundario */
--secondary-600: #475569  /* Texto principal */
--secondary-700: #334155  /* Títulos */
--secondary-800: #1e293b  /* Texto enfatizado */
--secondary-900: #0f172a  /* Texto muy oscuro */
--secondary-950: #020617  /* Negro */
```

### Colores de Estado

```css
/* Success - Verde */
--success-50: #ecfdf5
--success-500: #10b981
--success-600: #059669

/* Warning - Amarillo */
--warning-50: #fffbeb
--warning-500: #f59e0b
--warning-600: #d97706

/* Error - Rojo */
--error-50: #fef2f2
--error-500: #ef4444
--error-600: #dc2626
```

---

## 📝 Tipografía

### Jerarquía

```css
/* Display - Para títulos principales */
.text-display-xl: 4rem/4.5rem     /* 64px/72px - Hero titles */
.text-display-lg: 3rem/3.5rem     /* 48px/56px - Page titles */
.text-display-md: 2.25rem/2.75rem /* 36px/44px - Section titles */

/* Body - Para contenido */
.text-body-lg: 1.125rem/1.75rem   /* 18px/28px - Large body text */
.text-body-md: 1rem/1.5rem        /* 16px/24px - Default body text */
.text-body-sm: 0.875rem/1.25rem   /* 14px/20px - Small body text */

/* Caption - Para metadatos */
.text-caption: 0.75rem/1rem       /* 12px/16px - Captions, labels */
```

### Fuentes

- **Primaria**: Geist Sans (Variable font)
- **Monospace**: Geist Mono (para código y hashes)

---

## 🧩 Componentes Base

### Button

**Variantes disponibles:**
- `primary` - Acción principal (azul)
- `secondary` - Acción secundaria (gris)
- `ghost` - Sin fondo, solo hover
- `destructive` - Acciones destructivas (rojo)
- `outline` - Con borde
- `link` - Estilo de enlace

**Tamaños:**
- `sm` - 36px altura
- `md` - 40px altura (default)
- `lg` - 44px altura
- `xl` - 48px altura
- `icon` - 40x40px cuadrado

**Uso:**
```tsx
<Button variant="primary" size="md">
  Texto del botón
</Button>
```

### Input

**Variantes:**
- `default` - Estado normal
- `error` - Con error
- `success` - Válido

**Características:**
- Labels opcionales
- Texto de ayuda
- Iconos izquierda/derecha
- Estados de focus y error

**Uso:**
```tsx
<Input
  label="Email"
  placeholder="Ingresa tu email"
  helper="Te enviaremos confirmación"
  error="Email requerido"
  leftIcon={<EmailIcon />}
/>
```

### Card

**Variantes:**
- `default` - Card estándar con sombra
- `elevated` - Con más elevación
- `outlined` - Solo con borde
- `ghost` - Sin fondo ni borde

**Props especiales:**
- `interactive` - Hover effects para cards clickeables
- `padding` - Control de padding interno

**Uso:**
```tsx
<Card variant="elevated" interactive>
  <CardHeader>
    <CardTitle>Título</CardTitle>
    <CardDescription>Descripción</CardDescription>
  </CardHeader>
  <CardContent>
    Contenido principal
  </CardContent>
</Card>
```

### Badge

**Variantes:**
- `default` - Azul
- `secondary` - Gris
- `success` - Verde
- `warning` - Amarillo
- `error` - Rojo
- `outline` - Con borde

**Uso:**
```tsx
<Badge variant="success" size="md">
  Completado
</Badge>
```

---

## 🏗️ Layout y Estructura

### DashboardLayout

Componente principal que incluye:
- **Sidebar**: Navegación persistente con logo y menú
- **TopBar**: Breadcrumbs, búsqueda y acciones de usuario
- **Main Content**: Área principal con padding consistente

**Uso:**
```tsx
<DashboardLayout 
  title="Dashboard"
  breadcrumbs={[
    { label: 'Dashboard', href: '/dashboard' },
    { label: 'Repositorios' }
  ]}
>
  <div>Contenido de la página</div>
</DashboardLayout>
```

### Sidebar Navigation

- **Logo**: RepoScore con icono RS
- **Navegación principal**: Dashboard, Analytics, Configuración
- **Acción primaria**: Botón "Agregar Repo"
- **Usuario**: Información básica del usuario

### Grid System

```css
/* Breakpoints responsivos */
sm: 640px     /* Tablet */
md: 768px     /* Tablet grande */
lg: 1024px    /* Desktop */
xl: 1280px    /* Desktop grande */
2xl: 1536px   /* Desktop muy grande */
```

---

## 🎭 Espaciado y Tamaños

### Espaciado

```css
--space-xs: 4px     /* Elementos muy juntos */
--space-sm: 8px     /* Elementos relacionados */
--space-md: 16px    /* Espaciado estándar */
--space-lg: 24px    /* Secciones relacionadas */
--space-xl: 32px    /* Secciones separadas */
--space-2xl: 48px   /* Grandes separaciones */
--space-3xl: 64px   /* Separaciones de página */
```

### Contenedores

```css
--container-sm: 640px   /* Formularios */
--container-md: 768px   /* Contenido estándar */
--container-lg: 1024px  /* Tablas y listas */
--container-xl: 1280px  /* Dashboard principal */
--container-2xl: 1536px /* Pantallas grandes */
```

---

## ✨ Efectos Visuales

### Sombras

```css
/* Elevación progresiva */
--shadow-soft: 0 2px 15px -3px rgba(0, 0, 0, 0.07)
--shadow-medium: 0 4px 25px -5px rgba(0, 0, 0, 0.1)
--shadow-strong: 0 10px 40px -10px rgba(0, 0, 0, 0.15)
```

### Bordes

```css
/* Radio de bordes */
--radius-sm: 0.375rem    /* 6px - Badges, pills */
--radius-md: 0.5rem      /* 8px - Botones, inputs */
--radius-lg: 0.75rem     /* 12px - Cards */
--radius-xl: 1rem        /* 16px - Modales */
--radius-2xl: 1.5rem     /* 24px - Contenedores grandes */
```

### Animaciones

```css
/* Duraciones estándar */
--duration-fast: 150ms      /* Hover rápido */
--duration-normal: 200ms    /* Transiciones estándar */
--duration-slow: 300ms      /* Animaciones complejas */

/* Easing */
--ease-out: cubic-bezier(0, 0, 0.2, 1)
--ease-in: cubic-bezier(0.4, 0, 1, 1)
--ease-in-out: cubic-bezier(0.4, 0, 0.2, 1)
```

---

## 🎯 Principios de Diseño

### 1. Claridad
- **Jerarquía visual clara** con tipografía y espaciado
- **Contrastes apropiados** para legibilidad
- **Iconografía consistente** para comunicar funciones

### 2. Consistencia
- **Patrones reutilizables** en toda la aplicación
- **Espaciado sistemático** usando escala definida
- **Colores coherentes** con significado semántico

### 3. Eficiencia
- **Flujos optimizados** para tareas comunes
- **Acceso rápido** a funciones principales
- **Feedback inmediato** en interacciones

### 4. Accesibilidad
- **Contraste WCAG AA** mínimo 4.5:1
- **Navegación por teclado** en todos los elementos
- **Estados de focus** visibles y claros
- **Texto alternativo** en elementos visuales

### 5. Responsividad
- **Mobile-first** approach
- **Breakpoints consistentes** en toda la app
- **Adaptación inteligente** de layouts
- **Touch-friendly** en dispositivos móviles

---

## 📊 Estados de Interacción

### Botones y Enlaces
```css
/* Estados estándar */
:default     /* Estado base */
:hover       /* Elevación sutil + cambio de color */
:focus       /* Ring azul de 2px */
:active      /* Scale 95% + color más oscuro */
:disabled    /* Opacidad 50% + pointer-events none */
```

### Cards Interactivas
```css
/* Estados de card */
:default     /* Sombra soft */
:hover       /* Sombra medium + translate -1px */
:active      /* Scale 98% */
```

### Inputs
```css
/* Estados de input */
:default     /* Border gris */
:focus       /* Border azul + ring azul */
:error       /* Border rojo + ring rojo */
:disabled    /* Background gris + opacidad */
```

---

## 🚀 Mejores Prácticas

### Desarrollo

1. **Usar componentes base** antes de crear nuevos
2. **Consistencia en naming** de clases CSS
3. **Props tipadas** en todos los componentes
4. **Forwarded refs** para componentes reutilizables

### Diseño

1. **Mantener jerarquía visual** con tamaños y espaciado
2. **Usar colores semánticos** para estados y acciones
3. **Probar accesibilidad** con herramientas como axe-core
4. **Validar en múltiples dispositivos** y navegadores

### Performance

1. **Lazy loading** para componentes pesados
2. **Optimización de imágenes** con next/image
3. **Code splitting** por páginas principales
4. **Memoización** de componentes costosos

---

## 🔧 Herramientas y Configuración

### Dependencias Principales
```json
{
  "tailwindcss": "^4.0.0",
  "class-variance-authority": "^0.7.1",
  "clsx": "^2.1.1",
  "tailwind-merge": "^3.3.1"
}
```

### Configuración Recomendada

**VS Code Extensions:**
- Tailwind CSS IntelliSense
- PostCSS Language Support
- Headwind (class sorting)

**Scripts útiles:**
```json
{
  "design:check": "npx tailwindcss --dry-run",
  "design:build": "tailwindcss build -o dist/styles.css"
}
```

---

Esta guía debe evolucionar con el producto. Mantén la documentación actualizada cuando agregues nuevos componentes o modifiques el sistema de diseño.