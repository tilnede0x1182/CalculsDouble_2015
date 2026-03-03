# CalculsDouble

Librairie de calculs en Java avec calculs exacts sur les décimaux. Les nombres sont stockés sous forme de chaînes de caractères, permettant des calculs sans perte de précision.

## Prérequis

- Java (JDK 8+)
- Python 3
- Make

## Compilation

```bash
make compile
```

Cette commande :
1. Lance le préprocesseur Python sur `src/CalculsDouble.java`
2. Génère `src/CalculsDouble_modifie.java` (fichier passé par le préprocesseur d'imports)
3. Compile vers `build/`

## Pourquoi le préprocesseur d'imports ?

A l'époque de la création initiale de la librairie (2014) je ne connaisais pas bien les modataliés d'imports de fichiers en java et j'ai créé un préopresseur d'imports en python pour le faire.
Par la suite je l'ai gardé car je le trouvais intéressant sur le plan du code, mais techniquement, il serait sans doute plus juste de
refactorer le code pour utiliser les imports standarts de Java... Mais ce n'est pas prévu.

## Exécution

```bash
make run
```

## Génération Javadoc

```bash
make javadoc
```

La documentation est générée dans `javadoc/`.

## Structure

```
.
├── src/
│   ├── CalculsDouble.java          # Fichier maître (imports personnalisés)
│   ├── CalculsDouble_modifie.java  # Fichier généré (compilable)
│   ├── Fonctions_utilitaires/      # Constructeurs, utilitaires
│   ├── Operations/                 # +, -, *, /
│   └── Utilitaire/                 # Préprocesseur Python
├── build/                          # Classes compilées
├── javadoc/                        # Documentation générée
└── tests/                          # Tests JavaScript
```

## Fonctionnalités

- Opérations de base : addition, soustraction, multiplication, division
- Comparaison, valeur absolue, arrondis
- Décomposition en facteurs premiers
- Support représentation française (virgule) et anglaise (point)
- Arithmétique sur grands nombres (pas de limite Integer.MAX_VALUE)

## Tests

```bash
make run
```

23 tests unitaires couvrant :
- Constructeurs (positif, négatif, décimal, zéro)
- Addition, soustraction, multiplication, division
- Valeur absolue
- Division par zéro (retourne null avec message)
- Grands nombres (> 10 chiffres)

## À noter

**Reconnaissance_expression/** : Contient 2 fichiers mais seul `Reconnaissance_doubles_sans_parentheses.java` est utile. La version `_entiers_` est redondante car la version doubles gère aussi les entiers (un entier est un cas particulier de décimal).

**Archives/** : Anciennes versions avant refactor (2026-02-25)
- `CalculsDouble_modifie.java` : ancienne version du fichier passé par le préprocesseur d'imports
- `CalculsDouble_modifie.java.backup` : sauvegarde de sécurité (code non refactorisé)
- `compile.bat` : ancien script batch (remplacé par Makefile)
- `generate_javadoc.bat` : ancien script batch (remplacé par Makefile)
- `python3m1.py` : ancienne version du préprocesseur (code non refactorisé)
- `READ-ME.txt` : instructions de compilation initiales
