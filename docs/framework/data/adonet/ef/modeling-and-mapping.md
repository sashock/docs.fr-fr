---
title: "Modélisation et mappage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
caps.latest.revision: "7"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0782d75aa44557ef87f1d59757b0d60873d8a949
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="modeling-and-mapping"></a>Modélisation et mappage
Dans [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], vous pouvez définir le modèle conceptuel, le modèle de stockage et le mappage entre les deux de la façon la plus appropriée pour votre application. Les outils Entity Data Model dans [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] vous permettent de créer un.[ fichier edmx](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4) à partir d’une base de données ou un modèle graphique et puis mettez à jour ce fichier lorsque la base de données ou le modèle change.  
  
 Depuis Entity Framework 4.1, vous pouvez également créer un modèle par programme à l’aide du développement Code First. Il existe deux scénarios différents pour le développement Code First. Dans les deux cas, le développeur définit un modèle lors du codage des définitions de classe .NET Framework, puis spécifie éventuellement un mappage supplémentaire ou une configuration supplémentaire à l'aide des annotations de données ou de l'API Fluent.  
  
 Pour plus d’informations, consultez [création et mappage d’un modèle conceptuel](http://go.microsoft.com/fwlink/?LinkId=235016).  
  
 Vous pouvez également utiliser l’outil EDM Generator, qui est inclus dans le [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. EdmGen.exe génère les fichiers .csdl, .ssdl et .msl d'une source de données existante. Vous pouvez également créer manuellement le modèle et mapper le contenu. Pour plus d’informations, consultez [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).
