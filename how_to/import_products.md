# Come sincronizzare il Catalogo Prodotti
In questo tutorial affronteremo come fare ad importare i prodotti dentro a Crystal.
Per creare correttamente una referenza sarà necessario creare tutti gli oggetti
di seguito descritti in questo diagramma:

```mermaid
graph LR;
 A[Brand]:::brand;
 B[Modello]:::product;
 C[Cartella Colore]:::attribute;
 D[Cartella Materiale]:::attribute;
 E[Articolo]:::product;
 F[Cartella Taglie]:::attribute;
 G[Referenza SKU]:::product;
 A-->|brand_id|B;
 A-->|brand_id|C;
 A-->|brand_id|D;
 B-->|product_id|E;
 C-->|color_id|E;
 D-->|fabric_id|E;
 A-->|brand_id|F;
 E-->|product_version_id|G;
 F-->|size_id|G;
 classDef brand fill:#C00000,color:#FFF;
 classDef attribute fill:#00B050,color:#FFF;
 classDef product fill:#0070C0,color:#FFF;
```

I passaggi saranno i seguenti:
- sincronizzare *Modelli*
- sincronizzare *Cartella Colori*
- sincronizzare *Cartella Materiali*
- sincronizzare *Articoli*
- sincronizzare *Cartella Taglie*
- sincronizzare *Referenze SKU*

## Sincronizzare Modelli

Per sincronizzare i *Modelli* raccomandiamo di usare il seguente flusso:

```mermaid
graph TD;
	A[/`brand_id`/]:::input;
	B[/`product_code`/]:::input;
	C[Ricerca su Modelli]:::action;
	D{{Verifico se esiste il Modello}}:::logic;
	E{{Verifico se il Modello è aggiornato}}:::logic;
	F[Creo un nuovo Modello]:::action;
	G[Aggiorno il Modello]:::action;
	H{{Estraggo il `product_id`}}:::logic;
	A-->C;
	B-->C;
	C-->D;
	D-->|Esiste|E;
	E-->|Non è aggiornato|G;
	E-->|E' aggiornato|H;
	G-->H;
	D-->|Non esiste|F;
	F-->H;
	classDef input fill:#7F8C8D,color:#FFF;
	classDef action fill:#0070C0,color:#FFF;
	classDef logic fill:#D10069,color:#FFF;
```

Iniziamo verificando se il modello sia già presente in archivio.
Per farlo possiamo effettuare una ricerca esatta
sul campo `product_code` (Il codice identificativo usato dal produttore) e quindi
recuperare il codice `product_id` usato da Crystal.

> **Nota bene**  
> In caso si debba effettuare l'importazione di un numero importante di referenze
> potrebbe essere una buona idea scaricare l'intero database *Modelli* per usarlo
> come cache locale durante il processo di creazione

Con il seguente comando effettueremo una ricerca sul database per product_code.
Comando: **products**->**list**  
Richiesta:  
```json
{
	q : {
		"brand_id"		: "1",
		"product_code"	: "99999",
	}
}
```

Ipotizziamo che l'oggetto non sia stato creato.
In questo caso riceveremo una risposta simile alla seguente:

```json
{
	nav : {
		"page" 			: 1,
		"tot_pages" 	: 0,
		"results"		: 10,
		"tot_results" 	: 0,
		"orderBy"		: "product_id|DES" 
	},
	dataset: []
}
```
A questo punto possiamo procedere alla creazione del nuovo Modello.
Inviamo il seguente comando.  
Comando: **products**->**create**  
Richiesta:  
```json
{
	"brand_id" : 1,
    "product_name"   : "Modello Alpha",
    "product_code"   : "99999",
    "product_type"   : "shoes",
	"product_gender" : "man",
	"product_target" : "adult"
	"is_visible"     : 1
}
```
Risposta:  
```json
{
	"brand_id"		  : 1,
	"brand_name"	  : "My Brand",
    "product_id"      : 1,
    "product_name"    : "Modello Alpha",
    "product_code"    : "99999",
    "product_type"    : "shoes",
	"product_gender"  : "man",
	"product_target"  : "adult",
	"lang_translated" : null,
	"version_count"   : 0,
	"skus_count"      : 0,
	"is_visible"      : 1,
	"date_created"    : "2020-11-11 10:52:53"
}
```
_____________________________________________________________________________________________
## Sincronizzazione dei Colori

Per sincronizzare i *Colori* raccomandiamo di usare il seguente flusso di processo.

```mermaid
graph TD;
	A[/`brand_id`/]:::input;
	B[/`color_code`/]:::input;
	C[Ricerca su Colori]:::action;
	D{{Verifico se esiste il Colore}}:::logic;
	E{{Verifico se il Colore è aggiornato}}:::logic;
	F[Creo un nuovo Colore]:::action;
	G[Aggiorno il Colore]:::action;
	H{{Estraggo il `color_id`}}:::logic;
	A-->C;
	B-->C;
	C-->D;
	D-->|Esiste|E;
	E-->|Non è aggiornato|G;
	E-->|E' aggiornato|H;
	G-->H;
	D-->|Non esiste|F;
	F-->H;
	classDef input fill:#7F8C8D,color:#FFF;
	classDef action fill:#0070C0,color:#FFF;
	classDef logic fill:#D10069,color:#FFF;
```

Iniziamo verificando se il colore sia già presente in archivio.
Per farlo possiamo effettuare una ricerca esatta
sul campo `color_code` (Il codice identificativo usato dal produttore) e quindi
recuperare il codice `color_id` usato da Crystal.

> **Nota bene**  
> In caso si debba effettuare l'importazione di un numero importante di referenze
> potrebbe essere una buona idea scaricare l'intero database *Colori* per usarlo
> come cache locale durante il processo di creazione

Con il seguente comando effettueremo una ricerca sul database per product_code.
Comando: **productsColors**->**list**  
Richiesta:  
```json
{
	q : {
		"color_code" : "AAC123"
	}
}
```

Ipotizziamo che l'oggetto non sia stato creato.
In questo caso riceveremo una risposta simile alla seguente:

```json
{
	nav : {
		"page" 			: 1,
		"tot_pages" 	: 0,
		"results"		: 10,
		"tot_results" 	: 0,
		"orderBy"		: "color_id|DES" 
	},
	dataset: []
}
```
A questo punto possiamo procedere alla creazione del nuovo Colore.
Inviamo il seguente comando.  
Comando: **productsColors**->**create**  
Richiesta:  
```json
{
	"brand_id" 		: 1,
    "color_code"   	: "Gee3",
    "color_name"   	: "Grigio",
	"color_rgb" 	: "#626b5b"
}
```
Risposta:  
```json
{
	"brand_id"		: 1,
	"brand_name"	: "My Brand",
    "color_id"      : 1,
    "color_code"    : "Gee3",
    "color_name"    : "Grigio",
    "color_rgb"		: "#626b5b",
	"is_deleted"	: 0,
	"date_created"  : 2020-11-26 12:18:02,
	"date_deleted"	: null
}
```
_____________________________________________________________________________________________
## Sincronizzazione dei Materiali

Per sincronizzare i *Materiali* raccomandiamo di usare il seguente flusso di processo.

```mermaid
graph TD;
	A[/`brand_id`/]:::input;
	B[/`fabric_code`/]:::input;
	C[Ricerca sui Materiali]:::action;
	D{{Verifico se esiste il Materiale}}:::logic;
	E{{Verifico se il Materiale è aggiornato}}:::logic;
	F[Creo un nuovo Materiale]:::action;
	G[Aggiorno il Materiale]:::action;
	H{{Estraggo il `fabric_id`}}:::logic;
	A-->C;
	B-->C;
	C-->D;
	D-->|Esiste|E;
	E-->|Non è aggiornato|G;
	E-->|E' aggiornato|H;
	G-->H;
	D-->|Non esiste|F;
	F-->H;
	classDef input fill:#7F8C8D,color:#FFF;
	classDef action fill:#0070C0,color:#FFF;
	classDef logic fill:#D10069,color:#FFF;
```

Iniziamo verificando se il materiale sia già presente in archivio.
Per farlo possiamo effettuare una ricerca esatta
sul campo `fabric_code` (Il codice identificativo usato dal produttore) e quindi
recuperare il codice `fabric_id` usato da Crystal.

> **Nota bene**  
> In caso si debba effettuare l'importazione di un numero importante di referenze
> potrebbe essere una buona idea scaricare l'intero database *Materiali* per usarlo
> come cache locale durante il processo di creazione

Con il seguente comando effettueremo una ricerca sul database per fabric_code.
Comando: **productsFabrics**->**list**  
Richiesta:  
```json
{
	q : {
		"fabric_code" : "L4n4"
	}
}
```

Ipotizziamo che l'oggetto non sia stato creato.
In questo caso riceveremo una risposta simile alla seguente:

```json
{
	nav : {
		"page" 			: 1,
		"tot_pages" 	: 0,
		"results"		: 10,
		"tot_results" 	: 0,
		"orderBy"		: "fabric_id|DES" 
	},
	dataset: []
}
```
A questo punto possiamo procedere alla creazione del nuovo Materiale.
Inviamo il seguente comando.  
Comando: **productsFabrics**->**create**  
Richiesta:  
```json
{
	"brand_id" 				: 1,
    "fabric_code"   		: "L4n4",
    "fabric_name"   		: "LanaGrezza",
	"fabric_description" 	: "Lana grezza ma morbidissima"
}
```
Risposta:  
```json
{
	"brand_id"			: 1,
	"brand_name"		: "My Brand",
    "fabric_id"      	: 2,
    "fabric_code"    	: "L4n4",
    "fabric_name"    	: "LanaGrezza",
	"fabric_description": "Lana grezza ma morbidissima",
	"is_deleted"		: 0,
	"date_created"  	: 2020-11-26 12:18:02,
	"date_deleted"		: null,
	"date_updated" 		: null
}
```
_____________________________________________________________________________________________
## Sincronizzazione degli Articoli

Per sincronizzare gli *Articoli* raccomandiamo di usare il seguente flusso di processo.

```mermaid
graph TD;
	A[/`product_id`/]:::input;
	B[/`color_id`/]:::input;
	C[/`fabric_id`/]:::input;
	D[Ricerca sui Articoli]:::action;
	E{{Verifico se esiste l'Articolo}}:::logic;
	F{{Verifico se l'Articolo è aggiornato}}:::logic;
	G[Creo un nuovo Articolo]:::action;
	H[Aggiorno l'Articolo]:::action;
	I{{Estraggo il `product_version_id`}}:::logic;
	A-->D;
	B-->D;
	C-->D;
	D-->E;
	E-->|Esiste|F;
	F-->|Non è aggiornato|H;
	F-->|E' aggiornato|I;
	H-->I;
	E-->|Non esiste|G;
	G-->I;
	classDef input fill:#7F8C8D,color:#FFF;
	classDef action fill:#0070C0,color:#FFF;
	classDef logic fill:#D10069,color:#FFF;
```

Iniziamo verificando se l'articolo sia già presente in archivio.
Per farlo possiamo effettuare una ricerca esatta
sui campi `product_id`, `color_id`, `fabric_id` (che ci siamo salvati in precedenza) e quindi
recuperare il codice `product_version_id` usato da Crystal.

> **Nota bene**  
> In caso si debba effettuare l'importazione di un numero importante di referenze
> potrebbe essere una buona idea scaricare l'intero database *Articoli* per usarlo
> come cache locale durante il processo di creazione

Con il seguente comando effettueremo una ricerca sul database per sapere se esiste già la variante di quell'articolo.
Comando: **productsVersions**->**list**  
Richiesta:  
```json
{
	q : {
		"product_id"	: 1,
		"color_id" 		: 1,
		"fabric_id" 	: 2
	}
}
```

Ipotizziamo che l'oggetto non sia stato creato.
In questo caso riceveremo una risposta simile alla seguente:

```json
{
	nav : {
		"page" 			: 1,
		"tot_pages" 	: 0,
		"results"		: 10,
		"tot_results" 	: 0,
		"orderBy"		: "product_version_id|DES" 
	},
	dataset: []
}
```
A questo punto possiamo procedere alla creazione del nuovo Articolo.
Inviamo il seguente comando.  
Comando: **productsVersions**->**create**  
Richiesta:  
```json
{
	"product_id"	: 1,
	"color_id" 		: 1,
	"fabric_id" 	: 2
}
```
Risposta:  
```json
{
	"brand_id" 				: 1,
	"brand_name" 			: "My Brand",
	"color_id" 				: 1,
	"color_code" 			: "Gee3",
    "color_name" 			: "Grigio",
    "color_rgb" 			: "#626b5b",
    "fabric_id" 			: 2,
	"fabric_code" 			: "L4n4",
    "fabric_name" 			: "LanaGrezza",
	"product_id" 			: 1,
	"product_name"			: "Modello Alpha",
    "product_name_full" 	: "Modello Alpha - LanaGrezza - Grigio",
    "product_type" 			: "shoes",
    "product_target" 		: "adult",
	"product_code" 			: "99999",
	"product_gender" 		: "man",
    "product_version_hash" 	: "849117eb849d17c29d2b4aa723e41560",
	"product_version_id"	: 1,
	"images_list" 			: null,
    "sku_list"				: null,
    "is_product_visible"	: 1,
    "is_brand_deleted" 		: 0,
    "is_product_deleted"	: 0,
    "is_fabric_deleted"		: 0,
    "is_color_deleted" 		: 0,
    "is_version_deleted"	: 0,
	"date_created"			: "2020-11-26 12:46:01",
	"date_deleted" 			: null,
    "date_dismissed" 		: null,
}
```
_____________________________________________________________________________________________
## Sincronizzazione delle Taglie

Per importare una taglia è necessario seguire il seguente flusso:

```mermaid
graph TD;
	A[/`brand_id`/]:::input;
	B[/`size_type`/]:::input;
	C[/`size_id`/]:::input;
	D[Ricerca sulle Taglie]:::action;
	E{{Verifico se esiste la Taglia}}:::logic;
	G[Creo una nuova Taglia]:::action;
	I{{Estraggo il `size_id`}}:::logic;
	A-->D;
	B-->D;
	C-->D;
	D-->E;
	E-->|Esiste|I;
	E-->|Non esiste|G;
	G-->I;
	classDef input fill:#7F8C8D,color:#FFF;
	classDef action fill:#0070C0,color:#FFF;
	classDef logic fill:#D10069,color:#FFF;
```

Iniziamo verificando se la taglia sia già presente in archivio.
Per farlo possiamo effettuare una ricerca esatta
sui campi `brand_id`, `size_name`, `size_type` e quindi
recuperare il codice `size_id` usato da Crystal.

> **Nota bene**  
> In caso si debba effettuare l'importazione di un numero importante di referenze
> potrebbe essere una buona idea scaricare l'intero database *Taglie* per usarlo
> come cache locale durante il processo di creazione

Con il seguente comando effettueremo una ricerca sul database per sapere se esiste già la taglia.
Comando: **productsSizes**->**list**  
Richiesta:  
```json
{
	q : {
		"brand_id"	: 1,
		"size_name" : "27XL",
		"size_type" : "Taglie forti"
	}
}
```

Ipotizziamo che l'oggetto non sia stato creato.
In questo caso riceveremo una risposta simile alla seguente:

```json
{
	nav : {
		"page" 			: 1,
		"tot_pages" 	: 0,
		"results"		: 10,
		"tot_results" 	: 0,
		"orderBy"		: "size_id|DES" 
	},
	dataset: []
}
```
A questo punto possiamo procedere alla creazione della nuova Taglia.
Inviamo il seguente comando.  
Comando: **productsSizes**->**create**  
Richiesta:  
```json
{
	"brand_id"	: 1,
	"size_type" : "Taglie forti",
	"size_name" : "27XL"
}
```
Risposta:  
```json
{
	"brand_id" 				: 1,
	"brand_name" 			: "My Brand",
	"position" 				: 0,
	"size_id" 				: 2,
	"size_hash"				: "Taglie forti@27XL",
	"size_name" 			: "27XL",
	"size_type" 			: "Taglie forti"
	"is_deleted"			: 0,
	"date_created"			: "2020-11-26 12:46:01",
	"date_deleted" 			: null,
}
```


_____________________________________________________________________________________________
## Sincronizzazione Referenze SKU

L'ultimo passo per la sincronizzazione del catalogo è la sincronizzazione delle *Referenze*, ossia delle SKU
\(<i>**S**tock **K**eeping **U**nit</i>\). Useremo le variabili recuperate dal processo di sincronizzazione
degli **Articoli** *ProductsVersions* e della **Cartella Taglie** *ProductsSizes*.


```mermaid
graph TD;
	A[/"`product_version_id`"/]:::continue;
	B[/"`size_id`"/]:::continue;
	C["Ricerca sulle SKUs"]:::action;
	D{{Verifico se esiste la SKU}}:::logic;
	E{{Verifico se la SKU è aggiornata}}:::logic;
	F[Creo la SKU]:::action;
	G[Aggiorno la SKU]:::action;
	A-->C;
	B-->C;
	C-->D;
	D-->|Esiste|E;
	D-->|Non esiste|F;
	E-->|Non è aggiornata|G;
	classDef continue fill:#7F8C8D,color:#FFF;
	classDef action fill:#0070C0,color:#FFF;
	classDef logic fill:#D10069,color:#FFF;
```

Iniziamo verificando se la referenza sia già presente in archivio.
Per farlo possiamo effettuare una ricerca esatta
sui campi `product_version_id`, `size_id`.

Con il seguente comando effettueremo una ricerca sul database per sapere se esiste già la taglia.
Comando: **productsSKU**->**list**  
Richiesta:  
```json
{
	q : {
		"size_id"				: 1,
		"product_version_id"	: 1
	}
}
```

Ipotizziamo che l'oggetto non sia stato creato.
In questo caso riceveremo una risposta simile alla seguente:

```json
{
	nav : {
		"page" 			: 1,
		"tot_pages" 	: 0,
		"results"		: 10,
		"tot_results" 	: 0,
		"orderBy"		: "sku_id|DES" 
	},
	dataset: []
}
```
A questo punto possiamo procedere alla creazione della nuova Referenza.
Inviamo il seguente comando.  
Comando: **productsSKU**->**create**  
Richiesta:  
```json
{
	"product_version_id"	: 1,
	"size_id"				: 2,
	"sku_code"				: "XX00001",
}
```
Risposta:  
```json
{
	"sku_id"				: 1,
	"sku_code"				: "XX00001",
	"brand_name"			: "My Brand",
	"brand_id"				: 1,
	"product_id" 			: 1,
	"product_name"			: "Modello Alpha",
    "product_name_full" 	: "Modello Alpha - LanaGrezza - Grigio",
	"product_type" 			: "shoes",
	"product_code" 			: "99999",
	"product_gender" 		: "man",
	"product_target" 		: "adult",
	"product_version_id"	: 1,
	"product_version_hash" 	: "849117eb849d17c29d2b4aa723e41560",
	"color_id" 				: 1,
	"color_name" 			: "Grigio",
	"color_code" 			: "Gee3",
	"color_rgb" 			: "#626b5b",
	"fabric_id" 			: 2,
	"fabric_name" 			: "LanaGrezza",
	"fabric_code" 			: "L4n4",
	"size_id"				: "110",
	"size_type"				: "Taglie Internazionali",
	"size_name"				: "XXL",
	"is_deleted"			: 1,
	"is_product_visible"	: 1,
    "is_brand_deleted" 		: 0,
    "is_product_deleted"	: 0,
    "is_fabric_deleted"		: 0,
    "is_color_deleted" 		: 0,
    "is_version_deleted"	: 0,
	"is_sku_deleted"		: 1,
	"date_created"			: "2020-11-26 12:46:01",
	"date_deleted" 			: null
  }
```


    
