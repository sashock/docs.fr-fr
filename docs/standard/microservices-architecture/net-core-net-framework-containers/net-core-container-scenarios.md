---
title: Quand choisir .NET Core pour les conteneurs Docker
description: Architecture de microservices .NET pour les applications .NET en conteneur | Quand choisir .NET Core pour les conteneurs Docker
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d9489bca5ac69046818a1809b2f3082baea1eaa8
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2018
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Quand choisir .NET Core pour les conteneurs Docker

La modularité et la légèreté de .NET Core en font l’outil idéal pour les conteneurs. Quand vous déployez ou démarrez un conteneur, son image est beaucoup plus petite avec .NET Core qu’avec le .NET Framework. En revanche, pour utiliser le .NET Framework pour un conteneur, vous devez baser votre image sur l’image Windows Server Core, qui est beaucoup plus lourde que les images Windows Nano Server ou Linux que vous utilisez pour .NET Core.

De plus, .NET Core étant multiplateforme, vous pouvez déployer des applications serveur avec des images de conteneur Linux ou Windows. Cependant, si vous utilisez le .NET Framework classique, vous pouvez déployer uniquement des images basées sur Windows Server Core.

Vous trouverez ci-dessous une explication plus détaillée des raisons de choisir .NET Core.

## <a name="developing-and-deploying-cross-platform"></a>Développement et déploiement multiplateformes

Il va de soi que si votre objectif est de disposer d’une application (application ou service web) capable de s’exécuter sur plusieurs plateformes prises en charge par Docker (Linux et Windows), .NET Core est le bon choix, car le .NET Framework prend uniquement en charge Windows.

.NET Core prend aussi en charge macOS comme plateforme de développement. Cependant, quand vous déployez des conteneurs sur un hôte Docker, celui-ci doit (à ce moment-là) être basé sur Windows ou Linux. Par exemple, dans un environnement de développement, vous pouvez utiliser une machine virtuelle Linux s’exécutant sur un Mac.

[Visual Studio](https://www.visualstudio.com/) propose un environnement de développement intégré (IDE) pour Windows et prend en charge le développement Docker. 

[Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/) est un IDE (évolution de Xamarin Studio) qui s’exécute dans macOS et qui prend en charge Docker depuis la mi-année 2017.

Vous pouvez aussi utiliser [Visual Studio Code](https://code.visualstudio.com/) (VS Code) sur macOS, Linux et Windows. VS Code prend entièrement en charge .NET Core, notamment IntelliSense et le débogage. VS Code étant un éditeur léger, vous pouvez l’utiliser pour développer des applications en conteneur sur Mac en association avec l’interface CLI Docker et les [outils de d’interface de ligne de commande (CLI) .NET Core](../../../core/tools/index.md). Vous pouvez aussi cibler .NET Core avec la plupart des éditeurs tiers comme Sublime, Text, Emacs, vi et le projet open source OmniSharp, qui assure une prise en charge d’IntelliSense pour les langages .NET. En plus des IDE et des éditeurs, vous pouvez utiliser l’interface CLI .NET Core pour toutes les plateformes prises en charge.

## <a name="using-containers-for-new-green-field-projects"></a>Utilisation de conteneurs pour les nouveaux projets (« green-field »)

Les conteneurs sont couramment utilisés avec une architecture de microservices, même s’ils peuvent aussi servir à organiser en conteneurs les services ou applications web qui suivent un modèle d’architecture. Vous pouvez utiliser le .NET Framework dans les conteneurs Windows, mais par sa modularité et sa légèreté, .NET Core est parfait pour les conteneurs et les architectures de microservices. Quand vous créez et déployez un conteneur, son image est beaucoup plus petite avec .NET Core qu’avec le .NET Framework.

## <a name="creating-and-deploying-microservices-on-containers"></a>Création et déploiement de microservices dans des conteneurs

Vous pouvez utiliser le .NET Framework classique pour créer des applications basées sur des microservices (sans conteneurs) en suivant des processus ordinaires. De cette façon, comme .NET Framework est déjà installé et partagé entre les processus, ceux-ci démarrent rapidement du fait de leur légèreté. En revanche, si vous utilisez des conteneurs, l’image pour le .NET Framework classique est aussi basée sur Windows Server Core, ce qui la rend trop lourde pour une approche de microservices dans des conteneurs.

A contrario, .NET Core est le meilleur choix si vous adoptez un système orienté microservices basé sur des conteneurs, car .NET Core se est léger. De plus, les images de conteneur qui lui sont associées, que ce soit l’image Linux ou l’image Windows Nano, sont légères et petites, ce qui permet aux conteneurs de démarrer rapidement.

Un microservice doit être le petit possible de façon à être léger pendant son exécution, à offrir un faible encombrement, à présenter un contexte limité réduit, à ne pas être une source de problèmes et à démarrer et à s’arrêter rapidement. Pour remplir ces conditions, vous devez utiliser des images de conteneur petites et rapides à instancier à l’instar de l’image de conteneur .NET Core.

Une architecture de microservices permet aussi de combiner des technologies au-delà des limites d’un service. Une migration progressive vers .NET Core devient ainsi possible pour les nouveaux microservices qui fonctionnent conjointement avec d’autres microservices ou services développés avec Node.js, Python, Java, GoLang ou d’autres technologies.

## <a name="deploying-high-density-in-scalable-systems"></a>Déploiement de la haute densité dans des systèmes scalables

Quand votre système basé sur des conteneurs a besoin d’une densité, d’une granularité et de performances optimales, .NET Core et ASP.NET Core constituent les meilleures options. ASP.NET Core est jusqu’à dix fois plus rapide qu’ASP.NET dans le .NET Framework classique et il devance les autres technologies courantes pour les microservices, telles que les servlets Java, Go et Node.js.

Cela est particulièrement intéressant pour les architectures de microservices dans lesquelles plusieurs centaines de microservices (conteneurs) peuvent s’exécuter simultanément. Avec des images ASP.NET Core (basées sur le runtime .NET Core) sur Linux ou Windows Nano, vous pouvez exécuter votre système avec beaucoup moins de serveurs ou de machines virtuelles, ce qui en fin de compte vous permet de réaliser des économies en infrastructure et hébergement.


>[!div class="step-by-step"]
[Précédent] (general-guidance.md) [Suivant] (net-framework-container-scenarios.md)
