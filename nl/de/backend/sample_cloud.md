---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# Anwendungsfall für iOS und Cloudlogik
{: #sample_cloud}

Ein Beispiel für eine iOS-Anwendung, die eine BFF-Komponente nutzt, ist
in der Beispielanwendung [BluePic](https://github.com/IBM/BluePic) zu
sehen, die der gemeinsamen Nutzung von Bildern dient. Die BluePic-App nutzt die folgenden Technologien:

* Object Storage und Cloudant zum Speichern der Bilddaten
* Watson Visual Recognition und IBM Weather Company-Service zum Einbinden zusätzlicher Informationen in die Bilder
* Kitura und {{site.data.keyword.openwhisk}} zum Bereitstellen von Back-End-Logik sowie zum Steuern von Authentifizierung und Push-Benachrichtigungen (sämtlich in Swift geschrieben)

![BluePic](images/cloudlogic.png "Verarbeitungsablauf von BluePic")

Wenn im BluePic-Beispiel ein Bild gepostet wird, werden seine Daten in Cloudant aufgezeichnet und die Bildbinärdatei wird in Object Storage gespeichert. Von
dort aus wird eine {{site.data.keyword.openwhisk_short}}-Sequenz
aufgerufen, die eine Berechnung von Wetterdaten wie Temperatur und aktuelle
Wetterlage (z. B. sonnig oder bewölkt) für den Standort auslöst, an dem ein
Bild hochgeladen wurde. In der
{{site.data.keyword.openwhisk_short}}-Sequenz wird außerdem Watson
Visual Recognition eingesetzt, um das Bild zu analysieren und basierend auf dem
Inhalt des Bildes Texttags zu extrahieren. Am Ende wird eine
Push-Benachrichtigung an den Benutzer gesendet, die ihn über die Verarbeitung
des Bildes informiert und jetzt Wetter- und Tagdaten enthält.
