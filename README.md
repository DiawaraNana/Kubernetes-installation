# Script Simple d'Installation Kubernetes

**Auteurs** : Hasna Daoui, Diawara Nana  
**Projet 3-p2**

---

## Description

Dans un contexte où les volumes de données et la complexité applicative augmentent,  
Kubernetes s’impose comme solution d’orchestration incontournable pour les conteneurs.  
Ce projet propose une **solution automatisée, évolutive et reproductible** pour déployer un cluster Kubernetes, avec intégration de :

- **Kubeflow** pour les workflows de machine learning (MLOps)  
- **Rook Ceph** pour le stockage distribué et persistant  

Le but est de simplifier la mise en place d’un environnement cloud-native robuste, sécurisé et prêt à l’usage.

---

## Fonctionnalités

- Installation automatique des dépendances (Docker, kubeadm, Containerd…)
- Initialisation du nœud maître avec `kubeadm init`
- Génération de token pour les nœuds workers
- Installation de Calico (CNI réseau)
- Déploiement de Rook Ceph (stockage distribué)
- Installation de Kubeflow (MLOps)

---

## Structure du projet

- `installmaster.sh` – Script à exécuter sur le nœud master  
- `installworker.sh` – Script à exécuter sur le(s) nœud(s) worker  
- `install_$(date +'%Y%m%d_%H%M%S').log` – Fichier log horodaté  
- `README.md` – Ce fichier  

---

## Prérequis

> - Le nœud master doit être en **mode Bridge**  
> - Ajouter une partition de disque dédiée avant exécution  

---

## Instructions d’exécution

### Sur le nœud **master** :

```bash
sudo nano installmaster.sh
sudo chmod +x installmaster.sh
./installmaster.sh

### Sur le(s) nœud(s) worker :
```bash
sudo nano installworker.sh
sudo chmod +x installworker.sh
./installworker.sh

## Dépannage – Erreurs courantes
1. ❌ swap is enabled
Cause : swap activé

Solution :

bash

sudo swapoff -a
sudo sed -i '/ swap / s/^/#/' /etc/fstab







