Challenge compétitif Physique Environnement Finance Régression Tabulaires Moins de 10Mo Niveau basique
Dates

Une multitude de facteurs influencent le prix de l’électricité au quotidien. Des variations locales du climat pourront à la fois affecter la production et la demande électrique par exemple. Des phénomènes à plus long terme, comme le réchauffement climatique, auront également un impact évident. Des évènements géopolitiques, comme la guerre en Ukraine, peuvent en parallèle faire bouger le prix des matières premières qui sont clefs dans la production d’électricité, sachant que chaque pays s’appuie sur un mix énergétique qui lui est propre (nucléaire, solaire, hydrolique, gaz, charbon, etc). De plus chaque pays peut importer/exporter de l'électricité avec ses voisins au travers de marchés dynamiques, comme en Europe. Ces différents éléments rendent assez complexe la modélisation du prix de l’électricité par pays.
But

L'objectif est de modéliser le prix l'électricité à partir de données météorologiques, énergétiques (matières premières) et commerciales pour deux pays européens - la France et l'Allemagne.On soulignera que c’est ici un problème d’explication des prix par d’autres variables concomitantes et non pas un problème de prédiction.

Plus précisément le but est de construire un modèle qui, à partir de ces variables explicatives, renvoie une bonne estimation de la variation journalière du prix de contrats à terme (dits futures) sur l’électricité, en France ou en Allemagne. Ces contrats permettent d’acheter (ou de vendre) une quantité donnée d’électricité à un prix fixé par le contrat et qui sera livrée à une date future spécifiée (maturité du contrat). Les futures sont donc des instruments financiers qui donnent une estimation de la valeur de l’électricité au moment de la maturité du contrat à partir des conditions actuelles du marché - ici, on se restreint à des futures à courte maturité (24h). Soulignons que l’échange de futures sur l’électricité est un marché dynamique en Europe.

Concernant les variables explicatives, les participants auront accès pour chaque pays à des mesures journalières de données météorologiques (température, quantité de pluie et force du vent), de production énergétique (variations des prix de différentes matières premières / énergies) et d’utilisation de l’électricité (consommation, échanges entre ces deux pays, import-export avec le reste de l’Europe).

La fonction de score (métrique) utilisée est la corrélation de Spearman entre la réponse du participant et les variations réelles du prix des futures contenues dans le jeu de données de test.

N'hésitez pas à consulter notre forum dédié et notre page LinkedIn pour plus d'information sur le challenge et sur QRT.
Description des données

Trois jeux de données sont fournis au format csv : les données d'entrainement en entrée X_train et en sortie Y_train, et les données test en entrée X_test.

NB : Les données d'entrée X_train et X_test représentent les même variables explicatives mais sur deux périodes de temps différentes.

La colonne ID de X_train et Y_train est identique, et de même pour les données test. Les données d'entrainement fournissent 1494 lignes, et les données de test en contiennent 654.

Les données d'entrée possèdent 35 colonnes :

    ID : Identifiant d’index unique, associé à un jour (DAY_ID) et un pays (COUNTRY),

    DAY_ID : Identifiant du jour - les dates ont été anonymisées en préservant la structure des données,

    COUNTRY : Identifiant du pays - DE = Allemagne, FR = France,

et composées ensuite de variations journalières du prix de matières premières,

    GAS_RET : Gaz en Europe,

    COAL_RET : Charbon en Europe,

    CARBON_RET : Futures sur les émissions carbone,

de mesures météorologiques (journalières, dans le pays x),

    x_TEMP : Température,

    x_RAIN : Pluie,

    x_WIND : Vent,

de mesures de productions d'énergie (journalière, dans le pays x),

    x_GAS : Gaz naturel,

    x_COAL : Charbon,

    x_HYDRO : Hydrolique,

    x_NUCLEAR : Nucléaire,

    x_SOLAR : Photovoltaique,

    x_WINDPOW : Eolienne,

    x_LIGNITE : Lignite,

et de mesures d'utilisation électrique (journalières, dans le pays x),

    x_CONSUMPTION : Electricité totale consommée,

    x_RESIDUAL_LOAD : Electricité consommée après utilisation des énergies renouvelables,

    x_NET_IMPORT : Electricité importée depuis l'Europe,

    x_NET_EXPORT : Electricité exportée vers l'Europe,

    DE_FR_EXCHANGE : Electricité échangée entre Allemagne et France,

    FR_DE_EXCHANGE : Electricité échangée entre France et Allemagne.

Les données en sortie se composent de deux colonnes :

    ID : Identifiant unique - le même que celui des données d'entrée,

    TARGET : variation journalière du prix de futures d’électricité (maturité 24h).

Les solutions envoyées par les participants devront être structurées comme les données en sortie, à savoir un fichier au format csv avec deux colonnes ID et TARGET, avec comme valeurs ID les valeurs correspondantes à la colonne ID de X_test. Un exemple de fichier contenant une solution aléatoire est fourni - Cf. aussi le notebook fourni en matériel supplémentaire.
Description du benchmark

Le benchmark pour ce challenge consiste en une simple régression linéaire, après un léger nettoyage des données : les valeurs manquantes (NaN) ont été remplacées par des zéros et la colonne COUNTRY a été supprimée - en d'autres termes, nous avons utilisé un modèle identique pour la France et l'Allemagne.

Le score public obtenu pour ce benchmark est de 15.86%. Un notebook contenant la génération du benchmark et quelques discussions est disponible en "supplementary files" que vous trouverez sur cette page (colonne de droite).

    [Je veux annuler ma participation]

Barre Latérale
Cours

Enregistré sans cours

    [Ajouter un cours]

Fichiers

    x_train (variables explicatives pour l'entrainement)

    y_train (variable(s) cible(s) pour l'entrainement)

    x_test (variables explicatives pour le test)

    Exemple de soumission aléatoire (un exemple de soumission de fichier csv aléatoire)

    Fichiers supplémentaires (data-readers, baseline scripts, instructions, etc.)

L'organisateur du challenge

Qube Research & Technologies (QRT)
Qube Research & Technologies (QRT) is a global quantitative and systematic investment manager, operating in all asset classes across the world. Driven by a shared passion for data, research, technology and trading expertise, we strive to deliver high-quality returns for our investors. Established in 2018, QRT can rely on its 2 000+ employees across 16 offices globally. QRT supports various coding initiatives as well as academic projects developing and promoting maths and science education.
