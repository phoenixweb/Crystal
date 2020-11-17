# Protocollo di comunicazione di Crystal

Crystal basa la comunicazione client-server sul protocollo JSON per lo scambio dei dati.

> **_Cos'è JSON_**
> JSON (JavaScript Object Notation), è un semplice formato per lo scambio di dati tra client e server che si basa sulla sintassi di JavaScript, da cui il nome, ma il cui formato è esclusivamente testuale.
Per maggiori informazioni sul formato JSON, consultare la guida ufficiale.

# Come inviare a Crystal
Crystal è dotato di un webservice accessibile alla tradizionale porta `80`.
Nella comunicazione con Crystal è necessario impostare correttamente username e password.
Per ottenere queste informazioni rimandiamo alla pagina specifica.

Per effettuare l'accesso al server è necessario consocere usare il corretto indirizzo host.

| Dato           | Come ottenerlo                  |
|----------------|---------------------------------|
| indirizzo host | comunicato dal supporto tecnico |
| username       | visualizzabile dalla scheda Bot |
| password       | richiedibile dalla scheda Bot   |

## Struttura comando di login
Per inviare il comando di login è necessario inviare un comando **POST** con:

```
POST /gate/supplier_bot.php HTTP/2

login=true
&username=$username
&password=$password
```

Il comando di Login rilascerà al client un cookie (SessionID) che dovrà essere usato in tutti i comandi successivi.


## Struttura dei comandi
Tutti i comandi si basano su una struttura di 3 variabili:

| Chiave  	| Valore                                     	|
|---------	|--------------------------------------------	|
| module  	| Modulo da interrogare                     	|
| action  	| Azione da compiere                         	|
| dataset 	| Set di dati descritti come un oggetto JSON 	|

Tutti i dati devono essere inviati via **POST** utilizzando la seguente struttura:

```
POST /gate/supplier_bot.php HTTP/2

action=$action
&module=$module
&data=$dataset
```

> Si consiglia sempre di effettuare un *URL encode* sui dati prima dell'invio

Di seguito in questa documentazione non si farà più riferimento a come costruire il protocollo di comunicazione ma ci si concentrerà invece su come costruire `dataset` validi.

Ad esempio per recuperare i dati di un determinato brand XXX è necessario effettuare il comando:

```
POST /gate/supplier_bot.php HTTP/2

action=brands
&module=get
&data={brand_id:XXX}
```

Tuttavia ci concentreremo solo sulla descrizione del dataset da inviare in formato prettyJSON.
L'esempio precedente verrà quindi descritto così:

Comando: **brands**->**get**  
Dataset:  
```
{
	brand_id : XXX
}
```


