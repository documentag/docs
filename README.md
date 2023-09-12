# docs
docs.documentag.com

format plików archiwum zawierające dane:

    
    
    schema/ - schema for commands
      pdf.xslt
      pdf_ocr.xslt
      create.xslt
      add_table.xslt
      add_table.xslt
      add_rightx.xml
        
    data/ - data tables, history changes (commands) data inputs, e.g.: add icon, extracted ocr data
      history.xml      
      ops.xml
      files.xml
      rights.xml
      api.xml
      js.xml      
    
    src/ - all uploded inputs from email, api
      file.pdf
      ocr.txt
      icon.svg
      icon.png
      markdown.md
      favicon.ico

    
    index.html -   redndered format with xslt schema from xml data and included binary as name of file
        <meta> - describe the source file
        <body> - include all path to data, give the rights to update file



## Użycie


+ documentag render for browser
+ documentag host for machine
+ recordns to host on FaaS platform
    + public
    + private


## Standards

+ [MHTML - Wikipedia](https://en.wikipedia.org/wiki/MHTML)



An MHTML file is a web page archive format. It is meant to be stored and viewed but not to be edited directly.

However, you can easily extract the MHTML file to a regular HTML document (with linked files), edit it with your favorite HTML editor and then export it back to an MHTML archive (including the linked files).

you can open/save between HTML and MHTML files

### features

+ encryption
+ serialization
+ archive
+ compress
+ minimize (css, js, html)



### 1. W dowolnej przeglądarce internetowej lokalnie

html
```bash
documentag -url_from_zip github.com/documentag/docs/archive/refs/heads/main.zip -render_to_html index.html
```

lub

mhtml
```bash
documentag -url_from_zip github.com/documentag/docs/archive/refs/heads/main.zip -render_to_mhtml index.mhtml
```


open document
```bash    
open index.html 
```

### 2. Na serwerze lub lokalnie w formie uslugi

systemd stop,start,status

tylko do doczytu, renderowania
```bash
documentag -url_from_zip github.com/documentag/docs/archive/refs/heads/main.zip -static_host localhost -static_port 80
```

z zapisem danych 
```bash
documentag -url_from_zip github.com/documentag/docs/archive/refs/heads/main.zip -static_host localhost -static_port 80 -admin_host localhost -admin_port 8080
```


### 3. Poprzez konfigurację cdns na publicznej platformie FaaS

repozytorium git do odczytu
```bash
recordns provider ADD doc.domain.com CNAME git-static.faas.ovh
recordns provider ADD doc.domain.com TXT github.com/documentag/example.git
```

repozytorium git do zapisu
```bash
recordns provider ADD doc-admin.domain.com CNAME git-admin.faas.ovh
recordns provider ADD doc-admin.domain.com TXT github.com/documentag/example.git
```

lub z pliku archiwum zip

```bash
recordns provider ADD doc.domain.com CNAME zip-static.faas.ovh
recordns provider ADD doc.domain.com TXT github.com/documentag/docs/archive/refs/heads/main.zip
```


private user faas server with app and data definition and credentials from env variables

```bash
recordns provider ADD doc.domain.com CNAME username.oneday.run
recordns provider ADD git-app.doc.domain.com TXT github.com/documentag/docs.git
recordns provider ADD zip-data.doc.domain.com TXT github.com/documentag/docs/archive/refs/heads/main.zip
```


## Formaty danych


+ w formacie archiwum ze strukturą jak wyżej
+ w formacie html z tymi metadanymi wewnątrz


