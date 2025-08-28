***TOPICS:***

### **Sets**
* A set is just a collection of distinct elements.
* Example: $A = \{1, 2, 3\}$, $B = \{\text{apple}, \text{banana}, \text{pear}\}$.
### **Universe of discourse**
* Universe is the "big set" we’re working inside.
* Example: If $U = \{1,2,3,4,5\}$, then $A = \{1,3,5\}$ and $B = \{2,4\}$ are subsets of $U$.
### **Binary strings as sets**
* All binary strings = $\{0,1\}^*$.
* Example: $\epsilon$ (empty string), $0$, $1$, $01$, $10$, $111$, etc.
* A subset could be "all binary strings of length 2": $\{00, 01, 10, 11\}$.
### **Union, intersection, cross-product**
* Example: $A = \{1,2,3\}, B = \{3,4\}$
  * Union: $A \cup B = \{1,2,3,4\}$
  * Intersection: $A \cap B = \{3\}$
  * Cross product: $A \times B = \{(1,3), (1,4), (2,3), (2,4), (3,3), (3,4)\}$
### **Cardinality (finite, infinite)**
* Example (finite): $| \{a,b,c\} | = 3$
* Example (infinite): $|\mathbb{N}| = \infty$
### **Size comparison**
* Example:
  * $A = \{1,2,3\}, B = \{4,5,6\}$ → $|A| = |B| = 3$.
  * $C = \{1,2\}$ → $|C| < |A|$.
  * $D = \{1,2,3,4,5\}$ → $|D| > |A|$.
### **Even numbers vs naturals example**
* Naturals: $\mathbb{N} = \{0,1,2,3,4,5,\dots\}$.
* Evens: $E = \{0,2,4,6,\dots\}$.
* Function $f(n) = 2n$:
  * $f(0)=0, f(1)=2, f(2)=4, f(3)=6, \dots$.
* Every natural gets matched to exactly one even number.
* So $|\mathbb{N}| = |E|$, even though $E \subsetneq \mathbb{N}$.
### **Russell’s Paradox / Barber’s Paradox**
* **Russell’s Paradox**:
  * Define $R = \{x \mid x \notin x\}$.
  * If $R \in R$, contradiction.
  * If $R \notin R$, contradiction.
* **Barber’s Paradox**:
  * Village rule: “The barber shaves exactly those men who do not shave themselves.”
  * If barber shaves himself → then he shouldn’t.
  * If barber doesn’t shave himself → then he should.
  * Contradiction.



**Proofs**
* Contradiction
* Induction

**Relations**
* Binary relations
* Examples: divisibility, modular arithmetic, program outputs
* Reflexive
* Symmetric
* Transitive
* Antisymmetric
* Graphs: directed, undirected, path relation, DAG

**Functions**
* $f : S \to T$
* One-to-one (injective)
* Onto (surjective)

***RELATIONS***
**Reflexive**
* $\forall x \in S,\; (x,x) \in R$
**Irreflexive**
* $\forall x \in S,\; (x,x) \notin R$
**Symmetric**
* $\forall x,y \in S,\; (x,y) \in R \implies (y,x) \in R$
**Asymmetric**
* $\forall x,y \in S,\; (x,y) \in R \implies (y,x) \notin R$
**Antisymmetric**
* $\forall x,y \in S,\; (x,y) \in R \land (y,x) \in R \implies x=y$
**Transitive**
* $\forall x,y,z \in S,\; (x,y) \in R \land (y,z) \in R \implies (x,z) \in R$

Pigeonhole Principle:
* More objects than boxes ⇒ some box has ≥2 objects.
* General: $N$ objects in $k$ boxes ⇒ some box has at least $\lceil N/k \rceil$ objects.
