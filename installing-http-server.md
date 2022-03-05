# Installation des Apache HTTP Servers

## Über Amazon Linux

Amazon Linux basiert auf Fedora. Entsprechend werden für die Paketverwaltung `yum` und `rpm` verwendet.

Zum Erlangen der root-Rechte steht der Befehl `sudo` zur Verfügung. Um dauerhaft zu root zu wechseln, kann 
```
sudo -i
```
ausgeführt werden.

[Mehr Informationen zu Amazon Linux](https://docs.aws.amazon.com/linux/index.html)

## Installation des Apache HTTP Servers

1. Aktualisieren Sie die Paketliste.
    ```
    sudo yum update
    ```
1. Installieren Sie das Paket für den HTTP-Server.
    ```
    sudo yum install httpd
    ```
1. Bestätigen Sie die Frage, ob die Pakete installiert werden sollen, mit Y.

## Starten und Stoppen des Apache HTTP Servers

Fedora Linux verwendet systemd, entsprechend wird `systemctl` zur Bedienung der Dienste verwendet.

- Status des Dienstes
    ```
    sudo systemctl status httpd
    ```
- Start des Dienstes
    ```
    sudo systemctl start httpd
    ```
- Stopp des Dienstes
    ```
    sudo systemctl stop httpd
    ```
- Start des Dienstes beim Systemstart aktivieren
    ```
    sudo systemctl enable httpd
    ```
- Start des Dienstes beim Systemstart deaktivieren
    ```
    sudo systemctl disable httpd
    ```

## Konfigurationsdateien

Die Konfigurationsdateien des Apache-Servers befinden sich in */etc/httpd*. Die Hauptkonfigurationsdatei ist */etc/httpd/conf/httpd.conf*.

Zum Anzeigen von Konfigurationsdateien ohne Leerzeichen und Kommentare empfiehlt sich die Verwendung von `grep`:

```shell
grep -v -E '^\s*(#|$)' /etc/httpd/conf/httpd.conf
```

## Dokumentation

Die Dokumentation des Apache HTTP Servers ist auf https://httpd.apache.org/docs/

Die aktuelle Version kann mittels eines der folgenden Befehle ermittelt werden:

```
rpm -q httpd
httpd -v
```