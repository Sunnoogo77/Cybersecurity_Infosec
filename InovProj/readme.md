# 🔐 NSMS – Network Security & Monitoring System

> 🚀 Projet de fin d’année – Fusion Cybersécurité & Data  
> 📡 Objectif : Surveiller, analyser et **agir** sur le réseau en temps réel, via une interface web.

---

## 🎯 Objectif du projet

SecurNet Dashboard est une plateforme web destinée à :
- **Surveiller l’activité réseau** d’une infrastructure (trafic, flux, comportements suspects),
- **Détecter automatiquement** des anomalies ou attaques potentielles grâce à l’analyse des données,
- **Réagir en temps réel** en exécutant des actions concrètes sur le réseau (blocage d’IP, quarantaine, création de VLANs...).

Ce projet est né d’une collaboration entre une **équipe Data** (analyse, détection) et une **équipe Cybersécurité** (contrôle, réponse, architecture réseau).  
L’objectif final est d’avoir un **SOC minimaliste**, automatisé et interactif, adapté à des environnements virtualisés.

---

## 🧩 Fonctionnalités Clés

### 🔍 Monitoring (Analyse réseau – côté Data)
- Collecte des données réseau en temps réel (paquets, flux, sessions)
- Identification de comportements anormaux (trafic inhabituel, scans, connexions suspectes)
- Attribution d’un **score de risque** aux IPs ou hôtes actifs
- Tableau de bord avec :
  - Volume de trafic par IP
  - Protocoles utilisés
  - Liste d'alertes de sécurité
  - Historique des événements

### 🛡️ Réponse & Contrôle Réseau (Cybersécurité)

**Actions manuelles ou automatisées via l’interface web :**

#### 🔒 Blocage & Isolation
- Blocage d'une adresse IP suspecte à différents niveaux :
  - Pare-feu (iptables, ACL, etc.)
  - Règles de filtrage sur routeur/switch (ex : `deny`, `drop`)
- Isolation d'une machine dans un **VLAN dédié** pour mise en quarantaine

#### 🧠 Automatisation de la réponse (SOAR simplifié)
- Déclenchement automatique d'actions selon des conditions :
  - Score de menace > 90%
  - Taux d’alertes sur un hôte > seuil critique
- Utilisation de **scripts Ansible, commandes SSH ou API REST** pour appliquer les actions réseau

#### 🔧 Contrôle à distance de l’infrastructure
- Envoi de commandes vers :
  - Routeurs (modification de la config, ajout de routes, filtrage)
  - Switches (gestion VLANs, ports)
  - Firewalls (ajout de règles dynamiques)
- Interfaces possibles :
  - **SSH sécurisé** via scripts (ex : `paramiko` en Python)
  - **API REST/NETCONF** si les équipements les supportent
  - **Ansible Playbooks** déclenchés depuis le backend web

#### 📜 Journalisation & Logs
- Enregistrement de toutes les actions de sécurité prises
- Suivi de l’historique des IPs bloquées / machines isolées
- Interface d’audit pour voir qui a fait quoi, et quand

---

## 🧪 Architecture Générale

```
[Infra Réseau] ---> [Agents de collecte] ---> [Base de données/stream] <--- [Analyse Data]
                                                           |
                                                           v
                                           [Interface Web (Dashboard)]
                                                           |
                                                           v
                                      [Backend Cyber (Contrôle des équipements)]
```

---

## 🛠️ Technologies (prévisionnelles côté Cyber)

| Fonction                        | Technologies envisagées                     |
|--------------------------------|---------------------------------------------|
| Connexion aux équipements      | Python (`paramiko`, `netmiko`), Ansible     |
| Réponse automatisée            | Scripts déclenchés via API ou backend Flask |
| Interface web (cyber)          | Flask ou FastAPI                            |
| Journalisation des actions     | JSON logs, syslog, ou base simple (SQLite/PostgreSQL) |
| Gestion VLAN / routeur         | Commandes CLI via SSH (Cisco/Mikrotik), ou REST API |

> ⚠️ À adapter selon les équipements disponibles.  
> ⚙️ L’infrastructure peut être montée sur VMs avec routeurs/switches simulés ou physiques.

---

## 🧠 Rejoindre l’équipe cybersécurité

Si tu es intéressé·e par la **cybersécurité offensive/défensive**, les réseaux, les firewalls, les VLANs, le scripting ou juste curieux de comprendre comment on **agit concrètement sur une attaque réseau en live**, tu es bienvenu·e !

Tu peux aider sur :
- Le **contrôle réseau** (config routeurs, switchs, VLANs, etc.)
- Le **développement de scripts de réaction** (Python, Ansible)
- L’**architecture de sécurité**
- La **détection de comportements suspects**
- Ou tout simplement tester et casser pour améliorer ! 🧨😄

---

## ✨ Objectif final

Créer un **outil web simple, fonctionnel et impactant** qui montre clairement qu'on peut :
- **Surveiller le réseau en temps réel**
- **Identifier des comportements suspects**
- **Réagir immédiatement**, de manière **manuelle ou automatique**
- Le tout sur une **plateforme que vous avez conçue vous-même**

---

> Merci d’avoir lu jusqu’ici ! Si tu es motivé·e par les projets réseau/sécu, n’hésite pas, rejoins-nous 🔐🔥
