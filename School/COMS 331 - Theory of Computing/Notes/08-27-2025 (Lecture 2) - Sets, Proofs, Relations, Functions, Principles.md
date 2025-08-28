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

Example:
Let $S = \{1,2,3\}$.
We’ll check each property by going through the elements of $S$.
### Reflexive
**Definition:** For every $x \in S$, $(x,x) \in R$.
**Example:**
$R = \{(1,1),(2,2),(3,3),(1,2)\}$
Check each element of $S$:
* For $x=1$: $(1,1) \in R$
* For $x=2$: $(2,2) \in R$
* For $x=3$: $(3,3) \in R$
Since all self-pairs are included, $R$ is reflexive.
### Irreflexive
**Definition:** For every $x \in S$, $(x,x) \notin R$.
**Example:**
$R = \{(1,2),(2,3)\}$
Check each element:
* For $x=1$: $(1,1) \notin R$
* For $x=2$: $(2,2) \notin R$
* For $x=3$: $(3,3) \notin R$
None of the self-pairs are included, so $R$ is irreflexive.
### Symmetric
**Definition:** If $(x,y) \in R$, then $(y,x) \in R$.
**Example:**
$R = \{(1,2),(2,1),(2,3),(3,2)\}$
Check each pair:
* $(1,2) \in R$. Is $(2,1) \in R$? Yes.
* $(2,1) \in R$. Is $(1,2) \in R$? Yes.
* $(2,3) \in R$. Is $(3,2) \in R$? Yes.
* $(3,2) \in R$. Is $(2,3) \in R$? Yes.
All pairs have their reverse, so $R$ is symmetric.
### Asymmetric
**Definition:** If $(x,y) \in R$, then $(y,x) \notin R$.
**Example:**
$R = \{(1,2),(2,3)\}$
Check each pair:
* $(1,2) \in R$. Is $(2,1) \in R$? No.
* $(2,3) \in R$. Is $(3,2) \in R$? No.
No pair has its reverse, so $R$ is asymmetric.
### Antisymmetric
**Definition:** If $(x,y) \in R$ and $(y,x) \in R$, then $x=y$.
**Example:**
$R = \{(1,1),(2,2),(3,3),(1,2)\}$
Check pairs:
* $(1,1)$ has reverse $(1,1)$. Since $1=1$, allowed.
* $(2,2)$ has reverse $(2,2)$. Since $2=2$, allowed.
* $(3,3)$ has reverse $(3,3)$. Since $3=3$, allowed.
* $(1,2) \in R$. Is $(2,1) \in R$? No. So no violation.
No violation, so $R$ is antisymmetric.
### Transitive
**Definition:** If $(x,y) \in R$ and $(y,z) \in R$, then $(x,z) \in R$.
**Example:**
$R = \{(1,2),(2,3),(1,3)\}$
Check chains:
* $(1,2)$ and $(2,3)$ ⇒ need $(1,3)$. Yes, it is in $R$.
* $(2,3)$ has no pair starting with 3, so nothing to check.
* $(1,3)$ has no pair starting with 3, so nothing to check.

### Pigeonhole Principle
**Basic Idea:**
If you have more objects than boxes, at least one box must contain more than one object.
Example:
* 5 objects, 4 boxes → at least one box contains 2 or more objects.

**General Form:**
If you have $N$ objects and $k$ boxes, then some box contains at least
$$
\lceil N/k \rceil
$$
objects. Here, $\lceil x \rceil$ means “round x up to the nearest whole number.”

**Example Problem 1:**
There are 13 people in a room. Show that at least two of them were born in the same month.
**Solution:**
* **Objects (pigeons):** 13 people
* **Boxes (pigeonholes):** 12 months
* Since $13 > 12$, by the Pigeonhole Principle, at least one month must have at least 2 people.

**Example Problem 2 (General Form):**
A drawer contains 20 socks, each either black, white, or gray. What is the minimum number of socks you must pick to guarantee at least 8 of the same color?
**Solution:**
* **Objects:** the socks you pick
* **Boxes:** 3 colors
* Use the general form: if you want at least 8 of the same color, assume the worst case where each color has 7 socks first.
* Total socks in worst case: $7 + 7 + 7 = 21$ → one more sock (22nd) guarantees 8 of the same color.