# Hinzufügen von Unterstützung für .mjs-Dateien

## Aktuelle Konfiguration

In */etc/httpd/conf/httpd.conf* ist die aktuelle Konfiguration angeführt:

```
<IfModule mime_module>
    #
    # TypesConfig points to the file containing the list of mappings from
    # filename extension to MIME-type.
    #
    TypesConfig /etc/mime.types

    #
    # AddType allows you to add to or override the MIME configuration
    # file specified in TypesConfig for specific file types.
    #
    #AddType application/x-gzip .tgz
    #
    # AddEncoding allows you to have certain browsers uncompress
    # information on the fly. Note: Not all browsers support this.
    #
    #AddEncoding x-compress .Z
    #AddEncoding x-gzip .gz .tgz
    #
    # If the AddEncoding directives above are commented-out, then you
    # probably should define those extensions to indicate media types:
    #
    AddType application/x-compress .Z
    AddType application/x-gzip .gz .tgz

    #
    # AddHandler allows you to map certain file extensions to "handlers":
    # actions unrelated to filetype. These can be either built into the server
    # or added with the Action directive (see below)
    #
    # To use CGI scripts outside of ScriptAliased directories:
    # (You will also need to add "ExecCGI" to the "Options" directive.)
    #
    #AddHandler cgi-script .cgi

    # For type maps (negotiated resources):
    #AddHandler type-map var

    #
    # Filters allow you to process content before it is sent to the client.
    #
    # To parse .shtml files for server-side includes (SSI):
    # (You will also need to add "Includes" to the "Options" directive.)
    #
    AddType text/html .shtml
    AddOutputFilter INCLUDES .shtml
</IfModule>
```

## Ändern der Konfiguration

Um die bestehende Konfigurationsdatei nicht zu ändern, wird eine neue Konfigurationsdatei für die Unterstützung der Dateiendung *.mjs* angelegt.

    sudo nano /etc/httpd/conf.d/support-mjs.conf

In dieser Datei wird der MIME-Type **application/javascript** für diese Endung konfiguriert.

    AddType text/javascript .mjs

Danach ist ein Neuladen der Konfiguration erforderlich.

    sudo systemctl reload httpd
