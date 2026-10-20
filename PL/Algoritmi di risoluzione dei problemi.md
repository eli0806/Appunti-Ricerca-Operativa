Per la risoluzione di problemi sono neces modelli matematici di PL:
1) Scelta dei dati (solitamente sono specificati dal testo o ricavabili dal problema reale)
2) Scelta delle variabili decisionali 
3) scelta della funzione obbiettivo
4) Scelta dei vincoli: ricodando che avendo **più vincoli** i minimi **avrebbero valori maggiori** e i massimi **valori minori**
5) Scelta dell'algoritmo risolutivo 
6) Feedback da parte dell'algoritmo scelto

**Ma cos'è un modello matematico?**
Un modello matematico è un strumento che permette di **tradurre una tabella (o un insieme di dati) di un problemare reale in un vettore.**

# L'algoritmo del simplesso primale
L'algoritmo del simplesso primale è usato per la risoluzione di **problemi di PL in forma primale standard** (o ricondotti in forma primale standard [[PL/Altre cose importanti#**Rappresentazione algebrica di un problema PL ** (formato standard)]]). 
Esso consiste nell'analisi per **vertici adiacenti** (ossia collegati tra loro attraverso uno **spigolo**, che in $\mathbb{R}^2$ sono 2 e in $\mathbb{R}^3$ sono 3) e rappresenta notevolmente una **semplificazione del test di ottimalità([[PL/Teoremi#5)Teorema del test di ottimalità]])**. 
Esso consiste nell'individuazione di un **vertice** che rappresenta una **soluzione di base primale**, di trovarne la **soluzione complementare** e se essa **fosse ammissibile**, la soluzione è l'**ottimo**; altrimenti è **necessario il cambio di base**. L'algoritmo è fatto in maniera da **non fare ciclare le basi.**
## Passi dell'algoritmo:
1) Si scelga un vertice composto da **una base**.
2) Calcolare la **soluzione del duale** (usando il teorema della dualità ([[PL/Teoremi#4) Teorema della dualità]]))
3) 
	   1) Se positiva: La soluzione è l'ottimo
	   2) Se negativa: è necessario il cambio di base.
	  Ossia si calcola l'indice **uscente** :$$h=min\{i\in B :\overline{y_i}<0\}$$ che è il minimo tra le soluzioni di base trovate.
4) Calcolare la quantità $$A_iW^h~\forall i\in N$$Dove A è la matrice formata dagli indici di base e $W=-A_B^{-1}$ .
	   1) Se il prodotto dovesse risultare $\leq 0$ allora significherebbe che Il **valore ottimo del primale** sarebbe +$\infty$ e **il duale è** $\emptyset$ 
	 2) Se il prodotto fosse positivo, allora sarebbe necessario calcolare **l'indice uscente**$$k \coloneqq min \begin{cases} \frac{b_i - A_i\overline{x}}{A_iW_h} \end{cases}$$==Nota:== Questo rapporto **non può essere mai negativo**, 
## Regola dell'anticiclo di Bland
Se dovessero esserci **parecchi numeri negativi** si sceglie (a parità di valore) il primo (ossia l'indice più piccolo) $\to$ Per evitare che il simplesso **cicli su indici degeneri**.

==Nota:== Mentre gli indici si possono ripetere durante l'algoritmo, **non succederà mai che si ripeta una base.**

## I casi possibili nella risoluzione:
1) Sia la soluzione del primale che del duale sono **ammissibili** $\implies$ Ho trovato **l'ottimo**
2) La soluzione del primale è ammissibile , ma quella del duale no $\implies$ E' necessario un cambio di base (Fisso l'indice uscente)
3) La soluzione del duale è ammissibile ma quella del primale no $\implies$ E' necessario un cambio di base (Fisso l'indice entrante([[#L'algoritmo del simplesso duale]]))
4) Nessuna delle due soluzioni è ammissibile $\implies$ Devo **assolutamente** cambiare tutta la base

# L'algoritmo del simplesso duale
L'algoritmo è **totalmente analogo a quello del simplesso primale** [[#L'algoritmo del simplesso primale]]. Ne seguono i passi per evidenziarne le differenze: 

## Passi dell'algoritmo:
1) Si scelga un vertice composto **da una base**
2) Calcolare la soluzione **del primale**
3) 
	   1) Se $A_N\overline{x} \leq b_N$: La soluzione è l'ottimo
	   2) Se negativa: è necessario il cambio di base.
	  Ossia si calcola l'indice **entrante** :$$k=min\{i\in N :b_i-A_i\overline{x}<0\}$$ che è il minimo tra le soluzioni di base trovate.
4) Calcolare la quantità $$A_kW^i~\forall i\in N$$Dove A è la matrice formata dagli indici di base e $W=-A_B^{-1}$ .
	   1) Se il prodotto dovesse risultare $\geq 0$ allora significherebbe che Il **valore ottimo del duale** sarebbe +$\infty$ e **il primale è** $\emptyset$ 
	 2) Se il prodotto fosse negativo, allora sarebbe necessario calcolare **l'indice entrante**$$h=min\begin{cases}\frac{\overline{y_i}}{-A_kW^i} \end{cases}$$==Nota:== Questo rapporto **non può essere mai negativo**, 