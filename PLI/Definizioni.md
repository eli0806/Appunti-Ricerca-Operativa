# 1) Problema di PL rilassato:
   Dato un problema di PLI, il problema di PL che si ottiene eliminando i vincoli di interezza si chiama **problema di PL rilassato continuo** e vale:
   $$v_{PLI} \leq v_{PL}=V_s$$Dove $V_s$ prende il nome di **valutazione superiore** e rappresenta **la stima per eccesso dell'ottimo del corrispettivo PL** del problema.$$(P)\begin{cases} max~c^Tx \\ Ax \leq b \\ x \in \mathbb{z} \end{cases} \implies \begin{cases} max~c^Tx \\ Ax \leq b \end{cases}$$
# 2) Matrice unimodulare:
Una matrice $$A~m*n~~~~m>n~~~~rango~n$$si dice **unimodulare** se i determinanti delle sottomatrici quadrate di rango massimo (ossia le **basi**) sono tutti **1 o -1**.
# 3) Disuguaglianza valida: 
Si dice **disuguaglianza valida**, un qualsiasi vincolo tale che se $\gamma^Tx*x\leq \gamma_{0}~\forall x \in S$ 

# 4) Piano di taglio: 
Un **piano di taglio** è definito tale se $$\gamma^Tx_{OTT}^{PL}>\gamma_{0}$$
# 5) Ciclo hamiltoniano: 
Il ciclo hamiltoniano è un ciclo che **parte da un nodo orientato (talora il problema fosse asimmetrico)** e tocca tutti i nodi del grafo