 ALGORITHME Gestion Cinema
VARIABLES
salle : tableau à deux dimensions
choix : entier
FONCTION initialiser_salle()
VARIABLES
    salle : tableau à deux dimensions
    i, j : entier

DÉBUT

    POUR i DE 0 À 4 FAIRE
        POUR j DE 0 À 7 FAIRE
            salle[i][j] ← 0
        FIN POUR
    FIN POUR

    RETOURNER salle

FIN
​
FONCTION afficher_salle(salle)
VARIABLES
    i, j : entier

DÉBUT

    AFFICHER "1,2,3,4,5,6,7,8"

    POUR i DE 0 À 4 FAIRE

        AFFICHER "Rang ", i + 1

        POUR j DE 0 À 7 FAIRE
            AFFICHER salle[i][j]
        FIN POUR

    FIN POUR

FIN
​
FONCTION reserver_place(salle)
VARIABLES
    rang, place : entier

DÉBUT

    AFFICHER "Numéro du rang (1 à 5) : "
    LIRE rang

    AFFICHER "Numéro de la place (1 à 8) : "
    LIRE place

    SI rang < 1 OU rang > 5 ALORS

        AFFICHER "Numéro de rang invalide."

    SINON SI place < 1 OU place > 8 ALORS

        AFFICHER "Numéro de place invalide."

    SINON SI salle[rang - 1][place - 1] = 1 ALORS

        AFFICHER "Cette place est déjà occupée."

    SINON

        salle[rang - 1][place - 1] ← 1

        AFFICHER "Réservation effectuée."

    FIN SI

FIN
​
FONCTION annuler_reservation(salle)
VARIABLES
    rang, place : entier

DÉBUT

    AFFICHER "Numéro du rang (1 à 5) : "
    LIRE rang

    AFFICHER "Numéro de la place (1 à 8) : "
    LIRE place

    SI rang < 1 OU rang > 5 ALORS

        AFFICHER "Numéro de rang invalide."

    SINON SI place < 1 OU place > 8 ALORS

        AFFICHER "Numéro de place invalide."

    SINON SI salle[rang - 1][place - 1] = 0 ALORS

        AFFICHER "Cette place est déjà libre."

    SINON

        salle[rang - 1][place - 1] ← 0

        AFFICHER "Réservation annulée."

    FIN SI

FIN
​
FONCTION afficher_statistiques(salle)
VARIABLES
    i, j : entier
    total, occupees, libres : entier
    taux : réel
    nombre_rang : entier
    maximum : entier
    compteur_rang : entier

DÉBUT

    total ← 40
    occupees ← 0
    maximum ← 0
    nombre_rang ← 1

    POUR i DE 0 À 4 FAIRE

        compteur_rang ← 0

        POUR j DE 0 À 7 FAIRE

            SI salle[i][j] = 1 ALORS
                occupees ← occupees + 1
                compteur_rang ← compteur_rang + 1
            FIN SI

        FIN POUR

        SI compteur_rang > maximum ALORS
            maximum ← compteur_rang
            nombre_rang ← i + 1
        FIN SI

    FIN POUR

    libres ← total - occupees

    taux ← (occupees / total) * 100

    AFFICHER "Nombre total de places : ", total
    AFFICHER "Nombre de places occupées : ", occupees
    AFFICHER "Nombre de places libres : ", libres
    AFFICHER "Taux d'occupation : ", taux, " %"
    AFFICHER "Rang ayant le plus de réservations : Rang ", nombre_rang

FIN
​
FONCTION rechercher_places_libres(salle)
VARIABLES
    rang, j : entier
    places_libres : tableau à une dimension

DÉBUT

    AFFICHER "Numéro du rang (1 à 5) : "
    LIRE rang

    SI rang < 1 OU rang > 5 ALORS

        AFFICHER "Numéro de rang invalide."

    SINON

        places_libres ← tableau vide

        POUR j DE 0 À 7 FAIRE

            SI salle[rang - 1][j] = 0 ALORS
                AJOUTER j + 1 À places_libres
            FIN SI

        FIN POUR

        AFFICHER "Places libres : ", places_libres

    FIN SI

FIN
​
DÉBUT DU PROGRAMME
salle ← initialiser_salle()

choix ← -1

TANT QUE choix ≠ 0 FAIRE

    AFFICHER "1 - Afficher le plan de la salle"
    AFFICHER "2 - Réserver une place"
    AFFICHER "3 - Annuler une réservation"
    AFFICHER "4 - Afficher les statistiques"
    AFFICHER "5 - Rechercher les places libres d'un rang"
    AFFICHER "0 - Quitter"

    RÉPÉTER

        AFFICHER "Votre choix : "
        LIRE choix

    JUSQU'À choix >= 0 ET choix <= 5


    SI choix = 1 ALORS
        afficher_salle(salle)

    SINON SI choix = 2 ALORS
        reserver_place(salle)

    SINON SI choix = 3 ALORS
        annuler_reservation(salle)

    SINON SI choix = 4 ALORS
        afficher_statistiques(salle)

    SINON SI choix = 5 ALORS
        rechercher_places_libres(salle)

    FIN SI

FIN TANT QUE

AFFICHER "Au revoir !"
​
FIN
