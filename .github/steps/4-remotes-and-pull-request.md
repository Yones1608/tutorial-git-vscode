## Étape 4 : comprendre la synchronisation avec GitHub puis ouvrir une pull request

Tes commits locaux sont maintenant publiés sur GitHub. Avant d'ouvrir la pull request, prends deux minutes pour comprendre ce que Git suit réellement.

### Branche locale et branche de référence

Tu travailles directement sur une **branche locale**, ici `feature/robot-status`.

Quand tu as exécuté `git push -u origin feature/robot-status`, Git a aussi créé la branche correspondante sur GitHub et les a associées.

La branche de référence utilisée par défaut pour les prochains `push` et `pull` s'appelle la **branche amont** (_upstream branch_).

Dans ton dépôt, Git relie :

```text
feature/robot-status
        │
        │ upstream
        ▼
origin/feature/robot-status
        │
        │ représente le dernier état connu de
        ▼
feature/robot-status sur GitHub
```

Le point important est que `origin/feature/robot-status` n'est pas directement la branche hébergée sur GitHub : c'est une référence conservée dans ton dépôt local.

Affiche d'abord ton remote :

```bash
git remote -v
```

Puis les branches locales et leur branche amont :

```bash
git branch -vv
```

Git appelle `origin/feature/robot-status` une **référence de suivi distant** (_remote-tracking branch_) : elle mémorise localement le dernier état connu de la branche correspondante sur GitHub.

En résumé :

- `feature/robot-status` : ta branche locale, celle que tu modifies ;
- `feature/robot-status` sur GitHub : la vraie branche distante hébergée par GitHub ;
- `origin/feature/robot-status` : la représentation locale du dernier état connu de cette branche distante ;
- **upstream** : l'association par défaut entre ta branche locale et cette référence distante.

### `fetch`, `pull` et `push`

Mets à jour ta connaissance du remote sans modifier tes fichiers :

```bash
git fetch origin
```

Puis regarde le graphe :

```bash
git log --oneline --graph --decorate --all
```

À retenir :

- `git fetch` récupère les nouveaux commits et met à jour les références `origin/...`, **sans modifier les fichiers de ta branche courante** ;
- `git pull` récupère les changements puis les intègre dans ta branche courante ;
- `git push` envoie tes commits locaux vers la branche correspondante sur le remote.

### Vérifier avant la PR

Exécute encore :

```bash
git status
```

Git doit indiquer qu'il n'y a plus de modification locale non commitée et que ta branche est à jour avec sa branche amont.

### Ouvrir la pull request

Tu connais déjà les pull requests grâce au tutoriel **[GitHub Basics](https://github.com/ENSTARobotics/tutorial-github-basics)**. Ici, la différence est que **tout le travail a été produit localement**, puis publié avec `git push`.

[**Créer ma pull request →**](../../compare/main...feature/robot-status?expand=1)

Choisis :

- **base** : `main`, la branche de destination ;
- **compare** : `feature/robot-status`, la branche qui contient tes changements.

Utilise un titre clair, par exemple :

```text
Mettre à jour la configuration du robot
```

Ajoute une vraie description qui résume ce que tu as fait et pourquoi.

Le bot vérifiera également que la PR contient bien les deux fichiers attendus :

- `robot/config.yaml`
- `.gitignore`

Une fois la PR valide, **reste dans sa Conversation** : comme dans le premier tutoriel, la suite viendra directement à toi.
