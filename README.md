# ecosprint

Cette page contiens quelques idée concernant le dévellopement d'un type de véhicule 20-50 plus éfficace qu'une voiture tout en ne pénalisant pas trop ni le temps de trajet ni le confort.

# Le concept
![image](https://github.com/nathmo/velomobile/assets/15912256/69da165f-4358-4585-8511-32d21728ae27)

Selon un [rapport de l'UE](https://climate.ec.europa.eu/eu-action/transport/road-transport-reducing-co2-emissions-vehicles_en), les voitures personnelles émmettent 15% des émmissions de CO2 de l'Union européene.
Ce projet vise à explorer une piste pour réduire celles-ci.
Pour comprendre l'origine du problème il faut se penser sur le fonctionnement énergétique d'une voiture. En effet, selon newton, dans un monde idéal un objet en mouvement tend à rester en mouvement.
hors dans la vie si laisse rouler une balle elle finira par s'arreté à cause des pertes. Pour une voiture c'est la même chose.
La première source de perte c'est l'air, en effet plus on circule vite, plus la résistance de l'air augmente

$$F=\frac{1}{2}\rho v^2 c_d A \text{test}$$

$$A \text{ la surface frontale du véhicule en  } [m^{2}]$$

$$c_d \text{ le coéfficient de trainé (petit nombre pour exprimer un corp aérodynamique)}$$

$$v \text{ la vitesse du véhicule en} [m/s]$$

$$\rho \text{ la densité de l'air ~1.2 } [Kg/m^{3}])$$

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

### Article lié

[OETV](https://www.fedlex.admin.ch/eli/cc/1995/4425_4425_4425/fr)

![image](https://github.com/nathmo/velomobile/assets/15912256/c564c04e-94d6-462b-a00d-b0bd0a3e8fd5)

![image](https://github.com/nathmo/velomobile/assets/15912256/3a6b388c-43fd-4d2b-9ade-3ccf02df0595)

![image](https://github.com/nathmo/velomobile/assets/15912256/c503824d-82cf-49bc-85a1-f93463c2f00d)

![image](https://github.com/nathmo/velomobile/assets/15912256/aa5f8bf8-7bbd-470b-8f25-ded7966d57d4)

![image](https://github.com/nathmo/velomobile/assets/15912256/28e45b57-2d8a-47bd-a569-32c09cdc40f5)

![image](https://github.com/nathmo/velomobile/assets/15912256/dc0ba641-09b1-4ee0-a253-615cc65d2711)

![image](https://github.com/nathmo/velomobile/assets/15912256/37979023-b760-404c-8964-2215acbbf7f0)

![image](https://github.com/nathmo/velomobile/assets/15912256/ffcb9ad8-eadc-4d9c-bbcd-4ce880ca53b4)

![image](https://github.com/nathmo/velomobile/assets/15912256/ab72104a-839f-4854-9e9f-b5751ec8c61d)

![image](https://github.com/nathmo/velomobile/assets/15912256/704a5a54-7d4f-4d6e-a082-b51ffc96a9a3)

![image](https://github.com/nathmo/velomobile/assets/15912256/4b00e05e-6621-44f9-adaa-c7793b374c3f)

![image](https://github.com/nathmo/velomobile/assets/15912256/031bebf9-73d7-45fe-b542-6581731a37eb)

![image](https://github.com/nathmo/velomobile/assets/15912256/40d31198-f100-4af6-9258-a4425c3d6075)

![image](https://github.com/nathmo/velomobile/assets/15912256/f036b25a-207b-4b5c-8353-3796c5d8a01c)

![image](https://github.com/nathmo/velomobile/assets/15912256/a8c01b5b-a5e8-48c7-80d2-686f5e6f683f)




# Challenge technique

### Système de direction
Système différentiel à l'image des véhcule a chenilette ou les roues d'un coté tourne plus vite que l'autre.
[un article qui compare les directions classique avec une direction différentielle](https://www.researchgate.net/publication/261192572_Differential_Speed_Steering_Control_for_Four-Wheel_Independent_Driving_Electric_Vehicle?_tp=eyJjb250ZXh0Ijp7ImZpcnN0UGFnZSI6Il9kaXJlY3QiLCJwYWdlIjoiX2RpcmVjdCJ9fQ)

![image](https://github.com/nathmo/velomobile/assets/15912256/950e9bf2-ab61-462a-afa6-c7c3f08e56df)

ce système pose quelque challenge en terme de controle mais permet un chassis plus simple et donc plus leger et robuste.

### Système de freinage
frein régénératif, limite l'usure des freins et améliore l'autonomie.
frein a disque standard de vélo. 4 roue donc redondance.

### Transmission
##### transmission éléctrique 
routage simplifié, moins de pièce mobile, légèrement moins bonne éfficacité qu'un système directe à chaine.
simplicité de rendre le vehicule 4wd
##### transmission mécanique à chaine
routage compliqué avec 4 roues, nécéssite un différientielle.
### Propulsion
moteur éléctrique de faible puissance (100-500 W)
peut onereux, version 4x4 avec grande redondance donc moins d'entretiens et meilleures tenu de route.
- https://fr.aliexpress.com/item/1005004884524853.html
- https://fr.aliexpress.com/item/1005005874887142.html

### Suspension
en cours de réflexion. système actif ou passif ? architecture ? complexité ? comportement dans les virage ? encombrement ?

### Controle de la temperature
pompe à chaleur ?
système évaporatif a eau + chauffage dans le manche de commande + siège ?

mientiens de la temperature des batteries ?

### Ergonomie et Position du passagé et du pilote
![image](https://github.com/nathmo/velomobile/assets/15912256/cdb40655-ad67-43a8-9215-9289cb098ee9)

communication entre les personne ? mirroir ?

### Système de commande
volant ? joystick ?

### Pilote automatique ?


### Canopé et carrosserie

### Cout de fabrication

### lumière, signalisation
ruban de led qui permet de faire a la fois feux de position et clignotant.
phare avant LED ?

# Challenge psychosociaux

### un engin qui soit beau et désirable

### biais d'appriori

### prix de vente

# Autre
### Train
assimilé a un velo, trajet hybride, d'une ville a l'autre en train, last mile en ecosprint



