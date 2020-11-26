# Modulo ProductsColors

## Oggetto :: ProductsColors *(Cartella Colore)*
L'oggetto **ProductColor** definisce le informazioni relative ad un colore o una
combinazione di colori che potrà essere allegata ad un prodotto per descriverlo.


>E' possibile definire un colore specificando nome, brand di riferimento, codice **RGB** (formato esadecimale) ed un codice colore identificativo *univoco*.
>Qui è possibile effetuare delle prove e degli approfondimenti in merito: *https://htmlcolorcodes.com/*

All'interno della scheda colore sono presenti dati riguardanti il **brand** di appartenenza, il codice **RGB**,  
ed in maniera *opzionale* può essere aggiunta un'**immagine di anteprima** del colore stesso.

___

### Metodi disponibili

I metodi che possono essere svolti sul modulo **ProductsColors** sono:

- [get](#metodo-get)
- [create](#metodo-create)
- [update](#metodo-update)
- [delete](#metodo-delete)
- [list](#metodo-list)
___

# Metodo "get"

Il metodo <b>productsColors</b>-><b>get</b>() richiede i seguenti argomenti.

## Parametri

| Campo      | Obbligatorio | Descrizione                         | Data Type |
|------------|--------------|-------------------------------------|-----------|
| `color_id` | sì           | Il codice identificativo del colore | `intero`  |

## Risposta

| Campo          | Descrizione                                                  | Data Type  |
|----------------|--------------------------------------------------------------|------------|
| `brand_id`     | Il codice identificativo del brand                           | `intero`   |
| `brand_name`   | Il nome del brand                                            | `stringa`  |
| `color_id`     | Il codice identificativo del colore                          | `intero`   |
| `image_id`     | Il codice identificativo dell'immagine                       | `intero`   |
| `color_code`   | Il codice identificativo del colore assegnato dal produttore | `stringa`  |
| `color_name`   | Il nome del colore                                           | `stringa`  |
| `color_rgb`    | Il codice RGB del colore assegnato dal produttore            | `stringa`  |
| `is_deleted`   | Lo status di cancellazione del modello sui cataloghi         | `booleano` |
| `date_created` | Data di creazione oggetto                                    | `datetime` |
| `date_deleted` | Data di cancellazione oggetto                                | `datetime` |

___

# Metodo "create"

Il metodo <b>productsColors</b>-><b>create</b>() richiede i seguenti argomenti.

## Parametri

| Campo        | Obbligatorio | Descrizione                                   | Data Type |
|--------------|--------------|-----------------------------------------------|-----------|
| `brand_id`   | sì           | Il codice identificativo del brand            | `intero`  |
| `color_code` | sì           | Il codice del colore assegnato dal produttore | `stringa` |
| `color_name` | sì           | Il nome del colore assegnato dal produttore   | `stringa` |
| `color_rgb`  | facoltativo  | Il codice RGB assegnato dal produttore        | `stringa` |

## Risposta

La risposta è un nuovo oggetto `ProductColor` ([vedi struttura oggetto ProductColor](#metodo-get)).

___

# Metodo "update"

Il metodo <b>productsColors</b>-><b>update</b>() richiede i seguenti argomenti.

## Parametri

| Campo        | Obbligatorio | Descrizione                                                    | Data Type |
|--------------|--------------|----------------------------------------------------------------|-----------|
| `color_id`   | sì           | Il codice identificativo del colore che si desidera modificare | `intero`  |
| `color_code` | sì           | Il codice del colore assegnato dal produttore                  | `stringa` |
| `color_name` | sì           | Il nome del colore assegnato dal produttore                    | `stringa` |
| `color_rgb`  | facoltativo  | Il codice RGB assegnato dal produttore                         | `stringa` |

> ***Nota bene***  
> Una volta definito non è possibile modificare il `brand_id` di un Colore.

## Risposta

La risposta è l'oggetto `ProductColor` aggiornato ([vedi struttura oggetto ProductColor](#metodo-get)).

___

# Metodo "delete"

Il metodo <b>productsColors</b>-><b>delete</b>() richiede i seguenti argomenti.

## Parametri

| Campo      | Obbligatorio | Descrizione                         | Data Type |
|------------|--------------|-------------------------------------|-----------|
| `color_id` | sì           | Il codice identificativo del colore | `stringa` |

## Risposta

Nessuna risposta.

___

# Metodo "list"

Il metodo **productsColors**->**list**() richiede i seguenti argomenti.

## Parametri

| Campo            | Obbligatorio | Descrizione                                                        | Data Type |
|------------------|--------------|--------------------------------------------------------------------|-----------|
| `r`              | facoltativo  | Il numero di risultati per pagina                                  | `intero`  |
| `p`              | facoltativo  | La pagina da visualizzare                                          | `intero`  |
| `s`              | facoltativo  | La chiave di ordinamento da usare                                  | `intero`  |
| `q`              | facoltativo  | Un oggetto contenente chiavi di ricerca                            | `oggetto` |
| `q`.`free`       | facoltativo  | Ricerca libera sul campo `color_code`, `color_name` e `brand_name` | `stringa` |
| `q`.`brand_id`   | facoltativo  | Ricerca libera sul campo `brand_id`                                | `stringa` |
| `q`.`brand_name` | facoltativo  | Ricerca esatta sul campo `brand_name`                              | `stringa` |

### Parametri Sorting

| Sorting Key         | Descrizione                              |
|---------------------|------------------------------------------|
| `color_id\|ASC`     | Ordina per codice colore ascendente      |
| `color_id\|DES`     | Ordina per codice colore discendente     |
| `color_name\|ASC`   | Ordina per nome colore ascendente        |
| `color_name\|DES`   | Ordina per nome colore discendente       |
| `color_code\|ASC`   | Ordina per codice colore ascendente      |
| `color_code\|DES`   | Ordina per codice colore discendente     |
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

La ricerca sui **modelli** genera un dataset di oggetti di tipo **productColor**.
Per visualizzare la struttura di un oggetto productColor, guarda il risultato della funzione **productsColors**->**get**()
