
# Livewire
Laravel livewire è una tecnologia molto giovane, quindi presenta un po' incerta in certe dinamiche

 - Component non funziona senza apparenti motivi
 - dd() nel costrutture mount()
 - Model-binding reset values
 - lanciare migrazione specifica

## Component non funziona senza apparenti motivi
E' capitato che un component di Livewire smettesse di funzionare o che funzionassero solo certi eventi.
Dopo un po' di ricerca è emerso che in maniera trasparente, senza indicare da nessuna parte questa dinamica, livewire vuole che tutti i controlli del suo component siano contenuti in un tag div, senza di quello il component non funziona!
Link di riferimento: https://stackoverflow.com/a/66051914

## dd() nel costrutture mount()
Il metodo di laravel dd() sembra non funzionare dentro il metodo mount()

## Model-binding reset values
Si è presentata una casistica in cui il Model utilizzato come entity della form resetta le sue proprietà.
A quanto pare i campi non inclusi nelle $rules vengono eliminati

Link di riferimento: https://github.com/livewire/livewire/issues/1702


## Lanciare migrazione specifica
php artisan migrate:refresh --path=/database/migrations/my_migration_name.php