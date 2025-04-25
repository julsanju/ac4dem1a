# Diagrama de Arquitectura en Azure para PokeDex

```
+-----------------------------+
|       Usuario Final         |
|                             |
|  Acceso a través de HTTPS   |
+-----------------------------+
             |
             v
+-----------------------------+
|    Azure Static Web Apps    |
|                             |
| - Hosting estático          |
| - Despliegue automático     |
|   desde GitHub              |
| - URL pública asignada      |
|   (https://*.azurestaticapps.net) |
+-----------------------------+
             |
             v
+-----------------------------+
|        GitHub Repo          |
|                             |
| - Código fuente de PokeDex  |
| - Rama principal (main)     |
| - Configuración de build    |
|   (ej: /dist o /build)      |
+-----------------------------+
             |
             v
+-----------------------------+
|     GitHub Actions          |
|                             |
| - Automatización del build  |
| - Integración continua (CI) |
| - Despliegue continuo (CD)  |
+-----------------------------+
             |
             v
+-----------------------------+
|    Azure Resource Group     |
|                             |
| - Grupo lógico de recursos  |
| - Administración centralizada|
|   de todos los servicios    |
+-----------------------------+
             |
             v
+-----------------------------+
|    Azure Active Directory   |
|                             |
| - Autenticación y autorización|
| - Gestión de usuarios y roles|
|   (Estudiantes con cuenta)  |
+-----------------------------+
             |
             v
+-----------------------------+
|    Azure Security Center    |
|                             |
| - Monitoreo de seguridad    |
| - Protección contra amenazas|
| - Configuración de CORS     |
+-----------------------------+
```

## Explicación del Diagrama

Este diagrama representa la infraestructura de despliegue para la aplicación PokeDex Angular en Azure, utilizando el servicio Azure Static Web Apps. El diagrama muestra cómo los diferentes componentes interactúan para proporcionar una solución de despliegue eficiente y segura en la nube.

### Flujo de Implementación:

1. **Usuario Final**: Accede a la aplicación PokeDex a través de HTTPS desde cualquier navegador web.

2. **Azure Static Web Apps**: Servicio principal que aloja la aplicación web estática, proporcionando:
   - URL pública con HTTPS habilitado por defecto
   - Hospedaje optimizado para aplicaciones como Angular
   - Escalabilidad automática

3. **GitHub Repository**: Almacena el código fuente de la aplicación PokeDex Angular, incluyendo:
   - Archivos de configuración
   - Código fuente de la aplicación
   - Dependencias y recursos

4. **GitHub Actions**: Proporciona la automatización del proceso de CI/CD:
   - Detecta cambios en el repositorio
   - Ejecuta pruebas automáticas
   - Compila la aplicación
   - Despliega automáticamente a Azure

5. **Azure Resource Group**: Agrupa todos los recursos relacionados para facilitar:
   - Gestión centralizada
   - Monitoreo de costos
   - Administración de permisos

6. **Azure Active Directory**: Gestiona la autenticación y autorización:
   - Integración con cuentas de estudiantes
   - Control de acceso basado en roles
   - Inicio de sesión único (SSO)

7. **Azure Security Center**: Proporciona protección y monitoreo:
   - Configuración adecuada de CORS
   - Prevención de ataques
   - Cumplimiento de políticas de seguridad

Esta arquitectura garantiza un despliegue eficiente y seguro de la aplicación PokeDex Angular, aprovechando las capacidades de la nube de Azure y la integración con GitHub para una entrega continua.

# Publicación de la App PokeDex con Azure Static Web Apps

Este documento detalla cómo poner en línea tu aplicación **PokeDex** usando **Azure Static Web Apps**. Necesitarás una cuenta de Azure (idealmente la de estudiante) y el repositorio de GitHub del proyecto.

---

## 📋 Requerimientos Previos

-   Cuenta activa en Microsoft Azure.
-   Suscripción válida (puede ser gratuita, de estudiante o de pago).
-   Sesión iniciada en GitHub con acceso al repositorio del proyecto.

---

## 🛠️ Guía de Despliegue Paso a Paso

### 1. Acceso al Portal de Azure

Ingresa a tu cuenta de Azure a través de este enlace:
🌐 [https://portal.azure.com](https://portal.azure.com)

---

### 2. Localizar "Static Web Apps"

Utiliza la barra de búsqueda superior del portal, introduce `Static Web Apps` y selecciona el servicio correspondiente.
Haz clic en **"Crear"** para comenzar la configuración.

---

### 3. Configuración de la Nueva Aplicación

#### a. Información del Proyecto

-   **Suscripción:** Elige la suscripción que vas a utilizar.
-   **Grupo de recursos:** Selecciona un grupo existente o crea uno nuevo para organizar tus recursos.

#### b. Detalles de la Aplicación Estática

-   **Nombre:** Define un nombre único globalmente para tu PokeDex App.
-   **Plan:** Selecciona el plan (usualmente "Gratis" para empezar).
-   **Región:** Escoge la ubicación geográfica óptima para tu aplicación.

#### c. Detalles de la Implementación (Deployment)

-   **Fuente (Source):** Selecciona `GitHub`.
-   Asegúrate de tener la sesión de GitHub activa en tu navegador.
-   Autoriza a Azure para que acceda a tus repositorios de GitHub.
-   **Organización:** Selecciona tu cuenta de GitHub.
-   **Repositorio:** Elige el repositorio específico de tu PokeDex.
-   **Rama (Branch):** Selecciona la rama principal que contiene el código listo para desplegar (ej. `main`, `master`).
-   **Valores preestablecidos de compilación (Build Presets):** Selecciona el framework adecuado (React, Angular, Vue, etc.) o configura manualmente las ubicaciones de la app, API (si aplica) y la salida de compilación (`/build`, `/dist`, etc.).

---

### 4. Verificación y Lanzamiento

Pulsa **"Revisar y crear"**. Azure comprobará la configuración proporcionada.
Azure intentará detectar la configuración de compilación automáticamente si no la especificaste.

---

### 5. Creación del Recurso

Tras la validación exitosa, haz clic en **"Crear"**.
Azure comenzará a configurar los recursos y a desplegar tu aplicación desde GitHub Actions.

---

## 🎉 ¡Despliegue Completado!

Al finalizar el proceso, Azure te proporcionará una URL pública. ¡Tu PokeDex ya estará accesible en línea!

---

## 🔒 Consideraciones de Seguridad

-   Evita subir archivos de configuración (`.env`) o claves secretas directamente al repositorio. Usa las variables de entorno de Azure Static Web Apps.
-   Configura CORS adecuadamente si tu frontend consume APIs externas.
-   Confirma que el tráfico a tu sitio sea a través de HTTPS (Azure lo habilita por defecto).

---

### ✍️ Creado por

Julian Santana — Iniciativa académica para Pueblo Paleta Inc.
