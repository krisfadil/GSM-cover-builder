# GSM Cover Builder

## Description
**GSM Cover Builder** est un plugin QGIS conçu pour optimiser la planification du déploiement du réseau GSM.
Il permet d'automatiser l'analyse de couverture en regroupant des localités selon un rayon défini par l'utilisateur et en générant des buffers optimisés.
Il facilite ainsi la prise de décision pour le déploiement des infrastructures de télécommunication.

## Fonctionnalités
- Sélection d'une couche de localités en entrée.
- Définition d'un champ identifiant les localités.
- Choix d'un rayon de couverture pour le regroupement des localités.
- Option de raffinement des buffers avec des polygones de Voronoï.

## Installation
1. Téléchargez le plugin depuis le dépôt officiel.
2. Ouvrez QGIS et allez dans le gestionnaire d'extensions.
3. Installez et activez GSM Cover Builder.

## Utilisation
1. Ouvrir QGIS et charger une couche vectorielle contenant les localités.
2. Lancer **GSM Cover Builder** depuis le menu des plugins.
3. Sélectionner la couche et le champ identifiant les localités.
4. Définir le rayon de couverture souhaité.
5. Activer ou non l'option de raffinement par Voronoï.
6. Exécuter le traitement et visualiser les résultats sur la carte.

## Dépendances
- QGIS 3.x
- PyQt5
- Processing

## Auteur
Fadil Kristof GNANKAMBARY

## Licence
Ce plugin est distribué sous licence MIT. Voir le fichier `LICENSE` pour plus de détails.

## Contact
Pour toute assistance ou demande de renseignements, veuillez contacter Fadil Kristof GNANKAMBARY, krisfadil@live.fr.


||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||


# GSM Cover Builder - QGIS Plugin

## Overview
GSM Cover Builder is a QGIS plugin designed to optimize GSM network deployment by calculating optimal coverage plans.
The tool allows users to group localities based on a predefined coverage radius, helping to minimize the number of sites required to cover a given area efficiently.

## Features
- Selection of input vector layer containing localities
- Choice of the field containing locality names or unique identifiers
- Customizable coverage radius for site planning
- Option to refine coverage areas using Voronoi polygons
- Output layer with grouped localities and coverage zones

## Installation
1. Download the plugin from the official repository.
2. Open QGIS and go to the Plugin Manager.
3. Install and activate GSM Cover Builder.

## Usage
1. Open QGIS and load the vector layer containing locality points.
2. Launch the plugin from the `GSM Cover Builder` menu.
3. Select the input layer and the field containing locality names.
4. Define the coverage radius.
5. (Optional) Enable Voronoi polygons for refined coverage.
6. Click `Run` to generate the coverage plan.

## Dependencies
Ensure that the following Python libraries are installed in your QGIS environment:
- `PyQt5`
- `QGIS Core`
- `Processing`

## Contributing
Contributions, bug reports, and feature requests are welcome! Feel free to submit issues or pull requests via the project repository.

## Creator
Fadil Kristof GNANKAMBARY

## License
This plugin is distributed under the MIT License.

## Contact
For support or inquiries, please contact Fadil Kristof GNANKAMBARY, krisfadil@live.fr.



