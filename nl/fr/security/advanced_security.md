---

copyright:
  years: 2018
lastupdated: "2018-11-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}
{:tip: .tip} 

# Génération avec sécurité avancée
{: #security}

Les services de sécurité avancés d'{{site.data.keyword.cloud}} permettent aux développeurs Swift de protéger leurs clés et leurs données (au repos, en utilisation, ou en transit) de manière simple et bénéficiant du plus haut niveau de sécurité de l'industrie.
{: shortdesc}

Une méthode simple consiste à utiliser directement les services de plateforme hypersécurisés {{site.data.keyword.cloud_notm}} pour l'ensemble des services de sécurité avancés dans {{site.data.keyword.cloud}}. Pour plus d'informations, voir [Initiation aux services de plateforme hypersécurisés {{site.data.keyword.cloud_notm}}](/docs/services/hypersecure-platform/index.html){:new_window}.

## Utilisation du service {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}}

{{site.data.keyword.hscrypto}} est un service expérimental qui permet le chiffrement sur vos clés et de vos données avec le niveau de sécurité le plus élevé du secteur. Il offre la sécurité et l'intégrité d'IBM Z dans le cloud. La même technologie cryptographique sur laquelle les banques et les services financiers s'appuient est maintenant offerte aux utilisateurs de cloud via {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.hscrypto}} offre des modules de sécurité matérielle (HSM) adressables en réseau pour fournir un chiffrement sûr et sécurisé grâce aux interfaces de programmation d'applications PKCS#11. Vous pouvez accéder au plus haut niveau de sécurité possible pour le matériel cryptographique, c'est-à-dire FIPS 140-2 Niveau 4. {{site.data.keyword.hscrypto}} utilise également la solution IBM Advanced Crypto Service Provider (ACSP) qui permet l'accès à distance aux coprocesseurs cryptographiques d'IBM.

{{site.data.keyword.hscrypto}} est aussi le magasin de clés du service {{site.data.keyword.keymanagementserviceshort}}.

Pour plus d'informations sur {{site.data.keyword.hscrypto}}, voir [Initiation à {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}}](/docs/services/hs-crypto/index.html){:new_window}.

## Utilisation d'{{site.data.keyword.cloud_notm}} {{site.data.keyword.keymanagementserviceshort}}

{{site.data.keyword.keymanagementserviceshort}} permet de créer des clés chiffrées pour des applications au sein des services {{site.data.keyword.cloud_notm}}. Dans le cadre de la gestion du cycle de vie de vos clés, sachez que vos clés sont sécurisées par des modules HSM (Hardware Security Module) basés sur le cloud qui vous protègent contre le vol d'informations. Avec {{site.data.keyword.hscrypto}}, vos clés sont sécurisées au niveau de sécurité le plus élevé du certificat FIPS 140-2 Niveau 4.

Pour plus d'informations sur {{site.data.keyword.keymanagementserviceshort}}, voir [Initiation à {{site.data.keyword.keymanagementserviceshort}}](/docs/services/keymgmt/index.html){:new_window}.

## Utilisation d'{{site.data.keyword.cloud_notm}} Hyper Protect DBaaS
{: #hypersecure-dbaas}

{{site.data.data.keyword.cloud_notm}} Hyper Protect DBaaaS est un service {{site.data.data.keyword.cloud_notm}} expérimental qui crée des bases de données sécurisées sur demande. Il offre une plateforme extensible pour mettre à disposition et gérer rapidement et facilement votre base de données MongoDB.

Avec ce service, vous pouvez créer des clusters de base de données {{site.data.keyword.cloud_notm}}. Chaque cluster de base de données que vous créez possède une instance de base de données principale et deux instances de base de données secondaires qui servent de répliques de l'instance principale. La logique d'{{site.data.keyword.cloud_notm}} Hyper Protect DBaaS crée les bases de données MongoDB dans votre cluster de base de données et y accède.

### Sécurisation des données et confidentialité

{{site.data.keyword.IBM_notm}} héberge vos bases de données dans un environnement sécurisé hautement disponible et sécurisé :
 * Les données sont chiffrées au repos et à la volée.
 * Le matériel du système, la configuration du système et la configuration de la base de données garantissent une haute disponibilité.
 * Les technologies sous-jacentes empêchent {{site.data.keyword.IBM_notm}} ou un tiers d'accéder à vos données.

### Ajout de la logique {{site.data.keyword.cloud_notm}} Hyper Protect DBaaS à votre application 

Pour utiliser une base de données MongoDB dans votre application, voir
[Initiation à l'utilisation d'une base de données](../hypersecure_dbaas/database-cluster.html).  

### En savoir plus sur {{site.data.keyword.cloud_notm}} Hyper Protect DBaaS

Pour en savoir plus sur {{site.data.keyword.cloud_notm}} Hyper Protect DBaaS, voir [Initiation à IBM Cloud Hyper Protect DBaaS](/docs/services/hyper-protect-dbaas/index.html).

## Utilisation d'{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscontainers}}

{{site.data.keyword.hscontainers}} propose des outils puissants en combinant les technologies Docker et Kubernetes, une expérience utilisateur intuitive et une sécurité et un isolement intégrés pour automatiser le déploiement, l'exploitation, la mise à l'échelle et la surveillance d'applications conteneurisées dans un cluster d'hôtes de calcul.

{{site.data.keyword.hscontainers}} n'est disponible que pour les utilisateurs sponsorisés. Si vous souhaitez une assistance de sécurité dédiée, enregistrez-vous en tant qu'utilisateur sponsor auprès d'[IBM Z Client Feedback Program](https://www-01.ibm.com/marketing/iwm/iwmdocs/web/cc/earlyprograms/zcustomer.shtml) afin de déployer votre application dans le cluster {{site.data.keyword.hscontainers}}.
{: tip}

Avant de devenir un utilisateur sponsor, vous pouvez utiliser {{site.data.keyword.containershort_notm}} pour sécuriser votre application. Pour plus d'informations, voir [Initiation à {{site.data.keyword.containershort_notm}}](/docs/containers/container_index.html#container_index).
