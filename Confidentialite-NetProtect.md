# NetProtect — Note de confidentialité

*Version 2.0 — application Android NetProtect v2.12*
*Remplace la version 1.5 (qui décrivait la v2.9 et contenait une erreur sur la transmission de la clé de licence).*

## En une phrase

NetProtect filtre tout sur votre téléphone. Il n'existe **aucun serveur de surveillance** : ni votre navigation, ni vos recherches, ni les sites bloqués ne quittent votre appareil.

## Ce que fait NetProtect

- NetProtect installe un **VPN local** sur votre téléphone pour filtrer le trafic Internet
  (blocage des sites adultes, des recherches sensibles et des DNS chiffrés). Le VPN ne « sort »
  pas vers un serveur tiers : le trafic est analysé **sur votre appareil** puis renvoyé vers Internet.
- Le **filtre de recherche** compare le texte des recherches saisies dans le navigateur intégré
  à une liste de mots-clés **incluse dans l'application**. La comparaison se fait intégralement sur
  votre téléphone.
- La **liste des sites adultes** embarquée est stockée **compressée et chiffrée** (AES), puis
  contrôlée par une empreinte HMAC-SHA256 avant usage : elle n'est pas lisible en ouvrant simplement
  le fichier de l'application.

## Ce que la protection ne cache pas (honnêteté)

- Le chiffrement de la liste sert à **empêcher la lecture facile** de l'application par un tiers non
  laborieux. Ce n'est pas un secret industriel : la clé de déchiffrement est dans l'application,
  comme toute clé embarquée. Un informaticien expérimenté pourrait donc l'extraire.
- **L'intégrité réelle repose sur la signature du fichier** : Android refuse d'installer une version
  modifiée, et l'empreinte du certificat est publiée sur le site pour que vous puissiez vérifier le
  fichier que vous avez téléchargé.
- **La liste de règles téléchargée n'est pas signée.** Son adresse est obligatoirement en HTTPS, un
  fichier de moins de 20 000 domaines est refusé, et la fusion avec vos règles est **strictement
  additive**. Une source compromise peut donc ajouter des blocages à tort, mais **ne peut pas
  désobloquer** un site que vous aviez bloqué. C'est une limite réelle, que nous préférons indiquer
  plutôt que masquer.
- Aucun de ces mécanismes n'envoie quoi que ce soit sur Internet ni ne touche à votre vie privée.

## Données collectées

- **Aucune donnée personnelle n'est collectée** : pas de compte, pas de publicité, pas d'analytique,
  pas de tracking, pas de collecte de votre navigation.
- Les statistiques affichées (sites bloqués, requêtes analysées) restent **sur votre appareil**.
- **Aucun envoi n'est déclenché automatiquement.** Aucune donnée vous concernant ne part sans que
  vous le déclenchiez vous-même.
- L'application communique avec un serveur dans deux cas, et seulement deux :

  1. **L'activation de votre licence** (une seule fois, quand vous saisissez votre code).
     Sont transmis **exactement trois éléments** : l'identifiant de la commande, la signature
     RSA qui accompagne le code, et l'identifiant Android de l'appareil (`ANDROID_ID`). Rien d'autre.

     La signature est **vérifiée sur l'appareil avant tout appel réseau** : un code falsifié n'est
     jamais transmis. L'envoi se fait en HTTPS. Il sert uniquement à attacher la licence à cet
     appareil et à empêcher sa revente. Comme pour tout appel réseau, votre adresse IP publique est
     visible du serveur au moment de cet envoi.

  2. **Le téléchargement de la liste de règles.** C'est un téléchargement, pas un envoi : aucun
     élément de votre navigation n'est transmis. L'application vérifie au plus **une fois toutes
     les 24 heures**, uniquement au moment où vous activez la protection, et seulement si la liste
     a pu changer. L'adresse de la source est affichée dans l'écran « Règles » de l'application,
     ce qui vous permet de vérifier par vous-même d'où elle vient.

     Par défaut, la liste provient d'un **dépôt GitHub public** (projet StevenBlack/hosts), et non
     d'un serveur du vendeur. Votre adresse IP publique est visible de la source qui sert le
     fichier, comme pour n'importe quel téléchargement.

## Moteurs de recherche

- Une recherche lancée depuis le navigateur intégré passe par **Google, Bing ou DuckDuckGo**,
  selon le moteur choisi. Chaque moteur applique sa propre politique de confidentialité ; NetProtect
  n'y participe pas et n'en reçoit rien. Le filtre ne fait que bloquer la requête au moment où elle
  va partir, une fois le mot-clé comparé **localement**.

## Mot de passe et licence

- Votre mot de passe de protection n'est **jamais stocké en clair** : il est haché localement avec
  **PBKDF2-HMAC-SHA256, 200 000 itérations et un sel aléatoire de 16 octets**. Ni le vendeur ni un
  tiers ne peut le lire.
- Votre **clé d'activation** a la forme `identifiant:signature`. Sa signature RSA est vérifiée hors
  ligne sur l'appareil. Correction par rapport à la version 1.5 de cette note : l'identifiant et la
  signature **sont transmis** au serveur de licence lors de l'activation, afin d'y attacher la licence.
  Ce qui n'est jamais transmis, c'est votre navigation et votre mot de passe.

## Ce que le vendeur voit, et où

- Concernant **votre licence**, le serveur de licence enregistre trois éléments : l'identifiant de
  commande, l'identifiant Android de l'appareil (`ANDROID_ID`), et la date d'activation. Ni votre
  nom, ni votre e-mail, ni votre numéro de téléphone, ni aucun site que vous ne visitez.
- **Ce que le vendeur sait par ailleurs, parce que vous l'avez contacté :** pour vous remettre la
  clé, vous avez utilisé le canal de commande, donc le vendeur dispose au minimum du numéro ou de
  l'adresse que vous avez communiqué. C'est inhérent à toute vente à distance, et cela n'est pas
  collecté par l'application.
- Ces éléments sont stockés sur des serveurs situés **aux États-Unis** (hébergeur du service de
  licence). Ils ne sont ni revendus, ni utilisés à des fins publicitaires.
- **Aucune archive, aucun export, aucune sauvegarde** de votre navigation n'existe, parce que rien
  de tel n'est collecté.

## Vos droits

- **Désinstallation** : vous pouvez désinstaller l'application à tout moment. Toutes ses données
  locales (règles, statistiques, mot de passe, licence) sont supprimées.
- **Libération de licence** : si vous revendez votre téléphone, demandez la libération de votre
  licence avec votre identifiant de commande. Le rattachement licence / appareil est supprimé et la
  licence redevient utilisable sur un autre appareil.
- **Droit d'accès** : les données traitées sont exactement les trois listées ci-dessus ; il n'y en a
  pas d'autres.
- **Droit d'opposition et retrait** : le seul traitement indispensable au fonctionnement du service
  est l'activation de la licence. Le téléchargement de la liste de règles peut être neutralisé en
  pointant l'adresse de la source vers une liste locale, ou en ne jamais déclenchant la protection
  depuis un réseau non maîtrisé.
- Conformément à la **loi n° 001-2021/AN du 30 mars 2021** portant protection des personnes à
  l'égard du traitement des données à caractère personnel, vous pouvez aussi introduire une
  réclamation auprès de l'autorité de contrôle burkinabè compétente.
- Pour toute demande : contactez le vendeur par le canal de commande utilisé lors de l'achat.

## Sécurité réseau

- Depuis la **v2.12**, l'application **refuse tout trafic non chiffré** : sur un réseau hostile
  (Wi-Fi de motel, de café, d'aéroport), aucune requête en clair ne peut partir, et le contenu du
  trafic chiffré ne peut être ni lu ni modifié en transparence.
- Cela ne remplace pas un mot de passe distinct par compte, et ne protège pas contre un appareil
  auquel quelqu'un a installé un certificat d'autorité.