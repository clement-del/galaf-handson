<p align="center">
  <a href="https://ibb.co/bbSHPTB"><img src="https://i.ibb.co/J3fxKV7/Screenshot-2024-03-12-at-17-41-24.png" alt="Screenshot-2024-03-12-at-17-41-24" border="0"></a>
</p>


<div>
<br /><br />
<h1 align="center">Lien vers le lab <URL GALAF></h1>
<br /><br />
<p align="center">

</p>
</div>



# Lab 1 - Création d'un parcours avec Adobe Campaign augmenté

Adobe Campaign s'utilise conjointement avec la CDP Adobe pour enrichir l'expérience client avec un ensemble de fonctionnalités additionnelles. Vous allez ainsi pouvoir exploiter :

- La collecte de données en temps réel, au plus proche des utilisateurs et les segmenter à la volée en fonction de leurs comportements online, très utile pour personaliser le contenu sur les propriétés digitales en fonction de leurs appétences
- Un orchestrateur de parcours client individuels pour réagir en temps réel à des évènements générés par vos utilisateurs, et déterminer la meilleure expérience pour vos contacts. 
- Des modèles d'intelligence artificielle pour scorer vos contacts et déterminer leur propension à acheter un produit, ou leur propension à quitter les services de votre marque pour la concurrence. 
- Un vaste catalogue de destination pour activer vos audiences sur les canaux de votre choix: réseaux sociaux, email marketing, search & display, site web, CRM, etc..
- Appliquer des règles de gouvernance de la donnée et vous assurer que les données de vos utilisateurs soient uniquement utilisées à bon escient, et éviter tout risque de partage malencontreux vers un tiers, ou une utilisation de la donnée client qui n'a pas été consentie par votre contact. 


---

Au cours de ce Hands-On, nous allons utiliser une marque fictive d'équipements sportifs - intitulée **Luma** - pour illustrer ces fonctionnalités au travers d'un parcours client composé de 3 chapitres: 

- **L'acquisition de nouvelles données clients** depuis le site web Luma. Grace à la collecte en temps réel, nous allons récolter les interactions des visiteurs, même anonymes, et personnaliser le site web en temps réel en fonction de leurs comportements de navigation. Lorsqu'un utilisateur crééra son compte, son comportement en tant que visiteur anonyme sera automatiquement rattaché à son profil connu et complétera la vision 360° dans la CDP Adobe et dans Adobe Campaign V8. 

- **La conversion et l'abandon de panier**. En exploitant le moteur d'orchestration, nous allons pouvoir définir des messages personalisés à chacune des étapes du process de paiement en ligne. De l'ajout de produit dans un panier, à la finalisation du paiement, nous pouvons interagir à travers des communications personnalisées avec nos futurs clients, et également les recibler s'ils ne terminent pas le processus d'achat. Pour le routage des messages, faisons confiance à Adobe Campaign V8 !

- **Le cross sell**. Exploitons les capacités d'IA de la CDP Adobe pour calculer l'audience qui sera la plus à même d'acheter un accessoire de sport extérieur au cours des 3 prochaines semaines en nous basant sur l'analyse des données comportementales de nos précèdents clients. Partageons ensuite cette audience vers Snapchat puis Adobe Campaign V8


## Objectifs d'apprentissage
- Visualiser le profil temps réel et la reconciliation d'identités dans la CDP Adobe
- Configurer un parcours client avec un message personnalisé 
- Créer un segment utilisant les scores calculés par les services d'IA de la CDP Adobe
- Activer ce segment vers Adobe Campaign V8 et les réseaux sociaux


## Prérequis
- Un navigateur web **ouvert en mode incognito**, ceci afin de ne pas mélanger l'identifiant de connexion Adobe utilisé pour le Hands-On avec celui de votre entreprise. 
- Les logins et mots de passe pour vous connecter à l'environnement de démo.



## Exercices

[Acquisition](./ca-lab1-acquisition.md): Naviguer sur le site internet de démo et générer des données pour ensuite les visualiser dans la CDP Adobe.

[Conversion](./ca-lab1-conversion.md): Configurer le message personnalisé lors de l'abandon d'un panier sur le site e-commerce.

[Cross Sell](./ca-lab1-cross-sell.md): Créer une audience enrichie et l'activer via le catalogue des destinations.








