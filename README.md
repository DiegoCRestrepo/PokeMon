# Pokedex Angular - Despliegue en Azure Static Web Apps

Este proyecto es una implementación de una Pokédex hecha en Angular, basada en el repositorio original [`rcuello/ac4dem1a`](https://github.com/rcuello/ac4dem1a). Aquí aprenderás cómo desplegar la aplicación en Azure Static Web Apps y realizar configuraciones esenciales para su correcto funcionamiento y seguridad.

## 🚀 Pasos para empezar

1. **Fork del repositorio**
   - Haz fork del repositorio original en tu cuenta de GitHub.

2. **Crear Static Web App en Azure**
   - Accede a [Azure](https://portal.azure.com) y busca "Static Web Apps".
   - Crea una nueva instancia con los siguientes parámetros:
     - **Suscripción**: La que tengas activa (por ejemplo: *Azure for Students*).
     - **Tipo de plan**: Estándar.
     - **Origen**: GitHub.
     - **Cuenta/Organización/Repositorio**: Selecciona tu fork.
     - **Rama**: `master`.
     - **Ubicación de la aplicación**: `sistemas-distribuidos/poke-dex-lab/source/pokedex-angular`.

3. **Corregir rutas de imágenes**
   - Edita el archivo `src/environments/environment.prod.ts`:
     ```ts
     imagesPath: '/assets/images',
     ```
   - Guarda los cambios y haz commit.

4. **Mejorar seguridad**
   - Crea el archivo `staticwebapp.config.json` en la raíz del proyecto (`pokedex-angular`) con el siguiente contenido:
     ```json
     {
       "globalHeaders": {
         "Content-Security-Policy": "default-src * 'unsafe-inline' 'unsafe-eval' data: blob:;",
         "X-Frame-Options": "ALLOWALL",
         "Permissions-Policy": "geolocation=*, camera=*, microphone=*"
       }
     }
     ```
   - Commit y espera a que Azure actualice la web.

5. **Verificación**
   - Accede a tu sitio desde Azure.
   - Usa [securityheaders.com](https://securityheaders.com) para verificar los headers. Deberías obtener una nota de A.

---

## 📦 Tecnologías

- Angular
- Azure Static Web Apps
- GitHub Actions

## 🔒 Seguridad

Se aplicaron headers para Content Security Policy, X-Frame-Options y Permissions-Policy, siendo permisivos para evitar errores de despliegue en ambientes estáticos.

---

## ✨ Resultado

Una Pokédex Angular completamente desplegada, funcional y con headers de seguridad personalizados.