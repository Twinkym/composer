# Introduction

Composer is a tool for dependency management in PHP. It allows you to declare
the libraries your project depends on and it will manage (install/update) them
for you.
Composer es una herramienta para la gestión de dependencias en PHP. Te permite declarar
las librerias de las que depende su proyecto y las gestionará para usted (Instalar/Actualizar). 

## Dependency management

Composer is **not** a package manager in the same sense as Yum or Apt are. Yes,
it deals with "packages" or libraries, but it manages them on a per-project
basis, installing them in a directory (e.g. `vendor`) inside your project. By
default, it does not install anything globally. Thus, it is a dependency
manager. It does however support a "global" project for convenience via the
[global](03-cli.md#global) command.

Composer no es un gestor de paquetes en el mismo sentido como son Yum ó Apt.
Si, negocia con "paquetes" ó librerias, pero los gestiona en un (pre-projecto ó por proyecto)
base,instalandolos en un directorio (e.g. `vendor`) dentro de tu proyecto.
por defecto, no instala nada globalmente. por tanto, es un gerente de dependencias.
Sin embargo admite un proyecto global a traves del comando [global](03-cli.md#global).

This idea is not new and Composer is strongly inspired by node's
[npm](https://www.npmjs.com/) and ruby's [bundler](https://bundler.io/).

Esta idea idea no es nueva y Composer esta fuertemente inspirado por node 
[npm](https://www.npjs.com/) y ruby [bundler](https://bundler.io/).

Suppose:
Supon:

1. You have a project that depends on a number of libraries.
1. Tienes un projecto que depende de varias librerias.
2. Some of those libraries depend on other libraries.
2. Algunas de estas librerias dependen de otras librerias. 

Composer:
Composer:

1. Enables you to declare the libraries you depend on.
1. Le permite declarar las librerias de las que depende.
2. Encuentra que versión de cada paquete puede necesitar ser instalada, y 
   la instala (Lo que significa que la descarga en su projecto).
2. Finds out which versions of which packages can and need to be installed, and
   installs them (meaning it downloads them into your project).
3. You can update all your dependencies in one command.
3. Puede actualizar todas las dependencias con un comando. 

See the [Basic usage](01-basic-usage.md) chapter for more details on declaring
dependencies.
Ver el capitulo [uso basico](01-basic-usage.md) para más detalles en declarando 
dependencias.

## System Requirements
## Requisitos del Systema

Composer requires PHP 5.3.2+ to run. A few sensitive php settings and compile
flags are also required, but when using the installer you will be warned about
any incompatibilities.
Composer requiere PHP 5.3.2+ para ejcutarse. algunas configuraciones sensibles php
y compilar flags (variables) tambien es requerido, pero cuando uses el instalador 
seras alertado sobre cualquier incompatibilidad.

To install packages from sources instead of plain zip archives, you will need
git, svn, fossil or hg depending on how the package is version-controlled.
Para instalar paquetes desde fuentes en lugaar de archivos zip simples, necesitaras 
git, svn, fossil ó hg dependiendo como se controla la versión del paquete.

Composer is multi-platform and we strive to make it run equally well on Windows,
Linux and macOS.
Composer es multiplataforma y nois esforzamos para que funcione igualmente bien en 
windows, Linux and macOS.

## Installation - Linux / Unix / macOS
## Instalación - Linux / Unix / macOS

### Downloading the Composer Executable
### Descargando el ejecutable de Composer

Composer offers a convenient installer that you can execute directly from the
command line. Feel free to [download this file](https://getcomposer.org/installer)
or review it on [GitHub](https://github.com/composer/getcomposer.org/blob/master/web/installer)
if you wish to know more about the inner workings of the installer. The source
is plain PHP.
Composer ofrece un instalador conveniente que puede eejecutar directamente desde 
la linea de comandos. sientete libre para  [descargar este archivo](https://getcomposer.org/installer)
ó revisalo en [GitHub](https://github.com/composer/getcomposer.org/blob/master/web/instaler)
si deseas saber más sobre el funcionamiento interno de el instalador. La fuente 
es simple PHP.

There are in short, two ways to install Composer. Locally as part of your
project, or globally as a system wide executable.
En resumen hay dos formas de instalaar Composer. Local como parte de su proyecto, 
ó globalmente como un ejecutable de todo el sistema.


#### Locally
#### Localmente

To install Composer locally, run the installer in your project directory. See
[the Download page](https://getcomposer.org/download/) for instructions.
Para instalar Composer localmente, ejecute el instalador en el directorio de su
proyecto. Vea [La pagina de descarga](https://getcomposer.org/download/)
para instrucciones.

The installer will check a few PHP settings and then download `composer.phar`
to your working directory. This file is the Composer binary. It is a PHAR
(PHP archive), which is an archive format for PHP which can be run on
the command line, amongst other things.
El instalador comprobara algunas configuraciones PHP y descargará `composer.phar`
a tu directorio de trabajo. este archivo es el binario de Composer. Es un 
PHAR (PHP archivo), que es un formato de archivo PHP que puede ser ejecutado 
en la linea de comandos, entre otras cosas.


Now run `php composer.phar` in order to run Composer.
Ahora ejecuta `php composer.phar` con el fin de ejecutar Composer.

You can install Composer to a specific directory by using the `--install-dir`
option and additionally (re)name it as well using the `--filename` option. When
running the installer when following
[the Download page instructions](https://getcomposer.org/download/) add the
following parameters:
Puede instalar Composer en un directorio especifico usando la opción `--install-dir`
y adicionalmente renombrarlo tambien usando la opción `--filename`. Al ejecutar el instalador 
al seguir [las instrucciones de la pagina de descargas](https://getcomposer.org/download/)
añade los siguientes parametros:


```sh
php composer-setup.php --install-dir=bin --filename=composer
```

Now run `php bin/composer` in order to run Composer.
Ahora ejecuta `php bin/composer`con el fin de ejecutar composer.

#### Globally
#### Globalmente

You can place the Composer PHAR anywhere you wish. If you put it in a directory
that is part of your `PATH`, you can access it globally. On Unix systems you
can even make it executable and invoke it without directly using the `php`
interpreter.
puede colocar el Composer PHAR en cualquier lugar que desee. Si lo pone en 
un directorio que es parte de su `PATH`, podra acceder globalmente. En sistemas 
unix puede incluso hacerlo ejecutable e invocarlo directamente sin el interprete `php`.

After running the installer following [the Download page instructions](https://getcomposer.org/download/)
you can run this to move composer.phar to a directory that is in your path:
Despues de ejecutar el instalador siguiendo 
[las instrucciones de las pagina de descargas](https://getcomposer.org/download/)
puede ejecutar esto para mover composer.phar al directorio que esta en su ruta:

```sh
mv composer.phar /usr/local/bin/composer
```

If you like to install it only for your user and avoid requiring root permissions,
you can use `~/.local/bin` instead which is available by default on some
Linux distributions.
Si desea instalarlo solo para su usuario y evitar requerir permisos root,
puede usar `~/.local/bin` en su lugar, que esta disponible por defecto en algunas 
distribuciones linux.

> **Note:** If the above fails due to permissions, you may need to run it again
> with sudo.
> ##Note: ## Si lo anterior falla debido a los permisos, es posible que deba 
> ejecutarlo nuevamente con sudo.

> **Note:** On some versions of macOS the `/usr` directory does not exist by
> default. If you receive the error "/usr/local/bin/composer: No such file or
> directory" then you must create the directory manually before proceeding:
> `mkdir -p /usr/local/bin`.
> ## Note: ## En algunas versiones de macOS el directorio `/usr`no existe por defecto.
> Si recibe este error "/usr/local/bin/composer: tal archivo ó directorio no existe" 
> entonces debera crear el directorio manualmente antes de proceder:
> `mkdir -p /usr/local/bin`.

> **Note:** For information on changing your PATH, please read the
> [Wikipedia article](https://en.wikipedia.org/wiki/PATH_(variable)) and/or use
> your search engine of choice.
> ##Note: ## Para información al cambiar su ruta, por favor lea el 
> [articulo wikipedia](https://en.wikipedia.org/wiki/path_(variable)) y/ó
> usar buscador que prefiera. 
Now run `composer` in order to run Composer instead of `php composer.phar`.
Ahora ejecute `composer` con el fin de ejecutar composer en lugar de `phpcomposer.phar`

## Installation - Windows
## Instalación - Windows

### Using the Installer
### Usando el inataldor

This is the easiest way to get Composer set up on your machine.
Este es el modo más facil para configurar composer en su computadora.

Download and run
[Composer-Setup.exe](https://getcomposer.org/Composer-Setup.exe). It will
install the latest Composer version and set up your PATH so that you can
call `composer` from any directory in your command line.
Descarga y ejecuta 
[composer-setup.exe](htpps://getcomposer.org/Composer-setup.exe)

> **Note:** Close your current terminal. Test usage with a new terminal: This is
> important since the PATH only gets loaded when the terminal starts.
> ##Note:## Cierre su terminal actual. pruebe de uso con una nueva terminal: Esto 
> es importante ya que la ruta solo se carga cuando el terminal inicia.

### Manual Installation
### Instalación manual

Change to a directory on your `PATH` and run the installer following
[the Download page instructions](https://getcomposer.org/download/)
to download `composer.phar`.
Cambia el directorio en su `path`y ejecuta el instalador siguiendo 
[las instrucciones de la pagina de descargas](htpps://getcomposer.org/download/)
para descargar `composer.phar`.

Create a new `composer.bat` file alongside `composer.phar`:
Crea un nuevo archivo `composer.bat` junto a `composer.phar`:
usando cmd.exe:

Using cmd.exe:

```sh
C:\bin> echo @php "%~dp0composer.phar" %*>composer.bat
```

Using PowerShell:
usando PowerShell:

```sh
PS C:\bin> Set-Content composer.bat '@php "%~dp0composer.phar" %*'
```

Add the directory to your PATH environment variable if it isn't already.
For information on changing your PATH variable, please see
[this article](https://www.computerhope.com/issues/ch000549.htm) and/or
use your search engine of choice.
Añada el directorio a la variable de entorno de su ruta si aun no lo a hecho.
Para información sobre cambiar su variable path (ruta), por favor ver
[este articulo](htpps://www.computerhope.com/issues/ch000549.htm)

Close your current terminal. Test usage with a new terminal:
Cierre su terminal actual. prueba de uso con un nuevo terminal:

```sh
C:\Users\username>composer -V
Composer version 2.0.12 2021-04-01 10:14:59
```

## Using Composer
## Usando Composer

Now that you've installed Composer, you are ready to use it! Head on over to the
next chapter for a short demonstration.
Ahora que ha instalado Composer, esta listo para usarlo! dirijase al siguiente capitulo 
para una corta demostración.

[Basic usage](01-basic-usage.md) &rarr;
