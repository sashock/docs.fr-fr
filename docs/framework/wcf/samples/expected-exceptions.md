---
title: Expected Exceptions
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 728f13fcf265c20c480d34388001d528ce43190e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="expected-exceptions"></a>Expected Exceptions
Cet exemple montre comment intercepter des exceptions attendues lors de l'utilisation d'un client typé. Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice. Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Cet exemple illustre l'interception et la gestion des deux types d'exception attendues que les programmes corrects doivent gérer : `TimeoutException` et `CommunicationException`.  
  
 Les exceptions levées depuis les méthodes de communication sur un client [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sont soit attendues, soit inattendues. Les exceptions inattendues incluent les pannes catastrophiques comme `OutOfMemoryException` et les erreurs de programmation comme `ArgumentNullException` ou `InvalidOperationException`. En général, il n'y a aucune utilité à gérer des erreurs inattendues, donc vous ne devez pas les intercepter lors de l'appel à une méthode de communication du client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Les exceptions attendues depuis les méthodes de communication sur un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] incluent `TimeoutException`, `CommunicationException` et toute classe dérivée de `CommunicationException`. Celles-ci indiquent un problème pendant la communication qui peut être géré sans risque en abandonnant le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et en signalant un échec de communication. Étant donné que des facteurs externes peuvent provoquer ces erreurs dans toute application, les applications correctes doivent intercepter ces exceptions et récupérer lorsqu'elles se produisent.  
  
 Il existe plusieurs classes dérivées de `CommunicationException` qu'un client peut lever. Dans certains cas, les applications en interceptent et procèdent à un traitement spécial, mais laissent les autres être traitées comme `CommunicationException`. Cela peut être accompli en interceptant le type d'exception plus spécifique en premier, puis en interceptant `CommunicationException` dans une clause « catch » ultérieure.  
  
 Le code qui appelle une méthode de communication cliente doit intercepter `TimeoutException` et `CommunicationException`. Pour gérer de telles erreurs, il est possible d'abandonner le client et de signaler l'échec de communication.  
  
```  
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 Si une exception attendue se produit, le client peut ou ne peut pas être utilisable après-coup. Pour déterminer si le client est encore utilisable, vérifiez que la propriété `State` est `CommunicationState`.Opened. Si le client est toujours ouvert, il est encore utilisable. Sinon, vous devez abandonner le client et libérer toutes les références à ce dernier.  
  
> [!CAUTION]
>  Vous pouvez observer que bien souvent les clients qui ont une session ne sont plus utilisables après une exception, et les clients qui n'ont pas de session sont encore utilisables après une exception. Toutefois, cela n'est pas garanti, donc si vous souhaitez essayer de continuer à utiliser le client après une exception, votre application doit vérifier la propriété `State` pour vérifier le client est encore ouvert.  
  
 Lorsque vous exécutez l'exemple, les exceptions et réponses d'opération s'affichent dans la fenêtre de console du client.  
  
 Le processus client exécute deux scénarios, qui essaient tous deux d'appeler `Add` puis `Divide`. Le premier scénario simule un problème de réseau en abandonnant le client avant de faire appel à `Divide`. Le deuxième scénario provoque une condition de délai d'attente en définissant un délai d'attente trop court pour que la méthode se termine. Le processus client est censé donner le résultat suivant :  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
  
## <a name="see-also"></a>Voir aussi
