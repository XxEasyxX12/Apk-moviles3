
# Documentación de la Aplicación Móvil de Autenticación

## Descripción General

Esta aplicación móvil permite a los usuarios registrarse, iniciar sesión y acceder a contenido dentro de la app utilizando **Firebase Authentication**. La autenticación es posible a través de **correo electrónico y contraseña** o mediante cuentas de **Facebook**. La app está construida utilizando **React** y **Ionic**, lo que permite su ejecución tanto en dispositivos Android como iOS.

### Alcances de la Aplicación

La aplicación permite realizar las siguientes acciones:
- **Registro de usuario** mediante correo electrónico y contraseña.
- **Inicio de sesión** mediante correo electrónico y contraseña.
- **Inicio de sesión con Facebook**.
- **Visualización de contenido** de ejemplo (lista de posts y personas).

## Requerimientos Funcionales

1. **Registro de usuario**:
   - El usuario debe poder registrarse utilizando un correo electrónico y una contraseña.
   - El sistema debe validar la contraseña y asegurarse de que cumpla con los requisitos mínimos de seguridad (mínimo 6 caracteres).
   - El sistema debe permitir la verificación del correo electrónico.

2. **Inicio de sesión**:
   - El usuario debe poder iniciar sesión usando su correo electrónico y contraseña.
   - El sistema debe permitir el inicio de sesión usando cuentas de Facebook, gestionado por **Firebase Authentication**.

3. **Gestión de sesión**:
   - El sistema debe mantener la sesión activa durante la duración de la aplicación.
   - El usuario debe poder cerrar sesión en cualquier momento.

4. **Acceso a contenido**:
   - Una vez autenticado, el usuario podrá ver una lista de posts y personas.
   - Los datos de los posts se obtienen de una API pública (jsonplaceholder).
   - Los datos de las personas se obtienen de una API externa para demostración.

5. **Interfaz de usuario**:
   - La aplicación debe tener una interfaz clara y fácil de usar.
   - Debe ser compatible con dispositivos móviles de pantalla pequeña (smartphones).

## Requerimientos No Funcionales

1. **Rendimiento**:
   - La aplicación debe ser capaz de gestionar sesiones de usuario rápidamente, con tiempos de respuesta no mayores a 2 segundos para la autenticación.
   - La carga de los datos desde las APIs debe ser eficiente y no generar bloqueos en la interfaz de usuario.

2. **Seguridad**:
   - Los datos de autenticación deben ser manejados de manera segura mediante el uso de **Firebase Authentication**.
   - Las contraseñas deben ser almacenadas de manera segura en la base de datos de Firebase y no deben ser accesibles.

3. **Compatibilidad**:
   - La aplicación debe ser compatible con las últimas versiones de Android e iOS.
   - Debe funcionar correctamente tanto en dispositivos físicos como en emuladores.

4. **Escalabilidad**:
   - Aunque la aplicación no está orientada a ser masivamente escalable en este momento, debe ser capaz de soportar un incremento en la cantidad de usuarios sin comprometer su rendimiento.

5. **Usabilidad**:
   - La aplicación debe ser fácil de usar, con una navegación intuitiva y accesible para todo tipo de usuarios.
   - El diseño debe adaptarse a diferentes tamaños de pantalla y resoluciones.

## Tecnologías Utilizadas

1. **React**: Biblioteca de JavaScript para construir interfaces de usuario interactivas.
2. **Ionic Framework**: Framework para la creación de aplicaciones móviles híbridas utilizando tecnologías web.
3. **Firebase**:
   - **Firebase Authentication**: Para gestionar la autenticación de usuarios mediante correo electrónico y contraseña, así como la integración con Facebook.
   - **Firestore**: Base de datos en tiempo real para almacenar datos relacionados con el usuario.
4. **Capacitor**: Herramienta para construir y empaquetar aplicaciones móviles nativas para Android e iOS desde un proyecto web basado en Ionic.
5. **Firebase SDK**: Para conectar la aplicación a Firebase y manejar la autenticación.

## Manual de Usuario

### Registro y Login

1. **Registro**:
   - Abre la aplicación y selecciona la opción "Registrarse".
   - Ingresa tu correo electrónico y una contraseña segura (mínimo 6 caracteres).
   - Haz clic en "Registrarse" para completar el proceso.

2. **Inicio de sesión**:
   - Si ya tienes una cuenta, selecciona "Iniciar sesión".
   - Ingresa tu correo electrónico y contraseña, luego haz clic en "Iniciar sesión".

3. **Inicio de sesión con Facebook**:
   - Puedes optar por iniciar sesión utilizando tu cuenta de Facebook.
   - Haz clic en el botón "Iniciar sesión con Facebook" y autoriza la aplicación.

4. **Navegación**:
   - Una vez autenticado, serás redirigido a la pantalla principal donde podrás ver una lista de posts de ejemplo y personas.

### Cerrar sesión

- Para cerrar sesión, simplemente selecciona el botón de "Cerrar sesión" en el menú de usuario.

## Manual Técnico

### Instalación del Proyecto

1. **Clonar el repositorio**:
   - Si aún no has clonado el repositorio, usa el siguiente comando para clonarlo desde GitHub:
   
   ```bash
   git clone https://github.com/XxEasyxX12/Apk-moviles3.git
   ```

2. **Instalar dependencias**:
   - Navega hasta el directorio del proyecto y ejecuta el siguiente comando para instalar todas las dependencias necesarias:

   ```bash
   npm install
   ```

3. **Configurar Firebase**:
   - Asegúrate de tener un proyecto en **Firebase** y obtener las credenciales del SDK.
   - Coloca las credenciales de Firebase en el archivo `firebaseConfig.js` para conectar la aplicación a Firebase.

4. **Ejecutar el Proyecto**:
   - Para ejecutar la aplicación en modo de desarrollo, usa:

   ```bash
   ionic serve
   ```

   - Para compilar la aplicación para Android, primero asegúrate de tener **Capacitor** y **Android Studio** instalados, luego ejecuta:

   ```bash
   npx cap add android
   npx cap sync
   npx cap open android
   ```

   Desde Android Studio, puedes ejecutar la aplicación en un emulador o dispositivo físico.

### Estructura del Proyecto

- **`src/`**: Contiene los archivos de la aplicación.
   - **`components/`**: Componentes reutilizables como formularios y botones.
   - **`pages/`**: Contiene las pantallas principales de la aplicación (login, posts).
   - **`firebaseConfig.js`**: Configuración de Firebase.
   
- **`capacitor.config.ts`**: Configuración de Capacitor para las plataformas móviles.
- **`package.json`**: Dependencias y scripts del proyecto.

### Flujo de Autenticación

1. El usuario ingresa sus credenciales o inicia sesión con Facebook.
2. Firebase Authentication valida las credenciales del usuario.
3. Si el inicio de sesión es exitoso, el usuario es redirigido a la pantalla principal.
4. Los datos de los usuarios y posts se muestran en la pantalla principal.

### Compilación de la APK

1. **Construir el proyecto**:

   ```bash
   npm run build
   ```

2. **Sincronizar con Capacitor**:

   ```bash
   npx cap sync android
   ```

3. **Abrir el proyecto en Android Studio**:

   ```bash
   npx cap open android
   ```

4. Desde **Android Studio**, puedes generar el APK para distribución.

## Conclusiones

Este proyecto proporciona una aplicación de ejemplo que utiliza **Firebase** para la autenticación y **Ionic** para la construcción de aplicaciones móviles híbridas. La estructura del proyecto permite añadir nuevas características fácilmente, como la integración con otras APIs o la adición de más opciones de autenticación.
