# Modulo BuyersAddresses

## Oggetto :: BuyersAddresses *(Indirizzi del cliente)*
L'oggetto BuyerAddress descrive un **Indirizzo**.  

## Metodi disponibili

I metodi che possono essere svolti sul modulo **BuyersAddresses** sono:

- [get](#metodo-get)
- [list](#metodo-list)
- [create](#metodo-create)
- [update](#metodo-update)
- [delete](#metodo-delete)
- [setAsPrimary](#metodo-setAsPrimary)

___

# Metodo "get"

Il metodo <b>buyerAddress</b>-><b>get</b>() richiede i seguenti argomenti. 

## Parametri

| Campo        | Obbligatorio | Descrizione                             | Data Type |
|--------------|--------------|-----------------------------------------|-----------|
| `address_id` | sì           | Il codice identificativo dell'indirizzo | `intero`  |

## Risposta

| Campo                   | Descrizione                                  | Data Type  |
|-------------------------|----------------------------------------------|------------|
| `address_id`            | Il codice identificativo dell'indirizzo      | `intero`   |
| `buyer_id`              | Il codice identificativo del cliente         | `intero`   |
| `address_fingerprint`   | L'impronta digitale registrata dal cliente   | `stringa`  |
| `org_name`              | Il nome della società                        | `stringa`   |
| `name`                  | Il nome del cliente                          | `stringa`  |
| `surname`               | Il nome del cliente                          | `stringa`  |
| `address_street`        | La via dell'indirizzo                        | `stringa`  |
| `address_street_number` | Il numero civico                             | `intero`  |
| `address_city`          | Il nome della città di riferimento           | `stringa`  |
| `address_province`      | Il nome della provincia di riferimento       | `stringa`  |
| `address_postalcode`    | Il codice postale di riferimento             | `intero`  |
| `address_countrycode`   | Il codice nazionale di riferimento           | `stringa`  |
| `contact_tel`           | Il recapito telefonico registato dal cliente | `intero`  |
| `is_primary`            | Lo status di preferenza dell'indirizzo       | `booleano` |
| `is_visible`            | Lo status di visibilità dell'indirizzo       | `booleano` |
| `date_created`          | Data di cancellazione oggetto                | `datetime` |
| `date_deleted`          | Data di modifica oggetto                     | `datetime` |

___

# Metodo "create"

Il metodo <b>buyerAddress</b>-><b>create</b>() genera un nuovo indirizzo.

## Parametri

| Campo                   | Descrizione                                   | Data Type |
|-------------------------|-----------------------------------------------|-----------|
| `buyer_id`              | Il codice identificativo del cliente          | `intero`  |
| `address_fingerprint`   | L'impronta digitale registrata dal cliente    | `stringa` |
| `org_name`              | Il nome della società                         | `atringa` |
| `name`                  | Il nome del cliente                           | `stringa` |
| `surname`               | Il cognome del cliente                        | `stringa` |
| `address_street`        | La via dell'indirizzo                         | `stringa` |
| `address_street_number` | Il numero civico                              | `intero`  |
| `address_city`          | La città di residenza                         | `stringa` |
| `address_province`      | La provincia di residenza                     | `stringa` |
| `address_postalcode`    | Il codice postale di riferimento              | `intero`  |
| `address_countrycode`   | Il codice nazionale di riferimento            | `stringa` |
| `contact_tel`           | Il recapito telefonico registrato dal cliente | `stringa` |

## Risposta

La risposta è un nuovo oggetto `BuyerAddress` ([vedi struttura oggetto BuyerAddress](#metodo-get)).

___

# Metodo "update"

Il metodo <b>buyerAddress</b>-><b>update</b>() richiede i seguenti argomenti.

## Parametri

| Campo                   | Descrizione                                   | Data Type |
|-------------------------|-----------------------------------------------|-----------|
| `buyer_id`              | Il codice identificativo del cliente          | `intero`  |
| `address_fingerprint`   | L'impronta digitale registrata dal cliente    | `stringa` |
| `org_name`              | Il nome della società                         | `atringa` |
| `name`                  | Il nome del cliente                           | `stringa` |
| `surname`               | Il cognome del cliente                        | `stringa` |
| `address_street`        | La via dell'indirizzo                         | `stringa` |
| `address_street_number` | Il numero civico                              | `intero`  |
| `address_city`          | La città di residenza                         | `stringa` |
| `address_province`      | La provincia di residenza                     | `stringa` |
| `address_postalcode`    | Il codice postale di riferimento              | `intero`  |
| `address_countrycode`   | Il codice nazionale di riferimento            | `stringa` |
| `contact_tel`           | Il recapito telefonico registrato dal cliente | `stringa` |

## Risposta

La risposta è l'oggetto `BuyerAddress` aggiornato ([vedi struttura oggetto BuyerAddress](#metodo-get)).

___

# Metodo "list"

Il metodo **buyerAddress**->**list**() richiede i seguenti argomenti.

## Parametri

| Campo                | Obbligatorio | Descrizione                                                                    | Data Type |
|----------------------|--------------|--------------------------------------------------------------------------------|-----------|
| `r`                  | facoltativo  | Il numero di risultati per pagina                                              | `intero`  |
| `p`                  | facoltativo  | La pagina da visualizzare                                                      | `intero`  |
| `s`                  | facoltativo  | La chiave di ordinamento da usare                                              | `intero`  |
| `q`                  | facoltativo  | Una oggetto JSON contenente chiavi di ricerca                                  | `oggetto` |
| `q`.`free`           | facoltativo  | Ricerca libera sul campo `address_street`, `address_city` e `address_province` | `stringa` |
| `q`.`buyer_id`       | facoltativo  | Ricerca esatta sul campo `buyer_id`                                            | `stringa` |
| `q`.`address_street` | facoltativo  | Ricerca esatta sul campo `address_street`                                       | `stringa` |
| `q`.`address_city`   | facoltativo  | Ricerca esatta sul campo `address_city`                                       | `stringa` |


### Parametri Sorting

| Sorting Key       | Descrizione                             |
|-------------------|-----------------------------------------|
| `address_id\|ASC` | Ordina per codice indirizzo ascendente  |
| `address_id\|DES` | Ordina per codice indirizzo discendente |

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

La ricerca sugli **indirizzi** genera un dataset di oggetti di tipo **buyerAddress**.
Per visualizzare la struttura di un oggetto buyerAddress, guarda il risultato della funzione **buyerAddress**->**get**()

___

# Metodo "delete"

Il metodo <b>buyerAddress</b>-><b>delete</b>() richiede i seguenti argomenti.

## Parametri

| Campo        | Obbligatorio | Descrizione                             | Data Type |
|--------------|--------------|-----------------------------------------|-----------|
| `address_id` | sì           | Il codice identificativo dell'indirizzo | `stringa` |

## Risposta

Nessuna risposta.

___

# Metodo "setAsPrimary"

Il metodo <b>buyerAddress</b>-><b>setAsPrimary</b>() richiede i seguenti argomenti.

## Parametri

| Campo      | Obbligatorio | Descrizione                          | Data Type |
|------------|--------------|--------------------------------------|-----------|
| `buyer_id` | sì           | Il codice identificativo del cliente | `stringa` |

## Risposta

La risposta è l'oggetto `BuyerAddress` impostato come predefinito ([vedi struttura oggetto BuyerAddress](#metodo-get)).
