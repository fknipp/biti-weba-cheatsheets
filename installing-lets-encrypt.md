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