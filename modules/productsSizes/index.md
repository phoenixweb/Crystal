# Modulo ProductsSizes

## Oggetto :: ProductsSizes *(Cartella Taglie)*
L'oggetto **ProductsSizes**raccoglie le informazioni relative alle taglie degli articoli registrati all' interno dell' applicazione.

>E' possibile definire le taglie specificando brand di riferimento, nome del set(size_type) e quali taglie ne fanno parte.
>E' possibile inoltre modificare l' ordine in cui queste vengono mostrate(sortSizes).


___

## Metodi disponibili

I metodi che possono essere svolti sul modulo **ProductsSizes** sono:

- [list](#metodo-list)
- [listTypes](#metodo-listTypes)
- [create](#metodo-create)
- [createSizeType](#metodo-createSizeType)
- [delete](#metodo-delete)
- [sortSizes](#metodo-sortSizes)
___

# Metodo "listType" e "list"

Il metodo **productsSizes**->**list**() richiede i seguenti argomenti.

## Parametri

| Campo                | Obbligatorio | Descrizione                                             | Data Type      |
|----------------------|--------------|---------------------------------------------------------|----------------|
| `r`                  | facoltativo  | Il numero di risultati per pagina                       | `intero`       |
| `p`                  | facoltativo  | La pagina da visualizzare                               | `intero`       |
| `s`                  | facoltativo  | La chiave di ordinamento da usare                       | `intero`       |
| `q`                  | facoltativo  | Una oggetto JSON contenente chiavi di ricerca           | `JSON`         |
| `q`.`free`           | facoltativo  | Ricerca libera sul campo `product_name` e `brand_name`  | `stringa`      |
| `q`.`size_type`      | facoltativo  | Ricerca esatta sul campo `size_type`                    | `stringa`      |
| `q`.`brand_id`       | facoltativo  | Ricerca esatta sul campo `brand_id`                     | `intero`      |
| `q`.`brands_ids`     | facoltativo  | Ricerca multipla sul campo `brand_id`                   | `array`      |


## Risposta

| Campo               | Descrizione                                 | Data Type      |
|---------------------|---------------------------------------------|----------------|
| `nav`               | Oggetto contenente i dati di navigazione    | `JSON`         |
| `nav`.`page`        | Numero di pagina visualizzato               | `intero`       |
| `nav`.`tot_pages`   | Numero di pagine totali                     | `intero`       |
| `nav`.`results`     | Numero di risultati per pagina visualizzati | `intero`       |
| `nav`.`tot_results` | Numero di risultato totali della ricerca    | `intero`       |
| `nav`.`orderBy`     | Ordine di ricerca realmente applicato       | `stringa`      |
| `dataset`           | Oggetto contenente i risultati              | `JSON`         |
| `dataset`.**`n`**   | Oggetto contenente il risultato **n**       | `JSON`         |

___

# Metodo "create"

Il metodo <b>productsSizes</b>-><b>create</b>() richiede i seguenti argomenti.

## Parametri

| Campo            | Obbligatorio | Descrizione                                          | Data Type      |
|------------------|--------------|------------------------------------------------------|----------------|
| `brand_id`       | sì           | Il codice identificativo del brand                   | `intero`       |
| `size_type`      | sì           | La **tipologia della taglia**                        | `stringa`      |
| `size_name`      | sì           | Il nome della taglia                                 | `stringa`      |

## Risposta

Questa funzione non genera una risposta.

___
# Metodo "createSizeType"

Il metodo <b>productsSizes</b>-><b>createSizeType</b>() serve a creare un set di taglie *(bulk create)*.

## Parametri

| Campo            | Obbligatorio | Descrizione                                          | Data Type      |
|------------------|--------------|------------------------------------------------------|----------------|
| `brand_id`       | sì           | Il codice identificativo del brand                   | `intero`       |
| `size_type`      | sì           | La **tipologia della taglia**                        | `stringa`      |
| `sizes`          | sì           | Un array contenente le taglie che si desidera creare | `array`        |
| `sizes`.**`n`**  | sì           | Il nome della taglia **`n`** che si desidera creare  | `stringa`        |

## Risposta

Questa funzione non genera una risposta.

___

# Metodo "delete"

Il metodo <b>productsSizes</b>-><b>delete</b>() richiede i seguenti argomenti.

## Parametri

| Campo      | Obbligatorio | Descrizione                          | Data Type |
|------------|--------------|--------------------------------------|-----------|
| `size_id`  | sì           | Il codice identificativo dela taglia | `intero` |

## Risposta

Nessuna risposta.
___

# Metodo "sortSizes"

Il metodo <b>productsSizes</b>-><b>sortSizes</b>() serve a cambiare a piacimento 
l' ordine in cui le taglie vengono visualizzate.
Richiede i seguenti argomenti.

## Parametri

| Campo        | Obbligatorio | Descrizione                                                     | Data Type |
|--------------|--------------|-----------------------------------------------------------------|-----------|
| `size_id`    | sì           | Il codice identificativo dela taglia                            | `intero`  |
| `sizes_order`| sì           | Un array contenente gli ID delle taglie nell' ordine desiderato | `array`   |

## Risposta

Questo metodo restituisce un oggetto contenente la lista di taglie facenti parte del set,
con il nuovo ordine,con i seguenti dati per ognuna.

| Campo            | Obbligatorio | Descrizione                           | Data Type      |
|------------------|--------------|---------------------------------------|----------------|
| `brand_id`       | sì           | Il codice identificativo del brand    | `intero`       |
| `size_type`      | sì           | La **tipologia della taglia**         | `stringa`      |
| `size_name`      | sì           | Il nome della taglia                  | `stringa`      |

