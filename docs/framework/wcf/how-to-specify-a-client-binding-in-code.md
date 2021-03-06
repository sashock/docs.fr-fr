---
title: "Comment : spécifier une liaison client dans le code"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6c44bc03642eb83a28497b320a77b2f9f8c6fb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Comment : spécifier une liaison client dans le code
Dans cet exemple, un client est créé afin d’utiliser un service de calculatrice et la liaison du client est spécifiée de manière impérative dans le code. Le client accède au service `CalculatorService`, lequel implémente l'interface `ICalculator`. Le service et le client utilisent la classe <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Cette procédure part du principe que le service de calculatrice est en cours d'exécution. Pour plus d’informations sur la création du service, consultez [Comment : spécifier une liaison de Service dans la Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). Elle utilise également le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] fournit pour générer automatiquement les composants du client. Cet outil génère le code client permettant d'accéder au service.  
  
 La construction du client se divise en deux parties. L'outil Svcutil.exe génère la calculatrice `ClientCalculator` qui implémente l'interface `ICalculator`. Cette application cliente est ensuite créée en construisant une instance de `ClientCalculator`, puis en spécifiant la liaison et l'adresse du service dans le code.  
  
 Pour la copie de la source de cet exemple, consultez la [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) exemple.  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Pour spécifier une liaison personnalisée dans le code  
  
1.  Utilisez l'outil Svcutil.exe depuis la ligne de commande pour générer le code à partir des métadonnées de service.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  Le client généré contient l'interface `ICalculator` qui définit le contrat de service auquel l'implémentation du client doit satisfaire.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3.  Le client généré contient également l'implémentation de `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4.  Créez une instance de `ClientCalculator` qui utilise la classe <xref:System.ServiceModel.BasicHttpBinding> dans une application cliente. Appelez ensuite les opérations de service au niveau de l'adresse spécifiée.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5.  Compilez, puis exécutez le client.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de liaisons pour configurer des services et des clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
