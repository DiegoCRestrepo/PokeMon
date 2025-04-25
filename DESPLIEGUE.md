# 📦 Guía de Despliegue: Pokedex Angular en Azure Static Web Apps

## 1. Fork del Repositorio

Haz un fork del repositorio original:

🔗 [https://github.com/rcuello/ac4dem1a](https://github.com/rcuello/ac4dem1a)

Esto creará una copia del proyecto en tu cuenta de GitHub.

---

## 2. Crear Static Web App en Azure

1. Inicia sesión en Azure y busca **Static Web Apps**.
2. Haz clic en **Crear** y llena los campos:

- **Suscripción**: Tu plan actual (por ejemplo, Azure for Students).
- **Tipo de plan**: Estándar.
- **Origen**: GitHub (iniciar sesión y autorizar).
- **Organización**: Tu cuenta de GitHub.
- **Repositorio**: Selecciona el fork que creaste.
- **Rama**: `master`.
- **Ubicación de la aplicación**:  
  ```
  sistemas-distribuidos/poke-dex-lab/source/pokedex-angular
  ```

3. Haz clic en **Revisar y crear**, luego en **Crear**.

---

## 3. Corregir Ruta de Imágenes

Una vez desplegada la app, notarás que las imágenes no cargan. Para solucionarlo:

1. Ve al archivo:
   ```
   sistemas-distribuidos/poke-dex-lab/source/pokedex-angular/src/environments/environment.prod.ts
   ```
2. Modifica la línea 9:
   ```ts
   imagesPath: '/assets/images',
   ```
3. Haz commit y espera a que se actualice en Azure.

---

## 4. Mejorar Seguridad con Headers

Para mejorar la nota en [securityheaders.com](https://securityheaders.com):

1. Crea un archivo `staticwebapp.config.json` en la carpeta:
   ```
   sistemas-distribuidos/poke-dex-lab/source/pokedex-angular
   ```

2. Añade este contenido:
   ```json
   {
     "globalHeaders": {
       "Content-Security-Policy": "default-src * 'unsafe-inline' 'unsafe-eval' data: blob:;",
       "X-Frame-Options": "ALLOWALL",
       "Permissions-Policy": "geolocation=*, camera=*, microphone=*"
     }
   }
   ```

3. Commit y verifica en [securityheaders.com](https://securityheaders.com). La nota debería mejorar a **A**.

---

## ✅ Resultado

¡Tu Pokédex Angular ahora está desplegada, funcional y más segura!