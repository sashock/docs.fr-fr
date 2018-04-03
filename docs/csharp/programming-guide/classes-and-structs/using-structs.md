---
title: Utilisation de structs (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 94181c42ce913dc76c9a074e4bcbb8240764c896
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-structs-c-programming-guide"></a>Utilisation de structs (Guide de programmation C#)
Le type `struct` est approprié pour représenter des objets légers tels que `Point`, `Rectangle`et `Color`. Bien qu’il soit aussi pratique de représenter un point comme [classe](../../../csharp/language-reference/keywords/class.md) avec des [propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), un [struct](../../../csharp/language-reference/keywords/struct.md) peut être plus efficace dans certains scénarios. Par exemple, si vous déclarez un tableau de 1 000 objets `Point` , vous devez allouer de la mémoire supplémentaire pour faire référence à chacun des objets. Dans ce cas, un struct est moins onéreux. Étant donné que le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] contient un objet appelé <xref:System.Drawing.Point>, le struct dans cet exemple est nommé à la place « CoOrds ».  
  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 Définir un constructeur par défaut (sans paramètre) pour un struct constitue une erreur. Vous ne devez pas non plus initialiser un champ d'instance dans le corps d'un struct. Vous pouvez initialiser les membres du struct en externe accessible uniquement à l’aide d’un constructeur paramétrable, implicite, constructeur par défaut, un [initialiseur d’objet](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md), ou en accédant individuellement aux membres après le struct est déclaré. Tout membre privé ou inaccessible nécessite l’utilisation de constructeurs exclusivement.
  
 Lorsque vous créez un struct à l’aide de l'opérateur [new](../../../csharp/language-reference/keywords/new.md) (opérateur), celui-ci est créé et le constructeur approprié est appelé en fonction de la [signature du constructeur](../../../csharp/programming-guide/classes-and-structs/constructors.md#constructor-syntax). Contrairement aux classes, les structs peuvent être instanciés sans avoir recours à l’opérateur `new` . Dans un tel cas, il n’y a pas d’appel au constructeur, ce qui rend l’allocation plus efficace. Toutefois, les champs ne sont pas assignés et l’objet ne peut pas être utilisé tant que tous les champs ne sont pas initialisés. Cela inclut l’incapacité à obtenir ou définir des valeurs de propriétés implémentées automatiquement.
 
 Si vous instanciez un objet struct à l’aide de la valeur par défaut, le constructeur sans paramètre, tous les membres sont affectées en fonction de leur [les valeurs par défaut](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md).
  
 Lorsque vous écrivez un constructeur avec des paramètres pour un struct, vous devez explicitement initialiser tous les membres ; dans le cas contraire, un ou plusieurs membres restent non assignés et le struct ne peut pas être utilisé, produisant l’erreur du compilateur CS0171.  
  
 Il n'existe pas d'héritage pour un struct comme il en existe pour une classe. Un struct ne peut pas hériter d'un autre struct ou d'une classe ; il ne peut pas non plus servir de base à une classe. Toutefois, les structs héritent de la classe de base <xref:System.Object>. Un struct peut implémenter des interfaces exactement de la même manière que les classes.  
  
 Vous ne pouvez pas déclarer une classe à l’aide du mot clé `struct`. En C#, les classes et les structs ont une sémantique différente. Un struct est un type valeur, alors qu'une classe est un type référence. Pour plus d’informations, consultez [Types valeur](../../../csharp/language-reference/keywords/value-types.md).  
  
 Sauf si vous avez besoin d’une sémantique de type référence, une petite classe peut être gérée plus efficacement par le système si vous la déclarez plutôt sous forme de struct.  
  
## <a name="example-1"></a>Exemple 1  
  
### <a name="description"></a>Description  
 Cet exemple illustre l’initialisation du type `struct` à l’aide des constructeurs par défaut et des constructeurs paramétrables.  
  
### <a name="code"></a>Code  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]  
  
## <a name="example-2"></a>Exemple 2  
  
### <a name="description"></a>Description  
 Cet exemple montre une caractéristique propre aux structs. Il crée un objet CoOrds sans utiliser l’opérateur `new` . Si vous remplacez le mot `struct` par le mot `class`, le programme ne peut pas se compiler.  
  
### <a name="code"></a>Code  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md)
