---
title: Reprise de signet WorkflowHostingEndpoint
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 140ff5282447c2a2307dee325645fc1f3f0497fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>Reprise de signet WorkflowHostingEndpoint
Cet exemple montre comment <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> peut être utilisé avec <xref:System.ServiceModel.Activities.WorkflowServiceHost> pour créer des instances de workflow.  
  
## <a name="demonstrates"></a>Démonstrations  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Discussion  
 Cet exemple utilise <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> pour créer une instance de workflow hébergée à l'aide de <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> est un point d'extensibilité pour <xref:System.ServiceModel.Activities.WorkflowServiceHost> qui peut être utilisé dans les scénarios suivants :  
  
-   Création d'instances de workflow.  
  
-   Reprise de signets sur une instance de workflow hébergée dans un <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 L'exemple de point de terminaison inclus expose un contrat qui fournit des opérations pour créer un workflow et retourner un ID d'instance, ou créer une instance avec un ID spécifique. L'exemple d'application console crée une instance <xref:System.ServiceModel.Activities.WorkflowServiceHost> avec une définition de workflow de base et ajoute un `CreationEndpoint` à l'hôte. Il fait alors appel à l'opération `Create` sur le point de terminaison pour créer une instance de workflow.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Générez la solution.  
  
2.  Exécutez l'application. La console `CreationEndpoint` affiche un message qui inclut l'ID d'instance lorsque l'instance de workflow est créée. Le message « Hello World ! » est imprimé par le flux de travail sur la reprise réussie du signet.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
