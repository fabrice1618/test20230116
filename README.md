# Normalisation de capteur: langage C

## OBLIGATOIRE

les fichiers rendus nommés avec votre prénom et nom en prefixe. Pas d'accents, pas d'espaces, de symboles... exemples: prenom_nom_exo1.c, prenom_nom_exo2.h
- Vous remettrez un fichier Makefile permettant de compiler votre application. Il contiendra aussi une cible "test" permettant d'executer votre programme.

## Contexte

Vous devrez écrire un algorithme qui permet de normaliser les données d'un capteur.
Les données du capteur sont transmises sous la forme d'un tableau. Les valeurs de capteur valides sont comprises entre 0 et 1023.

Vous disposez d'un exemple réalisant ce calcul en utilisant un simple calcul de moyenne, mais les résultats ne sont pas très satisfaisants. En effet, à cause de perturbations électro-magnétiques certaines valeurs de capteur peuvent être plus fortes ou plus faibles que la valeur réelle.

Pour limiter les erreurs de lecture et améliorer les résultats, vous utiliserez l'algorithme simple suivant:
- supprimer les 2 valeurs de capteur les plus basses 
- supprimer les 2 valeurs les plus hautes 
- puis faire la moyenne des 4 valeurs restantes.

## 1 - exercice 1

Vous écrirez un programme en C qui utilise la méthode de calcul ci-dessus et affiche le résultat.

Pour information : vous devriez obtenir le résultat suivant:
Valeur du capteur = 59

## 2 - exercice 2 - bonus

Il est possible de résoudre cet exercice de nombreuses façons différentes. Un algorithme de complexité 3n est moins efficace qu'un algorithme de complexité 1n. Un algo de complexité 3n, fait 3 passes sur les données.

Bonus : 
- 3 points pour un algo de complexité 2n
- 5 points pour un algo de complexité 1n
- 1 point pour avoir optimisé la division par 4 en utilisant l'opérateur >> (décalage de bits)

```C
/*
Fichier exemple: 
Prénom Nom:
*/
#include <stdio.h>

int normaliseCapteur( int valCapteur[8] );

int main(void)
{
    int valCapteur[8] = { 2, 56, 180, 60, 10, 1020, 65, 55 };
    int moyenne;

    // Calcul et affichage de la valeur du capteur
    moyenne = normaliseCapteur(valCapteur);
    printf("Valeur du capteur = %d\n", moyenne);

    return 0;
}

// Fonction qui normalise les données lues. Ici avec une simple moyenne.
int normaliseCapteur( int valCapteur[8] )
{
    int i;
    int total;
    int moyenne;

    total = 0;
    for( i = 0; i < 8; i++) 
        total += valCapteur[i];
    
    moyenne = total / 8;

    return(moyenne);
}
```