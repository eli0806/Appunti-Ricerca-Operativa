**Problema di programmazione lineare:** 
Dicesi problema di **programmazione lineare**, un problema di **minimo e massimo** di una **funzione lineare** soggetta a **vincoli lineari** di $\leq$ , $\geq$ o =.

==Nota:== Non sarà mai possibile trovare un problema di programmazione lineare con > o <, e in tal caso sarebbe necessaria la modifica del vincolo inposto (in un valore minore o maggiore)

1) **Ottimizzazione:** Per ottimizzazione si intende un problema di **massimo e minimo** su una funzione $$f: \mathbb{R}^n \to \mathbb{R}$$ ristretta ad una regione $\Omega$ chiamata **regione ammissibile** e deriva **dall'intersezione dei vincoli**.  
2) **Vincoli:** chiamati anche "costrains" di un problema , sono delle funzioni di tipo :$$g(x)\leq 0$$
3) **Variabili decisionali:** Per variabili decisionali si intende **l'insieme delle variabili** necessarie a **trasformare il problema reale** in un **modello matematico**. Hanno cardinalità $\in \mathbb{R}^n$ . Se un bene è divisibile si considera l'arrotondamento per difetto, altrimenti si considera il numero ottenuto nello specifico
4) **Soluzione ammissibile:** è una soluzione che **rispetta tutti i vincoli**.
5) **Soluzione ottima:** soluzione (che è il massimo o il minimo) che rispetti tutti i vincoli
6) **Poliedro (matematica):** Dicesi poliedro (poligono in $\mathbb{R}^2$ ) **l'intersezione** (ossia devono essere soddisfatti tutti) **di un numero finito di semispazi** (semi=$\mathbb{R}^2$ , spazi=lineare) **chiusi**(ossia che contenga una frontiera (o bordo)).
7) **Poliedro (ricerca operativa):** Dicesi poliedro **l'insieme delle soluzioni del sistema di disequazioni lineare $$Ax \leq b$$
8) **Combinazione convessa:** Dati k vettori di $\mathbb{R}^n(x^1,~...~,x^t \in \mathbb{R}^n)$ , Y $\in \mathbb{R}^n$ , si dice che è **combinazione convessa** degli $x^i$ se $$\exists~\lambda_i, i=1,~...~,~k$$  con $$x_i \in [0,1]~|~Y=\sum_{i=1}^k \lambda_ix^i=\lambda_1x_1+\lambda_2x_2+~...~+\lambda_kx_k$$
9) **Combinazione convessa:** Dati k vettori di $\mathbb{R}^n(x^1,~...~,x^t \in \mathbb{R}^n)$ , Y $\in \mathbb{R}^n$ , si dice che è **combinazione conica** degli $x^i$ se $$\exists~\lambda_i, i=1,~...~,~k$$
   con $$\lambda_i\geq 0~|~Y=\sum_{i=1}^k \lambda_ix^i $$
10) **Vertici (matematica):** Un punto $\overline{x} \in P$ si dice **vertice** se **non si può esprimere** come **combinazione convessa** di altri  2 punti del poliedro con $\lambda \neq 0 \land \lambda \neq 1$  (ossia i punti **che non sono interni ad un segmento** del poliedro)
11) **Soluzione di base:** Una soluzione di base si dice **degenere** se soddisfa con **condizione di uguaglianza** almeno uno dei vincoli **non di base** . Essi sono indicati con la lettera N.
12) **Test di ottimalità:** Dato $\overline{x} \in P$, vertice, B (Base). Se $C(A_B^T)^{-1}\geq 0$ allora $\overline{x}$ è **ottimo**.
    ==Nota:== Non esistono test di ottimalità per soluzioni che **non hanno vertici**
    1) Si verifica **l'ammissibilità**
    2) Si risolvono **almeno N equazioni linearmente indipendenti**