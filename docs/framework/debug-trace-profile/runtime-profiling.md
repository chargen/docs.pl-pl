---
title: "Profilowanie środowiska uruchomieniowego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance counters
- common language runtime, profiling
- Perfmon.exe
- System Monitor
- profiling
- runtime, profiling
- profiling applications
- Performance Console
ms.assetid: ccd68284-f3a8-47b8-bc3f-92e5fe3a1640
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 876635cfe0349c734a61dcc827a6f9594bb2a5d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="runtime-profiling"></a><span data-ttu-id="bb690-102">Profilowanie środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="bb690-102">Runtime Profiling</span></span>
<span data-ttu-id="bb690-103">Profilowanie jest metoda zbierania danych wydajności w jakimkolwiek scenariuszu rozwoju lub wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="bb690-103">Profiling is a method of gathering performance data in any development or deployment scenario.</span></span> <span data-ttu-id="bb690-104">Ta sekcja dotyczy deweloperów i administratorów, którzy chcą zebrać informacje dotyczące wydajności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb690-104">This section is for developers and system administrators who want to gather information about application performance.</span></span>  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a><span data-ttu-id="bb690-105">Śledzenie wydajności w Monitorze wydajności (Perfmon.exe)</span><span class="sxs-lookup"><span data-stu-id="bb690-105">Tracking Performance Using the Performance Monitor (Perfmon.exe)</span></span>  
 <span data-ttu-id="bb690-106">Monitor wydajności jest najprostszym narzędzie służące do profilu użytkownika [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb690-106">The Performance Monitor is the easiest tool to use to profile your [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] application.</span></span> <span data-ttu-id="bb690-107">Monitor wydajności graficznie reprezentuje dane liczników wydajności .NET Framework, które są instalowane z środowisko uruchomieniowe języka wspólnego i [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb690-107">The Performance Monitor graphically represents data found in the .NET Framework performance counters that are installed with the common language runtime and the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span> <span data-ttu-id="bb690-108">Te liczniki może służyć do monitorowania wszystkich elementów zarządzania pamięcią just in time (JIT) kompilatora wydajność.</span><span class="sxs-lookup"><span data-stu-id="bb690-108">These counters can be used to monitor everything from memory management to just-in-time (JIT) compiler performance.</span></span> <span data-ttu-id="bb690-109">One informujące o zasobach używany przez aplikację, czyli pośrednich miar wydajności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb690-109">They tell you about the resources your application uses, which is an indirect measure of your application's performance.</span></span> <span data-ttu-id="bb690-110">Zrozumieć sposób działania aplikacji wewnętrznie przy użyciu tych liczników.</span><span class="sxs-lookup"><span data-stu-id="bb690-110">Use these counters to understand how your application works internally.</span></span>  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a><span data-ttu-id="bb690-111">Aby uruchomić Perfmon.exe w systemie Windows Vista i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="bb690-111">To run Perfmon.exe on Windows Vista and later versions</span></span>  
  
1.  <span data-ttu-id="bb690-112">W wierszu polecenia wpisz **perfmon**.</span><span class="sxs-lookup"><span data-stu-id="bb690-112">At the command prompt, type **perfmon**.</span></span> <span data-ttu-id="bb690-113">**Monitora wydajności** zostanie wyświetlony w konsoli.</span><span class="sxs-lookup"><span data-stu-id="bb690-113">The **Performance Monitor** console appears.</span></span>  
  
2.  <span data-ttu-id="bb690-114">W **narzędzia do monitorowania** folderu, kliknij przycisk **monitora wydajności**.</span><span class="sxs-lookup"><span data-stu-id="bb690-114">In the **Monitoring Tools** folder, click **Performance Monitor**.</span></span>  
  
3.  <span data-ttu-id="bb690-115">Na pasku narzędzi Monitora wydajności, kliknij przycisk **Dodaj** ikona (znak plus), jeśli jest obecna.</span><span class="sxs-lookup"><span data-stu-id="bb690-115">In the Performance Monitor toolbar, click the **Add** icon (the plus sign), if it is present.</span></span> <span data-ttu-id="bb690-116">Jeśli nie jest obecny, kliknij prawym przyciskiem myszy w oknie monitora i wybierz **Dodaj liczniki** opcji.</span><span class="sxs-lookup"><span data-stu-id="bb690-116">If it is not present, right-click in the monitor window and select the **Add Counters** option.</span></span>  
  
     <span data-ttu-id="bb690-117">Spowoduje to otwarcie **Dodaj liczniki** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="bb690-117">This opens the **Add Counters** dialog box.</span></span> <span data-ttu-id="bb690-118">**Dostępne liczniki** pole listy wyświetla obiekty dostępne wydajności.</span><span class="sxs-lookup"><span data-stu-id="bb690-118">The **Available counters** list box displays the available performance objects.</span></span> <span data-ttu-id="bb690-119">Istnieje wiele wstępnie zdefiniowanych obiektów dla aplikacji .NET Framework, w tym w zakresie zarządzania pamięcią (**pamięci platformy .NET CLR**), współdziałanie (**.NET CLR Interop**), obsługa wyjątków (**.NET CLR wyjątki**), a wielowątkowości (**.NET CLR LocksAndThreads**).</span><span class="sxs-lookup"><span data-stu-id="bb690-119">There are a number of predefined objects for .NET Framework applications, including those for memory management (**.NET CLR Memory**), interoperability (**.NET CLR Interop**), exception handling (**.NET CLR Exceptions**), and multithreading (**.NET CLR LocksAndThreads**).</span></span> <span data-ttu-id="bb690-120">Każdy obiekt wydajności zawiera wiele liczników wydajności indywidualnych.</span><span class="sxs-lookup"><span data-stu-id="bb690-120">Each performance object includes a number of individual performance counters.</span></span> <span data-ttu-id="bb690-121">Aby uzyskać listę dostępnych w Monitorze wydajności liczników wydajności, zobacz [liczniki wydajności](../../../docs/framework/debug-trace-profile/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="bb690-121">For a list of the performance counters available in Performance Monitor, see [Performance Counters](../../../docs/framework/debug-trace-profile/performance-counters.md).</span></span>  
  
4.  <span data-ttu-id="bb690-122">Zaznacz pole wyboru obok nazwy obiektu wydajności, aby wyświetlić listę liczników wydajności poszczególnych, które obsługuje.</span><span class="sxs-lookup"><span data-stu-id="bb690-122">Select the check box next to a performance object's name to view the list of individual performance counters that it supports.</span></span>  
  
5.  <span data-ttu-id="bb690-123">Kliknij przycisk licznika wydajności, które chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="bb690-123">Click the performance counter you want to view.</span></span>  
  
6.  <span data-ttu-id="bb690-124">W **wystąpienia wybranego obiektu** pola listy, kliknij przycisk  **\<wszystkie wystąpienia >** Aby określić globalnie monitorowanie licznika wydajności dla środowisko uruchomieniowe języka wspólnego (to znaczy na zasady systemowe).</span><span class="sxs-lookup"><span data-stu-id="bb690-124">In the **Instances of selected object** list box, click **\<All instances>** to specify that you want to monitor the performance counter for the common language runtime globally (that is, on a system-wide basis).</span></span>  
  
     <span data-ttu-id="bb690-125">—lub—</span><span class="sxs-lookup"><span data-stu-id="bb690-125">-or-</span></span>  
  
     <span data-ttu-id="bb690-126">W **wystąpienia wybranego obiektu** pola listy, kliknij nazwę aplikacji do monitorowania licznika wydajności dla tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb690-126">In the **Instances of selected object** list box, click an application name to monitor the performance counter for that application.</span></span>  
  
     <span data-ttu-id="bb690-127">Możesz rozróżnić wiele wersji środowiska uruchomieniowego lub do odróżniania wiele aplikacji o takiej samej nazwie, należy zmodyfikować klucz rejestru.</span><span class="sxs-lookup"><span data-stu-id="bb690-127">To differentiate multiple versions of the runtime, or to disambiguate multiple applications with the same name, you must also modify a registry key.</span></span> <span data-ttu-id="bb690-128">Aby uzyskać więcej informacji, zobacz [liczniki wydajności i wewnątrzprocesowe Side-By-Side aplikacji](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md).</span><span class="sxs-lookup"><span data-stu-id="bb690-128">For more information, see [Performance Counters and In-Process Side-By-Side Applications](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb690-129">Po zainstalowaniu nowe liczniki wydajności konsoli wydajności jest uruchomiona, Zatrzymaj i ponownie uruchomić konsolę wydajności, aby wyświetlić nowe liczniki.</span><span class="sxs-lookup"><span data-stu-id="bb690-129">When new performance counters are installed while the Performance console is running, stop and restart the Performance console to make the new counters visible.</span></span>  
  
 <span data-ttu-id="bb690-130">Jeśli chcesz profilu zestawu, który istnieje w strefie lub w udziale zdalnym, upewnij się, że zestaw zdalnego ma pełne zaufanie na komputerze, na którym działają liczników wydajności.</span><span class="sxs-lookup"><span data-stu-id="bb690-130">If you want to profile an assembly that exists in a zone or on a remote share, make sure that the remote assembly has full trust on the computer that runs the performance counters.</span></span> <span data-ttu-id="bb690-131">Jeśli zestaw nie ma wystarczających zaufania, liczniki wydajności nie będą działać.</span><span class="sxs-lookup"><span data-stu-id="bb690-131">If the assembly does not have sufficient trust, the performance counters will not work.</span></span> <span data-ttu-id="bb690-132">Aby uzyskać informacje o udzielanie zaufania do różnych stref, zobacz [Caspol.exe (narzędzie zasad zabezpieczenia dostępu kodu)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).</span><span class="sxs-lookup"><span data-stu-id="bb690-132">For information about granting trust to different zones, see [Caspol.exe (Code Access Security Policy Tool)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb690-133">W systemach, w którym [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] jest zainstalowany, Monitor wydajności mogą nie wyświetlać się danych liczników wydajności w niektórych kategorii, takich jak **.NET CLR danych** i **.NET CLR sieci**, dla aplikacje, które zostały opracowane za pomocą [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb690-133">On systems on which the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] is installed, the Performance Monitor may not display data for performance counters in some categories, such as **.NET CLR Data** and **.NET CLR Networking**, for applications that were developed using the [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].</span></span> <span data-ttu-id="bb690-134">Jeśli jest to możliwe, można skonfigurować Monitor wydajności, aby wyświetlić te dane, dodając [ \<forceperformancecounteruniquesharedmemoryreads — >](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) elementu do pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb690-134">If this is the case, you can configure Performance Monitor to display this data by adding the [\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) element to the application's configuration file.</span></span>  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a><span data-ttu-id="bb690-135">Odczytywanie i programowe tworzenie liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="bb690-135">Reading and Creating Performance Counters Programmatically</span></span>  
 <span data-ttu-id="bb690-136">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Udostępnia klasy służy do uzyskania programowego dostępu do tych samych informacji wydajności, które są dostępne w konsoli wydajności.</span><span class="sxs-lookup"><span data-stu-id="bb690-136">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides classes you can use to programmatically access the same performance information that is available in the Performance console.</span></span> <span data-ttu-id="bb690-137">Aby utworzyć niestandardowe liczniki wydajności umożliwia także tych klas.</span><span class="sxs-lookup"><span data-stu-id="bb690-137">You can also use these classes to create custom performance counters.</span></span> <span data-ttu-id="bb690-138">W poniższej tabeli opisano niektóre działania monitorowania klasy, które zostały opublikowane w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb690-138">The following table describes some of the performance monitoring classes that are provided in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
|<span data-ttu-id="bb690-139">Class</span><span class="sxs-lookup"><span data-stu-id="bb690-139">Class</span></span>|<span data-ttu-id="bb690-140">Opis</span><span class="sxs-lookup"><span data-stu-id="bb690-140">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|<span data-ttu-id="bb690-141">Oznacza składnik licznika wydajności systemu Windows NT.</span><span class="sxs-lookup"><span data-stu-id="bb690-141">Represents a Windows NT performance counter component.</span></span> <span data-ttu-id="bb690-142">Klasa używana do odczytu istniejących, wstępnie zdefiniowanych lub niestandardowych liczników i publikowania danych wydajności (Zapisz), w licznikach niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="bb690-142">Use this class to read existing predefined or custom counters and publish (write) performance data to custom counters.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|<span data-ttu-id="bb690-143">Zapewnia kilka metod do interakcji z liczników i kategorii liczników na komputerze.</span><span class="sxs-lookup"><span data-stu-id="bb690-143">Provides several methods for interacting with counters and categories of counters on the computer.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=nameWithType>|<span data-ttu-id="bb690-144">Określa Instalatora dla `PerformanceCounter` składnika.</span><span class="sxs-lookup"><span data-stu-id="bb690-144">Specifies an installer for the `PerformanceCounter` component.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=nameWithType>|<span data-ttu-id="bb690-145">Określa formułę do obliczania `NextValue` metodę `PerformanceCounter`.</span><span class="sxs-lookup"><span data-stu-id="bb690-145">Specifies the formula to calculate the `NextValue` method for a `PerformanceCounter`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb690-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb690-146">See Also</span></span>  
 [<span data-ttu-id="bb690-147">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="bb690-147">Performance Counters</span></span>](../../../docs/framework/debug-trace-profile/performance-counters.md)