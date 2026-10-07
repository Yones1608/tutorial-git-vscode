## Étape 3 : lire l'historique, annuler une modification et utiliser Source Control

Tu viens de créer puis pousser un commit. Avant d'en faire un deuxième, apprends à regarder l'historique et à corriger une erreur locale sans paniquer.

### 1. Explorer l'historique

Dans le terminal :

```bash
git log --oneline --graph --decorate --all
```

Ces options modifient seulement l'affichage :

- `--oneline` affiche un commit par ligne ;
- `--graph` dessine les embranchements de l'historique ;
- `--decorate` affiche les noms de branches et autres références près des commits ;
- `--all` inclut toutes les références connues, pas seulement la branche courante.

Tu dois voir au minimum :

- `main`, ta branche principale locale ;
- `feature/robot-status`, ta branche de travail locale ;
- ton commit récent ;
- des références comme `origin/main` ou `origin/feature/robot-status`.

Ces noms qui commencent par `origin/` sont des **références locales représentant l'état connu des branches sur GitHub**. L'étape suivante expliquera précisément leur rôle.

Git utilise aussi le nom spécial **`HEAD`** pour désigner l'endroit où tu te trouves actuellement dans l'historique, en pratique le dernier commit de ta branche courante.

Affiche ce commit en détail :

```bash
git show HEAD
```

Dans VS Code, ouvre **Source Control** puis la vue **Graph** si elle est disponible. Tu observes le même historique, mais visuellement.

### 2. Annuler une modification non commitée

Ouvre `robot/mission.md` et ajoute temporairement une ligne quelconque, par exemple :

```text
TEST TEMPORAIRE
```

Enregistre puis regarde :

```bash
git status
git diff robot/mission.md
```

Décide finalement de jeter cette modification :

```bash
git restore robot/mission.md
```

Puis :

```bash
git status
```

La modification a disparu.

> [!WARNING]
> `git restore` sur un fichier modifié remplace son contenu local par la version enregistrée dans Git. Vérifie toujours ce que tu jettes avant de l'utiliser.

### 3. Comprendre `.gitignore`

Un fichier **`.gitignore`** indique à Git quels fichiers ou dossiers non suivis il doit ignorer. Ils restent sur ton ordinateur mais ne viennent plus polluer `git status` et ne sont pas ajoutés par erreur à un commit.

Les projets robotiques génèrent souvent beaucoup de fichiers qu'on ne veut **pas** versionner : dossiers de compilation, caches Python, environnements virtuels, logs, etc.

Ouvre `.gitignore` dans VS Code et ajoute :

```gitignore
build/
install/
log/
__pycache__/
.venv/
```

Dans **Source Control**, ouvre le diff de `.gitignore` et relis-le.

Cette fois, stage le fichier depuis VS Code avec le bouton **+** à côté du fichier. Vérifie ensuite dans le terminal que VS Code a bien exécuté l'équivalent d'un `git add` :

```bash
git status
git diff --staged
```

### 4. Committer depuis VS Code

Dans **Source Control** :

1. saisis un message clair, par exemple `Ignorer les fichiers générés` ;
2. clique sur **Commit**.

Puis vérifie le résultat dans le terminal :

```bash
git log -2 --oneline
git status
```

Tu viens d'utiliser deux interfaces différentes sur **le même Git** : le terminal et VS Code.

Publie le deuxième commit :

```bash
git push
```

Mona vérifiera le contenu de `.gitignore` et que ta branche contient désormais plusieurs commits.
