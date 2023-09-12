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

+ w dowolnej przeglądarce internetowej lokalnie

```bash
documentag -url_from_zip github.com/documentag/docs/archive/refs/heads/main.zip -render_to_html index.html
```

```bash    
open index.html 
```

+ na serwerze lub lokalnie w formie uslugi

systemd stop,start,status

tylko do doczytu, renderowania
```bash
documentag -url_from_zip github.com/documentag/docs/archive/refs/heads/main.zip -static_host localhost -static_port 80
```

z zapisem danych 
```bash
documentag -url_from_zip github.com/documentag/docs/archive/refs/heads/main.zip -static_host localhost -static_port 80 -admin_host localhost -static_port 8080
```


+ poprzez konfigurację cdns na platformie FaaS

repozytorium git do odczytu
```bash
cdnop provider ADD domain.com CNAME git-static.faas.ovh
cdnop provider ADD domain.com TXT github.com/documentag/example.git
```

repozytorium git do zapisu
```bash
cdnop provider ADD domain.com CNAME git-admin.faas.ovh
cdnop provider ADD domain.com TXT github.com/documentag/example.git
```

lub z pliku archiwum zip

```bash
cdnop provider ADD domain.com CNAME zip-static.faas.ovh
cdnop provider ADD domain.com TXT github.com/documentag/docs/archive/refs/heads/main.zip
```


## Formaty danych


+ w formacie archiwum ze strukturą jak wyżej
+ w formacie html z tymi metadanymi wewnątrz


