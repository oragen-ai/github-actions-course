# github-actions-course

Mon dépôt de pratique pour la formation Coursera / Packt
« Automate your DevOps pipelines with GitHub Actions ».

Code d'origine : [PacktPublishing/Automate-your-DevOps-pipelines-with-GitHub-Actions-](https://github.com/PacktPublishing/Automate-your-DevOps-pipelines-with-GitHub-Actions-)
(licence MIT, voir `LICENSE`).

## Comment ça marche

- `03-app-dotnet/` : l'application web du cours (ASP.NET, C#).
- `cours-workflows/` : tous les workflows du cours, **en attente**. GitHub ne les lance pas ici.
- `.github/workflows/` : les workflows **actifs**. À chaque module, je déplace le workflow
  correspondant ici :

      git mv cours-workflows/010-blank-workflow.yml .github/workflows/

- `ressources/` : les PDF du cours. **Absents de GitHub** (exclus par `.gitignore`), ils restent seulement sur ma machine.

**Piège à chaque activation :** la plupart des workflows du cours contiennent `branches: none`.
L'auteur a mis ça pour les couper : ils ne se lancent qu'à la main (bouton *Run workflow*).
Pour qu'un workflow se lance tout seul à chaque push, remplacer `none` par `[ main ]`.

## Avancement

| Module | Workflow | Statut | Remarque |
|---|---|---|---|
| 010 | Workflow vide | ⬜ | |
| 020 | Lancement manuel avec paramètres | ⬜ | |
| 030 | Build .NET | ⬜ | |
| 031 | Déploiement sur Azure Web App | ⛔ | Compte Azure requis : lire seulement |
| 032 | Analyse de code CodeQL | ⬜ | |
| 040 | Linter (super-linter) | ⬜ | |
| 041 | Correcteur orthographique | ⬜ | Se lance **tout seul** (pas de `branches: none`). Dictionnaire anglais : ce README en français le fera échouer. `.cspell/project-words.txt` est en UTF-16, à reconvertir en UTF-8 |
| 050 | Build Docker | ⬜ | |
| 052 | Image Docker sur GitHub Container Registry | ⬜ | `IMAGE_NAME` pointe vers le compte de l'auteur : mettre `oragen-ai/github-actions-course` (en minuscules) |
| 060 | Kubernetes | 📖 | Fichier `.md` de liens, pas un workflow |
| 070 | Self-hosted runner | 🚫 | **Ne pas activer** : dépôt public, n'importe qui pourrait exécuter du code sur ma machine |
| 080 | Reusable workflow | ⬜ | Appelle le dépôt de l'auteur et exige un secret `TOKEN` qu'on n'a pas : pointer vers ce dépôt et retirer le bloc `secrets` |
| 090 | Connexion Azure OIDC | ⛔ | Compte Azure requis : lire seulement |
| 0100 | Déclencher Azure DevOps | ⛔ | Compte Azure DevOps requis : lire seulement |

Légende : ⬜ à faire · ✅ fait · ⛔ impossible sans Azure · 📖 lecture · 🚫 interdit
