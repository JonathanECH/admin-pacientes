# Administrador de Pacientes con Vue 3

Este proyecto es una aplicación web para la administración de pacientes de una clínica veterinaria, desarrollada con Vue 3 y herramientas modernas del ecosistema de JavaScript.

## ✨ Características Principales

- **Gestión de Pacientes (CRUD):**
  - **Crear:** Añadir nuevos pacientes a través de un formulario interactivo.
  - **Editar:** Modificar la información de pacientes existentes, con la opción de cancelar la edición.
  - **Eliminar:** Borrar pacientes del listado, con un modal de confirmación para evitar eliminaciones accidentales.
- **Persistencia de Datos:** La información de los pacientes se guarda en el `localStorage` del navegador, por lo que los datos persisten entre sesiones.
- **Reactividad:** La interfaz de usuario se actualiza automáticamente al agregar, editar o eliminar pacientes gracias a la reactividad de Vue.
- **Componentes Reutilizables:** El proyecto está estructurado en componentes como `Header`, `Formulario`, `Paciente`, `Alerta` y `Modal` para una mejor organización y mantenibilidad.
- **Validación de Formularios:** Se valida que todos los campos del formulario estén completos antes de guardar un paciente.
- **Alertas Dinámicas:** Se muestran notificaciones al usuario para confirmar acciones exitosas (guardar, editar, eliminar) o para informar de errores (campos vacíos).
- **Diseño Responsivo:** La interfaz está diseñada con Tailwind CSS para adaptarse a diferentes tamaños de pantalla, desde móviles hasta escritorios.
- **Experiencia de Usuario Mejorada:**
  - Scroll automático al formulario al editar un paciente.
  - Bloqueo del scroll de la página cuando el modal de confirmación está activo.

## 🌐 Demo en Vivo

Puedes ver el proyecto desplegado y probarlo en el siguiente enlace: [admin-pacientes-veterinaria-vue.netlify.app](https://admin-pacientes-veterinaria-vue.netlify.app/)

## 🛠️ Tecnologías Utilizadas

- **Vue 3:** El framework progresivo de JavaScript. Se utilizó la **Composition API** con la sintaxis `<script setup>` para una lógica de componentes más organizada y legible.
- **Vite:** Herramienta de construcción y servidor de desarrollo que ofrece un arranque en frío extremadamente rápido y recarga en caliente (HMR) instantánea.
- **Tailwind CSS:** Un framework de CSS "utility-first" para construir diseños personalizados rápidamente sin salir del HTML.
- **uid:** Una librería ligera para generar identificadores únicos para cada paciente.

## 🚀 Instalación y Puesta en Marcha

Sigue estos pasos para ejecutar el proyecto en tu entorno local:

1.  **Clonar el repositorio:**
    ```bash
    git clone <URL-DEL-REPOSITORIO>
    ```

2.  **Navegar al directorio del proyecto:**
    ```bash
    cd admin-pacientes
    ```

3.  **Instalar las dependencias:**
    ```bash
    pnpm install
    ```

4.  **Ejecutar el servidor de desarrollo:**
    ```bash
    pnpm dev
    ```

¡Y listo! La aplicación estará disponible en `http://localhost:5173` (o el puerto que Vite indique).
