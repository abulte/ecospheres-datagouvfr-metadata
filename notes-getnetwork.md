https://github.com/etalab/data.gouv.fr/issues/913

Côté OGC, tu peux regarder [demo georchestra](https://demo.georchestra.org/ogc-api-records/collections/main/items?f=dcat) ou [demo naturefrance](https://sib1.dev.pigeosolutions.fr/geonetwork/api/collections/97137d05-3901-490c-bce4-3a3c7b70616b/items?f=dcat) 
Côté CSW, tu peux regarder [demo geo2france](https://dev.geo2france.fr/geonetwork/virtual-geo2france/eng/csw?SERVICE=CSW&VERSION=2.0.2&REQUEST=GetRecords&outputSchema=http://www.w3.org/ns/dcat%23&typenames=gmd:MD_Metadata&elementSetName=full&resultType=results&startPosition=1) ou [autre demo naturefrance](https://data.naturefrance.fr/geonetwork/srv/eng/csw?SERVICE=CSW&VERSION=2.0.2&REQUEST=GetRecords&outputSchema=http://www.w3.org/ns/dcat%23&typenames=gmd:MD_Metadata&elementSetName=full&resultType=results&startPosition=1)

Fichiers de test CSW/DCAT Geonetwork v4 https://github.com/opendatateam/udata/blob/d1117eec549cf98555140ba7c6ce3b071e9090dd/udata/harvest/tests/csw_dcat/geonetworkv4-page-1.xml

```xml
<dcat:Dataset
  rdf:about="http://localhost:8080/geonetwork/srv/resources/datasets/https://www.geo2france.fr/chemins_ruraux_tests">
  <dct:identifier>https://www.geo2france.fr/chemins_ruraux_tests</dct:identifier>
  <dct:title>Identification des chemins ruraux</dct:title>
  <dct:abstract>Identification des chemins ruraux, sur des secteurs de tests (Houchin, Longfossé,
    Marck, Mont Bernachon, Saint Hilaire Cottes, Servins) par l'association des chemins ruraux en
    Hauts-de-France.</dct:abstract>
  <dcat:keyword>Biodiversité</dcat:keyword>
  <dcat:keyword>Nature</dcat:keyword>
  <dcat:theme
    rdf:resource="http://localhost:8080/geonetwork/srv/resources/registries/vocabularies/GEMET%20-%20INSPIRE%20themes%2C%20version%201.0/concepts/D%C3%A9nominations%20g%C3%A9ographiques" />
  <dcat:theme
    rdf:resource="http://localhost:8080/geonetwork/srv/resources/registries/vocabularies/GEMET%20-%20Concepts%2C%20version%202.4/concepts/sentier%20pedestre" />
  <dcat:theme
    rdf:resource="http://localhost:8080/geonetwork/srv/resources/registries/vocabularies/R%C3%A9gion/concepts/HAUTS-DE-FRANCE" />
  <dcat:theme
    rdf:resource="https://inspire.ec.europa.eu/metadata-codelist/TopicCategory/environment" />
  <foaf:thumbnail rdf:resource="https://www.geo2france.fr/public/vignettes_geonetwork/chemins.jpg" />
  <dct:spatial>
    <ogc:Polygon
      xmlns:ogc="http://www.opengis.net/rdf#">
      <geo:asWKT
        xmlns:geo="http://www.opengis.net/ont/geosparql#"
        rdf:datatype="http://www.opengis.net/rdf#wktLiteral">Polygon((1.38022461103 48.8372121327,
        1.38022461103 51.0890003105, 4.25573382669 51.0890003105, 4.25573382669 48.8372121327,
        1.38022461103 48.8372121327))
      </geo:asWKT>
    </ogc:Polygon>
  </dct:spatial>
  <dct:issued>2019-01-01</dct:issued>
  <dct:publisher
    rdf:resource="http://localhost:8080/geonetwork/srv/resources/organizations/G%C3%A9o2France" />
  <dcat:granularity>1000</dcat:granularity>
  <dcat:distribution
    rdf:resource="https://dev.geo2france.fr/geonetwork/records/33ba7668-5a93-47af-9e2f-8a72620b83b3#OGC%3AWMS-Secteur_HouchinFINAL" />
  <dcat:distribution
    rdf:resource="https://dev.geo2france.fr/geonetwork/records/33ba7668-5a93-47af-9e2f-8a72620b83b3#OGC%3AWMS-Secteur_Longfoss%C3%A9FINAL" />
  <dcat:distribution
    rdf:resource="https://dev.geo2france.fr/geonetwork/records/33ba7668-5a93-47af-9e2f-8a72620b83b3#OGC%3AWMS-Secteur_MarckFINAL" />
  <dcat:distribution
    rdf:resource="https://dev.geo2france.fr/geonetwork/records/33ba7668-5a93-47af-9e2f-8a72620b83b3#OGC%3AWMS-Secteur_MontBernanchonFINAL" />
  <dcat:distribution
    rdf:resource="https://dev.geo2france.fr/geonetwork/records/33ba7668-5a93-47af-9e2f-8a72620b83b3#OGC%3AWMS-Secteur_SaintHilaireCottesFINAL" />
  <dcat:distribution
    rdf:resource="https://dev.geo2france.fr/geonetwork/records/33ba7668-5a93-47af-9e2f-8a72620b83b3#OGC%3AWMS-Secteur_ServinsFINAL" />
  <dcat:distribution
    rdf:resource="https://dev.geo2france.fr/geonetwork/records/33ba7668-5a93-47af-9e2f-8a72620b83b3#OGC%3AWFS-asso_chemin_ruraux%3ASecteur_HouchinFINAL" />
  <dcat:distribution
    rdf:resource="https://dev.geo2france.fr/geonetwork/records/33ba7668-5a93-47af-9e2f-8a72620b83b3#OGC%3AWFS-asso_chemin_ruraux%3ASecteur_Longfoss%C3%A9FINAL" />
  <dcat:distribution
    rdf:resource="https://dev.geo2france.fr/geonetwork/records/33ba7668-5a93-47af-9e2f-8a72620b83b3#OGC%3AWFS-asso_chemin_ruraux%3ASecteur_MarckFINAL" />
  <dcat:distribution
    rdf:resource="https://dev.geo2france.fr/geonetwork/records/33ba7668-5a93-47af-9e2f-8a72620b83b3#OGC%3AWFS-asso_chemin_ruraux%3ASecteur_MontBernanchonFINAL" />
  <dcat:distribution
    rdf:resource="https://dev.geo2france.fr/geonetwork/records/33ba7668-5a93-47af-9e2f-8a72620b83b3#OGC%3AWFS-asso_chemin_ruraux%3ASecteur_SaintHilaireCottesFINAL" />
  <dcat:distribution
    rdf:resource="https://dev.geo2france.fr/geonetwork/records/33ba7668-5a93-47af-9e2f-8a72620b83b3#OGC%3AWFS-asso_chemin_ruraux%3ASecteur_ServinsFINAL" />
  <dcat:dataQuality />
</dcat:Dataset>
<skos:Concept
  rdf:about="http://localhost:8080/geonetwork/srv/resources/registries/vocabularies/GEMET%20-%20INSPIRE%20themes%2C%20version%201.0/concepts/D%C3%A9nominations%20g%C3%A9ographiques">
  <skos:inScheme
    rdf:resource="http://localhost:8080/geonetwork/srv/resources/registries/vocabularies/GEMET%20-%20INSPIRE%20themes%2C%20version%201.0" />
  <skos:prefLabel>Dénominations géographiques</skos:prefLabel>
</skos:Concept>
<skos:Concept
  rdf:about="http://localhost:8080/geonetwork/srv/resources/registries/vocabularies/GEMET%20-%20Concepts%2C%20version%202.4/concepts/sentier%20pedestre">
  <skos:inScheme
    rdf:resource="http://localhost:8080/geonetwork/srv/resources/registries/vocabularies/GEMET%20-%20Concepts%2C%20version%202.4" />
  <skos:prefLabel>sentier pedestre</skos:prefLabel>
</skos:Concept>
<skos:Concept
  rdf:about="http://localhost:8080/geonetwork/srv/resources/registries/vocabularies/R%C3%A9gion/concepts/HAUTS-DE-FRANCE">
  <skos:inScheme
    rdf:resource="http://localhost:8080/geonetwork/srv/resources/registries/vocabularies/R%C3%A9gion" />
  <skos:prefLabel>HAUTS-DE-FRANCE</skos:prefLabel>
</skos:Concept>
<dcat:Distribution
  rdf:about="https://dev.geo2france.fr/geonetwork/records/33ba7668-5a93-47af-9e2f-8a72620b83b3#OGC%3AWMS-Secteur_HouchinFINAL">
  <dcat:accessURL>https://www.geo2france.fr/geoserver/asso_chemin_ruraux/ows</dcat:accessURL>
  <dct:title>Secteur_HouchinFINAL</dct:title>
  <dct:format>OGC:WMS</dct:format>
</dcat:Distribution>
<foaf:Organization
  rdf:about="http://localhost:8080/geonetwork/srv/resources/organizations/G%C3%A9o2France">
  <foaf:name>Géo2France</foaf:name>
  <foaf:member
    rdf:resource="http://localhost:8080/geonetwork/srv/resources/persons/contact%40geo2france.fr" />
</foaf:Organization>
<foaf:Agent
  rdf:about="http://localhost:8080/geonetwork/srv/resources/persons/contact%40geo2france.fr">
  <foaf:mbox rdf:resource="mailto:contact@geo2france.fr" />
</foaf:Agent>
```


NatureFrance OGC

```xml
      <dcat:Dataset
        rdf:about="https://sib1.dev.pigeosolutions.fr/geonetwork/api/collections/main/items/d423332c-9eeb-4405-8054-317565d8e80f#resource">
        <dct:title>Copy of record Référentiel des méthodes et protocoles de collecte - CAMPanule
          created at 2023-06-17T14:15:51.016Z[Etc/UTC]</dct:title>
        <dct:description>Dans le cadre de la structuration des connaissances sur la biodiversité par
          le SINP, le projet CAMPanule (CAtalogue de Méthodes et Protocoles) a pour objectif de
          recenser et caractériser les techniques, méthodes et protocoles de collecte de données
          naturalistes en France. En constituant une liste de référence partagée, mobilisable lors
          de la saisie des observations naturalistes, ce catalogue peut permettre d'harmoniser la
          description des modalités de collecte des données, et ainsi faciliter l'analyse et la
          mobilisation des connaissances produites. En amont de la production, lors de l'élaboration
          d'une démarche, disposer d'un catalogue de référence peut également éclairer les
          opérateurs sur la diversité des méthodes existantes, leurs caractéristiques et
          contraintes.
          Données gérées dans le cadre du SINP.</dct:description>
        <dct:created>2022-01-17T00:00:00Z</dct:created>
        <dct:modified>2023-06-20T15:17:30.265Z</dct:modified>
        <dct:language>
          <skos:Concept rdf:about="http://publications.europa.eu/resource/authority/language/FRE">
            <skos:prefLabel>fre</skos:prefLabel>
            <rdf:type rdf:resource="http://purl.org/dc/terms/LinguisticSystem" />
          </skos:Concept>
        </dct:language>
        <dcat:contactPoint>
          <vcard:Kind>
            <vcard:title>PATRINAT</vcard:title>
            <vcard:role>pointOfContact</vcard:role>
            <vcard:hasEmail></vcard:hasEmail>
          </vcard:Kind>
        </dcat:contactPoint>
        <dcat:theme>
          <skos:Concept>
            <skos:prefLabel>État</skos:prefLabel>
          </skos:Concept>
        </dcat:theme>
        <dcat:theme>
          <skos:Concept>
            <skos:prefLabel>Ouverte</skos:prefLabel>
          </skos:Concept>
        </dcat:theme>
        <dcat:theme>
          <skos:Concept>
            <skos:prefLabel>Inventaire du patrimoine naturel</skos:prefLabel>
          </skos:Concept>
        </dcat:theme>
        <dcat:theme>
          <skos:Concept>
            <skos:prefLabel>Espèces</skos:prefLabel>
          </skos:Concept>
        </dcat:theme>
        <dcat:theme>
          <skos:Concept>
            <skos:prefLabel>Habitats et écosystèmes</skos:prefLabel>
          </skos:Concept>
        </dcat:theme>
        <dcat:theme>
          <skos:Concept>
            <skos:prefLabel>Données de référence</skos:prefLabel>
          </skos:Concept>
        </dcat:theme>
        <dct:type>
          <skos:Concept>
            <skos:prefLabel>Dataset</skos:prefLabel>
          </skos:Concept>
        </dct:type>
        <dcat:landingPage>
          <foaf:Document
            rdf:about="https://sib1.dev.pigeosolutions.fr/geonetwork/api/collections/main/items/d423332c-9eeb-4405-8054-317565d8e80f">
            <dct:title>Copy of record Référentiel des méthodes et protocoles de collecte - CAMPanule
              created at 2023-06-17T14:15:51.016Z[Etc/UTC]</dct:title>
          </foaf:Document>
        </dcat:landingPage>
        <dcat:distribution>
          <dcat:Distribution>
            <dcat:accessURL rdf:resource="https://inpn.mnhn.fr/programme/campanule" />
            <dct:title>Base de données CAMPanule</dct:title>
            <dct:description>Téléchargement de la base de données et du rapport d'accompagnement</dct:description>
            <adms:representationTechnique>
              <skos:Concept>
                <skos:prefLabel>WWW:LINK-1.0-http--link</skos:prefLabel>
              </skos:Concept>
            </adms:representationTechnique>
          </dcat:Distribution>
        </dcat:distribution>
        <dct:provenance>
          <dct:ProvenanceStatement>
            <rdfs:label>Le catalogue est développé sous forme d'une base de données qui permet de
              décrire des informations standardisées sur chaque technique, méthode ou protocole
              identifié. Ces informations concernent notamment les objectifs, les cibles, les
              modalités de mise en œuvre et moyens nécessaires, le territoire d'application, etc.,
              et permettent de développer des recherches par critères dans le catalogue. Des
              références bibliographiques et liens d'accès aux documents décrivant précisément les
              méthodes sont également bancarisés.

              https://inpn.mnhn.fr/programme/campanule</rdfs:label>
          </dct:ProvenanceStatement>
        </dct:provenance>
      </dcat:Dataset>
```

NatureFrance CSW

```xml
      <dcat:Dataset rdf:about="http://localhost:8080/geonetwork/srv/resources/datasets/04cd8aa9-77dd-463e-89c7-df3325b03be2">
        <dct:identifier>04cd8aa9-77dd-463e-89c7-df3325b03be2</dct:identifier>
        <dct:title>Référentiel des méthodes et protocoles de collecte - CAMPanule</dct:title>
        <dct:abstract>Dans le cadre de la structuration des connaissances sur la biodiversité par le SINP, le projet CAMPanule (CAtalogue de Méthodes et Protocoles) a pour objectif de recenser et caractériser les techniques, méthodes et protocoles de collecte de données naturalistes en France. En constituant une liste de référence partagée, mobilisable lors de la saisie des observations naturalistes, ce catalogue peut permettre d'harmoniser la description des modalités de collecte des données, et ainsi faciliter l'analyse et la mobilisation des connaissances produites. En amont de la production, lors de l'élaboration d'une démarche, disposer d'un catalogue de référence peut également éclairer les opérateurs sur la diversité des méthodes existantes, leurs caractéristiques et contraintes.
Données gérées dans le cadre du SINP.</dct:abstract>
        <dcat:theme rdf:resource="https://data.naturefrance.fr/thesaurus/opendata#819e8287-4f3f-4298-bb62-0fdf03ff0184" />
        <dcat:theme rdf:resource="https://data.naturefrance.fr/thesaurus/datatype#2c3f1ec6-8181-4ac0-b6ad-8705304fb9d1" />
        <dcat:theme rdf:resource="https://data.naturefrance.fr/thesaurus/thematiques#7d32e245-2e71-45e5-81e9-9c81a29c474f" />
        <dcat:theme rdf:resource="https://data.naturefrance.fr/thesaurus/thematiques#392aacf4-7949-4ae0-94c7-be308c4cbd27" />
        <dcat:theme rdf:resource="https://data.naturefrance.fr/thesaurus/politique_publique#a08cee47-f96b-4b62-82d7-51aa0bcbc26b" />
        <dcat:theme rdf:resource="https://data.naturefrance.fr/thesaurus/dpsir#73949c30-93f8-4b8c-b30e-a56ce40f0f6a" />
        <foaf:thumbnail rdf:resource="https://data.naturefrance.fr/geonetwork/srv/api/records/04cd8aa9-77dd-463e-89c7-df3325b03be2/attachments/campanule-SFigue_sinpt.jpg" />
        <dct:issued>2022-01-17</dct:issued>
        <dct:publisher rdf:resource="http://localhost:8080/geonetwork/srv/resources/organizations/PATRINAT" />
        <dct:language>fre</dct:language>
        <dct:license rdf:resource="https://www.etalab.gouv.fr/licence-ouverte-open-licence">Licence Ouverte version 2.0</dct:license>
        <dct:accessRights rdf:resource="http://inspire.ec.europa.eu/metadatacodelist/LimitationsOnPublicAccess/noLimitations">Pas de restriction d’accès public</dct:accessRights>
        <dcat:distribution rdf:resource="https://data.naturefrance.fr/geonetwork/records/04cd8aa9-77dd-463e-89c7-df3325b03be2#WWW%3ALINK-1.0-http--link-Base%20de%20donn%C3%A9es%20CAMPanule" />
        <dcat:dataQuality>Le catalogue est développé sous forme d'une base de données qui permet de décrire des informations standardisées sur chaque technique, méthode ou protocole identifié. Ces informations concernent notamment les objectifs, les cibles, les modalités de mise en œuvre et moyens nécessaires, le territoire d'application, etc., et permettent de développer des recherches par critères dans le catalogue. Des références bibliographiques et liens d'accès aux documents décrivant précisément les méthodes sont également bancarisés.

https://inpn.mnhn.fr/programme/campanule</dcat:dataQuality>
      </dcat:Dataset>
      <skos:Concept rdf:about="https://data.naturefrance.fr/thesaurus/opendata#819e8287-4f3f-4298-bb62-0fdf03ff0184">
        <skos:inScheme rdf:resource="http://custom.shared.obj.ch/concept#" />
        <skos:prefLabel>Ouverte</skos:prefLabel>
      </skos:Concept>
      <skos:Concept rdf:about="https://data.naturefrance.fr/thesaurus/datatype#2c3f1ec6-8181-4ac0-b6ad-8705304fb9d1">
        <skos:inScheme rdf:resource="http://custom.shared.obj.ch/concept#" />
        <skos:prefLabel>Données de référence</skos:prefLabel>
      </skos:Concept>
      <skos:Concept rdf:about="https://data.naturefrance.fr/thesaurus/thematiques#7d32e245-2e71-45e5-81e9-9c81a29c474f">
        <skos:inScheme rdf:resource="http://geonetwork-opensource.org/Thématiques" />
        <skos:prefLabel>Espèces</skos:prefLabel>
      </skos:Concept>
      <skos:Concept rdf:about="https://data.naturefrance.fr/thesaurus/thematiques#392aacf4-7949-4ae0-94c7-be308c4cbd27">
        <skos:inScheme rdf:resource="http://geonetwork-opensource.org/Thématiques" />
        <skos:prefLabel>Habitats et écosystèmes</skos:prefLabel>
      </skos:Concept>
      <skos:Concept rdf:about="https://data.naturefrance.fr/thesaurus/politique_publique#a08cee47-f96b-4b62-82d7-51aa0bcbc26b">
        <skos:inScheme rdf:resource="http://custom.shared.obj.ch/concept#" />
        <skos:prefLabel>Inventaire du patrimoine naturel</skos:prefLabel>
      </skos:Concept>
      <skos:Concept rdf:about="https://data.naturefrance.fr/thesaurus/dpsir#73949c30-93f8-4b8c-b30e-a56ce40f0f6a">
        <skos:inScheme rdf:resource="http://geonetwork-opensource.org/DPSIR" />
        <skos:prefLabel>État</skos:prefLabel>
      </skos:Concept>
      <dcat:Distribution rdf:about="https://data.naturefrance.fr/geonetwork/records/04cd8aa9-77dd-463e-89c7-df3325b03be2#WWW%3ALINK-1.0-http--link-Base%20de%20donn%C3%A9es%20CAMPanule">
        <dcat:accessURL>https://inpn.mnhn.fr/programme/campanule</dcat:accessURL>
        <dct:title>Base de données CAMPanule</dct:title>
        <dct:format>WWW:LINK-1.0-http--link</dct:format>
      </dcat:Distribution>
      <foaf:Organization rdf:about="http://localhost:8080/geonetwork/srv/resources/organizations/PATRINAT">
        <foaf:name>PATRINAT</foaf:name>
        <foaf:member rdf:resource="http://localhost:8080/geonetwork/srv/resources/persons/d23568e60" />
      </foaf:Organization>
      <foaf:Agent rdf:about="http://localhost:8080/geonetwork/srv/resources/persons/d23568e60">
        <foaf:mbox rdf:resource="mailto:" />
      </foaf:Agent>
```

Geoorchestra OGC

```xml
      <dcat:Dataset
        rdf:about="https://demo.georchestra.org/geonetwork/srv/metadata/fr-120066022-jdd-643b733c-2479-488e-b9d6-5eb502b279aa#resource">
        <dct:title>Table contenant les générateurs ponctuels liés aux servitudes de la
          catégorie AC1 en Pas-de-Calais</dct:title>
        <dct:description>Les servitudes de catégorie AC1 concernent les servitudes de
          protection des monuments historiques classés ou inscrits : - Classement au titre
          des monuments historiques : ces servitudes concernent les immeubles ou les
          parties d'immeubles dont la conservation présente du point de vue de l'histoire
          ou de l'art un intérêt public. Les propriétaires d'immeubles classés ne peuvent
          effectuer de travaux de restauration, de réparation ou de modification sans
          autorisation préalable du préfet de région ou du ministre chargé de la culture.
          - Inscription au titre des monuments historiques : ces servitudes concernent les
          immeubles ou parties d'immeubles qui, sans justifier une demande de classement
          immédiat, présentent un intérêt d'histoire ou d'art suffisant pour en rendre
          désirable la préservation. Les propriétaires d'immeubles inscrits ne peuvent
          procéder à aucune modification sans déclaration préalable ; aucune autorisation
          d'urbanisme ne peut être délivrée sans accord préalable du préfet de région. -
          Immeubles adossés aux immeubles classés et immeubles situés dans le champ de
          visibilité des immeubles classés ou inscrits : 1. Tout immeuble en contact avec
          un immeuble classé, en élévation, au sol ou en sous-sol est considéré comme
          immeuble adossé. Toute partie non protégée au titre des monuments historiques
          d'un immeuble partiellement classé est considérée comme immeuble adossé. 2. Est
          considéré comme étant situé dans le champ de visibilité d'un immeuble classé ou
          inscrit, tout autre immeuble, nu ou bâti, visible du premier ou visible en même
          temps que lui est situé dans un périmètre déterminé par une distance de 500m du
          monument. Ce périmètre de 500m peut être modifié ou adapté : • le périmètre de
          protection adapté (PPA) : lorsqu'un immeuble non protégé fait l'objet d'une
          procédure d'inscription, de classement, ou d'instance de classement,
          l'architecte des bâtiments de France (ABF) peut proposer un périmètre de
          protection adapté en fonction de la nature de l'immeuble et de son
          environnement. • Le périmètre de protection modifié (PPM) : le périmètre
          institué autour d'un monument historique peut être modifié sur proposition de
          l'ABF. Cette ressource décrit les générateurs ponctuels des servitudes de la
          catégorie AC1, à savoir les centroïdes de monuments ou de parties de monument
          classés ou inscrits ou classés et inscrits.

          Source : -NR-
          Millésime : -NR-
          Diffusion : Restreinte</dct:description>
        <dct:identifier>ad2aa2d9-3182-4edd-83f1-51608e2148a6</dct:identifier>
        <dct:issued>2021-06-15T00:00:00Z</dct:issued>
        <dct:modified>2021-06-07T00:00:00Z</dct:modified>
        <dct:language>
          <skos:Concept
            rdf:about="http://publications.europa.eu/resource/authority/language/FRE">
            <skos:prefLabel>fre</skos:prefLabel>
            <rdf:type rdf:resource="http://purl.org/dc/terms/LinguisticSystem" />
          </skos:Concept>
        </dct:language>
        <dcat:contactPoint>
          <vcard:Kind>
            <vcard:title>DDTM 62 (Direction départementale des territoires et de la mer
              du Pas-de-Calais)</vcard:title>
            <vcard:role>pointOfContact</vcard:role>
            <vcard:hasEmail>ddtm-mcsig@pas-de-calais.gouv.fr</vcard:hasEmail>
          </vcard:Kind>
        </dcat:contactPoint>
        <dcat:theme>
          <skos:Concept>
            <skos:prefLabel>données ouvertes</skos:prefLabel>
          </skos:Concept>
        </dcat:theme>
        <dcat:theme>
          <skos:Concept>
            <skos:prefLabel>Aménagement Urbanisme/Assiette Servitude</skos:prefLabel>
          </skos:Concept>
        </dcat:theme>
        <dcat:theme>
          <skos:Concept>
            <skos:prefLabel>PAS-DE-CALAIS</skos:prefLabel>
          </skos:Concept>
        </dcat:theme>
        <dcat:theme>
          <skos:Concept>
            <skos:prefLabel>http://id.insee.fr/geo/departement/62</skos:prefLabel>
          </skos:Concept>
        </dcat:theme>
        <dct:type>
          <skos:Concept>
            <skos:prefLabel>Dataset</skos:prefLabel>
          </skos:Concept>
        </dct:type>
        <dcat:landingPage>
          <foaf:Document
            rdf:about="https://demo.georchestra.org/geonetwork/srv/metadata/fr-120066022-jdd-643b733c-2479-488e-b9d6-5eb502b279aa">
            <dct:title>Table contenant les générateurs ponctuels liés aux servitudes de
              la catégorie AC1 en Pas-de-Calais</dct:title>
          </foaf:Document>
        </dcat:landingPage>
        <dcat:spatialResolutionInMeters>5000</dcat:spatialResolutionInMeters>
        <dct:spatial>
          <dct:Location>
            <locn:geometry>
              {"coordinates":[[[3.187139,50.021069],[1.555964,50.021069],[1.555964,51.006504],[3.187139,51.006504],[3.187139,50.021069]]],"type":"Polygon"}</locn:geometry>
          </dct:Location>
        </dct:spatial>
        <prov:wasUsedBy>
          <prov:Activity>
            <prov:used rdf:resource="local:ad2aa2d9-3182-4edd-83f1-51608e2148a6" />
            <prov:qualifiedAssociation>
              <prov:hadPlan>
                <prov:wasDerivedFrom rdf:parseType="Resource">
                  <dct:title>Règlement (UE) No 1088/2010</dct:title>
                </prov:wasDerivedFrom>
              </prov:hadPlan>
            </prov:qualifiedAssociation>
            <prov:generated>
              <rdf:type
                rdf:about="http://inspire.ec.europa.eu/metadata-codelist/DegreeOfConformity/notEvaluated" />
            </prov:generated>
          </prov:Activity>
        </prov:wasUsedBy>
        <dcat:distribution>
          <dcat:Distribution>
            <dcat:accessURL
              rdf:resource="https://ogc.geo-ide.e2.rie.gouv.fr/wxs?map=/opt/data/carto/geoide-catalogue/1.4/org_38066/ad2aa2d9-3182-4edd-83f1-51608e2148a6.intranet.map" />
            <dct:title>URL de base des services wms/wfs sur intranet</dct:title>
            <adms:representationTechnique>
              <skos:Concept>
                <skos:prefLabel></skos:prefLabel>
              </skos:Concept>
            </adms:representationTechnique>
          </dcat:Distribution>
        </dcat:distribution>
        <dct:provenance>
          <dct:ProvenanceStatement>
            <rdfs:label>COVADIS</rdfs:label>
          </dct:ProvenanceStatement>
        </dct:provenance>
      </dcat:Dataset>
```


Doc geonetwork
- API CSW https://geonetwork-opensource.org/manuals/4.0.x/en/api/csw.html
- Conf spécifique Inspire https://geonetwork-opensource.org/manuals/4.0.x/en/administrator-guide/configuring-the-catalog/inspire-configuration.html#inspire-configuration
	- bien documenté, apparemment plein de choses out of the box pour être compatible INSPIRE. Collocs françaises dans les screenshots.
- Installation OGC API records https://github.com/geonetwork/geonetwork-microservices/blob/main/modules/services/ogc-api-records/README.md