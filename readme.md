Projet #1 : Étude de cas et exigences

Concevez un réseau dans Cisco Packet Tracer pour connecter les départements ACCOUNTS et DELIVERY comme suit :

    Chaque département doit contenir au moins deux PC.
    Le nombre approprié de commutateurs et de routeurs doit être utilisé dans le réseau.
    En utilisant le réseau donné 192.168.40.0, toutes les interfaces doivent être configurées avec les adresses IP correctes, le masque de sous-réseau et les passerelles.
    Tous les dispositifs du réseau doivent être connectés à l'aide de câbles appropriés.
    Testez la communication entre les dispositifs dans les départements ACCOUNTS et DELIVERY.

Technologies mises en œuvre

    Création d'un réseau simple utilisant un routeur et un commutateur de couche d'accès.
    Connexion des dispositifs réseau avec le câblage approprié.
    Connexion de deux réseaux à l'aide d'un routeur.
    Subnetting et adressage IP.
    Attribution d'adresses IP aux interfaces du routeur.
    Allocation d'adresses IP statiques aux dispositifs hôtes.
    Test et vérification de la communication réseau.


    ### Conception du Réseau pour les Départements ACCOUNTS et DELIVERY

### 1. **Liste des Équipements**
- **Routeur Cisco (Router 1)**
- **Deux commutateurs Cisco (Switch 1 pour ACCOUNTS et Switch 2 pour DELIVERY)**
- **Quatre PC (deux pour chaque département)**

### 2. **Topologie du Réseau**
La topologie comprend deux départements, ACCOUNTS et DELIVERY, chacun connecté à un commutateur. Les commutateurs sont reliés à un routeur qui permet la communication entre les deux départements. Le réseau utilise l'adresse 192.168.40.0/24.

### 3. **Configuration des VLANs (si nécessaire)**
Si vous souhaitez isoler chaque département, vous pouvez créer des VLANs, mais dans cette configuration simple, cela n'est pas nécessaire. Tous les dispositifs seront sur le même réseau.

### 4. **Subnetting et Adressage IP**

Nous utilisons l'adresse réseau 192.168.40.0/24. Voici comment elle peut être subdivisée :

- **Département ACCOUNTS** : Sous-réseau 192.168.40.0/28
  - **Plage d'adresses disponibles** : 192.168.40.1 - 192.168.40.14
  - **Passerelle** : 192.168.40.1

- **Département DELIVERY** : Sous-réseau 192.168.40.16/28
  - **Plage d'adresses disponibles** : 192.168.40.17 - 192.168.40.30
  - **Passerelle** : 192.168.40.17

### 5. **Configuration des Interfaces sur le Routeur**

**a. Configurer les interfaces du routeur pour chaque sous-réseau :**
```bash
Router(config)# interface g0/0
Router(config-if)# ip address 192.168.40.1 255.255.255.240  # Pour ACCOUNTS
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# interface g0/1
Router(config-if)# ip address 192.168.40.17 255.255.255.240  # Pour DELIVERY
Router(config-if)# no shutdown
Router(config-if)# exit
```

### 6. **Attribution d'Adresses IP Statique aux Dispositifs Hôtes**

**a. Configuration des PC dans le département ACCOUNTS :**
- **PC1:**
  - **Adresse IP** : 192.168.40.2
  - **Masque de sous-réseau** : 255.255.255.240
  - **Passerelle** : 192.168.40.1

- **PC2:**
  - **Adresse IP** : 192.168.40.3
  - **Masque de sous-réseau** : 255.255.255.240
  - **Passerelle** : 192.168.40.1

**b. Configuration des PC dans le département DELIVERY :**
- **PC3:**
  - **Adresse IP** : 192.168.40.18
  - **Masque de sous-réseau** : 255.255.255.240
  - **Passerelle** : 192.168.40.17

- **PC4:**
  - **Adresse IP** : 192.168.40.19
  - **Masque de sous-réseau** : 255.255.255.240
  - **Passerelle** : 192.168.40.17

### 7. **Connexion des Dispositifs Réseau avec Câblage Approprié**
- **Routeur à Commutateurs** : Utilisez des câbles droits.
- **Commutateurs à PC** : Utilisez des câbles droits.

### 8. **Test et Vérification de la Communication Réseau**

**a. Ping entre les dispositifs des deux départements pour tester la communication.**

**Exemple de test de ping depuis PC1 vers PC3 :**
```bash
PC1> ping 192.168.40.18
```

### 9. **Conclusion**

Ce réseau permet une communication fluide entre les départements ACCOUNTS et DELIVERY, avec un routage inter-sous-réseaux assuré par le routeur. L'adressage IP est correctement configuré pour chaque sous-réseau, et tous les dispositifs peuvent communiquer entre eux via des connexions câblées appropriées.