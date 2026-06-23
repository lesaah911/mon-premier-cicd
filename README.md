# Mon Premier CI/CD — Jenkins + Ansible

Premier projet de pipeline CI/CD : déploiement automatisé d'un site statique via Jenkins et Ansible.

> Ce projet est un TP d'introduction au CI/CD, réalisé avant le projet [`secure-ci-cd-pipeline`](https://github.com/lesaah911/secure-ci-cd-pipeline) qui en constitue la version avancée avec scans de sécurité automatisés.

## Ce que fait ce pipeline

À chaque exécution, Jenkins :

1. Vérifie la présence des fichiers nécessaires
2. Déploie le site via un playbook Ansible sur un serveur distant
3. Teste que le serveur répond correctement avec un `curl`

## Stack technique

| Composant | Rôle |
|-----------|------|
| Jenkins | Orchestration du pipeline |
| Ansible | Déploiement du site sur le serveur distant |
| SSH | Connexion sécurisée au serveur cible |
| HTML/CSS | Contenu du site déployé |

## Structure du repo

```
.
├── Jenkinsfile          # Définition du pipeline
├── deploy.yml           # Playbook Ansible de déploiement
├── inventory.ini        # Inventaire Ansible (IP masquée)
└── website/             # Contenu statique déployé
```

## Lancer le pipeline

### Prérequis
- Jenkins installé avec les plugins Git et Ansible
- Clé SSH configurée dans Jenkins (`/var/lib/jenkins/.ssh/`)
- Serveur cible accessible

### Configuration
Remplacer `<VOTRE_IP>` dans `inventory.ini` par l'IP du serveur cible, puis configurer le job Jenkins en pointant sur ce repo (branch : `main`, script : `Jenkinsfile`).

## Ce que ce projet démontre

- Mise en place d'un pipeline Jenkins basique
- Déploiement automatisé avec Ansible
- Connexion SSH sécurisée via clé
- Vérification post-déploiement

## Évolution

Ce projet a évolué vers [`secure-ci-cd-pipeline`](https://github.com/lesaah911/secure-ci-cd-pipeline), qui ajoute une couche DevSecOps complète : scan de secrets (Gitleaks), scan de vulnérabilités (Trivy) et analyse statique du code (Semgrep).

## Contexte

Projet réalisé dans le cadre du Mastère Cybersécurité IPSSI Paris (2025-2027).
