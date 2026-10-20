# **Rappresentazione algebrica di un problema PL:**  (forma primale standard)
$$ \begin{cases}max~c^Tx~\to \textbf{funzione obbiettiva} \\ Ax \leq b~\to \textbf{matrice dei coefficienti} \end{cases} $$

Dove C è il gradiente della funzione obbiettiva

==Nota:== Questa rappresentazione **non è unica**

# **Feedback:** È il valore restituito dall' algoritmo , se sbagliato significa che ho applicato male i vincoli 

# Regola del minimo e del massimo
**"Fare i massimi e i minimi è la stessa cosa":**
$$ max~f(x)= - min(-f(x))$$
o nello specifico:
$$\overline{x}\in sgn~max~f(x)<=> \overline{x}~sgn~(-f(x))$$
# **Rappresentazione  geometrica:**  rappresentazione della regione ammissibile ([[PL/Definizioni]]) attraverso un poliedro([[PL/Definizioni]])
==Nota:== in questo caso conviene considerare i vincoli come **semipiani** , che vanno analizzati così:
- Parte corretta <
- al di sopra del piano =
- fuori dal piano >

==Nota:== Anche le rette sono poliedri 

## **Perchè consideriamo il minore uguale e non il minore stretto?**
Nella risoluzione di un sistema di  programmazione lineare, è necessario usare il **minore uguale** e non il minore stretto perchè nel secondo caso non verrebbe valutata la **frontiera**.

## **Perchè è importante che sia valutata anche la frontiera?**
E' importante che sia valutata anche la frontiera perchè per il **teorema di fermat** oppure **valutando il gradiente** sappiamo che **il massimo** o **il minimo** si trova su di esso. $\implies$ La soluzione otttina **NON È** all'interno del poliedro ([[PL/Definizioni]])

==Nota:== I problemi reali , in verità non hanno mai propriamente vincoli di $\leq$ o $\geq$ 

# **Rette di ISO-guadagno:**
Sono rette della forma $$x_1+x_2=K$$ con $k \in \mathbb{R}$
E permettono di rimanere nella **regione ammissibile**([[PL/Definizioni]]) ma facendo alzare il guadagno sempre di più. ( Si parla ancora di **risoluzione geometrica**)

Dal poliedro si ottengono **un  numero finito di vertici** , attraverso **un sistema tra i vincoli**.


# **Parlando della soluzione ottima:**
- Non è **sempre unica**
- Non sempre **corrisponde ad un vertice** $\implies$ Il **poliedro può risultare illimitato** $\to$ vincolo mancante , restituisce $+\infty$ 

==Nota:== Nella pratica l'illimitatezza di un poliedro è impossibile $\to$ Uso dell'**upperbound** (soglia massima) basato sulle risorse che ho a disposizione

==Nota:== Se i vincoli sono troppi , può risultare che il nostro algoritmo di risoluzione restituisca **l'insieme vuoto**

# **Equazione del segmento:**
$$\lambda a + (1- \lambda)~b$$ con $a,b \in \mathbb{R}^n$ e $1\geq\lambda\ge 0$  

**Baricentro( di un triangolo):**

$$P(\frac{1}{3},\frac{1}{3},\frac{1}{3})$$


# **Note sull combinazioni convesse ([[PL/Definizioni]])**
Le combinazioni convesse formano **sempre** un poligono, ma esso non è necessariamente di k lati.

# **A che cosa serve il teorema di Weyl ([[PL/Teoremi]])?** 
$$x \in P \to V,E$$
Ho la necessità di calcolare la funzione $$C^t*x=C^t(\sum_{i=1}^k \lambda_iv_i + \sum_{j=i}^p \overline{\mu}_je_j)$$
Dove abbiamo che : 
- $0 \leq \lambda \leq 1$
- $\overline{\mu}_je_j>0$ 

Per le proprietà del prodotto scalare:
$$\sum_{\overline{\lambda}_i}^k(C*v_i)~+\sum_{j=1}^P\overline{\mu}_j(C*e_j)~=C*x$$
Si noti che se un solo un fattore della seconda parte dell'equazione fosse positiva, ciò significherebbe che la funzione risulterebbe illimitata ( andrebbe a $+\infty$) $\implies$ Non è possibile la risoluzione del problema 

Sappiamo inoltre che **il massimo della somma è uguale alla somma dei massimi** (e perciò se esiste il massimo, esso è finito). 
La condizione per cui esista il massimo è $$\mathbf{C*e_j\leq 0}$$
## **Cos'è E nel teorema di Weyl([[PL/Teoremi]])?**

E rappresenta **l'insieme delle direzioni in cui il poliedro  "va a più infinito".**
Non è **mai vuoto** perchè **contiene l'origine** ( o si può dire anche che sia formato dal **solo vettore nullo**)


## **Che relazione c'è tra V di Weyl e i vertici?**

Siccome $$V\in \forall P$$
Quando un poliedro ha vertici, V è composto **dall'insieme dei vertici**.

Esistono però **poliedri che non hanno vertici**:
in $\mathbb{R}^2$ sono: 
- Il piano intero
- I semipiani 
- Le rette 
- Le strisce 

**Ossia la caratterizzazione è :** poliedri che contengono rette.

Ma vertici $\neq$ V

# Che relazione c'è tra problema (p) finito e un poliedro illimitato?

Un problema (P) finito ha **sempre un ottimo finito** , anche in assenza di vertici come nel caso delle strisce.
# Qual'è un poliedro illimitato?

E' un poliedro che è chiuso (per definizione tutti i poliedri sono chiusi, ossia **contengono la frontiera/bordo**) ma che non è contenuto in una palla di raggio R. 

L'ottimo di un poliedro è sulla frontiera **se esiste**. 
# Come trovare algebricamente i vertici: 
 Abbiamo una matrice quadrata :
 $$\begin{gather*} A \in \mathbb{R}^{m*n}\\ m\geq n~\land rangoA=m \end{gather*}$$
 Ossia dove A ha rango **massimo**.
 Un vettore di indici:$$\begin{gather*}B \subset\{1,..., n\}\\|B|=n \\ Ab~invertibile~e~formata~dagli~indici~di~base~B\end{gather*}$$
 Dove $i\in B$ rappresenta un indice di riga della matrice base e Ab la **sottomatrice di A composta dagli indici $\in b$** 

La soluzione del sistema Abx=bB (che sono **i termini noti relativi agli indici $\in$ B**) si dice **soluzione di base**.

Ossia:$$\overline{x}=A_{b}^{-1}*b_B$$
  Inoltre le soluzioni di base si dividono in 2 categorie: 
  - **Soluzioni ammissibili:** se $\overline{x} \in P$ 
  - **Soluzioni non ammissibili:** se $\overline{x} \notin P$

Per verificare l'ammissibilità, sostituisco **la soluzione base** nei vincoli che **non sono sati scelti come base**.
# Degenere $\neq$ Superfluo 

Il fatto che una soluzione sia degenere non implica che le equazioni per la quale è verificata siano superflue. 

Inoltre **non esiste nessun algoritmo che permetta la dimostrazione, del fatto che un equazione sia superflua**

# I poliedri in forma duale standard

I **poliedri in forma duale standard** hanno la forma :
$$\begin{cases} Ax =b \\x\geq 0 \end{cases}$$
Dove **tutte le equazioni** e **tutte le variabili sono positive**.

## Le regole di trasformazione

Se i vincoli **non sono espressi con l'=** nel problema , è possibile, attraverso le regole di trasformazione, con la sola clausola che **tutti i vincoli debbano essere positivi:**
1) **min/max:** Per trasformare un minimo in un massimo o viceversa si usa la formula [[#Regola del minimo e del massimo]]
2) $\leq \leftrightarrow \geq$ 
3) $=\to\leq$
4) $\leq \to =$ 
5) **Differenza tra interi:** Talvolta, non è possibile applicare i casi precedenti ai problemi che vengono posti, allora può essere utile aggiungere una variabile aggiuntiva chiamata **variabile di scarto**, che può inoltre facilitare i calcoli. La variabile di scarto può essere anche in sostituzione di un numero , che viene espresso **con una differenza.** 
## Come si calcolano i vertici in forma duale standard 

Si consideri $B \subseteq\{ 1,...,n\}$ **un insieme di indici di colonna** , $A_B$ una **matrice invertibile** $\in \mathbb{R}^m*n$.
L'equazione $A_Bx_B=b$ ha una **sola soluzione** che si calcola così:
Considero le **sottomatrici quadrate $n*n$** :
B ed n , dove rappresenta la **sottomatrice formata dagli indici di base** mentre n **quella formata dagli indici NON di base**.
Ho una **soluzione ammissibile se:**$$(x_B,0)=\overline{x}$$Dove $\overline{x}_B=A_B^{-1}*b$ e la soluzione si dice **ammissibile** se $X_B$ **positiva**