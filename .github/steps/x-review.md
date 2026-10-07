<!-- tutorial-git-vscode:review -->

## Bilan : ton cycle de travail Git local est complet

🎉 Tu viens d'effectuer le cycle Git que tu réutiliseras sur les projets du club.

### Ce que tu as réellement fait

```text
git clone
   ↓
git status
   ↓
git switch -c feature/...
   ↓
modifier dans VS Code
   ↓
git diff
   ↓
git add
   ↓
git diff --staged
   ↓
git commit
   ↓
git push
   ↓
pull request
   ↓
relecture
   ↓
merge
```

Tu as aussi utilisé :

- `git remote -v` pour voir où se trouve `origin` ;
- `git log` et `git show` pour inspecter l'historique ;
- `git restore` et `git restore --staged` pour revenir proprement sur une action locale ;
- `git fetch` pour mettre à jour ta connaissance du dépôt distant ;
- le panneau **Source Control** de VS Code comme autre interface sur le même moteur Git.

### Dernière étape sur ton ordinateur : resynchroniser `main`

Le merge vient d'avoir lieu sur GitHub. Ton dépôt local possède encore son ancien `main`.

Dans le terminal de VS Code :

```bash
git switch main
git pull --ff-only
```

L'option `--ff-only` signifie **fast-forward only** : Git accepte uniquement d'avancer ton `main` local jusqu'au nouveau commit de `main` sur GitHub. S'il faudrait créer un commit de merge local pour y arriver, la commande s'arrête au lieu de décider à ta place.

Supprime ensuite la branche locale devenue inutile :

```bash
git branch -d feature/robot-status
```

L'option `-d` demande à Git de supprimer la branche locale seulement si son travail a bien été intégré.

Enfin, nettoie les anciennes références de branches distantes :

```bash
git fetch --prune
```

`--prune` retire les références `origin/...` qui correspondent à des branches supprimées sur GitHub. Cela ne supprime pas tes branches locales.

Termine par :

```bash
git status
git branch -vv
git log --oneline --graph --decorate --all
```

### Le réflexe à garder

Quand quelque chose te paraît étrange :

```bash
git status
```

Avant un commit :

```bash
git diff
git diff --staged
```

Avant de commencer une nouvelle tâche :

```bash
git switch main
git pull --ff-only
git switch -c feature/ma-tache
```

### Dans le parcours ENSTARobotics

Le tutoriel précédent, **[GitHub Basics](https://github.com/ENSTARobotics/tutorial-github-basics)**, t'a appris les concepts depuis le navigateur. Celui-ci t'a appris à appliquer le même cycle depuis ton ordinateur.

Tu connais maintenant le chemin normal. Le prochain tutoriel utile sera consacré à ce qui arrive quand deux historiques se rencontrent mal : **les conflits de merge**, leur lecture et leur résolution dans VS Code.

Pour aller plus loin en attendant :

- documentation Git : <https://git-scm.com/doc>
- documentation GitHub sur Git : <https://docs.github.com/get-started/using-git>
- documentation VS Code Source Control : <https://code.visualstudio.com/docs/sourcecontrol/overview>
