# Modulo Products

## Oggetto :: ProductsVersions *(Articoli)*
L'oggetto ProductsVersions  descrive una variante che è possibile definire partendo dal modello prinicipale (Product).
E' costitutito dalla combinazione di:

- [Products](../products/index.md) *(modelli)*
- [ProductsColors](../productsColors/index.md) *(colori)*
- [ProductsFabrics](../productsFabrics/index.md) *(materiali)*

___

## Metodi disponibili

I metodi che possono essere svolti sul modulo **Products** sono:

- [get](#metodo-get)
- [create](#metodo-create)
- [update](#metodo-update)
- [delete](#metodo-delete)
- [setSizes](#metodo-setSizes)
======== * Azioni list ===================
- [list](#metodo-list)
- [listSKU](#metodo-listSKU)
- [listCollections](#metodo-listCollections)
- [listOutfits](#metodo-listOutfits)
- [listOrders](#metodo-listOrders)
___

# Metodo "get"

Il metodo <b>productsVersions</b>-><b>get</b>() richiede i seguenti argomenti.

## Parametri

| Campo                | Obbligatorio | Descrizione                             | Data Type      |
|----------------------|--------------|-----------------------------------------|----------------|
| `product_version_id` | sì           | Il codice identificativo della variante | `intero`       |

## Risposta

| Campo                 | Descrizione                                                                              | Data Type      |
|-----------------------|------------------------------------------------------------------------------------------|----------------|
| `brand_name`          | Il nome del brand                                                                        | `stringa`      |
| `brand_id`            | Il codice identificativo del brand                                                       | `intero`       |
| `product_id`          | Il codice identificativo del modello                                                     | `intero`       |
| `product_name`        | Il nome del modello assegnato dal produttore                                             | `stringa`      |
| `product_name_full`   | Il nome costruito in modo dinamico con nome prodotto, materiale e colore                 | `stringa`      |
| `product_code`        | Il codice identificativo del modello assegnato dal produttore                            | `stringa`      |
| `product_type`        | La **tipologia del modello** ([vedere lista](#tipologie-modelli-product_type))           | `stringa`      |
| `product_gender`      | Il **target di genere** del modello ([vedere lista](#target-di-genere-product_gender))   | `stringa`      |
| `product_target`      | Il **target di età** del modello ([vedere lista](#target-di-corporatura-product_target)) | `stringa`      |
| `product_version_id`  | Il codice identificativo del prodotto                                                    | `intero`       |
| `product_version_hash`| Il codice hash del prodotto                                                              | `stringa`      |
| `color_id`            | Il codice identificativo del colore                                                      | `intero`       |
| `color_name`          | Il nome del colore                                                                       | `stringa`      |
| `color_code`          | Il codice identificativo del colore assegnato dal produttore                             | `intero`       |
| `color_rgb`           | Il modello additivo del colore                                                           | `intero`     |
| `fabric_id`           | Il codice identificativo del materiale                                                   | `intero`        |
| `fabric_name`         | Il nome del materiale                                                                    | `stringa`       |
| `fabric_code`         | Il codice del materiale assegnato dal produttore                                         | `intero`        |
| `sku_list`            | L' insieme degli SKU di quel prodotto derivanti dalle diverse taglie disponibili         | `array`         |
| `images_list`         | L' insieme delle immagini di quel prodotto                                               | `array`         |
| `is_product_visible`  | Impostazione che ci mostra se il prodotto è visibile                                     | `booleano`      |
| `is_brand_deleted`    | Impostazione che ci mostra se il brand è cancellato                                      | `booleano`      |
| `is_product_deleted`  | Impostazione che ci mostra se il prodotto è cancellato                                   | `booleano`      |
| `is_fabric_deleted`   | Impostazione che ci mostra se il materiale è cancellato                                  | `booleano`     |
| `is_color_deleted`    | Impostazione che ci mostra se il colore è cancellato                                     | `booleano`     |
| `is_version_deleted`  | Impostazione che ci mostra se la variante è cancellata                                   | `booleano`     |
| `is_color_deleted`    | Impostazione che ci mostra se il colore è cancellato                                     | `booleano`     |
| `date_created`        | Data di creazione oggetto                                                                | `datetime`     |
| `date_dismissed`      | Data di dismissione dell'articolo                                                        | `datetime`     |
| `date_deleted`        | Data di eliminazione dell'oggetto                                                        | `datetime`     |

___

# Metodo "create"

Il metodo <b>productsVersions</b>-><b>create</b>() richiede i seguenti argomenti.

## Parametri

| Campo            | Obbligatorio | Descrizione                                          | Data Type      |
|------------------|--------------|------------------------------------------------------|----------------|
| `brand_id`       | sì           | Il codice identificativo del brand                   | `intero`       |
| `product_id`     | sì           | Il codice identificativo del modello                 | `intero `      |
| `color_id`       | facoltativo  | Il codice identificativo del colore                  | `intero `      |
| `fabric_id`      | facoltativo  | Il codice identificativo del materiale               | `intero      ` |

## Risposta

La risposta è un nuovo oggetto `ProductVersion` ([vedi struttura oggetto ProductVersion](#metodo-get)).

___

# Metodo "delete"

Il metodo <b>productsVersions</b>-><b>delete</b>() richiede i seguenti argomenti.

## Parametri

| Campo                  | Obbligatorio | Descrizione                                          | Data Type      |
|------------------------|--------------|------------------------------------------------------|----------------|
| `product_version_id`   | sì           | Il codice identificativo della variante              | `intero `      |

## Risposta

Nessuna risposta.
___

# Metodo "setSizes"

Il metodo <b>productsVersions</b>-><b>setSizes</b>() permette di impostare le taglie di una variante del prodotto,
creando quindi nuovi SKU per ognuna di esse, richiede un array di taglie.

## Parametri

| Campo       | Obbligatorio | Descrizione                                                                  | Data Type      |
|-------------|--------------|------------------------------------------------------------------------------|----------------|
| `new_sizes` | sì           | Insieme delle taglie che si desidera associare a quella variante di prodotto | `array`        |

## Risposta

La risposta è un nuovo oggetto `ProductVersion` ([vedi struttura oggetto ProductVersion](#metodo-get)).___

___

# Metodo "list"

Il metodo **productsVersions**->**list**() richiede i seguenti argomenti.

## Parametri

| Campo                | Obbligatorio | Descrizione                                             | Data Type      |
|----------------------|--------------|---------------------------------------------------------|----------------|
| `r`                  | facoltativo  | Il numero di risultati per pagina                       | `intero`       |
| `p`                  | facoltativo  | La pagina da visualizzare                               | `intero`       |
| `s`                  | facoltativo  | La chiave di ordinamento da usare                       | `intero`       |
| `q`                  | facoltativo  | Una oggetto JSON contenente chiavi di ricerca           | `oggetto`      |
| `q`.`free`           | facoltativo  | Ricerca libera sul campo `product_name` e `brand_name`  | `stringa`      |
| `q`.`product_type`   | facoltativo  | Ricerca esatta sul campo `product_type`                 | `stringa`      |
| `q`.`product_gender` | facoltativo  | Ricerca esatta sul campo `product_gender`               | `stringa`      |
| `q`.`product_target` | facoltativo  | Ricerca esatta sul campo `product_target`               | `stringa`      |
| `q`.`is_visible`     | facoltativo  | Ricerca esatta sulle varianti con status `is_visible`   | `intero`       |
| `q`.`status`         | facoltativo  | Ricerca esatta sullo status delle varianti (is_deleted) | `intero`       |


### Parametri Sorting

| Sorting Key           | Descrizione                                    |
|-----------------------|------------------------------------------------|
| `product_id\  |ASC`   | Ordina per codice variante modello ascendente  |
| `product_id\  |DES`   | Ordina per codice variante modello discendente |
| `brand_name\  |ASC`   | Ordina per nome brand ascendente               |
| `brand_name\  |DES`   | Ordina per nome brand discendente              |
| `product_name\|ASC`   | Ordina per nome modello ascendente             |
| `product_name\|DES`   | Ordina per nome modello discendente            |
| `color_code\  |ASC`   | Ordina per codice colore ascendente            |
| `color_code\  |DES`   | Ordina per codice colore discendente           |
| `fabric_code\ |ASC`   | Ordina per codice colore ascendente            |
| `fabric_code\ |DES`   | Ordina per codice colore discendente           |
| `date_created\|ASC`   | Ordina per data di creazione ascendente        |
| `date_created\|DES`   | Ordina per data di creazione discendente       |

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

La ricerca sulle **varianti prodotto** genera un dataset di oggetti di tipo **productVersion**.
Per visualizzare la struttura di un oggetto productVersion, guarda il risultato della funzione **products**->**get**()

___
*********Metodi list avanzati*********

# Metodo "listSKU"

Il metodo **productsVersions**->**listSKU**() permette di filtrare gli SKU sulla base di una specifica variante di prodotto,
richiede i seguenti argomenti.

### Parametri Sorting

| Sorting Key           | Descrizione                                    |
|-----------------------|------------------------------------------------|
| `sku_id\      |ASC`   | Ordina per codice SKU ascendente               |
| `sku_id\      |DES`   | Ordina per codice SKU discendente              |
| `brand_name\  |ASC`   | Ordina per nome brand ascendente               |
| `brand_name\  |DES`   | Ordina per nome brand discendente              |
| `product_name\|ASC`   | Ordina per nome modello ascendente             |
| `product_name\|DES`   | Ordina per nome modello discendente            |
| `color_code\  |ASC`   | Ordina per codice colore ascendente            |
| `color_code\  |DES`   | Ordina per codice colore discendente           |
| `fabric_code\ |ASC`   | Ordina per codice colore ascendente            |
| `fabric_code\ |DES`   | Ordina per codice colore discendente           |

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

La ricerca sugli **SKU** filtarti per **varianti prodotto**  genera un dataset di oggetti di tipo **productSKU**.
Per visualizzare la struttura di un oggetto productSKU, guarda il risultato della funzione **productsSKU**->**get**()

___
Altri metodi list ancora da inserire, per ognuno mettere il link alla funzione **get** della relativa pagina,
per poter visualizzare facilmente la struttura del singolo oggetto in questione.