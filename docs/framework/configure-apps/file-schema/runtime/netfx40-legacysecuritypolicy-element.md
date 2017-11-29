---
title: "&lt;NetFx40_LegacySecurityPolicy&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cb59eb6e2a5e831f603747b3e0f9435bd076fbf8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltnetfx40legacysecuritypolicygt-element"></a><span data-ttu-id="5c375-102">&lt;NetFx40_LegacySecurityPolicy&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="5c375-102">&lt;NetFx40_LegacySecurityPolicy&gt; Element</span></span>
<span data-ttu-id="5c375-103">Określa, czy środowisko uruchomieniowe używa zasady zabezpieczeń (CAS) starszego kodu dostępu.</span><span class="sxs-lookup"><span data-stu-id="5c375-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>  
  
 <span data-ttu-id="5c375-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="5c375-104">\<configuration></span></span>  
<span data-ttu-id="5c375-105">\<Runtime ></span><span class="sxs-lookup"><span data-stu-id="5c375-105">\<runtime></span></span>  
<span data-ttu-id="5c375-106">< NetFx40_LegacySecurityPolicy ></span><span class="sxs-lookup"><span data-stu-id="5c375-106"><NetFx40_LegacySecurityPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c375-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c375-107">Syntax</span></span>  
  
```xml  
<NetFx40_LegacySecurityPolicy  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c375-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5c375-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5c375-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5c375-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c375-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5c375-110">Attributes</span></span>  
  
|<span data-ttu-id="5c375-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5c375-111">Attribute</span></span>|<span data-ttu-id="5c375-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5c375-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5c375-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="5c375-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5c375-114">Określa, czy środowisko uruchomieniowe używa starszej wersji zasad CAS.</span><span class="sxs-lookup"><span data-stu-id="5c375-114">Specifies whether the runtime uses legacy CAS policy.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5c375-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="5c375-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5c375-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="5c375-116">Value</span></span>|<span data-ttu-id="5c375-117">Opis</span><span class="sxs-lookup"><span data-stu-id="5c375-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5c375-118">Środowisko uruchomieniowe nie używa starszej wersji zasad CAS.</span><span class="sxs-lookup"><span data-stu-id="5c375-118">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="5c375-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="5c375-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="5c375-120">Środowisko uruchomieniowe używa starszej wersji zasad CAS.</span><span class="sxs-lookup"><span data-stu-id="5c375-120">The runtime uses legacy CAS policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c375-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5c375-121">Child Elements</span></span>  
 <span data-ttu-id="5c375-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="5c375-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c375-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5c375-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5c375-124">Element</span><span class="sxs-lookup"><span data-stu-id="5c375-124">Element</span></span>|<span data-ttu-id="5c375-125">Opis</span><span class="sxs-lookup"><span data-stu-id="5c375-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5c375-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5c375-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5c375-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="5c375-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c375-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c375-128">Remarks</span></span>  
 <span data-ttu-id="5c375-129">W wersji .NET Framework 3.5 i wcześniejszymi wersjami urzędy certyfikacji zasad jest zawsze w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="5c375-129">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="5c375-130">W [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], należy włączyć zasady CAS.</span><span class="sxs-lookup"><span data-stu-id="5c375-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], CAS policy must be enabled.</span></span>  
  
 <span data-ttu-id="5c375-131">Urzędy certyfikacji zasad jest określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="5c375-131">CAS policy is version-specific.</span></span> <span data-ttu-id="5c375-132">Zasady niestandardowe urzędy certyfikacji znajdujące się we wcześniejszych wersjach programu .NET Framework musi obowiązywać w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c375-132">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>  
  
 <span data-ttu-id="5c375-133">Stosowanie `<NetFx40_LegacySecurityPolicy>` elementu [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] zestaw nie ma wpływu na [kod o przezroczystym poziomie bezpieczeństwa](../../../../../docs/framework/misc/security-transparent-code.md); nadal stosować zasady przezroczystość.</span><span class="sxs-lookup"><span data-stu-id="5c375-133">Applying the `<NetFx40_LegacySecurityPolicy>` element to a [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] assembly does not affect [security-transparent code](../../../../../docs/framework/misc/security-transparent-code.md); the transparency rules still apply.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5c375-134">Stosowanie `<NetFx40_LegacySecurityPolicy>` elementu może spowodować spadku wydajności istotne dla zestawów obrazu macierzystego utworzonych przez [Generator obrazu natywnego (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) nie są zainstalowane w [Globalna pamięć podręczna zestawów ](../../../../../docs/framework/app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="5c375-134">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../../../docs/framework/app-domains/gac.md).</span></span> <span data-ttu-id="5c375-135">Spadek wydajności jest spowodowany brakiem środowiska uruchomieniowego można załadować zestawów jako obrazów natywnych, gdy jest stosowany atrybut, co powoduje ich załadowanych zespołów jako just-in-time.</span><span class="sxs-lookup"><span data-stu-id="5c375-135">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c375-136">Jeśli określisz docelową wersję .NET Framework, która jest starsza niż [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] w ustawieniach projektu dla projektu programu Visual Studio, zasad CAS zostanie włączona, łącznie z urzędami certyfikacji zasad niestandardowych określony dla tej wersji.</span><span class="sxs-lookup"><span data-stu-id="5c375-136">If you specify a target .NET Framework version that is earlier than the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="5c375-137">Jednak nie będzie mógł używać nowego [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] typy i składniki.</span><span class="sxs-lookup"><span data-stu-id="5c375-137">However, you will not be able to use new [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] types and members.</span></span> <span data-ttu-id="5c375-138">Można także określić przy użyciu wcześniejszej wersji programu .NET Framework [ \<supportedRuntime > element](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) w schemat ustawień uruchamiania w Twojej [pliku konfiguracji aplikacji](../../../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="5c375-138">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../../../../docs/framework/configure-apps/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c375-139">Składnia pliku konfiguracji jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="5c375-139">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="5c375-140">Należy użyć składni, co zostało opisane w sekcji składnię i przykład.</span><span class="sxs-lookup"><span data-stu-id="5c375-140">You should use the syntax as provided in the Syntax and Example sections.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="5c375-141">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5c375-141">Configuration File</span></span>  
 <span data-ttu-id="5c375-142">Ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5c375-142">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c375-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c375-143">Example</span></span>  
 <span data-ttu-id="5c375-144">Poniższy przykład przedstawia sposób Włącz starszą zasadę dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5c375-144">The following example shows how to enable legacy CAS policy for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c375-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c375-145">See Also</span></span>  
 [<span data-ttu-id="5c375-146">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5c375-146">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="5c375-147">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5c375-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)