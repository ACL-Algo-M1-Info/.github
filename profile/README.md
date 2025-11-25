# Projet ACL

## Introduction

## Conventions d'écriture

Il faut respecter une syntaxe globale qui permet d'unifier les fichiers, et fluidifier la navigation dans le projet.
Les changements les plus notables sont:

1. Les identifiants sont en `camelCase`,
2. Il faut respecter l'ordre de définition des éléments dans un fichier (selon le langage),
3. Les accolades vont à la ligne lors de l'ouverture de blocs:
4. Les classes ont une documentation,
5. Les méthodes ont une documentation détaillant chaque variable et le retour,
6. Les variables peuvent être documentées, si jugé nécessaire,
7. Le nom d'un type ou d'une classe est en `PascalCase`,
7. Dans une classe, les champs privés sont préfixés par `_`,
8. Dans une classe, l'usage de `this` est obligatoire,
8. En C, les structures sont wrappées dans une définition de type, et sont également nommées (en plus du type),
9. En C, Aucun typedef par pointeur.

### Exemples

<details>
<summary>Structure d'un fichier C</summary>

```c
// Partie préprocesseur

// Si fichier header, liste les pragmas. Le pragma à mettre est
#pragma once

// Inclusions
#include <stdio.h>
#include <math.h>

// Macros, defines, ...
#define EX 50

// Constantes littérales

/** C'est la valeur de la vie askip... */
const int VALEUR = 42;

// Structures dans les fichiers header
// Avec un typedef. La structure est aussi nommée et doit avoir le nom correspondant au type défini préfixé par un "_"

/**
  * Exemple de structure
  */
typedef struct _MonType
{
    /** Début */
    int debut;
    
    /** Fin */
    int fin;
    
} MonType;

// Entête des fonctions publiques (si un main est dans le même fichier source, ou si fichier header)

/**
  * Calcule l'écart entre le début et la fin
  * @param type Type dont il faut calculer l'écart
  * @return Ecart type
  */
int calculerEcart(MonType *type);

// Main (si un main est dans le même fichier source)

int main(int argc, char *argv[])
{
    MonType t;
    t.debut = 0;
    t.fin = 1;
    
    printf("Ecart type : %d", calculerEcart(&t));

    return 0;
}

// Fonctions (seulement dans les fichiers sources)

int calculerEcart(MonType *type)
{
    return type->fin - type->debut;
}

/**
  * Fonction non visible par le main à ce stade
  */
void _fonctionPrivee()
{
    printf("Cette méthode ne peut pas être appelée dans le main!");
}
```
</details>

<details>
<summary>Structure d'un fichier C++</summary>

```cpp
// Partie préprocesseur

// Si fichier header, liste les pragmas. Le pragma à mettre est
#pragma once

// Inclusions
#include <iostream>
#include <string>

// Macros, defines, ...
#define EX 50

// Clauses using et aliases

using namespace std;
namespace s = std;

// Constantes littérales

/** C'est la valeur de la vie askip... */
const int VALEUR = 42;

// Structures dans les fichiers header
// Avec un typedef. La structure est aussi nommée et doit avoir le nom correspondant au type défini préfixé par un "_"

/**
  * Exemple de structure
  */
typedef struct _MonType
{
    /** Début */
    int debut;
    
    /** Fin */
    int fin;
    
} MonType;

// Définition de classes dans les fichiers header

/**
  * Ma superble classe super belle
  */
class MaClasse : public AutreClasse
{
    // CONSTANTES
    
    const int PI = 3.141592;
    
    // VARIABLES
    
private:

    /** Champ important !! */
    int _monChampPrive;
   
public:

    int monChampPublic;

    // SIGNAUX (pattern observable)
    
    // CONSTRUCTEUR / DESTRUCTEUR
    
    /**
      * Construit l'objet
      * @param ...
      * @param ...
      */
    MaClasse(int monChampPrive, int monChampPublic = PI)
        : _monChampPrive(monChampPrive), monChampPublic(monChampPublic)
    {}
    
    // GETTERS / SETTERS

public:
    
    /**
      * Obtention du champ privé
      */
    int getMonChampPrive() const
    {
        return this._monChampPrive;
    }
    
    // METHODES METIER
    
private:

    void _traitementImportant() const
    {
        cout << "ça ne fait rien du tout" << endl;
    }
    
    // CALLBACKS (pattern observable)
};

// Entête des fonctions publiques (si un main est dans le même fichier source, ou si fichier header)

/**
  * Calcule l'écart entre le début et la fin
  * @param type Type dont il faut calculer l'écart
  * @return Ecart type
  */
int calculerEcart(MonType *type);

// Main (si un main est dans le même fichier source)

int main(int argc, char *argv[])
{
    MonType t;
    t.debut = 0;
    t.fin = 1;
    
    printf("Ecart type : %d", calculerEcart(&t));

    return 0;
}

// Fonctions (seulement dans les fichiers sources)

int calculerEcart(const MonType *type)
{
    return type->fin - type->debut;
}

/**
  * Fonction non visible par le main à ce stade
  */
void _fonctionPrivee()
{
    cout << "Cette méthode ne peut pas être appelée dans le main!" << endl;
}
```
</details>

<details>
<summary>Structure d'un fichier Java</summary>
</details>