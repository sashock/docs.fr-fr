---
title: "Nouveautés de .NET Core 2.0"
description: "Découvrez les nouvelles fonctionnalités de .NET Core."
keywords: .NET, .NET Core
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.translationtype: HT
ms.sourcegitcommit: b47d4c74a01b99d743b69328c201096bc8d89794
ms.openlocfilehash: e43f72ebd26c34636c239d8ac9f749d52d3f60a0
ms.contentlocale: fr-fr
ms.lasthandoff: 08/14/2017

---
# <a name="whats-new-in-net-core"></a><span data-ttu-id="59683-104">Nouveautés de .NET Core</span><span class="sxs-lookup"><span data-stu-id="59683-104">What's new in .NET Core</span></span>

<span data-ttu-id="59683-105">.NET core 2.0 inclut les nouvelles fonctionnalités et améliorations dans les domaines suivants :</span><span class="sxs-lookup"><span data-stu-id="59683-105">.NET Core 2.0 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="59683-106">Outillage</span><span class="sxs-lookup"><span data-stu-id="59683-106">Tooling</span></span>](#tooling)
- [<span data-ttu-id="59683-107">Langages pris en charge</span><span class="sxs-lookup"><span data-stu-id="59683-107">Language support</span></span>](#language-support)
- [<span data-ttu-id="59683-108">Améliorations de plate-forme</span><span class="sxs-lookup"><span data-stu-id="59683-108">Platform improvements</span></span>](#platform-improvements)
- [<span data-ttu-id="59683-109">Modifications d'API</span><span class="sxs-lookup"><span data-stu-id="59683-109">API changes</span></span>](#api-changes-and-library-support)
- [<span data-ttu-id="59683-110">Intégration Visual Studio</span><span class="sxs-lookup"><span data-stu-id="59683-110">Visual Studio integration</span></span>](#visual-studio-integration)
- [<span data-ttu-id="59683-111">Améliorations apportées à la documentation</span><span class="sxs-lookup"><span data-stu-id="59683-111">Documentation improvements</span></span>](#documentation-improvements) 

## <a name="tooling"></a><span data-ttu-id="59683-112">Outillage</span><span class="sxs-lookup"><span data-stu-id="59683-112">Tooling</span></span>

### <a name="dotnet-restore-runs-implicitly"></a><span data-ttu-id="59683-113">la restauration de dotnet s’exécute implicitement</span><span class="sxs-lookup"><span data-stu-id="59683-113">dotnet restore runs implicitly</span></span>

<span data-ttu-id="59683-114">Dans les versions précédentes de .NET Core, vous deviez exécuter la commande [restauration de dotnet ](../tools/dotnet-restore.md) pour télécharger les dépendances immédiatement après la création d’un nouveau projet avec la commande [nouveauté de dotnet](../tools/dotnet-new.md), ainsi que dès que vous ajoutiez une nouvelle dépendance à votre projet.</span><span class="sxs-lookup"><span data-stu-id="59683-114">In previous versions of .NET Core, you had to run the [dotnet restore](../tools/dotnet-restore.md) command to download dependencies immediately after you created a new project with the [dotnet new](../tools/dotnet-new.md) command, as well as whenever you added a new dependency to your project.</span></span> <span data-ttu-id="59683-115">Dans .NET Core 2.0, `dotnet restore` s’exécute implicitement lorsque la `dotnet new` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="59683-115">In .NET Core 2.0, `dotnet restore` runs implicitly when the `dotnet new` command executes.</span></span> <span data-ttu-id="59683-116">Il s’exécute également implicitement si les dépendances doivent être mises à jour lorsque d’autres commandes, telles que les commandes `run`, `build` et `publish` s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="59683-116">It also runs implicitly if dependencies need to be updated when other commands, such as the `run`, `build`, and `publish` commands, execute.</span></span>

<span data-ttu-id="59683-117">Vous pouvez également désactiver l’appel automatique de `dotnet restore` en passant le commutateur `--no-restore` sur les commandes `new`, `run`, `build`, `publish`, `pack` et `test`.</span><span class="sxs-lookup"><span data-stu-id="59683-117">You can also disable the automatic invocation of `dotnet restore` by passing the `--no-restore` switch to the `new`, `run`, `build`, `publish`, `pack`, and `test` commands.</span></span> 

### <a name="retargeting-to-net-core-20"></a><span data-ttu-id="59683-118">Reciblage vers .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="59683-118">Retargeting to .NET Core 2.0</span></span>

<span data-ttu-id="59683-119">Si le Kit SDK .NET Core 2.0 est installé, les projets qui ciblent .NET Core 1.x peuvent être reciblés vers .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="59683-119">If the .NET Core 2.0 SDK is installed, projects that target .NET Core 1.x can be retargeted to .NET Core 2.0.</span></span> 

<span data-ttu-id="59683-120">Pour recibler vers .NET Core 2.0, modifiez votre fichier projet en modifiant la valeur de l’élément `<TargetFramework>` (ou l’élément `<TargetFrameworks>` si vous avez plus d’une cibles dans votre fichier projet) de 1.x à 2.0 :</span><span class="sxs-lookup"><span data-stu-id="59683-120">To retarget to .NET Core 2.0, edit your project file by changing the value of the `<TargetFramework>` element (or the `<TargetFrameworks>` element if you have more than one target in your project file) from 1.x to 2.0:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="59683-121">Vous pouvez également recibler les bibliothèques .NET Standard vers .NET Standard 2.0 de la même façon :</span><span class="sxs-lookup"><span data-stu-id="59683-121">You can also retarget .NET Standard libraries to .NET Standard 2.0 the same way:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="59683-122">Pour plus d’informations sur la migration de votre projet vers .NET Core 2.0, consultez [Migration depuis ASP.NET Core 1.x vers ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span><span class="sxs-lookup"><span data-stu-id="59683-122">For more information about migrating your project to .NET Core 2.0, see [Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span></span>

## <a name="language-support"></a><span data-ttu-id="59683-123">Langages pris en charge</span><span class="sxs-lookup"><span data-stu-id="59683-123">Language support</span></span>

<span data-ttu-id="59683-124">En plus de la prise en charge de c# et F #, .NET Core 2.0 prend également en charge Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="59683-124">In addition to supporting C# and F#, .NET Core 2.0 also supports Visual Basic.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="59683-125">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="59683-125">Visual Basic</span></span>

<span data-ttu-id="59683-126">Avec la version 2.0, .NET Core prend désormais en charge Visual Basic 2017.</span><span class="sxs-lookup"><span data-stu-id="59683-126">With version 2.0, .NET Core now supports Visual Basic 2017.</span></span> <span data-ttu-id="59683-127">Vous pouvez utiliser Visual Basic pour créer des types de projets suivants :</span><span class="sxs-lookup"><span data-stu-id="59683-127">You can use Visual Basic to create the following project types:</span></span>

- <span data-ttu-id="59683-128">Applications de consoles .NET Core</span><span class="sxs-lookup"><span data-stu-id="59683-128">.NET Core console apps</span></span>
- <span data-ttu-id="59683-129">Bibliothèques de classes .NET Core</span><span class="sxs-lookup"><span data-stu-id="59683-129">.NET Core class libraries</span></span>
- <span data-ttu-id="59683-130">Bibliothèques de classes .NET Standard</span><span class="sxs-lookup"><span data-stu-id="59683-130">.NET Standard class libraries</span></span>
- <span data-ttu-id="59683-131">Projets de test unitaire .NET Core</span><span class="sxs-lookup"><span data-stu-id="59683-131">.NET Core unit test projects</span></span>
- <span data-ttu-id="59683-132">Projet de test xUnit .NET Core</span><span class="sxs-lookup"><span data-stu-id="59683-132">.NET Core xUnit test projects</span></span> 

<span data-ttu-id="59683-133">Par exemple, pour créer une application Visual Basic « Hello World », procédez comme suit à partir de la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="59683-133">For example, to create a Visual Basic "Hello World" application, do the following steps from the command line:</span></span>

1. <span data-ttu-id="59683-134">Ouvrez la fenêtre de la console, créez un répertoire pour votre projet et définissez-le comme répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="59683-134">Open a console window, create a directory for your project, and make it the current directory.</span></span>

1. <span data-ttu-id="59683-135">Entrez la commande `dotnet new console -lang vb`.</span><span class="sxs-lookup"><span data-stu-id="59683-135">Enter the command `dotnet new console -lang vb`.</span></span>

   <span data-ttu-id="59683-136">La commande crée un fichier projet avec une extension de fichier `.vbproj` ainsi qu’un fichier de code source Visual Basic nommé *Program.vb*.</span><span class="sxs-lookup"><span data-stu-id="59683-136">The command creates a project file with a `.vbproj` file extension, along with a Visual Basic source code file named *Program.vb*.</span></span> <span data-ttu-id="59683-137">Ce fichier contient le code source pour écrire la chaîne « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="59683-137">This file contains the source code to write the string "Hello World!"</span></span> <span data-ttu-id="59683-138">sur la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="59683-138">to the console window.</span></span>
  
1.  <span data-ttu-id="59683-139">Entrez la commande `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="59683-139">Enter the command `dotnet run`.</span></span> <span data-ttu-id="59683-140">Les [outils .NET Core CLI](../tools/index.md) compilent et exécutent automatiquement l’application, qui affiche le message « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="59683-140">The [.NET Core CLI tools](../tools/index.md) automatically compile and execute the application, which displays the message "Hello World!"</span></span> <span data-ttu-id="59683-141">dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="59683-141">in the console window.</span></span>

### <a name="support-for-c-71"></a><span data-ttu-id="59683-142">Prise en charge de C#, 7.1</span><span class="sxs-lookup"><span data-stu-id="59683-142">Support for C# 7.1</span></span>

<span data-ttu-id="59683-143">.NET core 2.0 prend en charge C# 7.1, qui ajoute un nombre de nouvelles fonctionnalités, notamment :</span><span class="sxs-lookup"><span data-stu-id="59683-143">.NET Core 2.0 supports C# 7.1, which adds a number of new features, including:</span></span>

- <span data-ttu-id="59683-144">La méthode `Main`, le point d’entrée de l’application, peut être marquée avec le mot clé [asynchrone](../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="59683-144">The `Main` method, the application entry point, can be marked with the [async](../../csharp/language-reference/keywords/async.md) keyword.</span></span>
- <span data-ttu-id="59683-145">Déduire les noms de tuple.</span><span class="sxs-lookup"><span data-stu-id="59683-145">Inferred tuple names.</span></span>
- <span data-ttu-id="59683-146">Expressions par défaut.</span><span class="sxs-lookup"><span data-stu-id="59683-146">Default expressions.</span></span>

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a><span data-ttu-id="59683-147">Améliorations de plate-forme</span><span class="sxs-lookup"><span data-stu-id="59683-147">Platform improvements</span></span>

<span data-ttu-id="59683-148">.NET core 2.0 inclut plusieurs fonctionnalités qui facilitent l’installation de .NET Core et pour l’utiliser sur les systèmes d’exploitation pris en charge.</span><span class="sxs-lookup"><span data-stu-id="59683-148">.NET Core 2.0 includes a number of features that make it easier to install .NET Core and to use it on supported operating systems.</span></span>

### <a name="net-core-for-linux-is-a-single-implementation"></a><span data-ttu-id="59683-149">.NET core pour Linux est une mise en œuvre unique</span><span class="sxs-lookup"><span data-stu-id="59683-149">.NET Core for Linux is a single implementation</span></span>

<span data-ttu-id="59683-150">.NET core 2.0 offre une mise en œuvre unique de Linux qui fonctionne sur plusieurs distributions de Linux.</span><span class="sxs-lookup"><span data-stu-id="59683-150">.NET Core 2.0 offers a single Linux implementation that works on multiple Linux distributions.</span></span> <span data-ttu-id="59683-151">.NET core 1.x exige que vous téléchargiez une mise en œuvre de Linux spécifique à la distribution.</span><span class="sxs-lookup"><span data-stu-id="59683-151">.NET Core 1.x required that you download a distribution-specific Linux implementation.</span></span>

<span data-ttu-id="59683-152">Vous pouvez également développer des applications qui ciblent Linux en tant que système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="59683-152">You can also develop apps that target Linux as a single operating system.</span></span> <span data-ttu-id="59683-153">.NET core 1.x exige que vous cibliez séparément chaque distribution Linux.</span><span class="sxs-lookup"><span data-stu-id="59683-153">.NET Core 1.x required that you target each Linux distribution separately.</span></span> 

### <a name="support-for-the-apple-cryptographic-libraries"></a><span data-ttu-id="59683-154">Prise en charge des bibliothèques de chiffrement Apple</span><span class="sxs-lookup"><span data-stu-id="59683-154">Support for the Apple cryptographic libraries</span></span>

<span data-ttu-id="59683-155">.NET core 1.x sur macOS exige la bibliothèque de chiffrements du kit de ressources OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="59683-155">.NET Core 1.x on macOS required the OpenSSL toolkit's cryptographic library.</span></span> <span data-ttu-id="59683-156">.NET core 2.0 utilise les bibliothèques de chiffrement Apple et ne nécessite pas OpenSSL, vous n’en avez donc pas besoin pour l’installer.</span><span class="sxs-lookup"><span data-stu-id="59683-156">.NET Core 2.0 uses the Apple cryptographic libraries and doesn't require OpenSSL, so you no longer need to install it.</span></span> 

## <a name="api-changes-and-library-support"></a><span data-ttu-id="59683-157">Prise en charge de la bibliothèque et des modifications de l’API</span><span class="sxs-lookup"><span data-stu-id="59683-157">API changes and library support</span></span>

### <a name="support-for-net-standard-20"></a><span data-ttu-id="59683-158">Prise en charge de .NET 2.0 Standard</span><span class="sxs-lookup"><span data-stu-id="59683-158">Support for .NET Standard 2.0</span></span>

<span data-ttu-id="59683-159">.NET Standard définit un ensemble par version de l’API qui doit être disponible sur des mises en œuvre .NET conformes à cette version de la norme.</span><span class="sxs-lookup"><span data-stu-id="59683-159">The .NET Standard defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="59683-160">.NET Standard est destiné aux développeurs de bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="59683-160">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="59683-161">Il vise à garantir la fonctionnalité disponible dans une bibliothèque qui cible une version de .NET Standard sur chaque mise en œuvre .NET.</span><span class="sxs-lookup"><span data-stu-id="59683-161">It aims to guarantee the functionality that is available to a library that targets a version of the .NET Standard on each .NET implementation.</span></span> <span data-ttu-id="59683-162">.NET core 1.x prend en charge la .NET Standard version 1.6 ; .NET Core 2.0 prend en charge la dernière version, .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="59683-162">.NET Core 1.x supports the .NET Standard version 1.6; .NET Core 2.0 supports the latest version, .NET Standard 2.0.</span></span> <span data-ttu-id="59683-163">Pour plus d'informations, consultez [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="59683-163">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="59683-164">.NET Standard 2.0 inclut plus de 20 000 API de plus que dans la version .NET Standard 1.6.</span><span class="sxs-lookup"><span data-stu-id="59683-164">.NET Standard 2.0 includes over 20,000 more APIs than were available in the .NET Standard 1.6.</span></span> <span data-ttu-id="59683-165">Une grande partie de cette surface d’exposition étendue résulte de l’incorporation des API communs à .NET Framework et Xamarin dans .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="59683-165">Much of this expanded surface area results from incorporating APIs that are common to the .NET Framework and Xamarin into .NET Standard.</span></span>

<span data-ttu-id="59683-166">Les bibliothèques de classes .NET Standard 2.0 peuvent également faire référence à des bibliothèques de classes .NET Framework, à condition qu’elles appellent des API présents dans .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="59683-166">.NET Standard 2.0 class libraries can also reference .NET Framework class libraries, provided that they call APIs that are present in the .NET Standard 2.0.</span></span> <span data-ttu-id="59683-167">Aucune recompilation des bibliothèques .NET Framework n’est requise.</span><span class="sxs-lookup"><span data-stu-id="59683-167">No recompilation of the .NET Framework libraries is required.</span></span>

<span data-ttu-id="59683-168">Pour obtenir la liste des API ajoutés à .NET Standard depuis sa dernière version, la version 1.6 .NET Standard, consultez [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="59683-168">For a list of the APIs that have been added to the .NET Standard since its last version, the .NET Standard 1.6, see [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

### <a name="expanded-surface-area"></a><span data-ttu-id="59683-169">Surface d’exposition étendue</span><span class="sxs-lookup"><span data-stu-id="59683-169">Expanded surface area</span></span>

<span data-ttu-id="59683-170">Le nombre total d’API disponible sur .NET Core 2.0 a plus que doublé par rapport à .NET Core 1.1.</span><span class="sxs-lookup"><span data-stu-id="59683-170">The total number of APIs available on .NET Core 2.0 has more than doubled in comparison with .NET Core 1.1.</span></span> 

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="59683-171">Prise en charge des bibliothèques .NET Framework</span><span class="sxs-lookup"><span data-stu-id="59683-171">Support for .NET Framework libraries</span></span>

<span data-ttu-id="59683-172">Le code .NET Core peut faire référence aux bibliothèques .NET Framework existantes, y compris les packages NuGet existants.</span><span class="sxs-lookup"><span data-stu-id="59683-172">.NET Core code can reference existing .NET Framework libraries, including existing NuGet packages.</span></span> <span data-ttu-id="59683-173">Notez que les bibliothèques doivent utiliser des API qui se trouvent dans .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="59683-173">Note that the libraries must use APIs that are found in .NET Standard.</span></span>

## <a name="visual-studio-integration"></a><span data-ttu-id="59683-174">Visual Studio, intégration</span><span class="sxs-lookup"><span data-stu-id="59683-174">Visual Studio integration</span></span>

<span data-ttu-id="59683-175">Visual Studio 2017 version 15,3 et dans certains cas, Visual Studio pour Mac proposent un nombre d’améliorations importantes pour les développeurs de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="59683-175">Visual Studio 2017 version 15.3 and in some cases Visual Studio for Mac offer a number of significant enhancements for .NET Core developers.</span></span>

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a><span data-ttu-id="59683-176">Reciblage des applications .NET Core et des bibliothèques .NET Standard</span><span class="sxs-lookup"><span data-stu-id="59683-176">Retargeting .NET Core apps and .NET Standard libraries</span></span>

<span data-ttu-id="59683-177">Si le Kit SDK .NET Core 2.0 est installé, vous pouvez recibler les projets .NET Core 1.x vers .NET Core 2.0 et les bibliothèques .NET Standard 1.x vers .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="59683-177">If the .NET Core 2.0 SDK is installed, you can retarget .NET Core 1.x projects to .NET Core 2.0 and .NET Standard 1.x libraries to .NET Standard 2.0.</span></span> 

<span data-ttu-id="59683-178">Pour recibler votre projet dans Visual Studio, ouvrez l’onglet **Application** de la boîte de dialogue des propriétés du projet et modifiez la valeur**Infrastructure cible** sur **.NET Core 2.0** ou **.NET Standard 2.0**.</span><span class="sxs-lookup"><span data-stu-id="59683-178">To retarget your project in Visual Studio, you open the **Application** tab of the project's properties dialog and change the **Target framework** value to **.NET Core 2.0** or **.NET Standard 2.0**.</span></span> <span data-ttu-id="59683-179">Vous pouvez également le modifier en cliquant sur le projet avec le bouton droit et en sélectionnant l’option **Modifier le fichier\*.csproj**.</span><span class="sxs-lookup"><span data-stu-id="59683-179">You can also change it by right-clicking on the project and selecting the **Edit \*.csproj file** option.</span></span> <span data-ttu-id="59683-180">Pour plus d'informations, consultez la section [Outillage](#tooling) plus haut dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="59683-180">For more information, see the [Tooling](#tooling) section earlier in this topic.</span></span>

### <a name="live-unit-testing-support-for-net-core"></a><span data-ttu-id="59683-181">Prise en charge de Live Unit Testing pour .NET Core</span><span class="sxs-lookup"><span data-stu-id="59683-181">Live Unit Testing support for .NET Core</span></span>

<span data-ttu-id="59683-182">Lorsque vous modifiez votre code, Live Unit Testing exécute automatiquement tous les tests unitaires affectés en arrière-plan et présente les résultats et la couverture du code dans l’environnement Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="59683-182">Whenever you modify your code, Live Unit Testing automatically runs any affected unit tests in the background and displays the results and code coverage live in the Visual Studio environment.</span></span> <span data-ttu-id="59683-183">.NET Core 2.0 prend désormais en charge Live Unit Testing.</span><span class="sxs-lookup"><span data-stu-id="59683-183">.NET Core 2.0 now supports Live Unit Testing.</span></span> <span data-ttu-id="59683-184">Live Unit Testing était auparavant disponible uniquement pour les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="59683-184">Previously, Live Unit Testing was available only for .NET Framework applications.</span></span> 

<span data-ttu-id="59683-185">Pour plus d’informations, consultez [Live Unit Testing avec Visual Studio 2017](/visualstudio/test/live-unit-testing) et la [FAQ Live Unit Testing](/visualstudio/test/live-unit-testing-faq).</span><span class="sxs-lookup"><span data-stu-id="59683-185">For more information, see [Live Unit Testing with Visual Studio 2017](/visualstudio/test/live-unit-testing) and the [Live Unit Testing FAQ](/visualstudio/test/live-unit-testing-faq).</span></span>

### <a name="better-support-for-multiple-target-frameworks"></a><span data-ttu-id="59683-186">Meilleure prise en charge pour plusieurs infrastructures cibles</span><span class="sxs-lookup"><span data-stu-id="59683-186">Better support for multiple target frameworks</span></span>

<span data-ttu-id="59683-187">Si vous créez un projet pour plusieurs infrastructures cibles, vous pouvez maintenant sélectionner la plateforme cible dans le menu de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="59683-187">If you're building a project for multiple target frameworks, you can now select the target platform from the top-level menu.</span></span> <span data-ttu-id="59683-188">Dans l’illustration suivante, un projet nommé SCD1 cible Mac OS X 10.11 64 bits (`osx.10.11-x64`) et Windows 10/Windows Server 2016 64 bits (`win10-x64`).</span><span class="sxs-lookup"><span data-stu-id="59683-188">In the following figure, a project named SCD1 targets 64-bit Mac OS X 10.11 (`osx.10.11-x64`) and 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span></span> <span data-ttu-id="59683-189">Vous pouvez sélectionner l’infrastructure cible avant de sélectionner le bouton du projet, dans ce cas pour exécuter une version de débogage.</span><span class="sxs-lookup"><span data-stu-id="59683-189">You can select the target framework before selecting the project button, in this case to run a debug build.</span></span>

![Sélection de l’infrastructure cible lors de la génération d’un projet](media/multitarget.png) 

### <a name="side-by-side-support-for-net-core-sdks"></a><span data-ttu-id="59683-191">Prise en charge côte à côte pour les kits SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="59683-191">Side-by-side support for .NET Core SDKs</span></span>

<span data-ttu-id="59683-192">Vous pouvez maintenant installer le Kit SDK .NET Core indépendamment de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="59683-192">You can now install the .NET Core SDK independently of Visual Studio.</span></span> <span data-ttu-id="59683-193">Cela rend possible pour une seule version de Visual Studio pour générer des projets qui ciblent des versions différentes du .NET Core.</span><span class="sxs-lookup"><span data-stu-id="59683-193">This makes it possible for a single version of Visual Studio to build projects that target different versions of .NET Core.</span></span> <span data-ttu-id="59683-194">Auparavant, Visual Studio et le Kit SDK .NET Core ont été étroitement couplés ; une version particulière du kit SDK accompagnée d’une version particulière de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="59683-194">Previously, Visual Studio and the .NET Core SDK were tightly coupled; a particular version of the SDK accompanied a particular version of Visual Studio.</span></span>

## <a name="documentation-improvements"></a><span data-ttu-id="59683-195">Améliorations apportées à la documentation</span><span class="sxs-lookup"><span data-stu-id="59683-195">Documentation improvements</span></span>

### <a name="net-application-architecture"></a><span data-ttu-id="59683-196">Architecture de l’application .NET</span><span class="sxs-lookup"><span data-stu-id="59683-196">.NET Application Architecture</span></span>

<span data-ttu-id="59683-197">[L’architecture de l’application .NET](https://www.microsoft.com/net/learn/architecture) vous donne accès à un ensemble de livres électroniques qui fournissent des instructions, des meilleures pratiques et des exemples d’applications lors de l’utilisation de .NET pour générer :</span><span class="sxs-lookup"><span data-stu-id="59683-197">[.NET Application Architecture](https://www.microsoft.com/net/learn/architecture) gives you access to a set of eBooks that provide guidance, best practices, and sample applications when using .NET to build:</span></span>

- <span data-ttu-id="59683-198">Containers de Microservices et Docker.</span><span class="sxs-lookup"><span data-stu-id="59683-198">Microservices and Docker containers.</span></span>
- <span data-ttu-id="59683-199">Des applications web avec ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="59683-199">Web applications with ASP.NET.</span></span>
- <span data-ttu-id="59683-200">Des applications mobiles avec Xamarin.</span><span class="sxs-lookup"><span data-stu-id="59683-200">Mobile applications with Xamarin.</span></span>
- <span data-ttu-id="59683-201">Des applications qui sont déployées sur le Cloud avec Azure.</span><span class="sxs-lookup"><span data-stu-id="59683-201">Applications that are deployed to the Cloud with Azure.</span></span>

## <a name="see-also"></a><span data-ttu-id="59683-202">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59683-202">See also</span></span>
 [<span data-ttu-id="59683-203">Nouveautés de ASP.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="59683-203">What's new in ASP.NET Core 2.0</span></span>](/aspnet/core/aspnetcore-2.0)
