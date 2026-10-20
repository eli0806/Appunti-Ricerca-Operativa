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

