# ecosprint

Cette page contiens quelques idée concernant le dévellopement d'un type de véhicule 20-50 plus éfficace qu'une voiture tout en ne pénalisant pas trop ni le temps de trajet ni le confort.

# Le concept
![image](https://github.com/nathmo/velomobile/assets/15912256/69da165f-4358-4585-8511-32d21728ae27)

Selon un [rapport de l'UE](https://climate.ec.europa.eu/eu-action/transport/road-transport-reducing-co2-emissions-vehicles_en), les voitures personnelles émmettent 15% des émmissions de CO2 de l'Union européene.
Ce projet vise à explorer une piste pour réduire celles-ci.
Pour comprendre l'origine du problème il faut se pencher sur le fonctionnement énergétique d'une voiture. En effet, selon newton, dans un monde idéal un objet en mouvement tend à rester en mouvement.
hors dans la vie si laisse rouler une balle elle finira par s'arreté à cause des pertes. Pour une voiture c'est la même chose.
La première source de perte c'est l'air, en effet plus on circule vite, plus la résistance de l'air augmente

$$F=\frac{1}{2}\rho v^2 c_d A \text{ }$$

$$A \text{ la surface frontale du véhicule en  } [m^{2}]$$

$$c_d \text{ le coéfficient de trainé (plus il est petit, plus le corp est aérodynamique)}$$

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


# Challenge technique

### Système de direction
https://en.wikipedia.org/wiki/Steering

##### approche différentiel
J'ai dabbord envisagé un Système différentiel à l'image des véhcule a chenilette ou les roues d'un coté tourne plus vite que l'autre.
[un article qui compare les directions classique avec une direction différentielle](https://www.researchgate.net/publication/261192572_Differential_Speed_Steering_Control_for_Four-Wheel_Independent_Driving_Electric_Vehicle?_tp=eyJjb250ZXh0Ijp7ImZpcnN0UGFnZSI6Il9kaXJlY3QiLCJwYWdlIjoiX2RpcmVjdCJ9fQ)

![image](https://github.com/nathmo/velomobile/assets/15912256/950e9bf2-ab61-462a-afa6-c7c3f08e56df)

ce système pose quelque challenge en terme de controle mais permet un chassis plus simple et donc plus leger et robuste.
Le hic de cette approche est que les roue sont en dérrapage pendant les virage et par conséquence le véhicule n'est pas maniable a "grande" vitesse (passé 10 kmh)
Pour des raisons de tenu de route cette approche doit être abandonné.

##### approche axe central
design similaire à certaine machine de chantier avec un axe centrale.
potentiellement plus simple mécaniquement. 
https://en.wikipedia.org/wiki/Articulated_vehicle
Après avoir lu quelques études sur la stabilité et les limites de ce système ainsi que des difficulté d'avoir un chassis articulé dans une bulle qui se veux aussi aérodynamique que possible cette approche à été mise de coté.

##### approche ackerman
similaire a la direction d'une voiture. semble mécaniquement compliqué et nécéssite beaucoup de pièce mais méthode prouvé qui fonctionne.

##### approche roue indépendante
chaque roue est monté sur un axe et peut etre tourné indépendament. pas forcement plus simple que l'approche ackerman mais à potentiellement certain avantage.

##### Dans la pratique
Après avoir fait quelques estimation de cout, je me suis rendu compte que le plus économique et le plus simple à entretenir sera d'utiliser des pièces déja utilisé dans d'autre véhicule.
Un bon candidant serais d'utilisé des fourche de vélo avec suspension à air. elle coute dans les ~30$ pièces et offre un pivot robuste pour la direction ainsi qu'une suspension.

### Système de contrôle de l'inclinaison
Comme le véhicule est relativement étroit par rapport a son centre de gravité, il faut faire attention à l'acceleration centrifuge pendant les virages qui pourrais renverser le véhicule.
A l'image d'une vélo ou d'une moto qui s'incline dans les virage pour que la force soit dirigé dans les roues, il faut que le véhicule puisse aussi s'incliner.
Comme nous avons une carroserie il est compliquer d'attendre du pilote de se pencher pour compenser cette effet mais il est possible d'utiliser la suspension pour s'incliné.
(voir suspension active et semi active à air)

### Sécurité

#### Harnais
ceintures de sécurité standard ? Harnais style avion de chasse ?

#### Protection contre les tonneaux 
Le chassis fait office de Roll cage pour proteger les occupants
#### airbags
prix ? fabricant ? fonctionnement ? capteurs ?

### Système de freinage
frein régénératif, limite l'usure des freins et améliore l'autonomie.
frein a disque standard de vélo. 4 roue donc redondance.

La encore, le but serais d'utiliser des pièces communes pour rendre le véhicule peu chère a maintenir.

### Transmission et Propulsion

##### transmission éléctrique 
routage simplifié, moins de pièce mobile, légèrement moins bonne éfficacité qu'un système directe à chaine.
simplicité de rendre le vehicule 4wd

##### transmission mécanique à chaine
routage compliqué avec 4 roues, nécéssite un différientielle.
variante traction du véhicule ?

#####  motorisation
moteur éléctrique de faible puissance (100-500 W)
peut onereux, version 4x4 avec grande redondance donc moins d'entretiens et meilleures tenu de route.
- https://fr.aliexpress.com/item/1005004884524853.html
- https://fr.aliexpress.com/item/1005005874887142.html

version traction avant envisageable aussi.

### Suspension
Comme vu avec le contrôle de l'inclinaison, il faut être capable de faire penché le véhicule à gauche et a droite dans les virages.
De plus, il faut être en mesure d'absorbéer les irregularité de la route ( les pistes cyclables ayant en général un profil moins uniforme que le reste de la route avec les grille d'égouts et autres irrégulatité)
Pour des raisons de cout et de simplicité, le but serais d'utilisé des suspensions de vélo car en plus d'avoir des roulement pour la direction et d'être assez standardisé, certaines utilise un piston d'air comme ressort et un piston d'huile comme absorbeur.
le but serais de motorisé la commande de l'absorbeur et de connecter les piston à air à un système de pompe et valve pour controller au mieux le comportement du véhicule.

### Controle de la temperature
pompe à chaleur ?
système évaporatif a eau + chauffage dans le manche de commande + siège ?

mientiens de la temperature des batteries ?

chauffer le passagé par l'habitacle

### Ergonomie et Position du passagé et du pilote
![image](https://github.com/nathmo/velomobile/assets/15912256/cdb40655-ad67-43a8-9215-9289cb098ee9)

communication entre les personne ? mirroir ?
confort semi couché ?
vu du traffic sans se faire mal au cou

### Canopé et carrosserie
chassis en tube d'aluminium /voir acier selon poid/prix/énérgie
carrosserie en feuille de pet thermoformé 

### Cout de fabrication
pas de composite, problème de recyclage et chère.
Carrosserie en feuille de pet, résistant, léger, peu chère.

### lumière, signalisation
ruban de led qui permet de faire a la fois feux de position et clignotant.
phare avant LED ?

### Système de commande
volant ? joystick ?

### Pilote automatique ?
besoin d'avoir commande éléctrique ?
mais système mécanique directe plus robuste
hybride plus chère et lourd ?
trajet légèrement plus long qu'en voiture mais moins demandant cognitivement ?

# Challenge légaux

### Article lié
niche dans l'ordonnance sur les véhicule, considérer comme un vélo/cyclomoteur léger.

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


# Challenge psychosociaux

### un engin qui soit beau et désirable
dans quelle mesure on peut tout faire avec un bon graphisme ?
![image](https://github.com/nathmo/velomobile/assets/15912256/2eadd522-879d-4440-a752-34d1f0378999)

importance de la forme de la carroserie ?

### biais d'appriori
influence du prix ?
rendre le véhicule désirable ?
communication ?

### prix de vente
moins de 2000 CHF moins chère que les vélo éléctrique et les voitures. confort de la voiture, vitesse supérieur a un vélo moteur
(toutes les solutions simmilaires que j'ai trouvé sont produite en petites quantité et coute plus de ~10'000 CHF pièces.

# Autre
### Train
assimilé a un velo, trajet hybride, d'une ville a l'autre en train, last mile en ecosprint



