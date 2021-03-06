---
title: "Scénarios de routage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rounting [WCF], scenarios
ms.assetid: ec22f308-665a-413e-9f94-7267cb665dab
caps.latest.revision: 
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3ef101a9a5f78e1b85ac7cb983b4766088b83317
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="routing-scenarios"></a>Scénarios de routage
Bien que le service de routage soit entièrement personnalisable, concevoir une logique de routage efficace lors de la création d'une configuration à partir de zéro peut s'avérer difficile.  Toutefois, il existe plusieurs scénarios courants que suivent la plupart des configurations de service de routage. Bien que ces scénarios puissent ne pas s'appliquer directement à votre configuration spécifique, comprendre comment configurer le service de routage en vue de gérer ces scénarios vous permet de mieux maîtriser le fonctionnement du service de routage.  
  
## <a name="common-scenarios"></a>Scénarios courants  
 L'utilisation de base du service de routage consiste à agréger plusieurs points de terminaison de destination de façon à réduire le nombre de points de terminaison exposés aux applications clientes, puis à utiliser des filtres de message pour router chaque message vers sa destination appropriée. Les messages peuvent être routés en fonction d'exigences de traitement logique ou physique, par exemple un type de message doit être traité par un service spécifique, ou en fonction d'exigences professionnelles arbitraires, comme offrir un traitement prioritaire aux messages provenant d'une source spécifique. Le tableau suivant répertorie des scénarios courants et indique dans quels cas les utiliser :  
  
|Scénario|Cas d'utilisation|  
|--------------|--------------|  
|Contrôle des versions du service|Vous devez prendre en charge plusieurs versions d'un service ou envisagez de déployer à l'avenir une mise à jour du service.|  
|Partitionnement des données du service|Vous devez partitionner un service entre plusieurs hôtes|  
|Mise à jour dynamique|Vous devez reconfigurer la logique de routage de manière dynamique au moment de l'exécution pour gérer les modifications des déploiements de service.|  
|Multidiffusion|Vous devez envoyer un message à plusieurs points de terminaison.|  
|Pontage de protocoles|Vous recevez des messages sur un protocole de transport, mais le point de terminaison de destination utilise un autre protocole.|  
|Gestion des erreurs|Vous devez assurer une tolérance aux pannes réseau et aux défaillances de communication.|  
  
> [!NOTE]
>  Bien que de nombreux scénarios présentés répondent à des besoins professionnels ou de traitement particuliers, prendre en charge les mises à jour dynamiques et utiliser la gestion des erreurs sont des pratiques souvent conseillées. Elles vous permettent de modifier la logique de routage au moment de l'exécution et de récupérer suite à des défaillances provisoires du réseau et de la communication.  
  
### <a name="service-versioning"></a>Contrôle des versions du service  
 Lorsque vous introduisez une nouvelle version d'un service, vous devez souvent maintenir la version précédente jusqu'à ce que tous les clients aient basculé sur le nouveau service. Cela pose un problème particulièrement critique si le service est un processus de longue durée d'exécution qui prend des jours, des semaines, voire des mois pour s'effectuer. Habituellement cela requiert l'implémentation d'une nouvelle adresse de point de terminaison pour le nouveau service, tout en maintenant le point de terminaison d'origine pour la version précédente.  
  
 En utilisant le service de routage, vous pouvez exposer un point de terminaison pour recevoir les messages d'applications clientes, puis router chaque message vers la version appropriée du service, en fonction du contenu du message. L'implémentation de base implique d'ajouter au message un en-tête personnalisé, indiquant la version du service qui doit traiter le message. Le service de routage peut utiliser le XPathMessageFilter pour vérifier si un en-tête personnalisé est présent dans chaque message et router le message vers le point de terminaison de destination approprié.  
  
 Pour les étapes permettant de créer une configuration de contrôle de version de service, consultez [How To : le Service de contrôle de version](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md). Pour obtenir un exemple d’utilisation de la XPathMessageFilter pour router les messages selon un en-tête personnalisé, consultez la [les filtres avancés](../../../../docs/framework/wcf/samples/advanced-filters.md) exemple.  
  
### <a name="service-data-partitioning"></a>Partitionnement des données du service  
 Lors de la conception d'un environnement distribué, il est souvent préférable de répartir la charge de traitement entre plusieurs ordinateurs, afin d'assurer un haut niveau de disponibilité, de diminuer la charge de traitement sur les ordinateurs individuels, ou de fournir des ressources dédiées à un sous-ensemble spécifique de messages. Bien que le service de routage ne remplace pas une solution d'équilibrage de charge dédiée, sa capacité à effectuer des routages basés sur le contenu peut être utilisée pour router vers des destinations spécifiques des messages qui par ailleurs sont semblables. Par exemple, vous pouvez avoir besoin de traiter les messages d’un client spécifique séparément de ceux d’autres clients.  
  
 Pour les étapes permettant de créer une configuration du partitionnement de données de service, consultez [procédure : partitionnement des données de Service](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md). Pour obtenir un exemple de l’utilisation de filtres pour partitionner les données en fonction de l’URL et les en-têtes personnalisés, consultez la [les filtres avancés](../../../../docs/framework/wcf/samples/advanced-filters.md) exemple.  
  
### <a name="dynamic-routing"></a>Routage dynamique  
 Il est souvent préférable de modifier la configuration du routage pour satisfaire l'évolution des besoins professionnels : par exemple ajouter un itinéraire à la nouvelle version d'un service, modifier les critères de routage, ou modifier le point de terminaison de destination vers lequel le filtre route un message particulier. Le service de routage permet d'effectuer ces modifications via l'objet <xref:System.ServiceModel.Routing.RoutingExtension>, qui fournit une nouvelle RoutingConfiguration au moment de l'exécution. La nouvelle configuration entre immédiatement en vigueur, mais n'affecte que les nouvelles sessions traitées par le service de routage.  
  
 Pour les étapes utilisées pour implémenter le routage dynamique, consultez [comment faire : mise à jour dynamique](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md). Pour obtenir un exemple d’utilisation de routage dynamique, consultez la [Reconfiguration dynamique](../../../../docs/framework/wcf/samples/dynamic-reconfiguration.md) exemple.  
  
### <a name="multicast"></a>Multidiffusion  
 Lors du routage de messages, vous routez habituellement chaque message vers un point de terminaison de destination spécifique.  Toutefois, vous pouvez avoir besoin occasionnellement de router une copie du message vers plusieurs points de terminaison de destination. Pour effectuer un routage en multidiffusion, les conditions suivantes doivent être remplies :  
  
-   La forme du canal ne doit pas être de type demande-réponse (bien qu'elle puisse être monodirectionnelle ou duplex), car cette forme exige que l'application cliente ne reçoive qu'une seule réponse en réponse à la demande.  
  
-   Plusieurs filtres doivent retourner **true** lors de l’évaluation du message.  
  
 Si ces conditions sont réunies, chaque point de terminaison de destination associé à un filtre qui retourne true recevra une copie du message.  
  
### <a name="protocol-bridging"></a>Pontage de protocoles  
 En cas de routage de messages entre des protocoles SOAP dissemblables, le service de routage utilise des API WCF pour convertir le message dans un autre protocole. Cela se produit automatiquement lorsque le ou les points de terminaison de service exposés par le service de routage utilisent un protocole différent du ou des points de terminaison clients vers lesquels les messages sont routés. Il est possible de désactiver ce comportement si les protocoles utilisés ne sont pas standard ; mais vous devez alors fournir votre propre code de pontage.  
  
 . Pour obtenir un exemple de l’utilisation du Service de routage pour convertir des messages entre des protocoles, consultez le [pontage et la gestion des erreurs](../../../../docs/framework/wcf/samples/bridging-and-error-handling.md) exemple.  
  
### <a name="error-handling"></a>Gestion des erreurs  
 Dans un environnement distribué, il n'est pas rare de rencontrer des défaillances temporaires du réseau ou de la communication. Sans un service intermédiaire tel que le service de routage, la charge de gérer ces défaillances incomberait à l'application cliente. Si l'application cliente n'inclut aucune logique spécifique pour refaire une tentative en cas de panne réseau ou de défaillance de communication, et ne connaît aucun autre emplacement, l'utilisateur peut être confronté à une situation où il faut soumettre un message plusieurs fois avant que le service de destination réussisse à le traiter. Le client risque de ne pas être satisfait de l'application et de la considérer comme peu fiable.  
  
 Le service de routage tente de remédier à ce problème en fournissant de robustes fonctions de gestion des erreurs pour les messages confrontés à des pannes réseau ou des défaillances de communication. En créant une liste de points de terminaison de destination possibles et en associant cette liste à chaque filtre de messages, vous évitez le point de défaillance unique dû au fait de n'avoir qu'une seule destination possible. En cas de panne, le service de routage essaie de remettre le message au prochain point de terminaison de la liste, jusqu'à ce que le message soit remis, qu'une défaillance non liée à la communication se produise ou que tous les points de terminaison soient épuisés.  
  
 Pour les étapes permettant de configurer la gestion des erreurs, consultez [procédure : gestion des erreurs](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md). Pour obtenir un exemple d’implémentation de la gestion des erreurs, consultez le [pontage et la gestion des erreurs](../../../../docs/framework/wcf/samples/bridging-and-error-handling.md) et [avancées de gestion des erreurs](../../../../docs/framework/wcf/samples/advanced-error-handling.md) exemples.  
  
### <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour traiter la gestion de version](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)  
  
 [Guide pratique pour traiter le partitionnement des données](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md)  
  
 [Guide pratique pour effectuer une mise à jour dynamique](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md)  
  
 [Guide pratique pour effectuer la gestion des erreurs](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction au routage](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
