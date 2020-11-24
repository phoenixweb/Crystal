# Modulo Pricelists

## Oggetto :: Pricelists *(Modello)*
L'oggetto Pricelists è quello che si può definire un **listino prezzi**.  
Dal listino principale verranno poi create diverse **configurazioni** e di ogni configurazione sarà possibile inserire dei prodotti *PricelistProduct* (prodotto + taglia).

>E' possibile definire un listino prezzi specificando un distributore addetto alla vendita, una collezione di appartenenza ed un nome per il listino.  
>*N.B.* Devono essere già presenti almeno un distributore ed una collezione al momento della creazione di un listino.

## Metodi disponibili

I metodi che possono essere svolti sul modulo **Pricelists** sono:

- [get](#metodo-get)
- [list](#metodo-list)
- [create](#metodo-create)
- [update](#metodo-update)
- [updateAllPrices](#metodo-updateAllPrices)
- [clone](#metodo-clone)

___

# Metodo "get"

Il metodo <b>pricelists</b>-><b>get</b>() richiede i seguenti argomenti. 

## Parametri

| Campo          | Obbligatorio | Descrizione                          | Data Type |
|----------------|--------------|--------------------------------------|-----------|
| `pricelist_id` | sì           | Il codice identificativo del listino | `intero`  |

## Risposta

| Campo                     | Descrizione                                       | Data Type  |
|---------------------------|---------------------------------------------------|------------|
| `brand_id`                | Il codice identificativo del brand                | `intero`   |
| `brand_name`              | Il nome del brand                                 | `stringa`  |
| `collection_hash`         | Il codice univoco della collezione                | `stringa`  |
| `collection_id`           | Il codice identificativo della collezione         | `stringa`  |
| `collection_name`         | Il nome della collezione                          | `stringa`  |
| `date_availability_end`   | Data di fine disponibilità del listino            | `datetime` |
| `date_availability_start` | Data di inizio disponibilità del listino          | `datetime` |
| `date_created`            | Data di creazione oggetto                         | `datetime` |
| `date_deleted`            | Data di cancellazione oggetto                     | `datetime` |
| `date_updated`            | Data di modifica oggetto                          | `datetime` |
| `is_brand_deleted`        | Lo status di cancellazione del brand              | `booleano` |
| `is_collection_deleted`   | Lo status di cancellazione della collezione       | `booleano` |
| `is_pricelist_deleted`    | Lo status di cancellazione del listino prezzi     | `booleano` |
| `is_visible`              | Lo status di visibilità del listino               | `booleano` |
| `pricelist_id`            | Il codice identificativo del listino              | `intero`   |
| `pricelist_name`          | Il nome del listino assegnato dal produttore      | `stringa`  |
| `supplier_id`             | Il codice identificativo del distributore         | `intero`   |
| `supplier_name`           | Il nome del distributore assegnato dal produttore | `stringa`  |

___

# Metodo "list"

Il metodo **pricelists**->**list**() richiede i seguenti argomenti.

## Parametri

| Campo               | Obbligatorio | Descrizione                                                                 | Data Type |
|---------------------|--------------|-----------------------------------------------------------------------------|-----------|
| `r`                 | facoltativo  | Il numero di risultati per pagina                                           | `intero`  |
| `p`                 | facoltativo  | La pagina da visualizzare                                                   | `intero`  |
| `s`                 | facoltativo  | La chiave di ordinamento da usare                                           | `intero`  |
| `q`                 | facoltativo  | Una oggetto JSON contenente chiavi di ricerca                               | `JSON`    |
| `q`.`free`          | facoltativo  | Ricerca libera sul campo `pricelist_name`, `brand_name` e `collection_name` | `stringa` |
| `q`.`brand_id`      | facoltativo  | Ricerca esatta sul campo `brand_id`                                         | `stringa` |
| `q`.`collection_id` | facoltativo  | Ricerca esatta sul campo `collection_id`                                    | `stringa` |
| `q`.`brands_ids`    | facoltativo  | Ricerca multipla sul campo `brand_id`                                       | `array`   |
| `q`.`supplier_id`   | facoltativo  | Ricerca esatta sul campo `supplier_id`                                      | `stringa` |
| `q`.`suppliers_ids` | facoltativo  | Ricerca multipla sul campo `supplier_id`                                    | `array`   |
| `q`.`is_visible`    | facoltativo  | Ricerca esatta sui lsitini con status `is_visible`                          | `intero`  |
| `q`.`status`        | facoltativo  | Ricerca esatta sul campo `status`                                           | `intero`  |


### Parametri Sorting

| Sorting Key         | Descrizione                              |
|---------------------|------------------------------------------|
| `pricelist_id\|ASC` | Ordina per codice listino ascendente     |
| `pricelist_id\|DES` | Ordina per codice listino discendente    |
| `pricelist_id\|ASC` | Ordina per nome listino ascendente       |
| `pricelist_id\|DES` | Ordina per nome listino discendente      |
| `date_created\|ASC` | Ordina per data di creazione ascendente  |
| `date_created\|DES` | Ordina per data di creazione discendente |

## Risposta

| Campo               | Descrizione                                 | Data Type |
|---------------------|---------------------------------------------|-----------|
| `nav`               | Oggetto contenente i dati di navigazione    | `JSON`    |
| `nav`.`page`        | Numero di pagina visualizzato               | `intero`  |
| `nav`.`tot_pages`   | Numero di pagine totali                     | `intero`  |
| `nav`.`results`     | Numero di risultati per pagina visualizzati | `intero`  |
| `nav`.`tot_results` | Numero di risultato totali della ricerca    | `intero`  |
| `nav`.`orderBy`     | Ordine di ricerca realmente applicato       | `stringa` |
| `dataset`           | Oggetto contenente i risultati              | `JSON`    |
| `dataset`.**`n`**   | Oggetto contenente il risultato **n**       | `JSON`    |

La ricerca sui **listini** genera un dataset di oggetti di tipo **pricelist**.
Per visualizzare la struttura di un oggetto pricelist, guarda il risultato della funzione **pricelists**->**get**()

___

# Metodo "create"

Il metodo <b>pricelists</b>-><b>create</b>() richiede i seguenti argomenti.

## Parametri

| Campo            | Obbligatorio | Descrizione                                                        | Data Type |
|------------------|--------------|--------------------------------------------------------------------|-----------|
| `supplier_id`    | sì           | Il codice identificativo del distributore assegnata dal produttore | `intero`  |
| `collection_id`  | sì           | Il codice identificativo della collezione assegnata dal produttore | `stringa` |
| `pricelist_name` | sì           | Il nome del listino assegnato dal produttore                       | `stringa` |

## Risposta

La risposta è un nuovo oggetto `Pricelist` ([vedi struttura oggetto Pricelist](#metodo-get)).

___

# Metodo "update"

Il metodo <b>pricelists</b>-><b>update</b>() richiede i seguenti argomenti.

## Parametri

| Campo            | Obbligatorio | Descrizione                                                        | Data Type |
|------------------|--------------|--------------------------------------------------------------------|-----------|
| `pricelist_id`   | sì           | Il codice identificativo del listino                               | `stringa` |
| `supplier_id`    | sì           | Il codice identificativo del distributore assegnata dal produttore | `stringa` |
| `collection_id`  | sì           | Il codice identificativo della collezione assegnata dal produttore | `stringa` |
| `pricelist_name` | sì           | Il nome del listino assegnato dal produttore                       | `stringa` |

> ***Nota bene***  
> Una volta definito non è possibile modificare il `pricelist_id` di un listino.

## Risposta

La risposta è l'oggetto `Pricelist` aggiornato ([vedi struttura oggetto Pricelist](#metodo-get)).
___

# Metodo "updateAllPrices"

Il metodo <b>pricelists</b>-><b>updateAllPrices</b>() richiede i seguenti argomenti.

## Parametri

| Campo            | Obbligatorio | Descrizione                                          | Data Type  |
|------------------|--------------|------------------------------------------------------|------------|
| `pricelist_id`     | sì           | Il codice identificativo del modello                 | `stringa`  |
| `products`                   | sì           | Lista delle SKUs che si vuole modificare                 | `array`  |
| `products[`**`n`**`]`     | sì           | Oggetto contenente i dati della referenza **n** a listino                 | `oggetto`  |
| `products[`**`n`**`]`.`sku_id`     | sì           | Il codice SKU della referenza a listino                 | `array`  |
| `products[`**`n`**`]`.`status`     | sì           | Il codice SKU della referenza a listino                 | `array`  |
| `products[`**`n`**`]`.`unit_price`     | sì           | Il codice SKU della referenza a listino                 | `array`  |
| `products[`**`n`**`]`.`unit_discount`     | sì           | Il codice SKU della referenza a listino                 | `array`  |
| `products[`**`n`**`]`.`unit_min_quantity`     | sì           | Il codice SKU della referenza a listino                 | `array`  |


## Risposta

La risposta è l'oggetto `Pricelist` aggiornato ([vedi struttura oggetto Pricelist](#metodo-get)).

___

# Metodo "clone"

Il metodo <b>pricelists</b>-><b>delete</b>() richiede i seguenti argomenti.

## Parametri

| Campo            | Obbligatorio | Descrizione                                          | Data Type |
|------------------|--------------|------------------------------------------------------|-----------|
| `pricelist_id`   | sì           | Il codice identificativo del modello                 | `stringa` |

## Risposta

La risposta sarà un oggetto `Pricelist` clonato in base al listino selezionato.
