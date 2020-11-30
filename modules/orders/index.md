# Modulo Orders

## Oggetto :: Orders *(Ordini)*
L'oggetto Orders è quello che si definisce un **ordine**.  

___

## Metodi disponibili

I metodi che possono essere svolti sul modulo **Orders** sono:

- [get](#metodo-get)
- [create](#metodo-create)
- [update](#metodo-update)
- [setApproved](#metodo-setApproved)
- [delete](#metodo-delete)
- [list](#metodo-list)
___

# Metodo "get"

Il metodo <b>orders</b>-><b>get</b>() non ha bisogno di parametri in ingresso.

## Risposta

| Campo                        | Descrizione                                                     | Data Type  |
|------------------------------|-----------------------------------------------------------------|------------|
| `store_id`                   | Il codice identificativo del negozio                            | `intero`   |
| `store_token`                | Il codice identificativo del negozio                            | `stringa`  |
| `store_name`                 | Il nome del negozio                                             | `stringa`  |
| `supplier_id`                | Il codice identificativo del distributore                       | `intero`   |
| `supplier_token`             | Il codice identificativo del distributore                       | `stringa`  |
| `supplier_name`              | Il nome del distributore                                        | `stringa`  |
| `supplier_buyer_name`        | Il nome del cliente del distributore                            | `stringa`  |
| `supplier_buyer_code`        | Il codice univoco del cliente del distributore                  | `stringa`  |
| `supplier_buyer_id`          | Il codice identificativo del cliente del distributore           | `intero`   |
| `buyer_id`                   | Il codice identificativo del cliente                            | `intero`   |
| `buyer_token`                | Il codice identificativo del cliente                            | `stringa`  |
| `buyer_name`                 | Il nome del cliente                                             | `stringa`  |
| `agent_id`                   | Il codice identificativo dell'agente                            | `intero`   |
| `agent_token`                | Il codice identificativo dell'agente                            | `stringa`  |
| `agent_name`                 | Il nome dell'agente                                             | `stringa`  |
| `brand_id`                   | Il codice identificativo del brand                              | `intero`   |
| `brand_name`                 | Il nome del brand                                               | `stringa`  |
| `collection_id`              | Il codice identificativo della collezione                       | `intero`   |
| `collection_name`            | Il nome della collezione                                        | `stringa`  |
| `address_street`             | L'indirizzo di spedizione                                       | `stringa`  |
| `address_street_number`      | Il numero civico                                                | `stringa`  |
| `address_city`               | La città                                                        | `stringa`  |
| `address_province`           | La provincia                                                    | `stringa`  |
| `address_postalcode`         | Il codice postale                                               | `stringa`  |
| `address_countrycode`        | Il codice nazione                                               | `stringa`  |
| `buyer_address_date_deleted` | Data di cancellazione dell'indirizzo del cliente                | `datetime` |
| `tod_id`                     | Il codice identificativo dei termini di spedizione              | `intero`   |
| `tod_name`                   | Il nome dei termini di spedizione                               | `stringa`  |
| `tod_content`                | Il contenuto dei termini di spedizione                          | `stringa`  |
| `top_id`                     | Il codice identificativo dei termini di pagamento               | `intero`   |
| `top_name`                   | Il nome dei termini di pagamento                                | `stringa`  |
| `top_content`                | Il contenuto dei termini di pagamento                           | `stringa`  |
| `tos_id`                     | Il codice identificativo dei termini e condizioni               | `intero`   |
| `tos_name`                   | Il nome dei termini e condizioni                                | `stringa`  |
| `tos_content`                | Il contenuto dei termini e condizioni                           | `stringa`  |
| `order_id`                   | Il codice identificativo dell'ordine                            | `intero`   |
| `pricelist_id`               | Il codice identificativo del listino prezzi relativo all'ordine | `intero`   |
| `address_id`                 | Il codice identificativo dell'indirizzo di spedizione           | `intero`   |
| `cart_id`                    | Il codice identificativo del carrello                           | `intero`   |
| `notes`                      | Il contenuto delle note relative all'ordine                     | `stringa`  |
| `cache_price`                | Totale ordine                                                   | `intero`   |
| `cache_discount`             | Totale sconto                                                   | `intero`   |
| `cache_net`                  | Totale netto                                                    | `intero`   |
| `cache_vat`                  | Totale iva                                                      | `intero`   |
| `cache_gross`                | Totale lordo                                                    | `intero`   |
| `total_items`                | Il numero totale degli articoli inseriti nell'ordine            | `intero`   |
| `is_approved`                | Lo status di approvazione dell'ordine                           | `booleano` |
| `is_brand_approved`          | Lo status di approvazione dell'ordine da parte del distributore | `booleano` |
| `is_sent`                    | Lo status di spedizione dell'ordine                             | `booleano` |
| `is_delivered`               | Lo status di consegna dell'ordine                               | `booleano` |
| `is_paid`                    | Lo status di pagamento dell'ordine                              | `booleano` |
| `is_deleted`                 | Lo status di cancellazione dell'ordine                          | `booleano` |
| `date_created`               | Data di creazione ordine                                        | `datetime` |
| `date_approved`              | Data di approvazione ordine                                     | `datetime` |
| `date_brand_approved`        | Data di approvazione dell'ordine da parte del distributore      | `datetime` |
| `date_sent`                  | Data di spedizione ordine                                       | `datetime` |
| `date_delivered`             | Data di consegna ordine                                         | `datetime` |
| `date_paid`                  | Data di pagamento ordine                                        | `datetime` |
| `date_deleted`               | Data di cancellazione ordine                                    | `datetime` |
| `products_sku_list`          | La lista di tutti i prodotti inseriti nell'ordine               | `array`    |
| `products_versions_list`     | La lista di tutti gli assortimenti inseriti nell'ordine         | `array`    |
| `items`                      | La lista di tutti gli articoli inseriti nell'ordine             | `oggetto`  |
| `items`\[**`n`**\]           | L'identificativo `item_id` di un articolo                       | `intero`   |
| `products`                   | La lista di tutti gli articoli inseriti nell'ordine             | `oggetto`  |
| `products`\[**`n`**\]        | L'identificativo `product_id` di un prodotto                    | `intero`   |

___

# Metodo "create"

Il metodo <b>orders</b>-><b>create</b>() richiede i seguenti argomenti.

## Parametri

| Campo           | Obbligatorio | Descrizione                                           | Data Type |
|-----------------|--------------|-------------------------------------------------------|-----------|
| `store_id`      | sì           | Il codice identificativo del negozio                  | `intero`  |
| `supplier_id`   | sì           | Il codice identificativo del distributore             | `intero`  |
| `agent_id`      | facoltativo  | Il codice identificativo dell'agente                  | `intero`  |
| `buyer_id`      | sì           | Il codice identificativo del buyer                    | `intero`  |
| `collection_id` | sì           | Il codice identificativo della collezione             | `intero`  |
| `pricelist_id`  | sì           | Il codice identificativo del listino prezzi           | `intero`  |
| `address_id`    | sì           | Il codice identificativo dell'indirizzo di spedizione | `intero`  |
| `tos_id`        | sì           | Il codice identificativo dei termini e condizioni     | `intero`  |
| `top_id`        | sì           | Il codice identificativo dei termini di pagamento     | `intero`  |
| `tod_id`        | sì           | Il codice identificativo dei termini di spedizione    | `intero`  |
| `cart_id`       | facoltativo  | Il codice identificativo del carrello                 | `intero`  |
| `notes`         | facoltativo  | Il contenuto delle note relative all'ordine           | `stringa` |

## Risposta

La risposta è un nuovo oggetto `Orders` ([vedi struttura oggetto Orders](#metodo-get)).

___

# Metodo "update"

Il metodo <b>orders</b>-><b>update</b>() richiede i seguenti argomenti.

## Parametri

| Campo           | Obbligatorio | Descrizione                                           | Data Type |
|-----------------|--------------|-------------------------------------------------------|-----------|
| `buyer_id`      | sì           | Il codice identificativo del buyer                    | `intero`  |
| `address_id`    | sì           | Il codice identificativo dell'indirizzo di spedizione | `intero`  |
| `pricelist_id`  | sì           | Il codice identificativo del listino prezzi           | `intero`  |
| `tos_id`        | sì           | Il codice identificativo dei termini e condizioni     | `intero`  |
| `top_id`        | sì           | Il codice identificativo dei termini di pagamento     | `intero`  |
| `tod_id`        | sì           | Il codice identificativo dei termini di spedizione    | `intero`  |
| `notes`         | facoltativo  | Il contenuto delle note relative all'ordine           | `stringa` |

> ***Nota bene***  
> Una volta definiti non è possibile modificare `store_id`, `supplier_id`, `agent_id`, `collection_id` e `cart_id` di un ordine.

## Risposta

La risposta è un oggetto `Orders` aggiornato ([vedi struttura oggetto Orders](#metodo-get)).

___

# Metodo "setApproved"

Il metodo <b>orders</b>-><b>setApproved</b>() richiede i seguenti argomenti.

## Parametri

| Campo      | Obbligatorio | Descrizione                          | Data Type |
|------------|--------------|--------------------------------------|-----------|
| `order_id` | sì           | Il codice identificativo dell'ordine | `intero`  |

## Risposta

La risposta è un oggetto `Orders` impostato come approvato ([vedi struttura oggetto Orders](#metodo-get)).

___

# Metodo "delete"

Il metodo <b>orders</b>-><b>delete</b>() richiede i seguenti argomenti.

## Parametri

| Campo      | Obbligatorio | Descrizione                          | Data Type |
|------------|--------------|--------------------------------------|-----------|
| `order_id` | sì           | Il codice identificativo dell'ordine | `intero`  |

## Risposta

Nessuna risposta.

___

# Metodo "list"

Il metodo **orders**->**list**() richiede i seguenti argomenti.

## Parametri

| Campo                     | Obbligatorio | Descrizione                                                             | Data Type |
|---------------------------|--------------|-------------------------------------------------------------------------|-----------|
| `r`                       | facoltativo  | Il numero di risultati per pagina                                       | `intero`  |
| `p`                       | facoltativo  | La pagina da visualizzare                                               | `intero`  |
| `s`                       | facoltativo  | La chiave di ordinamento da usare                                       | `intero`  |
| `q`                       | facoltativo  | Un oggetto contenente chiavi di ricerca                                 | `oggetto` |
| `q`.`free`                | facoltativo  | Ricerca libera sui campi `buyer_name`, `buyer_name` e `collection_name` | `stringa` |
| `q`.`supplier_id`         | facoltativo  | Ricerca esatta sul campo `supplier_id`                                  | `stringa` |
| `q`.`supplier_buyer_code` | facoltativo  | Ricerca esatta sul campo `supplier_buyer_code`                          | `stringa` |
| `q`.`buyer_id`            | facoltativo  | Ricerca esatta sul campo `buyer_id`                                     | `stringa` |
| `q`.`store_id`            | facoltativo  | Ricerca esatta sul campo `store_id`                                     | `stringa` |
| `q`.`agent_id`            | facoltativo  | Ricerca esatta sul campo `agent_id`                                     | `stringa` |
| `q`.`brand_id`            | facoltativo  | Ricerca esatta sul campo `brand_id`                                     | `stringa` |
| `q`.`collection_id`       | facoltativo  | Ricerca esatta sul campo `collection_id`                                | `stringa` |
| `q`.`pricelist_id`        | facoltativo  | Ricerca esatta sul campo `pricelist_id`                                 | `stringa` |
| `q`.`tos_id`              | facoltativo  | Ricerca esatta sul campo `tos_id`                                       | `stringa` |
| `q`.`top_id`              | facoltativo  | Ricerca esatta sul campo `top_id`                                       | `stringa` |
| `q`.`tod_id`              | facoltativo  | Ricerca esatta sul campo `tod_id`                                       | `stringa` |
| `q`.`product_version_id`  | facoltativo  | Ricerca esatta sul campo `product_version_id`                           | `stringa` |
| `q`.`sku_id`              | facoltativo  | Ricerca esatta sul campo `sku_id`                                       | `stringa` |
| `q`.`date_from`           | facoltativo  | Ricerca esatta sul campo `date_from`                                    | `stringa` |
| `q`.`date_to`             | facoltativo  | Ricerca esatta sul campo `date_to`                                      | `stringa` |
| `q`.`is_approved`         | facoltativo  | Ricerca esatta sul campo `is_approved`                                  | `stringa` |
| `q`.`is_deleted`          | facoltativo  | Ricerca esatta sul campo `is_deleted`                                   | `stringa` |
| `q`.`status`              | facoltativo  | Ricerca esatta sul campo `status`                                       | `stringa` |

### Parametri Sorting

| Sorting Key         | Descrizione                              |
|---------------------|------------------------------------------|
| `order_id\|ASC`     | Ordina per codice ordine ascendente      |
| `order_id\|DES`     | Ordina per codice ordine discendente     |
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

La ricerca sugli **ordini** genera un dataset di oggetti di tipo **Order**.
Per visualizzare la struttura di un oggetto Order, guarda il risultato della funzione **orders**->**get**()
