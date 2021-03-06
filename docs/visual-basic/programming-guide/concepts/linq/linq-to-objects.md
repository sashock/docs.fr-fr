---
title: LINQ to Objects (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c2a48e792c656a84c07730b67f734f6b539ab97d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="linq-to-objects-visual-basic"></a>LINQ to Objects (Visual Basic)
« LINQ to Objects » fait référence à l’utilisation directe de requêtes LINQ avec n’importe quelle collection <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>, sans utiliser de fournisseur LINQ ou d’API intermédiaire comme [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) ou [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13). Vous pouvez utiliser LINQ pour interroger des collections énumérables telles que <xref:System.Collections.Generic.List%601>, <xref:System.Array> ou <xref:System.Collections.Generic.Dictionary%602>. La collection peut être définie par l’utilisateur ou retournée par une API du .NET Framework.  
  
 Fondamentalement, LINQ to Objects représente une nouvelle approche des collections. Auparavant, vous deviez écrire des boucles `For Each` complexes pour spécifier comment récupérer les données d'une collection. Avec l’approche LINQ, vous écrivez du code déclaratif qui décrit ce que vous voulez récupérer.  
  
 De plus, les requêtes LINQ offrent trois avantages principaux par rapport aux boucles `For Each` classiques :  
  
1.  Elles sont plus concises et lisibles, en particulier durant le filtrage de plusieurs conditions.  
  
2.  Elles fournissent de puissantes fonctionnalités de filtrage, de classement et de regroupement avec un minimum de code d'application.  
  
3.  Elles peuvent être portées vers d'autres sources de données avec peu ou pas de changements.  
  
 En général, plus l’opération que vous voulez effectuer sur les données est complexe, plus vous avez intérêt à utiliser LINQ à la place des techniques d’itération classiques.  
  
 Cette section a pour objectif de montrer l’approche basée sur LINQ avec quelques exemples sélectionnés. Elle ne se veut pas exhaustive.  
  
## <a name="in-this-section"></a>Dans cette section  
 [LINQ et chaînes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 Explique comment LINQ peut être utilisé pour interroger et transformer des chaînes et des collections de chaînes. Inclut également des liens vers les rubriques qui présentent ces principes.  
  
 [LINQ et réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 Contient un lien vers un exemple qui montre comment LINQ utilise la réflexion.  
  
 [LINQ et répertoires de fichiers (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 Explique comment LINQ peut être utilisé pour interagir avec les systèmes de fichiers. Inclut également des liens vers les rubriques qui présentent ces concepts.  
  
 [Comment : interroger un ArrayList avec LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 Montre comment interroger une ArrayList en C#.  
  
 [Comment : ajouter des méthodes personnalisées pour les requêtes LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 Explique comment étendre l'ensemble des méthodes utilisables pour les requêtes LINQ en ajoutant des méthodes d'extension à l'interface <xref:System.Collections.Generic.IEnumerable%601>.  
  
 [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Fournit des liens vers des rubriques qui présentent LINQ, ainsi que des exemples de code effectuant des requêtes.
