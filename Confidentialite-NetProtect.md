# NetProtect — Note de confidentialité

*Version 1.3 — application Android NetProtect v2.5*

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

## Ce que le vendeur voit, et où

- Le vendeur ne voit **que trois choses** liées à votre licence : votre **numéro de commande**,
  une **empreinte technique** de votre téléphone (non réversible, sert à bloquer le partage de la
  clé) et la **date d'activation**. Ni votre nom, ni votre e-mail, ni votre numéro de téléphone,
  ni aucun site que vous visitaz.
- Ces trois informations sont stockées sur des serveurs situés **aux États-Unis** (hébergeur du
  service de licence). Elles ne sont ni revendues, ni utilisées à des fins publicitaires.
- Vous pouvez demander la **suppression de votre licence** (contactez le vendeur avec votre numéro
  de commande) : la ligne correspondante est alors effacée du serveur.