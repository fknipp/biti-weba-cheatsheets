# Zuweisung einer fixen IP-Adresse

1. Wählen Sie unter **Netzwerk & Sicherheit** den Menüpunkt **Elastic IPs** aus.
1. Starten Sie die Zuweisung einer fixen IP-Adresse mittels **Elastic IP-Adresse zuweisen**.
    1. Beziehen Sie eine Adresse aus dem Amazon-Pool mit IPv4-Adressen durch Klick auf **Zuweisen**.
1. Wählen Sie in der Übersicht die neue IP-Adresse aus. Es öffnet sich die Detailansicht.
1. Wählen Sie **Elastic IP-Adresse zuordnen** in dieser Ansicht.
    1. Wählen Sie die gewünschte EC2-**Instance** aus.
    1. Wählen Sie die entsprechende **Private IP-Adresse** aus.
    1. Drücken Sie auf **Zuordnen**.

Nach Durchführung der Zuordnung sehen Sie die fixe IP-Adresse in der Ansicht der EC2-Instance. Diese bleibt auch beim Stoppen und Starten einer Instance erhalten.