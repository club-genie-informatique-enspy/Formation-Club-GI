# Cours - S1 - Réseau : Topologie - Protocoles Réseau OSI et TCP/IP



## Table des matières

1. [Introduction aux réseaux]
2. [Concepts de base]
3. [Le modèle OSI]
   - [Les 7 couches du modèle OSI]
   - [Protocol Data Unit (PDU)]
4. [Principaux protocoles réseau]
5. [Les topologies réseau]
6. [Applications et usage pratique : Adressage IP et Subnetting]
   - [Cas Pratique Corrigé : Découpage de Sous-Réseaux pour l'Université]



## 1. Introduction aux réseaux

### Qu'est-ce qu'un réseau informatique ?

De manière simple, un réseau informatique est un ensemble d'**appareils connectés** qui **échangent des informations** entre eux.

**Formule simplifiée :**
### Questions fondamentales

Trois questions essentielles permettent de mieux comprendre les réseaux :

- **C'est quoi exactement ?**
- **À quoi servent-ils ?**
- **Sont-ils indispensables ?**

### Exemples de réseaux utilisés

Les réseaux sont omniprésents dans notre quotidien. Plusieurs technologies coexistent :

- **4G / 5G** - Réseaux mobiles
- **Bluetooth** - Connexions courte portée
- **WWW (World Wide Web)** - Internet mondial

---

## 2. Concepts de base

### Applications nécessitant un réseau

**Applications nécessitant obligatoirement un réseau :**
- Pinterest, TikTok, YouTube, LinkedIn, Spotify, Snapchat, WhatsApp, Skype, Reddit, Twitch.

**Applications pouvant fonctionner hors ligne :**
- Aucune (selon la source initiale, soulignant la dépendance quasi-totale des applications modernes au réseau).

### Que se passe-t-il si le réseau tombe en panne ?

En cas de panne réseau, plusieurs impacts sont observables :

- Impossibilité d'accéder aux services en ligne
- Perte de connectivité avec les serveurs distants
- Interruption des communications en temps réel
- Dégradation ou arrêt des services cloud
- Perte de chiffre d'affaires (dans un contexte commercial)

---

## 3. Le modèle OSI

### Définition

**OSI = Open System Interconnection**

C'est une **norme** qui décrit comment se font les **communications dans un réseau** .

Le modèle OSI est divisé en **7 couches**, ayant chacune un rôle spécifique dans la chaîne de transmission de l'information, de l'application utilisateur (couche 7) au câble physique (couche 1).

---

### Les 7 couches du modèle OSI

| # | Nom de la Couche | Rôle principal | PDU (Unité de Donnée) | Exemples |
|:---:|:----------------|:----------------|:---------------------|:----------|
| **7** | **Application** | Interface utilisateur, gère les applications réseau. | Donnée | HTTP, DNS, DHCP, FTP |
| **6** | **Présentation**| Formatage des données, compression, chiffrement (SSL/TLS). | Donnée | JPEG, ASCII, TLS/SSL |
| **5** | **Session** | Établit, maintient et termine les sessions entre applications. | Donnée | NetBIOS, RPC |
| **4** | **Transport** | Assure la transmission de bout en bout (fiable ou rapide). | Segment (TCP) / Datagramme (UDP) | TCP, UDP |
| **3** | **Réseau** | Adressage logique (IP) et acheminement des données (routage) entre réseaux. | Paquet | IP, ICMP |
| **2** | **Liaison** | Contrôle d'accès au média et adressage physique (MAC) sur un réseau local. | Trame | Ethernet, Wi-Fi, Switch |
| **1** | **Physique** | Conversion des données en signaux (électriques, optiques, radio) et transmission des bits. | Bit | Câbles, Hubs, Modems |

---

### Protocol Data Unit (PDU)

Chaque couche possède une **unité spécifique d'encodage des informations** appelée **PDU (Protocol Data Unit)**.

| Couche | PDU |
|--------|-----|
| 7, 6, 5 | Donnée |
| 4 | Segment / Datagramme |
| 3 | Paquet |
| 2 | Trame |
| 1 | Bit |

---

## 4. Principaux protocoles réseau (Modèle TCP/IP)

Le modèle TCP/IP est la mise en œuvre pratique des réseaux modernes, fusionnant souvent les couches du modèle OSI.

| Protocole | Couche OSI | Rôle principal | Ports/Détails |
|:----------|:-----------|:---------------|:--------------|
| **DHCP** | Application (7) | Attribution **automatique** d'une adresse IP. | UDP 67 (serveur), UDP 68 (client). |
| **DNS** | Application (7) | Transformer un **nom de domaine** (URL) en **adresse IP**. | UDP 53 (requêtes), TCP 53 (transferts de zones). |
| **HTTP(S)** | Application (7) | Transfert de **pages Web**. | TCP 80 (HTTP), TCP 443 (HTTPS). |
| **TCP** | Transport (4) | Communication **fiable** (avec accusé de réception). | Connexion orientée. |
| **UDP** | Transport (4) | Communication **rapide** (sans contrôle d'erreur). | Non orienté connexion (Streaming, VoIP). |
| **IP** | Réseau (3) | **Routage** des paquets via les adresses IP. | Protocoles sans port. |
| **ARP** | Liaison (2) | Résolution des adresses IP en adresses MAC. | Protocoles sans port. |

---

## 5. Les topologies réseau

La topologie décrit l'agencement physique ou logique des appareils dans un réseau.

| Topologie | Description | Avantages | Inconvénients | Meilleur Usage |
|:----------|:------------|:----------|:-------------|:---------------|
| **Étoile** | Appareils connectés à un hub/switch central. | Fiable, facile à étendre. | Dépendance au hub central. | Réseaux d'entreprise/domestiques modernes. |
| **Anneau** | Appareils connectés en boucle fermée. | Pas de collision, performance constante. | Une seule panne bloque le réseau. | Réseaux industriels. |
| **Maille (Mesh)**| Chaque appareil connecté à plusieurs autres (redondance). | **Très haute fiabilité**, résistance aux pannes. | Très coûteux et complexe à gérer. | Datacenters, réseaux critiques. |
| **Bus** | Appareils connectés à un câble principal unique. | Faible coût, peu de câbles. | Dépendance totale au câble principal, performances faibles. | Petits réseaux temporaires/tests. |
| **Hybride**| Combinaison de plusieurs topologies (ex: Bus et Étoile).| Très flexible et évolutive. | Complexe à mettre en œuvre. | Grands réseaux d'entreprise complexes. |

---

## 6. Applications et usage pratique : Adressage IP et Subnetting

L'adressage IP (Internet Protocol) et le Subnetting (découpage en sous-réseaux) sont fondamentaux pour l'organisation et l'efficacité d'un réseau.

### IPv4 : Adresses et Masques

- **IPv4** : 32 bits, 4 octets décimaux (0 à 255) séparés par des points.
- **Masque de Sous-Réseau** : Sépare l'adresse IP en deux parties : la **Partie Réseau** (bits à 1) et la **Partie Hôte/Machine** (bits à 0).
- **Notation CIDR** : Remplace le masque décimal par une barre oblique `/` suivie du nombre de bits à 1 (ex: 255.255.255.0 = `/24`).
- **Adresses Privées (Classes B) :** La plage **172.16.0.0 à 172.31.255.255** est réservée pour les réseaux locaux et ne peut pas être routée sur Internet.

### Principe du VLSM (Variable Length Subnet Masking)

Le VLSM est une technique qui consiste à utiliser des masques de sous-réseau de différentes tailles (variables) au sein d'un même réseau principal. Cela permet d'optimiser l'espace d'adressage en allouant à chaque département uniquement le nombre d'adresses nécessaire.

**Règle de base :** Le nombre d'adresses dans une plage doit être une puissance de 2 **supérieure ou égale au nombre d'hôtes souhaité plus 2** (pour l'adresse Réseau et l'adresse de Diffusion).

$$Nb\_Adresses = 2^{Nb\_bits\_Hôtes} \ge (Nb\_Hôtes + 2)$$

---

### Cas Pratique Corrigé : Découpage de Sous-Réseaux pour l'Université

**Réseau Alloué :** **172.16.0.0/20** (Masque : 255.255.240.0)

**Populations à adresser :**
1.  **Informatique** : 280 étudiants
2.  **Sciences** : 125 étudiants
3.  **Administratif** : 60 membres
4.  **Professeurs** : 25 professeurs

#### Étape 1 : Détermination des besoins et des masques (VLSM)

On calcule la puissance de 2 nécessaire (en commençant par le plus grand besoin) :

| Département | Hôtes Nécessaires | $H + 2$ | Puissance de 2 ($2^n$) | $n$ (Bits Hôtes) | Masque | CIDR |
|:------------|:------------------|:--------|:------------------------|:-----------------|:-------|:-----|
| **Informatique** | 280 | 282 | **512** | 9 ($2^9$) | 255.255.254.0 | **/23** |
| **Sciences** | 125 | 127 | **128** | 7 ($2^7$) | 255.255.255.128 | **/25** |
| **Administratif** | 60 | 62 | **64** | 6 ($2^6$) | 255.255.255.192 | **/26** |
| **Professeurs** | 25 | 27 | **32** | 5 ($2^5$) | 255.255.255.224 | **/27** |

#### Étape 2 : Attribution séquentielle des plages

On attribue les plages en séquence, en garantissant qu'il n'y ait pas de chevauchement.

| Département | Hôtes Max | Adresse Réseau (ID) | Masque (CIDR) | Plage d'Adresses Utilisables | Adresse de Diffusion (Broadcast) |
|:------------|:----------|:--------------------|:--------------|:-----------------------------|:---------------------------------|
| **Informatique** | 510 | **172.16.0.0** | **/23** (255.255.254.0)| 172.16.0.1 à 172.16.1.254 | 172.16.1.255 |
| **Sciences** | 126 | **172.16.2.0** | **/25** (255.255.255.128)| 172.16.2.1 à 172.16.2.126 | 172.16.2.127 |
| **Administratif** | 62 | **172.16.2.128** | **/26** (255.255.255.192)| 172.16.2.129 à 172.16.2.190 | 172.16.2.191 |
| **Professeurs** | 30 | **172.16.2.192** | **/27** (255.255.255.224)| 172.16.2.193 à 172.16.2.222 | 172.16.2.223 |

**Conclusion du Cas Pratique :**

Le découpage est optimal. Le réseau parent **172.16.0.0/20** a été utilisé de manière efficace, en ne consommant qu'une petite partie de l'espace ($172.16.0.0$ à $172.16.2.223$). La plage restante ($172.16.2.224$ à $172.16.15.255$) est préservée pour la croissance future de l'université.

---

