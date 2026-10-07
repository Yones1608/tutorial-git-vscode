<!-- tutorial-git-vscode:step-5 -->

## Étape 5 : relire et merger

Ta pull request est valide. Le travail local est maintenant devenu une proposition de changement collaborative sur GitHub.

### Relire le résultat de ton travail local

Avant de merger :

1. ouvre **Files changed**, la vue du diff de la pull request ;
2. vérifie le changement de `robot/config.yaml` ;
3. vérifie les nouvelles règles de `.gitignore` ;
4. ouvre **Commits** : tu dois voir les commits créés depuis ton ordinateur ;
5. ouvre **Checks**, la vue des vérifications automatiques, et attends qu'elles soient terminées.

Cette vue permet de relier tout le tutoriel :

```text
VS Code / terminal
      ↓
working tree
      ↓ git add
staging area
      ↓ git commit
commits locaux
      ↓ git push
branche GitHub
      ↓ pull request
review
      ↓ merge
main sur GitHub
```

### Merger

Quand tout est correct :

1. clique sur **Merge pull request** ;
2. confirme le merge ;
3. supprime la branche sur GitHub si GitHub propose **Delete branch**. Ta branche locale existe encore sur ton ordinateur ; on la supprimera seulement après avoir resynchronisé `main`.

Après le merge, Mona publiera le bilan ici.

> [!IMPORTANT]
> Le merge met à jour `main` **sur GitHub**. Ton clone local ne se met pas à jour par magie : le bilan final te montrera comment resynchroniser ton ordinateur.
