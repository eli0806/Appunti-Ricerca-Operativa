# Il formato generale dei problemi 
$$\begin{cases} max~c^Tx \\ Ax \leq b \\ x \in \mathbb{Z}^n \end{cases}$$
Siccome non è possibile la dualità per i problemi di PLI, la loro **rappresentazione algebrica** prende il nome di **formato generale**. 
La differenza con i problemi di PL è l'obbligo alle variabili che lo compongono (C, A e b) di **assumere valori interi.**

## Formato geometrico e regione ammissibile

E' possibile rappresentare il problema attraverso il **poliedro $P=A_x \leq b$** .
Il poliedro in questione è composto da punti evidenziati che rappresentano **le componenti intere $\in$ P.

$P \cap \mathbb{Z}^n=S$ è **la regione ammissibile del problema generico (P) di PLI** ed è composta da **un numero finito di punti** $\implies$ Il poliedro **non ha struttura**.


# ==🔴Note per evitare errori==

- L'ottimo di un problema di PLI **non si ottiene** dall'ottimo del corrispettivo problema PL arrotondato.
- L'ottimo di un problema di PLI **non sempre** corrisponde ad un punto vicino all'ottimo (osservando il poliedro)
# Gestione dei problemi di minimo 
$$V_I=V_{PL} \leq \begin{cases} min~C^Tx \\ Ax \leq b \\ x \in \mathbb{Z}^n \end{cases} \leq C^T\overline{x}=V_s$$
# Ottimo PL a componenti interi
Se una soluzione di un problema  di PL rilassato restituisse **solo componenti intere** (ossia $\tilde{x}$ soluzione ottima ) $\implies$ Si ha che $V_I~e~V_s$ coincidono , rendendo il gap 0 , terminando l'algoritmo di restringimento del gap ([[PLI/Algoritmi di risoluzione dei problemi|Algoritmi di risoluzione dei problemi]]). 
# Ordine dei "4 numeri" per la soluzione dei problemi di PLI
$$C^T\overline{x}\leq \begin{cases} max~C^Tx \\ x \in P \cap \mathbb{Z}^n \end{cases} \leq \begin{cases} max~C^Tx \\ x \in convS \end{cases} \leq \begin{cases} max~C^Tx \\ x\in P \end{cases}$$Ossia $$V_I\leq V_{PLI} \leq VconvS \leq V_{PL}$$ Dove sia $VconvS$ che $V_{PL}$ rappresentano il limite superiore $V_s$ ([[PLI/Algoritmi di risoluzione dei problemi|Algoritmi di risoluzione dei problemi]])

# Perchè ci interessano le matrici unimodulari ([[PLI/Definizioni#2) Matrice unimodulare|Definizioni]])?
Prendiamo una matrice modulare$$A=\begin{pmatrix} [n*n] \\& \end{pmatrix}$$

di dimensioni m * n. 
I vertici di questa sono definiti da  $\overline{x}=A_B^{-1}b_B$

Consideriamo ora i **denominatori di ogni entrata** ossia $$\frac{}{(det~A_B)}$$
per le matrici unimodulari esso è sempre 1 o -1 e perciò , il rapporto raffigurato restituisce un valore intero $\implies$ **I problemi di PL con matrici A unimodulari hanno la seguente proprietà:**
- Vertici **a componenti intere**.

==🔴Nota:== Per i problemi di PL con matrice A unimodulare non abbiamo bisogno di applicare l'algoritmo di riduzione del gap ([[PLI/Algoritmi di risoluzione dei problemi|Algoritmi di risoluzione dei problemi]]), poiché i vertici sono a componente intera.

# Parliamo di problemi che sono composti da matrici unimodulari 
Quando si risolve un problema dell'assegnamento, descritto da una matrice unimodulare, distinguere un assegnamento cooperativo da uno non coperativo è futile, poichè la risoluzione avviene attraverso la PL a prescindere. 

==🔴Il problema dell'assegnamento non è un vero problema di PLI==

Anche il problema del trasporto è descritto attraverso una matrice unimodulare $\implies$ Non è necessario distinguere tra beni divisibili e indivisibili. $\implies$ Non è un problema di PLI

==Nota:== E' possibile comunque ottenere **infinite soluzioni** diverse da quella che si otterebbe applicando **l'algoritmo del simplesso** ([[PL/Algoritmi di risoluzione dei problemi#L'algoritmo del simplesso primale| L'algoritmo del simplesso]]) $\to$ Si tratta delle **soluzioni frazionarie** 

Le soluzioni frazionarie **non potranno mai essere vertici** del poliedro P rappresentante il problema (P).
# Effetti dei piani di taglio ([[PLI/definizioni#4) Piano di taglio | Piano di taglio]]) sul problema  Risolvibile dall'allgoritmo di risoluzione del gap([[PLI/Algoritmi di risoluzione dei problemi#Algoritmo di riduzione del GAP|algoritmo di risoluzione del gap]])

Aggiungendo un piano di taglio , il problema viene adesso formulato così:$$\begin{cases}
max~c^Tx\\ Ax\leq b \to Fino~a~qui~è~una~soluzione~inammissibile \\ \gamma_x\leq \gamma_0 \to L'insieme~di~questo~vincolo~con~quello~precedente~ci~da~\textbf{una Vs migliore}
\end{cases}$$
### Chi mi autorizza ad aggiungere il terzo vincolo ?
Siccome il problema, con l'aggiunta del vincolo, rimane invariato (poiché non si va a modificare la struttura di S([[#Il formato generale dei problemi|S]])) è utilissimo aggiungere il vincolo che mi determini il **piano di taglio** ([[PLI/Algoritmi di risoluzione dei problemi#Il metodo dei piani di taglio di Gomory|Piani di taglio di Gomory]])

# Quanti piani posso generare con l'ottimo del rilassato continuo?
Con l'ottimo del rilassato continuo posso generare **un piano per ogni variabile di base** (vale a dire N piani) con l'unico vincolo che la parte frazionaria della variabile **sia non nulla**.

# Dal [[PLI/Problemi#2) Il problema del T.S.P(S) (Travelling Sailsman Problem)|Problema di T.S.P]] che possiamo trarre ? 

Che **un ciclo hamiltoniano è un assegnamento** ma ==🔴non vale viceversa==. 

Un esempio di assengamento che **non è un ciclo hamiltoniano** è un problema di assegnamento risolto attraverso **un unione di cicli disgiunti.**

Al modello matematico per la risoluzione è necessario aggiunger il vincolo $$S\subset N$$
# Nell'algoritmo [[PLI/Algoritmi di risoluzione dei problemi#Il Branch and Bound|Branch and Bound]] , perchè $V_{I}(P_{ij})\geq V_{s}(P)$ mi autorizza a tagliare?

![[Schema branch and bound.png]]
# Chi è $V(P_{ij})$?
E' l'ottimo, ossia **il ciclo hamiltoniano** dove ho istanziato le variabili.
