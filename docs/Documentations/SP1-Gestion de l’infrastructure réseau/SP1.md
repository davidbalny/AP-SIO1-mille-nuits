# Calcul des besoins en hôtes et plan d’adressage IP

## Calcul des besoins en hôtes (avec marge)

Une marge de **20 %** est appliquée afin d’anticiper les évolutions futures (nouveaux postes, équipements supplémentaires).

### 🔹 Administratif
- 46 PC + 6 imprimantes = **52 hôtes**
- Marge 20 % → 52 × 1,2 = **62,4** → **63 hôtes**

### 🔹 Autres
- 90 PC + 10 imprimantes = **100 hôtes**
- Marge 20 % → 100 × 1,2 = **120 hôtes**

### 🔹 Production
- 100 PC + 10 imprimantes = **110 hôtes**
- Marge 20 % → 110 × 1,2 = **132 hôtes**

### 🔹 Logistique
- 25 PC + 5 imprimantes = **30 hôtes**
- Marge 20 % → 30 × 1,2 = **36 hôtes**

### 🔹 Ventes / Études
- 40 PC + 8 imprimantes = **48 hôtes**
- Marge 20 % → 48 × 1,2 = **57,6** → **58 hôtes**

### 🔹 Serveurs
- Réseau imposé : **172.16.5X.0/24**
- **254 hôtes utilisables**  
- Aucune marge supplémentaire demandée

---

## Détermination des masques nécessaires

| Sous-réseau        | Hôtes nécessaires | Masque | Hôtes possibles |
|--------------------|------------------|--------|-----------------|
| Production         | 132              | /24    | 254             |
| Autres             | 120              | /25    | 126             |
| Administratif      | 63               | /25    | 126             |
| Ventes / Études    | 58               | /26    | 62              |
| Logistique         | 36               | /26    | 62              |
| Serveurs           | —                | /24    | 254             |

---

## Attribution VLSM (du plus grand au plus petit)

- **Réseau de base** : `172.40.0.0/16`

### 🟦 Production
- Adresse réseau : `172.40.0.0/24`
- Masque : `255.255.255.0`
- Plage hôtes : `172.40.0.1 → 172.40.0.254`
- Adresse de diffusion : `172.40.0.255`
- Passerelle : `172.40.0.254`

---

### 🟦 Autres
- Adresse réseau : `172.40.1.0/25`
- Masque : `255.255.255.128`
- Plage hôtes : `172.40.1.1 → 172.40.1.126`
- Adresse de diffusion : `172.40.1.127`
- Passerelle : `172.40.1.126`

---

### 🟦 Administratif
- Adresse réseau : `172.40.1.128/25`
- Masque : `255.255.255.128`
- Plage hôtes : `172.40.1.129 → 172.40.1.254`
- Adresse de diffusion : `172.40.1.255`
- Passerelle : `172.40.1.254`

---

### 🟦 Ventes / Études
- Adresse réseau : `172.40.2.0/26`
- Masque : `255.255.255.192`
- Plage hôtes : `172.40.2.1 → 172.40.2.62`
- Adresse de diffusion : `172.40.2.63`
- Passerelle : `172.40.2.62`

---

### 🟦 Logistique
- Adresse réseau : `172.40.2.64/26`
- Masque : `255.255.255.192`
- Plage hôtes : `172.40.2.65 → 172.40.2.126`
- Adresse de diffusion : `172.40.2.127`
- Passerelle : `172.40.2.126`

---

### 🟥 Serveurs (réseau imposé)
- Adresse réseau : `172.16.5X.0/24`
- Masque : `255.255.255.0`
- Plage hôtes : `172.16.5X.1 → 172.16.5X.254`
- Adresse de diffusion : `172.16.5X.255`
- Passerelle : `172.16.5X.253`

---

## Récapitulatif synthétique

| Sous-réseau        | Adresse réseau        | Masque              | Diffusion           | Passerelle          |
|--------------------|-----------------------|---------------------|---------------------|---------------------|
| Production         | 172.40.0.0/24         | 255.255.255.0       | 172.40.0.255        | 172.40.0.254        |
| Autres             | 172.40.1.0/25         | 255.255.255.128     | 172.40.1.127        | 172.40.1.126        |
| Administratif      | 172.40.1.128/25       | 255.255.255.128     | 172.40.1.255        | 172.40.1.254        |
| Ventes / Études    | 172.40.2.0/26         | 255.255.255.192     | 172.40.2.63         | 172.40.2.62         |
| Logistique         | 172.40.2.64/26        | 255.255.255.192     | 172.40.2.127        | 172.40.2.126        |
| Serveurs           | 172.16.5X.0/24        | 255.255.255.0       | 172.16.5X.255       | 172.16.5X.253       |
