# Modulo Suppliers

## Oggetto :: SuppliersBuyers *(Cliente)*
L'oggetto SuppliersBuyers è quello che si definisce un **cliente**.  

___

## Metodi disponibili

I metodi che possono essere svolti sul modulo **SuppliersBuyers** sono:

- [get](#metodo-get)
- [create](#metodo-create)
- [update](#metodo-update)
- [createFullEntity](#metodo-createFullEntity)
- [updateFullEntity](#metodo-updateFullEntity)
- [delete](#metodo-delete)  
======== *Azioni list* ===================  
- [list](#metodo-list)

___

# Metodo "get"

Il metodo <b>suppliersBuyers</b>-><b>get</b>() non ha bisogno di parametri in ingresso.

## Risposta

| Campo                    | Descrizione                                                        | Data Type  |
|--------------------------|--------------------------------------------------------------------|------------|
| `buyer_id`               | Il codice identificativo del buyer                                 | `intero`   |
| `supplier_buyer_code`    | Il codice identificativo del buyer assegnato dal produttore        | `stringa`  |
| `supplier_buyer_name`    | Il nome del cliente                                                | `stringa`  |
| `buyer_type`             | La tipologia del buyer                                             | `intero`   |
| `entity_code`            | Il codice identificativo dell'ente                                 | `stringa`  |
| `entity_type`            | La tipologia di ente                                               | `intero`   |
| `entity_nationalitycode` | Il codice della nazionalità della società                          | `stringa`  |
| `org_name`               | La denominazione sociale                                           | `stringa`  |
| `org_vat_code`           | La partita IVA del soggetto                                        | `stringa`  |
| `org_tax_code`           | Il codice fiscale del soggetto                                     | `stringa`  |
| `address_street`         | Sede legale - Indirizzo                                            | `stringa`  |
| `address_street_number`  | Sede legale - Numero Civico                                        | `stringa`  |
| `address_city`           | Sede legale - Città                                                | `stringa`  |
| `address_province`       | Sede legale - Provincia                                            | `stringa`  |
| `address_postalcode`     | Sede legale - Codice di avviamento postale                         | `stringa`  |
| `address_countrycode`    | Sede legale - Codice paese (nazione)                               | `stringa`  |
| `vat_rate`               | L'aliquota IVA                                                     | `intero`   |
| `einvoice_type`          | La destinazione di fatturazione elettronica                        | `intero`   |
| `einvoice_pec`           | L'indirizzo PEC della fatturazione elettronica                     | `intero`   |
| `einvoice_code`          | Il codice identificativo di sette cifre dell'ufficio               | `stringa`  |
| `stores_list`\[**`n`**\] | L'identificativo `store_id` di uno store                           | `intero`   |
| `date_created`           | Data di creazione oggetto                                          | `datetime` |

___

# Metodo "create"

Il metodo <b>suppliersBuyers</b>-><b>create</b>() richiede i seguenti argomenti.

## Parametri

| Campo                 | Obbligatorio | Descrizione                                                  | Data Type |
|-----------------------|--------------|--------------------------------------------------------------|-----------|
| `buyer_id`            | sì           | Il codice identificativo del buyer                           | `intero`  |
| `supplier_buyer_code` | facoltativo  | Il codice identificativo del cliente                         | `intero`  |
| `supplier_buyer_name` | facoltativo  | Il codice identificativo del cliente                         | `intero`  |

## Risposta

La risposta è un nuovo oggetto `SuppliersBuyers` ([vedi struttura oggetto SupplierBuyer](#metodo-get)).

___

# Metodo "createFullEntity"

Il metodo <b>suppliersBuyers</b>-><b>createFullEntity</b>() richiede i seguenti argomenti.

## Parametri

| Campo                    | Obbligatorio | Descrizione                                           | Data Type |
|--------------------------|--------------|-------------------------------------------------------|-----------|
| `supplier_buyer_code`    | facoltativo  | Il codice identificativo del cliente                  | `stringa` |
| `supplier_buyer_name`    | facoltativo  | Il codice identificativo del cliente                  | `stringa` |
| `buyer_type`             | sì           | La tipologia del buyer                                | `intero`  |
| `entity_code`            | sì           | Il codice identificativo dell'ente                    | `stringa` |
| `entity_type`            | sì           | La tipologia di ente                                  | `intero`  |
| `entity_nationalitycode` | sì           | La nazionalità dell'ente                              | `stringa` |
| `org_name`               | sì           | La denominazione sociale                              | `stringa` |
| `org_vat_code`           | sì           | La partita IVA del soggetto                           | `stringa` |
| `org_tax_code`           | sì           | Il codice fiscale del soggetto                        | `stringa` |
| `address_street`         | sì           | Sede legale - Indirizzo                               | `stringa` |
| `address_street_number`  | sì           | Sede legale - Numero Civico                           | `stringa` |
| `address_city`           | sì           | Sede legale - Città                                   | `stringa` |
| `address_province`       | sì           | Sede legale - Provincia                               | `stringa` |
| `address_postalcode`     | sì           | Sede legale - Codice di avviamento postale            | `stringa` |
| `address_countrycode`    | sì           | Sede legale - Codice paese (nazione)                  | `stringa` |
| `vat_rate`               | sì           | L'aliquota IVA                                        | `intero`  |
| `einvoice_type`          | sì           | La destinazione di fatturazione elettronica           | `intero`  |
| `einvoice_pec`           | facoltativo  | L'indirizzo PEC della fatturazione elettronica        | `intero`  |
| `einvoice_code`          | facoltativo  | Il codice identificativo di sette cifre dell'ufficio  | `stringa` |

## Risposta

La risposta è un nuovo oggetto `SuppliersBuyers` ([vedi struttura oggetto SupplierBuyer](#metodo-get)).

___

# Metodo "update"

Il metodo <b>suppliersBuyers</b>-><b>update</b>() richiede i seguenti argomenti.

## Parametri

| Campo                 | Obbligatorio | Descrizione                                                  | Data Type |
|-----------------------|--------------|--------------------------------------------------------------|-----------|
| `buyer_id`            | sì           | Il codice identificativo del cliente                         | `intero`  |
| `supplier_buyer_code` | facoltativo  | Il codice univoco del cliente                                | `stringa` |
| `supplier_buyer_name` | facoltativo  | Il nome del cliente                                          | `stringa` |

> ***Nota bene***  
> Una volta definiti non è possibile modificare `supplier_id` e `buyer_id` di un cliente.

## Risposta

La risposta è un oggetto `SuppliersBuyers` aggiornato ([vedi struttura oggetto SupplierBuyer](#metodo-get)).

___

# Metodo "updateFullEntity"

Il metodo <b>suppliersBuyers</b>-><b>updateFullEntity</b>() richiede i seguenti argomenti.

## Parametri

| Campo                    | Obbligatorio | Descrizione                                           | Data Type |
|--------------------------|--------------|-------------------------------------------------------|-----------|
| `buyer_id`               | sì           | Il codice identificativo del cliente                  | `intero`  |
| `supplier_buyer_code`    | facoltativo  | Il codice identificativo del cliente                  | `stringa` |
| `supplier_buyer_name`    | facoltativo  | Il codice identificativo del cliente                  | `stringa` |
| `buyer_type`             | sì           | La tipologia del buyer                                | `intero`  |
| `entity_code`            | sì           | Il codice identificativo dell'ente                    | `stringa` |
| `entity_type`            | sì           | La tipologia di ente                                  | `intero`  |
| `entity_nationalitycode` | sì           | La nazionalità dell'ente                              | `stringa` |
| `org_name`               | sì           | La denominazione sociale                              | `stringa` |
| `org_vat_code`           | sì           | La partita IVA del soggetto                           | `stringa` |
| `org_tax_code`           | sì           | Il codice fiscale del soggetto                        | `stringa` |
| `address_street`         | sì           | Sede legale - Indirizzo                               | `stringa` |
| `address_street_number`  | sì           | Sede legale - Numero Civico                           | `stringa` |
| `address_city`           | sì           | Sede legale - Città                                   | `stringa` |
| `address_province`       | sì           | Sede legale - Provincia                               | `stringa` |
| `address_postalcode`     | sì           | Sede legale - Codice di avviamento postale            | `stringa` |
| `address_countrycode`    | sì           | Sede legale - Codice paese (nazione)                  | `stringa` |
| `vat_rate`               | sì           | L'aliquota IVA                                        | `intero`  |
| `einvoice_type`          | sì           | La destinazione di fatturazione elettronica           | `intero`  |
| `einvoice_pec`           | facoltativo  | L'indirizzo PEC della fatturazione elettronica        | `intero`  |
| `einvoice_code`          | facoltativo  | Il codice identificativo di sette cifre dell'ufficio  | `stringa` |

> ***Nota bene***  
> Una volta definiti non è possibile modificare `supplier_id` e `buyer_id` di un cliente.

## Risposta

La risposta è un oggetto `SuppliersBuyers` aggiornato ([vedi struttura oggetto SupplierBuyer](#metodo-get)).

___

# Metodo "delete"

Il metodo <b>suppliersBuyers</b>-><b>delete</b>() richiede i seguenti argomenti.

## Parametri

| Campo       | Obbligatorio | Descrizione                                                  | Data Type |
|-------------|--------------|--------------------------------------------------------------|-----------|
| `buyer_id`  | sì           | Il codice identificativo del cliente                         | `intero`  |

## Risposta

Nessuna risposta.

___

# Metodo "list"

Il metodo **suppliersBuyers**->**list**() richiede i seguenti argomenti.

## Parametri

| Campo                     | Obbligatorio | Descrizione                                                            | Data Type |
|---------------------------|--------------|------------------------------------------------------------------------|-----------|
| `r`                       | facoltativo  | Il numero di risultati per pagina                                      | `intero`  |
| `p`                       | facoltativo  | La pagina da visualizzare                                              | `intero`  |
| `s`                       | facoltativo  | La chiave di ordinamento da usare                                      | `intero`  |
| `q`                       | facoltativo  | Un oggetto contenente chiavi di ricerca                                | `oggetto` |
| `q`.`free`                | facoltativo  | Ricerca libera sui campi `supplier_buyer_name` e `supplier_buyer_code` | `stringa` |
| `q`.`buyer_id`            | facoltativo  | Ricerca esatta sul campo `buyer_id`                                    | `stringa` |
| `q`.`buyer_name`          | facoltativo  | Ricerca libera sul campo `buyer_name`                                  | `stringa` |
| `q`.`supplier_buyer_name` | facoltativo  | Ricerca libera sul campo `supplier_buyer_name`                         | `stringa` |

### Parametri Sorting

| Sorting Key                | Descrizione                                          |
|----------------------------|------------------------------------------------------|
| `buyer_id\|ASC`            | Ordina per codice buyer ascendente                   |
| `buyer_id\|DES`            | Ordina per codice buyer discendente                  |
| `supplier_buyer_name\|ASC` | Ordina per nome cliente ascendente                   |
| `supplier_buyer_name\|DES` | Ordina per nome cliente discendente                  |
| `supplier_buyer_code\|ASC` | Ordina per codice cliente ascendente                 |
| `supplier_buyer_code\|DES` | Ordina per codice cliente discendente                |
| `entity_code\|ASC`         | Ordina per codice società discendente                |
| `entity_code\|DES`         | Ordina per codice società discendente                |
| `address_countrycode\|ASC` | Ordina per codice nazionalità discendente            |
| `address_countrycode\|DES` | Ordina per codice nazionalità discendente            |
| `address_province\|ASC`    | Ordina per provincia discendente                     |
| `address_province\|DES`    | Ordina per provincia discendente                     |
| `date_created\|ASC`        | Ordina per data di creazione ascendente              |
| `date_created\|DES`        | Ordina per data di creazione discendente             |

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

La ricerca sui **clienti** genera un dataset di oggetti di tipo **supplierBuyer**.
Per visualizzare la struttura di un oggetto supplierBuyer, guarda il risultato della funzione **suppliersBuyers**->**get**()
