# docs
docs.documentag.com

format plików archiwum zawierające dane:

    
    
    schema/ - schema for commands
      pdf.xslt
      ocr.xslt            
      table.xslt
      right.xslt
        
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


## Why?

+ Utrzymanie, Maintenance
    + Aktualizacje
    + Zależności
    + Security
     + server
   + software
   + environment
   + 
+ Marketing, Zarządzanie, strategia
+ Administracja operations
+ integracja
    + api
    + webhooks
    + plugins
+ optymalizacja
    + latency
+ learn curve - krzywa uczenia   



## Użycie


+ documentag render for browser
+ documentag host for machine
+ recordns to host on FaaS platform
    + public
    + private


## output formats

+ mhtml
+ zip


## output services

Hereafter is a subset of the link, that contains in my opinion the most convenient ones.

### Python
```bash
python -m http.server 8000
```

### Ruby
```bash
ruby -run -ehttpd . -p8000
```

### Node
```bash
npm install -g http-server
http-server -p 8000
```

### Php
```bash
php -S 127.0.0.1:8000
```

### bash
```bash
while true; do { echo -e "HTTP/1.1 200 OK\r\n$(date)\r\n\r\n<h1>hello world from $(hostname) on $(date)</h1>" |  nc -vl 8080; } done
```

## Standards

+ [angea (Ange Albertini)](https://github.com/angea)
+ [Free Online XSL Transformer (XSLT) - FreeFormatter.com](https://freeformatter.com/xsl-transformer.html)
+ [E-invoice specification | Estonian Association of Information Technology and Telecommunications](https://itl.ee/en/estonian-ict-cluster/real-time-economy/e-invoice-specification/) 

+ [docs/PDF/PDF.md at master · corkami/docs](https://github.com/corkami/docs/blob/master/PDF/PDF.md)
  
+ [meta-module/docs: docs.metamodule.org](https://github.com/meta-module/docs)
Metamodules to prepare multisitemap


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

## Tools

[SingleFile - Chrome Web Store](https://chrome.google.com/webstore/detail/singlefile/mpiodijhokgodhhofbcjdecpffjipkle)
Save a complete page into a single HTML file
SingleFile is an extension that helps you to save a complete page (with CSS, images, fonts, frames, etc.) as a single HTML file.



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

username.oneday.run - user of platform with local user on server with local docker and parameters from TXT 
```bash
recordns ionos.de ADD doc.domain.com CNAME username.oneday.run
recordns ionos.de ADD _config_docker.doc.domain.com TXT dockerhub.com/documentag/docs
recordns ionos.de ADD _config_code.doc.domain.com TXT github.com/documentag/docs.git
recordns ionos.de ADD _config_data.doc.domain.com TXT github.com/documentag/docs/archive/refs/heads/main.zip
```

lub 

```bash
recordns cloudflare.com ADD doc.domain.com CNAME username.oneday.run
recordns cloudflare.com ADD json.doc.domain.com TXT '{ "docker": "dockerhub.com/documentag/docs", "code": "github.com/documentag/docs.git", "data": "github.com/documentag/docs/archive/refs/heads/main.zip"}
```

lub 

```bash
recordns provider ADD doc.domain.com CNAME username.oneday.run
recordns provider ADD config.doc.domain.com TXT github.com/documentag/doc-config.git
```



## Formaty danych


+ w formacie archiwum ze strukturą jak wyżej
+ w formacie html z tymi metadanymi wewnątrz



---
+ [Editing docs/README.md at main · documentag/docs](https://github.com/documentag/docs/edit/main/README.md)
