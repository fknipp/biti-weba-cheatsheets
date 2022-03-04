# Zugriff auf die EC2-Instanz

## Über den Web-Browser

1. Wählen Sie in der Liste der Instances die gewünschte Instanz mit der Checkbox aus.
1. Drücken Sie auf **Verbinden** oberhalb der Tabelle.
1. Drücken Sie auf **Verbinden** unter dem Formular.

Im Browserfenster wird ein Terminal emuliert. Die Shell wird angezeigt.

## Über SSH

Alternativ kann über SSH auf die Instanz zugegriffen werden. Dazu benötigen Sie die öffentliche IPv4-Adresse dieser Instanz.

1. Drücken Sie im AWS Academy Learner Lab **AWS Details**.
1. Laden Sie mittels **Download PEM** den privaten Schlüssel auf die Festplatte.
1. Öffnen Sie auf Ihrem Computer ein Terminal.
1. Wechseln Sie in das Verzeichnis der Downloads.
1. Starten Sie die Verbindung mittels 
   ```
   ssh -i labuser.pem ec2-user@<öffentliche IPv4-Adresse>
   ```
