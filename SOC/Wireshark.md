
| **Outil Wireshark**           | **Description**                                      | **Utilité**                                    | **Avantages**                                         | **Inconvénients**                                      | **Comparaison avec d'autres outils**                |
|-------------------------------|------------------------------------------------------|------------------------------------------------|------------------------------------------------------|-------------------------------------------------------|-----------------------------------------------------|
| **Capture Filter**            | Filtre appliqué avant la capture de paquets          | Limiter les paquets capturés                    | Réduit la quantité de données à analyser             | Doit être configuré avant la capture                  | Tcpdump et Tshark offrent des filtres de capture similaires en CLI |
| **Display Filter**            | Filtre appliqué après la capture de paquets          | Afficher uniquement les paquets d'intérêt       | Simplifie l'analyse en se concentrant sur les paquets pertinents | Peut être complexe à maîtriser pour des filtres avancés | Bro/Zeek offre des capacités de filtrage avancées mais sans interface graphique |
| **Follow TCP/UDP Stream**     | Regroupe et affiche les paquets d'une session        | Analyse de sessions TCP/UDP complètes           | Facilite la compréhension des flux de communication   | Peut être lourd pour les sessions très longues        | Tcpdump permet de suivre les flux mais de manière moins intuitive |
| **Protocol Hierarchy**        | Affiche la hiérarchie des protocoles capturés        | Vue d'ensemble des protocoles utilisés          | Visualisation claire des protocoles et de leur utilisation | Moins de détails sur chaque paquet                   | Aucun outil CLI ne fournit une visualisation aussi claire et directe |
| **Statistics (I/O Graphs)**   | Graphiques d'entrée/sortie pour analyser le trafic   | Visualisation des tendances de trafic           | Aide à identifier les pics et les anomalies de trafic | Peut nécessiter des réglages pour des analyses précises | ELK stack offre des visualisations avancées mais nécessite une configuration plus complexe |
| **Expert Information**        | Résumé des anomalies et erreurs détectées            | Identification rapide des problèmes potentiels  | Facilite le diagnostic des problèmes réseau           | Peut générer trop d'informations pour de grandes captures | Suricata et Bro/Zeek offrent des informations expertes similaires mais sans interface graphique |
| **Packet Details**            | Affiche les détails de chaque paquet capturé         | Analyse détaillée des en-têtes et des données   | Informations complètes et exhaustives                 | Peut être écrasant pour les nouveaux utilisateurs     | Tcpdump et Tshark fournissent des détails similaires en CLI mais sans interface graphique |
| **Coloring Rules**            | Applique des couleurs aux paquets selon des critères | Visualisation rapide des types de paquets       | Aide à identifier visuellement les paquets importants | Peut nécessiter des configurations spécifiques        | Aucun outil CLI ne fournit une telle visualisation rapide et intuitive |
| **Packet Reassembly**         | Reconstitue les données fragmentées                  | Analyse des fichiers transférés sur plusieurs paquets | Utile pour les protocoles qui fragmentent les données | Peut être complexe pour des protocoles peu documentés | Bro/Zeek et Suricata offrent des capacités de réassemblage mais sans interface graphique |

### Ajustements et Comparaison avec d'autres outils pour un SOC Analyste Niveau 1

1. **Capture Filter** et **Display Filter** : Éléments clés pour un analyste SOC de niveau 1, permettant de réduire la quantité de données à analyser et de se concentrer sur les paquets pertinents. La maîtrise de ces filtres peut grandement améliorer l'efficacité de l'analyse. Des outils comme Tcpdump et Tshark offrent des capacités similaires mais nécessitent des compétences en ligne de commande.

2. **Follow TCP/UDP Stream** : Crucial pour comprendre les flux de communication et reconstituer les sessions complètes, aidant à identifier les comportements anormaux ou malveillants. Tcpdump permet de suivre les flux, mais de manière moins intuitive.

3. **Protocol Hierarchy** et **Statistics (I/O Graphs)** : Aident à obtenir une vue d'ensemble des protocoles utilisés et à visualiser les tendances de trafic, facilitant l'identification des anomalies. Les outils comme l'ELK stack offrent des visualisations avancées mais nécessitent une configuration plus complexe.

4. **Expert Information** : Fournit un résumé des anomalies et erreurs détectées, facilitant la détection rapide des problèmes potentiels. Comparable à Suricata et Bro/Zeek, mais avec une interface graphique plus accessible.

5. **Packet Details** et **Packet Bytes** : Permettent une analyse détaillée des paquets, essentielle pour un diagnostic approfondi. Tcpdump et Tshark fournissent des détails similaires, mais sans interface graphique.

6. **Coloring Rules** : Aide à identifier visuellement les paquets importants, rendant l'analyse plus rapide et intuitive. Aucun outil CLI ne fournit une telle visualisation rapide et intuitive.

7. **Packet Reassembly** : Utile pour analyser les protocoles qui fragmentent les données. Bro/Zeek et Suricata offrent des capacités de réassemblage mais sans interface graphique, ce qui peut être moins accessible pour un analyste de niveau 1.

### Comparaison globale pour un SOC Analyste Niveau 1

- **Wireshark** : Offre une interface graphique intuitive et des outils puissants pour l'analyse détaillée des paquets. Idéal pour les analystes débutants et intermédiaires.
- **Tcpdump/Tshark** : Outils en ligne de commande puissants et légers, mais nécessitant des compétences avancées en CLI. Moins conviviaux pour une analyse visuelle.
- **Bro/Zeek** : Offre des capacités de détection d'intrusions et d'analyse avancées sans interface graphique, ce qui peut être un obstacle pour les analystes moins expérimentés.
- **Suricata** : Similaire à Snort avec une meilleure performance multi-threading, mais également sans interface graphique, rendant l'analyse moins intuitive pour les débutants.
- **ELK Stack** : Excellente pour la gestion et la visualisation des logs, mais nécessite une infrastructure plus importante et une configuration plus complexe, ce qui peut être une barrière pour les analystes de niveau 1.

Ce tableau devrait fournir une vue d'ensemble complète et ajustée des outils les plus utilisés dans l'interface de Wireshark pour un SOC Analyste de niveau 1, en mettant l'accent sur leur utilité, avantages et inconvénients par rapport à d'autres outils d'analyse de trafic réseau.
