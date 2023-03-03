# Hinzufügen einer EC2-Instanz

1. Öffnen Sie die AWS Management Console.
1. Öffnen Sie das **Services**-Menü. Wählen Sie **Datenverarbeitung** und weiters **EC2**.
1. Erstellen Sie eine neue Instanz durch Klick auf **Instance starten**
    1. Wählen Sie **Amazon Linux 2 AMI** (vorselektiert) aus.
    1. Wählen Sie für den Instance-Typ **t2.micro** (vorselektiert) aus.
    1. Wählen Sie das vorhandene Schlüsselpaar **vockey** aus.
    1. Wählen Sie die unter **Netzwerkeinstellungen** die Regeln aus:
        1. **Datenverkehr von SSH zulassen** (vorselektiert)
        1. **HTTPS-Datenverkehr aus dem Internet zulassen**
        1. **HTTP-Datenverkehr aus dem Internet zulassen**
    1. Drücke Sie auf **Instance starten**.
    1. Drücken Sie nach Durchführung der Initialisierung **Alle Instances anzeigen**.

Durch Auswahl der Instanz erfahren Sie im Feld Öffentliche IPv4-Adresse die Adresse, über die diese Instanz erreichbar ist. Das Icon links neben der Adresse kopiert die Adresse in die Zwischenablage. Beachten Sie, dass die öffentliche IPv4-Adresse bei jedem Start neu gesetzt wird.