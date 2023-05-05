---
dg-publish: true
---

# 1. Les Bases

#### Passer de la base 10 à la base 16

On prend le nombre en base 10, puis on fait la division euclidienne par 16. On retient le reste. Puis faire la même chose avec le quotient, jusqu'a avoir un quotient égal a zéro. Le nombre en base 16 sera les restes (du plus récent au plus vieux)

#### Passer de la base 16 à la base 10

On prend chaque termes du nombre en base 16, puis on multiplie chaque terme par 16^n  , n étant le rang du termes (0,1,2,3...).

Ex: FBB = (15x16^2) + (11x16^1) + (11x16^0) = 4027 . 

#### Passer de la base 10 à la base 2

On sait que 1111 1111 car 128+64+32+16+8+4+2+1), donc on peut retrouver le nombre que l'on veut avec ça.

#### Passer de la base 2 à la base 10

Tu fais l'inverse (EZ)

# 2. Les Ensembles

![[oui.gif]]


# 3. Matrices

#### Pour trouver une equation matricielle: 
Mettre ces matrices sur la calculette. 

#### Trouver la matrice inverse:
(la matrice) ^ -1

#### Trouver la fermeture transitive d'une matrice

![[FermetureMatrices.pdf]]

# 4. Trouver un type de relation

***Ici, R est "plus grand  que (>)" ***
- x = 4
- y = 2
- z = 1

##### Réflexivité 

*x R x* -> "4 n'est pas plus grand que 4" donc pas de réflexivité.

##### Symétrie

Si *x R y*, alors *y R x* .  "4 est supérieur à 2 alors 2 est supérieur à 4 " -> pas vrai donc pas symétrie.

##### Transitivité 

Si *x R y* et que *y R z* alors *x R z* " Si 4 est plus grand que 2, et que 2 est plus grand que 1, alors 4 est plus grand que 1" -> il y a transitivité.

##### Antisymétrie

Si *x R y* et *y R x*, alors *x = y*. Dans notre cas, il n'y a pas antisymétrie.

### Relation d'ordre

Si R est réflexive, antisymétrique et transitive, alors R est une relation d'ordre. 

### Relation d'équivalence

Si R est réflexive, symétrique et transitive, alors R est une relation d'équivalence.

# 5. Booléens

#### Faire un tableau de Karnaugh

Remplir le tableaux en fonction des proposition. Ensuite, chercher à regrouper ces proposition dans les plus grands groupes possibles. Ainsi, on pourra simplifier l'expression. 

|       |       |       |       |       |
|---    |:-:    |:-:    |:-:    |--:    |
|        |  B     |B       |B̄       | B̄      |
|   A    |       |       |       |       |
|   Ā    |       |       |       |       |
|        |  C     |C̄       |C̄      | C   |

# 6. Méthode MPM

#### Faire le graphe: 

![[mpm.png]]

### Calculer les différents éléments 
-   **Date au plus tôt :**
    -   Date à laquelle on peut commencer la tâche parce que les tâches précédentes sont terminées.
    -   formule : **= Max (Dates au plus tôt précédentes + durées précédentes).**  
          
        
-   **Date au plus tard :**
    -   Date maximale à laquelle on peut commencer la tâche sans repousser la fin du projet.
    -   formule : **= Min (Date au plus tard suivantes) - durée de la tâche.**  
          
        
-   **Marge totale :**
    -   Retard autorisé à la tâche sans retarder la fin du projet.
    -   formule : **= Date au plus tard - Date au plus tôt.**  
          
        
-   **Marge libre :**
    -   Retard autorisé sans retarder aucune des tâches suivantes.
    -   formule : **= Min (Dates au plus tôt suivantes) - Durée de la tâche - Date au plus tôt de la tâche.**

# Arithmétique 

## Calculer le Plus Grand Diviseur Commun:

#### Algorithme d'Euclide : méthode

● 1) On effectue la division euclidienne du plus grand des deux nombres par le plus petit.

● 2) On effectue la division euclidienne du diviseur par le reste de la division précédente, jusqu’à ce que le reste de la division soit égal à zéro.

● 3) Le PGCD est le dernier reste non nul dans la succession des divisions euclidiennes.

#### Algorithme d'Euclide : exemple

**Exemple :** Déterminer PGCD (1 326 ; 546).

Le dernier reste non nul est 78

**Remarque :** On peut schématiser l’algorithme ainsi :

1 326 = 2 × **546** + **234**

**546** = 2 x **234** + **78**

**234** = 3 x **78** + 0

