---
title: "Sécurité WebBrowser"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3985fc9916b3e95e650502ef1f8dc301363b1f90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="webbrowser-security"></a>Sécurité WebBrowser
Le <xref:System.Windows.Forms.WebBrowser> contrôle est conçu pour fonctionner en confiance totale uniquement. Le contenu HTML affiché dans le contrôle peut provenir de serveurs Web externes et peut contenir du code non managé sous la forme de scripts ou de contrôles Web. Si vous utilisez la <xref:System.Windows.Forms.WebBrowser> contrôle dans ce cas, le contrôle n’est pas moins sécurisé qu’Internet Explorer, mais managé <xref:System.Windows.Forms.WebBrowser> contrôle n’empêche pas ce code non managé en cours d’exécution.  
  
 Pour plus d’informations sur les problèmes de sécurité relatifs à ActiveX sous-jacent `WebBrowser` du contrôle, consultez [contrôle WebBrowser](http://go.microsoft.com/fwlink/?LinkId=198812).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.WebBrowser>  
 [Vue d’ensemble du contrôle WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [WebBrowser, contrôle](http://go.microsoft.com/fwlink/?LinkId=198812)
