# Modulo Stores

## Oggetto :: Stores *(Store)*
L'oggetto Stores è quello che si definisce un **negozio online**.  

___

## Metodi disponibili

I metodi che possono essere svolti sul modulo **Stores** sono:

- [get](#metodo-get)
- [list](#metodo-list)

___

# Metodo "get"

Il metodo <b>stores</b>-><b>get</b>() non ha bisogno di parametri in ingresso.

## Risposta

| Campo            | Descrizione                                       | Data Type  |
|------------------|---------------------------------------------------|------------|
| `store_id`       | Il codice identificativo del negozio              | `intero`   |
| `store_token`    | Il codice identificativo del negozio              | `stringa`  |
| `store_name`     | Il none del negozio                               | `stringa`  |
| `image_id`       | Il codice identificativo del logo del negozio     | `intero`   |
| `is_deleted`     | Lo status di cancellazione del negozio            | `booleano` |
| `host_name`      | Il nome dell'host al quale si appoggia il negozio | `stringa`  |
| `supplier_id`    | Il codice identificativo del distributore         | `intero`   |
| `supplier_token` | Il codice identificativo del distributore         | `stringa`  |
| `supplier_name`  | Il nome  del distributore                         | `stringa`  |
| `agent_id`       | Il codice identificativo del negozio              | `intero`   |
| `agent_name`     | Il nome del negozio                               | `stringa`  |
| `date_created`   | Data di creazione store                           | `datetime` |
| `date_updated`   | Data di aggiornamento store                       | `datetime` |
| `date_deleted`   | Data di cancellazione store                       | `datetime` |

___

# Metodo "list"

Il metodo **stores**->**list**() richiede i seguenti argomenti.

## Parametri

| Campo             | Obbligatorio | Descrizione                                   | Data Type |
|-------------------|--------------|-----------------------------------------------|-----------|
| `r`               | facoltativo  | Il numero di risultati per pagina             | `intero`  |
| `p`               | facoltativo  | La pagina da visualizzare                     | `intero`  |
| `s`               | facoltativo  | La chiave di ordinamento da usare             | `intero`  |
| `q`               | facoltativo  | Una oggetto JSON contenente chiavi di ricerca | `oggetto` |
| `q`.`free`        | facoltativo  | Ricerca libera sul campo `store_name`         | `stringa` |
| `q`.`supplier_id` | facoltativo  | Ricerca esatta sul campo `supplier_id`        | `stringa` |
| `q`.`agent_id`    | facoltativo  | Ricerca esatta sul campo `agent_id`           | `stringa` |

### Parametri Sorting

| Sorting Key         | Descrizione                                |
|---------------------|--------------------------------------------|
| `store_id\|ASC`     | Ordina per codice negozio ascendente       |
| `store_id\|DES`     | Ordina per codice negozio discendente      |
| `store_name\|ASC`   | Ordina per nome negozio ascendente         |
| `store_name\|DES`   | Ordina per nome negozio discendente        |
| `date_created\|ASC` | Ordina per data di creazione ascendente    |
| `date_created\|DES` | Ordina per data di creazione discendente   |

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

La ricerca sui **negozi online** genera un dataset di oggetti di tipo **store**.
Per visualizzare la struttura di un oggetto store, guarda il risultato della funzione **stores**->**get**()
