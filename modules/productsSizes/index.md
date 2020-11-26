# Modulo ProductsSizes

## Oggetto :: ProductsSizes *(Cartella Taglie)*
L'oggetto **ProductSize** definisce le informazioni relative ad una taglia.  
L'id `size_id` potrà essere utilizzato per creare ProductSKU

___

## Metodi disponibili

I metodi che possono essere svolti sul modulo **ProductsSizes** sono:

- [list](#metodo-list)
- [create](#metodo-create)
- [delete](#metodo-delete)

I metodi *bulk* che possono essere svolti sul modulo **ProductsSizes** sono:

- [listTypes](#metodo-listTypes)
- [createSizeType](#metodo-createSizeType)
- [sortSizes](#metodo-sortSizes)
___

# Metodo "listType" e "list"

Il metodo **productsSizes**->**list**() richiede i seguenti argomenti.

## Parametri

| Campo                | Obbligatorio | Descrizione                                             | Data Type    |
|----------------------|--------------|---------------------------------------------------------|--------------|
| `r`                  | facoltativo  | Il numero di risultati per pagina                       | `intero`     |
| `p`                  | facoltativo  | La pagina da visualizzare                               | `intero`     |
| `s`                  | facoltativo  | La chiave di ordinamento da usare                       | `intero`     |
| `q`                  | facoltativo  | Una oggetto JSON contenente chiavi di ricerca           | `oggetto`    |
| `q`.`free`           | facoltativo  | Ricerca libera sul campo `product_name` e `brand_name`  | `stringa`    |
| `q`.`size_type`      | facoltativo  | Ricerca esatta sul campo `size_type`                    | `stringa`    |
| `q`.`brand_id`       | facoltativo  | Ricerca esatta sul campo `brand_id`                     | `intero`     |
| `q`.`brands_ids`     | facoltativo  | Ricerca multipla sul campo `brand_id`                   | `array`      |


## Risposta

| Campo               | Descrizione                                 | Data Type      |
|---------------------|---------------------------------------------|----------------|
| `nav`               | Oggetto contenente i dati di navigazione    | `oggetto`      |
| `nav`.`page`        | Numero di pagina visualizzato               | `intero`       |
| `nav`.`tot_pages`   | Numero di pagine totali                     | `intero`       |
| `nav`.`results`     | Numero di risultati per pagina visualizzati | `intero`       |
| `nav`.`tot_results` | Numero di risultato totali della ricerca    | `intero`       |
| `nav`.`orderBy`     | Ordine di ricerca realmente applicato       | `stringa`      |
| `dataset`           | Oggetto contenente i risultati              | `oggetto`      |
| `dataset`.**`n`**   | Oggetto contenente il risultato **n**       | `oggetto`      |

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

# Metodo "delete"

Il metodo <b>productsSizes</b>-><b>delete</b>() richiede i seguenti argomenti.

## Parametri

| Campo      | Obbligatorio | Descrizione                          | Data Type |
|------------|--------------|--------------------------------------|-----------|
| `size_id`  | sì           | Il codice identificativo dela taglia | `intero` |

## Risposta

Nessuna risposta.
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

# Metodo "sortSizes"

Il metodo <b>productsSizes</b>-><b>sortSizes</b>() serve a cambiare a piacimento 
l' ordine in cui le taglie vengono visualizzate.
Richiede i seguenti argomenti.

## Parametri

| Campo                  | Obbligatorio | Descrizione                                                          | Data Type |
|------------------------|--------------|----------------------------------------------------------------------|-----------|
| `brand_id`             | sì           | Il codice identificativo del brand                                   | `intero`  |
| `size_type`            | sì           | La **tipologia della taglia** che si desidera modificare             | `stringa` |
| `sizes_order`          | sì           | Un array contenente gli ID delle taglie nell' ordine desiderato      | `array`   |
| `sizes_order`\[**x**\] | sì           | L'identificativo della taglia che si desidera spostare nella posizione **x**    | `intero`  |

## Risposta

Questo metodo restituisce un oggetto contenente la lista di taglie facenti parte del set,
con il nuovo ordine, con i seguenti dati per ognuna.

| Campo            | Obbligatorio | Descrizione                                                                 | Data Type      |
|------------------|--------------|-----------------------------------------------------------------------------|----------------|
| `brand_id`       | sì           | Il codice identificativo del brand                                          | `intero`       |
| `size_type`      | sì           | La **tipologia della taglia**                                               | `stringa`      |
| `size_list`      | sì           | Un array contenente la lista delle taglie della classe `size_type` specificata | `array`        |
| `size_list`\[**n**\].`size_id`   | sì           | L'identificativo della taglia **n**                         | `stringa`      |
| `size_list`\[**n**\].`size_type` | sì           | La tipologia della taglia **n**                             | `stringa`      |
| `size_list`\[**n**\].`size_name` | sì           | Il nome della taglia **n**                                  | `stringa`      |

