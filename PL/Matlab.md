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