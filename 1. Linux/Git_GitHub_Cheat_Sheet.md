# Fiche récap : Gérez du code avec Git et Github

## Flux de travail (Workflow)
1. **Working directory** (Développement)
2. **Stage** (Index)
3. **Repository** (Dépôt local)
4. **GitHub** (Dépôt distant)

## Configuration et initialisation
| Commande | Description |
| :--- | :--- |
| `cd Documents/Premier Projet` | Pour vous positionner dans le dossier Premier Projet |
| `git init` | Pour initialiser un nouveau dépôt Git |
| `git clone URL_DU_REPO` | Pour cloner un dépôt existant à partir de l'URL fournie |

## Gestion des fichiers et des commits
| Commande | Description |
| :--- | :--- |
| `git status` | Pour montrer l'état des fichiers |
| `git add fichier.html` | Pour ajouter des fichiers à l'index pour le prochain commit |
| `git commit -m "Message de commit"` | Pour créer un nouveau commit avec les fichiers ajoutés à l'index |

## Gestion des branches
| Commande | Description |
| :--- | :--- |
| `git branch` | Pour lister toutes les branches |
| `git branch NOM_DE_LA_BRANCHE` | Pour créer une nouvelle branche |
| `git checkout NOM_DE_LA_BRANCHE` | Pour changer de branche |
| `git merge NOM_DE_LA_BRANCHE` | Pour fusionner la branche spécifiée dans la branche actuelle |

## Travailler avec des dépôts distants
| Commande | Description |
| :--- | :--- |
| `git push` | Pour envoyer la nouvelle version sur le dépôt distant |
| `git pull` | Pour récupérer les dernières modifications du dépôt distant |

## Historique et inspection
| Commande | Description |
| :--- | :--- |
| `git log` | Pour voir l'historique des commits |
| `git stash` | Pour enregistrer temporairement des modifications non indexées |
| `git stash apply` | Pour appliquer les modifications enregistrées avec stash |