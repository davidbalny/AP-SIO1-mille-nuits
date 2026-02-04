# Créer une documentation avec MkDocs et GitHub Pages
## Préparation des prérequis
### 1. Installer Git
#### Linux (Debian / Ubuntu)

```bash
sudo apt update
sudo apt install git -y
````

```bash
git --version
```

#### macOS

```bash
brew install git
````

#### macOS

```bash
brew install git
```

#### Windows

Télécharger et installer :  
[https://git-scm.com/downloads](https://git-scm.com/downloads)

Vérification :

```bash
git --version
```

---

### 2. Installer Python

#### Linux (Debian / Ubuntu)

```bash
sudo apt install python3 python3-pip -y
```

#### macOS

```bash
brew install python
```

#### Windows

Télécharger et installer :  
[https://www.python.org/downloads/](https://www.python.org/downloads/)

⚠️ Cocher **Add Python to PATH**

Vérification :

```bash
python --version
pip --version
```

---

### 3. Installer MkDocs et le thème Material

```bash
pip install mkdocs mkdocs-material
```

Vérification :

```bash
mkdocs --version
```

---

## Création du projet de documentation

### 4. Créer un dépôt GitHub

1. Créer un dépôt GitHub public (exemple : `ma-documentation`)
    
2. Cloner le dépôt :
    

```bash
git clone https://github.com/<user>/ma-documentation.git
cd ma-documentation
```

---

### 5. Initialiser MkDocs

```bash
mkdocs new .
```

Structure obtenue :

```text
.
├── docs/
│   └── index.md
└── mkdocs.yml
```

---

## Rédaction de la documentation

### 6. Écrire le contenu Markdown

Modifier le fichier `docs/index.md` :

````markdown
# Bienvenue

Bienvenue dans la documentation de mon projet.

## Installation

```bash
pip install mon-projet
````

## Utilisation

### 7. Configurer le site

````
Modifier le fichier `mkdocs.yml` :

```yaml
site_name: Ma Documentation
site_url: https://<user>.github.io/ma-documentation

theme:
  name: material

nav:
  - Accueil: index.md
````

---

## Prévisualisation locale

### 8. Lancer le serveur local

```bash
mkdocs serve
```

Accéder à l’adresse :

```
http://127.0.0.1:8000
```

Le site se met à jour automatiquement lors des modifications.

---

## Publication sur GitHub Pages

### 9. Publier la documentation

```bash
mkdocs gh-deploy
```

Cette commande :

- Génère le site statique
    
- Crée la branche `gh-pages`
    
- Active GitHub Pages automatiquement
    

---

## Accès à la documentation

La documentation est accessible à l’adresse :

```
https://<user>.github.io/ma-documentation
```

---

## Bonnes pratiques Markdown

- Utiliser des titres hiérarchisés (`#`, `##`, `###`)
    
- Ajouter des exemples de code
    
- Documenter chaque étape
    

Exemple de note (thème Material) :

```markdown
!!! note
    Ceci est une note importante.
```

---

## Ressources

- MkDocs : [https://www.mkdocs.org](https://www.mkdocs.org)
    
- Material for MkDocs : [https://squidfunk.github.io/mkdocs-material/](https://squidfunk.github.io/mkdocs-material/)
    
- GitHub Pages : [https://pages.github.com](https://pages.github.com)
    