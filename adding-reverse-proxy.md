# Einrichten eines Reverse Proxy

## Vorbereitung

Richten Sie einen zusätzlichen Hostnamen ein.
```
curl https://weba-dynamic-dns.glitch.me/api/dnsname/proxy.student
```

## Einrichtung des Reverse Proxy

Es wird angenommen, dass die Anwendung auf **localhost:8000** betrieben wird.

Die Konfiguration erfolgt in */etc/httpd/conf.d/proxy-8000.conf*.

```
<VirtualHost *:80>
  ServerName proxy.student.weba.ditm.at
  DocumentRoot /var/www/html

  ProxyPass / http://localhost:8000/
  ProxyPassReverse / http://localhost:8000/
</VirtualHost>
```
