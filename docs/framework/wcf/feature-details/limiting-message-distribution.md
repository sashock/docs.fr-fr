---
title: Limitation de la distribution de messages
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8b5ec4b8-1ce9-45ef-bb90-2c840456bcc1
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b4d81583a8dfc2c48fb9b7533f071495b562615e
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2018
---
# <a name="limiting-message-distribution"></a>Limitation de la distribution de messages
Le canal homologue est, de par sa conception, une maille de diffusion. Son modèle de saturation de base implique la distribution de chaque message envoyé par tout membre d'une maille à tous les autres membres de cette maille. C'est idéal dans les situations où chaque message généré par un membre est pertinent et utile à tous les autres membres (par exemple, une salle de conversation). Toutefois, de nombreuses applications ont parfois besoin de limiter la distribution de messages. Par exemple, si un nouveau membre rejoint une maille et souhaite extraire le dernier message envoyé sur cette maille, cette demande ne doit pas être envoyée à chaque membre de la maille. Elle peut être limitée aux voisins proches ou les messages générés localement peuvent être filtrés. Les messages peuvent également être envoyés à un nœud individuel sur la maille. Cette rubrique décrit l'utilisation du nombre de sauts, d'un filtre de propagation de messages, d'un filtre local ou d'une connexion directe pour contrôler la façon dont les messages sont transférés sur la maille, et fournit des recommandations générales sur le choix d'une approche.  
  
## <a name="hop-counts"></a>Nombres de sauts  
 Le concept de `PeerHopCount` est semblable à la valeur TTL (durée de vie) utilisée par le protocole IP. La valeur du `PeerHopCount` est liée à une instance de message et spécifie le nombre de fois qu'un message doit être transféré avant d'être supprimé. Chaque fois qu'un client canal homologue reçoit un message, il l'examine afin de déterminer si le `PeerHopCount` est spécifié. S'il est spécifié, le client décrémente la valeur du nombre de sauts de un avant d'envoyer le message aux nœuds voisins. Lorsqu'un client reçoit un message dont la valeur du nombre de sauts est égale à zéro, il le traite mais ne le transfère pas aux voisins.  
  
 Le nombre de sauts peut être ajouté à un message en ajoutant `PeerHopCount` en tant qu'attribut à la propriété ou au champ applicable dans l'implémentation de la classe de message. Vous pouvez affecter à cet attribut une valeur spécifique avant d'envoyer le message à la maille. Vous pouvez ainsi utiliser le nombre de sauts pour limiter la distribution des messages sur la maille lorsque cela est nécessaire, ce qui évite la duplication de messages superflus. Cela est utile dans les cas où la maille comprend un grand nombre de données redondantes ou pour envoyer un message aux voisins immédiats ou voisins se trouvant à quelques sauts.  
  
-   Pour les extraits de code et des informations connexes, consultez la [blog de canal homologue](http://go.microsoft.com/fwlink/?LinkID=114531) (http://go.microsoft.com/fwlink/?LinkID=114531).  
  
## <a name="message-propagation-filter"></a>Filtre de propagation de messages  
 `MessagePropagationFilter` peut être utilisé pour le contrôle personnalisé de saturation de messages, en particulier lorsque le contenu des messages ou d'autres scénarios spécifiques déterminent la propagation. Le filtre prend les décisions de propagation pour chaque message passant par le nœud. C'est le cas des messages reçus par votre nœud en provenance d'autres emplacements de la maille ainsi que des messages créés par votre application. Le filtre ayant accès au message et à son origine, les décisions relatives à son transfert ou à sa suppression peuvent être basées sur toutes les informations disponibles.  
  
 <xref:System.ServiceModel.PeerMessagePropagationFilter> est une classe abstraite de base avec une fonction unique, <xref:System.ServiceModel.PeerMessagePropagationFilter.ShouldMessagePropagate%2A>. Le premier argument de l'appel de méthode passe dans une copie complète du message. La modification du message n'entraîne pas le changement du message proprement dit. Le dernier argument de l'appel de méthode identifie l'origine du message (`PeerMessageOrigination.Local` ou `PeerMessageOrigination.Remote`). Les implémentations concrètes de cette méthode doivent retourner une constante à partir de l'énumération <xref:System.ServiceModel.PeerMessagePropagation> indiquant que le message doit être transféré à l'application locale (`Local`), à des clients distants (`Remote`), aux deux (`LocalAndRemote`), ou ni à l'un ni à l'autre (`None`). Vous pouvez appliquer ce filtre en accédant à l'objet `PeerNode` correspondant et en spécifiant une instance de la classe de filtre de propagation dérivée dans la propriété `PeerNode.MessagePropagationFilter`. Assurez-vous que le filtre de propagation est joint avant d'ouvrir le canal homologue.  
  
-   Pour les extraits de code et des informations connexes, consultez la [blog de canal homologue](http://go.microsoft.com/fwlink/?LinkID=114532) (http://go.microsoft.com/fwlink/?LinkID=114532).  
  
## <a name="contacting-an-individual-node-in-the-mesh"></a>Contacter un nœud individuel dans la maille  
 Vous pouvez contacter un nœud individuel dans une maille en configurant un filtre local ou une connexion directe.  
  
 Si chaque nœud d'une maille a son propre ID, un ID de destination peut être spécifié dans l'implémentation de votre message. Vous pouvez configurer un filtre local en écrivant une fonction dans votre contrat de message qui ne rendra visible le message au nœud actuel que si son ID correspond à l'ID de destination spécifié. La maille transportant le message, la surcharge de traitement liée à la configuration d'une nouvelle connexion ne pèse donc pas. En revanche, il y a une perte de rendement puisque le message est envoyé plusieurs fois à travers la maille. Cette approche convient pour envoyer des messages à des membres individuels d'une maille tant que les messages ne sont pas trop volumineux ni trop fréquents.  
  
 Pour les connexions haut débit permanentes, il est préférable d'opter pour les connexions directes. Vous pouvez envoyer des informations de connexion sur la maille, puis configurer une connexion directe de votre choix pour envoyer/recevoir des messages.  
  
## <a name="choosing-an-approach-for-limiting-message-distribution"></a>Choix d'une approche pour limiter la distribution des messages  
 Lorsque vous découvrez un scénario dans lequel vous devez limiter la distribution des messages, posez-vous les questions suivantes :  
  
-   **Qui** doit recevoir le message ? Un nœud voisin seulement ? Un nœud ailleurs dans la maille ? La moitié de la maille ?  
  
-   **La fréquence à laquelle** sera envoyé ce message ?  
  
-   Le type de **la bande passante** utilisera ce message ?  
  
 Les réponses à ces questions peuvent vous aider à déterminer s'il faut utiliser le nombre de sauts, un filtre de propagation de messages, un filtre local ou une connexion directe. Prenez en compte les recommandations générales suivantes :  
  
-   **Qui**  
  
    -   *Nœud individuel*: filtre Local ou une connexion directe.  
  
    -   *Voisins à une certaine proximité*: PeerHopCount.  
  
    -   *Sous-ensemble complexe de la maille*: MessagePropagationFilter.  
  
-   **La fréquence à laquelle**  
  
    -   *Très fréquentes*: connexion directe, PeerHopCount, MessagePropagationFilter.  
  
    -   *Occasionnelles*: filtre Local.  
  
-   **Utilisation de bande passante**  
  
    -   *Haute*: connexion directe, utilisation de MessagePropagationFilter ou filtre local.  
  
    -   *Faible*: tout, connexion directe probablement ne pas nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une application de canal homologue](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
