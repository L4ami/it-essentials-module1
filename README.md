# Module 1 — IT Essentials : matériel, systèmes d'exploitation et réseau

Rendu complet des 7 travaux pratiques du module IT Essentials, réalisés dans le cadre du Bachelor en informatique du **Geneva Institute of Technology** (Genève).

**Auteur :** Paul Giocanti · **Classe :** E1B · **Date :** 09.09.2026

---

## Sommaire

| TP | Intitulé | Environnement utilisé | Statut |
|----|----------|----------------------|--------|
| [TP1](#tp1--montage--démontage-dun-pc) | Montage / démontage d'un PC | Lenovo ThinkCentre M92p (poste de labo) | Terminé |
| [TP2](#tp2--étude-et-validation-de-compatibilité-dune-configuration-pc) | Étude de compatibilité d'une configuration | PCPartPicker | Terminé |
| [TP3](#tp3--configuration-du-biosuefi--mot-de-passe-et-clear-cmos) | BIOS/UEFI : mot de passe et Clear CMOS | Lenovo ThinkCentre M92p (poste de labo) | Terminé |
| [TP4](#tp4--création-dune-clé-usb-bootable-windows-11-et-ubuntu) | Création de clés USB bootables | Rufus sur Lenovo Legion Pro 5 | Terminé |
| [TP5](#tp5--installation-de-windows-11) | Installation de Windows 11 | VM VMware Workstation | Terminé |
| [TP6](#tp6--installation-dubuntu-desktop) | Installation d'Ubuntu | VM VMware Workstation | Terminé |
| [TP7](#tp7--test-de-connectivité-réseau-ping) | Test de connectivité réseau (ping) | VMware Workstation, mode Pont | Terminé |

**Compétences mises en œuvre :** montage et diagnostic matériel · BIOS/UEFI · virtualisation (VMware Workstation) · installation et configuration de Windows 11 et d'Ubuntu · réseau TCP/IP, DHCP, ICMP, pare-feu · vérification d'intégrité (SHA-256) · documentation technique.

---

# TP1 — Montage / démontage d'un PC

## 1. Objectif

Identifier chaque composant matériel et son rôle, démonter puis remonter une machine en respectant les règles de sécurité, et la laisser fonctionnelle.

## 2. Matériel et environnement

- Machine : Lenovo ThinkCentre M92p, type 2988D6G (numéro de série masqué)
- Outils : tournevis cruciforme / Torx, visseuse électrique
- Sauvegarde des données : machine de labo — prérequis de sauvegarde et accord du propriétaire sans objet
- Accord de démontage signé (machine personnelle) : non applicable

## 3. Règles de sécurité appliquées

- [x] PC hors tension et débranché du secteur
- [x] Batterie retirée / débranchée (portable)
- [ ] Bracelet antistatique porté (protection ESD)
- [x] Aucune pièce forcée, spudger utilisé sur les clips plastiques

> **ESD (décharge électrostatique)** : transfert brutal de l'électricité statique accumulée par le corps humain vers un composant. Quelques dizaines de volts, imperceptibles pour l'utilisateur, suffisent à détruire ou fragiliser les circuits internes — d'où le port du bracelet antistatique.

## 4. Fiche d'identification des composants

| Composant | Rôle | Caractéristique relevée |
|-----------|------|-------------------------|
| CPU | Exécute toutes les instructions des programmes | Intel Core i5-3470 @ 3,20 GHz, 4 cœurs, socket LGA1155 |
| Ventirad | Évacue la chaleur du processeur pour éviter la surchauffe et le bridage | Ventirad aluminium + ventilateur, branché sur CPU_FAN |
| RAM | Mémoire de travail temporaire du processeur, vidée à l'extinction | 4096 Mo détectés (8 Go annoncés), DDR3 |
| Carte mère | Relie physiquement et électriquement tous les composants | Lenovo IS7XM Rev 1.0 / LGA1155 / SFF |
| Stockage | Conserve les données et le système hors tension | HDD WDC WD5000AAKX / 500 Go / SATA |
| GPU | Calcule et génère l'image affichée à l'écran | Aucune carte dédiée, GPU intégré au CPU, sorties VGA et DisplayPort |
| Alimentation (PSU) | Convertit le 230 V du secteur en 12 V / 5 V / 3,3 V | Liteon PS-4241-01, 240 W max, 80 PLUS |
| Boîtier | Enveloppe qui accueille et protège les composants | SFF (Small Form Factor), ThinkCentre M92p |
| Carte réseau | Connexion de la machine au réseau, filaire ou sans fil | Ethernet intégré + carte Wi-Fi Intel Centrino Advanced-N 6205 (carte fille PCI) |

## 5. Photos

Avant ouverture (machine fermée)
![Avant ouverture](https://hackmd.io/_uploads/Bke9MRAOfx.jpg)

Boîtier ouvert, avant démontage
![Boîtier ouvert](https://hackmd.io/_uploads/H1TezA0dzl.jpg)

Barrette de RAM
![RAM](https://hackmd.io/_uploads/BkXEfAROze.jpg)

CPU
![CPU](https://hackmd.io/_uploads/SJrbmCAOzl.jpg)

Disque dur
![HDD](https://hackmd.io/_uploads/r1pr700OMe.jpg)

Bloc d'alimentation
![Alimentation](https://hackmd.io/_uploads/Hk27EA0ufl.jpg)

Ventirad du processeur
![Ventirad](https://hackmd.io/_uploads/Bk6rVCCufl.jpg)

Carte mère (entièrement débranchée mais non déposée : une vis était grippée, retrait non forcé pour ne pas endommager le matériel)
![Carte mère](https://hackmd.io/_uploads/HkfEr0C_fg.jpg)

Écran de POST après remontage
![POST](https://hackmd.io/_uploads/r190F0R_Me.png)

> Partie B non réalisée : dispensée par le formateur.

## 6. Conclusion

Le démontage et le remontage ont été menés à terme : la machine passe le POST et redémarre normalement. Le point clé a été de photographier l'intérieur avant toute manipulation, ce qui a permis de recâbler sans hésitation, et de lire les erreurs du POST plutôt que de deviner — les deux erreurs rencontrées (ventilateur et RAM) ont directement désigné ce qui restait à corriger.

---

# TP2 — Étude et validation de compatibilité d'une configuration PC

## 1. Objectif

Proposer une configuration cohérente, compatible et dans le budget pour un usage cible donné, et justifier chaque choix.

## 2. Cahier des charges client

- Budget : 1500 CHF
- Usage cible : gaming en 1440p
- Contraintes : configuration évolutive, sans overclocking

## 3. Fiche de configuration

| Composant | Modèle choisi | Prix (CHF) | Caractéristiques clés |
|-----------|---------------|------------|------------------------|
| CPU | Intel Core i5-12600KF | 170 | LGA1700 / 10 cœurs (6P + 4E) / 125 W base — 150 W turbo |
| Carte mère | Gigabyte B760 Gaming X AX (ATX) | 150 | LGA1700 / ATX / DDR5 |
| RAM | Kingston FURY Beast 32 Go (2 × 16 Go) | 110 | DDR5 / 32 Go / 5600 MHz CL36 |
| Stockage | Samsung 990 EVO 1 To M.2 2280 | 90 | NVMe PCIe 4.0 ×4 / 1 To |
| GPU | Palit RTX 5060 Ti White OC 16 Go GDDR7 | 600 | ≈ 250 mm / 1 × PCIe 8 broches |
| Alimentation | Corsair RM650e — 650 W 80+ Gold ATX | 95 | 650 W / 24 broches + EPS 8 + PCIe |
| Boîtier | Montech XR Mid Tower | 65 | ATX / longueur GPU max ≥ 330 mm |
| Refroidissement | Thermalright Peerless Assassin 120 SE | 45 | LGA1700 / ≈ 220 W |
| **TOTAL** | | **1355 CHF** | Marge sur budget : 295 CHF (périphériques, accessoires) |

## 4. Tableau de vérification de compatibilité

| Point de contrôle | Élément A | Élément B | Compatible ? | Justification |
|---|---|---|---|---|
| Socket CPU ↔ carte mère | i5-12600KF — LGA1700 | B760 Gaming X AX — LGA1700 | ☑ | Sockets identiques. Un CPU LGA1700 n'entre physiquement pas dans un socket AM5 ou LGA1200. |
| Type de RAM (DDR4/DDR5) | Kingston FURY Beast — DDR5 | Carte mère version DDR5 | ☑ | Le socket LGA1700 existe en cartes DDR4 **et** DDR5 : détrompeurs différents, non interchangeables. |
| Fréquence RAM supportée | DDR5-5600 CL36 | Chipset B760 et contrôleur mémoire du CPU | ☑ | Une fréquence non supportée tournerait sous sa vitesse nominale, voire ne serait pas reconnue. |
| Format carte mère ↔ boîtier | Carte mère ATX | Montech XR — Mid Tower ATX | ☑ | Entraxes de fixation et panneau d'E/S normalisés ATX. |
| Longueur GPU ↔ boîtier | RTX 5060 Ti — ≈ 250 mm | Dégagement GPU ≥ 330 mm | ☑ | Marge de 80 mm. |
| Connecteurs d'alimentation | RM650e : 24 broches + EPS 8 + PCIe | Carte mère (24 + 8) et GPU (1 × PCIe 8) | ☑ | Tous les connecteurs requis sont présents, au format ATX comme le boîtier. |
| Interface stockage (M.2 / SATA) | SSD NVMe M.2 2280 PCIe 4.0 ×4 | Port M.2 PCIe 4.0 de la carte mère | ☑ | Le M.2 passe par le bus PCIe, bien plus rapide qu'un raccordement SATA. |
| Socket supporté par le ventirad | Peerless Assassin 120 SE — LGA1700, ≈ 220 W, hauteur 155 mm | i5-12600KF — 150 W en pointe · hauteur max du boîtier ≥ 165 mm | ☑ | Double vérification : compatibilité de socket **et** hauteur sous le panneau latéral. |

## 5. Calcul du TDP et marge d'alimentation

| Composant | Consommation estimée |
|---|---|
| CPU (PL2, turbo maximal) | 150 W |
| GPU (TGP constructeur) | 180 W |
| Autres (carte mère, RAM, stockage, ventilateurs) | 60 W |
| **Total estimé** | **390 W** |
| **Alimentation choisie** | **650 W** |
| **Marge** | **+67 %** (650 / 390 = 1,67×) |

> Règle appliquée : viser une alimentation d'environ 1,5× la consommation totale estimée, pour couvrir les pics et le rendement.

Le facteur de 1,67× couvre trois besoins :

1. **Les pics transitoires** de consommation, très brefs, que les cartes graphiques modernes génèrent et qui dépassent largement leur consommation moyenne.
2. **Le rendement**, optimal autour de 50 à 60 % de charge sur une alimentation 80 PLUS Gold : à 390 W sur 650 W, la configuration tourne à 60 %.
3. **L'évolutivité**, avec 260 W de réserve pour un futur changement de carte graphique sans changer l'alimentation.

## 6. Argumentaire

Le client joue en 1440p avec 1500 CHF : la carte graphique reçoit donc 40 % du budget, car c'est elle qui fixe les images par seconde. Ses 16 Go de VRAM évitent d'être bridé par les textures des jeux récents. Le i5-12600KF suffit à l'alimenter sans goulot d'étranglement, et son suffixe F économise le GPU intégré, inutile ici. Le chipset B760 remplace le Z790 puisque l'overclocking est exclu du cahier des charges. Les 32 Go en deux barrettes activent le double canal et donnent de la marge face aux jeux et aux applications de fond. L'alimentation passe en 650 W au format ATX : la SFX initiale n'était pas au format du boîtier, et 750 W était surdimensionné pour 390 W estimés. Enfin, le ventirad à air remplace le watercooling 360 mm, largement surdimensionné pour un CPU de 150 W et moins fiable à cause de sa pompe.

## 7. Captures

Configuration complète sur PCPartPicker, avec le contrôle de compatibilité visible
![PCPartPicker 1](https://hackmd.io/_uploads/HJvuha0dfg.png)
![PCPartPicker 2](https://hackmd.io/_uploads/rJNonaA_zl.png)
![PCPartPicker 3](https://hackmd.io/_uploads/SJFypaRdMx.png)

---

# TP3 — Configuration du BIOS/UEFI : mot de passe et Clear CMOS

## 1. Objectif

Naviguer dans le BIOS/UEFI, définir puis supprimer un mot de passe superviseur, et réaliser un Clear CMOS physique.

## 2. Matériel et environnement

- Machine : Lenovo ThinkCentre M92p, type 2988D6G (numéro de série masqué)
- Touche d'accès au BIOS : F1
- Méthode de Clear CMOS disponible : retrait de la pile / cavalier CLRTC

## 3. Règles de sécurité appliquées

- [x] PC hors tension et débranché avant ouverture du boîtier
- [ ] Bracelet antistatique porté
- [x] Aucune manipulation forcée sur la carte mère

## 4. Étapes réalisées

### Étape 1 — Accès au BIOS/UEFI

Écran d'accueil du BIOS, version du firmware visible
![BIOS](https://hackmd.io/_uploads/BkW7LARuMg.jpg)

### Étape 2 — Date/heure et ordre de démarrage

Date et heure réglées : 09.09.2026, 11h30
![Date/heure](https://hackmd.io/_uploads/BkN3LCCdGe.jpg)

Ordre de démarrage modifié
![Boot order](https://hackmd.io/_uploads/B1eID0Cufg.jpg)

### Étape 3 — Mot de passe superviseur

Menu Security, mot de passe au statut « Set »
![Security](https://hackmd.io/_uploads/r1DiPARdzx.jpg)

Invite de mot de passe au redémarrage
![Invite mot de passe](https://hackmd.io/_uploads/Hyo1_AA_Ge.jpg)

### Étape 4 — Clear CMOS

- Méthode utilisée : retrait manuel de la pile
- Durée de retrait : 5 minutes

Emplacement de la pile CMOS
![Emplacement pile](https://hackmd.io/_uploads/ByjUc0RuMg.png)

Pile retirée
![Pile retirée](https://hackmd.io/_uploads/SyHt9AAuMg.jpg)

### Étape 5 — Vérification

BIOS après Clear CMOS
![Après Clear CMOS](https://hackmd.io/_uploads/rJEw6ARuMl.jpg)

Date et heure réinitialisées
![Date réinitialisée](https://hackmd.io/_uploads/H1OaTA0uzx.jpg)

## 5. Constat avant / après

| Réglage | Avant Clear CMOS | Après Clear CMOS |
|---------|------------------|------------------|
| Mot de passe superviseur | Défini | **Toujours défini** |
| Date / heure | Défini | Réinitialisé |
| Ordre de démarrage | Défini | Réinitialisé |

## 6. Problème rencontré et solution

| Problème | Cause identifiée | Solution appliquée |
|---|---|---|
| Mot de passe toujours demandé après retrait de la pile CMOS | Sur ThinkCentre, le mot de passe administrateur est stocké dans une puce dédiée, séparée de la mémoire CMOS alimentée par la pile. Le retrait de la pile efface les réglages (date, heure, boot) mais pas ce mot de passe. | Constat documenté. Le mot de passe a été retiré manuellement depuis le BIOS (champs laissés vides) plutôt que par Clear CMOS. Le cavalier RTCRST, identifié comme méthode alternative, n'a pas été testé sur ce matériel de l'établissement. |

## 7. Conclusion

Les quatre volets ont été réalisés : navigation BIOS, date/heure, séquence de démarrage et mot de passe. Le résultat marquant reste que le Clear CMOS a bien réinitialisé les réglages, mais pas le mot de passe administrateur, stocké à part sur ce matériel professionnel — une différence concrète avec un PC grand public, où retirer la pile suffit généralement à tout effacer.

---

# TP4 — Création d'une clé USB bootable (Windows 11 et Ubuntu)

## 1. Objectif

Préparer les deux supports d'installation nécessaires aux TP5 et TP6, en GPT/UEFI, à partir d'ISO vérifiées.

## 2. Matériel et environnement

- Clé USB n°1 : 128 Go — Windows 11
- Clé USB n°2 : 32 Go — Ubuntu
- Outil utilisé : Rufus
- Source des ISO : liens SwissTransfer du formateur et sites officiels Microsoft / Ubuntu

## 3. Vérification d'intégrité des ISO (checksum)

```powershell
Get-FileHash .\Win11.iso -Algorithm SHA256
Get-FileHash .\ubuntu-24.04.2-desktop-amd64.iso -Algorithm SHA256
```

| ISO | Hash calculé | Hash officiel | Concordance |
|-----|--------------|---------------|-------------|
| Windows 11 Pro | B73AA55DB50D2AD348F61C6537DA05C0D6DED78A143763454E977BE85B444119 | Aucun disponible (source SwissTransfer) | Sans objet |
| Ubuntu Desktop | 601E30FBF5D97759367C632E2C33630665039B7E2158FD068403DA3CCF1BDA1F | Page SHA256SUMS officielle | ✅ Identique |

Résultat de `Get-FileHash` pour les deux ISO
![Get-FileHash](https://hackmd.io/_uploads/ryz8LkyYfl.png)

> **Pourquoi vérifier le checksum** : s'assurer que le fichier n'a pas été corrompu pendant le téléchargement et qu'il n'a pas été altéré — intégrité et authenticité du support d'installation.

## 4. Création des clés

### Clé Windows 11

- Schéma de partition : **GPT**
- Système cible : **UEFI (non CSM)**
- Système de fichiers : NTFS (imposé automatiquement, l'ISO contenant un fichier > 4 Go incompatible avec FAT32)

Paramètres Rufus avant lancement
![Rufus Windows](https://hackmd.io/_uploads/BkVKtyJKGe.png)

Fin de création
![Rufus prêt](https://hackmd.io/_uploads/HJVPf4ktfx.jpg)

### Clé Ubuntu

- Schéma de partition : **GPT**
- Système cible : **UEFI (non CSM)**

Paramètres Rufus avant lancement
![Rufus Ubuntu](https://hackmd.io/_uploads/rJC3xVyKMl.png)

Fin de création
![Rufus Ubuntu fin](https://hackmd.io/_uploads/Hy4k-Vytfe.png)

## 5. Test de démarrage

Touche du menu de boot sur la machine de test : F12

Menu de boot avec la clé détectée en mode UEFI
![Menu de boot](https://hackmd.io/_uploads/H13GG-ytGe.jpg)

Écran d'installation Windows 11 atteint
![Windows 11](https://hackmd.io/_uploads/SJ9bMZyKMl.jpg)

Écran GRUB « Try or Install Ubuntu » atteint
![GRUB Ubuntu](https://hackmd.io/_uploads/B1-EGbkKzx.jpg)

## 6. Problèmes rencontrés et solutions

| Problème | Cause identifiée | Solution appliquée |
|---|---|---|
| Impossible de vérifier l'intégrité de l'ISO Windows | L'ISO provient du lien SwissTransfer du formateur, source pour laquelle aucun hash de référence n'est publié | Hash calculé et documenté, mais comparaison impossible. La vérification complète a été réalisée sur l'ISO Ubuntu, dont le SHA256SUMS est publié officiellement. |
| Avertissement Rufus : « Bootloader UEFI révoqué détecté » | L'ISO Windows contient un bootloader antérieur à la mise à jour de sécurité Microsoft, signalé lorsque Secure Boot est actif | Avertissement analysé puis validé : l'installation étant réalisée en machine virtuelle, la révocation n'a pas d'impact pratique, et la source de l'ISO est fiable. |
| Options de contournement des prérequis proposées par Rufus | Rufus propose de supprimer les exigences RAM, Secure Boot et TPM 2.0 | Option volontairement décochée : le TP5 exige de respecter et de vérifier ces prérequis. |
| Version d'Ubuntu différente du guide du formateur | Téléchargement de la 26.04.1 LTS au lieu de la 24.04.2 LTS référencée | Écart documenté ; la procédure d'installation reste identique dans ses grandes lignes. |

## 7. Conclusion

Les supports d'installation ont été préparés en GPT/UEFI et le démarrage de la clé Ubuntu a été validé jusqu'à l'écran d'installation. L'apport principal de ce TP est d'avoir montré la limite d'un checksum : le calcul ne sert à rien sans une référence officielle à laquelle le comparer, ce qui distingue nettement une ISO téléchargée depuis la source constructeur d'une ISO transmise par un tiers, même de confiance. L'avertissement de bootloader révoqué a par ailleurs été l'occasion de comprendre le lien entre Secure Boot et la signature des composants de démarrage, plutôt que de le valider sans le lire.

---

# TP5 — Installation de Windows 11

> **Remarque :** cette VM ayant été créée avant le démarrage formel du TP, les captures du partitionnement et du choix d'installation personnalisée n'ont pas pu être conservées. Les captures de configuration post-installation (réseau, pilotes, nom du poste) sont en revanche complètes.

## 1. Objectif

Déployer un poste Windows 11 dans les règles de l'art : partitionnement GPT/UEFI, installation personnalisée, puis configuration post-installation (pilotes, réseau, nom du poste).

## 2. Environnement et paramètres de la VM

| Paramètre | Valeur |
|-----------|--------|
| RAM allouée | 4 Go |
| Disque virtuel | 64 Go |
| Processeurs / cœurs | 2 |
| Firmware | UEFI + Secure Boot |
| TPM virtuel | Nécessite le chiffrement de la VM |
| Mode réseau | Pont (Bridged) |

Paramètres de la VM montrant UEFI, Secure Boot et le TPM
![Paramètres VM 1](https://hackmd.io/_uploads/HkZDse1Kfx.png)
![Paramètres VM 2](https://hackmd.io/_uploads/Skhdne1Yfg.png)

> Windows 11 exige TPM 2.0 et Secure Boot. Sans eux, l'installateur affiche « Ce PC ne peut pas exécuter Windows 11 ».

## 3. Étapes réalisées

### Étape 1 — Partitionnement

Type d'installation : **personnalisée** (table rase, pas de mise à niveau).

> Après une installation en UEFI, Windows crée automatiquement : partition EFI, partition MSR, partition Windows et partition de récupération.

### Étape 2 — Configuration initiale (OOBE)

Type de compte : **local** (consigne du formateur).

Bureau Windows 11 final
![Bureau Windows](https://hackmd.io/_uploads/SJG-beyFMg.jpg)

### Étape 3 — Pilotes

VMware Tools installés — Gestionnaire de périphériques sans point d'exclamation
![Gestionnaire de périphériques](https://hackmd.io/_uploads/S1G8_xytze.png)

### Étape 4 — Réseau et nom du poste

Nom du poste défini
![Nom du poste](https://hackmd.io/_uploads/rk7Ucl1KGl.png)

Résultat de `winver` (version et build)
![winver](https://hackmd.io/_uploads/BJXuvektMx.jpg)

Résultat de `ipconfig` — adresse IPv4 relevée : 192.168.190.132
![ipconfig](https://hackmd.io/_uploads/B1wwae1Yze.png)

### Étape 5 — Windows Update

![Windows Update](https://hackmd.io/_uploads/B1sm1ZJFGl.png)

## 4. Problèmes rencontrés et solutions

| Problème | Cause identifiée | Solution appliquée |
|---|---|---|
| Captures du partitionnement manquantes | La VM avait été créée et installée avant le démarrage formel du TP | Documentation à partir de la configuration existante, remarque explicative ajoutée en tête de section |
| Impossible de localiser UEFI/Secure Boot dans l'onglet « Matériel » de la VM | Ces réglages se trouvent dans Options → Avancé, sous « Type de microprogramme » | Localisation trouvée dans le bon onglet, capture montrant UEFI actif et la présence du TPM |
| Case « pilotes constructeur via numéro de série » non applicable | Cette étape concerne une installation sur machine physique, pas une VM | Remplacée par VMware Tools, vérifié via le Gestionnaire de périphériques |

## 5. Conclusion

L'installation de Windows 11 en VM a été menée avec succès, avec les prérequis TPM et UEFI vérifiés et confirmés actifs. La principale limite de ce TP est documentaire : la VM ayant été créée avant le début formel de l'exercice, les captures du partitionnement n'ont pas pu être conservées, compensées par une documentation complète de la configuration post-installation. Ce TP a surtout clarifié une distinction utile : en environnement virtuel, VMware Tools remplace entièrement l'étape de recherche manuelle de pilotes constructeur nécessaire sur une machine physique.

---

# TP6 — Installation d'Ubuntu Desktop

## 1. Objectif

Déployer un poste Ubuntu Desktop, créer un utilisateur non-root, mettre le système à jour et relever l'adresse IP.

## 2. Environnement et paramètres de la VM

Version d'Ubuntu : `ubuntu-26.04.1-desktop-amd64`

| Paramètre | Valeur |
|-----------|--------|
| RAM allouée | 8 Go |
| Disque virtuel | 25 Go |
| Firmware | UEFI |
| Mode réseau | Pont (Bridged) |

## 3. Étapes réalisées

### Étape 1 — Démarrage sur le support

Écran « Try or Install Ubuntu »
![Try or Install Ubuntu](https://hackmd.io/_uploads/H1-LV4yFGg.png)

### Étape 2 — Installation

Type d'installation : **Normale**
![Type d'installation](https://hackmd.io/_uploads/ByBRNNyFMl.png)

### Étape 3 — Création du compte utilisateur

Utilisateur non-root créé.
![Création du compte](https://hackmd.io/_uploads/BJNZBNyYfx.png)

> **Pourquoi un utilisateur non-root** : sous Linux, on ne travaille jamais en root au quotidien. Les commandes privilégiées passent par `sudo`, ce qui limite les dégâts d'une fausse manipulation et laisse une trace dans les journaux.

### Étape 4 — Bureau et VMware Tools

Bureau Ubuntu après premier démarrage
![Bureau Ubuntu](https://hackmd.io/_uploads/SyrZ84kFzg.png)

`open-vm-tools-desktop` installé (copier-coller et redimensionnement de l'écran)
![open-vm-tools](https://hackmd.io/_uploads/rkGD3dktze.png)

### Étape 5 — Mise à jour du système

```bash
sudo apt update
sudo apt upgrade -y
```

![apt upgrade](https://hackmd.io/_uploads/ByQFh_1FGe.png)

### Étape 6 — Relevé de l'adresse IP

```bash
ip a
```

- Interface active : `ens33`
- Adresse IPv4 relevée : 192.168.1.109

![ip a](https://hackmd.io/_uploads/SyyfAuyYGx.png)

### Étape 7 — Pilotes

Sans objet : installation réalisée en VM, les pilotes étant fournis par `open-vm-tools-desktop` installé à l'étape 4.

## 4. Problèmes rencontrés et solutions

| Problème | Cause identifiée | Solution appliquée |
|---|---|---|
| Aucune connexion internet après l'installation | L'option « Do not connect to the internet » avait été sélectionnée pendant l'installation | Activation de la carte réseau, puis `sudo nmcli device connect ens33` |
| Adresse en 169.254.x.x au lieu d'une adresse du réseau local | Adresse d'auto-configuration (APIPA) attribuée faute de réponse du serveur DHCP | Passage de la carte réseau VMware du mode NAT au mode Pont, puis `sudo nmcli con mod netplan-ens33 ipv4.method auto` et `sudo nmcli con up netplan-ens33`. Adresse 192.168.1.109 obtenue de la box. |
| `dhclient: command not found` | Ubuntu 26.04 n'installe plus `dhclient` par défaut, la gestion réseau passant par NetworkManager | Utilisation de `nmcli` à la place |

## 5. Conclusion

L'installation d'Ubuntu s'est révélée plus rapide que celle de Windows 11, sans exigence de TPM ni de Secure Boot, et avec l'ensemble des pilotes déjà présents dans le noyau. La difficulté s'est concentrée sur la configuration réseau : le choix hors ligne fait pendant l'installation a entraîné un échec DHCP, reconnaissable à l'adresse en 169.254.x.x, résolu par le passage en mode Pont. Cette panne aura été l'occasion de manipuler `nmcli` et de vérifier concrètement la différence entre les modes NAT et Pont.

---

# TP7 — Test de connectivité réseau (ping)

## 1. Objectif

Configurer le mode réseau des machines, relever leurs adresses IP, tester le ping entre les VM et la machine physique dans les deux sens, puis diagnostiquer et corriger les échecs.

## 2. Machines impliquées

| Machine | Type | OS | Mode réseau | Adresse IPv4 | Masque |
|---------|------|-----|-------------|--------------|--------|
| Legion Pro 5 | Physique | Windows 11 | Wi-Fi | 192.168.1.120 | 255.255.255.0 |
| VM 1 | VMware Workstation | Windows 11 | Pont (Bridged) | 192.168.1.110 | 255.255.255.0 |
| VM 2 | VMware Workstation | Ubuntu | Pont (Bridged) | 192.168.1.109 | 255.255.255.0 |

Passerelle par défaut commune : 192.168.1.1

Paramètres réseau des VM en mode Pont
![Mode Pont 1](https://hackmd.io/_uploads/ryBMbF1tGx.png)
![Mode Pont 2](https://hackmd.io/_uploads/ryjJMtJFzg.png)

`ipconfig` sur la VM Windows et sur le poste physique
![ipconfig](https://hackmd.io/_uploads/B1_Q-Kktzg.png)

`ip a` sur la VM Ubuntu — interface ens33, 192.168.1.109/24
![ip a Ubuntu](https://hackmd.io/_uploads/r17eUGetfl.png)

Les trois adresses appartiennent au même sous-réseau 192.168.1.x, avec le même masque. Une adresse en 169.254.x.x aurait signalé un échec d'attribution DHCP.

## 3. Test préalable : joignabilité de la passerelle

| Depuis | Vers | Résultat |
|--------|------|----------|
| VM Windows | 192.168.1.1 | 4/4 reçus, 0 % de perte |
| VM Ubuntu | 192.168.1.1 | 4/4 reçus, 0 % de perte |

![Ping passerelle 1](https://hackmd.io/_uploads/rymd8Mgtfl.png)
![Ping passerelle 2](https://hackmd.io/_uploads/ryidLMeFGg.png)

Les deux VM joignent la box : la couche réseau et le mode Pont fonctionnent. Tout échec constaté ensuite ne peut donc pas venir de la configuration réseau.

## 4. Matrice des tests de ping

| Depuis → Vers | Résultat initial | Après correction |
|---------------|------------------|------------------|
| VM Windows → VM Ubuntu | 4/4 reçus | déjà fonctionnel |
| VM Ubuntu → VM Windows | 0/4, 100 % de perte | 4/4 reçus, ttl=128 |
| VM Ubuntu → poste physique | 0/4, 100 % de perte | 4/4 reçus, ttl=128 |
| Poste physique → VM Ubuntu | 4/4 reçus | déjà fonctionnel |

Échecs avant correction
![Échec 1](https://hackmd.io/_uploads/Bkl-vGlKGe.png)
![Échec 2](https://hackmd.io/_uploads/HypGwGlFMl.png)

Pings réussis après correction
![Succès 1](https://hackmd.io/_uploads/HkdIDfeFMl.png)
![Succès 2](https://hackmd.io/_uploads/BJpLwzlKfg.png)

> **Remarque sur le TTL** : la valeur reçue est de 128 depuis une cible Windows et de 64 depuis une cible Linux, c'est-à-dire la valeur initiale de chaque système. Aucun routeur n'a donc été traversé, ce qui confirme que les machines communiquent directement sur le même réseau local.

## 5. Diagnostic

### Distinguer deux messages d'erreur

| Message | Signification |
|---------|---------------|
| Destination Host Unreachable | La résolution ARP a échoué, la cible est introuvable sur le réseau |
| 100 % de perte sans message | La cible est jointe mais ne répond pas : filtrage |

Vérification de la table ARP côté Ubuntu avec `ip neigh` : l'entrée 192.168.1.110 apparaît à l'état REACHABLE avec son adresse MAC résolue. La cible est donc bien localisée sur le réseau et reçoit les paquets ; son silence relève d'un filtrage et non d'un problème de liaison.

![ip neigh](https://hackmd.io/_uploads/HyQnvfxYMl.png)

### Cas 1 — VM Windows : pare-feu Windows Defender

Le ping passait de Windows vers Ubuntu mais pas dans l'autre sens. Le lien fonctionnant dans un sens, le blocage venait de la cible.

**Cause :** le pare-feu Windows Defender rejette par défaut les demandes d'écho ICMPv4 entrantes.

**Correction :** console `wf.msc`, Règles de trafic entrant, activation de la règle « Partage de fichiers et d'imprimantes (Demande d'écho — Trafic entrant ICMPv4) ». Cette règle existe en trois versions, une par profil réseau (Domaine, Privé, Public) ; seul le profil actif s'applique.

![Règle avant](https://hackmd.io/_uploads/B1JRDzxFMx.png)
![Règle après](https://hackmd.io/_uploads/SJZlOGgFMe.png)
![Ping réussi](https://hackmd.io/_uploads/H1JBOfeKMe.png)

### Cas 2 — Poste physique : deux pare-feu superposés

Même symptôme, mais l'activation de la même règle Windows n'a produit aucun effet.

**Cause :** Bitdefender Total Security installe son propre pare-feu, qui se substitue à celui de Windows. Les règles de `wf.msc` restent visibles et modifiables mais ne sont plus appliquées. Son mode furtif (Stealth Mode) était activé sur la carte Wi-Fi, rendant la machine volontairement invisible en ignorant les requêtes ICMP entrantes. Il était en revanche désactivé sur les cartes VMware, ce qui explique que le poste répondait aux VM sur les réseaux virtuels mais pas via le Wi-Fi.

**Correction :** Bitdefender → Protection → Pare-feu → Settings → Stealth Mode, désactivation sur la carte Wi-Fi.

Le Wi-Fi est classé en « Dynamic », contrairement aux cartes VMware en « Home/Office »
![Network Adapters](https://hackmd.io/_uploads/rJ8wdMlKGg.png)

Mode furtif activé sur la carte Wi-Fi
![Stealth Mode 1](https://hackmd.io/_uploads/HJ59uzgFfl.png)
![Stealth Mode 2](https://hackmd.io/_uploads/B1rC_MgKGl.png)

Ping réussi après désactivation
![Ping final](https://hackmd.io/_uploads/SygkFGeYGl.png)

Le mode furtif a été réactivé après le test, la configuration initiale du poste étant restaurée.

## 6. Démarche de diagnostic appliquée

1. Les machines sont-elles dans le même sous-réseau ? (`ipconfig` / `ip a`)
2. Le mode réseau des VM est-il bien en Pont et non en NAT ?
3. Chaque machine joint-elle la passerelle ? Cela isole un défaut de liaison.
4. La cible est-elle résolue en ARP ? (`ip neigh`)
5. Le ping ne passe-t-il que dans un sens ? Le blocage vient alors de la cible : filtrage.
6. La correction reste-t-elle sans effet ? Vérifier qu'un autre pare-feu ne s'est pas substitué à celui du système.

## 7. Conclusion

Ce TP montre que le ping ne se lit pas comme un simple succès ou échec : le message obtenu oriente le diagnostic. Une absence totale de réponse alors que l'adresse MAC de la cible est résolue désigne un filtrage, pas un défaut de réseau.

Il montre surtout l'intérêt de tester dans les deux sens : c'est l'asymétrie du résultat qui a permis d'écarter la couche réseau et de désigner la cible comme responsable.

Enfin, le cas du poste physique a mis en évidence un piège concret : lorsqu'une suite de sécurité tierce prend le relais du pare-feu système, la configuration modifiée n'est plus celle qui est appliquée. Un même symptôme peut donc avoir deux causes différentes selon la machine, et une correction sans effet est en soi une information de diagnostic.

---

# Annexe — Conditions de réalisation

| Élément | Détail |
|---------|--------|
| Machine hôte utilisée | Lenovo Legion Pro 5 16IRX10 — Intel Core i9-14900HX, 32 Go de RAM, 2 SSD NVMe (WD PC SN8000S 1 To + Samsung 990 PRO 1 To), Windows 11 |
| Hyperviseur | VMware Workstation Pro |
| TP réalisés en autonomie | TP2, TP4, TP5, TP6, TP7 |
| TP réalisés en salle de labo | TP1, TP3 (Lenovo ThinkCentre M92p) |
| Durée totale | 7 à 10 heures |
