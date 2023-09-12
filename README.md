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
open index.html 
```

+ na serwerze


+ poprzez konfigurację cdns na platformie FaaS

```bash
cdnop provider ADD domain.com CNAME git.faas.ovh
cdnop provider ADD domain.com TXT github.com/documentag/example.git
```

lub 
```bash
cdnop provider ADD domain.com CNAME zip.faas.ovh
cdnop provider ADD domain.com TXT github.com/documentag/example.git
```


## Formaty danych


+ w formacie archiwum ze strukturą jak wyżej
+ w formacie html z tymi metadanymi wewnątrz


