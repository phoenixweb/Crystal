# Modulo ProductsSKU

## Oggetto :: ProductsSKU 

L'oggetto ProductSKU descrive una referenza unica (SKU).
E' costitutito dalla combinazione di:

- [ProductVersion](../productsVersions/index.md) *(articolo)*
- [ProductSize](../productsSizes/index.md) *(taglie)*

___

## Metodi disponibili

I metodi che possono essere svolti sul modulo **ProductsSKU** sono:

- [get](#metodo-get)
- [list](#metodo-list)
- [create](#metodo-create)
- [delete](#metodo-delete)
___

# Metodo "get"

Il metodo <b>productsSKU</b>-><b>get</b>() richiede i seguenti argomenti.

## Parametri

| Campo        | Obbligatorio | Descrizione                          | Data Type      |
|--------------|--------------|--------------------------------------|----------------|
| `sku_id`     | sì           | Il codice identificativo della SKU   | `intero`       |

## Risposta

| Campo                  | Descrizione                                                                | Data Type      |
|------------------------|----------------------------------------------------------------------------|----------------|
| `sku_id`               | Il codice identificativo dello sku                                         | `intero`       |
| `brand_id`             | Il codice identificativo del brand                                         | `intero`       |
| `brand_name`           | Il nome del brand                                                          | `stringa`      |
| `product_id`           | Il codice identificativo del modello                                       | `intero`       |
| `product_code`         | Il codice identificativo del modello assegnato dal produttore              | `stringa`      |
| `product_name`         | Il nome del modello assegnato dal produttore                               | `stringa`      |
| `product_name_full`    | Il nome costruito in modo dinamico con nome prodotto, materiale e colore   | `stringa`      |
| `product_type`         | La **tipologia del modello**                                               | `stringa`      |
| `product_target`       | Il **target di età** del modello                                           | `stringa`      |
| `product_gender`       | Il **target di genere** del modello                                        | `stringa`      |
| `product_version_id`   | Il codice identificativo del prodotto                                      | `intero`       |
| `product_version_hash` | Il codice hash del prodotto                                                | `stringa`      |
| `color_id`             | Il codice identificativo del colore                                        | `intero`       |
| `color_code`           | Il codice identificativo del colore assegnato dal produttore               | `intero`       |
| `color_name`           | Il nome del colore                                                         | `stringa`      |
| `color_rgb`            | Il modello additivo del colore                                             | `intero`       |
| `fabric_id`            | Il codice identificativo del materiale                                     | `intero`       |
| `fabric_code`          | Il codice del materiale assegnato dal produttore                           | `intero`       |
| `fabric_name`          | Il nome del materiale                                                      | `stringa`      |
| `size_id`              | Il codice identificativo della taglia                                      | `intero`       |
| `size_type`            | La **tipologia della taglia**                                              | `stringa`      |
| `size_name`            | Il nome della taglia                                                       | `stringa`      |
| `is_product_visible`   | Impostazione che ci mostra se il prodotto è visibile                       | `booleano`     |
| `is_brand_deleted`     | Impostazione che ci mostra se il brand è cancellato                        | `booleano`     |
| `is_product_deleted`   | Impostazione che ci mostra se il prodotto è cancellato                     | `booleano`     |
| `is_fabric_deleted`    | Impostazione che ci mostra se il materiale è cancellato                    | `booleano`     |
| `is_color_deleted`     | Impostazione che ci mostra se il colore è cancellato                       | `booleano`     |
| `is_version_deleted`   | Impostazione che ci mostra se la variante è cancellata                     | `booleano`     |
| `is_color_deleted`     | Impostazione che ci mostra se il colore è cancellato                       | `booleano`     |
| `is_sku_deleted`       | Impostazione che ci mostra se lo sku è cancellato                          | `booleano`     |
| `date_created`         | Data di creazione oggetto                                                  | `datetime`     |
| `date_deleted`         | Data di eliminazione dell'oggetto                                          | `datetime`     |

___

# Metodo "list"

Il metodo **productsSKU**->**list**() richiede i seguenti argomenti.

## Parametri

| Campo                | Obbligatorio | Descrizione                                             | Data Type      |
|----------------------|--------------|---------------------------------------------------------|----------------|
| `r`                  | facoltativo  | Il numero di risultati per pagina                       | `intero`       |
| `p`                  | facoltativo  | La pagina da visualizzare                               | `intero`       |
| `s`                  | facoltativo  | La chiave di ordinamento da usare                       | `intero`       |
| `q`                  | facoltativo  | Una oggetto JSON contenente chiavi di ricerca           | `JSON`         |
| `q`.`product_name`   | facoltativo  | Ricerca libera sul campo `product_name`                 | `stringa`      |
| `q`.`product_type`   | facoltativo  | Ricerca esatta sul campo `product_type`                 | `stringa`      |
| `q`.`product_gender` | facoltativo  | Ricerca esatta sul campo `product_gender`               | `stringa`      |
| `q`.`product_target` | facoltativo  | Ricerca esatta sul campo `product_target`               | `stringa`      |
| `q`.`is_visible`     | facoltativo  | Ricerca esatta sui prodotti con status `is_visible`     | `intero`      |


### Parametri Sorting

| Sorting Key           | Descrizione                                |
|-----------------------|--------------------------------------------|
| `brand_name\|ASC`     | Ordina per nome brand ascendente           |
| `brand_name\|DES`     | Ordina per nome brand discendente          |
| `product_name\|ASC`   | Ordina per nome modello ascendente         |
| `product_name\|DES`   | Ordina per nome modello discendente        |
| `product_color\|ASC`  | Ordina per codice colore ascendente        |
| `product_color\|DES`  | Ordina per codice colore discendente       |
| `product_fabric\|ASC` | Ordina per codice materiale ascendente     |
| `product_fabric\|DES` | Ordina per codice materiale discendente    |


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

La ricerca sui **productsSKU** genera un dataset di oggetti di tipo **productSKU**.
Per visualizzare la struttura di un oggetto productSKU, guarda il risultato della funzione **productsSKU**->**get**()

___

# Metodo "create"

Il metodo <b>productsSKU</b>-><b>create</b>() richiede i seguenti argomenti.

## Parametri

| Campo                | Obbligatorio | Descrizione                                            | Data Type      |
|----------------------|--------------|--------------------------------------------------------|----------------|
| `product_version_id` | si           | Il codice identificativo della variante del prodotto   | `intero`       |
| `size_id`            | si           | Il codice identificativo della taglia                  | `intero`       |

## Risposta

La risposta è un nuovo oggetto `ProductSKU` ([vedi struttura oggetto ProductsSKU](#metodo-get)).

___

# Metodo "delete"

Il metodo <b>productsSKU</b>-><b>delete</b>() richiede i seguenti argomenti.

## Parametri

| Campo            | Obbligatorio | Descrizione                                          | Data Type      |
|------------------|--------------|------------------------------------------------------|----------------|
| `sku_id`         | sì           | Il codice identificativo dello sku                   | `intero`       |

## Risposta

Nessuna risposta.
