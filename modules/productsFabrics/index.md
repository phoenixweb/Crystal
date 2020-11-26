# Modulo ProductsFabrics

## Oggetto :: ProductsFabrics *(Cartella Materiali)*
L'oggetto **ProductsFabrics** definisce le informazioni relative ad un materiale o
una combinazione di materiali che potrà essere allegata ad un prodotto per descriverlo.

___

### Metodi disponibili

I metodi che possono essere svolti sul modulo **ProductsFabrics** sono:

- [get](#metodo-get)
- [create](#metodo-create)
- [update](#metodo-update)
- [delete](#metodo-delete)
- [list](#metodo-list)
___

# Metodo "get"

Il metodo <b>productsFabrics</b>-><b>get</b>() richiede i seguenti argomenti.

## Parametri

| Campo       | Obbligatorio | Descrizione                            | Data Type |
|-------------|--------------|----------------------------------------|-----------|
| `fabric_id` | sì           | Il codice identificativo del materiale | `intero`  |

## Risposta

| Campo                | Descrizione                                                     | Data Type  |
|----------------------|-----------------------------------------------------------------|------------|
| `brand_id`           | Il codice identificativo del brand                              | `intero`   |
| `brand_name`         | Il nome del brand                                               | `stringa`  |
| `fabric_id`          | Il codice identificativo del materiale                          | `intero`   |
| `fabric_code`        | Il codice identificativo del materiale assegnato dal produttore | `stringa`  |
| `fabric_name`        | Il nome del materiale                                           | `stringa`  |
| `fabric_description` | La descrizione del materiale assegnata dal produttore           | `stringa`  |
| `is_deleted`         | Lo status di cancellazione del modello sui cataloghi            | `booleano` |
| `date_created`       | Data di creazione oggetto                                       | `datetime` |
| `date_updated`       | Data di aggiornamento oggetto                                   | `datetime` |
| `date_deleted`       | Data di cancellazione oggetto                                   | `datetime` |

___

# Metodo "create"

Il metodo <b>productsFabrics</b>-><b>create</b>() richiede i seguenti argomenti.

## Parametri

| Campo                | Obbligatorio | Descrizione                                           | Data Type |
|----------------------|--------------|-------------------------------------------------------|-----------|
| `brand_id`           | sì           | Il codice identificativo del brand                    | `intero`  |
| `fabric_code`        | sì           | Il codice del materiale assegnato dal produttore      | `stringa` |
| `fabric_name`        | sì           | Il nome del materiale assegnato dal produttore        | `stringa` |
| `fabric_description` | facoltativo  | La descrizione del materiale assegnata dal produttore | `stringa` |

## Risposta

La risposta è un nuovo oggetto `ProductFabric` ([vedi struttura oggetto ProductFabric](#metodo-get)).

___

# Metodo "update"

Il metodo <b>productsFabrics</b>-><b>update</b>() richiede i seguenti argomenti.

## Parametri

| Campo                | Obbligatorio | Descrizione                                           | Data Type |
|----------------------|--------------|-------------------------------------------------------|-----------|
| `fabric_id`          | sì           | Il codice identificativo del materiale                | `intero`  |
| `fabric_code`        | sì           | Il codice del materiale assegnato dal produttore      | `stringa` |
| `fabric_name`        | sì           | Il nome del materiale assegnato dal produttore        | `stringa` |
| `fabric_description` | facoltativo  | La descrizione del materiale assegnata dal produttore | `stringa` |

> ***Nota bene***  
> Una volta definito non è possibile modificare il `brand_id` di un Materiale.

## Risposta

La risposta è l'oggetto `ProductFabric` aggiornato ([vedi struttura oggetto ProductFabric](#metodo-get)).

___

# Metodo "delete"

Il metodo <b>productsFabrics</b>-><b>delete</b>() richiede i seguenti argomenti.

## Parametri

| Campo       | Obbligatorio | Descrizione                            | Data Type |
|-------------|--------------|----------------------------------------|-----------|
| `fabric_id` | sì           | Il codice identificativo del materiale | `stringa` |

## Risposta

Nessuna risposta.

___

# Metodo "list"

Il metodo **productsFabrics**->**list**() richiede i seguenti argomenti.

## Parametri

| Campo        | Obbligatorio | Descrizione                                                          | Data Type |
|--------------|--------------|----------------------------------------------------------------------|-----------|
| `r`          | facoltativo  | Il numero di risultati per pagina                                    | `intero`  |
| `p`          | facoltativo  | La pagina da visualizzare                                            | `intero`  |
| `s`          | facoltativo  | La chiave di ordinamento da usare                                    | `intero`  |
| `q`          | facoltativo  | Una oggetto JSON contenente chiavi di ricerca                        | `oggetto` |
| `q`.`free`   | facoltativo  | Ricerca libera sul campo `fabric_code`, `fabric_name` e `brand_name` | `stringa` |
| `q`.`status` | facoltativo  | Ricerca esatta sul campo `status`                                    | `stringa` |

### Parametri Sorting

| Sorting Key         | Descrizione                              |
|---------------------|------------------------------------------|
| `fabric_id\|ASC`    | Ordina per codice materiale ascendente   |
| `fabric_id\|DES`    | Ordina per codice materiale discendente  |
| `fabric_name\|ASC`  | Ordina per nome materiale ascendente     |
| `fabric_name\|DES`  | Ordina per nome materiale discendente    |
| `fabric_code\|ASC`  | Ordina per codice materiale ascendente   |
| `fabric_code\|DES`  | Ordina per codice materiale discendente  |
| `brand_name\|ASC`   | Ordina per nome brand ascendente         |
| `brand_name\|DES`   | Ordina per nome brand discendente        |
| `date_created\|ASC` | Ordina per data di creazione ascendente  |
| `date_created\|DES` | Ordina per data di creazione discendente |

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

La ricerca sui **modelli** genera un dataset di oggetti di tipo **productsFabrics**.
Per visualizzare la struttura di un oggetto productsFabrics, guarda il risultato della funzione **productsFabrics**->**get**()
