# 📊 Producción Isopan — Zona 7

Sistema de reportes interactivos de producción. Diseñado para desplegarse en **Netlify** y actualizarse diariamente con archivos Excel.

---

## 🚀 Despliegue en Netlify

### Primera vez

1. Crea una cuenta gratuita en [netlify.com](https://netlify.com)
2. Sube esta carpeta completa a un repositorio de **GitHub** (o GitLab)
3. En Netlify: **New site → Import from GitHub** → selecciona el repositorio
4. Configuración de build:
   - **Build command:** *(dejar vacío)*
   - **Publish directory:** `.`
5. Haz clic en **Deploy site**

---

## 📅 Flujo Diario de Actualización

### Opción A — Subir desde la web (recomendado)

1. Prepara el archivo Excel del día con el nombre:
   ```
   produccion_YYYY-MM-DD.xlsx
   ```
   Ejemplo: `produccion_2026-06-04.xlsx`

2. En GitHub, navega a la carpeta `data/daily/`
3. Haz clic en **Add file → Upload files**
4. Sube el archivo Excel del día
5. Haz clic en **Commit changes**
6. Netlify lo despliega automáticamente en ~1 minuto ✅

### Opción B — Git desde computadora

```bash
# Copia tu Excel a la carpeta data/daily/
cp produccion_2026-06-04.xlsx data/daily/

# Sube a GitHub
git add data/daily/produccion_2026-06-04.xlsx
git commit -m "Datos producción 2026-06-04"
git push
```

### Opción C — Subida manual directa en la app

Abre el sitio web → botón **"⬆ Cargar Excel"** en la esquina superior derecha.  
Los datos se visualizan al instante (sin guardar en servidor).

---

## 📋 Estructura del Archivo Excel

El archivo debe tener **3 hojas** con estos nombres exactos:

### Hoja 1: `Centros_Produccion`
| Centro de Producción | Responsable | Turno | Estado | Capacidad (unid/día) |
|---|---|---|---|---|
| CP-01 Panadería Principal | Carlos Pérez | Mañana | Activo | 2500 |

### Hoja 2: `Produccion`
| Producto | Centro | Planificado (u) | Elaborado (u) | Rendimiento (%) | Merma (u) | Merma (%) | No Elaborado (u) | Fecha | Turno |
|---|---|---|---|---|---|---|---|---|---|
| Pan Francés 50g | CP-01 | 1000 | 980 | 98.0 | 12 | 1.2 | 20 | 2026-06-04 | Mañana |

### Hoja 3: `Materiales_Pendientes`
| Material | Centro Solicitante | Cantidad Solicitada | Unidad | Stock Actual | Estado | Fecha Solicitud |
|---|---|---|---|---|---|---|
| Harina de Trigo | CP-01 | 500 | Quintales | 120 | URGENTE | 2026-06-04 |

**Valores válidos para Estado:** `Activo`, `Pendiente`, `URGENTE`, `Normal`, `Mantenimiento`

---

## 📁 Estructura de Carpetas

```
isopan-zona7/
├── index.html              ← Aplicación web principal
├── netlify.toml            ← Configuración Netlify
├── README.md               ← Este archivo
├── generate_sample.py      ← Script para generar Excel de muestra
└── data/
    └── daily/
        ├── produccion_2026-06-04.xlsx   ← Excel de hoy
        ├── produccion_2026-06-03.xlsx   ← Excel de ayer
        └── ...
```

---

## ✨ Funcionalidades del Sistema

- **Dashboard** con KPIs: planificado, elaborado, rendimiento, mermas, no elaborados, materiales
- **7 secciones** navegables: centros, productos, rendimientos, mermas, no elaborados, materiales, carga de datos
- **Barras de progreso** para rendimientos con indicador visual rojo/verde
- **Badges de estado** con colores: urgente (rojo), pendiente (naranja), activo (verde), normal (azul)
- **Búsqueda** en tiempo real en cada tabla
- **Ordenamiento** por columna con clic en el encabezado
- **Exportar a CSV** cada tabla
- **Mini gráficas** de producción por centro y rendimiento por producto
- **Carga automática** del Excel del día al abrir la página
- **Diseño responsivo** adaptado a colores corporativos Isopan

---

## 🛠️ Generar Excel de Muestra

```bash
pip install openpyxl
python3 generate_sample.py
```

Genera `data/daily/produccion_YYYY-MM-DD.xlsx` con datos de ejemplo.

---

*Sistema desarrollado para Panadería Isopan — Zona 7, Guatemala*
