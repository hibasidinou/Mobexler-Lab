# 📱 TP Sécurité Mobile — Mobexler Lab

> Lab de sécurité Android réalisé sous **Mobexler** (VM Kali-based) avec analyse d'applications mobiles via ADB et outils offensifs intégrés.

---

## 🖥️ Environnement

| Composant | Détail |
|---|---|
| VM Attaquant | Mobexler (VirtualBox) |
| OS | Kali Linux (base Mobexler) |
| Cible Android | Genymotion / Device physique |
| Outil ADB | Android Debug Bridge |
| Réseau NAT | 192.168.208.133/24 |

---

## ✅ Étape 1 — Import & Premier démarrage

- Import de l'OVA Mobexler dans VirtualBox
- Login : `mobexler` / `mobexler`
- Accès au bureau et ouverture du terminal

<img width="1713" height="881" alt="image" src="https://github.com/user-attachments/assets/f478060c-99e6-4853-842a-29d0832b8233" />


---

## ✅ Étape 2 — Vérification réseau

### `ip a`

```
ens33 : 192.168.208.133/24  → Interface NAT (Internet)
ens34 : (Host-Only)
docker0 : 172.17.0.1/16
```

<img width="960" height="422" alt="ip a" src="https://github.com/user-attachments/assets/ece7f7af-3c00-43a3-890f-927dfdf28b07" />


### `ip route`

```
default via 192.168.208.2 dev ens33   → Route par défaut OK
```

### Tests de connectivité

```bash
ping -c 2 8.8.8.8       # ✅ 0% packet loss
ping -c 2 google.com    # ✅ DNS résolu + 0% packet loss
```

<img width="891" height="466" alt="ip_route_and_ping" src="https://github.com/user-attachments/assets/48102ae4-afa1-4dab-8985-764648aa3ef4" />


---

## ✅ Étape 3 — Snapshot baseline

Snapshot créé dans VirtualBox avant toute manipulation :

- **Nom :** `CLEAN_BASELINE_TP1`
- **Description :** Import OK, NAT OK, boot OK, prêt ADB

<img width="813" height="607" alt="SNAPSHOT" src="https://github.com/user-attachments/assets/a26b23c3-8ad3-4d8a-b8f8-c1bbca75b2e7" />


---

## ✅ Étape 4 — Connexion cible Android

### Option choisie : Genymotion / USB

```bash
# Genymotion (réseau)
adb connect <IP_DEVICE>:5555

# OU téléphone USB
adb devices
```

Résultat attendu :

```
List of devices attached
<ID>    device
```

<img width="477" height="193" alt="phone_detected" src="https://github.com/user-attachments/assets/ec36a289-b5de-4809-b83e-3a6371ba673d" />


---

## 📂 Structure du dépôt

```
.
├── README.md
└── screenshots/
    ├── 01_bureau_mobexler.png
    ├── 02_ip_a.png
    ├── 03_ip_route.png
    ├── 04_ping_tests.png
    ├── 05_snapshot_virtualbox.png
    └── 06_adb_devices.png
```

---

## 🔧 Outils utilisés

- [Mobexler](https://mobexler.com/) — VM de pentest Android
- [ADB](https://developer.android.com/tools/adb) — Android Debug Bridge


