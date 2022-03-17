# Einrichtung von Let's Encrypt

## Installation des certbot

Für die Installation wird ein zusätzliches Repository installiert. Es nennt sich EPEL (Extra Packages for Enterprise Linux) und enthält das gewünschte Paket.

1. Installieren Sie die zusätzliche Paketquelle.
    ```
    sudo yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
    ```
1. Aktivieren Sie diese Paketquelle.
    ```
    sudo yum-config-manager --enable epel
    ```
1. Installieren Sie die Pakete für die Verwendung von SSL und Let's Encrypt.
    ```
    sudo yum install certbot python2-certbot-apache mod_ssl
    ```

## Einrichtung der SSL-Zertifikate

Die Einrichtung der Zertifikate ist über den **certbot** komplett automatisiert. Um ein Zertifikat für eine Domain einrichten zu können, wird von Let's Encrypt überprüft, ob die einzurichtende Domain überhaupt unter der Kontrolle der anfragenden Stelle ist. Dies geschieht in den meisten Fällen (und auch hier) über die HTTP Challenge.

1. Rufen Sie **certbot** für Ihre Domain auf und beobachten Sie dabei die Ausgaben.
    ```
    sudo certbot --register-unsafely-without-email -d student.weba.ditm.at
    ```
1. Prüfen Sie die Erreichbarkeit und das Zertifikat durch Aufruf von https://student.weba.ditm.at
1. Untersuchen Sie die geänderten und neuen Konfigurationsdateien. Sie finden deren Pfade in der Ausgabe vom Aufruf von **certbot**.