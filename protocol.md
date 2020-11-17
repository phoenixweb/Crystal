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
Per inviare il comando di login è necessario inviare un comando **POST** con i seguenti dati:

```
login=true
&username=$username
&password=$password
```

## Struttura dei comandi
Tutti i comandi si basano su una struttura di 3 variabili:

| Chiave  	| Valore                                     	|
|---------	|--------------------------------------------	|
| module  	| Modulo/componente di                      	|
| action  	| Azione da compiere                         	|
| dataset 	| Set di dati descritti come un oggetto JSON 	|

Tutti i dati devono essere inviati via **POST** utilizzando la seguente struttura.

```
action=$action
&module=$module
&data=$dataset
```

> Si consiglia sempre di effettuare un URLencode sui dati prima dell'invio
