

## 📌 Progreso de Etapas (Bitácora de 25/09/2026)

### 🔹 ETAPA 1 — Descubrir (Entender el negocio real)
* **Objetivo**: Establecer las bases operativas de la tienda física/digital y servicios.
* **Entregables Definidos**:
  * **Actores**: Administrador/Dueño de tienda.
  * **Canales**: Gestión móvil en punto de venta / carga en sitio.
  * **Productos / Servicios**: Indumentaria (femenina, masculina, niños, bebés), mascotas, juguetes, bazar, blanquería, belleza, deportes, entretenimiento y servicios (viajes, belleza).
  * **Reglas de Negocio Identificadas**:
    * Separación estricta entre **Stock Actual** (visión consolidada) y **Movimientos de Stock** (trazabilidad transaccional de entradas/salidas).
    * Cálculo de precio de venta automático basado en un **margen predeterminado del 40%** ($Precio\_Venta = Precio\_Costo \times 1.40$) con posibilidad de ajuste manual.
    * Inclusión de trazabilidad de confianza ($0.000$ a $1.000$) y observaciones estructuradas (`obs_*`) para futura auditoría por IA/n8n.

---

### 🔹 ETAPA 2 — Diseñar (Convertir el problema en arquitectura)
* **Objetivo**: Definir el modelo de datos relacional y los permisos.
* **Entregables Definidos**:
  * **Modelo de Datos en Supabase (PostgreSQL)**:
    * `config_cliente`: Registro multitenant (`id_cliente: 259d3b91-ea1f-472a-aaf2-06c19411a828`).
    * `categorias`: Parametrización inicial con 14 categorías comerciales.
    * `productos`: Catálogo principal, vinculación de categoría, precio costo, precio venta, foto de portada (`foto_url`) y `stock_actual`.
    * `movimientos_stock`: Registro histórico de auditoría de inventario.
    * `producto_media`: Esquema aditivo y escalable para soporte de galerías con múltiples fotos y videos cortos.
  * **Seguridad y Permisos**:
    * Configuración e implementación de Row Level Security (RLS) e idempotencia mediante scripts SQL limpios (`DROP POLICY IF EXISTS`).

---

### 🔹 ETAPA 3 — Construir el núcleo
* **Orden de Construcción**: `Supabase` (Base de datos) ➔ `n8n` (Automatización futura) ➔ `Lovable` (Interfaz Móvil).
* **Avances Realizados**:
  1. **Supabase**: Base de datos creada, esquema relacional activo, políticas RLS aplicadas y bucket público `productos` inicializado en Supabase Storage.
  2. **Base de Datos Cargada**: 28 registros consolidados en la tabla `categorias`.
  3. **Lovable (Frontend)**: Configuración del formulario móvil *Mobile-First* para carga de productos.

---

### 🔹 ETAPA 4 — MVP (Flujo Central de Demostración de Valor)
* **Objetivo de la Fase Actual**: Validar exclusivamente el flujo central antes de construir pantallas secundarias.
* **Flujo Implementado**:
  $$\text{Agregar Producto} \longrightarrow \text{Calcular (Margen 40\%)} \longrightarrow \text{Aprobar / Categorizar} \longrightarrow \text{Guardar Dual} \longrightarrow \text{Stock} \longrightarrow \text{Catálogo}$$

* **Funcionalidades del Formulario en Pruebas**:
  * Carga dinámica de categorías desde Supabase.
  * Autocompletado automático de Precio de Venta al ingresar Precio de Costo.
  * Opción de múltiples fotos e imágenes de portada.
  * Inserción dual simultánea: Creación en `productos` y registro automático de movimiento inicial en `movimientos_stock` (`tipo_movimiento: 'ENTRADA'`).

---

### 🔹 ETAPA 5 — Validación Real (En Proceso)
* **Objetivo**: Probar el sistema desde el dispositivo móvil en un entorno real antes de publicar.
* **Acciones en curso**:
  * Ejecución en modo **Vista Previa Mobile** de Lovable desde el smartphone.
  * Evaluación de la experiencia de toma de fotografías desde la cámara del celular.
  * Verificación de persistencia de datos en Supabase.
