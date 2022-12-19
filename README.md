# CNN-MammographyClassification
# 1	Introduction 
Un réseau neuronal convolutif (ConvNet/CNN) est un algorithme d'apprentissage en profondeur qui peut prendre en compte une image d'entrée, attribuer une importance (poids et biais apprenables) à divers aspects/objets de l'image et être capable de les différencier les uns des autres.
Les CNN désignent une sous-catégorie de réseaux de neurones et sont à ce jour un des modèles de classification d’images réputés être les plus performant. Leurs mode de fonctionnement est à première vue simple : l’utilisateur fournit en entrée une image sous la forme d’une matrice de pixels.(Deux dimensions pour une image en niveaux de gris) 

Contrairement à un modèle MLP (Multi Layers Perceptron) classique qui ne contient qu’une partie classification, l’architecture du Convolutional Neural Network dispose en amont d’une partie convolutive et comporte par conséquent deux parties bien distinctes :

•	Une partie convolutive : Son objectif final est d’extraire des caractéristiques propres à chaque image en les compressant de façon à réduire leurs taille initiale.
L’image fournie en entrée passe à travers une succession de filtres, créant par la même occasion de nouvelles images appelées cartes de convolutions. Enfin, les cartes de convolutions obtenues sont concaténées dans un vecteur de caractéristiques appelé code CNN.

•	Une partie classification : Le code CNN obtenu en sortie de la partie convolutive est fourni en entrée dans une deuxième partie, constituée de couches entièrement connectées appelées perceptron multicouche (MLP pour Multi Layers Perceptron). Le rôle de cette partie est de combiner les caractéristiques du code CNN afin de classer l’image.

# 2	Vérification de la base d’image
Nous allons d’abord vérifier la base des images et supprimer les images endommagées par le simple bout de code présent ci-dessus

# 3 Création des répertoires,compter et afficher les images
D’abord nous allons charger et les images de notre base. Nous allons utiliser la classe  ImageDataGenerator  peut être utilisé pour augmenter les données d’image avec beaucoup de pré-traitement intégré tels : le mise a l’échelle, le décalage, la rotation, le bruit, le blanchiment, etc. En ce moment, nous utilisons simplement l’attribut rescale pour mettre à l’échelle les valeurs du tenseur d’image entre 0 et 1.
Nous pouvons spécifier :

•	les noms de classe ;
•	le target_size, qui nous permet de redimensionner les images sources à une taille uniforme de 200 x 200, quelle que soit la taille originale de l’image ;
•	la taille du lot. Si vous laissez batch_size non spécifié, par défaut, il sera fixé à 32.


Lorsque vous exécutez ce code, la fonction Keras parcourt le répertoire de premier niveau, trouve tous les fichiers image et les étiquette automatiquement avec la classe appropriée.

Ensuite nous allons utiliser les bibliothèques  matplotlib.image  et  matplotlib.pyplot de python pour visualiser les images 


# 3 Création du modèle du réseau de neurone convolutive
Ensuite nous allons construire l’architecture de notre Model Convolutional Neural Network  CNN ..Elle est composée de : 
•	Couche de convolution (CONV) : Le rôle de cette première couche est d’analyser les images fournies en entrée et de détecter la présence d’un ensemble de features. On obtient en sortie de cette couche un ensemble de features maps 

•	Couche de Pooling (POOL) : La couche de Pooling est une opération généralement appliquée entre deux couches de convolution. Celle-ci reçoit en entrée les features maps formées en sortie de la couche de convolution et son rôle est de réduire la taille des images, tout en préservant leurs caractéristiques les plus essentielles. 
Nous allons utiliser Max Pooling qui fonctionne également comme un suppresseur de bruit .
•	La couche d’activation ReLU (Rectified Linear Units) : Cette couche remplace toutes les valeurs négatives reçues en entrées par des zéros. L’intérêt de ces couches d’activation est de rendre le modèle non linéaire et de ce fait plus complexe.
•	Couche Fully Connected (FC) :  Ces couches sont placées en fin d’architecture de CNN et sont entièrement connectées à tous les neurones de sorties . (Classificateur de réseaux neuronaux (ANN)).
•	Le flattening (mise à plat) :Cela consiste tout simplement à prendre la totalité des valeurs de nos matrices  calculées, et à les empiler, en vue de les exploiter dans la couche d’entrée d’un réseau de neurones.( aplatir la sortie 3D en 1D,)


# 4 	L’entrainement du modèle
L’étape suivante consiste à entrainer le modèle 

# 5 Evaluation du modèle 
La courbe bleue représente la précision sur les données d’entrainement, alors que l’orange représente la précision sur les données de test. On peut aussi voir la courbe de perte 

# 6	Matrice de confusion 
Dans le domaine de l'apprentissage automatique une matrice de confusion , également appelée matrice d'erreur, est une disposition de tableau spécifique qui permet de visualiser les performances d'un algorithme
 Chaque ligne de la matrice représente les instances d'une classe prédite tandis que chaque colonne représente les instances d'une classe réelle (ou vice versa). Le nom provient du fait qu'il permet de voir facilement si le système confond deux classes .
