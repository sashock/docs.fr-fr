---
title: "CorDebugChainReason, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugChainReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugChainReason
helpviewer_keywords:
- CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1951983c9d167862169bd6178dc65693d724dc0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugchainreason-enumeration"></a>CorDebugChainReason, énumération
Indique la ou les raisons de la mise en route d'une chaîne d'appels.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugChainReason {  
    CHAIN_NONE              = 0x000,  
    CHAIN_CLASS_INIT        = 0x001,  
    CHAIN_EXCEPTION_FILTER  = 0x002,  
    CHAIN_SECURITY          = 0x004,  
    CHAIN_CONTEXT_POLICY    = 0x008,  
    CHAIN_INTERCEPTION      = 0x010,  
    CHAIN_PROCESS_START     = 0x020,  
    CHAIN_THREAD_START      = 0x040,  
    CHAIN_ENTER_MANAGED     = 0x080,  
    CHAIN_ENTER_UNMANAGED   = 0x100,  
    CHAIN_DEBUGGER_EVAL     = 0x200,  
    CHAIN_CONTEXT_SWITCH    = 0x400,  
    CHAIN_FUNC_EVAL         = 0x800  
} CorDebugChainReason;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`CHAIN_NONE`|Aucune chaîne d'appel n'a été démarrée.|  
|`CHAIN_CLASS_INIT`|La chaîne a été démarrée par un constructeur.|  
|`CHAIN_EXCEPTION_FILTER`|La chaîne a été démarrée par un filtre d'exception.|  
|`CHAIN_SECURITY`|La chaîne a été démarrée par du code qui applique la sécurité.|  
|`CHAIN_CONTEXT_POLICY`|La chaîne a été démarrée par une stratégie de contexte.|  
|`CHAIN_INTERCEPTION`|Non utilisé.|  
|`CHAIN_PROCESS_START`|Non utilisé.|  
|`CHAIN_THREAD_START`|La chaîne a été démarrée par le démarrage d'une exécution de thread.|  
|`CHAIN_ENTER_MANAGED`|La chaîne a été démarrée par une entrée dans le code managé.|  
|`CHAIN_ENTER_UNMANAGED`|La chaîne a été démarrée par une entrée dans le code non managé.|  
|`CHAIN_DEBUGGER_EVAL`|Non utilisé.|  
|`CHAIN_CONTEXT_SWITCH`|Non utilisé.|  
|`CHAIN_FUNC_EVAL`|La chaîne a été démarrée par une évaluation de fonction.|  
  
## <a name="remarks"></a>Notes  
 Utilisez le [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) méthode pour déterminer les raisons de l’initiation d’une chaîne d’appel.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
