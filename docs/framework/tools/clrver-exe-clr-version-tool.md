---
title: Clrver.exe (outil CLR Version)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c09604c66b4628291b8e3c444d4c47c7aec8c026
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="clrverexe-clr-version-tool"></a>Clrver.exe (outil CLR Version)
L'outil de version CLR (Clrver.exe) rapporte toutes les versions installées du CLR (Common Runtime Language) sur l'ordinateur.  
  
 Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l'outil, utilisez l'invite de commandes développeur (ou l'invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 À l'invite de commandes, tapez le texte suivant :  
  
## <a name="syntax"></a>Syntaxe  
  
```  
clrver [option]  
```  
  
## <a name="options"></a>Options  
  
|Option|Description|  
|------------|-----------------|  
|`-all`|Affiche tous les processus de l'ordinateur qui utilisent le CLR.|  
|*pid*|Affiche la ou les versions du CLR utilisé par le processus qui a l'ID de processus spécifié (PID).|  
|`-?`|Affiche la syntaxe et les options de commande de l'outil.|  
  
## <a name="remarks"></a>Notes  
 Si vous appelez Clrver.exe sans option, il affiche toutes les versions de CLR installées. Si vous spécifiez PID pour un autre utilisateur, vous devez disposer des autorisations d'administrateur pour obtenir les informations de version.  
  
> [!NOTE]
>  Dans Windows Vista et version ultérieure, le contrôle de compte d'utilisateur détermine les privilèges d'un utilisateur. Si vous êtes membre du groupe Administrateurs intégrés, deux jetons d'accès au moment de l'exécution vous sont assignés : un jeton d'accès utilisateur standard et un jeton d'accès administrateur. Par défaut, vous êtes dans le rôle d'utilisateur standard. Pour exécuter le code qui requiert une autorisation d'administration, vous devez d'abord élever vos privilèges d'utilisateur standard à administrateur. Cela peut être effectué au démarrage de l'invite de commandes en cliquant avec le bouton droit sur l'icône de l'invite de commandes et en indiquant que vous voulez l'exécuter en tant qu'administrateur.  
  
 La tentative afin de déterminer la version du CLR pour des processus SYSTÈME, SERVICE LOCAL et SERVICE RÉSEAU entraîne un message indiquant que le PID n'existe pas.  
  
## <a name="examples"></a>Exemples  
 La commande suivante affiche toutes les versions du CLR installée sur l'ordinateur.  
  
 `clrver`  
  
 La commande suivante affiche la version du CLR utilisée par le processus 128.  
  
 `clrver 128`  
  
 La commande suivante affiche tous les processus gérés et la version du CLR qu'ils utilisent.  
  
 `Clrver -all`  
  
## <a name="see-also"></a>Voir aussi  
 [Outils](../../../docs/framework/tools/index.md)  
 [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
