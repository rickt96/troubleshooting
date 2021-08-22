
# Livewire
Laravel livewire è una tecnologia molto giovane, quindi presenta un po' incerta in certe dinamiche

 - Component non funziona senza apparenti motivi
 - dd() nel costrutture mount()

## Component non funziona senza apparenti motivi
E' capitato che un component di Livewire smettesse di funzionare o che funzionassero solo certi eventi.
Dopo un po' di ricerca è emerso che in maniera trasparente, senza indicare da nessuna parte questa dinamica, livewire vuole che tutti i controlli del suo component siano contenuti in un tag div, senza di quello il component non funziona!
Link di riferimento: https://stackoverflow.com/a/66051914

## dd() nel costrutture mount()
Il metodo di laravel dd() sembra non funzionare dentro il metodo mount()
