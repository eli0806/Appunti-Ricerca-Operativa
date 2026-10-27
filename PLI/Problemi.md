# 1) Problema dello zaino 
E' possibile trovare il problema dello zaino in 4 versioni:

## **Zaino intero**: Nello zaino intero è possibile reinserire più volte un elemento dello stesso tipo.
$$v^T*\tilde{x}~con~\tilde{x}~ammissibile=V_i \leq\begin{cases} max~v^T \\ P^T z \leq P \\ x \in \mathbb{Z}^n_+ \end{cases} \leq\begin{cases} max~v^Tx~~~~~\to Pl \to V_s \\ P^T\leq P \\ x \geq 0 \end{cases}$$
## **Zaino binario:** Al contrario del caso precedente, per ogni elemento è possibile una e una sola occorrenza. 
$$v^T\tilde{x} ~ammissibile=V_I \leq \begin{cases} max~v^Tx \\ P^Tx \leq P \\ x \in \{0,1\}^n \end{cases} \leq \begin{cases} max~C^Tx \\ P^Tx \in P \end{cases}=V_s$$

# 2) Il problema del T.S.P(S) (Travelling Sailsman Problem)
Questo problema consiste nella ricerca del **ciclo hamiltoniano più breve** ([[PLI/Definizioni#5) Ciclo hamiltoniano|Ciclo hamiltoniano]]) all'interno di un grafo **connesso** (ossia in un grafo dove **tutti i nodi sono collegati**).

Il collegamento tra nodi è descritto da **una tabella dei costi**.

Se provassimo a risolverlo attraverso le permutazioni avremmo un numero (n-1)! di tentativi

## Asimmetrico (caso migliore)
I problemi di T.S.P asimmetrico hanno la seguente forma:
$$\begin{cases}min~c^T \\ \sum^n_{i=1} x_{{ij}}=1~\forall j=1,\dots,n \\ \sum^n_{j=1} x_{{ij}}=1~\forall i=1,\dots,n \\ \sum^n_{s_{j\in S^c}} x_{{ij}}\geq 1~\forall S \subseteq N \\ x_{ij} \in \{0,1\}\end{cases}$$

## Simmetrico
Poniamo $$x_{ij}~~i<j$$
I problemi di T.S.P simmetrico hanno la seguente forma:$$\begin{cases}
min~c^Tx \\ \sum_{h<i} x_{hi} + \sum_{i<k} x_{ik} =2 \to Fissato~i \\\dots 
vincoli~di~connessione\\ x \in\{0,1\}\end{cases}$$
La specifica in questo caso viene data dal vincolo:

$$\sum_{h<i} x_{hi} + \sum_{i<k} x_{ik} \to Fissato~ i $$

# 3) Il problema di copertura(di costo minimo) o problema di covering
I problemi di copertura hanno la seguente forma : 
$$\begin{cases}
min~c^Tx \\ Ax\geq 1 \to Sono~tutti~i~termini~noti~\to\mathbb{R}^m \\
 x_{i}\in\{0,1\}~~\forall_{i}
\end{cases}$$
Possono esistere a sua volta anche dei casi particolari come quello del **servizio di necessaria attivazione**, dove è necessario considerare nei vincoli anche **la soglia di servizio**(come ad esempio il tempo massimo possibile per raggiungere un luogo, o per l'erogazione di un servizio).
Per facilitare la risoluzione è possibile ridurre il problema attraverso delle [[#Regole di riduzione|regole di riduzione]].

## Regole di riduzione del problema di copertura
Le regole di riduzione servono a **diminuire la grandezza del problema** per facilitare gli algoritmi di riduzione del GAP come il [[PLI/Algoritmi di risoluzione dei problemi#Il Branch and Bound|Branch and Bound]].

1) Se una riga fosse composta da soli 0 $\implies \emptyset \to$ Il problema è finito
2) Se una riga fosse composta da soli 1 $\implies$ Si elimina la riga
3) Se una colonna fosse composta da soli 0 $\implies$ Si elimina la colonna
4) Se una colonna fosse composta da soli 1 $\implies$ 
	1) Se osserviamo "il minor numero", questa colonna **rappresenta l'ottimo**
	2) Se osserviamo i costi , questa colonna "si lascia stare"
5) Se una riga dovesse contenere un singolo 1 ($x_{i})\implies$ Cancello **la riga** e **la colonna** che lo contengono.
   Elimino inoltre **tutte le righe che hanno 1 nella colonna i**.
   ==🔵Osservazione:== Se trovassi una colonna con un singolo 1$\implies$ Non faccio nulla $\implies$ La lascio
6) $$\begin{cases}
min~c^Tx \\ Ax\geq 1 \\
 x_{i}\in\{0,1\}~~\forall_{i}
\end{cases}$$
Dove i termini noti b sono **tutti -1**.

# 4) Il problema del "Bin Packing"

Il problema del Bin Packing consiste nell'avere n valori da inserire in un numero di scatole, delimitate da una capienza massima C. 
E' necessario **portare TUTTI i valori** $\implies$ E' necessario che si abbiano **più contenitori**.

**Quali sono le variabili?** 
Le variabili sono **il numero di contenitori $y_i$ $$y_{i}=\begin{cases}
0 \\1
\end{cases}$$** e l'**associazione degli oggetti ai vari contenitori**. $$x_{ij}=\begin{cases} 0 \\ 1\end{cases}$$Dove i rappresenta **l'indice del contenitore** e j **l'indice dell'oggetto** , i valori 0 e 1 **identificano se il contenitore i contiene o no l'oggetto j**

Il modello che lo descrive ha la seguente forma:$$\begin{cases}
		min~\sum_{i=1}^n y_i\\\sum_{i=1}^n  x_{ij}=~~\forall j=\{1 \dots n\}\to Vincoli~di~semi-assegnamento \\
		\sum_{j=1}^n w_jx_{ij}\leq C*y_i~\forall i \in\{1 \dots n\} \to Vincoli~di~peso \to Lega~le~variabili~in~x_{ij}~a~quelli~in ~y\\ x_{ij},y_i \in\{0,1\}
\end{cases}$$
