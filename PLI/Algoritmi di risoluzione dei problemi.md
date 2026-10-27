Non esiste nessun algoritmo autonomo diretto per la risoluzione di un problema di PLI.
# Prepariamoci all'algoritmo di riduzione del gap
La risoluzione di un problema di questo genere però inizia con la definizione di **una valutazione superiore e una valutazione inferiore**.
Le valutazioni **superiore ed inferiore** devono essere:
- semplici 
- rapide
- reiterabili 
e **in miglioramento** (ossia atte all'avvicinarsi all'ottimo).
La differenza tra le due valutazioni prende il nome di **gap** e da vita all'**algoritmo di riduzione del gap**. 
Quest'algoritmo termina quando **il gap vale 0** oppure quando si è raggiunta la tolleranza desiderata([[#Stima di miglioramento]])
### Parliamo di limiti e valutazioni:
Il **limite inferiore** è rappresentato dalla **migliore** soluzione ammissibile che siamo riusciti a calcolare

==🔴Nota:== Quando andiamo a calcolare il **limite superiore** (ossia $V_s$ , da [[PLI/Definizioni#1) Problema di PL rilassato |Rilassato continuo]] ), la soluzione **non è ammissibile** $\implies$ E' necessario fornire una **stima**

#### Stima di miglioramento:
La stima di miglioramento equivale a $$\frac{V_s - V_I}{V_I}$$Dove $V_I$ rappresenta la soluzione ammissibile che abbiamo scelto come limite inferiore.

# Algoritmi greedy per il problema dello zaino ([[PLI/Problemi#Problema dello zaino|Problemi]])
## Algoritmo per lo zaino intero (1, semplice)
1) Calcolare il rendimento di **tutti i beni**
2) Ordinare i beni (secondo il loro rapporto) in ordine crescente
3) Prendere il bene di massimo rendimento
4) Saturare lo zaino con il bene di massimo rendimento
5) Ripetere finchè rimane spazio nello zaino
   
==🔵Nota:== E' possibile usare lo stesso ragionamento ma considerando l'ordine decrescente e il bene di minimo rendimento. 

## Algoritmo per lo zaino intero (2, completo)
1) Prendere il bene di massimo rendimento 
2) Metto la maggior quantità possibile dell'elemento di maggior rendimento
3) Calcolo lo spazio residuo 
4) Prendo il secondo bene di maggior rendimento
5) .. reitero fino al k-esimo elemento, che riempie lo zaino
   
==Nota:== Questo algoritmo è valido anche se avessimo il problema dello zaino binario , solo che al posto di indicare le occorrenze del bene ne indicheremmo solamente la presenza in relazione allo spazio residuo rimanente.

# Algoritmo di riduzione del GAP
L'algoritmo di riduzione del GAP risolve problemi del tipo $$\begin{cases} min~C^{T}x \\ Ax=b \\ x \geq 0 \\ x \in \mathbb{Z}^n\end{cases} oppure \begin{cases}
max~c^Tx \\Ax \geq b \\ x \in \mathbb{Z}^n
\end{cases}$$Talora avessimo problemi  di PLI in forme diverse è **assolutamente necessario riportarli in questa forma**.

## Il metodo dei piani di taglio di Gomory
Per ridurre il gap mi è necessario **aggiungere vincoli specifici** che riducano "la quota massima" (ossia $V_s$). 
Dal punto di vista **geometrico** si tratta di **tagliare il poliedro P**. 

**I vincoli in questione devono:**
- Essere accettabili $\to$ Non devono ridurre S ([[PLI/Altre cose importanti#Formato geometrico e regione ammissibile|S]]) 
- Devono ridurre il poliedro P

### Vediamo come si opera algebricamente... 
Dato un vertice di $$\begin{cases}
Ax=b~~~\overline{x}_{OTT}^{PL} \\ x>0
\end{cases}$$devo fare un piano di taglio per questo poliedro. 

Sia **B la base ottima**, la matrice A viene partizionata in 2 blocchi ([[PL/Altre cose importanti#I poliedri in forma duale standard|Forma duale standard)]] 
$$(A_{b} | A_{n}) \begin{pmatrix}
x_{B}\\x_{N}
\end{pmatrix} \\ \tilde{A} = A_{B}^{-1}A_{n}$$
Dove $\tilde{A}$ ha dimensione $n*(m-n)$ , $A_B^{-1} ~n*m$ e $A_N~n*(m-n)$.

Sia inoltre r un  **vertice di $x_{OTT}^{PL}$**
$$(x_{OTT}^{PL})_{r}~è~un~poliedro \\ a\in\mathbb{R} \\ \{a\} \triangleq a-[a]$$

Dove $\{a \}$ è la parte frazionaria ed è composta da **soli numeri positivi** mentre $[a]$ la parte intera ( che può essere arrotondata sia per eccesso che per difetto)

## In parole povere : 
1) Trovo l'ottimo del **rilassato continuo** ([[PLI/Definizioni#1) Problema di PL rilassato |Rilassato continuo]])
	Posso usare 3 metodi: 
	- Geometrico 
	- Vertice specifico 
	- Calcolo dei vertici $\to$ 3 di questi sono banali ( per trovare l'intersezione basta **invertire la matrice**)
2) Si porta il problema in **forma duale standard** ([[PL/Altre cose importanti#I poliedri in forma duale standard|Forma duale standard)]] 
3) Si sceglie una base e si calcolano **gli indici non di base**
4) Si applica (([[PLI/Teoremi#3) Teorema dei piani di taglio di Gomery|Il teorema dei piani di taglio di Gomery))]] 

## Risoluzione del problema T.S.P
E' necessario ricavare : 
- $V_i \to$ Che è la risoluzione del rilassato continuo $\to$ ==🔴 non funziona, perchè abbiamo un numero esponenziale di vincoli==
- $V_s \to$ Che è una qualsiasi soluzione ammissibile
- Il gap ( $V_s -V_i$ )
- Un passo dell'algoritmo di riduzione del gap

**Per ovviare al problema della $V_i$** possiamo escludere  il vincolo :$$\sum^n_{s_{j\in S^c}} x_{{ij}}\geq 1~\forall S \subseteq N$$ togliendo così $2^n$ vincoli dal numero di vincoli totale. 
E al contrario di come ci si potrebbe aspettare , **la $V_i$ si discosta pochissimo dalla soluzione ottima T.S.P**. 

## L'algoritmo delle toppe 
Per creare con certezza un **ciclo hamiltoniano** (in un problema di T.S.P asimmetrico) usiamo il **metodo delle toppe** che consiste nell' **unire cicli disgiunti**. 
$$(i,j)~(k,l) \to Sono~le~due~coppie~originali(cicli~disgiunti)\\(i,l)~(k,j) \to Sono~le~coppie~con~indice~scambiato \implies \\abbiamo~collegato~due~cicli~disgiunti~del~grafo $$
Più sono i cicli disgiunti , più è necessario svolgere passi con questa procedura : 
Possiamo avere fino ad un numero massimo di $n^2$ arhci


## T.S.P simmetrico 

Otteniamo $V_i$ per eliminazione e $V_s$ calcolando la soluzione ammissibile **migliore**. 

Per trovare la $V_s$ è necessario considerare **tutti gli archi a costo minore** che permettono **l'interconnessione tra tutti i nodi** , sommandoli otteniamo la $V_s$ . 

Siccome gli archi non sono orientati, hanno **grado 2** .

Per il fatto che i vincoli di connessione sono di numero esponenziale, non posso risolvere il problema rilassato continuo $\to$ devo e posso eliminare **vincoli di grado.**

(Ad esempio leviamo **tutti i vincoli di grado ad esclusione di quelli del grado 1**)

Così facendo costruiamo l'albero di **copertura mimina** che esclude **il nodo equivalente ai vincoli di grado scelto** $\to$ Questo è il **k-albero**

# Il Branch and Bound
Il Branch and Bound è un algoritmo di riduzione del gap che si applica a problemi del tipo : $$\begin{cases}
min~c^Tx \\ Ax \leq b\\
x \in\{0,1\} \to deve~avere~una~V_i~e~una~V_s~\forall (P)
\end{cases} \to Ottimizzazione~PLI$$Ed è basato completamente sull'**albero dell'enumerazione totale**.
L'idea è quella di **calcolare** $\forall P_{ij}~una~V_{i}$ , ad ogni passo dell'esplorazione dell'albero (che avviene in profondità, orizzontalmente). 


**Regola:** Calcolo $V_{I}(P_{ij})$ attraverso il k-albero (man mano che aggiungiamo vincoli, il **k-albero sale**) $\implies$ Se $V_I(P_{ij})\geq V_{s} (P) \implies taglio$
Per aver il $V_s$ migliore, ogni volta che l'idea è soddisfatta **posso tagliare il ramo che la genera**!


## Le regole di taglio 
1) $P_{ij}=\emptyset$ ossia **vedere se il poliedro si è svuotato**
2) $V_I(P_{ij})\geq V_{s}(P)$ 
3) $V_{I}(P_{ij})<V_{s} (P)$ $\to$ In questo caso ad essere tagliato non è $V_I$ , piuttosto sostituisce il $V_s$ trovato $\implies V_{s}(P)=V_{I}(P_{ij})$

# Il Branch and Bound per problemi di massimo

Come nel caso del [[#Il Branch and Bound| Branch and bound "classico"]] , anche qui abbiamo la necessita di determinare un valore $V_I$ e un valore $V_s$ e si ottengono nei seguenti modi: 

- $V_I$ : Calcolando la **miglior soluzione ammissibile** 
- $V_s$ : E' ottenibile attraverso l'eliminazione dei vincoli.

==Nota:== Solitamente la $V_s$ viene trovata attraverso la risoluzione del **rilassato continuo** , ma ciò non è possibile per i problemi di [[PLI/Problemi#2) Il problema del T.S.P(S) (Travelling Sailsman Problem)|T.S.P]].

Trattata la fase di "Bound", ossia di definizione dei limiti dell'algoritmo , è necessario trattare quella di "Branch", ossia 
## Le regole di taglio :
1) $p_{ij}=\emptyset \to$ Perchè dopo aver raggiunto un determinato livello non sarà più possibile trovare soluzioni ammissibili $\to$ C'è un vincolo che è stato **definitivamente** violato 
   Insomma non è possibile ==🔴disinstanziare variabili==
2) $V_s(P_{ij})\leq V_{I(P)}$
3) $V_s(P_{ij})>V_{I}(P) \to$ Ossia la **soluzione ottima del** [[PLI/Definizioni#1) Problema di PL rilassato|Rilassato continuo]]

==Nota:== E' necessario calcolare $V_s$ ad ogni passo , permettendo così una "riduzione" del valore del massimo


# Risoluzione del [[PLI/Problemi#3) Il problema di copertura(di costo minimo) o problema di covering|problema di copertura]]
Il problema di copertura, così come il resto dei problemi di PLI si risolve attraverso la determinazione di una valutazione inferiore ($V_I$) e di una valutazione inferiore ($V_s$), procedendo poi con l'applicazione del [[#Il Branch and Bound| Branch and Bound]] .

==🟡Nota:== Esisterebbe un algoritmo migliore del Branch and Bound , che sarebbe il Branch and cut, che mescola la metodologia del Branch and Bound con quella dei piani di taglio di Gomory.

In questo caso abbiamo che :$$V_{I}=Rilassato~continuo*\\V _{S}=Soluzione~ammissibile~del~problema~P$$
$*$ Il rilassato continuo in questo caso corrisponde al "linprog" del problema.
## Calcolo della $V_s$ (Generico)
1) Contare il numero di 1 presente per ogni colonna 
2) Considerare ed eliminare la colonna con il maggior numero di 1 (dopo averne posto la corrispettiva variabile a 1).
3) Cancellare le righe che hanno 1 in quella determinata colonna

==Nota:== E' possibile arricchire l'algoritmo attraverso l'aggiunta di costi e regole di riduzione.


## L'algoritmo di Chvatal  (Calcolo della $V_s$)
E' l'algoritmo "più **greedy**" in assoluto e sfrutta i rendimenti. 
1) Costruire il vettore dei rendimenti, che corrisponde a :$$r=(\frac{c_{i}}{\#_{1}i}~o\frac{\#_{1}i}{c_{i}} )$$
   Dove $\#_{i}$ è il **numero relativo alla colonna i** .
   ==Nota:== Le due notazioni scritte sopra sono totalmente indifferenti, tranne per il fatto che **è necessario considerare il massimo** se si scegliesse la prima, e il **minimo** se si scegliesse la seconda.

# Risoluzione dei problemi di tipo [[PLI/Problemi#4) Il problema del "Bin Packing"|Bin packin]] 
$V_I=Soluzione~ottima~del~rilassato~continuo \\ V_{s}=soluzione~ammissibile$

Ma come trovo la soluzione ammissibile? 
Ho a disposizione 3 metodi: 
1) **Next fit decreasing:**
	1) Ordinare i valori in ordine **decrescente**
	2) Aprire un primo "bin" e inserire il primo oggetto 
	3) Se il valore del secondo oggetto sfora il limite del bin, allora è necessario aprire un secondo bin, altrimenti si inserisce l'oggetto nel primo bin.
	4) Ripetere fin quando non si termina di collocare gli oggetti.
2) **First bin decreasing:** 
	   1) Ordinare i valori in ordine **decrescente**
	2) Ogni volta che si considera un oggetto inserirlo nel **primo bin possibile** , talora non potesse accadere è necessario aggiungere **un nuovo bin**.
	==Nota:== Questo metodo permette **di avere uno sfido(ossia spazio libero rimanente) più equilibrato**.
3) **Best fit decreasing:**
	   1) Ordinare i valori in ordine **decrescente**.
	   2) Ogni volta che si considera un oggetto, inseriro nel **bin che permette di lasciare il minor sfrido possibile**. 
	==Nota:== In questo modo **riempiamo il più possibile i bin**.

E invece la $V_I$ come si calcola? 

La $V_I$ si calcola attraverso il rapporto tra **la sommatoria di tutti gli oggetti** e **la capacità dei bin** ossia:$$\frac{\sum_{i=i}^{n} w_{i}}{C} $$Si considera l'arrotondamento **per eccesso** al fine di definire **il valore ottimo del rilassato continuo**. 
