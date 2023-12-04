# ecosprint

Cette page contiens quelques idée concernant le dévellopement d'un type de véhicule 20-50 plus éfficace qu'une voiture tout en ne pénalisant pas trop ni le temps de trajet ni le confort.

# Le concept
![image](https://github.com/nathmo/velomobile/assets/15912256/69da165f-4358-4585-8511-32d21728ae27)

Selon un [rapport de l'UE](https://climate.ec.europa.eu/eu-action/transport/road-transport-reducing-co2-emissions-vehicles_en), les voitures personnelles émmettent 15% des émmissions de CO2 de l'Union européene.
Ce projet vise à explorer une piste pour réduire celles-ci.
Pour comprendre l'origine du problème il faut se penser sur le fonctionnement énergétique d'une voiture. En effet, selon newton, dans un monde idéal un objet en mouvement tend à rester en mouvement.
hors dans la vie si laisse rouler une balle elle finira par s'arreté à cause des pertes. Pour une voiture c'est la même chose.
La première source de perte c'est l'air, en effet plus on circule vite, plus la résistance de l'air augmente

$$F=\frac{1}{2}\rho v^2 c_d A$$
$$A \text { la surface frontale du véhicule en  }[m^{2}]$$
$$c_d \text {le coéfficient de trainé (petit nombre pour exprimer un corp aérodynamique)}$$
$$v \text {la vitesse du véhicule en [m/s]}$$
$$\rho \text {la densité de l'air ~1.2 }() [Kg/m^{3}])$$

si on veux réduire les perte il faut que le résultat de cette équation sois aussi petit que possible. 
Pour cela nous pouvons réduire 3 chose. Le coeeficient de trainé, la surface frontale et la vitesse.
Hors pour la vitesse il s'agit d'un compromis car certe allé plus lentement réduis les dégat en cas d'accident il rend aussi le trajet plus long.
C'est pourquoi je me suis concentré sur la réduction du coeeficient de trainé et de l'aire frontale.

quelques exemple de [coeeficient de trainé](https://en.wikipedia.org/wiki/Drag_coefficient) pour comparaison. 

![image](https://github.com/nathmo/velomobile/assets/15912256/6cf3151b-0b7a-4441-be17-9ceede0f71e5)

je vise un coeefficient de 0.1-0.2 avec une surface frontale de 0.5 m^2 donc un total $c_dA$ de 0.05 m^2 (10 fois moins que celui d'une [voiture](https://en.wikipedia.org/wiki/Automobile_drag_coefficient))


![image](https://github.com/nathmo/velomobile/assets/15912256/c301caab-7291-426c-9b6d-bded240d8281)

J'en suis arrivé a une architecture avec deux passagé allongé l'un derrière l'autre pour obtenir une forme pointue et allongé avec une surface frontale minimale.


Ma la réalité pratique est plus compliqué qu'une simple équation.
Il faut tenir compte de la durée et de la distance à parcourir, du cadre légal, du confort des passagé, des apprioris, des contraintes de cout, de la tenue de route, du stockage de l'energie, de la recyclabilité, ...

c'est pourquoi je tiens à pouvoir dévelloper tout ces point pour arriver a plus qu'un simple concept rendu par ordinateur mais a un vrai prototype viable commercialement qui permettrait réellement de réduire l'impacte des transport personnel sur le climat.

# Challenge légaux

# Challenge technique

### Système de direction

### Système de freinage

### Propulsion

### Suspension

### Controle de la temperature

### Position du passagé et du pilote

### Système de commande

### Pilote automatique ?

### Canopé et carrosserie

### Cout de fabrication

# Challenge psychosociaux

### un engin qui soit beau et désirable

### biais d'appriori

### prix de vente







