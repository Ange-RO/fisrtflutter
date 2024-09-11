flutter clean
flutter pub get


 Le code comporte plusieurs classes, chacune ayant un rôle spécifique dans l'application Flutter.
 Voici un résumé détaillé de chaque classe et son rôle :

### 1. **`MyApp`**

#### Rôle :
- Cette classe configure et initialise l'application Flutter.

#### Détails :
- **Type :** `StatelessWidget` (ne maintient pas d'état interne mutable)
- **Méthode `build` :** 
  - Utilise `ChangeNotifierProvider` pour fournir une instance de `MyAppState` à l'ensemble de l'application.
  - Configure le thème de l'application avec `MaterialApp`, en définissant le titre, le thème (avec Material3) et la page d'accueil (`MyHomePage`).

### 2. **`MyAppState`**

#### Rôle :
- Cette classe gère l'état de l'application, y compris le mot aléatoire actuel et les favoris.

#### Détails :
- **Type :** `ChangeNotifier` (peut notifier les abonnés lorsqu'un changement se produit)
- **Variables :**
  - `current` : Stocke le mot aléatoire actuel.
  - `favorites` : Liste des mots favoris.
- **Méthodes :**
  - `getNext()` : Met à jour `current` avec un nouveau mot aléatoire et notifie les abonnés.
  - `toggleFavorite()` : Ajoute ou supprime le mot actuel de la liste des favoris et notifie les abonnés.

### 3. **`MyHomePage`**

#### Rôle :
- Cette classe fournit une interface utilisateur principale avec une navigation entre les pages "Générateur" et "Favoris".

#### Détails :
- **Type :** `StatefulWidget` (maintient un état mutable)
- **Méthode `createState` :** Crée une instance de `_MyHomePageState`.
  
### 4. **`_MyHomePageState`**

#### Rôle :
- Cette classe gère l'état interne de `MyHomePage`, y compris la gestion de la sélection de la page dans la barre de navigation.

#### Détails :
- **Variables :**
  - `selectedIndex` : Indique quelle page est actuellement sélectionnée dans la barre de navigation.
- **Méthode `build` :**
  - Utilise un `LayoutBuilder` pour obtenir les contraintes de la mise en page.
  - Utilise un `Scaffold` avec une `NavigationRail` pour la navigation entre les pages.
  - Affiche la page sélectionnée (`GeneratorPage` ou `FavoritesPage`) en fonction de `selectedIndex`.

### 5. **`GeneratorPage`**

#### Rôle :
- Cette classe affiche le mot aléatoire actuel et permet à l'utilisateur d'interagir avec (ajouter aux favoris ou obtenir un nouveau mot).

#### Détails :
- **Type :** `StatelessWidget`
- **Méthode `build` :**
  - Récupère l'état actuel de l'application (`MyAppState`).
  - Affiche un `BigCard` avec le mot aléatoire.
  - Fournit des boutons pour ajouter aux favoris ou obtenir un nouveau mot.

### 6. **`BigCard`**

#### Rôle :
- Cette classe affiche le mot aléatoire dans une carte stylisée.

#### Détails :
- **Type :** `StatelessWidget`
- **Variables :**
  - `pair` : Le mot aléatoire à afficher.
- **Méthode `build` :**
  - Affiche le mot dans une `Card` avec un style défini par le thème de l'application.

### 7. **`FavoritesPage`**

#### Rôle :
- Cette classe affiche la liste des mots favoris de l'utilisateur.

#### Détails :
- **Type :** `StatelessWidget`
- **Méthode `build` :**
  - Récupère l'état actuel de l'application (`MyAppState`).
  - Affiche un message si la liste des favoris est vide.
  - Affiche une liste des mots favoris sous forme de `ListView`.

### Résumé des Classes et de leurs Rôles

- **`MyApp`** : Configure l'application et son thème.
- **`MyAppState`** : Gère l'état global de l'application (mot aléatoire et favoris).
- **`MyHomePage`** : Gère la navigation entre les pages principales de l'application.
- **`_MyHomePageState`** : Gère l'état interne de `MyHomePage`, comme la page actuellement sélectionnée.
- **`GeneratorPage`** : Affiche le mot aléatoire actuel et fournit des actions pour interagir avec ce mot.
- **`BigCard`** : Affiche un mot aléatoire dans une carte stylisée.
- **`FavoritesPage`** : Affiche la liste des mots favoris.

Chaque classe joue un rôle spécifique dans l'organisation de l'application, avec une séparation claire des responsabilités, ce qui facilite la gestion et l'évolution de l'application.