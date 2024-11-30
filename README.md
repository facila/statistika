# Fonction de statistiques d'une table mysql

```
Comptage du nombre d'éléments de chaque colonne

fct_sql_stat.pl -h : aide
fct_sql_stat.pl -e : exemple
fct_sql_stat.pl "$mysql" 2-

utilisation du module fct_sql_stat.pm
options :
- filter    : filtre des colonnes à prendre en compte
- ref_stat  : tableau initial des valeurs pour trier
- init_stat : pour initialiser les valeurs à partir du tableau ref_stat
- ref_lg    : tableau des longueurs des colonnes
- init_lg   : pour calculer puis retourner les longueurs

filter : 2-
mysql  : 
+-----------+---------+-----------+-------------+---------+--------+---------+
| numero    | nom     | prenom    | departement | marque  | modele | couleur |
+-----------+---------+-----------+-------------+---------+--------+---------+
| AB 123 CD | Henri   | Philippe  | Paris       | Renault | Clio   | Blanc   |
| AB 456 CD | Martin  |           | Paris       | Citroen | C4     | Blanc   |
| AB 789 CD | Dupont  | Eric      | Paris       | Peugeot | 308    | Noir    |
| EF 123 GH | Olivier | Catherine | Eure        | Peugeot | 308    | Blanc   |
| EF 456 GH | Lucas   | Eric      | Oise        | Citroen | C3     | Noir    |
| EF 789 GH | Henri   | Valérie   | Nord        | Citroen | C4     | Rouge   |
+-----------+---------+-----------+-------------+---------+--------+---------+

fct_sql_stat tableau @result : création d'un tableau intermédiaire contenant le résultat de chaque colonne
nom     5/6
Henri     2
Olivier   1
Lucas     1
Martin    1
Dupont    1

prenom    4/5
Eric        2
Catherine   1
Philippe    1
Valérie     1

departement 4/6
Paris         3
Eure          1
Oise          1
Nord          1

marque  3/6
Citroen   3
Peugeot   2
Renault   1

modele 4/6
C4       2
308      2
Clio     1
C3       1

couleur 3/6
Blanc     3
Noir      2
Rouge     1

fct_column @result -> $result : affichage en colonne du tableau @result 
+-------------+---------------+-----------------+-------------+------------+-------------+
| nom     5/6 | prenom    4/5 | departement 4/6 | marque  3/6 | modele 4/6 | couleur 3/6 |
+-------------+---------------+-----------------+-------------+------------+-------------+
| Henri     2 | Eric        2 | Paris         3 | Citroen   3 | C4       2 | Blanc     3 |
| Olivier   1 | Catherine   1 | Eure          1 | Peugeot   2 | 308      2 | Noir      2 |
| Lucas     1 | Philippe    1 | Oise          1 | Renault   1 | Clio     1 | Rouge     1 |
| Martin    1 | Valérie     1 | Nord          1 |             | C3       1 |             |
| Dupont    1 |               |                 |             |            |             |
+-------------+---------------+-----------------+-------------+------------+-------------+

