---
title: "Navigation dans la collection de nœuds à l’aide de XPathNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d1bca725d20ec35ef7d6f60fce131f9d9c951650
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="node-set-navigation-using-xpathnavigator"></a>Navigation dans la collection de nœuds à l’aide de XPathNavigator
Vous pouvez parcourir les nœuds d'un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> à l'aide des méthodes de navigation entre les collections de nœuds de la classe <xref:System.Xml.XPath.XPathNavigator>. Vous pouvez parcourir tous ces nœuds ou certaines collections de nœuds retournées par l'une des méthodes de sélection de la classe <xref:System.Xml.XPath.XPathNavigator>.  
  
## <a name="element-node-set-navigation"></a>Navigation entre les collections de nœuds d'éléments  
 La classe <xref:System.Xml.XPath.XPathNavigator> fournit plusieurs méthodes de navigation entre les nœuds d'élément. Le tableau suivant indique les méthodes de navigation disponibles et donne une description de leur mode de déplacement, mais ne comprend pas les méthodes permettant de naviguer entre les nœuds d'attribut et d'espace de noms.  
  
 Pour plus d’informations sur la sélection de nœuds dans un objet <xref:System.Xml.XPath.XPathNavigator>, consultez [Sélection, évaluation et mise en correspondance de données XML à l’aide de XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md). Pour plus d’informations sur la navigation dans les nœuds d’attribut et d’espace de noms, consultez [Navigation entre les nœuds d’attribut et d’espace de noms à l’aide de XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers la même position que l'objet <xref:System.Xml.XPath.XPathNavigator> spécifié.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers un nœud enfant du nœud actuel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers le premier nœud frère du nœud actuel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers le premier nœud enfant du nœud actuel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers l'élément spécifié dans l'ordre du document.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers le nœud possédant un attribut de type `ID` avec une valeur correspondant à l'objet <xref:System.String> donné.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers le nœud frère suivant du nœud actuel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers le nœud parent du nœud actuel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers le nœud frère précédent du nœud actuel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers le nœud racine du document XML.|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a>Commentaires et instructions de traitement de la navigation entre les nœuds  
 Les méthodes suivantes de la classe <xref:System.Xml.XPath.XPathNavigator> sont valide pour le déplacement de commentaires ou d'instructions de traitement d'autres nœuds dans un document XML.  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Traitement des données XML à l’aide du modèle de données XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Navigation entre les nœuds d’attribut et d’espace de noms à l’aide de XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [Extraction de données XML à l’aide de XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 [Accès à des données XML fortement typées à l’aide de XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
