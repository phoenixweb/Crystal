# Modulo Collections

## Oggetto :: Collections *(Collezione)*
L'oggetto Collections descrive una Collezione di articoli.

E' possibile specificare una finestra temporale in cui la Collezione sarà
disponibile per la vendita, per farlo sarà sufficiente valorizzare gli attributi:

- `date_availability_start` che stabilisce la data di inizio della campagna vendite
 della collezione. Nel caso non venga specificata viene considerata immediatamente
 disponibile.

- `date_availability_end` che stabilisce la data di fine della campagna vendite
 della collezione. Nel caso non venga specificata, la campagna vendita della
 collezione resta attiva permanentemente.

E' sufficiente non specificare nessuna delle due date qualora si desiderasse
rendere la collezione disponibile senza limiti di tempo.

___

## Metodi disponibili

I metodi che possono essere svolti sul modulo **Collections** sono:

- [get](#metodo-get)
- [list](#metodo-list)
- [create](#metodo-create)
- [update](#metodo-update)
- [updateVisibility](#metodo-updatevisibility)
- [delete](#metodo-delete)

#### Metodi per aggiungere o rimuovere articoli dalla Collezione
- [addProduct](#metodo-addProduct)
- [removeProduct](#metodo-removeProduct)
- [listProducts](#metodo-listProduct)
___

# Metodo "get"

Il metodo <b>collections</b>-><b>get</b>() richiede i seguenti argomenti.

## Parametri

| Campo           | Obbligatorio | Descrizione                               | Data Type      |
|--------------   |--------------|-------------------------------------------|----------------|
| `collection_id` | sì           | Il codice identificativo della collezione | `intero`       |

## Risposta

| Campo                     | Descrizione                                              | Data Type      |
|---------------------------|----------------------------------------------------------|----------------|
| `brand_id`                | Il codice identificativo del brand                       | `intero`       |
| `brand_name`              | Il nome del brand                                        | `stringa`      |
| `collection_id`           | Il codice identificativo della collezione                | `intero`       |
| `collection_hash`         | Il codice univoco della collezione                       | `stringa`      |
| `collection_name`         | Il nome della collezione assegnato dal produttore        | `stringa`      |
| `image_id`                | Il codice identificativo dell'anteprima della collezione | `intero`       |
| `is_visible`              | Lo status di visibilità della collezione                 | `booleano`     |
| `is_ended`                | Lo status di fine disponibilità della collezione         | `booleano`     |
| `is_started`              | Lo status di inizio disponibilità della collezione       | `booleano`     |
| `is_deleted`              | Lo status di cancellazione della collezione              | `booleano`     |
| `date_availability_start` | Data di inizio disponibilità della collezione            | `datetime`     |
| `date_availability_end`   | Data di fine disponibilità della collezione              | `datetime`     |
| `date_created`            | Data di creazione della collezione                       | `datetime`     |
| `date_deleted`            | Data di cancellazione della collezione                   | `datetime`     |

___

# Metodo "list"

Il metodo **collections**->**list**() richiede i seguenti argomenti.

## Parametri

| Campo                    | Obbligatorio | Descrizione                                               | Data Type |
|--------------------------|--------------|-----------------------------------------------------------|-----------|
| `r`                      | facoltativo  | Il numero di risultati per pagina                         | `intero`  |
| `p`                      | facoltativo  | La pagina da visualizzare                                 | `intero`  |
| `s`                      | facoltativo  | La chiave di ordinamento da usare                         | `intero`  |
| `q`                      | facoltativo  | Una oggetto JSON contenente chiavi di ricerca             | `oggetto` |
| `q`.`free`               | facoltativo  | Ricerca libera sul campo `collection_name` e `brand_name` | `stringa` |
| `q`.`collection_name`    | facoltativo  | Ricerca libera sul campo `collection_name`                | `stringa` |
| `q`.`collection_code`    | facoltativo  | Ricerca esatta sul campo `collection_code`                | `stringa` |
| `q`.`brand_id`           | facoltativo  | Ricerca esatta sul campo `brand_id`                       | `stringa` |
| `q`.`brands_ids`         | facoltativo  | Ricerca multipla sul campo `brand_id`                     | `array`   |
| `q`.`product_id`         | facoltativo  | Ricerca esatta sul campo `product_id`                     | `stringa` |
| `q`.`product_version_id` | facoltativo  | Ricerca esatta sul campo `product_version_id`             | `stringa` |
| `q`.`is_visible`         | facoltativo  | Ricerca esatta sui prodotti con status `is_visible`       | `intero`  |
| `q`.`status`             | facoltativo  | Ricerca esatta sui campi `status`                         | `intero`  |


### Parametri Sorting

| Sorting Key            | Descrizione                              |
|------------------------|------------------------------------------|
| `collection_id\|ASC`   | Ordina per codice collezione ascendente  |
| `collection_id\|DES`   | Ordina per codice collezione discendente |
| `collection_name\|ASC` | Ordina per nome collezione ascendente    |
| `collection_name\|DES` | Ordina per nome collezione discendente   |
| `brand_name\|ASC`      | Ordina per nome brand ascendente         |
| `brand_name\|DES`      | Ordina per nome brand discendente        |
| `date_created\|ASC`    | Ordina per data di creazione ascendente  |
| `date_created\|DES`    | Ordina per data di creazione discendente |

## Risposta

| Campo               | Descrizione                                 | Data Type |
|---------------------|---------------------------------------------|-----------|
| `nav`               | Oggetto contenente i dati di navigazione    | `oggetto` |
| `nav`.`page`        | Numero di pagina visualizzato               | `intero`  |
| `nav`.`tot_pages`   | Numero di pagine totali                     | `intero`  |
| `nav`.`results`     | Numero di risultati per pagina visualizzati | `intero`  |
| `nav`.`tot_results` | Numero di risultato totali della ricerca    | `intero`  |
| `nav`.`orderBy`     | Ordine di ricerca realmente applicato       | `stringa` |
| `dataset`           | Oggetto contenente i risultati              | `oggetto` |
| `dataset`.**`n`**   | Oggetto contenente il risultato **n**       | `oggetto` |

La ricerca sulle **collezioni** genera un dataset di oggetti di tipo **collection**.
Per visualizzare la struttura di un oggetto collection, guarda il risultato della funzione **collections**->**get**()

___

# Metodo "create"

Il metodo <b>collections</b>-><b>create</b>() richiede i seguenti argomenti.

## Parametri

| Campo                     | Obbligatorio | Descrizione                                       | Data Type  |
|---------------------------|--------------|---------------------------------------------------|------------|
| `brand_id`                | sì           | Il codice identificativo del brand                | `intero`   |
| `collection_code`         | sì           | Il codice identificativo assegnato dal produttore | `stringa`  |
| `collection_name`         | sì           | Il nome della collezione assegnato dal produttore | `stringa`  |
| `is_visible`              | sì           | Impostazione dello status di visibilità           | `booleano` |
| `date_availability_start` | facoltativo  | Data di inizio disponibilità della collezione     | `datetime` |
| `date_availability_end`   | facoltativo  | Data di fine disponibilità della collezione       | `datetime` |

## Risposta

La risposta è un nuovo oggetto `Collection`
([vedi struttura oggetto Collection](#metodo-get)).

___

# Metodo "update"

Il metodo <b>collections</b>-><b>update</b>() richiede i seguenti argomenti.

## Parametri

| Campo                     | Obbligatorio | Descrizione                                       | Data Type  |
|---------------------------|--------------|---------------------------------------------------|------------|
| `collection_id`           | sì           | Il codice identificativo della collezione         | `stringa`  |
| `collection_name`         | sì           | Il nome della collezione assegnato dal produttore | `stringa`  |
| `is_visible`              | sì           | Impostazione dello status di visibilità           | `booleano` |
| `date_availability_start` | facoltativo  | Data di inizio disponibilità della collezione     | `datetime` |
| `date_availability_end`   | facoltativo  | Data di fine disponibilità della collezione       | `datetime` |

> ***Nota bene***  
> Una volta definito non è possibile modificare il `brand_id` di una Collezione.

## Risposta

La risposta è l'oggetto `Collection` aggiornato
([vedi struttura oggetto Collection](#metodo-get)).
___

# Metodo "updateVisibility"

Il metodo <b>collections</b>-><b>updateVisibility</b>() richiede i seguenti argomenti.

## Parametri

| Campo           | Obbligatorio | Descrizione                               | Data Type      |
|-----------------|--------------|-------------------------------------------|----------------|
| `collection_id` | sì           | Il codice identificativo della collezione | `stringa`      |
| `is_visible`	  | sì           | Impostazione dello status di visibilità   | `booleano`     |

## Risposta

La risposta è l'oggetto `Collection` aggiornato
([vedi struttura oggetto Collection](#metodo-get)).

___

# Metodo "delete"

Il metodo <b>collections</b>-><b>delete</b>() richiede i seguenti argomenti.

## Parametri

| Campo           | Obbligatorio | Descrizione                               | Data Type |
|-----------------|--------------|-------------------------------------------|-----------|
| `collection_id` | sì           | Il codice identificativo della collezione | `stringa` |

## Risposta

Nessuna risposta.

___

# Metodo "addProducts"

Il metodo <b>collections</b>-><b>addProducts</b>() richiede i seguenti argomenti.

## Parametri

| Campo                | Obbligatorio | Descrizione                               | Data Type |
|----------------------|--------------|-------------------------------------------|-----------|
| `collection_id`      | sì           | Il codice identificativo della collezione | `stringa` |
| `product_version_id` | sì           | Il codice identificativo dell'articolo    | `stringa` |

## Risposta

La risposta è l'oggetto `Collection` aggiornato
([vedi struttura oggetto Collection](#metodo-get)).

___

# Metodo "removeProducts"

Il metodo <b>collections</b>-><b>removeProducts</b>() richiede i seguenti argomenti.

## Parametri

| Campo                | Obbligatorio | Descrizione                               | Data Type |
|----------------------|--------------|-------------------------------------------|-----------|
| `collection_id`      | sì           | Il codice identificativo della collezione | `stringa` |
| `product_version_id` | sì           | Il codice identificativo dell'articolo    | `stringa` |

## Risposta

La risposta è l'oggetto `Collection` aggiornato
([vedi struttura oggetto Collection](#metodo-get)).

___

# Metodo "listProducts"

Il metodo <b>collections</b>-><b>listProducts</b>() richiede i seguenti argomenti.

## Parametri

| Campo                | Obbligatorio | Descrizione                                                     | Data Type |
|----------------------|--------------|-----------------------------------------------------------------|-----------|
| `r`                  | facoltativo  | Il numero di risultati per pagina                               | `intero`  |
| `p`                  | facoltativo  | La pagina da visualizzare                                       | `intero`  |
| `s`                  | facoltativo  | La chiave di ordinamento da usare                               | `intero`  |
| `q`                  | facoltativo  | Una oggetto JSON contenente chiavi di ricerca                   | `oggetto` |
| `q`.`collection_id`  | sì           | Ricerca esatta sul campo `collection_id`                        | `stringa` |
| `q`.`free`           | facoltativo  | Ricerca libera sui campi sotto elencati come *ricerca libera*   | `stringa` |
| `q`.`brand_name`     | facoltativo  | *Ricerca libera* sul campo `brand_name`                         | `stringa` |
| `q`.`product_name`   | facoltativo  | *Ricerca libera* sul campo `product_name`                       | `stringa` |
| `q`.`product_type`   | facoltativo  | *Ricerca libera* sul campo `product_type`                       | `stringa` |
| `q`.`color_rgb`      | facoltativo  | *Ricerca libera* sul campo `color_rgb`                          | `stringa` |
| `q`.`color_code`     | facoltativo  | *Ricerca libera* sul campo `color_code`                         | `stringa` |
| `q`.`color_name`     | facoltativo  | *Ricerca libera* sul campo `color_name`                         | `stringa` |
| `q`.`fabric_code`    | facoltativo  | *Ricerca libera* sul campo `fabric_code`                        | `stringa` |
| `q`.`fabric_name`    | facoltativo  | *Ricerca libera* sul campo `fabric_name`                        | `stringa` |
| `q`.`product_type`   | facoltativo  | *Ricerca libera* sul campo `product_type`                       | `stringa` |
| `q`.`brand_id`       | facoltativo  | Ricerca esatta sul campo `brand_id`                             | `stringa` |
| `q`.`brands_ids`     | facoltativo  | Ricerca multipla sul campo `brand_id`                           | `array`   |
| `q`.`product_id`     | facoltativo  | Ricerca esatta sul campo `product_id`                           | `stringa` |
| `q`.`product_type`   | facoltativo  | Ricerca esatta sul campo `product_type`                         | `stringa` |
| `q`.`product_gender` | facoltativo  | Ricerca esatta sul campo `product_gender`                       | `stringa` |
| `q`.`product_target` | facoltativo  | Ricerca esatta sul campo `product_target`                       | `stringa` |
| `q`.`color_id`       | facoltativo  | Ricerca esatta sul campo `color_id`                             | `stringa` |
| `q`.`fabric_id`      | facoltativo  | Ricerca esatta sul campo `fabric_id`                            | `stringa` |
| `q`.`outfit_id`      | facoltativo  | Ricerca esatta sul campo `outfit_id`                            | `stringa` |
| `q`.`pricelist_id`   | facoltativo  | Ricerca esatta sul campo `pricelist_id`                         | `stringa` |
| `q`.`is_visible`     | facoltativo  | Ricerca esatta sui prodotti con status `is_visible`             | `intero`  |


### Parametri Sorting

| Sorting Key               | Descrizione                              |
|---------------------------|------------------------------------------|
| `product_version_id\|ASC` | Ordina per nome collezione ascendente    |
| `product_version_id\|DES` | Ordina per nome collezione discendente   |
| `product_id\|ASC`         | Ordina per codice collezione ascendente  |
| `product_id\|DES`         | Ordina per codice collezione discendente |
| `date_created\|ASC`       | Ordina per data di creazione ascendente  |
| `date_created\|DES`       | Ordina per data di creazione discendente |

## Risposta

| Campo               | Descrizione                                 | Data Type |
|---------------------|---------------------------------------------|-----------|
| `nav`               | Oggetto contenente i dati di navigazione    | `oggetto` |
| `nav`.`page`        | Numero di pagina visualizzato               | `intero`  |
| `nav`.`tot_pages`   | Numero di pagine totali                     | `intero`  |
| `nav`.`results`     | Numero di risultati per pagina visualizzati | `intero`  |
| `nav`.`tot_results` | Numero di risultato totali della ricerca    | `intero`  |
| `nav`.`orderBy`     | Ordine di ricerca realmente applicato       | `stringa` |
| `dataset`           | Oggetto contenente i risultati              | `oggetto` |
| `dataset`.**`n`**   | Oggetto contenente il risultato **n**       | `oggetto` |

La ricerca sugli **articoli** nelle **collezioni** genera un dataset di oggetti
di tipo **productVersion**.
