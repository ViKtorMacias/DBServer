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
