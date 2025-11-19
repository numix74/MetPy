# MetPy - Guide pour Claude

## Vue d'ensemble du projet

MetPy est une bibliothèque Python pour l'analyse et la visualisation de données météorologiques. Ce projet fournit des outils pour travailler avec des données atmosphériques, effectuer des calculs météorologiques et créer des visualisations scientifiques.

## Structure du projet

```
MetPy/
├── src/metpy/          # Code source principal
├── tests/              # Tests unitaires et d'intégration
├── docs/               # Documentation
├── examples/           # Exemples d'utilisation
└── setup.py            # Configuration de l'installation
```

## Technologies utilisées

- **Python** : Langage principal
- **NumPy** : Calculs numériques
- **Matplotlib** : Visualisation
- **Pint** : Gestion des unités physiques
- **xarray** : Manipulation de données multidimensionnelles

## Directives de développement

### Configuration de l'environnement

```bash
# Créer un environnement virtuel
python -m venv venv
source venv/bin/activate  # Sur Linux/Mac
# ou
venv\Scripts\activate  # Sur Windows

# Installer les dépendances de développement
pip install -e .[dev,test]
```

### Standards de code

- **Style** : Suivre PEP 8
- **Docstrings** : Format NumPy/SciPy
- **Type hints** : Utiliser les annotations de type Python
- **Longueur de ligne** : Maximum 100 caractères

### Tests

```bash
# Exécuter tous les tests
pytest

# Exécuter avec couverture
pytest --cov=metpy

# Exécuter des tests spécifiques
pytest tests/test_calc.py
```

### Linting et formatage

```bash
# Vérification du style
flake8 src/metpy

# Formatage automatique
black src/metpy tests

# Vérification des imports
isort src/metpy tests
```

## Concepts clés

### Unités physiques

MetPy utilise Pint pour la gestion des unités. Toujours attacher des unités aux valeurs :

```python
from metpy.units import units

temperature = 25 * units.degC
pressure = 1013.25 * units.hPa
```

### Calculs météorologiques

Les fonctions de calcul se trouvent dans `metpy.calc` :

```python
from metpy.calc import dewpoint_from_relative_humidity

dewpoint = dewpoint_from_relative_humidity(temperature, rh)
```

### Visualisation

MetPy fournit des outils pour créer des cartes météorologiques :

```python
from metpy.plots import SkewT, StationPlot
```

## Tâches courantes

### Ajouter une nouvelle fonction de calcul

1. Ajouter la fonction dans `src/metpy/calc/`
2. Inclure des docstrings complètes avec exemples
3. Ajouter des tests dans `tests/calc/`
4. Vérifier la gestion des unités
5. Mettre à jour la documentation si nécessaire

### Corriger un bug

1. Créer un test qui reproduit le bug
2. Corriger le problème
3. Vérifier que tous les tests passent
4. Mettre à jour la documentation si nécessaire

### Ajouter de la documentation

1. Modifier les fichiers dans `docs/`
2. Construire la documentation : `make -C docs html`
3. Vérifier le rendu dans `docs/_build/html/`

## Ressources utiles

- **Documentation officielle** : https://unidata.github.io/MetPy/
- **Référence API** : Voir docs/api/
- **Exemples** : Voir examples/ et la galerie d'exemples dans docs/
- **Issues GitHub** : Pour les bugs et demandes de fonctionnalités

## Notes importantes pour Claude

### Lors de l'analyse du code

- Toujours vérifier la cohérence des unités dans les calculs
- Respecter les conventions de nommage scientifiques
- Prendre en compte la compatibilité NumPy/xarray

### Lors de l'écriture de tests

- Tester avec différentes unités d'entrée
- Vérifier les cas limites (valeurs NaN, infinies, etc.)
- Inclure des tests pour les erreurs attendues

### Lors de la documentation

- Inclure des références scientifiques pour les formules
- Fournir des exemples pratiques
- Expliquer les paramètres d'entrée et leurs unités attendues

## Commandes Git

```bash
# Créer une branche de fonctionnalité
git checkout -b feature/nouvelle-fonctionnalite

# Commiter les changements
git add .
git commit -m "Description claire du changement"

# Pousser vers le dépôt distant
git push -u origin feature/nouvelle-fonctionnalite
```

## Contact et contribution

- Suivre le guide de contribution dans CONTRIBUTING.md
- Discuter des changements majeurs dans les issues avant de commencer
- Respecter le code de conduite de la communauté

---

*Ce document est conçu pour aider Claude à comprendre et travailler efficacement avec le projet MetPy.*
