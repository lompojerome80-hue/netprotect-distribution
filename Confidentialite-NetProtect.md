# NetProtect — Note de confidentialité

*Version 1.0 — application Android NetProtect v2.2*

## Ce que fait NetProtect

- NetProtect installe un **VPN local** sur votre téléphone pour filtrer le trafic Internet
  (blocage des sites adultes et des DNS chiffrés). Le VPN ne « sort » pas vers un serveur tiers :
  le trafic est analysé **sur votre appareil** puis renvoyé vers Internet.

## Données collectées

- **Aucune donnée personnelle n'est collectée** : pas de compte, pas de publicité,
  pas d'analytique, pas de tracking, pas de collecte de votre navigation.
- Les statistiques affichées (sites bloqués, requêtes analysées) restent **sur votre appareil**.
- L'application ne communique avec un serveur que dans deux cas :
  1. **L'activation de votre licence** (une seule fois, au premier lancement) : elle envoie
     un **identifiant technique de votre téléphone** (empreinte d'appareil) et votre clé,
     uniquement pour lier la clé à ce téléphone. Rien d'autre n'est transmis.
  2. Le **téléchargement des domaines adultes** (serveur de règles) : aucune information
     sur votre navigation, seulement l'heure et votre adresse IP publique (comme n'importe
     quelle visite de site).

## Mot de passe et licence

- Votre mot de passe de protection est stocké localement sous forme **hachée** (PBKDF2,
  sel aléatoire) : ni le vendeur ni un tiers ne peut le lire.
- Votre **clé d'activation** est vérifiée sur l'appareil (signature RSA hors ligne) :
  elle n'est jamais transmise.

## Vos droits

- Vous pouvez à tout moment désinstaller l'application : toutes ses données (règles,
  statistiques, mot de passe, licence) sont supprimées.
- Pour toute question : contactez le vendeur à partir de votre e-mail de commande.