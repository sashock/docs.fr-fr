---
title: "Qualification des types .NET en vue d'une interopérabilité"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0f08f2de4a8f402b2c9c41908aa4bcfe2730fef5
ms.sourcegitcommit: d95a91d685565f4d95c8773b558752864a6a3d7e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2018
---
# <a name="qualifying-net-types-for-interoperation"></a>Qualification des types .NET en vue d'une interopérabilité
Si vous envisagez d’exposer les types d’un assembly à des applications COM, prenez en compte les exigences COM Interop au moment de la conception. Les types managés (classe, interface, structure et énumération) s’intègrent parfaitement aux types COM lorsque vous respectez les consignes suivantes :  
  
-   Les classes doivent implémenter les interfaces de manière explicite.  
  
     Même si COM Interop fournit un mécanisme permettant de générer automatiquement une interface contenant tous les membres de la classe et de sa classe de base, il est fortement recommandé de fournir des interfaces explicites. L’interface générée automatiquement est appelée « interface de classe ». Pour connaître les instructions, consultez [présentation de l’interface de classe](com-callable-wrapper.md#introducing-the-class-interface).  
  
     Vous pouvez utiliser Visual Basic, c# et C++ pour incorporer des définitions d’interface dans votre code, au lieu de devoir utiliser le langage IDL (Interface Definition) ou son équivalent. Pour plus d’informations sur la syntaxe, consultez la documentation relative à votre langage.  
  
-   Les types managés doivent être publics.  
  
     Seuls les types publics d’un assembly sont inscrits et exportés vers la bibliothèque de types. Par conséquent, seuls les types publics sont visibles par COM.  
  
     Les types managés exposent des fonctionnalités à un autre code managé qui peut ne pas être exposé à COM. Par exemple, les constructeurs paramétrables, les méthodes statiques et les champs constants ne sont pas exposés aux clients COM. De plus, comme le runtime marshale les données d’un type à un autre, les données peuvent être copiées ou transformées.  
  
-   Les méthodes, les propriétés, les champs et les événements doivent être publics.  
  
     Les membres des types publics doivent également être publics pour être visibles par COM. Vous pouvez restreindre la visibilité d’un assembly, d’un type public ou de membres publics d’un type public en appliquant <xref:System.Runtime.InteropServices.ComVisibleAttribute>. Par défaut, tous les membres et types publics sont visibles.  
  
-   Les types doivent avoir un constructeur public par défaut pour être activés dans COM.  
  
     Les types publics managés sont visibles par COM. Toutefois, sans constructeur public par défaut (constructeur sans arguments), les clients COM ne peuvent pas créer le type. Les clients COM peuvent toujours utiliser le type s’il est activé par d’autres moyens.  
  
-   Les types ne peuvent pas être abstraits.  
  
     Ni les clients COM ni les clients .NET ne peuvent créer de types abstraits.  
  
 Lors de l’exportation vers COM, la hiérarchie d’héritage d’un type managé est aplatie. Le contrôle de version est également différent dans les environnements managés et non managés. Les types exposés à COM n’ont pas les mêmes caractéristiques de contrôle de version que les autres types managés.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>  
 [Exposition de composants .NET Framework à COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Présentation de l’Interface de classe](https://msdn.microsoft.com/library/733c0dd2-12e5-46e6-8de1-39d5b25df024(v=vs.100))  
 [Application d’attributs d’interopérabilité](../../../docs/framework/interop/applying-interop-attributes.md)  
 [Empaquetage d'un assembly pour COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
