---
title: "ROW (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "ESQL"
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# ROW (Entity SQL)
Construit des enregistrements anonymes structurellement typés à partir d'une ou plusieurs valeurs.  
  
## Syntaxe  
  
```  
  
ROW (expression [ AS alias ] [,...] )  
```  
  
## Arguments  
 `expression`  
 Toute expression de requête valide qui retourne une valeur à construire dans un type de ligne.  
  
 `alias`  
 Spécifie un alias pour la valeur spécifiée dans un type de ligne. Si aucun alias n'est fourni, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] essaie de générer un alias en fonction des règles de génération d'alias [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## Valeur de retour  
 Type de ligne.  
  
## Notes  
 Les constructeurs de ligne s'avèrent utiles dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pour construire des enregistrements anonymes structurellement types à partir d'une ou plusieurs valeurs. Le type de résultat d'un constructeur de ligne est un type de ligne dont les types de champ correspondent aux types des valeurs qui ont servi à construire la ligne. Par exemple, l'expression suivante construit une valeur de type `Record(a int, b string, c int)`.  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 Si vous ne fournissez pas d'alias pour une expression contenue dans un constructeur de ligne, Entity Framework essaie d'en générer un. Pour plus d'informations, voir la section « Règles d'alias » de la rubrique [Identificateurs](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).  
  
 Les règles suivantes s'appliquent à l'utilisation d'alias dans les expressions d'un constructeur de ligne :  
  
-   les expressions contenues dans un constructeur de ligne ne peuvent pas faire référence aux autres alias du même constructeur ;  
  
-   deux expressions contenues dans un même constructeur de ligne ne peuvent pas avoir le même alias.  
  
 Pour plus d’informations sur les constructeurs de requête, consultez [Construction de types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## Exemple  
 La requête Entity SQL ci\-dessous utilise l'opérateur ROW pour construire des enregistrements anonymes structurellement typés. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## Voir aussi  
 [Construction de types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)   
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [Définitions de types](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)