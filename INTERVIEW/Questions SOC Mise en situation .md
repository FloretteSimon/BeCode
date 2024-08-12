## 1. Imagine que tu reçois une alerte concernant une connexion suspecte depuis un pays étranger. Comment enquêterais-tu sur cette alerte ?Pour enquêter sur une alerte concernant une connexion suspecte depuis un pays étranger, je suivrais ces étapes :

1. **Vérification de l’alerte** :
   - **Confirmer l'alerte** : Vérifier les détails de la connexion, comme l'adresse IP, le protocole utilisé, et le moment de la connexion.
   - **Analyser le contexte** : Examiner si la connexion correspond à des activités normales ou à des exceptions prévues (par exemple, des employés en déplacement).

2. **Analyse des logs** :
   - **Examiner les logs** : Analyser les logs de pare-feu, de serveurs et de systèmes pour comprendre la nature de la connexion (tentatives de connexion, heures d'accès, ressources accédées).
   - **Vérifier les patterns** : Rechercher des comportements inhabituels ou des patterns de trafic associés à la connexion suspecte.

3. **Identification de la source** :
   - **Géolocaliser l'IP** : Utiliser des outils de géolocalisation pour confirmer le pays d'origine de l'adresse IP.
   - **Rechercher des informations** : Vérifier si l'adresse IP appartient à une plage d'adresses utilisée par des services cloud ou par des adresses IP dynamiques.

4. **Évaluation du risque** :
   - **Analyser les permissions** : Déterminer si l'utilisateur ou le système accédant est autorisé à accéder aux ressources ciblées.
   - **Examiner les données accédées** : Évaluer si des données sensibles ou critiques ont été consultées ou modifiées.

5. **Actions correctives** :
   - **Contenir l'incident** : Si nécessaire, bloquer l'adresse IP suspecte ou restreindre les accès pour prévenir d'autres connexions.
   - **Notifier les parties prenantes** : Informer les responsables de la sécurité et les équipes pertinentes de la situation.

6. **Documentation et amélioration** :
   - **Documenter l'incident** : Créer un rapport détaillé sur l'incident, y compris les actions prises et les découvertes.
   - **Réviser les politiques** : Mettre à jour les politiques de sécurité et les configurations pour mieux détecter et prévenir les connexions suspectes à l'avenir.


## 2. Un utilisateur signale que son ordinateur est devenu extrêmement lent. Comment enquêterais-tu sur cette situation ?

Pour enquêter sur un ordinateur devenu extrêmement lent, je suivrais ces étapes :

1. **Collecte d'informations** :
   - **Description du problème** : Demander à l'utilisateur des détails spécifiques sur les symptômes (quand la lenteur a commencé, les applications affectées, etc.).
   - **Historique des modifications** : Vérifier si des changements récents ont été effectués sur l'ordinateur, comme des installations ou des mises à jour de logiciels.

2. **Analyse des ressources système** :
   - **Utilisation des ressources** : Examiner l'utilisation du processeur, de la mémoire, et du disque à l'aide de gestionnaires de tâches ou d'outils similaires pour identifier des goulets d'étranglement.
   - **Processus en cours** : Identifier les processus ou applications consommant des ressources de manière excessive.

3. **Examen des performances** :
   - **Analyse des processus** : Utiliser des outils d'analyse de performance pour examiner les processus en cours et détecter d'éventuelles anomalies.
   - **Vérification des disques** : Contrôler l'état du disque dur ou SSD pour détecter des problèmes de performance ou de fragmentation.

4. **Analyse de la sécurité** :
   - **Scan antivirus** : Effectuer un scan complet avec un logiciel antivirus pour détecter la présence de logiciels malveillants qui pourraient ralentir le système.
   - **Vérification des menaces** : Rechercher des signes d’infection ou de logiciels indésirables.

5. **Analyse des logs** :
   - **Examiner les journaux** : Vérifier les logs système et applicatifs pour des erreurs ou des avertissements pouvant indiquer des problèmes sous-jacents.

6. **Nettoyage et maintenance** :
   - **Optimisation du système** : Exécuter des outils de nettoyage pour supprimer les fichiers temporaires, les caches, et optimiser les performances du système.
   - **Désinstallation** : Envisager la désinstallation des applications inutilisées ou des logiciels qui pourraient causer des conflits.

7. **Tests matériels** :
   - **Vérification des composants** : Si nécessaire, tester les composants matériels (comme la RAM et le disque dur) pour détecter des défaillances potentielles.

8. **Rapport et recommandations** :
   - **Documentation** : Consigner les résultats de l’enquête, les actions entreprises, et les recommandations pour résoudre le problème.
   - **Suivi** : Si le problème persiste après les interventions, recommander des actions supplémentaires comme une réinstallation du système d'exploitation ou des tests plus approfondis.

En procédant ainsi, on peut identifier la cause de la lenteur et appliquer les mesures nécessaires pour restaurer les performances optimales de l'ordinateur.
