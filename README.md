# repo-helm

# Pour mettre à jour les dépendances
helm dependency build nginx-exemple


# Création 
helm package mon-application

# Copy d'une nouvel chart
cp mon-application-0.1.0.tgz /chemin/vers/repo-chart/charts/

# Mise à jour de index
helm repo index /chemin/vers/repo-chart --url https://github.com/aurelienvelo/repo-helm/repo-chart/main/

### Add and Push on githun
# Naviguez vers votre repo-chart si ce n'est pas déjà fait
cd /chemin/vers/repo-chart
# Ajoutez les nouveaux fichiers
git add charts/mon-application-0.1.0.tgz
git add index.yaml
# Committez les changements
git commit -m "Ajout du chart mon-application version 0.1.0"
# Poussez les changements vers le dépôt distant
git push origin main


### Utilisation ###
# Ajoutez le repo à votre configuration Helm locale (à faire une seule fois)
helm repo add mon-repo https://github.com/aurelienvelo/repo-helm/repo-chart/main/

# Mettez à jour les informations du repo
helm repo update

# Installez le chart depuis le repo
helm install mon-app mon-repo/mon-application