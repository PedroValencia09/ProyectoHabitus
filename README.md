# ProyectoHabitus

# 1. VENTANA LOGIN
La función mostrar_login() es parte de la interfaz gráfica de la aplicación Habitus +, desarrollada con Python y la biblioteca tkinter. Esta función permite que los usuarios inicien sesión en la aplicación o accedan a la pantalla de registro en caso de que aún no tengan una cuenta. También se encarga de validar las credenciales ingresadas y redirigir al usuario a la siguiente ventana del sistema si los datos son correctos.

# Objetivo de la función
El objetivo principal de esta función es proporcionar una ventana de inicio de sesión clara, intuitiva y funcional. A través de esta ventana, el usuario puede:

- Ingresar sus credenciales (correo y contraseña).
- Acceder a la siguiente parte de la aplicación si los datos son correctos.
- Ser redirigido a la ventana de registro en caso de no tener cuenta.
- Salir del modo pantalla completa presionando la tecla ESC.

# Herramientas utilizadas
- tkinter: Biblioteca estándar de Python para interfaces gráficas.
- Toplevel: Se utiliza para crear una nueva ventana que no reemplaza la principal.
- messagebox: Permite mostrar mensajes emergentes de advertencia o error.
- Variables globales: Se hace uso de variables como usuario_actual y constantes de color (COLOR_FONDO, COLOR_VERDE, etc.) definidas en otras partes del programa.

#  Creación de la ventana
La función inicia creando una nueva ventana Toplevel que ocupa toda la pantalla, con fondo personalizado.

#  Elementos visuales
Se colocaron los siguientes elementos en la ventana:

- Título de la aplicación.
- Mensaje de bienvenida.
- Campo de entrada para correo electrónico.
- Campo de entrada para contraseña (con texto oculto).
- Botón para iniciar sesión.
- Botón para ir al registro de nuevo usuario.

#  Validación de datos (iniciar_sesion)
Primero se obtienen los datos ingresados por el usuario y se eliminan posibles espacios vacíos.

- Luego se verifica que ambos campos estén llenos.
- Si los datos coinciden con el contenido de usuario_actual, se oculta la ventana actual y se llama a mostrar_rutina().
- Si los datos son incorrectos, se muestra un mensaje de error.
- Si hay campos vacíos, se muestra una advertencia.

#  Redirección al registro (ir_a_registro)
Esto abre la ventana de registro y mantiene la ventana de login como base para conservar el control de navegación.





<img width="1917" height="1079" alt="Captura de pantalla 2025-07-11 092925" src="https://github.com/user-attachments/assets/421f1934-cd41-4027-90a2-429b8c7be09f" />




# 2. VENTANA REGISTRO
Esta parte del código pertenece a la ventana de registro de usuario. Es la pantalla que se abre cuando alguien todavía no tiene cuenta y necesita crear una para poder usar la app. Como estoy trabajando en la versión beta de Habitus +, decidí mantener el proceso simple pero funcional.

# Objetivo
La función mostrar_ventana_registro(ventana_login) abre una nueva ventana a pantalla completa donde el usuario puede escribir su nombre completo, su correo electrónico y una contraseña.
Cuando el usuario termina de llenar los campos, puede presionar el botón "Registrar", y si todo está correcto, los datos se guardan en una variable global llamada usuario_actual. Después de eso, la ventana se cierra y lo regresa automáticamente a la pantalla de login.

# ¿Cómo funciona la transición entre ventanas?
Cuando esta función se llama, lo primero que hace es ocultar la ventana de login:
Eso es para que no estén dos ventanas activas al mismo tiempo. Luego se crea una nueva ventana (registro_window) con Toplevel(), lo cual es útil porque no cierra la app principal, solo agrega una ventana encima.
Cuando el usuario termina el registro o presiona "Volver al login", esa ventana se destruye y vuelve a mostrar la de login:
Esto hace que la navegación sea fluida y no rompa el flujo de la app.

# ¿Qué pasa al registrar?
Cuando se presiona el botón Registrar, se ejecuta la función registrar_usuario():
-Se recogen los datos que el usuario escribió.
-Se verifica que ninguno esté vacío.

# Si todo está bien:
-Se guardan los datos en la variable global usuario_actual.
-Se asigna el nivel "Principiante" por defecto.
-Se muestra un messagebox avisando que el registro fue exitoso.
-Y se vuelve a la ventana de login.

Si algún campo está vacío, se muestra una advertencia pidiendo que complete todos los datos.


# Por qué es importante esta parte
Aunque no está conectada a una base de datos todavía (porque esta es una beta), esta ventana simula muy bien cómo sería un registro real. Además, me sirve para hacer pruebas de navegación, validación de formularios y estructura general del sistema sin tener que usar datos reales ni usuarios externos.




<img width="1919" height="1030" alt="Captura de pantalla 2025-07-11 093302" src="https://github.com/user-attachments/assets/b8462649-4b68-46b3-828d-0ce0a0b62545" />







# 3. VENTANA CUENTAS CON UNA RUTINA
Esta función muestra una pantalla donde el usuario debe responder si ya cuenta con una rutina establecida. Forma parte del flujo principal de la aplicación Habitus + y sirve para dirigir al usuario hacia su experiencia personalizada dentro de la app, dependiendo de su respuesta.

# ¿Qué hace esta función?
La función mostrar_rutina(login_window) se encarga de:
- Ocultar la ventana de login (de donde viene el usuario).
- Mostrar una nueva ventana a pantalla completa donde se le pregunta:
“¿Cuentas con alguna rutina?”

# Ofrecer dos botones:

- SÍ: para usuarios que ya tienen una rutina, y redirige a la ventana principal de la app.
- NO: para usuarios nuevos que todavía no tienen rutina, y los lleva a la sección de "Mi Yo Ideal" para definirla.

# ¿Por qué es importante esta pantalla?
Esta parte del flujo es esencial porque define cómo se va a comportar la aplicación a partir del usuario que la esté usando. Si es alguien nuevo, lo guiamos para construir su rutina desde cero. Si es alguien que ya tiene una rutina, lo llevamos directo al inicio.
Es una decisión que marca el camino en la app, por eso lo presento de forma clara y con solo dos opciones.



<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/7e89644e-2235-4612-ada7-8b5554002ee6" />








# 4. VENTANA MI YO IDEAL
Esta función representa una de las pantallas más importantes de la experiencia inicial dentro de la app Habitus +. Aquí, el usuario puede elegir los hábitos saludables que le gustaría adoptar, sirviendo como punto de partida para construir una rutina personalizada.

# ¿Qué hace esta función?
La función mostrar_mi_yo_ideal() abre una ventana a pantalla completa donde el usuario debe seleccionar manualmente qué hábitos le interesan. Es ideal para quienes aún no tienen una rutina, ya que permite armar una desde cero.
Actualmente, la versión beta incluye tres hábitos básicos:

- Caminar🚶
- Leer📖
- Dormir🛏️
El usuario puede marcar uno o varios hábitos y luego presionar el botón "Aceptar" para guardar su selección.


# ¿Cómo se guardan los hábitos?
Cada hábito se asocia a una variable booleana (tk.BooleanVar), que indica si está marcado o no. Cuando el usuario hace clic en "Aceptar", se ejecuta la función guardar_seleccion():

-Se limpia la lista habitos_activos.
-Se agregan los hábitos seleccionados.
-Se cierra la ventana actual (ideal_window.destroy()).
-Luego se muestra la ventana con la rutina personalizada.

# ¿Por qué es importante esta pantalla?
Esta pantalla representa un momento clave donde el usuario define su propia experiencia dentro de la aplicación. En vez de imponer una rutina genérica, se le permite construir una basada en lo que realmente desea mejorar.
Es parte del enfoque de personalización del hábito, y también facilita que el usuario se involucre desde el primer momento.

# 5. VENTANA RUTINA PREDISEÑADA

# ¿Qué hace esta función?
Esta función abre una ventana en pantalla completa que muestra al usuario su rutina inicial, basada en los hábitos que seleccionó previamente en la pantalla de "Mi yo ideal". Es una forma de presentar una rutina personalizada desde el principio del uso de la app.

# ¿Cómo lo hace?
Crea una nueva ventana (Toplevel):
Se abre una ventana llamada "Tu rutina inicial" en modo pantalla completa, con fondo personalizado.

# Contenedor de hábitos:
Dentro de la ventana, se crea un Frame que almacena la información de cada hábito activo.
Aquí entra en juego la lista habitos_activos, que ya contiene los hábitos seleccionados por el usuario.

# Despliegue dinámico de la rutina:
Por cada hábito en habitos_activos, se consulta la información en habitos_info (como tiempo sugerido y días recomendados). Esta info se muestra en un cuadro tipo tarjeta.
Por ejemplo, si el usuario eligió Caminar, se mostrará algo como:

- Caminar - Nivel 1
- Tiempo sugerido: 30 min
- Días: Lunes, Miércoles, Viernes
Botón Aceptar:
Al final, hay un botón que permite continuar (cierra esta ventana y lleva al usuario al inicio).

# ¿Por qué es importante?
Esta parte del código le da al usuario una sensación de personalización desde el principio. No solo elige hábitos al azar, sino que ve reflejadas sus decisiones en una rutina inicial clara y visual. Esto motiva y da dirección desde la primera vez que se usa la app.

# 6. Ventana Principal de Inicio 
Esta función crea la ventana principal de la app Habitus + que se muestra después de que el usuario haya iniciado sesión o completado su rutina personalizada. Es el panel central desde donde el usuario puede acceder a diferentes funcionalidades.

# ¿Qué hace esta función?
mostrar_inicio() abre una nueva ventana en pantalla completa llamada "Inicio" y contiene:

Un conjunto de botones que llevan a diferentes secciones de la aplicación:

- Mira tu Rutina
- Progreso
- Editar Rutina
- Estadísticas
Esta ventana funciona como un menú principal para navegar fácilmente por las funcionalidades clave.


# ¿Qué pasa al hacer clic en los botones?
Cada botón ejecuta una función que abre la ventana o sección correspondiente:

- Mira tu Rutina: Abre la rutina personalizada del usuario.

- Progreso: Muestra el avance del usuario en sus hábitos.

- Editar Rutina: Permite modificar la rutina establecida.

- Estadísticas: Muestra datos estadísticos sobre el comportamiento del usuario.

Esto facilita que el usuario pueda navegar sin complicaciones y acceda rápido a las herramientas que necesita.

# ¿Por qué es importante esta pantalla?
Es la puerta de entrada a la experiencia completa del usuario dentro de la app. Desde aquí puede gestionar sus hábitos, ver su progreso y tomar acciones para mejorar. Tener una ventana clara, organizada y con botones bien definidos mejora mucho la usabilidad y la satisfacción del usuario.

# 7.  VENTANA DE RUTINA PERSONAL 
Esta función abre una ventana que muestra al usuario su rutina personalizada de hábitos. Es una vista donde puede visualizar los hábitos activos que ha seleccionado, junto con información útil como el tiempo asignado y los días en que se realizan.

# ¿Qué hace esta función?
mostrar_mi_rutina() crea una nueva ventana a pantalla completa que:
- Muestra un encabezado con el título y un botón para regresar.
- Presenta una lista de hábitos activos con detalles como el tiempo estimado por hábito y los días asignados.
- Permite al usuario marcar hábitos como realizados 

# ¿Qué pasa con los datos mostrados?
Los datos de cada hábito vienen de dos variables:
- habitos_activos: contiene los nombres de los hábitos activos del usuario.
- habitos_info: es un diccionario que guarda la información detallada por hábito, como el tiempo y los días.

# ¿Por qué es importante esta pantalla?
Es la sección donde el usuario revisa su rutina diaria. Aunque no permite editar (eso se hace en otra pantalla), esta ventana ayuda a visualizar y seguir el plan de hábitos que se ha definido. Es especialmente útil para reforzar la disciplina y llevar un orden cada día.

# 8. VENTANA DE PROGRESO 
Esta función abre una ventana donde el usuario puede registrar su progreso diario relacionado con los hábitos que ha seleccionado previamente. Es una herramienta clave para que el usuario pueda llevar un seguimiento de lo que ha hecho en un día, cuánto tiempo le dedicó a un hábito y en qué fecha.

# ¿Qué hace esta función?
mostrar_progreso() crea una nueva ventana a pantalla completa que:
- Muestra un encabezado con el título “Progreso” y un botón de regreso.

Incluye campos para que el usuario registre:

- El día en el que hizo el hábito.
- Cuánto tiempo le dedicó.
- A qué hábito corresponde ese registro (seleccionado desde un menú desplegable).
Agrega un botón para guardar el progreso registrado, el cual en esta versión solo muestra un mensaje de confirmación (aún no guarda en base de datos o archivo real).

# ¿Qué pasa con los datos que se ingresan?
Cuando se hace clic en el botón “Guardar Progreso”, se ejecuta la función interna guardar_progreso(), que:
- Toma los datos ingresados en los campos (día, tiempo, hábito).
- Verifica que no estén vacíos.
- Muestra una alerta informativa (messagebox.showinfo) con los datos registrados.
- Borra el contenido de los campos para permitir un nuevo ingreso.

# ¿Por qué es importante esta pantalla?
Esta pantalla es clave porque le permite al usuario hacer un seguimiento diario de sus hábitos. Registrar el día, el hábito y el tiempo ayuda a mantener la constancia y a tomar conciencia del progreso personal.

# 9. VENTANA EDITAR RUTINA 
Esta función abre una ventana donde el usuario puede editar su rutina de hábitos. Es una sección pensada para que el usuario seleccione un hábito activo y lo modifique, o también agregue uno nuevo.

# ¿Qué hace esta función?
mostrar_editor_rutina() crea una nueva ventana a pantalla completa que:
- Muestra un encabezado con un botón de regreso y un título.
- Presenta una serie de hábitos activos, cada uno con un ícono, su nombre y un botón de “Aceptar” para editarlo.
- Incluye un botón flotante (+) en la parte inferior izquierda para agregar un nuevo hábito.
Organiza visualmente los hábitos activos con íconos grandes y diseño amigable.


# ¿Por qué es importante esta pantalla?
Esta ventana es esencial porque permite modificar hábitos activos, personalizar su configuración y añadir otros nuevos. Es el corazón del editor, desde donde el usuario toma control de su rutina.
Aunque la versión actual aún no hace cambios en tiempo real sobre el checkbox o el diseño, la funcionalidad de navegación y selección ya está integrada y operativa, lo cual es un gran paso en esta versión beta de la app.


# 10. PATALLA EDICION INDIVIDUAL DE CADA HABITO
Esta función abre una pantalla específica para editar los detalles de un hábito activo previamente seleccionado por el usuario. Se usa cuando el usuario da clic en "Aceptar" desde la pantalla del Editor de Rutina.

# ¿Qué hace esta función?
mostrar_edicion_habito(nombre_habito) crea una ventana a pantalla completa que permite al usuario:

- Cambiar los días en que realiza el hábito.
- Cambiar el tiempo estimado para realizarlo.
- Eliminar el hábito si ya no lo quiere en su rutina.

# Eliminar hábito
En la parte inferior, hay un botón rojo que dice "Eliminar hábito". Este:
-Llama a la función confirmar_eliminacion_habito().
-Muestra una alerta de confirmación antes de eliminar el hábito (útil para evitar errores).

# Conclusión
La función mostrar_edicion_habito() es fundamental en Habitus+ porque permite ajustar detalles clave de los hábitos personalizados. Desde aquí, el usuario puede modificar su rutina a medida que cambian sus necesidades o tiempos. Además, da la opción de eliminar hábitos, lo cual mantiene la rutina limpia y relevante. Una función sencilla, pero potente y esencial para una experiencia personalizada y dinámica.

$ 10. VENTANA ELIMINAR HABITO
Esta función muestra una ventana emergente que sirve como alerta de confirmación para eliminar un hábito específico. Es una medida de seguridad dentro de la app para evitar que el usuario borre hábitos por accidente.

# ¿Qué hace esta función?
Cuando el usuario hace clic en "Eliminar hábito", se abre una mini ventana emergente donde se le pregunta:
"¿Deseas realizar esta acción?"

 Botón “Sí”:
Si el usuario confirma:
Se revisa si el hábito está en la lista habitos_activos.
Se elimina de esa lista.
Se cierran ambas ventanas: la de confirmación y la de edición.
Se vuelve a abrir el Editor de Rutina, ya con el hábito eliminado.


# ¿Por qué es importante esta función?
Este tipo de confirmaciones es buena práctica en interfaces de usuario. En apps reales, borrar algo sin querer puede arruinar la experiencia. Esta pequeña ventana le da al usuario la oportunidad de reconsiderar antes de eliminar.
Además, se destruye la ventana del hábito y se actualiza la interfaz automáticamente con mostrar_editor_rutina() para que el cambio sea inmediato y visualmente claro.

# 11. VENTANA DE AGREGAR HABITO
Esta función se encarga de mostrar una ventana de pantalla completa donde el usuario puede agregar un nuevo hábito predefinido a su rutina.

# ¿Cuál es el objetivo?
Permitir que el usuario seleccione uno de los hábitos sugeridos ("Caminar", "Leer", "Dormir") para añadirlo a su lista personal. Esta es una forma sencilla de empezar a armar su rutina con hábitos comunes.

# Parte funcional: agregar_habito(nombre)
Esta función se activa cuando el usuario presiona uno de los botones de hábitos. Hace lo siguiente:

- Verifica que el hábito no esté ya en la lista habitos_activos.
- Si no está, lo agrega a esa lista.
- Llama a mostrar_info_habito(nombre) para abrir su vista individual.
- Cierra esta ventana de agregar hábito.
- Si hay una ventana abierta llamada "Editor Rutina", la cierra para que se actualice.
- Vuelve a abrir mostrar_editor_rutina() con los cambios aplicados.
- Este paso de cerrar y volver a abrir el editor es importante porque refresca la información automáticamente, sin necesidad de reiniciar la app.

# ¿Por qué es útil esta función?
Le da al usuario una forma rápida y guiada de crear su rutina. No tiene que escribir el hábito ni pensar en nombres, solo elige uno y listo. Esto es ideal para una primera versión beta de la app, donde queremos que la experiencia sea lo más simple y fluida posible.

# VENTANA INFO NUEVO HABITO
Cuando se llama esta función, se abre una nueva ventana a pantalla completa con los datos del hábito que el usuario eligió. Estos datos se sacan del diccionario habitos_info, que contiene info como:
- tiempo: cuánto tiempo se recomienda dedicarle al hábito.
- dias: qué días se sugiere hacerlo.
- descripcion: una pequeña explicación motivacional o funcional.


# ¿Por qué esta parte es importante?
Porque la idea es que el usuario no solo agregue hábitos por agregar, sino que entienda qué está haciendo y por qué. Mostrar esta info refuerza el propósito del hábito y ayuda a generar más compromiso con la rutina.

#12. VENTANA ESTADISTICA 
Esta función abre una nueva ventana donde el usuario puede ver sus estadísticas actuales dentro de la app Habitus+. Es una especie de “panel de progreso” que ayuda a visualizar cómo van sus hábitos y su nivel como si fuera un juego.

# ¿Qué se muestra en esta pantalla?
La ventana está organizada con diseño limpio y dividido en secciones:


- RACHA DÍAS
Indica cuántos días seguidos el usuario ha cumplido sus hábitos.

Por ahora muestra "00" como valor de prueba.

- RACHA HÁBITOS
Muestra cuántos hábitos seguidos se han mantenido activos.

También inicia en "00", pero más adelante se puede conectar con una base de datos o contador real.

# ¿Por qué es útil esta función?
Porque visualizar el progreso es clave para mantener la motivación. Ver que llevas una racha de días o que estás cerca del siguiente nivel hace que el usuario quiera seguir. Y como es una beta, este diseño básico permite seguir iterando fácilmente.

# 13. VENTANA PERFIL
Esta función abre una ventana donde el usuario puede ver y editar su información personal dentro de la aplicación Habitus+. Es la sección dedicada a mostrar datos básicos como nombre, apellido, correo, contraseña y nivel actual.

# ¿Qué hace esta función?
mostrar_perfil() crea una ventana nueva, a pantalla completa, que:
- Muestra un encabezado con un botón para regresar.
- Presenta un avatar (círculo negro) y el nombre completo del usuario.
- Permite editar campos de texto: nombre, apellido, correo y contraseña.
- Muestra el nivel del usuario en modo solo lectura.
- Incluye un botón para guardar los cambios realizados.


# ¿Qué pasa con los datos mostrados y guardados?
Los datos iniciales provienen del diccionario global usuario_actual.
- Cuando el usuario edita y presiona "Aceptar", los campos actualizados se guardan en usuario_actual.
- Se muestra un mensaje informando que los cambios se guardaron.
- La ventana se cierra después de guardar.

# ¿Por qué es importante esta pantalla?
El perfil es el centro de la personalización del usuario y da control sobre su información básica. Poder actualizar correo y contraseña es fundamental para mantener la cuenta segura y actualizada.





