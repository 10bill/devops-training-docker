#Bilale ROUAMBA

A.Création du repo Git

git init devops-training-docker
cd devops-training-docker
touch README.md
git add README.md
git commit -m "Initial commit - ajout du fichier README"

B.
2.recuperer image docker hub (docker pull nginx)
3.verifier l'image (docker images)
4.Créer un fichier index.html (echo "Hello World" > index.html)
5. Lancer un container en liant ce fichier avec un volume (docker run -d --name mon-nginx -p 8081:80 -v /html/index.html:/usr/share/nginx/html nginx)
6.supprimer container(docker rm mon-nginx)
7.relancer container, Copier un fichier dans le container après exécution(docker cp index.html mon-nginx:/usr/share/nginx/html/index.html)

C.
1.Crée Dockerfile (FROM nginx

COPY html/index.html /usr/share/nginx/html/index.html

EXPOSE 80)

2.execution de la commande image(docker run -d --name mon-nginx-custom -p 8081:80 mon-nginx-image)

3.Différences entre volume et COPY
a.Monter le volume: (Avantage : Permet des mises à jour en temps réel du fichier sans reconstruire l'image , Inconvenient : Peut compliquer la gestion des autorisations)

b.COPY dans Dockerfile : (Avantage : Image autonome , Inconvenient : Nécessité de reconstruire l'image à chaque modification)

D.
1.base de données avec un container Docker(docker run -d --name db -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=devops -p 3306:3306 mariadb )

PhpMyAdmin (docker run -d --name phpmyadmin -e PMA_HOST=mysql-db -p 8081:80 --network bridge phpmyadmin/phpmyadmin
)

2.execution 2 container (docker run -d --name phpmyadmin -e PMA_HOST=db -p 8081:80 phpmyadmin/phpmyadmin
)

E.Utilisation de docker-compose.yml
Différences entre docker run etdocker-compose
a.docker run : ( Démarrez un seul conteneur, Ne gérer pas les dépendances entre conteneurs )

b.docker-compose :(Définir plusieurs conteneurs dans un fichier YAML , Gère automatiquement les réseaux et les dépendances)


a.lancer tous les container (docker-compose up -d)
b.commande pour stopper(docker-compose down)

Bonnes pratiques Git