# Modulo Brands

I metodi che possono essere svolti sul modulo Brand sono:

- get
- list

___

# Metodo "get"

Il metodo <b>brands</b>-><b>get</b>() richiede i seguenti argomenti.

## Parametri

| Campo      | Obbligatorio | Descrizione                        | Valori Ammessi |
|------------|--------------|------------------------------------|----------------|
| `brand_id` | sì           | Il codice identificativo del brand | `intero`       |

## Risposta

| Campo           | Descrizione                                 | Valori Ammessi |
|-----------------|---------------------------------------------|----------------|
| `brand_id`      | Il codice identificativo del brand          | `intero`       |
| `brand_name`    | Il nome del Brand                           | `stringa`      |
| `product_count` | Il numero di modelli associati al brand     | `intero`       |
| `version_count` | Il numero di varianti associate al brand    | `intero`       |
| `sku_count`     | Il numero di singole SKU associate al brand | `intero`       |
| `date_created`  | Data di creazione oggetto                   | `datetime`     |

___

# Metodo "list"

Il metodo **brands**->**list**() richiede i seguenti argomenti.

## Parametri

| Campo      | Obbligatorio | Descrizione                                   | Valori Ammessi |
|------------|--------------|-----------------------------------------------|----------------|
| `q`        | no           | Una oggetto JSON contenente chiavi di ricerca | `JSON`         |
| `r`        | no           | Il numero di risultati per pagina             | `intero`       |
| `p`        | no           | La pagina da visualizzare                     | `intero`       |
| `s`        | no           | La chiave di ordinamento da usare             | `intero`       |

### Parametri Query

| Campo      | Obbligatorio | Descrizione                           | Valori Ammessi |
|------------|--------------|---------------------------------------|----------------|
| `free`     | facoltativo  | Ricerca libera sul campo `brand_name` | `stringa`      |

### Parametri Sorting

| Sorting Key      | Descrizione                         |
|------------------|-------------------------------------|
| `brand_id\|ASC`   | Ordina per codice brand ascendente  |
| `brand_id\|DES`   | Ordina per codice brand discendente |
| `brand_name\|ASC` | Ordina per nome brand ascendente    |
| `brand_name\|DES` | Ordina per nome brand discendente   |

## Risposta

| Campo             | Descrizione                                 | Valori Ammessi |
|-------------------|---------------------------------------------|----------------|
| `nav`             | Oggetto contenente i dati di navigazione    | `JSON`         |
| `nav.page`        | Numero di pagina visualizzato               | `intero`       |
| `nav.tot_pages`   | Numero di pagine totali                     | `intero`       |
| `nav.results`     | Numero di risultati per pagina visualizzati | `intero`       |
| `nav.tot_results` | Numero di risultato totali della ricerca    | `intero`       |
| `nav.orderBy`     | Ordine di ricerca realmente applicato       | `stringa`      |
| `dataset`         | Oggetto contenente i risultati              | `JSON`         |
| `dataset`.**`n`** | Oggetto contenente il risultato **n**       | `JSON`         |

La ricerca sui **brand** genera un dataset di oggetti di tipo **brand**.
Per visualizzare la struttura di un oggetot brand, guarda il risultato della funzione **brand**->**get**()

