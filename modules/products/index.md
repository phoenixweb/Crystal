# Modulo Products

## Oggetto :: Products *(Modello)*
L'oggetto Products è quello che si può definire un **modello**.  
Dal modello principale verranno poi create diverse **varianti** (*ProductVariant*) e di ogni variante sarà possibile creare delle **SKU** (variante + taglia).

> E' possibile che in futuro tale oggetto venga rinominato più specificatamente
> **ProductModel** per rendere più esplicito il ruolo dell'oggetto.

Nella definizione di un modello è possibile specificare alcuni attributi che
possono assumere solo alcuni valori specifici.  
Di seguito analizziamo le chiavi supportate.

### Tipologie Modelli `product_type`

Le tipologie di modelli ammissibili con cui è possibile valorizzare l'attributo `product_type`:

- `shoes`,
- `sneakers`,
- `slippers`,
- `dress`,
- `short dress`,
- `long dress`,
- `blouse`,
- `gilet`,
- `jacket`,
- `jumper`,
- `sweater`,
- `sweatshirt`,
- `shirt`,
- `long shirt`,
- `t-shirt`,
- `bermuda`,
- `blazer`,
- `skirt`,
- `short skirt`,
- `long skirt`,
- `pants`,
- `shorts`,
- `boxer`,
- `slip`,
- `bodysuit`,
- `swimsuit`,
- `tank`,
- `top`,
- `socks`,
- `bag`,
- `suitecase`,
- `belt`,
- `gloves`,
- `hat`,
- `mask`,
- `foulard`,
- `scarf`,
- `earrings`

### Target di genere `product_gender`

I target di genere ammissibili con cui è possibile valorizzare l'attributo `product_gender`:

- `unisex`
- `man`
- `woman`

### Target di corporatura `product_target`

I target di corporatura ammissibili con cui è possibile valorizzare l'attributo `product_target`:

- ` ` (tutti)
- `children`
- `teenager`
- `adult`

___

## Metodi disponibili

I metodi che possono essere svolti sul modulo **Products** sono:

- [get](#metodo-get)
- [list](#metodo-list)
- [create](#metodo-create)
- [update](#metodo-update)
- [updateVisibility](#metodo-updatevisibility)
- [delete](#metodo-delete)
___

# Metodo "get"

Il metodo <b>products</b>-><b>get</b>() richiede i seguenti argomenti.

## Parametri

| Campo        | Obbligatorio | Descrizione                          | Data Type      |
|--------------|--------------|--------------------------------------|----------------|
| `product_id` | sì           | Il codice identificativo del modello | `intero`       |

## Risposta

| Campo             | Descrizione                                                       | Data Type      |
|-------------------|-------------------------------------------------------------------|----------------|
| `brand_id`        | Il codice identificativo del brand                                | `intero`       |
| `brand_name`      | Il nome del brand                                                 | `stringa`      |
| `product_id`      | Il codice identificativo del modello                              | `intero`       |
| `product_code`    | Il codice identificativo del modello assegnato dal produttore     | `stringa`      |
| `product_name`    | Il nome del modello assegnato dal produttore						| `stringa`      |
| `product_type`    | La **tipologia del modello** ([vedere lista](#tipologie-modelli-product_type))         | `stringa` |
| `product_gender`  | Il **target di genere** del modello ([vedere lista](#target-di-genere-product_gender)) | `stringa` |
| `product_target`  | Il **target di età** del modello ([vedere lista](#target-di-corporatura-product_target))    | `stringa` |
| `is_visible`      | Lo status di visibilità del modello sui cataloghi                 | `booleano`     |
| `lang_translated` | Lista delle lingue in cui è stato tradotta la descrizione modello | `array`        |
| `version_count`   | Il numero di varianti associate al modello                        | `intero`       |
| `sku_count`       | Il numero di singole SKU associate al modello                     | `intero`       |
| `date_created`    | Data di creazione oggetto                                         | `datetime`     |

___

# Metodo "list"

Il metodo **products**->**list**() richiede i seguenti argomenti.

## Parametri

| Campo                | Obbligatorio | Descrizione                                             | Data Type      |
|----------------------|--------------|---------------------------------------------------------|----------------|
| `r`                  | facoltativo  | Il numero di risultati per pagina                       | `intero`       |
| `p`                  | facoltativo  | La pagina da visualizzare                               | `intero`       |
| `s`                  | facoltativo  | La chiave di ordinamento da usare                       | `intero`       |
| `q`                  | facoltativo  | Una oggetto JSON contenente chiavi di ricerca           | `oggetto`      |
| `q`.`free`           | facoltativo  | Ricerca libera sul campo `product_name` e `brand_name`  | `stringa`      |
| `q`.`product_name`   | facoltativo  | Ricerca libera sul campo `product_name`                 | `stringa`      |
| `q`.`product_type`   | facoltativo  | Ricerca esatta sul campo `product_type`                 | `stringa`      |
| `q`.`product_gender` | facoltativo  | Ricerca esatta sul campo `product_gender`               | `stringa`      |
| `q`.`product_target` | facoltativo  | Ricerca esatta sul campo `product_target`               | `stringa`      |
| `q`.`brand_id`       | facoltativo  | Ricerca esatta sul campo `brand_id`                     | `stringa`      |
| `q`.`brands_ids`     | facoltativo  | Ricerca multipla sul campo `brand_id`                   | `array`      |
| `q`.`is_visible`     | facoltativo  | Ricerca esatta sui prodotti con status `is_visible`     | `intero`      |


### Parametri Sorting

| Sorting Key           | Descrizione                                |
|-----------------------|--------------------------------------------|
| `product_id\|ASC`     | Ordina per codice modello ascendente       |
| `product_id\|DES`     | Ordina per codice modello discendente      |
| `product_name\|ASC`   | Ordina per nome modello ascendente         |
| `product_name\|DES`   | Ordina per nome modello discendente        |
| `product_type\|ASC`   | Ordina per tipoologia prodotto ascendente  |
| `product_type\|DES`   | Ordina per tipoologia prodotto discendente |
| `brand_name\|ASC`     | Ordina per nome brand ascendente           |
| `brand_name\|DES`     | Ordina per nome brand discendente          |
| `versions_count\|ASC` | Ordina per numero di versioni ascendente   |
| `versions_count\|DES` | Ordina per numero di versioni discendente  |
| `skus_count\|ASC`     | Ordina per numero di SKU ascendente        |
| `skus_count\|DES`     | Ordina per numero di SKU discendente       |
| `date_created\|ASC`   | Ordina per data di creazione ascendente    |
| `date_created\|DES`   | Ordina per data di creazione discendente   |

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

La ricerca sui **modelli** genera un dataset di oggetti di tipo **product**.
Per visualizzare la struttura di un oggetto product, guarda il risultato della funzione **products**->**get**()

___

# Metodo "create"

Il metodo <b>products</b>-><b>create</b>() richiede i seguenti argomenti.

## Parametri

| Campo            | Obbligatorio | Descrizione                                          | Data Type      |
|------------------|--------------|------------------------------------------------------|----------------|
| `brand_id`       | sì           | Il codice identificativo del brand                   | `intero`       |
| `product_code`   | sì           | Il codice del modello assegnato dal produttore       | `stringa`      |
| `product_name`   | sì           | Il nome del modello assegnato dal produttore         | `stringa`      |
| `product_type`   | sì           | La **tipologia del modello** ([vedere lista](#tipologie-modelli-product_type))         | `stringa` |
| `product_gender` | facoltativo  | Il **target di genere** del modello ([vedere lista](#target-di-genere-product_gender)) | `stringa` |
| `product_target` | facoltativo  | Il **target di età** del modello ([vedere lista](#target-di-corporatura-product_target))    | `stringa` |
| `is_visible`	   | sì           | Impostazione dello status di visibilità              | `booleano`     |

## Risposta

La risposta è un nuovo oggetto `Product` ([vedi struttura oggetto Product](#metodo-get)).

___

# Metodo "update"

Il metodo <b>products</b>-><b>update</b>() richiede i seguenti argomenti.

## Parametri

| Campo            | Obbligatorio | Descrizione                                          | Data Type      |
|------------------|--------------|------------------------------------------------------|----------------|
| `product_id`     | sì           | Il codice identificativo del modello                 | `stringa`      |
| `product_code`   | sì           | Il codice del modello assegnato dal produttore       | `stringa`      |
| `product_name`   | sì           | Il nome del modello assegnato dal produttore         | `stringa`      |
| `product_type`   | sì           | La **tipologia del modello** ([vedere lista](#tipologie-modelli-product_type))         | `stringa` |
| `product_gender` | sì           | Il **target di genere** del modello ([vedere lista](#target-di-genere-product_gender)) | `stringa` |
| `product_target` | sì           | Il **target di età** del modello ([vedere lista](#target-di-corporatura-product_target))    | `stringa` |
| `is_visible`	   | sì           | Impostazione dello status di visibilità              | `booleano`     |

> ***Nota bene***  
> Una volta definito non è possibile modificare il `brand_id` di un Modello.

## Risposta

La risposta è l'oggetto `Product` aggiornato ([vedi struttura oggetto Product](#metodo-get)).
___

# Metodo "updateVisibility"

Il metodo <b>products</b>-><b>updateVisibility</b>() richiede i seguenti argomenti.

## Parametri

| Campo            | Obbligatorio | Descrizione                                          | Data Type      |
|------------------|--------------|------------------------------------------------------|----------------|
| `product_id`     | sì           | Il codice identificativo del modello                 | `stringa`      |
| `is_visible`	   | sì           | Impostazione dello status di visibilità              | `booleano`     |

## Risposta

La risposta è l'oggetto `Product` aggiornato ([vedi struttura oggetto Product](#metodo-get)).

___

# Metodo "delete"

Il metodo <b>products</b>-><b>delete</b>() richiede i seguenti argomenti.

## Parametri

| Campo            | Obbligatorio | Descrizione                                          | Data Type      |
|------------------|--------------|------------------------------------------------------|----------------|
| `product_id`     | sì           | Il codice identificativo del modello                 | `stringa`      |

## Risposta

Nessuna risposta.
