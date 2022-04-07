# Rapport d'evaluation du modèle CVMNet

## Architecture du modèle
On considère une pose par un vecteur des positions des articulations du squelette. On simplifie le squelette à un nombre d'articulations J=17.
Une séquence de pose est une suite de vecteurs décrivant les poses du squelette en fonction du temps. On considère en comme donnée d'entrée du modèle une séquence de poses en 2D qu'on note ![P2D](https://render.githubusercontent.com/render/math?math=P_{2D}) et comme donnée résultat une séquence de pose en 3D ![P2D](https://render.githubusercontent.com/render/math?math=P_{3D}).
L'objectif du modèle est de calculer la transformation 2D vers 3D du séquence de pose de longueur T :
<center>
![f](https://render.githubusercontent.com/render/math?math=P_{3D}=f(P_{2D}))
</center>

![P2D](https://render.githubusercontent.com/render/math?math=P_{2D}) est de dimension [1,T,2xJ] et ![P3D](https://render.githubusercontent.com/render/math?math=P_{3D}) est de dimension [1,T,3xJ]

Voici l'architecture du modèle utilisé pour réaliser cette tâche:
<center>
![Alt](network-architecture.png)

*Figure1: Architecture du modèle d'estimation de poses 3D*
</center>

## Evaluation avec la base de données Human3.6m

On évalue le modèle en utilisant le Protocol#1 du benchmark Human3.6m. Le tableau Table 1 ci-après représente les résultats de l'évaluation.

Modèles | Directions | Discussion | Eating | Greeting | Phoning | Photo | Posing | Purchases | Sitting | SittingDown | Smoking | Waiting | WalkDog | Walking | WalkTogether | Average |
:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
CVMNet (1 bloc) | 85.25 | 129.41 | 109.17 | 101.22 | 117.17 | 137.31 | 86.12 | 293.37 | 152.75 | 248.98 | 119.87 | 105.45 | 261.62 | 87.20 | 87.81 | 142.47 |
CVMNet (2 blocs) | 89.18 | 121.00 | 135.62 | 101.21| 130.79 | 137.12 | 85.83 | 226.98 | 191.31 | 261.97 | 133.23 | 103.17 | 218.35 | 83.93 | 86.03 | 141.25 |
MotioNet | 45.48 | 51.28 | 49.43 | 51.91 | 52.58 | 66.46 | 50.59 | 48.46 | 55.90 | 64.25 | 53.79 | 52.84 | 58.85 | 49.99 | 48.25 | 53.47 |

###Quelques résultats graphiques
Action | Vérité terrain | Motionet | CVMNet(1bloc) | CVMNet(2blocs) |
|:-----:|:-----:|:-----:|:-----:|:-----:|
|Directions|![Vérité terrain](./demos/gt/s9_directions.gif  "Ground truth")|![MotioNet](./demos/motionet/s9_directions.gif  "Motionet")|![CVMNet1](./demos/temporalposesmodel_1/s9_directions.gif  "CVMNet1")|![CVMNet2](./demos/temporalposesmodel_2/s9_directions.gif  "CVMNet2")|
|Greeting|![Vérité terrain](./demos/gt/s9_greeting.gif  "Ground truth")|![MotioNet](./demos/motionet/s9_greeting.gif  "Motionet")|![CVMNet1](./demos/temporalposesmodel_1/s9_greeting.gif  "CVMNet1")|![CVMNet2](./demos/temporalposesmodel_2/s9_greeting.gif  "CVMNet2")|
|Posing|![Vérité terrain](./demos/gt/s11_posing.gif  "Ground truth")|![MotioNet](./demos/motionet/s11_posing.gif  "Motionet")|![CVMNet1](./demos/temporalposesmodel_1/s11_posing.gif  "CVMNet1")|![CVMNet2](./demos/temporalposesmodel_2/s11_posing.gif  "CVMNet2")|
|Walking|![Vérité terrain](./demos/gt/s11_walking.gif  "Ground truth")|![MotioNet](./demos/motionet/s11_walking.gif  "Motionet")|![CVMNet1](./demos/temporalposesmodel_1/s11_walking.gif  "CVMNet1")|![CVMNet2](./demos/temporalposesmodel_2/s11_walking.gif  "CVMNet2")|