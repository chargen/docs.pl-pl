---
title: "Porady: lokalizowanie zestawów za pomocą DEVPATH"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 70448f7ce4c00274dde14bace603e5c8852bf148
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="de42f-102">Porady: lokalizowanie zestawów za pomocą DEVPATH</span><span class="sxs-lookup"><span data-stu-id="de42f-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="de42f-103">Deweloperzy mogą chcieć upewnij się, że współużytkowanego zespołu, które są one tworzenie działa poprawnie z wieloma aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="de42f-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="de42f-104">Zamiast stale umieszczanie zestawu w pamięci podręcznej GAC podczas cyklu programowania, deweloper może utworzyć zmienną środowiskową DEVPATH wskazujące budowy katalogu wyjściowego dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="de42f-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="de42f-105">Załóżmy na przykład, czy tworzysz zestaw udostępnionego o nazwie MySharedAssembly i katalog wyjściowy jest C:\MySharedAssembly\Debug.</span><span class="sxs-lookup"><span data-stu-id="de42f-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="de42f-106">Możesz też zaznaczyć C:\MySharedAssembly\Debug za pomocą DEVPATH zmiennej.</span><span class="sxs-lookup"><span data-stu-id="de42f-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="de42f-107">Następnie należy określić [ \<developmentmode — >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) elementu w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="de42f-107">You must then specify the [\<developmentMode>](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="de42f-108">Ten element określa, że środowisko uruchomieniowe języka wspólnego do użycia DEVPATH do lokalizowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="de42f-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="de42f-109">Zestaw udostępnionego musi być wykrywalny przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="de42f-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="de42f-110">Aby określić katalog prywatnej w celu rozwiązania użyj odwołania do zestawu [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) lub [ \<sondowanie > elementu](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) w pliku konfiguracji, zgodnie z opisem w temacie [Określanie lokalizacji zestawu](../../../docs/framework/configure-apps/specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="de42f-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) or [\<probing> Element](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  <span data-ttu-id="de42f-111">Można również umieścić zestaw w podkatalogu w katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de42f-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="de42f-112">Aby uzyskać więcej informacji, zobacz [jak zestawy środowiska wykonawczego lokalizuje](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="de42f-112">For more information, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de42f-113">Jest to zaawansowana funkcja przeznaczona tylko dla rozwoju.</span><span class="sxs-lookup"><span data-stu-id="de42f-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="de42f-114">Poniższy przykład pokazuje, jak spowodować środowiska uruchomieniowego do wyszukiwania zestawów w katalogach określonej przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="de42f-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de42f-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="de42f-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="de42f-116">Domyślnie to ustawienie na wartość false.</span><span class="sxs-lookup"><span data-stu-id="de42f-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de42f-117">Tego ustawienia należy używać tylko w czasie opracowywania.</span><span class="sxs-lookup"><span data-stu-id="de42f-117">Use this setting only at development time.</span></span> <span data-ttu-id="de42f-118">Środowisko uruchomieniowe nie sprawdza wersje zestawów o silnych nazwach w DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="de42f-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="de42f-119">Po prostu używa pierwszego zestawu znalezione.</span><span class="sxs-lookup"><span data-stu-id="de42f-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de42f-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de42f-120">See Also</span></span>  
 [<span data-ttu-id="de42f-121">Konfigurowanie aplikacji programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="de42f-121">Configuring .NET Framework Apps</span></span>](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)