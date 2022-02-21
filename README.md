# DBServer
sistema base para estas implementacion  Ubuntu 20

# Postgresql

para comprobar la version 

apt install postgresql-client-common




Para desinstalar PostgreSQL en Linux Mint o en Ubuntu, ejecuta los siguientes comandos.

{% filename %}command-line{% endfilename %}
$ dpkg -l | grep postgres


Con el comando anterior obtienes una lista de todos los paquetes PostgreSQL instalados en tu servidor, con esto procedemos a des instalarlos con el siguiente comando, en mi caso quedo así.

{% filename %}command-line{% endfilename %}
$ sudo apt-get --purge remove postgresql-x.x postgresql-client-x.x postgresql-client-common postgresql-common postgresql-contrib postgresql-contrib-x.x

Sustituye x.x según la versión que tienes instalada de PosgreSQL.

## Introducción

Los sistemas de administración de bases de datos relacionales son un componente clave de una gran cantidad de aplicaciones y sitios web. Proporcionan una alternativa estructurada para almacenar la información, organizarla y acceder a ella.

PostgreSQL, o Postgres, es un sistema de administración de bases de datos relacionales que proporciona una implementación del lenguaje de consulta SQL. Cumple con los estándares y tiene muchas funciones avanzadas como transacciones fiables y concurrencia sin bloqueos de lectura.

Esta guía demuestra cómo instalar Postgres en un servidor Ubuntu 20.04. También proporciona algunas instrucciones para la administración general de la base de datos.
Requisitos previos

Para completar este tutorial, necesitará un servidor de Ubuntu 20.04 configurado conforme a nuestra Guía de configuración inicial de servidores para Ubuntu 20.04. Una vez completado este tutorial de requisitos previos, su servidor debería contar con un non-root user con permisos sudo y un firewall básico.

Paso 1: Instalar PostgreSQL
Los repositorios predeterminados de Ubuntu contienen paquetes de Postgres, para que pueda instalarlos utilizando el sistema de empaquetado apt.

Si no lo hizo recientemente, actualice el índice del paquete local de su servidor:

$sudo apt update

Luego, instale el paquete de Postgres junto con un paquete -contrib, que agrega algunas utilidades y funcionalidades adicionales:

$sudo apt install postgresql postgresql-contrib

Ahora que el software está instalado, podemos analizar su funcionamiento y la forma en que puede diferenciarse de otros sistemas de administración de bases de datos relacionales que pueda haber utilizado.

Paso 2: Utilizar roles y bases de datos de PostgreSQL

Por defecto, Postgres utiliza un concepto llamado “roles” para gestionar la autenticación y la autorización. Estos son, en algunos aspectos, parecidos a las cuentas normales de estilo Unix, pero Postgres no distingue entre los usuarios y los grupos, y en su lugar prefiere el término más flexible de “rol”.

Tras la instalación, Postgres se configura para usar la autenticación ident. Esto significa que asocia los roles de Postgres con una cuenta de sistema Unix o Linux correspondiente. Si existe un rol dentro de Postgres, un nombre de usuario de Unix o Linux con el mismo nombre puede iniciar sesión ocupando ese rol.

El procedimiento de instalación creó una cuenta de usuario llamada postgres, que se asocia con el rol predeterminado de Postgres. Para usar Postgres, puede iniciar sesión en esa cuenta.

Existen algunas maneras de usar esta cuenta para acceder a Postgres.

Cambiar a la cuenta de postgres
Cambie a la cuenta de postgres en su servidor escribiendo lo siguiente:

$sudo -i -u postgres