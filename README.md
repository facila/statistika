Fontion de statistiques d'une table mysql
```
Comptage du nombre d'éléments de chaque colonne

Exemple à partir de la variable $mysql contenant une table 
 
fct_sql_stat.pl "$mysql" 2-
mysql :
 +-----------+---------+-----------+-------------+---------+--------+---------+
 | numero    | nom     | prenom    | departement | marque  | modele | couleur |
 +-----------+---------+-----------+-------------+---------+--------+---------+
 | AB 123 CD | Henri   | Philippe  | Paris       | Renault | Clio   | Blanc   |
 | AB 456 CD | Martin  | Michel    | Paris       | Citroen | C4     | Blanc   |
 | AB 789 CD | Dupont  | Eric      | Paris       | Peugeot | 308    | Noir    |
 | EF 123 GH | Olivier | Catherine | Eure        | Peugeot | 308    | Blanc   |
 | EF 456 GH | Lucas   | Eric      | Oise        | Citroen | C3     | Noir    |
 | EF 789 GH | Henri   | Valérie   | Nord        | Citroen | C4     | Rouge   |
 +-----------+---------+-----------+-------------+---------+--------+---------+
filter : 2-

fct_sql_stat tableau @result : création d'un tableau contenant le résultat de chaque colonne

nom
     1 Dupont
     2 Henri
     1 Lucas
     1 Martin
     1 Olivier

prenom
     1 Catherine
     2 Eric
     1 Michel
     1 Philippe
     1 Valérie

departement
     1 Eure
     1 Nord
     1 Oise
     3 Paris

marque
     3 Citroen
     2 Peugeot
     1 Renault

modele
     2 308
     1 C3
     2 C4
     1 Clio

couleur
     3 Blanc
     2 Noir
     1 Rouge

fct_column @result -> $result : affiche en colonne du tableau @result 
+-----------+-------------+-------------+-----------+--------+---------+
| nom       | prenom      | departement | marque    | modele | couleur |
+-----------+-------------+-------------+-----------+--------+---------+
| 1 Dupont  | 1 Catherine | 1 Eure      | 3 Citroen | 2 308  | 3 Blanc |
| 2 Henri   | 2 Eric      | 1 Nord      | 2 Peugeot | 1 C3   | 2 Noir  |
| 1 Lucas   | 1 Michel    | 1 Oise      | 1 Renault | 2 C4   | 1 Rouge |
| 1 Martin  | 1 Philippe  | 3 Paris     |           | 1 Clio |         |
| 1 Olivier | 1 Valérie   |             |           |        |         |
+-----------+-------------+-------------+-----------+--------+---------+
```

