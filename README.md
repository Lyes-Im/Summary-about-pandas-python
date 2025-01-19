# cheat-sheet-pandas-
**1. Importation de la bibliothèque pandas :**  <br> import pandas as pd <br>
**2. Récap sur les DataFrame :**<br>
**La différence entre la classe DataFrame et Numpy :**<br>
La classe DataFrame contient davantage de méthodes pour la manipulation et le pré-traitement de bases de données, tandis que NumPy se spécialise plutôt dans le calcul optimisé. <br>
**L'importation des données CSV dans un DataFrame :** <br>
df = pd.read_csv('filepath_or_buffer' , sep = ',', header = 0, index_col = 0 ... )<br>
**header :** Le numéro de la ligne qui contient les noms des colonnes. Si par exemple les noms de colonnes sont renseignés dans la première ligne du fichier .csv, alors il faut spécifier header = 0. Si les noms ne sont pas renseignés, on mettra header = None. <br>
**index_col :** Le nom ou numéro de la colonne contenant les indices de la base de données. Si les entrées de la base sont indexées par la première colonne, il faudra renseigner index_col = 0. Alternativement, si les entrées sont indexées par une colonne qui porte le nom "Id", on pourra spécifier index_col = "Id". <br>
### Exploration d'un DataSet grâce à la classe DataFrame : <br>
Les principales méthodes de la classe DataFrame qui vont nous permettre de faire une rapide analyse de notre jeu de données sont:<br>
- La fonction **head()** Pour afficher les premières lignes du **DataFrame** par défaut, elle affiche les 5 premières lignes.<br>
- La fonction **tail()** permet d'afficher les dernières lignes du **DataFrame**.<br>
- Pour <ins>recupérer le nom des colonnes</ins> d'un **DataFrame**, on utilise **Objet_DF.columns[..]**<br>
- Pour afficher <ins>les dimensions</ins> de notre **DataFrame** on utilise l'attribut **shape**.<br>  
- Pour <ins>l'extraction des colonnes </ins> d'un **DataFrame**, on utilise **new_DF = df[["col1","col2"]]** <br>
- Pour extraire <ins>une ou plusieurs lignes </ins> d'un **DataFrame**, on utilise la fonction **loc[index]** / **DF.loc[[index1, index2], ['col1', 'col2']]** <br>
- La méthode **iloc** permet <ins>d'indexer</ins> un **DataFrame**, c'est-à-dire en ne renseignant que les indexes numériques des lignes et colonnes. Ceci permet d'utiliser le slicing sans contraintes (Exemple : **DF.iloc[0:4, 0:3]**)<br>
- Nous pouvons utiliser **l'indexation conditionnelle** pour <ins>extraire les lignes</ins> d'un Dataframe qui vérifient <ins>une condition donnée</ins> ou <ins>stocker</ins> quelques informations en relation avec cette condition. Voici la syntaxe : **df.loc[df['col 2'] == 3]**.





