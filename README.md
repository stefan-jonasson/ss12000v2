# ss12000v2



# Kända problem

OpenAPI verkar ha lite problem med relativa path:er. `swagger-codegen` har inte samma uppfattning som den modul som används i MS Code. Vi refererar från `openapi.yaml` -> `paths/xxx.taml` -> `searchParameters.yaml`, och kanske är det då underspecificerat vad som är _current work directory_ relativt filen `./paths/xxx.yaml`. En del verktyg förväntar sig att searchparameters i `paths/searchParameters.yaml`, det gör den swagger jag kör i MS Code. `swagger-codegen` letar i en nivå upp, på samma ställe som openapi.yaml. Det är väl lite oklart vad som är korrekt, skulle jag gissa, och openapi har den egenheten att den har lite svårt med referenser till filer i olika mappar, eftersom den kontexten kan tappas bort  om man implementerar delar som makron, vilket verkar vara hur det går till.

En symlänk, `cd ss12000v2; ln -s paths/searchParameters.yaml`, löser problemet för `swagger-codegen` för stunden. Vi får fixa det, antagligen flytta ner allt i samma mapp  eller nåt.