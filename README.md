# ProyectoHabitus

#Introducción VENTANA LOGIN
La función mostrar_login() es parte de la interfaz gráfica de la aplicación Habitus +, desarrollada con Python y la biblioteca tkinter. Esta función permite que los usuarios inicien sesión en la aplicación o accedan a la pantalla de registro en caso de que aún no tengan una cuenta. También se encarga de validar las credenciales ingresadas y redirigir al usuario a la siguiente ventana del sistema si los datos son correctos.

#Objetivo de la función
El objetivo principal de esta función es proporcionar una ventana de inicio de sesión clara, intuitiva y funcional. A través de esta ventana, el usuario puede:

-Ingresar sus credenciales (correo y contraseña).
-Acceder a la siguiente parte de la aplicación si los datos son correctos.
-Ser redirigido a la ventana de registro en caso de no tener cuenta.
-Salir del modo pantalla completa presionando la tecla ESC.

#Herramientas utilizadas
-tkinter: Biblioteca estándar de Python para interfaces gráficas.
-Toplevel: Se utiliza para crear una nueva ventana que no reemplaza la principal.
-messagebox: Permite mostrar mensajes emergentes de advertencia o error.
-Variables globales: Se hace uso de variables como usuario_actual y constantes de color (COLOR_FONDO, COLOR_VERDE, etc.) definidas en otras partes del programa.

#1. Creación de la ventana
La función inicia creando una nueva ventana Toplevel que ocupa toda la pantalla, con fondo personalizado.

#2. Elementos visuales
Se colocaron los siguientes elementos en la ventana:

-Título de la aplicación.
-Mensaje de bienvenida.
-Campo de entrada para correo electrónico.
-Campo de entrada para contraseña (con texto oculto).
-Botón para iniciar sesión.
-Botón para ir al registro de nuevo usuario.

#3. Validación de datos (iniciar_sesion)
Primero se obtienen los datos ingresados por el usuario y se eliminan posibles espacios vacíos.

-Luego se verifica que ambos campos estén llenos.
-Si los datos coinciden con el contenido de usuario_actual, se oculta la ventana actual y se llama a mostrar_rutina().
-Si los datos son incorrectos, se muestra un mensaje de error.
-Si hay campos vacíos, se muestra una advertencia.

#4. Redirección al registro (ir_a_registro)
Esto abre la ventana de registro y mantiene la ventana de login como base para conservar el control de navegación.



