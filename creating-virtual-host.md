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

## Konfiguration des HTTP Servers

