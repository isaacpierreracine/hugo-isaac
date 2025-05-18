---
title: Perpétuelle 01 - illusion ruisseau
date: '2025-03-26T12:51:15+01:00'
tags: ['perpetuelle','ruisseau']
categories: ['art']
draft: false
cover:
    image: /hugo-isaac/img/ruisseau3.jpg
    alt: 'this is an image'
    caption: 'croquis abstrait'
---
(may 3, 2025)  
L'installation est située en bordure d'un sentier préambule du spectacle du Cirque de la Pointe Sèche qui adapte MacBeth avec un fond thématique de magie et de prédilection; un élément scénographique qui transmet l'énergie d'un ruisseau à un artefact cinétique capable de créer une illusion optique. L'oeuvre est en fonction de nuit, une heure par jour, 6 jours par semaine pendant 2 mois. 

J'ai défini les éléments formels de l'installation prenant en considération:   

- lieu sur le sentier
- source d'énergie naturelle disponible
- thème dramatique du spectacle (dualité,double,cycles...)
- illusion optique potentielle et pertinence avec la thèmatique du spectacle 
- contexte de diffusion

L'esthétique est déterminée par les besoins fonctionels symboliques et conditionnée par les contraintes  techniques et logistiques. Conceptuellement mon critère cherche avant tout une harmonie avec le processus d'expérimentation avec un ensembles d'éléments trouvés pendant les différentes étapes de création. Il est difficile pour moi de considérer une oeuvre terminée. Je concois l'idée qu'elle puisse arrêter d'évoluer mais jamais se termniner. 
Un de mes plus grand défi est d'intégrer la source d'énergie comme l'élément de la rencontre du sens et de la fonctionalité. 

#### Processus décisionel - intuitif et contradictoire. 

J'ai élaboré plusieurs scénarios d'implantation avec différents endroits du sentier et du potentiel interactif avec le ruisseau et j'ai décidé de situer l'installation dans un petit alcôve rocheux bordé de quelques vieux cèdres en bordure du sentier de suite après avoir traversé le ruisseau. La proximité d'un lieu isolé du reste, la quiétude, la profondeur crée une atmosphère pertinente à mes intentions. L'emplacement offre aussi plusieurs avantages techniques et logistiques. Il est à l'abri du vent et de l'intempérie, l'espace est contenu facilitant autant l'éclairage, le sonore et les travaux d'installation et de maintenance. 
Un socle, perché sur un tréteau métallique soutient le masque en rotation. Le mouvement est activé par un jet d'eau propulsé sur les pales d'une hélice qui entrainent un système de poulies e d'axes concues pour permettre la rotation du masque et des autres éléments.

![Alt text](/hugo-isaac/img/alcove1.jpg)*Alcôve du ruisseau*
![Croquis](/hugo-isaac/img/ruisseaucroquis.jpg)  

Pour l'illusion optique mon choix s'est arrêté sur l'idée d'un masque rotatif de type "hollow face illusion". Dans un éclairage spécifique, dans un rayon de distance détermninée, lorsqu'on observe le masque  d'un visage humain en rotation, une étrange illusion apparaît. De même lorsqu'on bouge en observant le masque statique l'illusion apparaît aussi. Je veux combiner le mouvement du point de vue et le mouvement du masque sur son axe. Mon désir est de créer une interaction. 

![Alt text](/hugo-isaac/img/hollowface.jpg)*[Holow face illusion](https://www.youtube.com/watch?v=sKa0eaKsdA0&t=1s)*  
![Alt text](/hugo-isaac/img/masque1.jpg)*prototype illusion optique* 

#### Prototypage d'une idéee: vers un proof-of-concept. 

![Alt text](/hugo-isaac/img/ruisseau2.jpg) 

Pour commencer j'ai produit un masque de mon propore visage pour comprendre, tester et expérimenter avec la création de l'illusion optique. J'ai moulé mon visage puis retravaillé le moule manuellement ajoutant du platre pour égualiser les parties externes et internes ajoutant des petits bouts de bande de platre et une finition au pinceau avec du platre de paris. 
![Alt text](/hugo-isaac/img/masque2.jpg)*1 er moule auto-pprtrait* 
![Alt text](/hugo-isaac/img/masque3.jpg)*moule auto-pprtrait retouché*  
![Alt text](/hugo-isaac/img/masque4.jpg)*moule auto-pprtrait revers retouché*  
*Noter que l'effet visuel rend impossible photographier la texture réelle du négatif du visage. Le perception photographique est incapable de montrer le réel. Elle ne montre que l'illusion.*  
 
Tous les éléments sont des objets trouvés, recyclés et/ou industriels neufs trouvés en liquidation dans les quincaileries locales. J'ai orientée ma recherche vers les éléments de formes circulaire ou en spirale. J'ai cherché les matériaux à l'éco-centre principalement et parmi des objets de mon inventaire personel. 

![Alt text](/hugo-isaac/img/objetstrouves1.jpg)*éléments d'inspiration*  

L'installation est 100% autonôme énergétiquement via une colonne d'eau formée de boyaux dont l'entrée est placé en amont et la sortie au lieu de l'installation. Le dénivellement entre les deux points, d'une quinzaine de mètres, permet un débit et une pression suffisante pour activer le mécanisme et produire le courant électrique de l'éclairage. 
La colonne d'eau est composée de 35m. de boyau de pompier (1.5 pcs diam.) réduit à un boyau d'arrosage de   1/2 pcs d'une longueur de 25m..  

L'effet d'éclaboussement sur les pales de l'hélices rend manifeste la force hydraulique permettant à l'installation d'exister.
![Alt text](/hugo-isaac/img/helice1.jpg)*Force d'impact eau/hélice*  

#### Production
    
J'ai fait une listes des éléments et processus impliqués pour la réalisation du projet. 

- hollow mask
    - masques (1)
    - support masque et mécanique des mouvements
    - canalisation eau 
    - mini-turbine hydraulique (2 x 9v./10 watt) 
    - moteur dc à engrenage (mouvement 1-socle)
    - moteur dc à engrenage (mouvement 2-masque)
    - control moteur 
    - plaque esp32 ou Arduino (tbd) 
    - control d'interaction (numérique ou analogique)
    - batterie (si intection numérique) 
    - programmation 

  *Note: Un valve électrique connecté au réseau principal du sentier, permet aux techniciens du Cirque de la Pointe Sèche d'activer et de désactiver l'installation manuellement au début et à la fin du spectacle. 

L'esthétique finale va évoluer avec le processus de réalisation. Seul un doute important persiste à savoir s'il est vraiment nécessaire d'intégrer une technologie numérique pour le mécanisme d'interaction avec le public. Je souhaite trouver une solution alternative, plus analogue et qui offre une intaraction bien réelle.  




