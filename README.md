# M347 - Dockerfile

## Vorwort

In diesem Projekt wird ein Image erstellt, welches einen Webserver startet und eine Webpage mit den Kontaktdaten des Autors anzeigt.

Als Technologie wird Apache im Zusammenspiel mit php8 verwendet.

Die fertigen Dateien können hier heruntergeladen werden:

1. [Dockerfile](https://github.com/damblatt/M347-Dockerfile/blob/main/Dockerfile)
2. [index.php](https://github.com/damblatt/M347-Dockerfile/blob/main/index.php)

## Umgebung einrichten

````bash
mkdir m347-dockerfile
cd m347-dockerfile
````

## Dockerfile erstellen

````bash
touch Dockerfile
nano Dockerfile
````

... und folgenden Inhalt einfügen:

````dockerfile
FROM php:8-apache
COPY index.php /var/www/html
````

## Index.php erstellen

````bash
touch index.php
````

... und folgenden Inhalt einfügen:

````html
<!DOCTYPE html >
<html >
<head >
<title >M347</title >
<meta charset ="utf-8" />
</head >
<body >
<h1>M347 - Webpage mit Dockefile</h1>
<?php
$vorname = "Damian";
$nachname = "Blatt";
echo "Autor: ${vorname} ${nachname}";
?> 
</body >
</html >
````

## Image erstellen

````bash
docker build -t m347-dockerfile
docker image ls
````

Nun sollten u. a. folgende Images aufgeführt werden:

````
REPOSITORY       TAG        IMAGE ID       CREATED              SIZE
m347-dockefile   latest     c5a049e80c58   About a minute ago   458MB
php              8-apache   af944036d594   About a minute ago	458MB
````

##  Container starten

````bash
docker run -d --name m347-dockerfile-container -p 8080:80 m347-dockefile
````

## Webpage aufrufen

Die Webpage kann nun unter _localhost:8080_ aufgerufen werden.

