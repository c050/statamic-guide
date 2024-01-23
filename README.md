# Guía básica de Statamic

## Setup Local en macOS

Primero, se debe instalar [Laravel Herd](https://herd.laravel.com), que incluye *php*, entre otras herramientas necesarias para el funcionamiento de un proyecto de *Statamic*. Se requiere de *macOS* >= 12.0.

Todos los proyectos de PHP dentro de 

	~/Herd 

se van a encontrar disponibles para acceder desde el navegador. 

Luego, para la instalación de *Statamic* se requiere de su respectiva *CLI*. Para instalarla se debe ejecutar el siguiente comando en la terminal, obtenida desde su [documentación](https://statamic.dev/installing/laravel-herd#install-laravel-herd):

	composer global require statamic/cli

Una vez instalada la *CLI*, basta con ejecutar el siguiente comando para crear un nuevo proyecto:

	statamic new project-name

### Troubleshooting

Existe la posibilidad de que la terminal no encuentre el comando *statamic*. En ese caso, se deben seguir las siguientes instrucciones.

1. Identificar el *path* del directorio Composer global bin usando:

		composer global config bin-dir --absolute

2. Copiar el path obtenido en el paso anterior.
3. Abrir el archivo *~/.zshrc* (o *.bashrc* o *.bash_proifile*) en el directorio raíz y añadir

		export PATH="$PATH:{{path_to_composer_global_bin_directory}}"

4. Finalmente, reemplazar *{{path_to_composer_global_bin_directory}}* con el *path* absoluto obtenido desde el paso 2.

## Creación de un proyecto

Tal como se indicó previamente, para crear un proyecto se debe ejecutar el siguiente comando en la terminal dentro de *~/Herd* y seguir los pasos que se muestran en la *CLI*:

	statamic new your-project-name

Luego, se puede acceder al sitio generado desde el navegador accediendo al link:

	http://your-project-name.test

## Panel de control

Para acceder al panel de control, desde donde se pueden manejar múltiples aspectos como las vistas o los *assets*, se debe acceder a:

	http://your-project-name.test/cp
## Opcional, pero recomendado
Si bien la versión actual de *Statamic* es la 4, en el tutorial de instalación de la versión 3 se recomienda instalar *NPM* y *Tailwind* para una mejor experiencia desarrollando el *front end* de la página.

### NPM

*NPM* viene instalado con *Node.js* por lo que basta con instalar node desde su sitio oficial.
Luego, se debe ejecutar el siguiente comando en la terminal para hacer el *build*:

	npm run dev

Si se encuentra en el entorno de desarrollo o

	npm run production

Si se encuentra en el entorno de producción.

### Tailwind

Si bien ya viene incluido en el proyecto creado por *Statamic*, es importante explicar que se tiene un archivo llamado *tailwind.config.js* que permite configurar *Tailwind* a voluntad

## Crear un nuevo usuario

Si bien se puede crear un *superuser* desde la *CLI* al momento de crear el proyecto, también se puede realizar posteriormente desde la consola. Para esto, se debe ejecutar el siguiente comando:

	php please make:user

A continuación, se solicitarán las credenciales del nuevo usuario y si se quiere que sea o no un *superuser*.

Este comando creará un archivo *yaml* con las credenciales del usuario dentro del directorio *users* del proyecto.

## Vistas

Las vistas se encuentran contenidas dentro de *resources/views*.

- *layout.antlers.html* contiene todo el *markup* que tenga que estar presente en todas las vistas
	- *Navigation*
	- *Header*
	- *Footer*
	- Entre otros
- *home.antlers.html* contiene lo que se encuentra en la *landing page* que funciona como *placeholder*

Desde la sección de *Collections -> Pages* del panel de control se pueden observar los *templates* para generar vistas.

Para crear un nuevo *template*, basta con dirigirse a *resources/views* y crear un nuevo archivo, *new-page.antlers.html* y completarlo con el *html* que se requiera. Con esto se genera un *template* disponible desde el panel de control.

Además de contenido estático, se puede añadir contenido dinámico en las vistas desde los templates. Para esto, se llama, desde el *html* a las variables solicitadas usando la siguiente sintaxis:

	{{ variable-name }}

Por ejemplo, si se busca mostrar el contenido de *title*, que fue asignado desde el panel de control, y mostrarlo como un *h1*, basta con escribir un template que contenga:

	<h1> {{ title }} </h1>


# New Project Info

## Superser 

### Email

	coavendano@uc.cl

### Password

	newprojectpassword
