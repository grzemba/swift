---

copyright:
  years: 2018
lastupdated: "2018-08-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Création d'applis Swift avec les kits de démarrage
{: #intro}

La console de développement {{site.data.keyword.cloud_notm}} pour Apple afin de permettre aux développeurs de créer ds applis à partir des différents kits de démarrage, mettre à disposition et connecter les principaux services optimisés {{site.data.keyword.cloud_notm}}, puis téléchargez rapidement le code opérationnel (ou définissez une distribution continue). Les utilisateurs peuvent ainsi créer, consulter, configure et gérer votre appli, mais également télécharger le code de votre appli. Avec les kits de démarrage, vous pouvez rapidement évaluer et tester les services {{site.data.keyword.cloud_notm}} avec une toute nouvelle appli.

Prêt à vous lancer ? Visitez dès maintenant le site [Console de développement pour Apple {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/appledevelopment/starter-kits) pour démarrer.
{: tip}

## Qu'est-ce qu'un kit de démarrage ?
{: #starter_kits}

Avec {{site.data.keyword.cloud_notm}} Developer Experience, vous pouvez choisir différents kits de démarrage. Les kits de démarrage indiquent à {{site.data.keyword.cloud_notm}} comment assembler de manière dynamique une appli de production squelette, dans le langage de votre choix, prête pour le déploiement en cloud. Chaque kit de démarrage intègre un langage, une infrastructure et un modèle pour un cas d'utilisation réel spécifique qui permet la réutilisation du code plutôt que sa réinvention.

Les kits de démarrage sont prêts pour la production et ils sont axés sur la démonstration d'une implémentation de pattern de clé à l'aide d'un environnement d'exécution (Swift, par exemple). Dans certains cas, les kits de démarrage offrent une expérience utilisateur simple ayant pour but de mettre en évidence l'intégration du service. Dans d'autres cas, les kits de démarrage représentent une implémentation personnalisable d'un cas d'utilisation élaboré.

Les kits de démarrage contiennent des instructions permettant à {{site.data.keyword.cloud_notm}} de générer automatiquement des applications échafaudées avec du code portable et d'indiquer la mise à disposition automatique de ressources lorsque vous créez une appli depuis le kit de démarrage.

## Utilisation de la console de développement {{site.data.keyword.cloud_notm}} pour Apple
{: #journey}

La console de développement {{site.data.keyword.cloud_notm}} pour Apple propose un processus transparent pour la génération d'une application Starter Swift pour votre cas d'utilisation spécifique. Examinons les étapes que vous pouvez au cours de ce processus.

### Ecran de présentation
{: #overview_screen}

Cet écran présente le contenu qui est adapté à un ensemble de cas d'utilisation tels que Watson, Weather, etc. Depuis l'écran de présentation, vous pouvez accéder à la documentation, aux ressources de formation, parcourir les services, consulter les kits de démarrage en exergue ou encore établir une liaison à une collection kits de démarrage plus large. Cliquez sur `Kits` dans la zone de navigation de gauche pour passer à la vue Kits de démarrage.

![Ecran de présentation de la console de développement {{site.data.keyword.cloud_notm}} pour Apple](images/overview_screen.png "Ecran de présentation") <br> *Ecran de présentation de la console de développement {{site.data.keyword.cloud_notm}} pour*

### Vue Kits de démarrage
{: #starter_kits_view}

La vue Kits de démarrage affiche la collection des kits de démarrage spécifiques à une zone de cas d'utilisation. Vous pouvez cliquer sur les différents liens d'une carte de kit de démarrage pour voir des démonstrations et d'autres informations. Sélectionnez un kit de démarrage pour passer à la vue Créer une appli.

![Vue Kits de démarrage de la console de développement {{site.data.keyword.cloud_notm}} pour Apple](images/starter_kits_screen.png "Vue Kits de démarrage") <br> *Vue Kits de démarrage de la console de développement {{site.data.keyword.cloud_notm}} pour Apple*

### Vue Créer une appli
{: #create_new_app_view}

Depuis la vue **Créer une appli**, vous pouvez nommer votre appli, mais également fournir des informations de déploiement et de routage. Sur la droite, vous pouvez également voir les services qui sont automatiquement mis à disposition lorsque vous créez votre appli, ainsi que les plans de tarification, et les conditions de chacun. Cliquez sur `Créer` pour accéder à la vue Détails de l'application. Si vous n'êtes pas connecté à {{site.data.keyword.cloud_notm}}, vous devez le faire maintenant.

![Vue Créer une application de la console de développement {{site.data.keyword.cloud_notm}} pour Apple](images/create_new_project_screen.png "Vue Créer une application") <br> *Vue Créer une application de la console de développement {{site.data.keyword.cloud_notm}} pour Apple*

## Vue Détails de l'application
{: #app_details_view}

Cette vue affiche une liste de tous les services configurés pour votre appli. Pour chaque élément de la liste, vous pouvez voir le nom de service, les liens vers d'autres informations, et un bouton **Actions** comportant trois points alignés verticalement. Les options du bouton **Actions** permettent de retirer des services d'une appli, d'ouvrir le tableau de bord du service et de supprimer un service. Le retrait d'une instance de service retire l'association à cette appli, mais cela ne supprime pas l'instance de service. De plus, les données d'identification du service sont consolidées dans cette vue, de sorte que vous n'avez pas à visiter chaque vue d'instance de service individuelle pour les obtenir.

![Vue Détails de l'application de la console de développement {{site.data.keyword.cloud_notm}} pour Apple](images/project_details_screen.png "Vue Détails de l'application") <br> *Vue Détails de l'application de la console de développement {{site.data.keyword.cloud_notm}} pour Apple*

Depuis la vue Détails de l'application, vous pouvez ajouter des services nouveaux ou existants à votre appli qui ne faisaient pas parti du kit de démarrage d'origine. Cliquez sur le lien **Ajouter une ressource** dans la zone de liste de service pour ajouter des services. Les services disponibles dépendent du type d'appli et des services qui sont offerts dans une région, de sorte qu'il n'est pas possible d'associer tous les services à toutes les applis.

![Boîte de dialogue Ajouter une ressource de la console de développement {{site.data.keyword.cloud_notm}} pour Apple](images/add_resource_screen.png "Boîte de dialogue Ajouter une ressource") <br> *Boîte de dialogue Ajouter une ressource de la console de développement {{site.data.keyword.cloud_notm}} pour Apple*

Dans la vue Détails de l'application, vous pouvez accéder au code de deux manières différentes :
*  Sélectionnez **Télécharger le code** pour générer et télécharger le code de votre appli.

### Vue Liste des applications
{: #app_list_view}

Vous pouvez afficher la liste de toutes les applis créées à partir de la vue Liste des applications. Vous pouvez renommer ou supprimer vos applis dans cette vue. Cliquez sur la ligne du nom d'une application afin de revenir à la vue Détails de l'application.

![Vue Liste des applications de la console de développement {{site.data.keyword.cloud_notm}} pour Apple](images/project_list_screen.png "Vue Liste des applications") <br> *Vue Liste des applications de la console de développement {{site.data.keyword.cloud_notm}} pour Apple*

Pour plus d'informations, visitez le site [{{site.data.keyword.cloud_notm}} Developer Console for Apple Learning Resources](https://console.bluemix.net/developer/appledevelopment/learning-resources).
{: tip}