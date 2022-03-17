# Anlegen eines virtuellen Hosts

## Setzen eines DNS-Eintrags

Unter Virtual Hosting wird der Betrieb mehrere Webseiten auf einem Server bezeichnet. Im Regelfall erfolgt die Auswahl des gewünschten Virtual Hosts über den verwendeten Hostnamen der HTTP-Anfrage.

Nachdem sich die öffentliche IP-Adresse der EC2-Instance im AWS Academy Learner Lab von einem Start zum nächsten ändert, wird ein fester Hostname für diese dynamische IP-Adresse konfiguriert.

1. Richten Sie einen selbstgewählten Hostnamen, am besten aus den Anfangsbuchstaben Ihrer Namen ein.
    ```
    curl https://weba-dynamic-dns.glitch.me/api/dnsname/<gewähltes Kürzel>
    ```
    <small>Dieser Dienst verfügt derzeit über keine Fehlerbehandlung oder Absicherung gegen Falscheingaben.</small>
1. Merken Sie sich den Namen, der nach dem Aufruf angezeigt wird, z. B.
    ```
    DNS record created for student.weba.ditm.at with IP address 3.87.225.196.
    ```

Dieser Schritt muss nach jedem Neustart des Labors durchgeführt werden, um die IP-Adresse zu aktualisieren.

## Vorbereitung der Inhalte für den Virtual Host

In den kommenden Beispielen wird **student.weba.ditm.at** als der gewählte Hostname verwendet. Er ist entsprechend durch Ihren persönlichen Hostnamen zu ersetzen.

1. Legen Sie eine passende Verzeichnisstruktur für den *DocumentRoot* des virtuellen Hosts an.
    ```
    sudo mkdir -p /var/www/vhosts/student.weba.ditm.at/htdocs
    ```
1. Setzen Sie die Verzeichniseigentümer für die einfachere Bearbeitung der Inhalte durch den Benutzer *ec2-user*.
    ```
    sudo chown -R ec2-user /var/www/vhosts/student.weba.ditm.at
    ```
1. Legen Sie eine passende HTML-Datei in */var/www/vhosts/student.weba.ditm.at/htdocs/index.html* an.
    ```
    nano /var/www/vhosts/student.weba.ditm.at/htdocs/index.html
    ```

Als Beispiel für diese Startseite können Sie das folgende HTML-Dokument verwenden:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>TEST</title>
  </head>
  <body>
    <h1>Es funktioniert!</h1>
  </body>
</html>
```

## Konfiguration des HTTP Servers

Der Webserver kennt diesen Virtual Host noch nicht, dieser muss in der Konfiguration angelegt werden. 

1. Legen Sie eine Konfiguration für den Virtual Host in */etc/httpd/conf.d/student.weba.ditm.at.conf* an. 
    ```
    <VirtualHost *:80>
      ServerName student.weba.ditm.at
      DocumentRoot /var/www/vhosts/student.weba.ditm.at/htdocs
    </VirtualHost>
    ```

1. Laden Sie die Konfiguration des Webservers neu, um die Änderungen zu übernehmen.
    ```
    sudo systemctl reload httpd
    ```
1. Testen Sie die Erreichbarkeit des virtuellen Hosts durch Aufruf von http://student.weba.ditm.at.

## Hinweis zur Struktur der Verzeichnisse und der Konfigurationsdateien

Je nach Linux-Distribution sind die Speicherorte für Konfigurationsdateien und Dokumente unterschiedlich.

So liegen in anderen Distributionen alle Dokumente in Verzeichnissen unterhalb von */srv/www*. Dieser Pfad würde dem Filesystem Hierarchy Standard entsprechen.

In Debian liegen die Konfigurationsdateien für den HTTP-Server in */etc/apache2*. Für die virtuellen Hosts werden zwei Verzeichnisse verwendet, nämlich */etc/apache2/sites-available* und */etc/apache2/sites-enabled*. Die aktivierten Virtual Hosts in *sites-enabled* verweisen dabei per symbolischen Link auf die entsprechende Konfigurationsdatei in *sites-available*. Das Anlegen dieser symbolischen Links wird dabei durch Skripte **a2ensite** und **a2dissite** unterstützt.
