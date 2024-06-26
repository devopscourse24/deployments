# CICD training

![Untitled (1)](https://github.com/devopscourse24/deployments/assets/29838473/45f54e6a-5d18-4598-858e-30d98fda44bc)

L'image décrit un pipeline de CI/CD utilisant Jenkins, Docker, GitHub, Argo et Kubernetes sur AWS EKS. Voici l'explication des étapes :

1. **Déclenchement du Build Jenkins** : Quand le code est poussé localement vers le dépôt GitHub du microservice, un webhook GitHub déclenche un build Jenkins.
2. **Stage 1 - Maven** : Jenkins commence par cloner le dépôt et utilise Maven pour construire l'application (**`mvn build`**).
3. **Stage 2 - Docker** : L'application construite est ensuite empaquetée dans une image Docker qui est construite et poussée vers un registre d'images.
4. **Stage 3 - Mise à jour du manifeste** : Le tag de l'image Docker est mis à jour dans le dépôt de manifestes GitHub.
5. **Détection de changement dans le dépôt de manifestes** : Un changement dans le dépôt de manifestes est détecté.
6. **Déploiement via Argo dans Kubernetes** : Argo déploie la dernière version du fichier manifeste dans un cluster Kubernetes.
7. **AWS EKS** : Le service Kubernetes exécuté est AWS Elastic Kubernetes Service (EKS), qui gère l'orchestration des conteneurs basés sur les configurations définies.

Ceci illustre un flux d'automatisation où le code, une fois poussé, passe par des étapes de build, de conteneurisation et de déploiement sans intervention manuelle, reflétant les principes de CI/CD pour le développement de microservices.
