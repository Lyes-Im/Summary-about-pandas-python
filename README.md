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
- Pour la <ins>création d'une nouvelle colonne</ins> 'col' avec les valeurs contenue dans une varibale 'var' **DF_name['col'] = var** <br>
- Pour extraire <ins>une ou plusieurs lignes </ins> d'un **DataFrame**, on utilise la fonction **loc[index]** / **DF.loc[[index1, index2], ['col1', 'col2']]** <br>
- La méthode **iloc** permet <ins>d'indexer</ins> un **DataFrame**, c'est-à-dire en ne renseignant que les indexes numériques des lignes et colonnes. Ceci permet d'utiliser le slicing sans contraintes (Exemple : **DF.iloc[0:4, 0:3]**)<br>
- Nous pouvons utiliser **l'indexation conditionnelle** pour <ins>extraire les lignes</ins> d'un Dataframe qui vérifient <ins>une condition donnée</ins> ou <ins>stocker</ins> quelques informations en relation avec cette condition. Voici la syntaxe : **df.loc[df['col 2'] == 3]**.<br>
- Une colonne d'un **DataFrame** peut être parcourue comme une liste dans une boucle for (Exemple : for indice in DF['total_amt']: ).<br>
- La méthode **describe** d'un DataFrame <ins>retourne un résumé des statistiques descriptives (min, max, moyenne, quantiles,..) de ses variables quantitatives</ins>.
C'est donc un outil très utile pour une première visualisation du type et de la distribution de ces variables.<br>
- Pour <ins>analyser les variables catégorielles</ins>, il est préférable de commencer par utiliser la méthode **value_counts** qui renvoie le nombre d'occurrences pour chaque modalité de ces variables. La méthode value_counts ne peut pas s'utiliser directement sur un DataFrame mais que sur les colonnes du DataFrame qui sont des objets de la classe pd.Series ( Ex: DataFrame_name['colonne_spécifier'].value_counts(). )
  # 1. Nettoyage d'un DataSet :<br>
 Les méthodes de la classe **DataFrame** utiles au nettoyage d'un dataset. Ces méthodes peuvent se regrouper dans trois catégories différentes :

- <ins>Gestion des doublons</ins> (méthodes **duplicated** et **drop_duplicates**).
- <ins>Modification des éléments</ins> d'un DataFrame (méthodes **replace**, **rename** et **astype**).
- <ins>Opérations sur les valeurs</ins> d'un DataFrame (méthode **apply** et clause **lambda**).<br>
### 1.1 Gestion des doublons dans un DataFrame :
Quand nous découvrons un jeu de données il est <ins>très important de vérifier</ins> dès le départ qu'il **n'y ait pas de doublons** afin d'éviter des erreurs dans les calcules statistiques.
<ins>La présence de doublons</ins> se vérifie à l'aide de la méthode **duplicated** d'un DataFrame (DF.duplicated()), qui nous dit pour chaque ligne si elle est un doublon (boolean).
- nous pouvons lui appliquer la méthode **sum** pour <ins>compter le nombre de doublons</ins> : **df.duplicated().sum()**
- La méthode d'un DataFrame permettant de supprimer les doublons est **drop_duplicates** et sa syntaxe est : **drop_duplicates(subset = ['col_spécifier'], keep, inplace)**
### 1.2 Modification (transformations) des éléments d'un DataFrame : 
- La méthode **replace** permet de <ins>remplacer une ou plusieurs valeurs d'une colonne</ins> d'un DataFrame et sa syntaxe : **replace(to_replace = [], value=[])**.
- On peut renommer les colonnes d'un DataFrame grace à la fonction **rename** qui prend en paramètre un **dictionnaire** et la syntaxe : **df = df.rename(dictionnaire, axis = 1)**
- On peut aussi <ins>modifier le type d'une colonne</ins> à l'aide de la fonction **astype** qui prend en argument un dictionnaire dont les clés sont les noms des colonnes concernées et les valeurs sont les nouveaux types à assigner et la syntaxe :<br>
   ```df['colonne'] = df['colonne'].astype('int')```<br>
  ```dictionnaire = {'col_1': 'int', 'col_2': 'float' } df = df.astype(dictionnaire)``` <br>
- Il est souvent intéressant de <ins>modifier ou agréger les informations des colonnes</ins> d'un **DataFrame** à l'aide d'une **opération** ou **d'une fonction**. Ces opérations peuvent être tout type de fonction qui prend en argument une colonne. <ins>La méthode permettant d'effectuer une opération sur une colonne</ins> est la méthode **apply** d'un DataFrame dont l'en-tête est : ```apply(func, axis)```
- Pour calculer **la somme** de toutes les **lignes** on utilise ```axis = 1```. Ex : ```df_lines = df.apply(np.sum, axis = 1)``` || ```df_columns = df.apply(np.sum, axis = 0)```
- - ```df['colonne'].apply(func)``` : Appliquer une fonction à chaque valeur d'une colonne.
- La méthode **apply** est très puissante lorsqu'elle est associée à **une fonction lambda**.
- En Python, le mot clé lambda est utilisé pour définir une fonction anonyme : <ins>une fonction déclarée sans nom</ins>.
- Une fonction lambda peut <ins>prendre n'importe quel nombre d'arguments</ins>, mais ne peut avoir qu'<ins>une seule expression</ins> et voici sa syntaxe :  ```lambda arguments: expression```.



  
  







