
1. run the following commands in your powershell prompt 

```powershell
bcdedit /set hypervisorlaunchtype off
Disable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-All
```

1. if not working you can procced to the following solution as well 

	- search on the win search for : `core isolation`
	- then you gotta diable `memory integrity` feature.

--- 

- how to attribute a static ip address 

```bash
auto eth0 
iface eth0 inet static 
	address 192.168.10.5
	network 255.255.255.0
	getway 192.168.1.1
```

- restart the interfce eth0

```bash
-kk
```

- check the ip add 

```bash 
ip a
```


---

**Installation :**

sh

CopyEdit

`apk add busybox-extras`

**Configurer `udhcpd` :**  
Modifie le fichier `/etc/udhcpd.conf` :

sh

CopyEdit

`nano /etc/udhcpd.conf`

Ajoute cette configuration :

nginx

CopyEdit

`start 192.168.1.100 end 192.168.1.200 interface eth0 option subnet 255.255.255.0 option router 192.168.1.1 option dns 8.8.8.8, 8.8.4.4 lease 86400`

**Démarrer le service :**

sh

CopyEdit

`rc-service udhcpd start rc-update add udhcpd`

![[Pasted image 20250313003408.png]]

---
## **Vérifier l'accès réseau**

Essaye d’abord de voir si ta machine a accès à Internet :

sh

CopyEdit

`ping -c 4 8.8.8.8`

- **Si ça marche** : La connexion fonctionne, le problème vient des dépôts.
- **Si ça ne marche pas** : Tu as un problème réseau (par ex. la carte réseau n'est pas bien configurée).

## **Vérifier l'accès réseau**

Teste si la machine a une adresse IP :

sh

CopyEdit

`ip a`

- Si tu ne vois **aucune adresse IP** (hors `127.0.0.1`), alors la machine n'est pas connectée au réseau.
- Si tu vois une adresse **commençant par 169.254**, c'est un problème DHCP (aucun bail obtenu).

Ensuite, essaye un **ping vers une adresse IP** (Google DNS) :

sh

CopyEdit

`ping -c 4 8.8.8.8`

- **Si ça fonctionne** ✅ → Internet marche, mais le problème vient du DNS.
- **Si ça ne fonctionne pas** ❌ → Pas de connexion réseau (voir étape 2).

Teste maintenant un **ping avec un nom de domaine** :

sh

CopyEdit

`ping -c 4 google.com`

- **Si ça marche** ✅ → Le DNS fonctionne, ton problème peut être lié aux dépôts Alpine.
- **Si ça échoue** ❌ → Le DNS est mal configuré (voir étape 3).

---

## **2️⃣ Configurer l'interface réseau**

Si `ping 8.8.8.8` ne marche pas, ton interface réseau n'est pas bien configurée.  
Tu peux essayer de redémarrer le service réseau :

sh

CopyEdit

`ifup eth0`

Si ça ne marche pas, active l'interface manuellement :

sh

CopyEdit

`ip link set eth0 up udhcpc -i eth0`

Vérifie ensuite si une adresse IP est assignée :

sh

CopyEdit

`ip a`

---

## **3️⃣ Configurer le DNS**

Si `ping 8.8.8.8` marche mais `ping google.com` ne marche pas, il faut configurer ton DNS.

Ajoute Google DNS dans `/etc/resolv.conf` :

sh

CopyEdit

`echo "nameserver 8.8.8.8" > /etc/resolv.conf echo "nameserver 1.1.1.1" >> /etc/resolv.conf`

Teste à nouveau :

sh

CopyEdit

`ping -c 4 google.com`

---

## **4️⃣ Vérifier les dépôts Alpine**

Si le réseau fonctionne maintenant, mets à jour les dépôts :

sh

CopyEdit

`apk update`

---

## **3️⃣ Vérifier l’état du gestionnaire de paquets**

Si `apk update` ne fonctionne toujours pas, essaye de forcer la réinitialisation :

sh

CopyEdit

`rm -rf /var/cache/apk/* apk update`

Ensuite, réessaie l’installation de `dhcp` :

sh

CopyEdit

`apk add dhcp`
---

### 3️⃣ **Créer le fichier de service udhcpd**

Dans Alpine, certains services ne sont pas créés automatiquement. Il faut créer un script de démarrage pour **OpenRC**.

**Installation :**

sh

CopyEdit

`apk add busybox-extras`

**Configurer `udhcpd` :**  
Modifie le fichier `/etc/udhcpd.conf` :

sh

CopyEdit

`nano /etc/udhcpd.conf`

Ajoute cette configuration :

nginx

CopyEdit

`start 192.168.1.100 end 192.168.1.200 interface eth0 option subnet 255.255.255.0 option router 192.168.1.1 option dns 8.8.8.8, 8.8.4.4 lease 86400`

**Démarrer le service :**

sh

CopyEdit

`rc-service udhcpd start rc-update add udhcpd`
#### ➤ Crée un fichier de service :

sh

CopyEdit

`nano /etc/init.d/udhcpd`

Ajoute ce contenu :

sh

CopyEdit

`#!/sbin/openrc-run  name="udhcpd" command="/usr/sbin/udhcpd" pidfile="/var/run/udhcpd.pid"  depend() {     need net }`

Enregistre (`CTRL + X`, puis `Y`, puis `Enter`).

---

### 4️⃣ **Donner les permissions et activer le service**

Fais ces commandes pour donner les bonnes permissions :

sh

CopyEdit

`chmod +x /etc/init.d/udhcpd rc-update add udhcpd service udhcpd start`

---

### 5️⃣ **Vérifier si udhcpd fonctionne**

Après l'exécution, vérifie avec :

sh

CopyEdit

`ps aux | grep udhcpd netstat -tunlp | grep 67`

Si **udhcpd** fonctionne, il devrait écouter sur le port **67**.


---

## **📌 Configuration corrigée :**

ini

CopyEdit

```
Plage d'adresses pour eth1 
start 192.168.10.1 
end 192.168.100.254 
interface eth1 
option subnet 255.255.255.0 
option dns 8.8.8.8 
lease 86400  
# Plage d'adresses pour eth2 
start 192.168.20.1 
end 192.168.20.254 
interface eth2 
option subnet 255.255.255.0 
option dns 8.8.8.8 
lease 86400  
# Nombre maximal de baux max_leases 254`
```

🚀 **Ensuite, redémarre udhcpd :**

sh

CopyEdit

`service udhcpd restart`

Puis vérifie son état :

sh

CopyEdit

`service udhcpd status`