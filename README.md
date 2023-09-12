# docs
docs.documentag.com

format plików archiwum zawierające dane:

    
    
    xslt/ - schema for commands
      pdf.xslt
      pdf_ocr.xslt
      create.xslt
      add_table.xslt
      add_table.xslt
        
    xml/ - data tables, history changes (commands) data inputs, e.g.: add icon, extracted ocr data
      history.xml      
      ops.xml
      files.xml
    
    source/ - all uploded inputs from email, api
      file.pdf
      ocr.txt
      icon.svg
      icon.png
      markdown.md
      
    index.html -   redndered format with xslt schema from xml data and included binary as name of file
        <meta> - describe the source file
        <body> - include all path to data, give the rights to update file
