---
title: "Guide pratique pour contrôler les préfixes d'espaces de noms (C#) (LINQ to XML)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fc8d652c54be62fdf38e0aa05fcf6a81af3f719b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a>Guide pratique pour contrôler les préfixes d'espaces de noms (C#) (LINQ to XML)
Cette rubrique décrit comment contrôler les préfixes d’espaces de noms lors de la sérialisation d’une arborescence XML.  
  
 Dans de nombreux cas, il n'est pas nécessaire de contrôler les préfixes d'espaces de noms.  
  
 Cependant, certains outils de programmation XML requièrent un contrôle spécifique des préfixes d'espaces de noms. Par exemple, vous pourriez manipuler une feuille de style XSLT ou un document XAML qui contient des expressions XPath incorporées qui font référence à des préfixes d'espaces de noms spécifiques ; dans ce cas, il est important que le document soit sérialisé avec ces préfixes spécifiques.  
  
 Il s'agit de la raison la plus courante de contrôle des préfixes d'espaces de noms.  
  
 Le contrôle des préfixes d'espaces de noms peut également s'avérer nécessaire lorsque vous souhaitez que les utilisateurs modifient le document XML manuellement et que vous souhaitez créer des préfixes d'espaces de noms faciles à taper pour l'utilisateur. Par exemple, vous pourriez générer un document XSD. Les conventions applicables aux schémas suggèrent que vous utilisiez `xs` ou `xsd` comme préfixe de l'espace de noms de schéma.  
  
 Pour contrôler les préfixes d'espaces de noms, vous devez insérer des attributs qui déclarent des espaces de noms. Si vous déclarez les espaces de noms avec des préfixes spécifiques, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tentera d'honorer les préfixes d'espaces de noms lors de la sérialisation.  
  
 Pour créer un attribut qui déclare un espace de noms avec un préfixe, vous devez créer un attribut où l'espace de noms du nom de l'attribut est <xref:System.Xml.Linq.XNamespace.Xmlns%2A> et le nom de l'attribut est le préfixe d'espace de noms. La valeur de l'attribut est l'URI de l'espace de noms.  
  
## <a name="example"></a>Exemple  
 Cet exemple déclare deux espaces de noms. Il spécifie que l’espace de noms `http://www.adventure-works.com` a le préfixe `aw` et que l’espace de noms `www.fourthcoffee.com` a le préfixe `fc`.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des espaces de noms XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
