# 📊 Isopan — Devolución y Mala Producción

Dashboard interactivo para reportar Devolución y Mala Producción por tienda, código de producto y razón. Diseñado para desplegarse en **Netlify** y actualizarse cada vez que cambien los datos.

---

## 🚀 Despliegue en Netlify (primera vez)

1. Sube esta carpeta completa a un repositorio de GitHub (puedes usar una subcarpeta de tu repositorio `FabricaZ7`, por ejemplo `devoluciones/`, o un repo nuevo — lo importante es que `index.html`, `netlify.toml` y `data/` queden en la raíz del proyecto publicado).
2. En [netlify.com](https://netlify.com): **New site → Import from GitHub** → selecciona el repositorio.
3. Configuración de build:
   - **Base directory:** `devoluciones` (si usaste subcarpeta) o vacío si es un repo dedicado
   - **Build command:** *(dejar vacío)*
   - **Publish directory:** `.` (o `devoluciones` según corresponda)
4. **Deploy site**.

---

## 📅 Flujo de actualización de datos

Como tu tabla de Excel **acumula todo el histórico** (no es un snapshot diario), no necesitas subir un archivo distinto cada día — solo **sobreescribe siempre el mismo archivo**:

1. Abre el Excel en SharePoint/OneDrive (`GCI-FR-045- Reporte Devolución y PM`)
2. **Archivo → Descargar → Descargar una copia** (para obtener el `.xlsx` actualizado)
3. Renombra el archivo descargado a exactamente:
   ```
   reporte_devolucion_pm.xlsx
   ```
4. En GitHub, navega hasta la carpeta `data/`
5. Clic en **Add file → Upload files**
6. Sube el archivo (reemplazará al anterior automáticamente)
7. **Commit changes** con un mensaje como "Actualización 2026-07-02"
8. Netlify republica el sitio en ~1 minuto ✅

### Alternativa — sin tocar GitHub

Usa el botón **"⬆ Cargar Excel"** en la esquina superior derecha del dashboard para ver los datos al instante en tu sesión, sin necesidad de subir nada (no se guarda para otras personas, solo para tu vista).

---

## ✨ Funcionalidades

- **Filtros**: rango de fechas, tienda, código y nombre (selección múltiple), mes, año
- **Tabla agrupada por producto** con: cantidad por mala producción, cantidad por vencimiento (devolución), suma total, % devolución, % de mala producción, y primera fecha/razón — expandible para ver el detalle diario por tienda
- **3 gráficas**: barras comparativas por código, barras horizontales por razón, y dona de devolución vs. mala producción
- **Exportar a CSV** de la vista filtrada actual
- **Reconocimiento flexible de columnas**: si los encabezados del Excel cambian ligeramente (mayúsculas, tildes), el dashboard los sigue detectando

---

## 🗂 Estructura del proyecto

```
isopan-devoluciones/
├── index.html          ← Dashboard completo (HTML+CSS+JS)
├── netlify.toml         ← Configuración de despliegue
├── data/
│   └── reporte_devolucion_pm.xlsx   ← Se reemplaza en cada actualización
└── README.md
```

---

*Sistema desarrollado para Panadería Isopan*
