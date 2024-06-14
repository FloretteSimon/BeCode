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




# Link:
https://www.youtube.com/watch?v=5aYpkLfkgRE
https://www.youtube.com/playlist?list=PLV1TsfPiCx8PXHsHeJKvSSC8zfi4Kvcfs



# Steps:

pip3 install flask


pip3 install requests: "requests" is a popular Python library for making HTTP requests. It simplifies interaction with web services by providing a user-friendly interface for sending HTTP requests (GET, POST, PUT, DELETE, etc.) and managing responses.

## code flask py

from flask import Flask, render_template, request, redirect, url_for, flash -> from flask import Flask, render_template, request, redirect, url_for, flash : Importe les classes et fonctions nécessaires depuis le module Flask.
Flask : Classe principale de l'application Flask.
render_template : Fonction pour rendre des fichiers de template HTML.
request : Objet qui contient les données de la requête HTTP (GET ou POST).
redirect : Fonction pour rediriger l'utilisateur vers une autre URL.
url_for : Fonction pour générer des URLs.
flash : Fonction pour afficher des messages temporaires à l'utilisateur.

import re: import re -> Importe le module re pour utiliser les expressions régulières en Python.


app = Flask(__name__)-> Crée une instance de l'application Flask. __name__ est un argument qui indique le nom du module.
app.secret_key = 'supersecretkey'-> Définit une clé secrète pour l'application. Cette clé est nécessaire pour utiliser des fonctionnalités comme flash et la gestion de sessions.

def sanitize_input(input_string): -> Déclare une fonction qui nettoie les entrées utilisateur en supprimant tout code HTML.
    return re.sub(r'<.*?>', '', input_string) -> Utilise une expression régulière pour remplacer tout ce qui ressemble à un tag HTML par une chaîne vide.

def email_valid(email): -> Déclare une fonction qui valide le format d'un email.
    regex = r'^\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b' -> Expression régulière pour correspondre au format d'un email valide.
    return re.match(regex, email) -> Retourne un objet match si l'email correspond au regex, sinon retourne None.

@app.route('/', methods=['GET', 'POST']) -> Déclare une route pour l'URL racine de l'application. Accepte les méthodes GET et POST.
def formulaire(): -> Définit la fonction de vue qui gère les requêtes à cette URL.
    if request.method == 'POST': -> Vérifie si la requête est de type POST (si l'utilisateur a soumis le formulaire).
        nom = sanitize_input(request.form.get('nom', '').strip())
        prenom = sanitize_input(request.form.get('prenom', '').strip())
        email = sanitize_input(request.form.get('email', '').strip())
        pays = sanitize_input(request.form.get('pays', '').strip())
        message = sanitize_input(request.form.get('message', '').strip())
        genre = request.form.get('choix_genre')
        sujet = request.form.get('choix')
        honeypot = sanitize_input(request.form.get('honeypot', ''))
        
-> Récupère les données du formulaire avec request.form.get et les nettoie avec sanitize_input. strip() supprime les espaces en trop.
nom, prenom, email, pays, message : Champs texte du formulaire.
genre : Champ radio pour le genre.
sujet : Champ sélection pour le sujet.
honeypot : Champ caché pour la protection anti-spam.

        errors = {} -> initialise un dictionnaire pour stocker les messages d'erreur.

        if honeypot:
            flash("SPAM DETECTED", "ERROR")
            return render_template("Formulaire.html", data=request.form)
        -> Si le champ caché honeypot contient une valeur (indiquant un bot), un message de spam est flashé et le formulaire est réaffiché.


        if not nom:
            errors['nom'] = "Nom obligatoire!"

        if not prenom:
            errors['prenom'] = "Prénom obligatoire!"

        if not email or not email_valid(email):
            errors['email'] = "Email obligatoire et doit être valide!"

        if not pays:
            errors['pays'] = "Pays obligatoire!"

        if not message:
            errors['message'] = "Message obligatoire!"

        if not genre:
            errors['genre'] = "Genre obligatoire!"

        -> Vérifie que tous les champs obligatoires sont remplis et ajoute les messages d'erreur appropriés au dictionnaire errors.


        if errors:
            return render_template("Formulaire.html", data=request.form, errors=errors)

        -> Si des erreurs sont trouvées, le formulaire est réaffiché avec les valeurs précédentes et les messages d'erreur.

        return render_template("Merci.html", nom=nom, prenom=prenom, email=email, pays=pays, message=message, genre=genre, sujet=sujet)

        -> Si le formulaire est correctement rempli, la page de remerciement Merci.html est rendue avec les données du formulaire.


    return render_template("Formulaire.html")

    -> Si la requête est de type GET, affiche le formulaire vide.

if __name__ == '__main__': -> Vérifie si le script est exécuté directement (et non importé comme module).
    app.run(debug=True) -> Lance l'application Flask en mode debug, ce qui permet d'avoir des messages d'erreur détaillés.



## template Formulaire.html


<!DOCTYPE html>
<html lang="fr"> ->  Déclare que le langage du document est le français.
<head>
    <meta charset="UTF-8"> -> Définit le jeu de caractères du document à UTF-8, permettant l'utilisation de la plupart des caractères et symboles.
    <meta name="viewport" content="width=device-width, initial-scale=1.0"> -> Configure la mise en page responsive en définissant la largeur de la fenêtre à la largeur de l'appareil et le niveau de zoom initial à 1.0.
    <title>Contact Us - Hackers Poulette™</title>
</head>
<body>
    <h1>Formulaire de contact</h1>
    <form action="" method="POST"> ->  Déclare un formulaire HTML qui enverra les données en utilisant la méthode POST à la même URL.
        <!-- Nom -->
        <p>
            <label for="nom">Nom: </label>
            <input type="text" name="nom" id="nom" value="{{ request.form.get('nom', '') }}" required> ->Champ de saisie de type texte pour le nom, pré-rempli avec la valeur envoyée précédemment (si présente).
            {% if errors and errors.get("nom") %}
                <span>{{ errors.get("nom") }}</span>
            {% endif %}
            ->Affiche un message d'erreur si présent.
        </p>
        <!-- Prénom -->
        <p>
            <label for="prenom">Prénom: </label>
            <input type="text" name="prenom" id="prenom" value="{{ request.form.get('prenom', '') }}" required>
            {% if errors and errors.get("prenom") %}
                <span>{{ errors.get("prenom") }}</span>
            {% endif %}
        </p>
        <!-- Email -->
        <p>
            <label for="email">Email: </label>
            <input type="email" name="email" id="email" value="{{ request.form.get('email', '') }}" required>
            {% if errors and errors.get("email") %}
                <span>{{ errors.get("email") }}</span>
            {% endif %}
        </p>
        <!-- Pays -->
        <p>
            <label for="pays">Pays: </label>
            <input type="text" id="pays" name="pays" value="{{ request.form.get('pays', '') }}" required>
            {% if errors and errors.get("pays") %}
                <span>{{ errors.get("pays") }}</span>
            {% endif %}
        </p>
        <!-- Message -->
        <p>
            <label for="message">Écrire un message: </label>
            <textarea name="message" id="message" rows="6" cols="50" required>{{ request.form.get('message', '') }}</textarea>
            {% if errors and errors.get("message") %}
                <span>{{ errors.get("message") }}</span>
            {% endif %}
        </p>
        <!-- Genre -->
        <p>
            Genre:
            <input type="radio" name="choix_genre" value="H" id="homme" {% if request.form.get('choix_genre') == 'H' %}checked{% endif %} required>
            <label for="homme">Homme</label>
            <input type="radio" name="choix_genre" value="F" id="femme" {% if request.form.get('choix_genre') == 'F' %}checked{% endif %} required>
            <label for="femme">Femme</label>
            {% if errors and errors.get("genre") %}
                <span>{{ errors.get("genre") }}</span>
            {% endif %}
        </p>
        <!-- Sujet -->
        <p>
            <label for="sujet">Sujet: </label>
            <select name="choix" id="sujet">
                <option value="réparation" {% if request.form.get('choix') == 'réparation' %}selected{% endif %}>Réparation</option>
                <option value="commande" {% if request.form.get('choix') == 'commande' %}selected{% endif %}>Commande</option>
                <option value="autre" {% if request.form.get('choix') == 'autre' %}selected{% endif %}>Autre</option>
            </select>
        </p>
        <!-- Honeypot -->
        <p>
            <label for="honeypot" style="display:none;">Honeypot:</label>
            <input type="text" id="honeypot" name="honeypot" style="display: none;">
        </p>
        <!-- Bouton d'envoi -->
        <p>
            <input type="submit" value="Envoyer le formulaire">
        </p>
    </form>
</body>
</html>


## template Merci.html

<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Merci - Hackers Poulette™</title>
</head>
<body>
    <h1>Merci de nous avoir contacté</h1>
    <p>Voici les informations que vous avez fournies:</p>
    <ul>
        <li><strong>Nom:</strong> {{ nom }}</li>
        <li><strong>Prénom:</strong> {{ prenom }}</li>
        <li><strong>Email:</strong> {{ email }}</li>
        <li><strong>Pays:</strong> {{ pays }}</li>
        <li><strong>Message:</strong> {{ message }}</li>
        <li><strong>Genre:</strong> {{ genre }}</li>
        <li><strong>Sujet:</strong> {{ sujet }}</li>
    </ul>
</body>
</html>


# Photos:

<img width="676" alt="Capture d’écran 2024-06-14 à 14 02 48" src="https://github.com/FloretteSimon/BeCode/assets/155719677/ccc7f9f5-ce45-4f2c-a9e9-23c0f73d731a">


<img width="664" alt="Capture d’écran 2024-06-14 à 14 03 26" src="https://github.com/FloretteSimon/BeCode/assets/155719677/d2154cac-2ae8-452d-872f-1dde97f18e62">


<img width="688" alt="Capture d’écran 2024-06-14 à 14 03 47" src="https://github.com/FloretteSimon/BeCode/assets/155719677/1e8e7113-e5ed-461f-bfb4-b62bfa687e6d">


<img width="669" alt="Capture d’écran 2024-06-14 à 14 04 13" src="https://github.com/FloretteSimon/BeCode/assets/155719677/d20211fb-6617-4aab-9694-894418fb0fd8">


<img width="603" alt="Capture d’écran 2024-06-14 à 14 04 27" src="https://github.com/FloretteSimon/BeCode/assets/155719677/e4c5d3a2-0029-4f9f-82a5-c5f37135c1d2">


