# PL
Per risolvere dei problemi di PL con matlab è necessario porli nella forma :
$$ \begin{cases}min~c^Tx~\\ Ax \leq b \\ Aeqx=beq \to beq~rappresenta~il~poliedro~p \\ LB \leq x \leq UB \end{cases}~ $$

==Nota:== L'ordine in cui si inseriscono i vari elementi non ha importanza (però nella funzione linprog sì)

**Specifiche:**
$$\begin{gather*} x \in \mathbb{R}^n \\ C \in \mathbb{R}^n \\ A \in \mathbb{R}^{n*m} \\ b \in \mathbb{R}^p \end{gather*}$$
Dove: 
- m= **numero di vincoli di uguaglianza**
- p=**numero vincoli di disuguaglianza**

**Se non si hanno vincoli di uguaglianza  si scrive:**
Aeq=$[]$ e beq=$[]$ 

# PLI
Per risolvere problemi di PLI è possibile usare un comando chiamato **intlinprog**. 

Esso ha la seguente sintassi: 

**intlinprog(** C,I,A,b,Aeq,Beq,Lb,Ub **)** 

**Cos'è I?** 
I è un insieme che indica **quali variabili devono essere intere** ( è molto utile nei problemi misti, dove **solo alcune variabili sono necessariamente intere**)

Presenta questa sintassi: 

I=$[var_{1},var_{2},var_{3}\dots,var_{n}]$ 

# Risolvere il problema [[PLI/Problemi#4) Il problema del "Bin Packing"|Bin packin]]
## Quante variabili abbiamo?
 $n*y+y$ (dove y numero di bin)

## Come si compone il vettore C? 
Il vettore C si compone di $n*y$ zeri e di y 1. 

## Come si compone il vettore b? 
Il vettore b è composto da **solo zeri** ($n*y$) , poiché, al fine di garantire un collegamento tra le variabili $x_{ij}$ e $y$ , i termini noti vengono "spostati" nel lato sinistro delle disequazioni dei vincoli.

## Come si compone il vettore Aeq?
Per definire il vettore Aeq, in primis, è necessario mettere in ordine lessicografico (ossia ad esempio da $x_{11}$ a $x_{nn}$). 
Successivamente, è necessario: 
- Inserire 1 in corrispondenza delle colonne (relative ai bin) dove potrebbe trovarsi l'oggetto 
- Inserire 0 nello spazio restante
  
  ==Nota:== Ogni riga ha dimensione $n*y+y$ 
## Come si compone il vettore A?

La matrice A si compone dei coefficienti relativi ai pesi degli oggetti ($w_i$), posizionati nelle colonne del rispettivo bin, ne seguono tanti zeri quante le posizioni non occupate dall'accoppiata oggetto-bin, e infine il valore $-C$ (meno la capacità) in corrispondenza della colonna della variabile $y_j$ di quel bin.