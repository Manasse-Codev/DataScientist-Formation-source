# DataScientist Formation

Projet de formation et d'expérimentation en **Data Science avec Python**.

Ce dépôt contient les travaux pratiques, notebooks Jupyter, exercices et expérimentations réalisés au cours de la formation.

---

## 📋 Prérequis

Avant de commencer, il est recommandé d'avoir :

* Python **3.12** ou une version compatible
* Git
* pip
* `python3-venv`
* Jupyter

Le projet utilise un **environnement virtuel Python (`.venv`)** afin d'isoler les dépendances du projet du Python installé sur le système.

> ⚠️ Sur les distributions Linux récentes basées sur Debian/Ubuntu, l'installation directe de packages avec `pip` dans le Python système peut être bloquée par **PEP 668**. Il faut donc utiliser l'environnement virtuel du projet.

---

# 🚀 Installation

## 1. Cloner le projet

Avec SSH :

```bash
git clone git@github.com:Manasse-Codev/DataScientist-Formation-source.git
```

Entrer dans le projet :

```bash
cd DataScientist-Formation-source
```

> L'utilisation de SSH permet d'éviter de saisir un Personal Access Token GitHub à chaque opération Git.

---

## 2. Installer le support des environnements virtuels

### Linux Mint / Ubuntu / Debian

Si nécessaire :

```bash
sudo apt update
sudo apt install python3-full python3-venv
```

Vérifier Python :

```bash
python3 --version
```

Exemple :

```text
Python 3.12.x
```

---

## 3. Créer l'environnement virtuel

Dans le dossier du projet :

```bash
python3 -m venv .venv
```

Cette commande crée le dossier :

```text
.venv/
```

L'environnement virtuel permet d'installer les bibliothèques du projet sans modifier le Python système.

---

## 4. Activer l'environnement virtuel

Sous Linux :

```bash
source .venv/bin/activate
```

Lorsque l'environnement est correctement activé, le terminal doit afficher :

```text
(.venv) utilisateur@ordinateur:~/DataScientist-Formation-source$
```

Le `(.venv)` indique que l'environnement virtuel est actif.

---

## 5. Mettre pip à jour

Une fois `.venv` activé :

```bash
python -m pip install --upgrade pip
```

---

## 6. Installer les dépendances

Si le fichier `requirements.txt` existe :

```bash
pip install -r requirements.txt
```

Sinon, pour installer les dépendances principales :

```bash
pip install numpy matplotlib jupyter
```

Les principales bibliothèques utilisées actuellement sont :

* **NumPy** : calcul numérique et manipulation de tableaux
* **Matplotlib** : visualisation et graphiques
* **Jupyter** : notebooks interactifs pour les exercices et expérimentations

---

# 📦 Générer `requirements.txt`

Après avoir installé les dépendances dans `.venv`, il est recommandé de générer le fichier :

```bash
pip freeze > requirements.txt
```

Le fichier permet à un autre développeur de recréer le même environnement avec :

```bash
pip install -r requirements.txt
```

> Le fichier `requirements.txt` doit être versionné avec Git.

---

# 📓 Lancer Jupyter

Vérifier que l'environnement virtuel est actif :

```bash
source .venv/bin/activate
```

Puis lancer Jupyter :

```bash
jupyter notebook
```

ou, de préférence :

```bash
jupyter lab
```

Jupyter ouvrira normalement une interface dans le navigateur.

---

# 🧪 Vérifier l'installation

Pour vérifier NumPy :

```bash
python -c "import numpy; print(numpy.__version__)"
```

Pour vérifier Matplotlib :

```bash
python -c "import matplotlib; print(matplotlib.__version__)"
```

Pour vérifier Jupyter :

```bash
jupyter --version
```

---

# 💻 Utilisation avec VS Code

Ouvrir le projet :

```bash
code .
```

Dans VS Code :

1. Ouvrir la palette de commandes avec `Ctrl + Shift + P`
2. Rechercher **Python: Select Interpreter**
3. Sélectionner :

```text
.venv/bin/python
```

Pour les notebooks `.ipynb`, sélectionner également le kernel Python correspondant à `.venv`.

---

# 🔄 Workflow quotidien

À chaque nouvelle session de travail :

```bash
cd DataScientist-Formation-source
source .venv/bin/activate
```

Puis lancer Jupyter :

```bash
jupyter lab
```

Lorsque le travail est terminé :

```bash
deactivate
```

---

# 🌿 Git et GitHub

## Vérifier l'état du projet

```bash
git status
```

## Ajouter les modifications

```bash
git add .
```

## Créer un commit

```bash
git commit -m "description de la modification"
```

## Envoyer les modifications sur GitHub

```bash
git push origin main
```

---

# 🔐 Authentification GitHub avec SSH

Le projet utilise une connexion SSH pour GitHub.

Vérifier la connexion :

```bash
ssh -T git@github.com
```

Si l'authentification est correctement configurée, GitHub doit reconnaître le compte associé à la clé SSH.

Vérifier l'adresse distante du dépôt :

```bash
git remote -v
```

Elle doit utiliser une adresse de ce type :

```text
origin  git@github.com:Manasse-Codev/DataScientist-Formation-source.git
```

et non :

```text
https://github.com/Manasse-Codev/DataScientist-Formation-source.git
```

---

# ⚠️ Important : environnement virtuel

Le dossier `.venv` ne doit **pas** être envoyé sur GitHub.

Le fichier `.gitignore` doit contenir :

```gitignore
.venv/
__pycache__/
*.pyc
.ipynb_checkpoints/
```

Cela évite d'envoyer l'environnement Python local et les fichiers temporaires dans le dépôt.

---

# 📁 Structure du projet

Une structure recommandée :

```text
DataScientist-Formation-source/
│
├── .venv/                  # Environnement virtuel local
├── notebooks/              # Notebooks Jupyter
├── data/                   # Jeux de données
├── src/                    # Code Python
├── tests/                  # Tests
│
├── .gitignore
├── requirements.txt
├── README.md
└── ...
```

> Le contenu exact des dossiers peut évoluer au fur et à mesure de la formation.

---

# 🛠️ Résolution des problèmes courants

## `externally-managed-environment`

Si cette erreur apparaît :

```text
error: externally-managed-environment
```

Ne forcez pas l'installation avec :

```bash
pip install --break-system-packages
```

Créez plutôt un environnement virtuel :

```bash
python3 -m venv .venv
```

Puis :

```bash
source .venv/bin/activate
```

Et enfin :

```bash
pip install -r requirements.txt
```

---

## `.venv/bin/activate: Aucun fichier ou dossier de ce nom`

Cela signifie généralement que l'environnement virtuel n'existe pas encore.

Exécuter :

```bash
sudo apt install python3-full python3-venv
```

Puis :

```bash
python3 -m venv .venv
```

Et :

```bash
source .venv/bin/activate
```

---

## `python3 pip install ...`

Cette commande est incorrecte :

```bash
python3 pip install numpy
```

Utiliser :

```bash
python3 -m pip install numpy
```

ou, lorsque `.venv` est activé :

```bash
pip install numpy
```

---

# 👨‍💻 Auteur

**Manasse-Codev**

Projet personnel de formation et de progression en **Python / Data Science**.

---

## 📌 État du projet

Projet en cours de développement et d'apprentissage.

Les notebooks et exercices seront progressivement ajoutés au dépôt.
