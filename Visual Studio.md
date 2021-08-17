
# Visual Studio

 - Cambiare tema
 - Errore "Cannot run while setup is in progress"
 - Creare installer onffline per VS2017
 - Errore "current version .net sdk not support net core 2.2"
 -  Icona fulmine eventi non visibile nei file aspx in asp.net
 - Errore "lc.exe exited with code -1"
 - Ripristinare configurazione iniziali
 -  Errore "The setup for this installation of visual studio is not complete"
 - VS Code CSC : error CS1617: Invalid option '7.3' for /langversion

## Cambiare tema
menu di navigazione > strumenti > opzioni
nella prima schermata in lato selezionare dalla combobox il tema

## Errore "Cannot run while setup is in progress"
L'eerrore "Cannot run while setup is in progress" è abbastanza autoesplicativo ed indica che è in corso un setup per VS.
Il processo in carico è localizzabile nel task manager ma suggeriscono di non terminarlo per evitare problemi, limitarsi a tenerlo monitorato ed attendere la fine.
in caso di necessità immediata di avviare VS è possibile farlo lanciandolo da console con il parametro /AllowDuringSetup.

Link di riferimento: https://stackoverflow.com/questions/27538833/cannot-open-visual-studio-throw-error-cannot-run-when-setup-is-in-progress

## Creare installer onffline per VS2017
Da VS 2017 in poi non hanno rilasciato la ISO. Visto che l'installazione con tutti i moduli può arrivare a pesare 30+GB è possibile tramite console creare un installer offline:
1. scarica dal sito il web installer
2. riominalo in "vs_community.exe"
3. aprire la console (cmd) e spostarsi sulla directory del file exe
4. esegui il comando "vs_community.exe --layout c:\vs2017offline --lang en-US it-IT"

Link di riferimento: https://docs.microsoft.com/it-it/visualstudio/install/workload-component-id-vs-community

## Errore "current version .net sdk not support net core 2.2"
"The Current .Net SDK does not support targeting .Net Core 2.2 Target .Net Core 2.1 or Lower"
L'errore si può presentare all'apertura di una solution asp net core.
Di per se è abbastanza autoesplicativo, se non che presenta dei falsi positivi:
1. nella macchina non è installato l'sdk 2.2: Per risolvere basta installare al versione sdk necessaria da qui https://dotnet.microsoft.com/download/visual-studio-sdks
2. bug di visual studio 2017: A quanto risulta da vari link l'ultima versione di vs 2017 comminity non si interfaccia correttamente con la versione sdk 2.2. Quindi durante il wizard per la creazione della soluzione è possibile selezionare in alto la destinazione 2.2 ma una volta avviata la soluzione essa solleva l'errore indicato sopra.

A quanto detto nel link di riferimento sembra quindi che sia possibile puntare la versione 2.2 soltanto installando l'sdk 2.2.1xx
La soluzione adottata nel mio caso è stata la seguente:
1. disinstallando tramite vs installer la versione community di visual studio (sospetto sia lei ad avere questo bug)
2. installando l'ultima versione di VS 2017 enterprise
3. installando la versione x64 / x86 dell'sdk 2.2.105

Link di riferimento: https://developercommunity.visualstudio.com/content/problem/470616/the-current-net-sdk-does-not-support-targeting-net-5.html

##  Icona fulmine eventi non visibile nei file aspx in asp.net
non viene mostrata l'icona del fulmine nella finestra delle proprieta
1. clicca sul designer grafico
2. ritornando al codice l'icona dovrebbe comparire

Link di riferimento: https://forums.asp.net/t/1064117.aspx?Events+Not+Showing+Up+in+Properties+Tab

## Errore "lc.exe exited with code -1"
Questo errore è tipico quando una soluzione ha generato un errore in fase di compilazione e tale errore si propaga al compilatore. La cosa strana è data dal fatto che se presenta solo l'errore di compilazione senza altri dettagli.
Il file di licenza licenses.licx conteneva degli errori (nel mio caso dovuti ad un marker di merge) e ciò non viene segnalato.

Link di riferimento: 
 - http://help.grapecity.com/spread/MultiRow/UserGuide_TroubleShooting_Lcexe.html
 - https://stackoverflow.com/questions/13239325/how-to-find-reason-of-failed-build-without-any-error-or-warning

## Ripristinare configurazione iniziali
1. selezionare da windows il programma "Developer Command Prompt for VS XXXX"
2. digitare "devenv /ResetSettings General"

## Errore "The setup for this installation of visual studio is not complete"
Quando si tenta di avviare vs viene fuori una messagebox di warning che indica che l'installazione non è completa.
come workaround della soluzione è necessario aprire l'installer di vs, cliccare su modifica ed aggiungere o modificare un componente esistente, poi applicare la modifica.

Link di riferimento: https://stackoverflow.com/questions/50185146/the-setup-for-this-installation-of-visual-studio-is-not-complete-really/50687020

## VS Code CSC : error CS1617: Invalid option '7.3' for /langversion
https://stackoverflow.com/questions/50266795/vs-code-csc-error-cs1617-invalid-option-7-3-for-langversion