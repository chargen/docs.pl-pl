---
title: "Schemat ustawień sieci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ca4a0000d85c8fbac9a723beeda51f9c7886ed8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="network-settings-schema"></a><span data-ttu-id="57e7e-102">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="57e7e-102">Network Settings Schema</span></span>
<span data-ttu-id="57e7e-103">Ustawienia sieci określają, jak programu .NET Framework łączy się z Internetem.</span><span class="sxs-lookup"><span data-stu-id="57e7e-103">Network settings specify how the .NET Framework connects to the Internet.</span></span> <span data-ttu-id="57e7e-104">W poniższej tabeli opisano funkcję każdego podrzędnego elementu konfiguracji w obszarze [ \<system.Net > (ustawienia sieciowe) elementu](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="57e7e-104">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="57e7e-105">Element</span><span class="sxs-lookup"><span data-stu-id="57e7e-105">Element</span></span>|<span data-ttu-id="57e7e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="57e7e-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57e7e-107">\<authenticationModules — > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="57e7e-107">\<authenticationModules> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="57e7e-108">Określa moduły używane do uwierzytelniania żądań Internet.</span><span class="sxs-lookup"><span data-stu-id="57e7e-108">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="57e7e-109">\<connectionmanagement — > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="57e7e-109">\<connectionManagement> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="57e7e-110">Określa maksymalną liczbę połączeń z hostami w Internecie.</span><span class="sxs-lookup"><span data-stu-id="57e7e-110">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="57e7e-111">\<defaultProxy — > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="57e7e-111">\<defaultProxy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="57e7e-112">Określa serwer proxy do żądań HTTP w Internecie.</span><span class="sxs-lookup"><span data-stu-id="57e7e-112">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="57e7e-113">\<mailSettings > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="57e7e-113">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="57e7e-114">Zawiera ustawienia Opcje wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="57e7e-114">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="57e7e-115">\<requestCaching — > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="57e7e-115">\<requestCaching> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="57e7e-116">Określa moduły używane do żądania informacji z Internetu hostów.</span><span class="sxs-lookup"><span data-stu-id="57e7e-116">Specifies the modules used to request information from Internet hosts.</span></span>|  
|[<span data-ttu-id="57e7e-117">\<requestCaching — > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="57e7e-117">\<requestCaching> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="57e7e-118">Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="57e7e-118">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>|  
|[<span data-ttu-id="57e7e-119">\<webRequestModules — > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="57e7e-119">\<webRequestModules> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="57e7e-120">Określa moduły używane do żądania informacji z Internetu hostów.</span><span class="sxs-lookup"><span data-stu-id="57e7e-120">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
 <span data-ttu-id="57e7e-121">Identyfikator URI ustawienia określają, jak programu .NET Framework obsługuje adresy URL wyrazić przy użyciu uniform resource identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="57e7e-121">Uri settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="57e7e-122">W poniższej tabeli opisano funkcję każdego podrzędnego elementu konfiguracji w obszarze [ \<Uri > elementu (ustawienia identyfikatorów Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="57e7e-122">The following table describes the function of each child configuration element under the [\<Uri> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="57e7e-123">Element</span><span class="sxs-lookup"><span data-stu-id="57e7e-123">Element</span></span>|<span data-ttu-id="57e7e-124">Opis</span><span class="sxs-lookup"><span data-stu-id="57e7e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57e7e-125">\<IDN > elementu (ustawienia identyfikatorów Uri)</span><span class="sxs-lookup"><span data-stu-id="57e7e-125">\<idn> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="57e7e-126">Określa, czy międzynarodowych nazw domen (IDN) podczas analizowania została zastosowana do nazw domen.</span><span class="sxs-lookup"><span data-stu-id="57e7e-126">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="57e7e-127">\<iriParsing > elementu (ustawienia identyfikatorów Uri)</span><span class="sxs-lookup"><span data-stu-id="57e7e-127">\<iriParsing> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="57e7e-128">Określa identyfikator zasobu międzynarodowych (IRI) podczas analizowania odnosi się do <xref:System.Uri> i określa, czy powinny być stosowane IRI podczas analizowania reguły.</span><span class="sxs-lookup"><span data-stu-id="57e7e-128">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="57e7e-129">\<schemeSettings > elementu (ustawienia identyfikatorów Uri)</span><span class="sxs-lookup"><span data-stu-id="57e7e-129">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="57e7e-130">Określa sposób <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.</span><span class="sxs-lookup"><span data-stu-id="57e7e-130">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57e7e-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57e7e-131">See Also</span></span>  
 [<span data-ttu-id="57e7e-132">Konfigurowanie aplikacji internetowych</span><span class="sxs-lookup"><span data-stu-id="57e7e-132">Configuring Internet Applications</span></span>](../../../../../docs/framework/network-programming/configuring-internet-applications.md)  
 [<span data-ttu-id="57e7e-133">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="57e7e-133">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)