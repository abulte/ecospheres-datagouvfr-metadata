
Objet : récapitulatif des travaux et réflexions sur le support par data.gouv.fr de nouvelles métadonnées utiles à Ecosphères.

- [[#Préambule|Préambule]]
- [[#Méthodologie et concepts|Méthodologie et concepts]]
- [[#Documents liés|Documents liés]]
- [[#Références|Références]]
- [[#Métadonnées|Métadonnées]]
	- [[#Métadonnées#Identificateur de ressource unique|Identificateur de ressource unique]]
		- [[#Identificateur de ressource unique#Evolution possible|Evolution possible]]
	- [[#Métadonnées#Couverture spatiale|Couverture spatiale]]
		- [[#Couverture spatiale#Alimentation|Alimentation]]
		- [[#Couverture spatiale#Evolution|Evolution]]
			- [[#Evolution#Geozones|Geozones]]
			- [[#Evolution#Géométries|Géométries]]
	- [[#Métadonnées#Granularité et résolution spatiales|Granularité et résolution spatiales]]
		- [[#Granularité et résolution spatiales#Granularité|Granularité]]
		- [[#Granularité et résolution spatiales#Résolution|Résolution]]
	- [[#Métadonnées#Dates de référence|Dates de référence]]
		- [[#Dates de référence#Alimentation|Alimentation]]
			- [[#Alimentation#CKAN|CKAN]]
			- [[#Alimentation#DCAT|DCAT]]
		- [[#Dates de référence#Evolutions possibles|Evolutions possibles]]
		- [[#Dates de référence#Date des métadonnées|Date des métadonnées]]
			- [[#Date des métadonnées#Alimentation|Alimentation]]
			- [[#Date des métadonnées#Evolution possible|Evolution possible]]
	- [[#Métadonnées#Etendue / couverture temporelle|Etendue / couverture temporelle]]
		- [[#Etendue / couverture temporelle#Alimentation|Alimentation]]
			- [[#Alimentation#CKAN|CKAN]]
			- [[#Alimentation#DCAT|DCAT]]
	- [[#Métadonnées#Point de contact|Point de contact]]
		- [[#Point de contact#Alimentation|Alimentation]]
			- [[#Alimentation#CKAN|CKAN]]
			- [[#Alimentation#OpenDataSoft / DCAT|OpenDataSoft / DCAT]]
	- [[#Métadonnées#Catégorie thématique|Catégorie thématique]]
	- [[#Métadonnées#Mots clés|Mots clés]]
	- [[#Métadonnées#Format / encodage|Format / encodage]]
		- [[#Format / encodage#Alimentation|Alimentation]]
			- [[#Alimentation#CKAN|CKAN]]
			- [[#Alimentation#DCAT|DCAT]]
	- [[#Métadonnées#Contraintes en matière d’accès et d’utilisation / Licence|Contraintes en matière d’accès et d’utilisation / Licence]]
		- [[#Contraintes en matière d’accès et d’utilisation / Licence#Evolutions possibles|Evolutions possibles]]
	- [[#Métadonnées#Type de la ressource / ensemble de séries|Type de la ressource / ensemble de séries]]
		- [[#Type de la ressource / ensemble de séries#Evolution possible|Evolution possible]]
- [[#Autres champs à traiter|Autres champs à traiter]]
- [[#Evolutions du modèle et de l'API data.gouv.fr|Evolutions du modèle et de l'API data.gouv.fr]]
	- [[#Evolutions du modèle et de l'API data.gouv.fr#Modèle|Modèle]]
	- [[#Evolutions du modèle et de l'API data.gouv.fr#API|API]]
- [[#Annexes|Annexes]]
	- [[#Annexes#Export API CKAN `ckanext-spatial`|Export API CKAN `ckanext-spatial`]]
	- [[#Annexes#Export RDF/DCAT OpenDataSoft|Export RDF/DCAT OpenDataSoft]]
	- [[#Annexes#Analyse LL sur le sujet type de ressource|Analyse LL sur le sujet type de ressource]]

## Préambule

Le parti pris original d'Ecosphères est de se conformer à la directive INSPIRE en ce qui concerne la définition et la qualification des métadonnées à moissonner et à exposer. Celle-ci a en effet l'avantage d'être un standard déjà bien adopté, et obligatoire, pour une grande partie du périmètre des données du pôle ministériel de l'Environnement.

data.gouv.fr n'a pas été pensé autour de cette norme et possède un ensemble de métadonnées restreint et, le cas échéant, pas toujours compatible avec l'interprétation de la directive INSPIRE.

Les présents travaux visent à une convergence entre les métadonnées de la plateforme Ecosphères (~INSPIRE) et celles de data.gouv.fr. Faute de pouvoir rendre immédiatement data.gouv.fr parfaitement compatible avec INSPIRE, il conviendra de :
- Procéder incrémentalement : ajout progressif de métadonnées sur data.gouv.fr, avec pour ordre de priorité la valeur d'une métadonnée pour les usagers finaux d'Ecosphères ;
- Éventuellement, procéder à des compromis sur la définition d'une ou plusieurs métadonnées existantes sur data.gouv.fr qui pourraient avoir une interprétation différente de celle d'INSPIRE.

On considérera également que data.gouv.fr est principalement alimenté par un mécanisme de moissonnage (65% du catalogue en août 2023, en incluant geo.data.gouv.fr) et on s'attachera ainsi à proposer des pistes pour l'alimentation des métadonnées supplémentaires par ce mécanisme.

| Moissoneur       | JDD   | % total |
| ---------------- | ----- | ------- |
| DCAT             | 2952  | 6.02%   |
| OpenDataSoft     | 10333 | 21.09%  |
| MAAF             | 13    | 0.03%   |
| CKAN             | 3479  | 7.10%   |
| geo.data.gouv.fr | 13694 | 27.95%  |
| Total            | 48996 |         |

## Méthodologie et concepts

Le point de départ de l'analyse d'un concept dans la partie **Métadonnées** ci-dessous part généralement de la définition INSPIRE, et plus précisément de sa définition ou de son analyse dans les documents "Prise en charge des métadonnées INSPIRE par data.gouv.fr" et "Guide de saisie des métadonnées INSPIRE du CNIG" (cf "Documents liés").

Les métadonnées étudiées ne sont pas exhaustives et ont été choisies de manière opportuniste : présentant un intérêt fort en matière d'interopérabilité et/ou pouvant apporter une valeur ajoutée lors de l'analyse. Par exemple la métadonnée "Titre" étant triviale elle a été mise de côté. La partie **Autres champs à traiter** recense les métadonnées au sens INSPIRE non analysées à date.

Pour chaque métadonnée, l'analyse suivante est faite :
- Support ou non par data.gouv.fr d'un concept équivalent et similaire et calcul du taux de complétion par analyse du catalogue ;
- Support ou non par CKAN avec ou sans `ckanext-spatial` et le cas échéant comment ;
- Support ou non par DCAT en étudiant le mapping proposé par le profil belge et le mapping du CNIG ;
- Quand la métadonnée est supportée par data.gouv.fr, on analyse comment elle est alimentée par les moissonneurs DCAT ou CKAN ;
- S'il y a eu lieu, proposition d'évolutions pour le support de la métadonnée par data.gouv.fr ou références vers des évolutions en cours.

On parlera de "Ecosphères CKAN" pour désigner [la plateforme CKAN d'Ecosphères moissonnant des catalogues INSPIRE](https://preprod.data.developpement-durable.gouv.fr).

On parlera d'*exposition* `ckanext-spatial` lorsque [cette extension](https://github.com/ckan/ckanext-spatial) moissonne cette métadonnée via les flux ISO/INSPIRE et la réexpose via l'API standard de CKAN. On parlera de *calcul* de la métadonnée lorsqu'elle est extraite des flux mais non réexposée.

En plus de l'analyse des métadonnées, un embryon de réflexion est engagée sur l'**évolution du modèle et de l'API data.gouv.fr** dans une section dédiée.

## Documents liés

Autres documents produits dans le cadre du projet Ecosphères :

- [Mapping des métadonnées existantes Ecosphères / data.gouv.fr (voir onglet Ecosphères)](https://docs.google.com/spreadsheets/d/1zHLJxZ6Lya74a2lRMqLMC4KSaXtdSH6LqqkClmgaP3g/edit?usp=sharing)
- [Prise en charge des métadonnées INSPIRE par data.gouv.fr](https://github.com/ecolabdata/ecospheres/blob/main/doc/inspire_vs_data_gouv.md)

## Références

- [Code : mapping RDF (DCAT) vers et depuis data.gouv.fr](https://github.com/opendatateam/udata/blob/550f32bb009a6409598264dff47ecb3cc696e5cb/udata/core/dataset/rdf.py#L448)
- [Code : moissonneur CKAN de data.gouv.fr](https://github.com/opendatateam/udata-ckan/) 
- [Guide de saisie des métadonnées INSPIRE du CNIG](https://cnig.gouv.fr/IMG/pdf/guide-de-saisie-des-elements-de-metadonnees-inspire-v2.0-1.pdf)
- [Mapping DCAT / INSPIRE de data.gov.be](https://github.com/belgif/inspire-dcat/blob/main/DCATAPprofil.fr.md)
- [Mapping DCAT / INSPIRE du CNIG (WIP)](https://github.com/cnigfr/metadonnee/tree/main/MappingINSPIRE-DCAT)
- [Export DCAT du catalogue fédéral belge](https://github.com/fedict/dcat)
- [Code : mapping XML du moissonneur ISO/INSPIRE de `ckanext-spatial`](https://github.com/ckan/ckanext-spatial/blob/e59a295431247fcd605fe55bb4fd9a2ecfc28d2b/ckanext/spatial/harvested_metadata.py)
- [Code : alimentation du jeu de données CKAN par `ckanext-spatial` au moissonnage](https://github.com/ckan/ckanext-spatial/blob/e59a295431247fcd605fe55bb4fd9a2ecfc28d2b/ckanext/spatial/harvesters/base.py)

## Métadonnées

### Identificateur de ressource unique 

| Champ data.gouv.fr               | Remplissage | Note |
| -------------------------------- | ----------- | ---- |
| `dataset.id`                     | 100 %       |      |
| `dataset.resources[].id`         | 100 %       |      |
| `dataset.harvest.dct_identifier` | ?           |      |
| `dataset.harvest.remote_id`      | ?           |      |

data.gouv.fr crée pour chaque jeu de données et chaque ressource associée un identifiant réputé unique (MongoID ou UUID).

Dans le cadre du moissonnage, data.gouv.fr stocke également :
- pour DCAT le `dct:idenfifier`
- pour CKAN et OpenDatasoft un `remote_id` exposé par ces plateformes comme étant identifiant (souvent un slug)

Lors de l'exposition RDF d'un élément du catalogue, data.gouv.fr expose `dct_identifer` s'il est présent, sinon son propre id.

Les spécifications INSPIRE permettent d'avoir plusieurs identifiants pour une même ressource (à condition qu'un même identifiant ne pointe pas vers plusieurs ressources). Le CNIG préconise un identifiant sous forme d'URL afin d'associer un espace de nom (nom de domaine) à un identifiant (chemin).

La cardinalité `1..*` pour l'identifiant est aujourd'hui incompatible avec le moissonnage data.gouv.fr, cet identifiant unique servant en effet de pivot pour reconnaitre un jeu de données. On notera également que les [spécifications belges](https://github.com/belgif/inspire-dcat/blob/main/DCATAPprofil.fr.md#instanciation-de-dcatdataset) indiquent une cardinalité de 1.

CKAN `ckanext-spatial` [récupère cet identifiant](https://github.com/ckan/ckanext-spatial/blob/e59a295431247fcd605fe55bb4fd9a2ecfc28d2b/ckanext/spatial/harvested_metadata.py#L553) avec une cardinalité `0..1` dans le moissonnage ISO et ne l'expose pas par défaut.

#### Evolution possible

Il pourrait être intéressant pour data.gouv.fr de supporter des identifiants multiples :
- Résolution de problèmes de compatibilité avec certains catalogues Geonetwork (cf issue dédiée) ;
- Meilleure modélisation de la "chaine de moissonnage".

Le mécanisme pourrait être le suivant :
- data.gouv.fr conserve évidemment ses identifiants techniques ;
- Introduction d'une liste `harvest.identifiers` reprenant les `identifiers` moissonnés ;
- Au moissonnage, data.gouv.fr vérifie si _un des_ identifiants exposés correspond à un des identifiants stockés et effectue ainsi le rapprochement — cette comparaison se faisant dans le scope d'une plateforme donnée (i.e. un moissonneur), le risque de collision est faible même si l'identifiant ne l'est pas (e.g. un slug) ;
- Lors de l'exposition RDF, data.gouv.fr peut exposer plusieurs `identifiers` moissonnés en plus de sien. Il sera alors intéressant de l'exposer sous la forme `https://www.data.gouv.fr/datasets/{id-technique}` afin de suivre les recommendations du CNIG et de permettre de reconnaitre cet identifiant parmi les autres.

### Couverture spatiale

| Champ data.gouv.fr      | Remplissage | Note                                                                                  |
| ----------------------- | ----------- | ------------------------------------------------------------------------------------- |
| `dataset.spatial.zones` | 19 %        | lien vers une ou plusieurs [geozones](https://www.data.gouv.fr/fr/datasets/geozones/) | 
| `dataset.spatial.geom`  | 3 %         | géométrie GeoJSON                                                                     |

#### Alimentation

Les zones sont alimentées via un formulaire sur la page d'édition d'un jeu de données ou par l'API.

Les géométries sont alimentées par API.

Le [moissonneur CKAN](https://github.com/opendatateam/udata-ckan/) de data.gouv.fr supporte également ces deux attributs :
- 2 jeux de données ont leurs zones remplies par le moissonnage [exemple](https://www.data.gouv.fr/api/1/datasets/velos-en-libre-service/)
- 60% des jeux de données ayant une géométrie sont alimentés par moissonnage — on peut noter l'[exemple du Grand Est](https://www.data.gouv.fr/api/1/datasets/648a584690b40931713a42ed/) qui, outre les géométries, expose un grand nombre de métadonnées ~INSPIRE (`lineage`, `bbox`, `contact`) via les extras de CKAN qui sont rapatriés dans les extras de data.gouv.fr (cf Annexes)
#### Evolution

##### Geozones

Les geozones ne sont plus maintenues et ne constituent pas un référentiel partagé avec d'autres catalogues, ce qui limite les possibilité d'interopérabilité.

Une [refonte de ce système](https://github.com/etalab/data.gouv.fr/issues/1116) a été engagée par data.gouv.fr, notamment suite aux échanges avec Ecosphères.

Le futur système se basera (au moins) sur le [référentiel administratif de l'INSEE (COG RDF)](https://rdf.insee.fr/geo/index.html). Ce référentiel pourra être partagé avec d'autres catalogues. Il est notamment [utilisé par la version CKAN d'Ecosphères](https://github.com/ecolabdata/ckanext-ecospheres/blob/9c849a4089a7ba6ce94c56faf02869cea3f96f51/ckanext/ecospheres/scheming/ecospheres_dataset_schema.yaml#L1019C19-L1019C19) comme un des vocabulaires permettant de remplir la métadonnée `spatial_coverage`.

L'alimentation se fera :
- initialement via la migration des geozones vers (au moins) le référentiel de l'INSEE (max 20% du catalogue)
- via un champ de l'administration similaire à celui existant sur les geozones
- *via le moissonnage : point non spécifié à date*

> Piste de collaboration Ecosphères / data.gouv.fr sur le remplissage de cette métadonnée au moissonnage avec la même mécanique que Ecosphères CKAN ?

> A creuser :
> - quid des autres vocabulaires utilisées par Ecosphères ? Seraient-ils utiles à data.gouv.fr ?
> - mécanique de remplissage de la métadonnée par Ecosphères (extraire les spécifications)
##### Géométries

Pas d'évolution structurelle prévue sur ce point côté data.gouv.fr.

> Piste d'évolution : remplir la métadonnée au moissonnage avec les attributs INSPIRE correspondants, a minima la bounding box.
> - CKAN : avec `ckanext-spatial`, disponible dans `bbox-*` sur les jeux INSPIRE
> - DCAT : [attribut dcat:bbox](https://github.com/belgif/inspire-dcat/blob/main/DCATAPprofil.fr.md#k-dctlocation) dans Dcat:Dataset > Dcat:Location ?
> 
> A noter : la géométrie n'est pas une métadonnée priorisée d'un point usager final Ecosphères.

### Granularité et résolution spatiales

#### Granularité

| Champ data.gouv.fr                     | Remplissage | Note |
| ----------------------------- | ----------- | ---- |
| `dataset.spatial.granularity` | 52%         |      |

data.gouv.fr utilise un notion de granularité spatiale qui n'est pas définie par INSPIRE. Cette métadonnée permet de spécifier à quelle maille géographique une "ligne" des données référencées se rapporte. Par exemple une liste des achats de pesticides par département aura une granularité spatiale "département". Le référentiel est celui des [niveaux des geozones](https://github.com/opendatateam/udata/blob/8bf8e516826bf72ee746f897a2e441508f3bdc12/udata/core/spatial/models.py#L290), augmenté des valeurs "POI" et "Autre".

Au niveau moissonnage, cette métadonnée est supportée par OpenDataSoft seulement. Sachant cela, le taux de remplissage global est impressionnant ; peut-être parce que la métadonnée rentre dans le calcul de l'indicateur de qualité dans la partie "couverture spatiale" ?

#### Résolution

Métadonnée supportée par INSPIRE mais pas par data.gouv.fr, cf [analyse Ecosphères](https://github.com/ecolabdata/ecospheres/blob/main/doc/inspire_vs_data_gouv.md#résolution-spatiale). Complexe à exprimer car en fonction du type de données.

Les spécifications belges DCAT propose un mapping `dcat:Dataset,dqv:hasQualityMeasurement,dqv:QualityMeasurement`. Toutefois, on ne retrouve pas d'exemple de cette propriété dans le catalogue fédéral.

CKAN avec `ckanext-spatial` calcule les attributs suivants issus des propriétés INSPIRE `gmd:spatialResolution/gmd:MD_Resolution` mais ne les expose pas par défaut :
- `equivalent-scale`
- `spatial-resolution`
- `spatial-resolution-units`

Pas de support constaté sur OpenDataSoft (legacy).

### Dates de référence

Dans l'analyse Ecosphères :
- [date de publication](https://github.com/ecolabdata/ecospheres/blob/main/doc/inspire_vs_data_gouv.md#date-de-publication)
- [date de dernière révision](https://github.com/ecolabdata/ecospheres/blob/main/doc/inspire_vs_data_gouv.md#date-de-dernière-révision)
- [date de création](https://github.com/ecolabdata/ecospheres/blob/main/doc/inspire_vs_data_gouv.md#date-de-création)

NB : certaines constatations dans l'analyse ci-dessus sont basées sur et biaisées par un flux DCAT Geocatalogue qui n'expose pas ou peu de dates.

| Champ data.gouv.fr                | Remplissage | Note                                                       |
| --------------------------------- | ----------- | ---------------------------------------------------------- |
| `dataset.created_at`              | 100%        | Moissonnée ou système                                      |
| `dataset.last_modified`           | 100%        | Moissonnée ou système (ou calculé pour une ressource)      | 
| `dataset.last_update`             | 100%        | Calculé comme le plus récent modified dataset vs resources |
| `dataset.harvest.last_update`     |             | Dernier passage du moissonneur                             |
| `dataset.harvest.modified_at`     |             | Moissonnée                                                 |
| `dataset.harvest.created_at`      |             | Moissonnée                                                 |
| `dataset.internals.*_at_internal` | 100%        | Système                                                    |

Ces attributs sont répliqués au niveau de la ressource, à l'exception de `last_update`.

[Calcul de `last_modified` pour un jeu de données](https://github.com/opendatateam/udata/blob/8bf8e516826bf72ee746f897a2e441508f3bdc12/udata/core/dataset/models.py#L607C29-L607C29) sur data.gouv.fr : max de date de modification interne (hors moissonnage) et modification moissonnée, si pas moissonnée date interne.

[Calcul de `last_modified` pour une ressource](https://github.com/opendatateam/udata/blob/8bf8e516826bf72ee746f897a2e441508f3bdc12/udata/core/dataset/models.py#L309) sur data.gouv.fr : max de date de modification interne (hors moissonnage) et modification moissonnée, si pas moissonnée date détectée par crawler, sinon date interne.

data.gouv.fr n'a pas de notion de date de publication. Elle existait pour une ressource [avant d'être supprimée](https://github.com/opendatateam/udata/pull/2807) en raison de la confusion qu'elle créait et de son faible taux de remplissage. On notera que sa présence au niveau de la ressource ne permettait de toute façon pas un mapping avec INSPIRE (plutôt niveau jeu de données). 

Le guide de saisie des métadonnées INSPIRE du CNIG ne donne pas beaucoup de contexte pour le remplissage de la date de publication, à part peut-être un lien avec une date d'entrée en vigueur (pour des raisons réglementaires ?). L'accent est mis surtout sur la date de création et sur la date de révision le cas échéant.

#### Alimentation

##### CKAN

CKAN expose par défaut sur le jeu de données :
- `metadata_created`, utilisée par data.gouv.fr pour `created_at`
- `metadata_modified`, utilisée par data.gouv.fr pour `last_modified` (cf plus haut)

CKAN expose par défaut sur la ressource :
- `created`, utilisée par data.gouv.fr pour `created_at`
- `last_modified`, utilisée par data.gouv.fr pour `last_modified` (cf plus haut)

CKAN `ckanext-spatial` calcule les attributs INSPIRE :
- `date-released` depuis `dataset-reference-date.publication`
- `date-updated` depuis `dataset-reference-date.revision` 
- `date-created` depuis `dataset-reference-date.creation`

L'attribut parent est exposé dans l'extra `dataset-reference-date`, cf ci-dessous :

```json
{
	"value": "[{\"type\": \"creation\", \"value\": \"2016-01-01\"}, {\"type\": \"edition\", \"value\": \"2023-06-13\"}, {\"type\": \"publication\", \"value\": \"\"}]",
	"key": "dataset-reference-date"
},
```

Il n'y a pas de mapping de ces dates spécifiques INSPIRE vers les attributs par défaut de CKAN. En effet, ces dates concernent normalement les données et non les métadonnées (cf paragraphe plus bas sur cette distinction).

data.gouv.fr n'utilise pas ces dates INSPIRE au moissonnage.

##### DCAT

data.gouv.fr consomme et expose le mapping suivant pour un jeu de données et une ressource :
- `created_at` : `DCT.issued`
- `last_modified` : `DCT.modified` (avec règle de gestion, cf plus haut)

Les spécifications belges proposent le mapping suivant sur un `Dataset` et un `DataService` :
- creation : `dct:created`
- revision : `dct:modified`
- publication : `dct:issued`

Le CNIG semble avoir fait une erreur dans son mapping en échangeant création et dernière révision :
- publication : `dct:issued`
- création : `dct:modified`
- dernière révision : `dct:created`

#### Evolutions possibles

La date de modification data.gouv.fr devrait être exposée et consommée en tant que `dct:modified`.

La date de publication pourrait être gérée en tant que métadonnée supplémentaire, facilement accessible via DCAT et `ckanext-spatial`. Attention toutefois à la confusion entre date des données et des métadonnées (cf plus bas).

#### Date des métadonnées

INSPIRE fait une distinction entre dates des données (cf dates de référence plus haut) et date des métadonnées (autre attribut discuté ici).

Pour les dates des données, on peut citer le guide CNIG pour la date de création :

*Il s’agit de la date de création de la série de données ou de l’ensemble de séries de données, mais pas la date de création du ou des objets du monde réel décrits. Typiquement, si la série de données est une photographie prise le 15 mai 2000 d’un monument historique datant de 1920, la date de création de la ressource est le 15 mai 2000.*

La couverture temporelle (cf plus bas) s'appliquerait elle plutôt aux objects sous-jacents aux données (1920 dans l'exemple ci-dessus).

La date des métadonnées est moins bien explicitée. On peut faire l'hypothèse qu'elle se réfère à la date de création puis de modification de l'enregistrement sur le ou les catalogues qui exposent la ressource.

data.gouv.fr mélange les notions de dates des données (possiblement récupérées via le moissonnage) et les dates des métadonnées (dates système). Vu la complexité du sujet, il est possible que de nombreux autres catalogues fassent cette confusion.

##### Alimentation

CKAN `ckanext-spatial` calcule et expose `metadata-date`. Cette date sert de référence pour savoir si un objet a été modifié au moissonnage. Elle n'alimente pas `metadata_modified`. Cet attribut n'est pas utilisé par le moissonnage CKAN data.gouv.fr.

Les spécifications DCAT/INSPIRE belges et le CNIG proposent un mapping vers `dcat:CatalogRecord/dct:modified`. L'object `CatalogRecord` se situerait à un niveau "au-dessus" du `dcat:Dataset`. Pas d'exemple trouvé dans le catalogue fédéral belge.

##### Evolution possible

En fonction du schéma DCAT retenu en exposition et en entrée, il pourra être intéressant d'intégrer la notion de `CatalogRecord` et de cette métadonnée. Il est possible de récupérer la métadonnée via `ckanext-spatial` ou via DCAT le cas échéant.

La complexité de l'interprétation de cette métadonnée interroge toutefois sur son utilité au delà d'une logique de moissonnage INSPIRE (i.e. quelle valeur ajoutée pour les portails ?).

### Etendue / couverture temporelle

| Champ data.gouv.fr        | Remplissage | Note |
| ------------------------- | ----------- | ---- |
| `temporal_coverage.start` | 12 %        |      |
| `temporal_coverage.end`   | 12 %        |      |

Voir [l'analyse détaillée Ecopshères](https://github.com/ecolabdata/ecospheres/blob/main/doc/inspire_vs_data_gouv.md#etendue-temporelle). A noter : peu utilisé en pratique dans les catalogues INSPIRE. Permet de définir plusieurs périodes discontinues.

#### Alimentation

##### CKAN

CKAN `ckanext-spatial` expose les extras `temporal-extent-begin` et `temporal-extent-end`, qui sont la première occurence de l'une ou l'autre des propriétés INSPIRE, donc une seule période retenue.

Le moissonneur CKAN de data.gouv.fr utilise les extras `temporal_start` et `temporal_end`, d'origine inconnue. Seuls 3 jeux de données sur data.gouv.fr semble exploiter ces extras.

> Amélioration possible : utiliser les "bons" attributs.

##### DCAT

data.gouv.fr expose `dct:temporal,DCT.PeriodOfTime,DCAT.startDate|DCAT.endDate` et ingère le même format, ce qui est conforme aux spécifications en dehors de la cardinalité (`0..1` vs `0..n`).

110 jeux de données moissonnées en DCAT bénéficie de ce format.

### Point de contact

Métadonnée non supportée à date par data.gouv.fr. Le support de cette métadonnée est envisagé.
#### Alimentation

##### CKAN

CKAN avec `ckanext-spatial` expose `contact-email` en extras. Le [calcul de cette métadonnée](https://github.com/ecolabdata/ckanext-spatial/blob/944ae4dd973f37a291514823b27607ea296af05a/ckanext/spatial/harvested_metadata.py#L950) semble indiquer que cette valeur correspond à l'email de la première des _Organisations responsables de l'établissement, de la gestion, de la maintenance et de la diffusion des séries et services de données géographiques_. L'[extension calcule également le label associé](https://github.com/ecolabdata/ckanext-spatial/blob/944ae4dd973f37a291514823b27607ea296af05a/ckanext/spatial/harvested_metadata.py#L942) `contact` mais ne semble pas l'exposer en extras.
##### OpenDataSoft / DCAT

OpenDataSoft est capable d'exposer un point de contact dans son export RDF/DCAT (cf Annexes pour l'export complet).

```xml
<dcat:contactPoint>
	<vcard:Organization>
		<rdf:type rdf:resource="http://www.w3.org/2006/vcard/ns#Kind" />
		<vcard:hasEmail rdf:resource="mailto:dataesr@recherche.gouv.fr" />
	</vcard:Organization>
</dcat:contactPoint>
```

Ce formalisme semble correspondre aux bonnes pratiques, [par exemple dans les spécifications belges](https://github.com/belgif/inspire-dcat/blob/main/DCATAPprofil.fr.md#instanciation-de-dcatdataset). L'`Organization` gagnerait à être complétée par son label et son rôle.

### Catégorie thématique

Cette propriété pioche dans un [vocabulaire contrôlé ISO](https://inspire.ec.europa.eu/metadata-codelist/TopicCategory), qui ne correspond _pas_ aux thèmes INSPIRE (un mapping indicatif est proposé dans le guide de saisie du CNIG).

Le CNIG et les spécifications belges préconisent un mapping vers `dcat:Dataset,dct:Subject,skos:Concept`

CKAN avec `ckanext-spatial` calcule `topic-category` le cas échéant mais ne l'expose pas par défaut.

data.gouv.fr ne prend pas en compte cette propriété dans le moissonnage DCAT ou CKAN et ne possède pas de support de vocabulaire contrôlé.

> Le support de cette propriété en tant que simple mot clé (cf ci-dessous) via le moissonneur DCAT est trivial.
> Quels sont les usages réels de la propriété ?

### Mots clés

| Champ data.gouv.fr | Remplissage | Note |
| ------------------ | ----------- | ---- |
| `dataset.tags`     | 88%         |      |

Cf [analyse Ecopshères](https://github.com/ecolabdata/ecospheres/blob/main/doc/inspire_vs_data_gouv.md#mots-clés).

data.gouv.fr supporte des mots clés en tant que liste de textes libres. Niveau moissonnage :
- OpenDataSoft support natif
- CKAN : propriété `tags`, provenant de `keyword-inspire-theme` et `keyword-controlled-other` pour `ckanext-spatial` (les deux propriétés INSPIRE recommandées)
- DCAT : `DCAT.theme` et `DCAT.keyword`, concaténés

Le principal facteur limitant est l'absence de support sur data.gouv.fr de vocabulaires contrôlés qui pourraient apporter améliorer l'interopérabilité de la plateforme et la lisibilité des métadonnées moissonnées.

> Voir les réflexions sur le modèle et l'API ci-dessous pour le support de ces vocabulaires.

On notera que CKAN n'expose pas non plus le vocabulaire utilisé dans les métadonnées INSPIRE le cas échéant. Seul le support de vocabulaires contrôlés via DCAT pourrait être ajouté par data.gouv.fr.

### Format / encodage

| Champ data.gouv.fr           | Remplissage | Note |
| ---------------------------- | ----------- | ---- |
| `dataset.resources[].format` | 98%         |      |
| `dataset.resources[].mime`   | 53%         |      |

INSPIRE utilise la notion d'encodage comme proche de celle de format utilisée sur data.gouv.fr.

*Description du ou des concepts en langage machine spécifiant la représentation des objets de données dans un enregistrement, un fichier, un message, un dispositif de stockage ou un canal de transmission.*

INSPIRE préconise d'associer un format à une version dès que c'est possible (e.g. GeoTIFF 1.0). Il est possible de spécifier plusieurs formats. Aucun vocabulaire contrôlé n'est préconisé.

Sur data.gouv.fr l'information `format` est portée par chaque ressource, avec une liste semi-ouverte (auto-complétion et ajout de valeurs si besoin). Pas de support formel de la notion de version, même si on peut remplir `geotiff-1.0` par exemple si besoin.

data.gouv.fr supporte aussi la notion de [type Mime](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types), également sous forme de liste semi-ouverte. Cette information est extraite automatiquement pour les fichiers uploadés sur data.gouv.fr et renseignée par le producteur sinon.

#### Alimentation

##### CKAN

CKAN expose `mimetype` et `format`, que le moissonneur data.gouv.fr utilise.  `ckanext-spatial` [calcule `format` en fonction de l'URL de la ressource](https://github.com/ckan/ckanext-spatial/blob/e59a295431247fcd605fe55bb4fd9a2ecfc28d2b/ckanext/spatial/harvesters/base.py#L63), pas depuis un attribut ISO/INSPIRE. `data-format` [est calculé depuis les flux ISO](https://github.com/ecolabdata/ckanext-spatial/blob/944ae4dd973f37a291514823b27607ea296af05a/ckanext/spatial/harvested_metadata.py#L805C1-L805C1) mais non exposé.

##### DCAT

Les spécifications préconisent l'utilisation d'un [vocabulaire contrôlé](http://publications.europa.eu/resource/authority/file-type) pour la propriété `Distribution-dct:format` mais pas de mapping depuis `gmd:distributionFormat`. Le CNIG préconise le mapping vers `dct:format`.

Exemple catalogue fédéral belge :

```xml
<dct:format rdf:resource="http://publications.europa.eu/resource/authority/file-type/CSV"/>
```

Le moissonneur data.gouv.fr utilise `DCAT.mediaType` et `DCT.format` pour remplir les attributs correspondants en texte libre.

### Contraintes en matière d’accès et d’utilisation / Licence

| Champ data.gouv.fr | Remplissage | Note |
| ------------------ | ----------- | ---- |
| `dataset.license`     | 94%         |      |

data.gouv.fr supporte un champ `license` qui prend son identifiant dans un [vocabulaire contrôlé spécifique](https://www.data.gouv.fr/api/1/datasets/licenses/). Ce vocabulaire est réutilisé par certaines plateformes moissonnées.

Lors du moissonnage, les attributs suivants sont utilisés :
- CKAN : `license_id` et `license_title`
- DCAT : `dct:license` et `dct:right` au niveau des `Distributions`

data.gouv.fr [tente de "deviner"](https://github.com/opendatateam/udata/blob/8bf8e516826bf72ee746f897a2e441508f3bdc12/udata/core/dataset/models.py#L186) la licence en fonction des différents champs du vocabulaire et le calcul d'une distance sémantique.

INSPIRE propose des notions beaucoup plus large qu'une simple licence :
- Restrictions d’accès public : pas de restriction d’accès public ou [une des exceptions prévues par INSPIRE (vocabulaire)](https://inspire.ec.europa.eu/metadata-codelist/LimitationsOnPublicAccess)
- Conditions légales applicables à l’accès et à l’utilisation : pas de condition, tarification... et **le cas particulier de la licence**
- D'autres contraintes qui ne rentreraient pas dans les cas précédents
#### Evolutions possibles

data.gouv.fr envisage de référencer explicitement des données non disponibles en "open data pur", i.e. soumises à des conditions d'accès ou de réutilisation.

Dans ce cadre il pourra être intéressant de s'inspirer des travaux INSPIRE et GD4H, au moins pour assurer une rétro-compatibilité. L'introduction de champs supplémentaires au simple `license` sera certainement nécessaire. L'utilisation de vocabulaires contrôlés est encouragée quand cela est possible, [cf les préconisations belges](https://github.com/belgif/inspire-dcat/blob/main/DCATAPprofil.fr.md#annexe-ii).

Le champ `license` gagnerait aussi à utiliser un vocabulaire contrôlé externe (ex : SPDX) pour une meilleure interopérabilité. On notera qu'INSPIRE ou le CNIG n'émet pas de recommandation sur ce vocabulaire.

Pour le moissonnage :
- `dct:accessRights` et `dct:License` sont disponibles en DCAT sur `Dataset` et `DataService`. Attention, data.gouv.fr utilise aujourd'hui les attributs de `Distribution` (`DataService` nouveau en DCAT v2)
- CKAN  :
	- Expose `use_constraints` via un mapping vers un vocabulaire interne de licence
	- Expose `limitations-on-public-access` (ISO) dans `access_constraints` 
	- Calcule `access-constraints` (ISO) mais ne l'expose pas


### Type de la ressource / ensemble de séries

Cf [analyse détaillée Ecosphères](https://github.com/ecolabdata/ecospheres/blob/main/doc/inspire_vs_data_gouv.md#type-de-la-ressource). On s'intéresse ici à l'ensemble de séries, c'est-à-dire à la modélisation d'une liste de jeux de données liés que "les gestionnaires de données [...] utilisent pour regrouper des jeux de données formant un ensemble cohérent et pertinent pour les réutilisateurs."

Se référer également à l'annexe "Analyse LL sur le sujet type de ressource" pour plus de détails.

data.gouv.fr n'a pas de support à date de cette notion. Les évolutions prévues sur le sujet des "topics" peuvent s'en rapprocher en ce qu'ils constituent une liste arbitraire d'objets liés entre eux, par exemple des jeux de données. data.gouv.fr expose également des "jeux de données recommandés", soit de manière éditoriale soit de manière automatique, dans les extras d'un jeu de données.

Côté INSPIRE, la modélisation concrète de cette notion ne semble pas bien définie et on trouve des approches différentes selon les catalogues : soit une indication de la présence d'un parent dans une fiche enfant, soit l'indication de la présence d'enfants dans une fiche parent.

Ecosphères CKAN [a traité le cas de Geo-IDE catalogue](https://github.com/ecolabdata/ckanext-ecospheres/blob/9c849a4089a7ba6ce94c56faf02869cea3f96f51/ckanext/ecospheres/spatial/harvester.py#L387) en exploitant la métadonnée `aggregation-info` calculée par `ckanext-spatial` ainsi que d'autres attributs XML extraits pour l'occasion. Ceci aboutit à l'exposition d'une métadonnée `series_members` avec la liste des identifiants des enfants sur le jeu de données parents et la métadonnées `in_series` sur les jeux de données enfants contenant la liste des autres jeux de données enfants.

Côté DCAT, les spécifications belges ne traitent pas de ce sujet. Côté CNIG, [cette issue recense les différents possibilités](https://github.com/cnigfr/metadonnee/issues/14), à savoir `dct:isPartOf` et `dct:hasPart` en DCAT v2 ou [`dcat:DatasetSeries`](https://www.w3.org/TR/vocab-dcat-3/#Class:Dataset_Series) en v3. On note que "la notion de série est peu utilisée au niveau des plateformes régionales."

#### Evolution possible

Il pourrait être intéressant pour data.gouv.fr de supporter cette notion d'ensemble de jeux de données, et ce au delà de la compatibilité INSPIRE.

Le moissonnage s'avère complexe et sera à arbitrer en fonction des opportunités et des possibilités des plateformes source. L'évolution des paradigmes utilisé dans les catalogues DCAT sera à suivre. On notera que CKAN Ecosphères parvient à 42% de remplissage de la métadonnée `in_series`, a priori à travers le seul Geo-IDE catalogue.

Comme évoqué plus tôt, cette notion peut être intuitivement rapprochée [des travaux sur les topics](https://github.com/etalab/data.gouv.fr/issues/1117). Toutefois, via ce concept, on ne pourra pas exprimer une relation entre un jeu de données parent et ses enfants, par exemple [Ilots déclarés à la PAC 2012 et le groupe de cultures dominant - Rhône-Alpes](https://catalogue.datara.gouv.fr/geonetwork/srv/api/records/fff02ef4-8918-4d42-a6ab-53a0d83468bf/formatters/xml) et son enfant [Ilots déclarés à la PAC 2012 et le groupe de cultures dominant - Ardèche](https://catalogue.datara.gouv.fr/geonetwork/srv/api/records/5b786cc5-0159-4e45-96dd-1ef8564c298a/formatters/xml). De plus, cela conduirait à la création de nombreux topics pas forcément pertinent. Une métadonnée similaire parent/enfant à celle proposée par Ecosphères CKAN serait certainement mieux adaptée. data.gouv.fr pourrait en tirer parti pour enrichir l'interface en proposant une navigation parent/enfant/frères.

## Autres champs à traiter

Plan du guide de saisie des métadonnées du CNIG dont les parties n'ont pas été traitées dans ce document :

II.1. INTITULE DE LA RESSOURCE
II.2. RESUME DE LA RESSOURCE
~~II.3. TYPE DE LA RESSOURCE~~
II.4. LOCALISATEUR DE LA RESSOURCE
~~II.5. IDENTIFICATEUR DE RESSOURCE UNIQUE~~
II.6. LANGUE DE LA RESSOURCE
~~II.7. ENCODAGE~~
II.8. ENCODAGE DES CARACTERES
II.9. TYPE DE REPRESENTATION GEOGRAPHIQUE
V.2.  REFERENTIEL DE COORDONNEES
~~VI. REFERENCE TEMPORELLE~~
VII.1 GENEALOGIE
~~VII.2 RESOLUTION SPATIALE~~
VII.3 COHERENCE TOPOLOGIQUE
VIII. Conformité
X. ORGANISATIONS RESPONSABLES DE L’ETABLISSEMENT, DE LA GESTION, DE LA MAINTENANCE ET DE LA DIFFUSION DES SERIES ET SERVICES DE DONNEES GEOGRAPHIQUES
~~XI.2. DATE DES METADONNEES~~
XI.3. LANGUE DES METADONNEES
XI.4. IDENTIFIANT DE LA METADONNEE

## Evolutions du modèle et de l'API data.gouv.fr

Si des métadonnées sont précisées ou ajoutées à data.gouv.fr dans le cadre de ces travaux, il sera nécessaire de faire évoluer le modèle de données et l'API (au sens large mise à disposition programmatique des données).

### Modèle

Plusieurs possibilités :

- Création de champs "libres" dans les dictionnaires `dataset.extras` et `resource.extras` avec des clés valeurs simples (i.e. pas d'objet/dictionnaire imbriqué) : solution simple et rapide qui ne permet pas de valider les valeurs ou de stocker des valeurs complexes. La recherche ne fonctionnera pas sur ces champs. Ils ne seront pas disponibles dans les formulaires. Ils seront disponibles dans l'API mais pas dans les [représentations RDF](https://www.data.gouv.fr/fr/datasets/bureaux-de-vote-et-adresses-de-leurs-electeurs/rdf.json), sauf développement.
- Evolution du modèle "coeur" de `udata` avec la création de nouveaux champs des objets `Dataset` ou `Resource`. Solution qui demande plus de développement mais permet de modéliser n'importe quelle typologie. Rend possible : inclusion dans les formulaires, validation, sélection dans une liste de valeurs, indexation dans le moteur de recherche.

Vu l'importance des vocabulaires contrôlées sur le périmètre qui nous intéresse, il pourra être intéressant de modéliser ce comportement de manière générique, peut-être dans un type de champ dédié. La métadonnée `spatial.zones` pourrait être un terrain d'expérimentation.

### API

L'[API JSON/REST](https://www.data.gouv.fr/api/1/) est facilement extensible pour inclure de nouveaux champs.

En revanche, cette API n'est peut-être pas favorable à l'expression de concepts sémantiques (e.g. vocabulaires contrôlés). Il faudrait en effet transformer l'ensemble de la réponse en RDF par exemple pour exprimer correctement de tels concepts, ce qui n'est probablement pas envisageable.

Chaque jeu de données et le catalogue dispose d'une exposition RDF multiformat, par exemple en [JSON](https://www.data.gouv.fr/fr/datasets/bureaux-de-vote-et-adresses-de-leurs-electeurs/rdf.json) ou en [XML](https://www.data.gouv.fr/fr/datasets/bureaux-de-vote-et-adresses-de-leurs-electeurs/rdf.xml). Ces points d'exposition pourraient être utilisés pour exprimer des spécificités sémantiques tel qu'une valeur d'un vocabulaire contrôlé.

On pourrait imaginer "sémantiser" une partie de la réponse API :

```xml
<dcat:theme rdf:resource="http://publications.europa.eu/resource/authority/data-theme/ENVI"/>
```

deviendrait 

```json
[...]
"theme": {
	"@context": {
		"dcat": "http://www.w3.org/ns/dcat#"
	},
	"dcat:theme": "http://publications.europa.eu/resource/authority/data-theme/ENVI" 
}
[...]
```

Toutefois ce format ne correspond a priori à aucune spécification, ne permet pas de récupérer directement la valeur (dans ce cas `Environnement`) — ce qui pourrait être contourné en rajoutant un attribut `value`, est verbeux et mènerait à une duplication de contextes.

Autre possibilité en travaillant au niveau de l'objet et en incluant du json-ld dans un payload json standard :

```json
{
  "@context": {
    "dcat": "http://www.w3.org/ns/dcat#"
  },
  "data" : {
	[...]
    "du": "json_normal"
    [...]
  },
  "dcat:theme": "http://publications.europa.eu/resource/authority/data-theme/ENVI"
}
```

Cette solution est bancale car l'ensemble du jeu de données ne sera pas interprétable en RDF. De plus, pour des attributs existants, il y aurait une collision ou une duplication entre l'ancien nom de l'attribut (e.g. `theme`) et le nouveau (`dcat:theme`).

On peut noter que CKAN semble avoir adopté une approche spécifique pour le cas des vocabulaires contrôlés, par exemple pour un tag sur la plateforme Grand Est :

```json
      {
        "vocabulary_id": null,
        "state": "active",
        "display_name": "données ouvertes",
        "id": "9e9bd373-7d24-4765-9150-1136d250be3a",
        "name": "données ouvertes"
      }
```

Toutefois il s'agit de [vocabulaires spécifiques à l'instance CKAN](https://docs.ckan.org/en/2.9/maintaining/tag-vocabularies.html).

Ecosphères [expose certaines métadonnées](https://preprod.data.developpement-durable.gouv.fr/api/3/action/package_show?id=fr-120066022-jdd-375ba6b7-1cc2-4a51-a59f-bfd3b96dbd86) sous forme d'URI. C'est une solution simple et efficace mais qui pose la question de la consommation de l'API qui ne porte pas l'information que tel ou tel attribut doit être interprété comme une ressource au sens RDF.

```json
[...]
"result": 
	{
		"accrual_periodicity": "http://inspire.ec.europa.eu/metadata-codelist/MaintenanceFrequency/asNeeded",
		"license": "https://spdx.org/licenses/etalab-2.0",
		"license_id": null,
		"license_title": null,
	},
[...]
```

data.gov (qui utilise CKAN) modélise également [certains attributs sous forme d'URI dans les extras](https://catalog.data.gov/api/3/action/package_show?id=fdic-failed-bank-list) :

```json
"extras": [
	{
		"key": "catalog_conformsTo",
		"value": "https://project-open-data.cio.gov/v1.1/schema"
	}
]
```
## Annexes

### Export API CKAN `ckanext-spatial`

NB : a priori cet export est augmenté par la plateforme vs les fonctionnalités par défaut du plugin, on y retrouve en effet des attributs ISO non exposés par défaut (eg `equivalent-scale`). On retrouve, selon notre compréhension, [les attributs exposés par défaut ici](https://github.com/ckan/ckanext-spatial/blob/e59a295431247fcd605fe55bb4fd9a2ecfc28d2b/ckanext/spatial/harvesters/base.py#L233). L'ensemble des attributs ISO récupérés par le moissonneur mais pas forcément exposés est [ici](https://github.com/ckan/ckanext-spatial/blob/e59a295431247fcd605fe55bb4fd9a2ecfc28d2b/ckanext/spatial/harvested_metadata.py).

https://grandest-moissonnage.data4citizen.com/api/3/action/package_show?id=fr-200052264-commune_grand_est

```json
{
  "help": "https://grandest-moissonnage.data4citizen.com/api/3/action/help_show?name=package_show",
  "success": true,
  "result": {
    "owner_org": "088032c5-e519-49fa-b1a1-b421bbfe7be5",
    "maintainer": null,
    "relationships_as_object": [],
    "private": false,
    "maintainer_email": null,
    "num_tags": 7,
    "id": "4c91f7c2-af7c-4128-99c0-b0af56ce5b7f",
    "metadata_created": "2023-06-14T00:49:28.521578",
    "metadata_modified": "2023-06-14T00:49:28.521585",
    "author": null,
    "author_email": null,
    "state": "active",
    "version": null,
    "license_id": null,
    "type": "dataset",
    "resources": [
      {
        "cache_last_updated": null,
        "package_id": "4c91f7c2-af7c-4128-99c0-b0af56ce5b7f",
        "datastore_active": false,
        "id": "41f1c5b6-22f1-4d55-b713-f496470c0ea2",
        "size": null,
        "state": "active",
        "resource_locator_function": "",
        "hash": "",
        "description": "Webservice : flux WMS pour visualiser les données",
        "format": "",
        "mimetype_inner": null,
        "url_type": null,
        "resource_locator_protocol": "OGC:WMS",
        "mimetype": null,
        "cache_url": null,
        "name": "commune_actuelle",
        "created": "2023-06-14T00:49:32.028649",
        "url": "https://www.datagrandest.fr/geoserver/region-grand-est/wms",
        "last_modified": null,
        "position": 0,
        "revision_id": "b645df5e-68dc-479d-8839-18e214dddd5f",
        "resource_type": null
      },
      {
        "cache_last_updated": null,
        "package_id": "4c91f7c2-af7c-4128-99c0-b0af56ce5b7f",
        "datastore_active": false,
        "id": "4b1b0d3c-9d8c-4f52-abcf-de3c8172e4fd",
        "size": null,
        "state": "active",
        "resource_locator_function": "",
        "hash": "",
        "description": "Webservice : flux WFS pour télécharger les données",
        "format": "",
        "mimetype_inner": null,
        "url_type": null,
        "resource_locator_protocol": "OGC:WFS",
        "mimetype": null,
        "cache_url": null,
        "name": "commune_actuelle",
        "created": "2023-06-14T00:49:32.028656",
        "url": "https://www.datagrandest.fr/geoserver/region-grand-est/wfs",
        "last_modified": null,
        "position": 1,
        "revision_id": "b645df5e-68dc-479d-8839-18e214dddd5f",
        "resource_type": null
      },
      {
        "cache_last_updated": null,
        "package_id": "4c91f7c2-af7c-4128-99c0-b0af56ce5b7f",
        "datastore_active": false,
        "id": "612bae96-5c16-4687-a041-dad351f0e09a",
        "size": null,
        "state": "active",
        "resource_locator_function": "",
        "hash": "",
        "description": "Licence Ouverte Etalab V2",
        "format": "PDF",
        "mimetype_inner": null,
        "url_type": null,
        "resource_locator_protocol": "WWW:DOWNLOAD-1.0-http--download",
        "mimetype": null,
        "cache_url": null,
        "name": "Licence Ouverte Etalab V2",
        "created": "2023-06-14T00:49:32.028660",
        "url": "http://odgeo.grandest.fr/Imagette_MD/ETALAB-Licence-Ouverte-v2.0.pdf",
        "last_modified": null,
        "position": 2,
        "revision_id": "b645df5e-68dc-479d-8839-18e214dddd5f",
        "resource_type": null
      }
    ],
    "num_resources": 3,
    "tags": [
      {
        "vocabulary_id": null,
        "state": "active",
        "display_name": "COMMUNE",
        "id": "0f434436-a63f-4235-8af4-4dd098dabd6f",
        "name": "COMMUNE"
      },
      {
        "vocabulary_id": null,
        "state": "active",
        "display_name": "DONNEES GEOGRAPHIQUES",
        "id": "b43bf45d-56c9-4509-91d7-033cbef8f60a",
        "name": "DONNEES GEOGRAPHIQUES"
      },
      {
        "vocabulary_id": null,
        "state": "active",
        "display_name": "Géoportail",
        "id": "207af8cb-ee0c-4d19-a7b0-0a38d64aba92",
        "name": "Géoportail"
      },
      {
        "vocabulary_id": null,
        "state": "active",
        "display_name": "LIMITE COMMUNALE",
        "id": "7013b23f-a60f-4543-abd8-6263c2da21a9",
        "name": "LIMITE COMMUNALE"
      },
      {
        "vocabulary_id": null,
        "state": "active",
        "display_name": "Systèmes de maillage géographique",
        "id": "08a14a1c-1fc8-4df0-bda6-a8304905a679",
        "name": "Systèmes de maillage géographique"
      },
      {
        "vocabulary_id": null,
        "state": "active",
        "display_name": "UNITE ADMINISTRATIVE",
        "id": "28c07d39-ccce-45a7-b3c8-e6a2f3830d79",
        "name": "UNITE ADMINISTRATIVE"
      },
      {
        "vocabulary_id": null,
        "state": "active",
        "display_name": "données ouvertes",
        "id": "9e9bd373-7d24-4765-9150-1136d250be3a",
        "name": "données ouvertes"
      }
    ],
    "title": "DONNEE - Commune du Grand Est (petite échelle)",
    "groups": [],
    "creator_user_id": "345264f9-9290-4600-8b27-68a48f9286ca",
    "relationships_as_subject": [],
    "name": "fr-200052264-commune_grand_est",
    "isopen": false,
    "url": null,
    "notes": "Donnée des communes du Grand Est, mise à jour régulière par le management et valorisation de la donnée de la Région Grand Est.\nLa géométrie est issue de la Base AdminExpress de l'IGN, géométrie 2018, prise en compte des fusions à aujourd'hui\nLa table basée sur la table acal.commune_actuelle avec une sélection de champs.\nSource : Région Grand Est / IGN  \n\nChamps\ninsee_com : code insee\nnom_com : nom de la commune\nstatut_n : statut administratif\nsuperf_km : superficie en km2\ndensite : densité en hab/km2 (selon pmun_2020)\ncode_reg : code région\ncode_dept : code département\nnom_dept : nom département\nid_canton  identifiant du canton\nlib_canton libellé du canton\nid_arrondt identifiant de l’arrondissement\nnom_arrondt libellé de l’arrondissement\npop_dgf_2022 : population DGF 2022\nsituation_fiscale_2022 : Source DGCL, Données 2022\nCas N°1 (– –) : Potentiel financier par habitant inférieur au potentiel financier moyen de la strate & Effort fiscal supérieur à l'effort fiscal moyen de la strate\nCas N°2 (– +) : Potentiel financier par habitant inférieur au potentiel financier moyen de la strate & Effort fiscal inférieur à l'effort fiscal moyen de la strate\nCas N°3 (+ –) : Potentiel financier par habitant supérieur au potentiel financier moyen de la strate & Effort fiscal supérieur à l'effort fiscal moyen de la strate\nCas N°4 (+ +) : Potentiel financier par habitant supérieur au potentiel financier\nid_maison_region_dl : identifiant de la Maison de Région vue des lycées\nlib_maison_region_dl : nom de la Maison de Région vue des lycées\nid_maison_region_climaxion  : identifiant de la Maison de Région pour Climaxion\nlib_maison_region_climaxion : nom de la Maison de Région pour Climaxion\nid_maison_region_eco  : identifiant de la Maison de Région vue développement éco\nlib_maison_region_eco : nom de la Maison de Région vue développement éco\nid_maison_region_amg : identifiant de la Maison de Région vue aménagement\nlib_maison_region_amg  : nom de la Maison de Région vue aménagement\nid_maison_region_formpro : identifiant de la Maison de Région vue formation pro\nlib_maison_region_formpro  : nom de la Maison de Région vue formation pro\nid_maison_region_transport : identifiant de la Maison de Région vue transport\nlib_maison_region_transport  : nom de la Maison de Région vue transport\nmaison_region character  cf lib_maison_region_amg\nid_maison_region cf id_maison_region_amg\nlib_pays character nom du pays / petr\nnom_complet_pays nom complet du pays / petr\npays_type indication pays ou Petr\npays_siren code SIREN en cas de Petr,\nid_pays identifiant du pays /petr\nid_epci : code siren de l’EPCI,\nepci_nom_complet nom de l’EPCI\nepci_nature_juridique nature juridique de l’EPCI\nepci_regime_fiscal regime fiscal de l’EPCI\nepci_nombre_commune_regroupe nombre de commune de l’EPCI\nepci_pop_totale vide\nepci_pop_municipale population municipale 2019\nid_scot : identifiant du SCOT\nscot_nom_complet  nom complet du SCOT\nscot_nature_juridique nature juridique du SCOT\nnomscot_court nom court du SCOT\nid_pnr identifiant du PNR\nnompnr_court nom du PNR\nid_massif identifiant du massif\nlib_massif nom du massif\nid_ze identifiant de la zone d’emploi 2020\nlib_ze nom de la zone d’emploi 2020\nlib_gal nom du GAL\nid_gal identifiant du GAL\npmun_rp2020 population municipale RP2020,\npmun_rp2019 population municipale RP2019,\npmun_rp2018 population municipale RP2018,\npmun_rp2017 population municipale RP2017,\npmun_rp2016 population municipale RP2016,\npmun_rp2015 population municipale RP2015,\npmun_rp2014, population municipale RP2014\npmun_rp2013 : population municipale RP2013\npmun_rp2012 : population municipale RP2012\npmun_rp2011 : population municipale RP2011\npmun_rp2010 : population municipale RP2010\npmun_rp2009 : population municipale RP2009\npmun_rp2008 : population municipale RP2008\npmun_rp2006 : population municipale RP2006\npsdc99 population sans double compte 1999\npsdc90 population sans double compte 1990,\npsdc82 population sans double compte 1982,\npsdc75 population sans double compte 1975,\npsdc68 population sans double compte 1968,\npsdc62 population sans double compte 1962,\ncode_bassin_vie code bassin de vie\nlib_bassin_vie nom du bassin de vie\nlib_ville_centre_bassin_vie nom de la ville centre du bassin de vie\ntypo_bassin_vie type de bassin de vie\nuu2020 identifiant de l’unité urbaine 2020\nuu2020_lib nom de l’unité urbaine 2020\nuu2020_type_com type de commune de l’unité urbaine\nuu2020_statut_2017 : Statut de la commune dans l'unité urbaine\nStatut de la commune : Ce code est calculé en fonction de la population au recensement 2017.\nH - Hors unité urbaine\nC - Ville-centre\nB - Banlieue\nI - Ville isolée\nxmin84 double precision,\nxmax84 double precision,\nymin84 double precision,\nymax84 double precision",
    "license_title": null,
    "extras": [
      {
        "value": "[]",
        "key": "access_constraints"
      },
      {
        "value": "8.2",
        "key": "bbox-east-long"
      },
      {
        "value": "50.2",
        "key": "bbox-north-lat"
      },
      {
        "value": "47.4",
        "key": "bbox-south-lat"
      },
      {
        "value": "3.3",
        "key": "bbox-west-long"
      },
      {
        "value": "mvd@grandest.fr",
        "key": "contact-email"
      },
      {
        "value": "[]",
        "key": "coupled-resource"
      },
      {
        "value": "[{\"type\": \"creation\", \"value\": \"2016-01-01\"}, {\"type\": \"edition\", \"value\": \"2023-06-13\"}, {\"type\": \"publication\", \"value\": \"\"}]",
        "key": "dataset-reference-date"
      },
      {
        "value": "{100000}",
        "key": "equivalent-scale"
      },
      {
        "value": "continual",
        "key": "frequency-of-update"
      },
      {
        "value": "Illustration Limite communale",
        "key": "graphic-preview-description"
      },
      {
        "value": "https://www.geograndest.fr/metadata/region-grand-est/FR-200052264-COMMUNE-GRAND-EST/FR-200052264-COMMUNE-GRAND-EST.jpg",
        "key": "graphic-preview-file"
      },
      {
        "value": "FR-200052264-Commune_Grand_Est",
        "key": "guid"
      },
      {
        "value": "[\"Licence ouverte \\\"Etalab\\\" V2\"]",
        "key": "licence"
      },
      {
        "value": "Donnée obtenue par fusion des polygones des communes de la BD AdminExpress® de l'IGN (géométrie 2018)",
        "key": "lineage"
      },
      {
        "value": "2023-06-13",
        "key": "metadata-date"
      },
      {
        "value": "fre",
        "key": "metadata-language"
      },
      {
        "value": "",
        "key": "progress"
      },
      {
        "value": "dataset",
        "key": "resource-type"
      },
      {
        "value": "{\"contact-info\": {\"city\": \"Strasbourg\", \"phone\": \"03 26 70 31 85\", \"address\": \"1, place Adrien Zeller\", \"online-resource\": \"\", \"postal-code\": \"67070\", \"email\": \"mvd@grandest.fr\"}, \"role\": \"owner\", \"organisation-name\": \"R\\u00e9gion Grand Est / Service Management et Valorisation de la Donn\\u00e9es\", \"individual-name\": \"\", \"position-name\": \"\"}",
        "key": "responsible-organisation-1"
      },
      {
        "value": "[{\"name\": \"R\\u00e9gion Grand Est / Service Management et Valorisation de la Donn\\u00e9es\", \"roles\": [\"owner\"]}]",
        "key": "responsible-party"
      },
      {
        "value": "{\"type\": \"Polygon\", \"coordinates\": [[[3.3, 47.4], [8.2, 47.4], [8.2, 50.2], [3.3, 50.2], [3.3, 47.4]]]}",
        "key": "spatial"
      },
      {
        "value": "",
        "key": "spatial-data-service-type"
      },
      {
        "value": "RGF93 – Lambert 93 (EPSG:2154)",
        "key": "spatial-reference-system"
      },
      {
        "value": "vector",
        "key": "spatial-representation-type"
      },
      {
        "value": "true",
        "key": "spatial_harvester"
      },
      {
        "value": "\"Licence ouverte \\\"Etalab\\\" V2\"",
        "key": "use-constraints-1"
      },
      {
        "value": "8138a435-7737-4f65-8280-b492959a2273",
        "key": "harvest_object_id"
      },
      {
        "value": "794b1c09-e13a-44bb-8882-7f82dcee4097",
        "key": "harvest_source_id"
      },
      {
        "value": "region-grand-est",
        "key": "harvest_source_title"
      }
    ],
    "organization": {
      "description": "",
      "title": "region-grand-est",
      "created": "2021-03-11T14:41:37.576419",
      "approval_status": "approved",
      "is_organization": true,
      "state": "active",
      "image_url": "",
      "revision_id": "733e7894-2e08-4ecd-b6ff-8ee0257f727b",
      "type": "organization",
      "id": "088032c5-e519-49fa-b1a1-b421bbfe7be5",
      "name": "region-grand-est"
    },
    "revision_id": "b645df5e-68dc-479d-8839-18e214dddd5f"
  }
}
```

### Export RDF/DCAT OpenDataSoft

https://data.rennesmetropole.fr/api/v2/catalog/exports/dcat?lang=fr&where=dataset_id:%27principaux-etablissements-denseignement-superieur%27

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rdf:RDF xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:dcterms="http://purl.org/dc/terms/"
  xmlns:dctype="http://purl.org/dc/dcmitype/" xmlns:dcat="http://www.w3.org/ns/dcat#"
  xmlns:foaf="http://xmlns.com/foaf/0.1/" xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
  xmlns:rdfs="http://www.w3.org/2000/01/rdf-schema#" xmlns:vcard="http://www.w3.org/2006/vcard/ns#"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema#" xmlns:skos="http://www.w3.org/2004/02/skos/core#">
  <rdf:Description rdf:about="https://data.rennesmetropole.fr/api/v2/catalog/datasets/">
    <rdf:type rdf:resource="http://www.w3.org/ns/dcat#Catalog" />
    <dcterms:title><![CDATA[rennes-metropole catalog]]></dcterms:title>
    <dcterms:description><![CDATA[rennes-metropole catalog]]></dcterms:description>
    <dcterms:language rdf:resource="http://id.loc.gov/vocabulary/iso639-1/fr" />
    <foaf:homepage>
      <foaf:Document rdf:about="https://data.rennesmetropole.fr">
        <rdf:type rdf:resource="http://xmlns.com/foaf/0.1/Document" />
      </foaf:Document>
    </foaf:homepage>
    <dcat:dataset>
      <dcat:Dataset
        rdf:about="https://data.rennesmetropole.fr/api/v2/catalog/datasets/principaux-etablissements-denseignement-superieur">
        <dcterms:description xml:lang="fr"><![CDATA[<p>Caractéristiques des principaux établissements d'enseignement supérieur. Situation à date.</p>]]></dcterms:description>
        <dcterms:identifier>principaux-etablissements-denseignement-superieur@rennes-metropole</dcterms:identifier>
        <rdf:type rdf:resource="dctype:Dataset" />
        <rdf:type rdf:resource="http://www.w3.org/ns/dcat#Dataset" />
        <dcterms:issued rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">2021-12-29T00:00:00</dcterms:issued>
        <dcterms:date rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">2021-12-29T00:00:00</dcterms:date>
        <dcterms:modified rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">
          2018-04-25T08:16:43+00:00</dcterms:modified>
        <dcterms:creator
          rdf:resource="https://data.rennesmetropole.fr/explore/?refine.dcat.creator=Minist%C3%A8re+de+l%27Enseignement+sup%C3%A9rieur%2C+de+la+Recherche+et+de+l%27Innovation+%3E+Sous-direction+des+Syst%C3%A8mes+d%27information+et+%C3%A9tudes+statistiques" />
        <dcterms:publisher>
          <foaf:Agent
            rdf:about="https://data.rennesmetropole.fr/explore/?refine.publisher=Minist%C3%A8re+de+l%27Enseignement+sup%C3%A9rieur%2C+de+la+Recherche+et+de+l%27Innovation">
            <foaf:name>Ministère de l&#x27;Enseignement supérieur, de la Recherche et de
              l&#x27;Innovation</foaf:name>
          </foaf:Agent>
        </dcterms:publisher>
        <dcterms:contributor
          rdf:resource="https://data.rennesmetropole.fr/explore/?refine.publisher=Minist%C3%A8re+de+l%27Enseignement+sup%C3%A9rieur%2C+de+la+Recherche+et+de+l%27Innovation" />
        <dcterms:license>
          <dcterms:LicenseDocument
            rdf:about="https://www.etalab.gouv.fr/wp-content/uploads/2017/04/ETALAB-Licence-Ouverte-v2.0.pdf">
            <rdf:type rdf:resource="http://purl.org/dc/terms/LicenseDocument" />
          </dcterms:LicenseDocument>
        </dcterms:license>
        <dcterms:rights
          rdf:resource="https://www.etalab.gouv.fr/wp-content/uploads/2017/04/ETALAB-Licence-Ouverte-v2.0.pdf" />
        <dcat:landingPage>
          <foaf:Document
            rdf:about="https://data.rennesmetropole.fr/explore/dataset/principaux-etablissements-denseignement-superieur/">
            <rdf:type rdf:resource="http://xmlns.com/foaf/0.1/Document" />
          </foaf:Document>
        </dcat:landingPage>
        <dcterms:title xml:lang="fr">Principaux établissements d&#x27;enseignement supérieur -
          Rennes Métropole</dcterms:title>
        <dcterms:language>
          <dcterms:LinguisticSystem rdf:about="http://id.loc.gov/vocabulary/iso639-1/fr">
            <rdf:type rdf:resource="http://purl.org/dc/terms/LinguisticSystem" />
          </dcterms:LinguisticSystem>
        </dcterms:language>
        <dcat:keyword xml:lang="fr">établissement</dcat:keyword>
        <dcat:keyword xml:lang="fr">enseignement supérieur</dcat:keyword>
        <dcat:keyword xml:lang="fr">formation</dcat:keyword>
        <dcat:keyword xml:lang="fr">siret</dcat:keyword>
        <dcat:keyword xml:lang="fr">universités</dcat:keyword>
        <dcat:keyword xml:lang="fr">université</dcat:keyword>
        <dcat:keyword xml:lang="fr">établissements scolaires</dcat:keyword>
        <dcterms:accrualPeriodicity>
          <dcterms:Frequency rdf:about="En continu">
            <rdf:type rdf:resource="http://purl.org/dc/terms/Frequency" />
          </dcterms:Frequency>
        </dcterms:accrualPeriodicity>
        <dcat:contactPoint>
          <vcard:Organization>
            <rdf:type rdf:resource="http://www.w3.org/2006/vcard/ns#Kind" />
            <vcard:hasEmail rdf:resource="mailto:dataesr@recherche.gouv.fr" />
          </vcard:Organization>
        </dcat:contactPoint>
        <dcat:theme>
          <skos:Concept rdf:about="https://data.rennesmetropole.fr/explore/?refine.theme=Education">
            <rdf:type rdf:resource="http://www.w3.org/2004/02/skos/core#Concept" />
            <skos:prefLabel>Education</skos:prefLabel>
          </skos:Concept>
        </dcat:theme>
        <dcterms:subject
          rdf:resource="https://data.rennesmetropole.fr/explore/?refine.theme=Education" />
        <dcterms:spatial rdf:resource="France entière et hors territoire" />
        <dcterms:coverage rdf:resource="France entière et hors territoire" />
        <dcat:distribution>
          <dcat:Distribution
            rdf:about="https://data.rennesmetropole.fr/api/v2/catalog/datasets/principaux-etablissements-denseignement-superieur-json">
            <rdf:type rdf:resource="http://www.w3.org/ns/dcat#Distribution" />
            <dcterms:title xml:lang="fr">json</dcterms:title>
            <dcterms:description xml:lang="fr">Principaux établissements d&#x27;enseignement
              supérieur - Rennes Métropole (json)</dcterms:description>
            <dcat:accessURL
              rdf:resource="https://data.rennesmetropole.fr/api/v2/catalog/datasets/principaux-etablissements-denseignement-superieur/exports/json" />
            <dcat:downloadURL
              rdf:resource="https://data.rennesmetropole.fr/api/v2/catalog/datasets/principaux-etablissements-denseignement-superieur/exports/json" />
            <dcterms:format>
              <dcterms:MediaTypeOrExtent
                rdf:about="https://www.iana.org/assignments/media-types/application/json">
                <rdf:type rdf:resource="http://purl.org/dc/terms/MediaTypeOrExtent" />
              </dcterms:MediaTypeOrExtent>
            </dcterms:format>
            <dcat:mediaType
              rdf:resource="https://www.iana.org/assignments/media-types/application/json" />
            <dcterms:license>
              <dcterms:LicenseDocument
                rdf:about="https://www.etalab.gouv.fr/wp-content/uploads/2017/04/ETALAB-Licence-Ouverte-v2.0.pdf">
                <rdf:type rdf:resource="http://purl.org/dc/terms/LicenseDocument" />
              </dcterms:LicenseDocument>
            </dcterms:license>
            <dcterms:rights
              rdf:resource="https://www.etalab.gouv.fr/wp-content/uploads/2017/04/ETALAB-Licence-Ouverte-v2.0.pdf" />
            <dcterms:language>
              <dcterms:LinguisticSystem rdf:about="http://id.loc.gov/vocabulary/iso639-1/fr">
                <rdf:type rdf:resource="http://purl.org/dc/terms/LinguisticSystem" />
              </dcterms:LinguisticSystem>
            </dcterms:language>
            <dcterms:issued rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">
              2021-12-29T00:00:00</dcterms:issued>
            <dcterms:date rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">
              2021-12-29T00:00:00</dcterms:date>
            <dcterms:modified rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">
              2018-04-25T08:16:43+00:00</dcterms:modified>
          </dcat:Distribution>
        </dcat:distribution>
        <dcat:distribution>
          <dcat:Distribution
            rdf:about="https://data.rennesmetropole.fr/api/v2/catalog/datasets/principaux-etablissements-denseignement-superieur-csv">
            <rdf:type rdf:resource="http://www.w3.org/ns/dcat#Distribution" />
            <dcterms:title xml:lang="fr">csv</dcterms:title>
            <dcterms:description xml:lang="fr">Principaux établissements d&#x27;enseignement
              supérieur - Rennes Métropole (csv)</dcterms:description>
            <dcat:accessURL
              rdf:resource="https://data.rennesmetropole.fr/api/v2/catalog/datasets/principaux-etablissements-denseignement-superieur/exports/csv" />
            <dcat:downloadURL
              rdf:resource="https://data.rennesmetropole.fr/api/v2/catalog/datasets/principaux-etablissements-denseignement-superieur/exports/csv" />
            <dcterms:format>
              <dcterms:MediaTypeOrExtent
                rdf:about="https://www.iana.org/assignments/media-types/text/csv">
                <rdf:type rdf:resource="http://purl.org/dc/terms/MediaTypeOrExtent" />
              </dcterms:MediaTypeOrExtent>
            </dcterms:format>
            <dcat:mediaType rdf:resource="https://www.iana.org/assignments/media-types/text/csv" />
            <dcterms:license>
              <dcterms:LicenseDocument
                rdf:about="https://www.etalab.gouv.fr/wp-content/uploads/2017/04/ETALAB-Licence-Ouverte-v2.0.pdf">
                <rdf:type rdf:resource="http://purl.org/dc/terms/LicenseDocument" />
              </dcterms:LicenseDocument>
            </dcterms:license>
            <dcterms:rights
              rdf:resource="https://www.etalab.gouv.fr/wp-content/uploads/2017/04/ETALAB-Licence-Ouverte-v2.0.pdf" />
            <dcterms:language>
              <dcterms:LinguisticSystem rdf:about="http://id.loc.gov/vocabulary/iso639-1/fr">
                <rdf:type rdf:resource="http://purl.org/dc/terms/LinguisticSystem" />
              </dcterms:LinguisticSystem>
            </dcterms:language>
            <dcterms:issued rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">
              2021-12-29T00:00:00</dcterms:issued>
            <dcterms:date rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">
              2021-12-29T00:00:00</dcterms:date>
            <dcterms:modified rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">
              2018-04-25T08:16:43+00:00</dcterms:modified>
          </dcat:Distribution>
        </dcat:distribution>
        <dcat:distribution>
          <dcat:Distribution
            rdf:about="https://data.rennesmetropole.fr/api/v2/catalog/datasets/principaux-etablissements-denseignement-superieur-geojson">
            <rdf:type rdf:resource="http://www.w3.org/ns/dcat#Distribution" />
            <dcterms:title xml:lang="fr">geojson</dcterms:title>
            <dcterms:description xml:lang="fr">Principaux établissements d&#x27;enseignement
              supérieur - Rennes Métropole (geojson)</dcterms:description>
            <dcat:accessURL
              rdf:resource="https://data.rennesmetropole.fr/api/v2/catalog/datasets/principaux-etablissements-denseignement-superieur/exports/geojson" />
            <dcat:downloadURL
              rdf:resource="https://data.rennesmetropole.fr/api/v2/catalog/datasets/principaux-etablissements-denseignement-superieur/exports/geojson" />
            <dcterms:format>
              <dcterms:MediaTypeOrExtent
                rdf:about="https://www.iana.org/assignments/media-types/application/json">
                <rdf:type rdf:resource="http://purl.org/dc/terms/MediaTypeOrExtent" />
              </dcterms:MediaTypeOrExtent>
            </dcterms:format>
            <dcat:mediaType
              rdf:resource="https://www.iana.org/assignments/media-types/application/json" />
            <dcterms:license>
              <dcterms:LicenseDocument
                rdf:about="https://www.etalab.gouv.fr/wp-content/uploads/2017/04/ETALAB-Licence-Ouverte-v2.0.pdf">
                <rdf:type rdf:resource="http://purl.org/dc/terms/LicenseDocument" />
              </dcterms:LicenseDocument>
            </dcterms:license>
            <dcterms:rights
              rdf:resource="https://www.etalab.gouv.fr/wp-content/uploads/2017/04/ETALAB-Licence-Ouverte-v2.0.pdf" />
            <dcterms:language>
              <dcterms:LinguisticSystem rdf:about="http://id.loc.gov/vocabulary/iso639-1/fr">
                <rdf:type rdf:resource="http://purl.org/dc/terms/LinguisticSystem" />
              </dcterms:LinguisticSystem>
            </dcterms:language>
            <dcterms:issued rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">
              2021-12-29T00:00:00</dcterms:issued>
            <dcterms:date rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">
              2021-12-29T00:00:00</dcterms:date>
            <dcterms:modified rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">
              2018-04-25T08:16:43+00:00</dcterms:modified>
          </dcat:Distribution>
        </dcat:distribution>
        <dcat:distribution>
          <dcat:Distribution
            rdf:about="https://data.rennesmetropole.fr/api/v2/catalog/datasets/principaux-etablissements-denseignement-superieur-shp">
            <rdf:type rdf:resource="http://www.w3.org/ns/dcat#Distribution" />
            <dcterms:title xml:lang="fr">shp</dcterms:title>
            <dcterms:description xml:lang="fr">Principaux établissements d&#x27;enseignement
              supérieur - Rennes Métropole (shp)</dcterms:description>
            <dcat:accessURL
              rdf:resource="https://data.rennesmetropole.fr/api/v2/catalog/datasets/principaux-etablissements-denseignement-superieur/exports/shp" />
            <dcat:downloadURL
              rdf:resource="https://data.rennesmetropole.fr/api/v2/catalog/datasets/principaux-etablissements-denseignement-superieur/exports/shp" />
            <dcterms:format>
              <dcterms:MediaTypeOrExtent
                rdf:about="https://www.iana.org/assignments/media-types/application/zip">
                <rdf:type rdf:resource="http://purl.org/dc/terms/MediaTypeOrExtent" />
              </dcterms:MediaTypeOrExtent>
            </dcterms:format>
            <dcat:mediaType
              rdf:resource="https://www.iana.org/assignments/media-types/application/zip" />
            <dcterms:license>
              <dcterms:LicenseDocument
                rdf:about="https://www.etalab.gouv.fr/wp-content/uploads/2017/04/ETALAB-Licence-Ouverte-v2.0.pdf">
                <rdf:type rdf:resource="http://purl.org/dc/terms/LicenseDocument" />
              </dcterms:LicenseDocument>
            </dcterms:license>
            <dcterms:rights
              rdf:resource="https://www.etalab.gouv.fr/wp-content/uploads/2017/04/ETALAB-Licence-Ouverte-v2.0.pdf" />
            <dcterms:language>
              <dcterms:LinguisticSystem rdf:about="http://id.loc.gov/vocabulary/iso639-1/fr">
                <rdf:type rdf:resource="http://purl.org/dc/terms/LinguisticSystem" />
              </dcterms:LinguisticSystem>
            </dcterms:language>
            <dcterms:issued rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">
              2021-12-29T00:00:00</dcterms:issued>
            <dcterms:date rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">
              2021-12-29T00:00:00</dcterms:date>
            <dcterms:modified rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">
              2018-04-25T08:16:43+00:00</dcterms:modified>
          </dcat:Distribution>
        </dcat:distribution>
      </dcat:Dataset>
    </dcat:dataset>
    <dcat:service>
      <dcat:DataService rdf:about="https://data.rennesmetropole.fr/api/v2">
        <dcterms:title xml:lang="en"><![CDATA[Explore API v2]]></dcterms:title>
        <dcterms:identifier>https://data.rennesmetropole.fr/api/v2</dcterms:identifier>
        <dcat:endpointURL rdf:resource="https://data.rennesmetropole.fr/api/v2" />
        <dcat:endpointDescription rdf:resource="https://data.rennesmetropole.fr/api/v2/swagger.json" />
        <dcat:landingPage rdf:resource="https://data.rennesmetropole.fr/api/v2/console" />
        <dcat:servesDataset
          rdf:resource="https://data.rennesmetropole.fr/api/v2/catalog/datasets/principaux-etablissements-denseignement-superieur" />
      </dcat:DataService>
    </dcat:service>
  </rdf:Description>
</rdf:RDF>
```

### Analyse LL sur le sujet type de ressource

INSPIRE ne modélise pas vraiment, tout ce que tu as c'est une définition très large. "« ensemble de séries de données géographiques » : une compilation de séries de données géographiques partageant la même spécification de produit." [1]. Pour le reste, il n'y a rien qui distingue concrètement un ensemble de séries d'une série dans la réglementation INSPIRE, hormis la valeur de la métadonnée "Type de la ressource". Dans DCAT v3, dcat:DatasetSeries est une sous-classe de dcat:Dataset, et sur le principe cette vision me semble assez proche de celle d'INSPIRE.  
  
INSPIRE est clair sur l'existence d'une relation entre l'ensemble et les séries qui le composent, mais cette relation n'est pas mentionnée dans les métadonnées obligatoires, ni pour l'ensemble, ni pour les séries. Ce qui explique sans doute pourquoi le Guide de saisie des éléments de métadonnées INSPIRE du CNIG n'en parle pas non plus. Il y a effectivement plus de choses dans le Guide de gestion des catalogues de métadonnées INSPIRE [3]. En pratique, celui-ci recommande de matérialiser la relation dans les XML, pour les séries uniquement, en utilisant identificationInfo.citation.serie. Mais je ne connais pas de catalogue qui ait fait ce choix. Géo-IDE Catalogue utilise identificationInfo.aggregationInfo pour matérialiser la relation dans les métadonnées du parent uniquement - exemple [4]. Je ne sais pas si ça vient de Prodige ou de GeoNetwork, mais dans d'autres catalogues comme datAra la relation est matérialisée avec parentIdentifier dans les fiches de métadonnées des séries : fiche d'un ensemble [5] ; XML de l'ensemble [6] ; fiche d'une des séries de l'ensemble [7] ; XML de la série [8]. GéoIDE Catalogue se sert aussi de parentIdentifier, mais pour autre chose. Je crois que ça identifie la fiche de métadonnées standard qui a servi de modèle - exemple de deux fiches de métadonnées d'ensembles basées sur le même modèle "plan de prévention des risques" : [9] et [10].  
  
Dans le code d'Ecosphères, j'avais uniquement traité le cas de GéoIDE [11]. Outre la disponibilité des relations dans les XML, les deux points problématiques étaient que :  
- Ce n'est pas parce qu'il y a une relation que les métadonnées de l'objet visé sont également exposées.  
- Sauf à faire en sorte de moissonner séparément les séries et les ensembles (possible avec des filtres dans la requête au CSW, c'est ce que j'avais fait), on ne maîtrise pas l'ordre dans lequel sont récupérées les fiches. Comme les relations ne sont à ma connaissance jamais matérialisées à la fois sur l'ensemble et sur les séries, il y a toujours le risque de traiter la fiche de l'objet qui contient la référence avant d'avoir moissonné celle de l'objet qu'elle vise. Pas idéal quand on aimerait recréer la relation dans le nouveau catalogue.  

[1] [https://eur-lex.europa.eu/legal-content/FR/TXT/?uri=CELEX%3A02008R1205-20081224](https://eur-lex.europa.eu/legal-content/FR/TXT/?uri=CELEX%3A02008R1205-20081224)  
[2] [http://cnig.gouv.fr/IMG/pdf/guide-de-saisie-des-elements-de-metadonnees-inspire-v2.0-1.pdf](http://cnig.gouv.fr/IMG/pdf/guide-de-saisie-des-elements-de-metadonnees-inspire-v2.0-1.pdf)  
[3] [https://cnig.gouv.fr/IMG/documents_wordpress/2014/01/2012-08-20_guide-catalogues-md-inspire-v1.0.pdf#page=11](https://cnig.gouv.fr/IMG/documents_wordpress/2014/01/2012-08-20_guide-catalogues-md-inspire-v1.0.pdf#page=11)  
[4] [https://ogc.geo-ide.developpement-durable.gouv.fr/csw/all-dataset?REQUEST=GetRecordById&SERVICE=CSW&VERSION=2.0.2&RESULTTYPE=results&elementSetName=full&TYPENAMES=gmd:MD_Metadata&OUTPUTSCHEMA=http://www.isotc211.org/2005/gmd&ID=fr-120066022-ldd-a2086c57-1888-4270-a5b7-84c67b83585e](https://ogc.geo-ide.developpement-durable.gouv.fr/csw/all-dataset?REQUEST=GetRecordById&SERVICE=CSW&VERSION=2.0.2&RESULTTYPE=results&elementSetName=full&TYPENAMES=gmd:MD_Metadata&OUTPUTSCHEMA=http://www.isotc211.org/2005/gmd&ID=fr-120066022-ldd-a2086c57-1888-4270-a5b7-84c67b83585e)  
[5] [https://catalogue.datara.gouv.fr/geonetwork/srv/fre/catalog.search#/metadata/fff02ef4-8918-4d42-a6ab-53a0d83468bf](https://catalogue.datara.gouv.fr/geonetwork/srv/fre/catalog.search#/metadata/fff02ef4-8918-4d42-a6ab-53a0d83468bf)  
[6] [https://catalogue.datara.gouv.fr/geonetwork/srv/api/records/fff02ef4-8918-4d42-a6ab-53a0d83468bf/formatters/xml](https://catalogue.datara.gouv.fr/geonetwork/srv/api/records/fff02ef4-8918-4d42-a6ab-53a0d83468bf/formatters/xml)  
[7] [https://catalogue.datara.gouv.fr/geonetwork/srv/fre/catalog.search#/metadata/fff02ef4-8918-4d42-a6ab-53a0d83468bf](https://catalogue.datara.gouv.fr/geonetwork/srv/fre/catalog.search#/metadata/fff02ef4-8918-4d42-a6ab-53a0d83468bf)  
[8] [https://catalogue.datara.gouv.fr/geonetwork/srv/api/records/5b786cc5-0159-4e45-96dd-1ef8564c298a/formatters/xml](https://catalogue.datara.gouv.fr/geonetwork/srv/api/records/5b786cc5-0159-4e45-96dd-1ef8564c298a/formatters/xml)  
[9] [https://ogc.geo-ide.developpement-durable.gouv.fr/csw/all-dataset?REQUEST=GetRecordById&SERVICE=CSW&VERSION=2.0.2&RESULTTYPE=results&elementSetName=full&TYPENAMES=gmd:MD_Metadata&OUTPUTSCHEMA=http://www.isotc211.org/2005/gmd&ID=fr-120066022-ldd-a2086c57-1888-4270-a5b7-84c67b83585e](https://ogc.geo-ide.developpement-durable.gouv.fr/csw/all-dataset?REQUEST=GetRecordById&SERVICE=CSW&VERSION=2.0.2&RESULTTYPE=results&elementSetName=full&TYPENAMES=gmd:MD_Metadata&OUTPUTSCHEMA=http://www.isotc211.org/2005/gmd&ID=fr-120066022-ldd-a2086c57-1888-4270-a5b7-84c67b83585e)  
[10] [https://ogc.geo-ide.developpement-durable.gouv.fr/csw/all-dataset?REQUEST=GetRecordById&SERVICE=CSW&VERSION=2.0.2&RESULTTYPE=results&elementSetName=full&TYPENAMES=gmd:MD_Metadata&OUTPUTSCHEMA=http://www.isotc211.org/2005/gmd&ID=fr-120066022-ldd-bca2eac8-583e-481b-a300-fd4c7266afe5](https://ogc.geo-ide.developpement-durable.gouv.fr/csw/all-dataset?REQUEST=GetRecordById&SERVICE=CSW&VERSION=2.0.2&RESULTTYPE=results&elementSetName=full&TYPENAMES=gmd:MD_Metadata&OUTPUTSCHEMA=http://www.isotc211.org/2005/gmd&ID=fr-120066022-ldd-bca2eac8-583e-481b-a300-fd4c7266afe5)  
[11] [https://github.com/ecolabdata/ckanext-ecospheres/blob/9c849a4089a7ba6ce94c56faf02869cea3f96f51/ckanext/ecospheres/spatial/harvester.py#L387](https://github.com/ecolabdata/ckanext-ecospheres/blob/9c849a4089a7ba6ce94c56faf02869cea3f96f51/ckanext/ecospheres/spatial/harvester.py#L387)