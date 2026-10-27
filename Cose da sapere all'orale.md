1) Come fare l'algoritmo dei piani di taglio di Gomory a livello matematico
2) Una base B è ammissibile nel formato primale? Anche nel suo corrispettivo duale? $\to$ Ragionare "al contrario"
   **Risposta:**
   Disegnare tutti i vettori $\to$ Formiamo il **cono di competenza della base** ( ossia la porzione di un angolo giro identificata univocamente da una base per lo specificon problema in analisi). 
   Una base ammissibile per il duale non è per forza ammissibile nel primale (allora possiamo dire che non è ottima) $\to$ Possiamo trovare l'indice entrante (attraverso il simplesso) da sostiture all'interno del primale
3) Come si risolve (avendo a disposizione un software che fa il [[PLI/Algoritmi di risoluzione dei problemi#Il Branch and Bound|Branch and Bound]]) , un problema di zaino intero dove **non dobbiamo considerare solo il peso , ma peso e volume**?
   - Attraverso il metodo dei [[PLI/Algoritmi di risoluzione dei problemi#Il metodo dei piani di taglio di Gomory|Metodo dei piani di taglio di Gomory]]
   - Attraverso l'algoritmo del [[PLI/Algoritmi di risoluzione dei problemi#Il Branch and Bound|Branch and Bound]]
   
   A prescindere è necessario calcolare $V_I$ e $V_s$ , $V_s$ attraverso il rilassato continuo e $V_I$ con soluzioni ammissibili **greedy e facili da calcolare** 
   
   ==🔴Nello zaino non conta il valore o il peso ma il rapporto ( o rendimento).==
   
   Al fine di calcolare il rendimento è necessario fare **la media ponderata** creando un "**super rendimento".
4) Se un problema non ammette la possibilità di Branch and Bound, cosa dovremmo modificare al fine di poterlo utilizzare

# Domande per la lode: 
## 1) ![[Pasted image 20261027185624.png]]
**E' necessario ricavare un assegnamento di costo minimo che con abbia un consumo maggiore di 280.**

## Costruzione del modello : 
$$ \begin{cases}
min~C^Tx \\
x_{11}+x_{12}+x_{13}=1 \\
x_{21}+x_{22}+x_{23}=1 \\
x_{31}+x_{32}+x_{33}=1 \to Abbiamo~6~vincoli~di~assegnamento\\ 
x_{11}+x_{21}+x_{31}=1 \\
x_{12}+x_{22}+x_{32}=1 \\
x_{13}+x_{23}+x_{33}=1 \\
86x_{11}+84x_{12}+85x_{13}+91x_{21}+92x_{22}+90x_{23}+78x_{31}+35x_{32}+77x_{33}\leq 280
\end{cases}$$
## Domande
1) **Il problema gode di interezza?** 
   No, per natura dei vertici che permettono la soluzione del problema 
2) **Come andrebbe ottenuta una $V_I$?**
   Mantenendo i vincoli di interezza , ma **eliminando il vincolo del consumo delle risorse**.
3) **Potrebbe essere un problema vuoto per 280?** Sì.
   