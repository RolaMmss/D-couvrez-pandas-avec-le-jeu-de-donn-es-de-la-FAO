# D-couvrez-pandas-avec-le-jeu-de-donn-es-de-la-FAO
Découvrez la librairie pandas avec le jeu de données de la FAO

Activité guidée : Découverte de Pandas

Pandas - Matplotlib - Seaborn

Mise en situation : 

Félicitations, vous venez de décrocher votre premier job au sein de la FAO (Organisation des Nations Unies pour l’alimentation et l’agriculture).

Votre première mission est de réaliser une étude sur la démographie et la nutrition.

- Étape n°0 : se former sur pandas et préparer son environnement

    Commencez par revoir ou apprendre les concepts principaux de Pandas avant de vous lancer dans le projet, rendez-vous ici. 

    Pour ce projet, je vous conseille de travailler sur votre environnement conda dédié à la data science et d’utiliser un jupyter notebook pour répondre aux questions.

- Étape n°1 : Récupérer les jeux de données

    Rendez-vous sur le site de la FAO dans la section FAOSTAT puis dans la catégorie bilans alimentaires.

    Votre objectif est d’extraire 3 jeux de données (fichiers csv) avec les informations suivantes :
    les produits d'origine animale
    les produits d’origine végétale 
    la population de chaque pays

    Vous devez récupérer la liste de tous les produits, par exemple, pour les produits animales : viande bovine, poulet, etc.

    Sélectionnez les années 2018 et 2019 et récupérez le jeu de données en anglais.

    Pour les data sets relatifs aux produits, sélectionnez les éléments suivants (4):
    disponibilité alimentaire en kg/personne/jour
    disponibilité alimentaire en kcal/personne/jour
    disponibilité alimentaire en protéines/personne/jour
    disponibilité alimentaire en matière grasse/personne/jour

    Vous aurez donc 3 fichiers csv. Importez les données avec Pandas afin de créer 3 DataFrames : df_anim, df_veg et df_pop.

    Avant de vous lancez dans le code, prenez du temps pour comprendre les données et la mission de la FAO. Pour cela : explorez la section définitions et standards

Étape n°2 : Nettoyage et préparation des données

    Explorez votre jeu de données grâce à des méthodes de la librairie Pandas. Les méthodes utilisées doivent vous permettre de répondre aux questions suivantes :

    Nettoyer les titres de colonnes :
    Supprimer les espaces au début et à la fin des titres (s’il y en a)
    Remplacer les espaces par des underscores (ceux se situant entre les mots)
    Tout mettre en minuscule
    Quelle sont les dimensions des jeux de données ?
    A quoi ressemblent les 5 premières lignes de mes jeux de données ?
    Pour les datasets df_anim et df_veg, ajoutez une colonne ‘type’ qui prendra respectivement une valeur ‘animal’ et ‘vegetal’. Une fois cette étape effectuée, regroupez les deux jeux de données en 1 et appelez ce DataFrame product. Attention à bien comprendre la structure des données pour utiliser la bonne méthode.
    Transformez df_pop afin de ne garder que le code du pays, le pays, l’année et la population. Renommer la colonne ‘value’ en ‘pop_1000_hab’.
    Transformez products afin de ne garder que les colonnes area_code_(fao), area, element, item, year, type, unit, value.
    Fusionnez df_pop avec products et nommez ce DataFrame df. Afin de fusionner ces jeux de données vous devez identifier les clés primaires. Renommer les colonnes comme sur la capture d’écran ci-dessous.
    Note : ajouter la population à la base de données créera de la redondance dans la bdd mais simplifiera les calculs pour les questions suivantes. Ne pas supprimer df_pop.

    Maintenant que nous avons un DF unique, il sera plus facile de l’explorer :

    Quelles sont les types de données de chaque colonne ?
    Combien y-a t’il de valeurs manquantes par variable ?
    Est-ce qu’il y a des valeurs aberrantes ? (population négative, etc.) Utilisez un récapitulatif statistique pour répondre à cette question.
    Affichez les valeurs uniques de la colonne area
    Gardez uniquement les informations relatives aux pays (supprimez les zones géographiques ou économiques) Note : en fonction de votre méthode d’importation de données cette étape est facultative.
    Modifiez votre jeu de données afin que les informations soient indexées par area_code, area, year, pop_1000_hab, type et item. Les valeurs de la colonne element doivent être séparées dans des colonnes différentes. Recherchez sur internet la différence entre les formats long et les formats wide. Pour réussir cette étape creuser la méthode pivot_table. Il est préférable d’appliquer la méthode reset_index() après avoir utilisé la méthode précédente.
    Faire du nettoyage dans le nom des colonnes
    À ce stade votre jeu de données doit ressembler à cela :

    Notez bien la dimension du jeu de données. Si tout s'est bien déroulé vous devez avoir le même resultat, sinon revoyez les étapes précédentes.

    Créez des masques afin d’afficher un DataFrame qui ne contient que l’année 2018
    Nous allons ajouter une nouvelle colonne à notre jeu de données : la zone géographique. Pour cela rendez-vous sur le site de la FAO, votre objectif est de télécharger des nouveaux datasets pour ajouter les zones suivantes à votre jeu de données : 'eastern_africa', 'middle_africa', 'northern_africa', 'southern_africa', 'western_africa', 'northern_america', 'central_america', 'caribbean', 'south_america', 'central_asia', 'eastern_asia', 'southern_asia', 'south_eastern_asia', 'western_asia', 'eastern_europe', 'northern_europe', 'southern_europe', 'western_europe', 'australia_new_zealand', 'melanesia', 'micronesia', 'polynesia'


Étape n°3: Exploration
  Lorsqu’aucune précision n’est donnée, veuillez répondre en utilisant l’année la plus récente :

  Quelle est la médiane de la variable fat_supply_quantity_(g/capita/day) ? Q1 ? Q3 ? La moyenne ? L’écart type ? (il existe une méthode pour visualiser toutes ces informations en même temps). Interprétez ces mesures statistiques dans une phrase.
  Visualisez la distribution des données numériques à l’aide d’un histogramme. Utilisez une boucle si nécessaire. Si certaines variables contiennent des valeurs extrêmes vous pouvez effectuer une transformation sur vos données. (En logarithmes par exemple)
  Quelle est la population de l’Ukraine en 2018 ? L’output doit être un int (pas un DataFrame)
  Quels sont les 10 pays les plus peuplés ?
  Quelle est la population mondiale en 2018 ? En 2019 ? Est-ce que ce chiffre correspond à la réalité ? Menez votre enquête et faites les corrections nécessaires en cas de problème. Contrôlez vos données grâce à ce site. (Si l’erreur est de l’ordre de quelques dizaines de millions, c’est peut-être la méthode de calcul mais si c’est supérieur à 1 milliard, il y a une erreur dans la façon dont vous avez récupérer les données)
  Pour quels pays dispose-t-on du moins d’informations (nombre de valeurs manquantes) ? Donnez-en 5.
  Créez une nouvelle colonne taux_croissance_pop_18_19 avec le taux de variation de la population entre 2018 et 2019 dans chaque pays. Affichez les 5 pays avec le taux de croissance démographique le plus élevé.
  Quel est le taux de croissance moyen en fonction de la zone géographique ?
  Calculez la disponibilité de nourriture totale par pays et par année, en kcal et kg de protéines. Attention aux unités de mesure !
  Calculez le ratio énergie/poids de chaque produit et pays. Vous devriez vous apercevoir qu’étonnement, ces informations varient en fonction du pays. Pour pallier ce problème, calculez la moyenne de ce ratio pour chaque aliment.  Attention à bien gérer les valeurs égales à 0. Vérifiez la cohérence de votre calcul en comparant le résultat avec l’apport calorique d’un œuf.
  À l’instar de la question précédente, calculez le pourcentage de protéine de chaque aliment. Vérifiez votre résultat en le comparant avec l’apport en protéines d’un œuf.
  Quels sont les 10 aliments les plus caloriques ? Utiliser un diagramme à barres pour visualiser les résultats. À cette étape, vous pouvez vous rendre compte qu’il y a des valeurs aberrantes. Mener votre enquête et corriger le tir.
  Quels sont les 10 aliments les plus riches en protéines ? Utiliser un diagramme à barres pour interpréter les résultats.
  Créez une boîte à moustache de la quantité de nourriture disponible par habitant en kcal par zone géographique. Afin d’optimiser l’affichage modifier les éléments nécessaires si besoin :
  Mettez un titre
  La taille du graphique
  Étiquettes des axes, 
  Les axes 
  la couleur en fonction de chaque boite à moustache
  Effectuez ce graphique en utilisant la librairie de visualisation seaborn. Interpréter ce graphique.
  Avec la disponibilité alimentaire combien d’être humains pourrait-on nourrir ? et avec la disponnibilité alimentaire en végétaux ? Pour répondre à cette question vous avez besoin d’estimer les besoins alimentaires moyens d’une personne, effectuer une recherche pour trouver cette information. Interpréter vos résultats. Exprimer vos résultats sous la forme de % de la population mondiale.
  Bonus : Avec la nourriture destinée aux animaux combien d’humains pour être nourris ? (Vous devez récupérer plus d’informations sur le site de la FAO)

