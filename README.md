# Lab — Application Android (Formulaire et Récapitulatif)

## Objectif

Réaliser une application Android simple composée de :

* Un écran de saisie (Screen 1)
* Un écran de récapitulatif (Screen 2)
* Transmission des données via Intent
* Un bouton de retour

---

## Étape 1 — Interface principale (activity_main.xml)

Un formulaire a été créé contenant les champs suivants :

* Nom & Prénom
* Email
* Téléphone
* Adresse
* Ville
* Bouton Envoyer

Chaque champ utilise un identifiant personnalisé afin d’éviter les noms génériques.

Exemples d’identifiants :

* `inputIdentite`
* `inputCourriel`
* `inputMobile`
* `inputLocalisation`
* `inputVille`
* `actionEnvoyer`
![](/activityMain.png)
---

## Étape 2 — Écran de récapitulatif (activity_screen2.xml)

Le second écran contient :

* Un titre
* Une zone d’affichage des données
* Un bouton Retour

Identifiants utilisés :

* `lblHeader`
* `txtResume`
* `btnBackHome`

---

## Étape 3 — Implémentation de MainActivity

Dans `MainActivity.java` :

### Liaison des vues

Les composants XML sont reliés aux variables Java avec `findViewById()`.

### Lecture des données

Lors du clic sur le bouton Envoyer :

* Lecture des champs avec `getText().toString().trim()`
* Vérification simple : Nom et Email obligatoires

### Navigation vers Screen2

Un Intent explicite est créé :

```java
Intent goRecap = new Intent(MainActivity.this, Screen2Activity.class);
```

Les données sont transmises via des clés personnalisées :

* `x_identite`
* `x_courriel`
* `x_mobile`
* `x_adresse`
* `x_ville`

---

## Étape 4 — Implémentation de Screen2Activity

Dans `Screen2Activity.java` :

### Récupération des données

Les valeurs sont récupérées avec :

```java
getIntent().getStringExtra(...)
```

### Construction du résumé

Un texte multi-ligne est généré pour afficher les informations saisies.

### Bouton Retour

Le bouton exécute :

```java
finish();
```

ce qui ferme l’écran courant et revient au précédent.

---

## Étape 5 — Configuration du AndroidManifest

Les deux activités sont déclarées :

* `MainActivity` (activité de lancement)
* `Screen2Activity`

L’attribut `android:exported` est configuré correctement pour Android récent.

---

## Résultat

L’application permet :

* la saisie des informations utilisateur
* la transmission vers un second écran
* l’affichage du récapitulatif
* le retour vers le formulaire

Des identifiants personnalisés ont été utilisés afin d’éviter les conventions standards du template.
