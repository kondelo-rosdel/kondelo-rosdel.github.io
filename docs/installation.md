# ⚙️ Installation

## 1. Raspberry Pi OS

````md

```bash
sudo apt update && sudo apt upgrade -y
````

## 2. Installer Pi-hole

```bash
curl -sSL https://install.pi-hole.net | bash
```

Options recommandées:

* DNS: 1.1.1.1
* Interface: wlan0

## 3. Installer Tailscale

```bash
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up
```

````

---

# 📄 docs/configuration.md

```md
# 🔧 Configuration

## Pi-hole + Tailscale

Éditer:

```bash
sudo nano /etc/dnsmasq.d/02-pihole.conf
````

Ajouter:

```conf
interface=tailscale0
```

Redémarrer:

```bash
pihole restartdns
```

## DNS Tailscale

```bash
sudo tailscale up --accept-dns=true
```

````

---

# 📄 docs/network.md

```md
# 🌐 Configuration réseau (Freebox)

## Paramètres

- IP fixe: 192.168.1.50
- DNS: 192.168.1.50

## DHCP

Réserver l'IP du Raspberry.

## Test

```bash
nslookup google.com 192.168.1.50
````

````

---

# 📄 docs/commands.md

```md
# 🧪 Commandes utiles

## Statut

```bash
pihole status
tailscale status
````

## Logs

```bash
pihole -t
journalctl -u tailscaled
```

## Restart

```bash
sudo systemctl restart pihole-FTL
sudo systemctl restart tailscaled
```

````

---

# 📄 docs/troubleshooting.md

```md
# 🛠️ Troubleshooting

## Pi-hole ne bloque pas

- Vérifier DNS client
- Vérifier IP Pi-hole

## Tailscale KO

```bash
tailscale status
````

Relancer:

```bash
sudo tailscale up
```

## Conflit DNS

```bash
sudo tailscale up --accept-dns=false
```

````

---

# 📄 docs/diagrams.md

```md
# 📊 Architecture

````

[ Client ]
|
v
[ Pi-hole ] ---> Internet
|
v
[ Tailscale VPN ]
|
v
[ Accès distant ]

```
```

---

# 🚀 Déploiement GitHub Pages

1. Push le repo
2. Aller dans Settings → Pages
3. Source: `/docs`

---

# 🎨 Bonus (optionnel)

Créer `_config.yml`

```yml
theme: minima
title: Pi-hole Homelab
```

---

# ✅ DONE

Projet prêt à être publié 🚀
