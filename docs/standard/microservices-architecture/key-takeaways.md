---
title: "Points importants à retenir"
description: "Architecture de microservices .NET pour les applications .NET en conteneur | Points importants à retenir"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2dbcfbe28f5461b7a40e8b0b49dbcf5e31490d70
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="key-takeaways"></a>Points importants à retenir

En guise de récapitulatif et de conclusion, voici les principaux points importants à retenir de ce guide.

**Avantages liés à l’utilisation de conteneurs** : les solutions à base de conteneurs offrent un avantage important en termes de réduction des coûts. En effet, les conteneurs sont une solution aux problèmes de déploiement liés au manque de dépendances dans les environnements de production. Les conteneurs améliorent considérablement les opérations DevOps et de production.

**Omniprésence annoncée des conteneurs** : les conteneurs Docker sont en passe de devenir de facto le standard dans le domaine du conteneur, recueillant l’adhésion des éditeurs les plus en vue dans les écosystèmes Windows et Linux. Parmi ceux-ci : Microsoft, Amazon AWS, Google et IBM. Dans un avenir proche, Docker sera probablement omniprésent dans les centres de données cloud et locaux.

**Des conteneurs comme unité de déploiement** : le conteneur Docker est en passe de devenir l’unité de déploiement standard des applications ou services basés sur un serveur.

**Microservices** : l’architecture de microservices est en passe de devenir l’approche privilégiée pour les applications stratégiques distribuées de nature complexe ou de grande ampleur basées sur divers sous-systèmes indépendants, qui prennent la forme de services autonomes. Dans une architecture basée sur des microservices, l’application s’appuie sur un ensemble de services qui peuvent être développés, testés, versionnés, déployés et mis à l’échelle de manière indépendante ; cela peut inclure n’importe quelle base de données autonome connexe.

**Conception pilotée par le domaine et SOA** : les modèles d’architecture de microservices sont un dérivé de l’architecture orientée services (SOA) et de la conception pilotée par le domaine (DDD). Quand vous concevez et développez des microservices pour des environnements avec des règles d’entreprise évolutives qui façonnent un domaine particulier, il est important de prendre en compte les approches et les modèles DDD.

**Problèmes liés aux microservices** : Les microservices offrent de nombreuses fonctionnalités intéressantes, comme le déploiement indépendant, des limites de sous-systèmes marquées et une diversité de technologies. Cependant, ils soulèvent aussi de nombreux problèmes nouveaux liés au développement d’applications distribuées, à savoir des modèles de données fragmentés et indépendants, une communication résiliente entre les microservices, la cohérence à terme et une complexité opérationnelle imputable à l’agrégation des informations de journalisation et de surveillance des divers microservices. Ces aspects introduisent un plus haut niveau de complexité par rapport à une application monolithique classique. De ce fait, les applications basées sur les microservices doivent être réservées à certains scénarios bien spécifiques. Tel est le cas des applications complexes et de grande échelle qui se composent de multiples sous-systèmes évolutifs ; dans ce cas, il est judicieux d’investir dans une architecture logicielle plus complexe, car elle offrira une meilleure agilité dans le temps et permettra de mieux maintenir l’application.

**Des conteneurs pour n’importe quelle application** : si les conteneurs s’avèrent pratiques pour les microservices, ils ne leur sont pas réservés. Les conteneurs peuvent aussi être utilisés avec les applications monolithiques, notamment des applications existantes basées sur le .NET Framework classique et modernisées via des conteneurs Windows. Les avantages offerts par Docker, comme l’élimination des nombreux problèmes liés au déploiement en production et le haut niveau de sophistication de ses environnements de développement et de test, valent pour divers types d’applications.

**CLI ou IDE** : les outils Microsoft vous laissent le choix quant à l’approche à adopter pour développer des applications .NET en conteneur. Vous pouvez ainsi choisir de les développer dans une interface de ligne de commande (CLI) et un environnement basé sur un éditeur via l’interface CLI Docker et Visual Studio Code. Vous pouvez aussi opter pour une approche axée sur un environnement de développement intégré (IDE) avec Visual Studio et ses fonctionnalités uniques pour Docker, telles que la possibilité de déboguer les applications multiconteneurs.

**Des applications cloud résilientes** : dans les systèmes basés sur le cloud et les systèmes distribués en général, il existe toujours un risque de défaillance partielle. Sachant que les clients et les services sont des processus (conteneurs) distincts, il peut arriver qu’un service ne puisse pas répondre à temps à une demande de client. Par exemple, un service peut être indisponible à la suite d’une défaillance partielle ou pour cause de maintenance ; le service peut être surchargé et répondre très lentement aux demandes ; ou il peut simplement ne pas être accessible pendant un bref laps de temps en raison de problèmes réseau. Par conséquent, une application basée sur le cloud doit parer ces défaillances et disposer d’une stratégie pour y répondre. Ces stratégies peuvent inclure des stratégies de nouvelles tentatives (renvoi des messages ou nouvelles tentatives des demandes) et l’implémentation des modèles de disjoncteur pour éviter la charge exponentielle des demandes répétées. Avant tout, les applications basées sur le cloud doivent intégrer des mécanismes résilients, qu’ils soient personnalisés ou basés sur une infrastructure cloud, comme les frameworks généraux d’orchestrateurs ou de bus de services.

**Sécurité** : notre monde moderne de conteneurs et de microservices peut présenter de nouvelles vulnérabilités. La sécurité de base des applications repose sur l’authentification et l’autorisation ; il existe plusieurs façons de les implémenter. Cependant, les conteneurs intègrent d’autres composants de sécurité essentiels qui profitent intrinsèquement à la sécurité des applications. Pour créer des applications plus sûres, il est essentiel de sécuriser la communication avec les autres applications et systèmes. Cela passe souvent par l’utilisation d’informations d’identification, de jetons, de mots de passe et d’autres types d’informations confidentielles, que l’on appelle souvent des secrets d’application. Une solution sécurisée doit suivre les bonnes pratiques de sécurité, comme le chiffrement des secrets en cours de transit ; le chiffrement des secrets au repos ; et la prévention des fuites accidentelles de secrets au moment d’être consommés par l’application finale. Ces secrets doivent être stockés et gardés en lieu sûr. Pour améliorer la sécurité, vous pouvez exploiter l’infrastructure de l’orchestrateur de votre choix ou une infrastructure cloud comme Azure Key Vault et profiter des moyens mis à la disposition du code d’application.

**Orchestrateurs** : les orchestrateurs à base de conteneurs comme ceux fournis par Azure Container Service (Kubernetes, Mesos DC/OS et Docker Swarm) et Azure Service Fabric sont indispensables aux applications basées sur des microservices et aux applications multiconteneurs qui affichent une grande complexité, des besoins de scalabilité et une évolution constante. Ce guide vous a présenté les orchestrateurs et leur rôle dans les solutions basées sur des microservices et des conteneurs. Si vos besoins en applications évoluent en direction des applications en conteneur complexes, il vous sera utile de rechercher des ressources supplémentaires pour découvrir plus en détail les orchestrateurs.

>[!div class="step-by-step"]
[Précédent] (secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)
