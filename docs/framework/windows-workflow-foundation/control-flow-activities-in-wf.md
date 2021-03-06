---
title: "Activités de flux de contrôle dans WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6892885b-f7c5-4aea-8f5e-28863fb4ae75
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e8520e34cf9bd9d31e9b877849e7c9611d6d989
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="control-flow-activities-in-wf"></a>Activités de flux de contrôle dans WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] fournit plusieurs activités pour le contrôle de flux d'exécution dans un workflow. Quelques-unes de ces activités (telles que `Switch` et `If`) implémentent des structures de contrôle de flux semblables à celles utilisées dans les environnements de programmation tels que [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], alors que d'autres modélisent de nouvelles structures de programmation (telles que `Pick`.)  
  
 Notez que lorsque les activités telles que les activités `Parallel` et `ParallelForEach` planifient plusieurs activités enfants pour qu'elles s'exécutent simultanément, seul un thread unique est utilisé pour un workflow. Chaque activité enfant de ces activités s'exécute séquentiellement et les activités consécutives ne s'exécutent pas tant que d'anciennes activités ne soient terminées ou ne deviennent inactives. Par conséquent, ces activités sont très utiles pour les applications dans lesquelles plusieurs activités potentielles de blocage doivent s'exécuter de façon entrelacée. Si aucune des activités enfants de ces activités n'est inactive, une activité `Parallel` s'exécute juste comme une activité `Sequence`, et une activité `ParallelForEach` s'exécute juste comme une activité `ForEach`. Si, toutefois, des activités asynchrones (telles que des activités qui dérivent de <xref:System.Activities.AsyncCodeActivity>) ou des activités de messagerie sont utilisées, le contrôle passe à la branche suivante alors que l'activité enfant attend son message à accepter ou son travail asynchrone à exécuter.  
  
## <a name="flow-control-activities"></a>Activités de contrôle de flux  
  
|Activité|Description|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.DoWhile>|Exécute une fois les activités contenues et continue de le faire jusqu'à ce qu'une condition soit `true`.|  
|<xref:System.Activities.Statements.ForEach%601>|Exécute une instruction incorporée en séquence pour chaque élément d'une collection. <xref:System.Activities.Statements.ForEach%601> est semblable au mot clé `foreach`, mais est implémenté comme une activité et non comme une instruction de langage.|  
|<xref:System.Activities.Statements.If>|Exécute des activités contenues si une condition est `true`, et peut exécuter des activités contenues dans la propriété <xref:System.Activities.Statements.If.Else%2A> si la condition est `false`.|  
|<xref:System.Activities.Statements.Parallel>|Exécute des activités contenues en parallèle.|  
|<xref:System.Activities.Statements.ParallelForEach%601>|Exécute une instruction incorporée en parallèle pour chaque élément d'une collection.|  
|<xref:System.Activities.Statements.Pick>|Fournit une modélisation de flux de contrôle reposant sur des événements.|  
|<xref:System.Activities.Statements.PickBranch>|Représente un chemin d'exécution potentiel dans une activité <xref:System.Activities.Statements.Pick>.|  
|<xref:System.Activities.Statements.Sequence>|Exécute des activités contenues dans l'ordre.|  
|<xref:System.Activities.Statements.Switch%601>|Choisit de traiter une activité parmi un certain nombre d'activités, en fonction de la valeur de l'expression donnée.|  
|<xref:System.Activities.Statements.While>|Exécute des activités contenues tant qu'une condition est `true`.|
