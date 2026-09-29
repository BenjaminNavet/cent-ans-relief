# Cent Ans — relief fin

Cache de relief fin du jeu *Cent Ans* (pyramide de relief E1-E7, fleuves et routes fins), publié
selon l'ADR 0077 du jeu. Les fichiers sont dans les **Releases** : archive `.tar` découpée en parts
et `manifest.json` (version, tailles, SHA-256, crédits).

Installation depuis le dépôt du jeu :

```sh
uv run --project tools cent-ans geo relief-fetch
```

La commande télécharge les parts de la version indiquée dans `data/map/relief_hosting.json`,
vérifie leurs empreintes et installe le cache.

## Crédits et licences des données

Produits dérivés calculés par les outils du jeu à partir des sources suivantes (mentions exigées
reproduites telles quelles ; la liste complète figure aussi dans `manifest.json`).


Le relief et l'hydrographie de la carte de campagne sont des produits dérivés, calculés par les
outils du projet (`tools/cent_ans_tools/geo`, `docs/geo.md`) à partir des sources ci-dessous ; le
cache du relief fin (`data/map/pyramid/`, livré dans l'application ou dans le dossier « Cent Ans
relief », ADR 0036) en fait partie. Les mentions d'attribution exigées par chaque licence sont
reproduites telles quelles (entre guillemets).

- **Relief (terre et bathymétrie)** : ETOPO 2022 15 Arc-Second Global Relief Model, NOAA
  National Centers for Environmental Information — domaine public (données du gouvernement des
  États-Unis). Citation : *NOAA National Centers for Environmental Information. 2022: ETOPO
  2022 15 Arc-Second Global Relief Model. doi:10.25921/fd45-gt74*.
- **Terres, côtes, rivières, lacs** : [Natural Earth](https://www.naturalearthdata.com/)
  (10 m physical) — domaine public. « Made with Natural Earth. »
- **Relief fin (terres de l'emprise jouable)** : Copernicus DEM GLO-90, © DLR e.V. 2010-2014 et
  © Airbus Defence and Space GmbH 2014-2018, fourni dans le cadre de COPERNICUS par l'Union
  européenne et l'ESA — tous droits réservés ; licence gratuite avec attribution. Tuiles lues
  sur le bucket public AWS Open Data `copernicus-dem-90m` (lot R1, ADR 0019). Mention : « © DLR
  e.V. 2010-2014 and © Airbus Defence and Space GmbH 2014-2018 provided under COPERNICUS by the
  European Union and ESA; all rights reserved. » Sert aussi aux étages E1-E2 de la pyramide de
  relief (palier 1, lot ZG1) et aux horizons des batailles (`game/assets/horizon/relief/`, EP2).
- **Relief rapproché (pyramide de relief, palier 2)** : Copernicus DEM GLO-30 Public, © DLR e.V.
  2010-2014 et © Airbus Defence and Space GmbH 2014-2018, fourni dans le cadre de COPERNICUS par
  l'Union européenne et l'ESA — tous droits réservés ; licence gratuite avec attribution
  (conditions : https://dataspace.copernicus.eu/explore-data/data-collections/copernicus-contributing-missions/collections-description/COP-DEM).
  « Copernicus Digital Elevation Model (DEM) was accessed on 2026-09-25 from
  https://registry.opendata.aws/copernicus-dem. » Les organismes en charge du programme
  Copernicus n'encourent aucune responsabilité pour l'usage qui en est fait. Modifié : canopée,
  bâti moderne et retenues de barrages retirés (lot ZG1, ADR 0036). Les tuiles E1-E2 de la
  pyramide dérivent de GLO-90 (même licence).
- **Occupation du sol actuelle (correction du relief)** : ESA WorldCover 10 m 2021 v200,
  © ESA WorldCover project 2021 / Contains modified Copernicus Sentinel data (2021) processed by
  ESA WorldCover consortium — licence CC BY 4.0. Citation : *Zanaga, D. et al. (2022). ESA
  WorldCover 10 m 2021 v200. doi:10.5281/zenodo.7254221* ; accédé le 2026-09-25 depuis
  https://registry.opendata.aws/esa-worldcover-vito. Sert uniquement à retirer arbres, bâti et
  plans d'eau modernes du relief GLO-30 (lot ZG1).
- **Défrichement vers 1340** : KK10 Anthropogenic Land Cover Change — Kaplan, J. O. et
  Krumhardt, K. M. (2017), PANGAEA, doi:10.1594/PANGAEA.871369, licence CC BY 3.0 ; méthode :
  Kaplan et al. (2011), *The Holocene* 21(5), doi:10.1177/0959683610386983. Moyenne 1330-1349,
  combinée aux grandes forêts et zones humides nommées de `data/map/historical_forests.json` et
  `data/map/wetlands.json` (sources par entrée).
- **Relief détaillé des zones historiques (palier 3, lot ZG3, ADR 0036)** — modèles numériques
  de terrain sans sursol, rééchantillonnés à 11, 5,6 et 2,8 m (34 zones de
  `data/map/detail_zones.json`, étages E5-E7) :
  - France : RGE ALTI® 1 m / 5 m, © IGN (Institut national de l'information géographique et
    forestière), [Licence Ouverte Etalab 2.0](https://www.etalab.gouv.fr/licence-ouverte-open-licence/) ;
    service WMS-R de la Géoplateforme (`data.geopf.fr`). Mention : « Source : IGN – RGE ALTI® ».
  - Angleterre : LIDAR Composite Digital Terrain Model (DTM) 1 m, Environment Agency,
    [Open Government Licence v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/).
    Mention : « © Environment Agency copyright and/or database right 2022. All rights reserved. »
  - Pays-Bas : Actueel Hoogtebestand Nederland (AHN) DTM 0,5 m, Rijkswaterstaat / Het Waterschapshuis,
    service PDOK, [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/) (aucune attribution
    exigée ; citée par courtoisie).
  - Flandre : Digitaal Hoogtemodel Vlaanderen II (DTM 1 m) et I (DTM 5 m), © Digitaal Vlaanderen,
    [Modellicentie Gratis Hergebruik v1.0](https://data.vlaanderen.be/doc/licentie/modellicentie-gratis-hergebruik/v1.0)
    (réutilisation gratuite, y compris commerciale, avec mention de la source).
  - Repli (Tournai, Wallonie : pas de service à valeurs brutes) : Copernicus DEM GLO-30, © DLR e.V.
    2010-2014 et © Airbus Defence and Space GmbH 2014-2018, fourni dans le cadre de COPERNICUS par
    l'Union européenne et l'ESA ; licence gratuite avec attribution.
  - Effacement des aménagements modernes (autoroutes, voies ferrées, carrières, retenues, digues de
    port) : masques calculés à partir d'OpenStreetMap, © les contributeurs d'OpenStreetMap,
    [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/) — méthode seulement : aucune donnée
    OSM n'est redistribuée (masques intermédiaires hors dépôt).
- **Routes** (`data/map/roads.geojson`) : Itiner-e, *A High-Resolution Dataset of Roads of the
  Roman Empire* (de Soto, Pažout, Brughmans et al.), Zenodo doi:10.5281/zenodo.17122148, licence
  CC BY 4.0 ; citation : *de Soto P., Pažout A., Brughmans T. et al. (2025). Itiner-e: A
  high-resolution dataset of roads of the Roman Empire. Scientific Data.
  doi:10.1038/s41597-025-06140-z*. Complété par des tronçons calculés par le projet.
- **Hameaux** (`data/map/hamlets.json`) : [GeoNames](https://www.geonames.org/) `cities500`,
  © GeoNames, licence CC BY 4.0.
- **Villes emblématiques** (`data/landmarks/`) : quelques dizaines de points de contrôle de position
  par ville relevés à la main sur © les contributeurs
  d'[OpenStreetMap](https://www.openstreetmap.org/copyright) (ODbL 1.0), arrondis. Les plans
  anciens de Wikimedia Commons cités dans ces fichiers ont servi de référence et ne sont pas
  redistribués.
- **Villes emblématiques à l'échelle 1:1** (`data/landmarks_v2/`, ADR 0078) : tracés des rues
  actuelles héritées du plan médiéval, positions et orientations des églises, tracé des
  boulevards bâtis sur les enceintes arasées, extraits d'OpenStreetMap (Overpass) par
  `cent-ans geo landmarks` : © les contributeurs
  d'[OpenStreetMap](https://www.openstreetmap.org/copyright), base de données sous licence
  ODbL 1.0. Les plans anciens (Le Lieur, Braun et Hogenberg, plans Gallica, carte d'Agas) ne
  servent qu'au contrôle humain et ne sont ni extraits ni redistribués.
- **Paris vers 1340 à l'échelle 1:1** (`data/landmarks_v2/paris.json`, lot VH5) : réseau des
  rues, enceintes, portes, emprises des monuments, îlots, îles et lit de la Seine d'après « Paris
  en 1380 » ; gabarit des parcelles d'après les données Vasserot version 1. © ALPAGE :
  P. Rouet (Paris en 1380), A.-L. Bethe (données Vasserot) ; Arch. nat. F31 73-96 – Arch. Paris
  © ALPAGE. Base de données sous licence
  [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/), https://alpage.huma-num.fr/gis-data/
  (consortium ALPAGE : LAMOP-Paris 1, LIENSs, ArScAn, L3i ; dir. H. Noizet). Les données
  dérivées (`paris.json`) restent sous ODbL.
- **Réseau hydrographique fin (lot ZG5a, ADR 0036)** — tracés recalés sur la pyramide de relief,
  canaux postérieurs à 1340 retirés :
  - France : BD TOPAGE® 2025, tronçons hydrographiques (IGN, OFB, agences de l'eau ; diffusion
    SANDRE, `services.sandre.eaufrance.fr`),
    [Licence Ouverte Etalab 2.0](https://www.etalab.gouv.fr/licence-ouverte-open-licence/).
    Mention : « Source : BD TOPAGE® – IGN, OFB ».
  - Grande-Bretagne : OS Open Rivers, Ordnance Survey,
    [Open Government Licence v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/).
    Mention : « Contains OS data © Crown copyright and database right 2026. »
  - Bénélux, Rhénanie, versants suisse, italien et espagnol du cœur : EU-Hydro River Network
    Database v1.3, Copernicus Land Monitoring Service, Agence européenne pour l'environnement,
    lue sur le service ArcGIS public `image.discomap.eea.europa.eu` ; accès libre, complet et
    gratuit selon la politique de données Copernicus (règlement délégué (UE) n° 1159/2013).
    Mention : « © European Union, Copernicus Land Monitoring Service 2020, European Environment
    Agency (EEA). »
  - Hors cœur : Natural Earth (voir ci-dessus).
- Traitement (reprojection EPSG:3035, découpage des provinces) : outils `tools/cent_ans_tools/geo`
  (voir `docs/geo.md`).

