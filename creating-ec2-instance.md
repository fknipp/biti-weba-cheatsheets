# Hinzufügen einer EC2-Instanz

1. Öffnen Sie die AWS Management Console.
1. Öffnen Sie das **Services**-Menü. Wählen Sie **Datenverarbeitung** und weiters **EC2**.
1. Erstellen Sie eine neue Instanz durch Klick auf **Instances starten**
    1. Wählen Sie das erste **Amazon Linux 2 AMI** aus.
    1. Wählen Sie für den Instance-Typ **t2.micro** aus.
    1. Drücken Sie **Überprüfung und Lancierung**.
    1. Klicken Sie den Link **Sicherheitsgruppen bearbeiten**.
        1. Fügen Sie eine Regel für Zielbereich **HTTP** hinzu.
        1. Fügen Sie eine Regel für Zielbereich **HTTPS** hinzu.
        1. Drücken Sie **Überprüfung und Lancierung**.
    1. Drücke Sie auf **Starten**.
    1. Wählen Sie das vorhandene Schlüsselpaar **vockey | RSA** aus.
    1. Bestätigen Sie die Checkbox.
    1. Drücken Sie **Starten der Instances**.
    1. Drücken Sie nach Durchführung der Initialisierung **Instances anzeigen**.

Durch Auswahl der Instanz erfahren Sie im Feld Öffentliche IPv4-Adresse die Adresse, über die diese Instanz erreichbar ist. Das Icon links neben der Adresse kopiert die Adresse in die Zwischenablage. Beachten Sie, dass die öffentliche IPv4-Adresse bei jedem Start neu gesetzt wird.