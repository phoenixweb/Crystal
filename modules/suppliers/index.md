# Modulo Suppliers

## Oggetto :: Suppliers *(Distributore)*
L'oggetto Suppliers è quello che si definisce un **distributore**.  

___

## Metodi disponibili

I metodi che possono essere svolti sul modulo **Suppliers** sono:

- [get](#metodo-get)
___

# Metodo "get"

Il metodo <b>suppliers</b>-><b>get</b>() non ha bisogno di parametri in ingresso.

## Risposta

| Campo                    | Descrizione                                                        | Data Type  |
|--------------------------|--------------------------------------------------------------------|------------|
| `supplier_id`            | Il codice identificativo del distributore                          | `intero`   |
| `supplier_code`          | Il codice identificativo del distributore assegnato dal produttore | `stringa`  |
| `supplier_token`         | Il codice identificativo del distributore                          | `stringa`  |
| `entity_type`            | La tipologia societaria                                            | `intero`   |
| `entity_nationalitycode` | Il codice della nazionalità della società                          | `intero`   |
| `entity_name`            | Il nome della società                                              | `stringa`  |
| `org_name`               | La denominazione sociale                                           | `stringa`  |
| `org_vat_code`           | La partita IVA della società                                       | `stringa`  |
| `org_tax_code`           | Il codice fiscale della società                                    | `stringa`  |
| `vat_rate`               | L'aliquota IVA                                                     | `intero`   |
| `address_street`         | La via dell'indirizzo dichiarato                                   | `stringa`  |
| `address_street_number`  | Il numero civico dell'indirizzo dichiarato                         | `stringa`  |
| `address_city`           | La città nella quale ha sede la società                            | `stringa`  |
| `address_province`       | La provincia nella quale ha sede la società                        | `stringa`  |
| `address_postalcode`     | Il codice postale della città nella quale ha sede la società       | `stringa`  |
| `address_countrycode`    | Il codice nazionale nella quale ha sede la società                 | `stringa`  |
| `contact_email`          | L'email dichiarata dal distributore                                | `stringa`  |
| `contact_fax`            | Il numero fax dichiarato dal distributore                          | `stringa`  |
| `contact_mobile`         | Il numero di telefono cellulare dichiarato dal distributore        | `stringa`  |
| `contact_tel`            | Il numero di telefono fisso dichiarato dal distributore            | `stringa`  |
| `einvoice_type`          | La destinazione di fatturazione elettronica                        | `intero`   |
| `einvoice_pec`           | L'indirizzo PEC della fatturazione elettronica                     | `intero`   |
| `einvoice_code`          | Il codice identificativo di sette cifre dell'ufficio               | `stringa`  |
| `brands_list`            | La lista di tutti i brand trattati dal distributore                | `oggetto`  |
| `is_deleted`             | Lo status di cancellazione del distributore                        | `booleano` |
| `date_created`           | Data di creazione oggetto                                          | `datetime` |
| `date_updated`           | Data di aggiornamento oggetto                                      | `datetime` |
| `date_deleted`           | Data di cancellazione oggetto                                      | `datetime` |
