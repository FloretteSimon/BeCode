Projet: Formulaire en Python avec Flask
Durée : 5 jours

1 Jour pour vous informer sur Flask : https://openclassrooms.com/fr/courses/4425066-concevez-un-site-avec-flask
4 Jours pour effectuer le projet.
Compétences travaillées
Backend: PYTHON programming (initiation aux structures logiques)
Sanitzation et validation d'un formulaire
Implémentation des méthodes POST et GET
Implémentation de template avec Jinja
Situation-problème
La société Hackers Poulette ™ vend des kits et accessoires pour Rasperri Pi à monter soi-même. Elle souhaite permettre à ses utilisateurs de contacter son support technique. Ta mission: développer un script en python, permettant d'afficher un formulaire de contact et de traiter sa réponse: sanitisation, validation, puis envoi et feedback à l'utilisateur.

Critères de performance
Si l'utilisateur commet une erreur, lui retourner le formulaire, avec les réponses valides remises dans leurs inputs respectifs.
Idéalement: afficher les messages d'erreurs à proximité de leur champ respectif.
Le formulaire effectuera un nettoyage (sanitization) et une validation serverside
Si la sanitization et la validation sont ok, une page "Merci de nous avoir contacté." s'affichera avec un résumé de l'ensemble des informations encodées.
Implémentation de la technique antispam du honeypot
Champs du formulaire: prénom & nom + email + pays (liste) + message + genre (H/F) (Radio box) + 3 sujets possibles ((Réparation, Commande, Autres) doit être des checkbox). Tous les champs sont obligatoires, sauf le sujet (dans ce cas, valeur = "Autre")

Formulaire de contact (Python)
présentation: architecture serveur/client (transmissif, 10")
sanitization: neutraliser tout encodage nocif (<script>)
validation: champs obligatoires + Email valide
Envoi + Feedback
PAS BESOIN DE JAVASCRIPT, NI DE CSS
À la fin de ce projet vous devez être capable :
D'expliquer la différence entre une requête POST et une requête GET
De vous protéger contre les failles XSS
De vous protéger contre une attaque SSTI
Utilser un micro famework
Faire un déployement
