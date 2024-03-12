[accueil](README.md)

<p align="center">
    <img src="https://user-images.githubusercontent.com/40355195/218433960-efb1147f-d81f-4a8a-80a4-a28451960311.png" />
</p>



Créer une audience enrichie et l'activer via le catalogue de destinations
=========================================================================

Exploitons les capacités d'intelligence artificielle d'Adobe Experience Platform pour créer une audience qui sera la plus à même d'acheter un équipement sportif de plein air au cours des 3 prochaines semaines. Nous allons nous baser sur l'analyse des données comportementales de nos précèdents acheteurs. 
Partageons ensuite cette audience à Snapchat et vers Adobe Campaign pour peaufiner notre ciblage avec les fonctionnalités présentes dans notre outil de marketing automation (règles de pression, gestion de la deliverabilité...).


## De l'intelligence au service de vos audiences
AEP met à disposition des services intelligents préconfigurés pour les utilisateurs métiers. Pour y accéder cliquer sur _Services_ dans le menu _Science des données_ et cliquez sur le bouton _Ouvrir_ dans la carte _IA dédiée aux clients_.


![image](https://user-images.githubusercontent.com/40355195/217492668-877411a8-c47e-45c6-bdb2-62c8a6aaa3ea.png)

Sur cet écran vous pouvez créér votre propre instance du modèle d'intelligence artificielle. 
La propension à la conversion doit être utilisée pour de la prédiction de vente, ce qui implique qu'un score élevé est positif et qu'un score faible est peu intéressant. Vous pouvez vous en servir pour prédire si les utilisateurs achèteront un produit, souscrirons à un abonnement ou soumettront un formulaire d'inscription.

Il est également possible de configurer le modèle pour la prévision de l'attrition (churn) comme par exemple l'annulation d'un abonnement ou le non retour sur votre site Web. 

Pour ce lab, l'instance a déjà été prédéfinie pour calculer un score de propension à l'achat d'équipements d'exterieurs au cours des 30 prochains jours. cliquez sur l'instance de service _Propensity to buy outdoor gears_

![image](https://user-images.githubusercontent.com/40355195/217497970-15da535b-f9a2-4339-9985-6ee232b27e74.png)

Le dahboard vous permet d'analyser la répartition de la population en 3 clusters: 
- Rouge: ceux ayant une faible propension à l'achat (score < 24)
- Jaune: ceux ayant une moyenne propension à l'achat (score entre 25 et 74)
- Vert: ceux ayant une forte propension à l'achat (score > 75)

Le dashboard présente également les facteurs d'influences qui ont le plus contribués à la décision dans chaque cluster. Les facteurs d'influences sont eux préconfigurés dans le modèle. 
Cliquez sur  le bouton _Créér le segment_ dans la carte propension élevée pour basculer dans l'éditeur de segment et ainsi créér votre audience. 

---

## Créér un segment pour les clients interessés par les équipements d'exterieurs

Vous voici dans l'interface de création des segments où vous allez pouvoir mixer vos critères de ciblages en se basant sur : 
- les Attributs: toutes les informations attachées au profil temps réel sont disponibles pour segmenter votre audiences, que ce soit les données personnelles, des préfèrences utilisateurs ou des valeurs dérivées tel que les score précèdement calculés.
- les Evènements: toutes les interactions que notre profil a eu avec la marque. On peut sélectionner 0, 1 ou plusieurs évènements et définir l'intervalle de temps dans lesquels ils doivent avoir eu lieu. Les logs de Campaign sont également disponibles.
- les Audiences: Il est possible de combiner les audiences déjà présentes dans la Customer Data Platform pour recouper les segments et dégager les intersections les plus pertinentes.


![image](https://user-images.githubusercontent.com/40355195/217499302-db898983-3f6b-455c-96f7-49345cdebaa6.png)

Dans notre cas, nous ciblons uniquement les profils avec un score élevé n'ayant pas cliqués sur un email dont le nom de diffusion contient _outdoor gears_ au cours des 2 dernières semaines. 

- Donnez le nom suivant à votre segment : [identifiantParticipant] - Propension ++ Sport Ext, par exemple _participant01 - Propension ++ Sport Ext_
- Ajoutez une description : Audience ayant une haute propension à l'achat d'équipements d'exterieurs sans click sur campagne email.
- Aller sur l'onglet Evènements, filtrer les évènements en saisissant _email opened_ dans le champ texte.
- Glissez-déposez l'évènement Email Opened dans l'interface de segmentation
- Cliquer sur l'évènement pour faire apparaitre les options avancées d'inclusion/exclusion
- Changez _Inclure_ par _Exclure_ dans le container _Règle d'évènement_
- Dans les variables de l'évènement Email Opened, saisissez _delivery name_ pour filtrer la liste disponible.
- Glissez-déposez la variable _Delivery Name_ dans la règle d'évènement et saisissez _outdoor gears_ comme valeur de comparaison
- Dans le container Evènement, changer la temporalité de _N'importe quand_ à _Dernier_ et tapez _14_ jours
- Actualisez l'estimation et cliquez sur _Enregistrer et fermer_


![segmentation](https://user-images.githubusercontent.com/40355195/217507906-1a1f2394-b80d-4967-a36d-fc586ad833d4.gif)


Nous allons maintenant pouvoir activer le segment à travers le catalogue des destinations de notre Customer Data Platform. Pour ce lab nous choisirons Adobe Campaign et Snapchat. 

---

## Activer votre segment vers Adobe Campaign

- Cliquer sur le bouton _Activer vers la destination_ et sélectionnez _Adobe Campaign_, cliquez sur Suivant
- Cliquer sur _Créer un planning_, laissez les options par défaut sauf pour la date de fin qui doit être marquée pour  le 11/03. Cliquez sur _Créer_ puis sur _Suivant_
- Nous allons transférer vers Adobe Campaign les champs suivants : 
  * xdm: person.name.firstName
  * xdm: person.name.lastName
  * \_demosystem4.CustomerAI.Propensitytobuyoutdoorgears.probability
  * xdm: personalEmail.address (clé obligatoire et de déduplication)
  
Cliquez sur _Suivant_, puis sur _Terminer_

![campaignActivation](https://user-images.githubusercontent.com/40355195/217518424-e3a5c9f9-7561-42ea-9944-51a7a2d961d0.gif)

Une fois la destination activé le segment va transiter sous forme de fichier vers Adobe Campaign qui va l'ingérer via un workflow de data management pour en créér une liste ou mettre à jour la table des profils si nécessaire.

![Campaign](https://user-images.githubusercontent.com/40355195/218585830-1fe7e50e-f8a2-4f1f-a355-0d214d66dc09.gif)


---

## Activer votre segment vers Snapchat

Nous allons maintenant activer notre audience à travers Snapchat en temps réel. Dès qu'un utilisateur qualifiera pour notre segment, son email hashé sera envoyé en  streaming vers le réseau social pour améliorer nos capacité de ciblage multicanale.

- Retournez sur votre segment en cliquant sur l'onglet _Parcourir_ du menu _Segment_.
- Cliquer sur le bouton _Activer vers la destination_ et sélectionnez _Snapchat - test, cliquez sur Suivant
- Cochez la case _Appliquez la transformation_ à côté du champ cible Identity:emailAdress
- Nous allons transférer vers Snapchat une audience composé d'un identifiant client. Ce peut être un numéro de téléphone, un identifiant publicitiare Google ou Apple ou bien un email. Dans tous les cas Snapchat, comme la plupart des réseaux sociaux, accepte uniquement les données encryptées. Nous allons utliser un email encrypté comme identifiant de client à partager à Snapchat. Sélectionner le champ suivant
  * xdm: personalEmail.address - Cochez la case _Appliquez la transformation_ pour envoyer le hash de l'email

Cliquez sur _Suivant_, puis sur _Terminer_ pour valider la destination. 

![snapchat](https://user-images.githubusercontent.com/40355195/217572903-fd40e3c6-a559-4e06-9edc-7a7c71d016a9.gif)


L'audience est partagé en temps réel vers Snapchat, et est visible dans l'interface d'administration Snapchat

![image](https://user-images.githubusercontent.com/40355195/217883972-32857e01-9c6b-4322-ac3e-b2dba44ad1a7.png)



Notre segment enrichi à l'intelligence artificelle **Propension ++ Sport Ext** a été partagé en quelques clics à l'outil de Marketing Automation ainsi qu'à un réseau social ! 
Partagez vos audiences est facilement réalisable en quelques clics vers toutes les destnations disponible dans le catalogue. Ces plateformes de destination incluent des solutions Adobe, des plateformes publicitaires, d’enquête et de marketing par e-mail, des extensions Experience Platform, et bien plus encore.

--- 

Bravo ! Vous avez terminé le lab 👍 ✨ 🎉 🚀 🤘 Ensemble nous avons pu  : 
- Améliorer notre connaissance client en collectant  de la donnée visiteur sur notre site web
- Batir une fiche client avec des données comportementales et des données personnelles. 
- Améliorer le revenu en reciblant les abandonnistes au travers de parcours client personnalisés.
- Faire du cross-sell en partageant des audiences boostées à l'intelligennce artificielle vers les outils de Marketing Automation et les réseaux sociaux


Tout ça en 1h30 👏 👏 👏 Ca mérite bien un cadeau pour tous ces efforts 😛 



[Accueil](README.md)
