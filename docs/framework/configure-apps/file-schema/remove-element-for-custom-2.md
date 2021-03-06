---
title: "&lt;supprimer&gt; élément de NameValueSectionHandler et DictionarySectionHandler"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 27b01120cb279dc23b3b081e35f17addc6d1897d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Supprimer >, élément pour NameValueSectionHandler et DictionarySectionHandler

Supprime un paramètre défini précédemment.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Supprimer >**

## <a name="syntax"></a>Syntaxe

```xml
<add remove="key" />
```

## <a name="attribute"></a>Attribut

|           | Description |
| --------- | ----------- |
| **key**   | Attribut requis.<br><br>Spécifie le nom du paramètre à supprimer. |

## <a name="parent-element"></a>Élément parent

| Élément | Description |
| ------- | ------------|
| [**\<sectionName >** élément](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | Définit les paramètres pour les sections de configuration personnalisées qui utilisent le <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler> classes. |

## <a name="child-elements"></a>Éléments enfants

Aucun.

## <a name="remarks"></a>Notes

Vous pouvez utiliser la  **\<Supprimer >** élément à supprimer les paramètres de votre application qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le  **\<Supprimer >** élément dans un fichier de configuration pour supprimer les paramètres définis précédemment dans le fichier de configuration machine.

Le code suivant du fichier de configuration machine déclare la section  **\<MaSection >** et ajoute deux paramètres, `key1` et `key2`, à celui-ci :

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

Le code du fichier de configuration application suivant supprime la `key2` définition à partir de  **\<MaSection >**:

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* les fichiers qui ne sont pas au niveau du répertoire d’application.

## <a name="see-also"></a>Voir aussi

[Schéma de fichier de configuration pour le .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
