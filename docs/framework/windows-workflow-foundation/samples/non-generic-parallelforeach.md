---
title: "ParallelForEach non générique"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eb019aed7fce267506ddb495609df5a80a8f8d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="non-generic-parallelforeach"></a>ParallelForEach non générique
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]est fourni dans sa boîte à outils, un ensemble d’activités de flux de contrôle, y compris <xref:System.Activities.Statements.ParallelForEach%601>, ce qui permet l’itération au sein de <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` collections.  
  
 <xref:System.Activities.Statements.ParallelForEach%601>nécessite son <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> propriété de type <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`. Cela empêche les utilisateurs d’itérer au sein des structures de données qui implémentent <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` interface (par exemple, <xref:System.Collections.ArrayList>). La version non générique de <xref:System.Activities.Statements.ParallelForEach%601> passe outre cette spécification, aux dépens d'un runtime plus complexe afin de garantir la compatibilité des types des valeurs dans la collection.  
  
 Cet exemple montre comment implémenter une activité <xref:System.Activities.Statements.ParallelForEach%601> non générique et son concepteur. Cette activité peut être utilisée pour itérer au sein de <xref:System.Collections.ArrayList>.  
  
## <a name="parallelforeach-activity"></a>Activité ParallelForEach  
 L'instruction C#/VB `foreach` énumère les éléments d'une collection, exécutant une instruction incorporée pour chaque élément de la collection. Les activités [!INCLUDE[wf1](../../../../includes/wf1-md.md)] équivalentes sont <xref:System.Activities.Statements.ForEach%601> et <xref:System.Activities.Statements.ParallelForEach%601>. L'activité <xref:System.Activities.Statements.ForEach%601> contient une liste de valeurs et un corps. Au moment de l'exécution, la liste fait l'objet d'une itération et le corps est exécuté pour chaque valeur de la liste.  
  
 <xref:System.Activities.Statements.ParallelForEach%601> a un <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> afin que l'activité <xref:System.Activities.Statements.ParallelForEach%601> puisse se terminer tôt si l'évaluation du <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> retourne la valeur `true`. Le <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> est évalué à l'issue de chaque itération.  
  
 Dans la plupart des cas, la version générique de l'activité doit être la solution par défaut, car elle couvre la plupart des scénarios dans lesquels elle est utilisée, et fournit la vérification des types au moment de la compilation. La version non générique peut être utilisée pour itérer au sein de types qui implémentent l'interface <xref:System.Collections.IEnumerable> non générique.  
  
## <a name="class-definition"></a>Définition de classes  
 L'exemple de code suivant illustre la définition d'une activité `ParallelForEach` non générique.  
  
```  
[ContentProperty("Body")]  
public class ParallelForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    public Activity<bool> CompletionCondition  
    [DefaultValue(null)]  
    [DependsOn("CompletionCondition")]  
    ActivityAction<object> Body { get; set; }   
}  
```  
  
 Body (facultatif)  
 <xref:System.Activities.ActivityAction> de type <xref:System.Object>, qui est exécuté pour chaque élément de la collection. Chaque élément individuel est passé dans le corps (Body) via sa propriété Argument.  
  
 Values (facultatif)  
 Collection des éléments sur lesquels est effectuée l'itération. La vérification que tous les éléments de la collection sont de types compatibles est effectuée au moment de l'exécution.  
  
 CompletionCondition (facultatif)  
 La propriété <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> est évaluée à l'issue de toute itération. Si sa valeur est `true`, les itérations en attente planifiées sont annulées. Si cette propriété n'est pas définie, toutes les activités de la collection Branches s'exécutent jusqu'à la fin.  
  
## <a name="example-of-using-parallelforeach"></a>Exemple d'utilisation de ParallelForEach  
 Le code suivant montre comment utiliser l'activité ParallelForEach dans une application.  
  
```  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ParallelForEach  
    {  
       Values = new InArgument<IEnumerable>(c=> names),  
       Body = new ActivityAction<object>   
       {                          
           Argument = iterationVariable,  
           Handler = new WriteLine  
           {  
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))  
           }  
       }  
   };  
```  
  
## <a name="parallelforeach-designer"></a>Concepteur ParallelForEach  
 Le concepteur d'activités de l'exemple est semblable, en apparence, au concepteur fourni pour l'activité <xref:System.Activities.Statements.ParallelForEach%601> intégrée. Le concepteur s’affiche dans la boîte à outils dans le **exemples**, **activités Non génériques** catégorie. Le concepteur est nommé **ParallelForEachWithBodyFactory** dans la boîte à outils, car l’activité expose un <xref:System.Activities.Presentation.IActivityTemplateFactory> dans la boîte à outils qui crée l’activité avec correctement configuré <xref:System.Activities.ActivityAction>.  
  
```  
public sealed class ParallelForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ParallelForEach()  
        {  
            Body = new ActivityAction<object>()  
            {  
                Argument = new DelegateInArgument<object>()  
                {  
                    Name = "item"  
                }  
            }  
        };  
    }  
}  
```  
  
#### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
1.  Définissez le projet de votre choix comme projet de démarrage de la solution.  
  
    1.  **CodeTestClient** montre comment utiliser l’activité à l’aide de code.  
  
    2.  **DesignerTestClient** montre comment utiliser l’activité dans le concepteur.  
  
2.  Générez et exécutez le projet.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
