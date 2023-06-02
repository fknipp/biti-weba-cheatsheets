# Einrichtung des OWASP Juice Shop

[OWASP Juice Shop](https://owasp.org/www-project-juice-shop/) ist eine Anwendung zum Erkennen von Sicherheitslücken in modernen Webapplikationen.

## Installation von Node.js

Die Installation erfolgt gemäß der [von Amazon beschriebenen Vorgehensweise](
https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-up-node-on-ec2-instance.html).

1. Installation des Node Version Managers
    ```
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
    ```
1. Aktivieren von nvm
    ```
    . ~/.nvm/nvm.sh
    ```
1. Installation von Node.js in der aktuellen LTS-Version
    ```
    nvm install v16
    ```

## Testen von Node.js

```
node -e "console.log(process.version)"
```

## Installation des OWASP Juice Shop

Die Installation erfolgt gemäß [Pwning OWASP Juice Shop](https://pwning.owasp-juice.shop/part1/running.html) aus dem TGZ-Archiv.

1. Herunterladen des Archivs
    ```
    wget https://github.com/juice-shop/juice-shop/releases/download/v14.0.1/juice-shop-14.0.1_node16_linux_x64.tgz
    ```
1. Entpacken des Archivs
    ```
    tar xvfz juice-shop-14.0.1_node16_linux_x64.tgz
    ```

## Start des OWASP Juice Shop

1. Installation der Abhängigkeiten
    ```
    cd juice-shop_14.0.1
    npm start
    ```

## Zugriff auf den OWASP Juice Shop

Für den Zugriff kann entweder der Port 3000 in den Sicherheitsrichtlinien geöffnet oder ein Reverse Proxy gemäß [Anleitung](adding-reverse-proxy.md) eingerichtet werden.

## Alternative Einrichtung über Feld Benutzerdaten

Beim Starten einer EC2-Instanz können direkt Befehle ausgeführt werden. Diese müssen in das Feld Benutzerdaten eingegeben werden ([Quelle](https://pwning.owasp-juice.shop/part1/running.html#amazon-ec2-instance)).

```
#!/bin/bash
yum update -y
yum install -y docker
service docker start
docker pull bkimminich/juice-shop
docker run -d -p 80:3000 bkimminich/juice-shop
```

Beim ersten Start der Instanz wird auch gleich die Anwendung gestartet. Bei späteren Starts muss am Prompt die letzte Zeile eingegeben werden.
