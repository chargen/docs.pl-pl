---
title: "Organizowanie i testowanie projektów przy użyciu wiersza polecenia platformy .NET Core"
description: "W tym samouczku opisano sposób organizowania i testowanie projektów .NET Core w wierszu polecenia."
keywords: Testowanie .NET Core CLI, xUnit jednostki .NET i .NET core
author: cartermp
ms.author: mairaw
ms.date: 05/16/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 52ff1be3-d92e-4477-9c84-8c1771e87ab5
ms.openlocfilehash: 62c81bf070a435f6105c313ae95340a5504233df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a><span data-ttu-id="94fbc-104">Organizowanie i testowanie projektów przy użyciu wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="94fbc-104">Organizing and testing projects with the .NET Core command line</span></span>

<span data-ttu-id="94fbc-105">W tym samouczku wykonuje [Rozpoczynanie pracy z platformą .NET Core w systemie Windows/Linux/macOS przy użyciu wiersza polecenia](using-with-xplat-cli.md), otwieranie poza tworzenie aplikacji konsoli simple do opracowywania zaawansowanych i dobrze zorganizowane aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94fbc-105">This tutorial follows [Getting started with .NET Core on Windows/Linux/macOS using the command line](using-with-xplat-cli.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="94fbc-106">Po przedstawiający sposób używania folderów do organizowania kodu, w tym samouczku przedstawiono sposób rozszerzyć aplikacji konsoli z [xUnit](https://xunit.github.io/) testowania framework.</span><span class="sxs-lookup"><span data-stu-id="94fbc-106">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="94fbc-107">Organizowanie kodu za pomocą folderów</span><span class="sxs-lookup"><span data-stu-id="94fbc-107">Using folders to organize code</span></span>

<span data-ttu-id="94fbc-108">Aby dodać nowe typy w aplikacji konsoli, możesz to zrobić przez dodanie plików zawierających typy do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94fbc-108">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="94fbc-109">Na przykład możesz dodać pliki zawierające `AccountInformation` i `MonthlyReportRecords` typów do projektu, struktura pliku projektu jest prosty i nawigację:</span><span class="sxs-lookup"><span data-stu-id="94fbc-109">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="94fbc-110">Jednak to działa tylko oraz gdy jest stosunkowo mały rozmiar projektu.</span><span class="sxs-lookup"><span data-stu-id="94fbc-110">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="94fbc-111">Można w pewnym sensie co się stanie po dodaniu 20 typów do projektu?</span><span class="sxs-lookup"><span data-stu-id="94fbc-111">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="94fbc-112">Ostatecznie projektu nie będą łatwe do nawigowania i obsługa z tym wiele plików littering katalog główny projektu.</span><span class="sxs-lookup"><span data-stu-id="94fbc-112">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="94fbc-113">Aby zorganizować projektu, Utwórz nowy folder i nadaj mu nazwę *modele* do przechowywania plików typu.</span><span class="sxs-lookup"><span data-stu-id="94fbc-113">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="94fbc-114">Umieścić pliki typu *modele* folderu:</span><span class="sxs-lookup"><span data-stu-id="94fbc-114">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="94fbc-115">Projekty, które logicznie grupy plików w folderach łatwych do nawigowania i obsługa.</span><span class="sxs-lookup"><span data-stu-id="94fbc-115">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="94fbc-116">W następnej sekcji utworzysz próbkę bardziej złożonych z folderami i testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="94fbc-116">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="94fbc-117">Organizowanie i testowania przy użyciu przykładowych zwierząt domowych NewTypes</span><span class="sxs-lookup"><span data-stu-id="94fbc-117">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="94fbc-118">Tworzenie przykładowej</span><span class="sxs-lookup"><span data-stu-id="94fbc-118">Building the sample</span></span>

<span data-ttu-id="94fbc-119">Dla następujących kroków, można to wykonać przy użyciu [NewTypes zwierząt domowych próbki](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild) lub tworzyć własne pliki i foldery.</span><span class="sxs-lookup"><span data-stu-id="94fbc-119">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="94fbc-120">Typy są logicznie pogrupowane w struktury folderów, która pozwala na dodanie większej liczby typów później, a testy również logicznie są umieszczane w folderach umożliwiający dodanie większej liczby testów później.</span><span class="sxs-lookup"><span data-stu-id="94fbc-120">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="94fbc-121">Próbka zawiera dwa typy `Dog` i `Cat`i ich implementacji wspólny interfejs ma `IPet`.</span><span class="sxs-lookup"><span data-stu-id="94fbc-121">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="94fbc-122">Dla `NewTypes` projektu, jest organizowania typów związanych z pet do *zwierząt domowych* folderu.</span><span class="sxs-lookup"><span data-stu-id="94fbc-122">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="94fbc-123">Jeśli później dodać inny zestaw typów *WildAnimals* na przykład jest umieszczany w *NewTypes* folderu obok *zwierząt domowych* folderu.</span><span class="sxs-lookup"><span data-stu-id="94fbc-123">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="94fbc-124">*WildAnimals* folder może zawierać typy zwierząt, które nie są zwierząt domowych, takich jak `Squirrel` i `Rabbit` typów.</span><span class="sxs-lookup"><span data-stu-id="94fbc-124">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="94fbc-125">W ten sposób jako typy są dodawane, projekt pozostaje również zorganizowany.</span><span class="sxs-lookup"><span data-stu-id="94fbc-125">In this way as types are added, the project remains well organized.</span></span> 

<span data-ttu-id="94fbc-126">Utwórz następującą strukturę folderów z zawartością pliku wskazanego:</span><span class="sxs-lookup"><span data-stu-id="94fbc-126">Create the following folder structure with file content indicated:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
```

<span data-ttu-id="94fbc-127">*IPet.cs*:</span><span class="sxs-lookup"><span data-stu-id="94fbc-127">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="94fbc-128">*Dog.cs*:</span><span class="sxs-lookup"><span data-stu-id="94fbc-128">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="94fbc-129">*Cat.cs*:</span><span class="sxs-lookup"><span data-stu-id="94fbc-129">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="94fbc-130">*Plik program.cs*:</span><span class="sxs-lookup"><span data-stu-id="94fbc-130">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

<span data-ttu-id="94fbc-131">*NewTypes.csproj*:</span><span class="sxs-lookup"><span data-stu-id="94fbc-131">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="94fbc-132">Uruchom następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="94fbc-132">Execute the following commands:</span></span>

```console
dotnet run
```

<span data-ttu-id="94fbc-133">Uzyskaj następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="94fbc-133">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="94fbc-134">Ćwiczenie opcjonalne: można dodać nowy typ domowych, takich jak `Bird`, rozszerzając tego projektu.</span><span class="sxs-lookup"><span data-stu-id="94fbc-134">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="94fbc-135">Wprowadź ptaka `TalkToOwner` podać metodę `Tweet!` do właściciela.</span><span class="sxs-lookup"><span data-stu-id="94fbc-135">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="94fbc-136">Ponownie uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="94fbc-136">Run the app again.</span></span> <span data-ttu-id="94fbc-137">Dane wyjściowe będą zawierać`Tweet!`</span><span class="sxs-lookup"><span data-stu-id="94fbc-137">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="94fbc-138">Testowanie próbki</span><span class="sxs-lookup"><span data-stu-id="94fbc-138">Testing the sample</span></span>

<span data-ttu-id="94fbc-139">`NewTypes` Projektu jest już na miejscu i ułożone go przechowując powiązane zwierząt domowych typów w folderze.</span><span class="sxs-lookup"><span data-stu-id="94fbc-139">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="94fbc-140">Następnie utwórz projekt testowy i rozpocząć pisanie testów z [xUnit](https://xunit.github.io/) struktury testowej.</span><span class="sxs-lookup"><span data-stu-id="94fbc-140">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="94fbc-141">Testy jednostkowe umożliwia automatyczne sprawdzenie dostępności bevahior pet typów, aby upewnić się, że są one poprawnie działających.</span><span class="sxs-lookup"><span data-stu-id="94fbc-141">Unit testing allows you to automatically check the bevahior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="94fbc-142">Utwórz *test* folder o *NewTypesTests* folderze.</span><span class="sxs-lookup"><span data-stu-id="94fbc-142">Create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="94fbc-143">W wierszu polecenia z *NewTypesTests* folderu, wykonać `dotnet new xunit`.</span><span class="sxs-lookup"><span data-stu-id="94fbc-143">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="94fbc-144">To tworzy dwa pliki: *NewTypesTests.csproj* i *UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="94fbc-144">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="94fbc-145">Projekt testowy nie może obecnie przetestować typów w `NewTypes` i wymaga odwołania projektu do `NewTypes` projektu.</span><span class="sxs-lookup"><span data-stu-id="94fbc-145">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="94fbc-146">Aby dodać odwołanie do projektu, należy użyć [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="94fbc-146">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="94fbc-147">Masz również możliwość ręcznie dodać odwołanie do projektu, dodając `<ItemGroup>` węzeł *NewTypesTests.csproj* pliku:</span><span class="sxs-lookup"><span data-stu-id="94fbc-147">You also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="94fbc-148">*NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="94fbc-148">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="94fbc-149">*NewTypesTests.csproj* plik zawiera następujące:</span><span class="sxs-lookup"><span data-stu-id="94fbc-149">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="94fbc-150">Odwołanie do pakietu `Microsoft.NET.Test.Sdk`, .NET testowania infrastruktury</span><span class="sxs-lookup"><span data-stu-id="94fbc-150">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="94fbc-151">Odwołanie do pakietu `xunit`, xUnit testowania framework</span><span class="sxs-lookup"><span data-stu-id="94fbc-151">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="94fbc-152">Odwołanie do pakietu `xunit.runner.visualstudio`, uruchamiający</span><span class="sxs-lookup"><span data-stu-id="94fbc-152">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="94fbc-153">Odwołanie do projektu `NewTypes`, kod do testowania</span><span class="sxs-lookup"><span data-stu-id="94fbc-153">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="94fbc-154">Zmień nazwę *UnitTest1.cs* do *PetTests.cs* i Zastąp kod w pliku następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="94fbc-154">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();
        
        Assert.NotEqual(expected, actual);
    }
    
    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();
        
        Assert.NotEqual(expected, actual);
    }
}
```

<span data-ttu-id="94fbc-155">Opcjonalne wykonywania: Jeśli dodano `Bird` wcześniej typu, który daje `Tweet!` do właściciela, Dodaj metodę testu *PetTests.cs* pliku `BirdTalkToOwnerReturnsTweet`, aby sprawdzić, czy `TalkToOwner` metoda działa poprawnie na `Bird` typu.</span><span class="sxs-lookup"><span data-stu-id="94fbc-155">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="94fbc-156">Mimo że oczekuje, że `expected` i `actual` wartości są równe, początkowej potwierdzenia z `Assert.NotEqual` kontroli Określ, czy są one *równa*.</span><span class="sxs-lookup"><span data-stu-id="94fbc-156">Although you expect that the `expected` and `actual` values are equal, the initial assertions with the `Assert.NotEqual` checks specify that they are *not equal*.</span></span> <span data-ttu-id="94fbc-157">Zawsze początkowo tworzenie testów niepowodzenie raz w celu sprawdzenia logiki testów.</span><span class="sxs-lookup"><span data-stu-id="94fbc-157">Always initially create your tests to fail once in order to check the logic of the tests.</span></span> <span data-ttu-id="94fbc-158">Jest to ważny krok metodologii test-driven projektu (TDD).</span><span class="sxs-lookup"><span data-stu-id="94fbc-158">This is an important step in test-driven design (TDD) methodology.</span></span> <span data-ttu-id="94fbc-159">Po upewnieniu się, że testy zostaną zakończone niepowodzeniem, możesz dostosować potwierdzenia umożliwia im to do przekazania.</span><span class="sxs-lookup"><span data-stu-id="94fbc-159">After you confirm the tests fail, you adjust the assertions to allow them to pass.</span></span>

<span data-ttu-id="94fbc-160">Poniżej przedstawiono struktury kompletnego projektu:</span><span class="sxs-lookup"><span data-stu-id="94fbc-160">The following shows the complete project structure:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

<span data-ttu-id="94fbc-161">Uruchom w *testu/NewTypesTests* katalogu.</span><span class="sxs-lookup"><span data-stu-id="94fbc-161">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="94fbc-162">Przywracanie projektu testowego z [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="94fbc-162">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="94fbc-163">Uruchom testy z [ `dotnet test` ](../tools/dotnet-test.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="94fbc-163">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="94fbc-164">To polecenie uruchamia uruchamiający określony w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="94fbc-164">This command starts the test runner specified in the project file.</span></span>

 [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

 
<span data-ttu-id="94fbc-165">Zgodnie z oczekiwaniami, testowania kończy się niepowodzeniem i konsoli wyświetla następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="94fbc-165">As expected, testing fails, and the console displays the following output:</span></span>
 
```
Test run for C:\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp1.1\NewTypesTests.dll(.NETCoreApp,Version=v1.1)
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.7271827]   Discovering: NewTypesTests
[xUnit.net 00:00:00.8258687]   Discovered:  NewTypesTests
[xUnit.net 00:00:00.8663545]   Starting:    NewTypesTests
[xUnit.net 00:00:01.0109236]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
[xUnit.net 00:00:01.0119107]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0120278]       Expected: Not "Meow!"
[xUnit.net 00:00:01.0120968]       Actual:   "Meow!"
[xUnit.net 00:00:01.0130500]       Stack Trace:
[xUnit.net 00:00:01.0141240]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(22,0): at PetTests.CatTalkToOwnerReturnsMeow()
[xUnit.net 00:00:01.0272364]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:01.0273649]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0274166]       Expected: Not "Woof!"
[xUnit.net 00:00:01.0274690]       Actual:   "Woof!"
[xUnit.net 00:00:01.0275264]       Stack Trace:
[xUnit.net 00:00:01.0275960]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(13,0): at PetTests.DogTalkToOwnerReturnsWoof()
[xUnit.net 00:00:01.0294509]   Finished:    NewTypesTests
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 2.1371 Seconds
```

<span data-ttu-id="94fbc-166">Zmień potwierdzenia testów `Assert.NotEqual` do `Assert.Equal`:</span><span class="sxs-lookup"><span data-stu-id="94fbc-166">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="94fbc-167">Ponownie uruchom testy z `dotnet test` poleceń i uzyskać następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="94fbc-167">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:01.3882374]   Discovering: NewTypesTests
[xUnit.net 00:00:01.4767970]   Discovered:  NewTypesTests
[xUnit.net 00:00:01.5157667]   Starting:    NewTypesTests
[xUnit.net 00:00:01.6408870]   Finished:    NewTypesTests

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6634 Seconds
```

<span data-ttu-id="94fbc-168">Testowanie przejścia.</span><span class="sxs-lookup"><span data-stu-id="94fbc-168">Testing passes.</span></span> <span data-ttu-id="94fbc-169">Metody typów pet zwracać poprawnych wartości komunikuje się z właścicielem.</span><span class="sxs-lookup"><span data-stu-id="94fbc-169">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="94fbc-170">Znasz już techniki organizowanie i testowanie projektów przy użyciu xUnit.</span><span class="sxs-lookup"><span data-stu-id="94fbc-170">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="94fbc-171">Przejdź do przodu z tych metod, stosując je do własnych projektów.</span><span class="sxs-lookup"><span data-stu-id="94fbc-171">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="94fbc-172">*Kodowanie przyjemność!*</span><span class="sxs-lookup"><span data-stu-id="94fbc-172">*Happy coding!*</span></span>
