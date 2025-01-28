# Sudoers
Add user in sudo mod
Pour ajouter un utilisateur aux sudoers sur Debian, voici les étapes à suivre :

---

### Étape 1 : Connectez-vous en tant que root ou un utilisateur avec des privilèges sudo
Si vous êtes déjà connecté en tant qu'utilisateur avec des privilèges root, vous pouvez passer aux étapes suivantes. Sinon, utilisez la commande suivante pour passer en root :
```bash
su -
```

---

### Étape 2 : Ajouter l'utilisateur au groupe `sudo`
Par défaut, les utilisateurs du groupe `sudo` ont des privilèges sudo sur Debian. Vous pouvez ajouter un utilisateur existant au groupe `sudo` avec la commande suivante :
```bash
usermod -aG sudo nom_utilisateur
```
Remplacez `nom_utilisateur` par le nom de l'utilisateur que vous souhaitez ajouter.

---

### Étape 3 : Vérifiez les privilèges sudo
Pour vérifier si l'utilisateur a bien été ajouté au groupe `sudo`, utilisez cette commande :
```bash
groups nom_utilisateur
```
Vous devriez voir `sudo` parmi les groupes listés.

---

### Étape 4 : (Optionnel) Modifier le fichier `sudoers` pour une configuration spécifique
Si vous avez besoin d'accorder des permissions plus spécifiques ou personnaliser les privilèges :
1. Éditez le fichier `sudoers` avec l'éditeur `visudo` (cela permet d'éviter les erreurs de syntaxe) :
   ```bash
   visudo
   ```
2. Ajoutez une ligne comme celle-ci pour accorder à l'utilisateur un accès complet :
   ```
   nom_utilisateur ALL=(ALL:ALL) ALL
   ```

---

### Étape 5 : Tester les permissions sudo
Connectez-vous en tant que l'utilisateur en question :
```bash
su - nom_utilisateur
```
Et testez une commande avec sudo, par exemple :
```bash
sudo apt update
```
