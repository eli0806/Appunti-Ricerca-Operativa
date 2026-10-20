# 1) **Teorema di Weyl (o di rappresentanza dei poliedri):**
   Dato un poliedro P. Allora $$\exists~V=\{v_1,~...~v_k\}\in P$$
   ed $$\exists E=\{e_1,~..., e_p\}$$
   tali che $$P=conv~V + conv~ E$$
   ==Nota:== Per conv si intende **l'insieme di tutte le combinaioni convesse** (ossia le possibili somme tra due insiemi)
   ==Nota:== La rappresentazione di Weyl non è unica.
# 2) **Teorema fondamentale della PL:**
   Sia dato un problema di PL i formato primale standard max c.
   Siano v ed e, un insieme della rappresentazione di Weyl del poliedro. 
   Allora può succedere una e una sola di queste tre situazioni:
	- La soluzione **non si può trovare** (ad esempio per la presenza di troppi vincoli o di vincoli incompatibili tra di loro)
	- Il problema va a $+ \infty$ (per l'assenza di vincoli )
	- Uno dei punti di v è **sicuramente ottimo**
# 3) Teorema della caratterizzazione dei vertici
1) **Terorema di caratterizzazione dei vertici:** 
  Un punto $\overline{x} \in P$ è un vertice **se e solo se** è **una soluzione di base ammissibile**.
2) **Teorema di caratterizzazione dei veritici bis:**
  Un punto appartiene ad un poliedro D in **forma duale standard**([[PL/Altre cose importanti#I poliedri in forma duale standard]]) è un **vertice,se e solo se è una soluzione ammissibile.**
  Una **soluzione di base** si dice **degenere** se **anche una sola delle componenti di x è 0**.
# 4) Teorema della dualità
1) **Teorema della dualità:** $$(P)\begin{cases} max~C^Tx \\ Ax\leq b \end{cases} \to (D)\begin{cases} min~b^Ty \\ A^Ty=C \\ y_i\geq 0 \end{cases}$$Con$$A~m*n,~rango~massimo,~b\in\mathbb{R}^m,~C\in\mathbb{R}^n$$
	   Vale $P \neq \emptyset~?$ 
	   	2) **Teorema della dualità (STRONG)**
		**Ipotesi:** Supponiamo che $P,D\neq \emptyset \to$ Ossia che **non siano vuoti**$$\begin{cases}max~C^Tx \\ x \in p \end{cases} = \begin{cases} min~b^Ty \\x\in D \end{cases}$$Dove ($A^Ty=c$)
		
**Corollario:** Se $$\overline{x}\in P, \overline{y}\in ~tali~che~C^T\overline{x}=b^T*\overline{y}$$Allora $\exists~A_B\overline{x}=b_B$ e |B|=n.
		
Da ciò abbiamo, inoltre, che $\overline{x}\in P$ è **vertice** , perché **soluzone di base ammissibile** $\implies$ **Soluzione ottima**
		
E' importante notare che:$$A^Ty=C\to A_B^t~\overline{y_B}=c$$$$\overline{y_n}=0~~~~~~~~(C(A_B^t)^{-1},0)=(Y_B,Y_n)=\overline{y}$$Dove $\overline{y}$ è la **soluzione complementare**.
		Insomma **preso un vertice primale** costruisco **la forma duale** , talora la soluzione del **duale** fosse ammissibile **abbiamo la soluzione ottima**. **Test di ottimalità (Teorema)([[PLI/Definizioni]])**

# 5)Teorema  del test di ottimalità
[[PLI/Definizioni]]
1) $\overline{x}$ vertice di P               se $C(A_B^T)^{-1}\geq0$ , allora $\overline{x}$ è ottima
2) $\overline{y}$ vertice di D               se la complementare $\overline{x}$ è ammissibile allora $\overline{y}$ è ottima