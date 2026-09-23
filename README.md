# GS Tienda & Servicios - Plan de Transformación Digital

Repositorio centralizado para la organización, estructuración y automatización del modelo de negocio multipropósito de **GS Tienda & Servicios**.

---

## 📌 Descripción del Proyecto

**GS Tienda & Servicios** es un emprendimiento enfocado en brindar una solución integral a las necesidades cotidianas del hogar y uso personal. Combina la comercialización de productos con la prestación de servicios bajo un modelo de atención directa y personalizada.

*   **Línea de Productos:** Indumentaria, Calzado, Deportes, Blanquería, Bazar y Juguetes.
*   **Línea de Servicios:** Belelza integral, Coordinación de Viajes.

El objetivo central de este proyecto es transformar una operación 100% manual en una estructura organizada, digitalizada y escalable.

---

## 🛠️ Stack Tecnológico Proyectado

# 🚀 App Web Full-Stack (Lovable + Supabase + n8n)

Aplicación web moderna desarrollada mediante el stack de desarrollo acelerado con Inteligencia Artificial.

---

## 🛠️ Arquitectura y Stack Tecnológico

* **Frontend & Interfaz:** [Lovable](https://lovable.dev) (React + Tailwind CSS / Shadcn UI).
* **Backend & Base de Datos:** [Supabase](https://supabase.com) (PostgreSQL, Autenticación de usuarios y Almacenamiento).
* **Lógica & Automatización:** [n8n](https://n8n.io) (Orquestación de flujos de trabajo, APIs y agentes de IA).

---

## 📐 Estructura del Sistema

1. **Interfaz (Lovable):** Diseñada e interactuada mediante visores de IA. Genera código limpio en React y se sincroniza automáticamente con este repositorio en GitHub.
2. **Base de Datos & Auth (Supabase):** Gestiona las tablas de PostgreSQL, políticas de seguridad (RLS) y la sesión de los usuarios.
3. **Motor de Integración (n8n):** Recibe Webhooks desde la app/Supabase para ejecutar la lógica de negocio pesada, integración con modelos de IA (OpenAI, Claude) y conectores a servicios externos.

---

## ⚙️ Configuración y Variables de Entorno

Asegúrate de configurar las siguientes variables en tu entorno de desarrollo local o producción:

```env
VITE_SUPABASE_URL=tu_supabase_url
VITE_SUPABASE_ANON_KEY=tu_supabase_anon_key
VITE_N8N_WEBHOOK_URL=tu_n8n_webhook_url

---

### 🤖 ¿Cómo interactúan entre sí?

1. **Lovable (Frontend):** Es el generador con IA que dibuja la interfaz y escribe el código en React. Se conecta directo a Supabase con la librería `@supabase/supabase-js`.
2. **Supabase (Backend/Database):** Guarda los datos de tus usuarios de forma segura.
3. **n8n (Workflows & IA):** Es el "cerebro" detrás de escena. Cuando ocurre una acción en la web (ej. un usuario da clic a un botón o llena un formulario), Lovable o Supabase le envían un **Webhook** a n8n, el cual procesa la lógica, llama a modelos de IA (como ChatGPT, Claude o Gemini) y le devuelve la respuesta a la web.

## 🚀 Contenido del Repositorio

* `/docs`: Propuesta comercial, templates de atención y especificaciones del proyecto.
* `/assets`: Material gráfico, identidades visuales e iconografía del negocio.
* `/templates`: Flujos de atención comercial y guiones de respuesta.
