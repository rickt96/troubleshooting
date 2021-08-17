
# Console Windows
Non sono un profondo conoscitore della console di windows, quindi qui ci sono tip molto banali.

 - Aggiungere prefisso ai files di una cartella
 - Output su file del contenuto di una cartella
 - Rinominare lowercase dei file
 - Visualizzare PID processi

## Aggiungere prefisso ai files di una cartella

    for %a in (*.*) do ren "%a" "prefix - %a"
for <nome_tmp> in (<nome.estensione>) do <azione_rinomina> "nome_iniziale" "nome_finale"

Link di riferimento: https://stackoverflow.com/questions/20874915/rename-multiple-files-in-a-folder-add-a-prefix-windows

## Output su file del contenuto di una cartella

    dir > output_filename.txt

## Rinominare lowercase dei file

    for /f "Tokens=*" %f in ('dir /l/b/a-d') do (rename "%f" "%f")

## Visualizzare PID processi

    tasklist /fi "pid eq 4444"

Link di riferimento: https://stackoverflow.com/questions/27211427/find-process-name-by-its-process-id
