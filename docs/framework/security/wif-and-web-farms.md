---
title: "WIF i farmy serwerów sieci Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 22c2272118c8f8a42523d9bc8ceaa2007c0b7b57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="wif-and-web-farms"></a><span data-ttu-id="88cb2-102">WIF i farmy serwerów sieci Web</span><span class="sxs-lookup"><span data-stu-id="88cb2-102">WIF and Web Farms</span></span>
<span data-ttu-id="88cb2-103">Korzystając z programu Windows Identity Foundation (WIF) do zabezpieczania zasobów jednostki uzależnionej aplikacji firmy (RP), które zostało wdrożone w farmie sieci web, należy wykonać określone kroki, aby upewnić się, że WIF może przetwarzać tokenów z wystąpień RP aplikacji uruchomionych na różnych komputery z farmy.</span><span class="sxs-lookup"><span data-stu-id="88cb2-103">When you use Windows Identity Foundation (WIF) to secure the resources of a relying party (RP) application that is deployed in a web farm, you must take specific steps to ensure that WIF can process tokens from instances of the RP application running on different computers in the farm.</span></span> <span data-ttu-id="88cb2-104">Proces przetwarzania obejmuje sprawdzanie poprawności Podpisy tokenu sesji, szyfrowania i odszyfrowywania tokenów sesji, buforowanie tokeny sesji i wykrywanie odtwarzany tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="88cb2-104">This processing includes validating session token signatures, encrypting and decrypting session tokens, caching session tokens, and detecting replayed security tokens.</span></span>  
  
 <span data-ttu-id="88cb2-105">W przypadku typowej gdy WIF służy do zabezpieczania zasobów aplikacji RP — czy RP działa na pojedynczym komputerze lub w kolektywie serwerów sieci web--sesji jest nawiązywane z klienta na podstawie tokenów zabezpieczeń, który został uzyskany z usługi tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="88cb2-105">In the typical case, when WIF is used to secure resources of an RP application – whether the RP is running on a single computer or in a web farm -- a session is established with the client based on the security token that was obtained from the security token service (STS).</span></span> <span data-ttu-id="88cb2-106">Pozwoli to uniknąć wymuszania klienta do uwierzytelniania na STS dla każdego zasobu jest zabezpieczone przy użyciu WIF aplikacji.</span><span class="sxs-lookup"><span data-stu-id="88cb2-106">This is to avoid forcing the client to have to authenticate at the STS for every application resource that is secured using WIF.</span></span> <span data-ttu-id="88cb2-107">Aby uzyskać więcej informacji na temat obsługi WIF sesji, zobacz [WIF sesji zarządzania](../../../docs/framework/security/wif-session-management.md).</span><span class="sxs-lookup"><span data-stu-id="88cb2-107">For more information about how WIF handles sessions, see [WIF Session Management](../../../docs/framework/security/wif-session-management.md).</span></span>  
  
 <span data-ttu-id="88cb2-108">Gdy używane są ustawienia domyślne, WIF wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="88cb2-108">When default settings are used, WIF does the following:</span></span>  
  
-   <span data-ttu-id="88cb2-109">Używa wystąpienia <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy do odczytu i zapisu tokenu sesji (wystąpienie <xref:System.IdentityModel.Tokens.SessionSecurityToken> klasy) która prowadzi oświadczenia i innych informacji o tokenie zabezpieczającym, który był używany do uwierzytelniania, a także informacje o sesji samego siebie.</span><span class="sxs-lookup"><span data-stu-id="88cb2-109">It uses an instance of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class to read and write a session token (an instance of the <xref:System.IdentityModel.Tokens.SessionSecurityToken> class) that carries the claims and other information about the security token that was used for authentication as well as information about the session itself.</span></span> <span data-ttu-id="88cb2-110">Tokenu sesji zostaje spakowany i przechowywane w pliku cookie sesji.</span><span class="sxs-lookup"><span data-stu-id="88cb2-110">The session token is packaged and stored in a session cookie.</span></span> <span data-ttu-id="88cb2-111">Domyślnie <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> używa <xref:System.IdentityModel.ProtectedDataCookieTransform> klasy, która używa interfejsu API ochrony danych (DPAPI), aby chronić tokenu sesji.</span><span class="sxs-lookup"><span data-stu-id="88cb2-111">By default, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> uses the <xref:System.IdentityModel.ProtectedDataCookieTransform> class, which uses the Data Protection API (DPAPI), to protect the session token.</span></span> <span data-ttu-id="88cb2-112">DPAPI zapewnia ochronę przy użyciu poświadczeń użytkownika lub komputera i przechowuje dane klucza w profilu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="88cb2-112">The DPAPI provides protection by using the user or machine credentials and stores the key data in the user profile.</span></span>  
  
-   <span data-ttu-id="88cb2-113">Używa domyślnej, wykonania w pamięci <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy do przechowywania i przetwarzania tokenu sesji.</span><span class="sxs-lookup"><span data-stu-id="88cb2-113">It uses a default, in-memory implementation of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class to store and process the session token.</span></span>  
  
 <span data-ttu-id="88cb2-114">Te ustawienia domyślne działają w scenariuszach, w których aplikacja RP jest wdrażana na pojedynczym komputerze; Jednak po wdrożeniu na farmie sieci web każde żądanie HTTP mogą być wysyłane do i przetwarzane przez inne wystąpienie aplikacji planu odzyskiwania uruchomiony na innym komputerze.</span><span class="sxs-lookup"><span data-stu-id="88cb2-114">These default settings work in scenarios in which the RP application is deployed on a single computer; however, when deployed in a web farm, each HTTP request may be sent to and processed by a different instance of the RP application running on a different computer.</span></span> <span data-ttu-id="88cb2-115">Domyślne ustawienia WIF opisane powyżej w tym scenariuszu nie będą działać, ponieważ token ochrony i buforowania tokenu są zależne od określonego komputera.</span><span class="sxs-lookup"><span data-stu-id="88cb2-115">In this scenario, the default WIF settings described above will not work because both token protection and token caching are dependent on a specific computer.</span></span>  
  
 <span data-ttu-id="88cb2-116">Aby wdrożyć aplikację planu odzyskiwania w farmie sieci web, należy upewnić przetwarzania tokenów sesji (a także powtórzony tokenów) nie jest zależna od aplikacja była uruchomiona na określonym komputerze.</span><span class="sxs-lookup"><span data-stu-id="88cb2-116">To deploy an RP application in a web farm, you must ensure that the processing of session tokens (as well as of replayed tokens) is not dependent on the application running on a specific computer.</span></span> <span data-ttu-id="88cb2-117">Aby zrobić to do wdrożenia aplikacji planu odzyskiwania, tak aby były używane funkcje udostępniane przez platformę ASP.NET `<machineKey>` element konfiguracji zawiera systemy buforowania rozproszonego przetwarzania tokenów sesji i odtwarzany tokenów.</span><span class="sxs-lookup"><span data-stu-id="88cb2-117">One way to do this is to implement your RP application so that it uses the functionality provided by the ASP.NET `<machineKey>` configuration element and provides distributed caching for processing session tokens and replayed tokens.</span></span> <span data-ttu-id="88cb2-118">`<machineKey>` Element umożliwia określenie klucze wymagane do weryfikacji, szyfrowania i odszyfrowywania tokenów w pliku konfiguracji, który umożliwia określenie tych samych kluczy na różnych komputerach w farmie sieci web.</span><span class="sxs-lookup"><span data-stu-id="88cb2-118">The `<machineKey>` element allows you to specify the keys needed to validate, encrypt, and decrypt tokens in a configuration file, which enables you to specify the same keys on different computers in the web farm.</span></span> <span data-ttu-id="88cb2-119">WIF zawiera specjalne sesji programu obsługi tokenów, <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, która chroni tokeny przy użyciu kluczy określona w `<machineKey>` elementu.</span><span class="sxs-lookup"><span data-stu-id="88cb2-119">WIF provides a specialized session token handler, the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, that protects tokens by using the keys specified in the `<machineKey>` element.</span></span> <span data-ttu-id="88cb2-120">Do wdrożenia tej strategii, należy wykonać następujące wytyczne:</span><span class="sxs-lookup"><span data-stu-id="88cb2-120">To implement this strategy, you can follow these guidelines:</span></span>  
  
-   <span data-ttu-id="88cb2-121">Za pomocą programu ASP.NET `<machineKey>` element w konfiguracji, aby jawnie określić klucze podpisywania i szyfrowania, które mogą być używane na komputerach w farmie.</span><span class="sxs-lookup"><span data-stu-id="88cb2-121">Use the ASP.NET `<machineKey>` element in configuration to explicitly specify signing and encryption keys that can be used across computers in the farm.</span></span> <span data-ttu-id="88cb2-122">Następujący kod XML zawiera specyfikację `<machineKey>` elementu w obszarze `<system.web>` w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="88cb2-122">The following XML shows the specification of the `<machineKey>` element under the `<system.web>` element in a configuration file.</span></span>  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
-   <span data-ttu-id="88cb2-123">Konfigurowanie aplikacji do korzystania z <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> przez dodanie go do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="88cb2-123">Configure the application to use the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> by adding it to the token handler collection.</span></span> <span data-ttu-id="88cb2-124">Należy najpierw usunąć <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (lub pochodny żadnych obsługi <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy) z kolekcji programu obsługi tokenów, jeśli program obsługi jest obecny.</span><span class="sxs-lookup"><span data-stu-id="88cb2-124">You must first remove the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (or any handler derived from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class) from the token handler collection if such a handler is present.</span></span> <span data-ttu-id="88cb2-125"><xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> Używa <xref:System.IdentityModel.Services.MachineKeyTransform> klasy, która chroni dane pliku cookie sesji przy użyciu kryptograficznych materiałów, określonych w `<machineKey>` elementu.</span><span class="sxs-lookup"><span data-stu-id="88cb2-125">The <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> uses the <xref:System.IdentityModel.Services.MachineKeyTransform> class, which protects the session cookie data by using the cryptographic material specified in the `<machineKey>` element.</span></span> <span data-ttu-id="88cb2-126">Następujący kod XML przedstawiono sposób dodawania <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="88cb2-126">The following XML shows how to add the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> to a token handler collection.</span></span>  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
-   <span data-ttu-id="88cb2-127">Pochodzić od <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> i wdrożenie rozproszone buforowania, czyli pamięci podręcznej, który jest dostępny ze wszystkich komputerów w farmie serwerów, na którym planu odzyskiwania mogą zostać uruchomione.</span><span class="sxs-lookup"><span data-stu-id="88cb2-127">Derive from <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> and implement distributed caching, that is, a cache that is accessible from all computers in the farm on which the RP might run.</span></span> <span data-ttu-id="88cb2-128">Konfigurowanie planu odzyskiwania, aby użyć rozproszonej pamięci podręcznej, określając [ \<sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="88cb2-128">Configure the RP to use your distributed cache by specifying the [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element in the configuration file.</span></span> <span data-ttu-id="88cb2-129">Można zastąpić <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> metody w klasie pochodnej, aby zaimplementować elementy podrzędne `<sessionSecurityTokenCache>` elementu, jeśli są wymagane.</span><span class="sxs-lookup"><span data-stu-id="88cb2-129">You can override the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> method in your derived class to implement child elements of the `<sessionSecurityTokenCache>` element if they are required.</span></span>  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!—optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     <span data-ttu-id="88cb2-130">Jednym ze sposobów zaimplementować systemy buforowania rozproszonego jest zapewnienie WCF frontonu dla niestandardowych pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="88cb2-130">One way to implement distributed caching is to provide a WCF front end for your custom cache.</span></span> <span data-ttu-id="88cb2-131">Aby uzyskać więcej informacji o implementacji WCF, buforowanie usługi, zobacz [usługi WCF buforowanie](#BKMK_TheWCFCachingService).</span><span class="sxs-lookup"><span data-stu-id="88cb2-131">For more information about implementing a WCF caching service, see [The WCF Caching Service](#BKMK_TheWCFCachingService).</span></span> <span data-ttu-id="88cb2-132">Aby uzyskać więcej informacji o implementacji klienta WCF, służącego do wywoływania usługi buforowania aplikacji planu odzyskiwania, zobacz [WCF buforowanie klient](#BKMK_TheWCFClient).</span><span class="sxs-lookup"><span data-stu-id="88cb2-132">For more information about implementing a WCF client that the RP application can use to call the caching service, see [The WCF Caching Client](#BKMK_TheWCFClient).</span></span>  
  
-   <span data-ttu-id="88cb2-133">W przypadku wykrycia przez aplikację tokenów powtórzony należy wykonać podobne rozproszonej pamięci podręcznej strategii dla pamięci podręcznej powtórzeń tokenów przez wynikających z <xref:System.IdentityModel.Tokens.TokenReplayCache> i wskazujący Twojej powtórzeń tokenów buforowanie usługi w [ \< tokenReplayCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="88cb2-133">If your application detects replayed tokens you must follow a similar distributed caching strategy for the token replay cache by deriving from <xref:System.IdentityModel.Tokens.TokenReplayCache> and pointing to your token replay caching service in the [\<tokenReplayCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) configuration element.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="88cb2-134">Wszystkie przykładowe XML i kodu w tym temacie jest pobierana z [ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) próbki (http://go.microsoft.com/fwlink/?LinkID=248408).</span><span class="sxs-lookup"><span data-stu-id="88cb2-134">All of the example XML and code in this topic is taken from the [ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) (http://go.microsoft.com/fwlink/?LinkID=248408) sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="88cb2-135">Przykłady w tym temacie podano jako — jest i nie są przeznaczone do użycia w kodzie produkcyjnym bez żadnych modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="88cb2-135">The examples in this topic are provided as-is and are not intended to be used in production code without modification.</span></span>  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a><span data-ttu-id="88cb2-136">Buforowanie usługi WCF</span><span class="sxs-lookup"><span data-stu-id="88cb2-136">The WCF Caching Service</span></span>  
 <span data-ttu-id="88cb2-137">Następujący interfejs definiuje kontrakt między usługą buforowania WCF i klienta WCF, używany przez aplikację jednostki uzależnionej strony do komunikowania się z nim.</span><span class="sxs-lookup"><span data-stu-id="88cb2-137">The following interface defines the contract between the WCF caching service and the WCF client used by the relying party application to communicate with it.</span></span> <span data-ttu-id="88cb2-138">Zasadniczo udostępnia metody <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy jako operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="88cb2-138">It essentially exposes the methods of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class as service operations.</span></span>  
  
```  
[ServiceContract()]  
public interface ISessionSecurityTokenCacheService  
{  
    [OperationContract]  
    void AddOrUpdate(string endpointId, string contextId, string keyGeneration, SessionSecurityToken value, DateTime expiryTime);  
  
    [OperationContract]  
    IEnumerable<SessionSecurityToken> GetAll(string endpointId, string contextId);  
  
    [OperationContract]  
    SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration);  
  
    [OperationContract(Name = "RemoveAll")]  
    void RemoveAll(string endpointId, string contextId);  
  
    [OperationContract(Name = "RemoveAllByEndpointId")]  
    void RemoveAll(string endpointId);  
  
    [OperationContract]  
    void Remove(string endpointId, string contextId, string keyGeneration);  
}  
```  
  
 <span data-ttu-id="88cb2-139">Poniższy kod przedstawia implementację usługi WCF buforowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="88cb2-139">The following code shows the implementation of the WCF caching service.</span></span> <span data-ttu-id="88cb2-140">W tym przykładzie wartość domyślna implementowane przez WIF pamięci podręcznej tokenu sesji w pamięci jest używany.</span><span class="sxs-lookup"><span data-stu-id="88cb2-140">In this example, the default, in-memory session token cache implemented by WIF is used.</span></span> <span data-ttu-id="88cb2-141">Alternatywnie można zaimplementować trwałej pamięci podręcznej przechowywana w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="88cb2-141">Alternatively, you could implement a durable cache backed by a database.</span></span> <span data-ttu-id="88cb2-142">`ISessionSecurityTokenCacheService`definiuje interfejs przedstawionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="88cb2-142">`ISessionSecurityTokenCacheService` defines the interface shown above.</span></span> <span data-ttu-id="88cb2-143">W tym przykładzie nie wszystkie metody, musi implementować interfejs są wyświetlane dla skrócenia.</span><span class="sxs-lookup"><span data-stu-id="88cb2-143">In this example, not all of the methods required to implement the interface are shown for brevity.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace WcfSessionSecurityTokenCacheService  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    public class SessionSecurityTokenCacheService : ISessionSecurityTokenCacheService  
    {  
        SessionSecurityTokenCache internalCache;  
  
        // sets the internal cache used by the service to the default WIF in-memory cache.  
        public SessionSecurityTokenCacheService()  
        {  
            internalCache = new IdentityModelCaches().SessionSecurityTokenCache;  
        }  
  
        ...  
  
        public SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration)  
        {  
            // Delegates to the default, in-memory MruSessionSecurityTokenCache used by WIF  
            SessionSecurityToken token = internalCache.Get(new SessionSecurityTokenCacheKey(endpointId, GetContextId(contextId), GetKeyGeneration(keyGeneration)));  
            return token;  
        }  
  
        ...  
  
        private static UniqueId GetContextId(string contextIdString)  
        {  
            return contextIdString == null ? null : new UniqueId(contextIdString);  
        }  
  
        private static UniqueId GetKeyGeneration(string keyGenerationString)  
        {  
            return keyGenerationString == null ? null : new UniqueId(keyGenerationString);  
        }  
    }  
}  
```  
  
<a name="BKMK_TheWCFClient"></a>   
## <a name="the-wcf-caching-client"></a><span data-ttu-id="88cb2-144">Buforowanie klienta WCF</span><span class="sxs-lookup"><span data-stu-id="88cb2-144">The WCF Caching Client</span></span>  
 <span data-ttu-id="88cb2-145">W tej sekcji przedstawiono implementacji klasy, która jest pochodną <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> oraz że delegatów wywołania do usługi buforowania.</span><span class="sxs-lookup"><span data-stu-id="88cb2-145">This section shows the implementation of a class that derives from <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> and that delegates calls to the caching service.</span></span> <span data-ttu-id="88cb2-146">Konfigurowanie aplikacji RP do korzystania z tej klasy przy użyciu [ \<sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element jak następujący kod XML</span><span class="sxs-lookup"><span data-stu-id="88cb2-146">You configure the RP application to use this class through the [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element as in the following XML</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 <span data-ttu-id="88cb2-147">Przesłonięć klasy <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> metodę, aby uzyskać punkt końcowy usługi z niestandardowego `<cacheServiceAddress>` elementem podrzędnym `<sessionSecurityTokenCache>` elementu.</span><span class="sxs-lookup"><span data-stu-id="88cb2-147">The class overrides the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> method to get the service endpoint from the custom `<cacheServiceAddress>` child element of the `<sessionSecurityTokenCache>` element.</span></span> <span data-ttu-id="88cb2-148">Używa tego punktu końcowego, aby zainicjować `ISessionSecurityTokenCacheService` kanału, przez który może komunikować się z usługą.</span><span class="sxs-lookup"><span data-stu-id="88cb2-148">It uses this endpoint to initialize an `ISessionSecurityTokenCacheService` channel over which it can communicate with the service.</span></span>  <span data-ttu-id="88cb2-149">W tym przykładzie nie wszystkie metody wymagane do zaimplementowania <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy są wyświetlane dla skrócenia.</span><span class="sxs-lookup"><span data-stu-id="88cb2-149">In this example, not all of the methods required to implement the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class are shown for brevity.</span></span>  
  
```  
using System;  
using System.Configuration;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace CacheLibrary  
{  
    /// <summary>  
    /// This class acts as a proxy to the WcfSessionSecurityTokenCacheService.  
    /// </summary>  
    public class SharedSessionSecurityTokenCache : SessionSecurityTokenCache, ICustomIdentityConfiguration  
    {  
        private ISessionSecurityTokenCacheService WcfSessionSecurityTokenCacheServiceClient;  
  
        internal SharedSessionSecurityTokenCache()  
        {  
        }  
  
        /// <summary>  
        /// Creates a client channel to call the service host.  
        /// </summary>  
        protected void Initialize(string cacheServiceAddress)  
        {  
            if (this.WcfSessionSecurityTokenCacheServiceClient != null)  
            {  
                return;  
            }  
  
            ChannelFactory<ISessionSecurityTokenCacheService> cf = new ChannelFactory<ISessionSecurityTokenCacheService>(  
                new WS2007HttpBinding(SecurityMode.None),  
                new EndpointAddress(cacheServiceAddress));  
            this.WcfSessionSecurityTokenCacheServiceClient = cf.CreateChannel();  
        }  
  
        #region SessionSecurityTokenCache Members  
        // Delegates the following operations to the centralized session security token cache service in the web farm.  
  
        ...  
  
        public override SessionSecurityToken Get(SessionSecurityTokenCacheKey key)  
        {  
            return this.WcfSessionSecurityTokenCacheServiceClient.Get(key.EndpointId, GetContextIdString(key), GetKeyGenerationString(key));  
        }  
  
        ...  
  
        #endregion  
  
        #region ICustomIdentityConfiguration Members  
        // Called from configuration infrastructure to load custom elements  
        public void LoadCustomConfiguration(XmlNodeList nodeList)  
        {  
            // Retrieve the endpoint address of the centralized session security token cache service running in the web farm  
            if (nodeList.Count == 0)  
            {  
                throw new ConfigurationException("No child config element found under <sessionSecurityTokenCache>.");  
            }  
  
            XmlElement cacheServiceAddressElement = nodeList.Item(0) as XmlElement;  
            if (cacheServiceAddressElement.LocalName != "cacheServiceAddress")  
            {  
                throw new ConfigurationException("First child config element under <sessionSecurityTokenCache> is expected to be <cacheServiceAddress>.");  
            }  
  
            string cacheServiceAddress = null;  
            if (cacheServiceAddressElement.Attributes["url"] != null)  
            {  
                cacheServiceAddress = cacheServiceAddressElement.Attributes["url"].Value;  
            }  
            else  
            {  
                throw new ConfigurationException("<cacheServiceAddress> is expected to contain a 'url' attribute.");  
            }  
  
            // Initialize the proxy to the WebFarmSessionSecurityTokenCacheService  
            this.Initialize(cacheServiceAddress);  
        }  
        #endregion  
  
        private static string GetKeyGenerationString(SessionSecurityTokenCacheKey key)  
        {  
            return key.KeyGeneration == null ? null : key.KeyGeneration.ToString();  
        }  
  
        private static string GetContextIdString(SessionSecurityTokenCacheKey key)  
        {  
            return GetContextIdString(key.ContextId);  
        }  
  
        private static string GetContextIdString(UniqueId contextId)  
        {  
            return contextId == null ? null : contextId.ToString();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="88cb2-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88cb2-150">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>  
 [<span data-ttu-id="88cb2-151">Zarządzanie sesjami WIF</span><span class="sxs-lookup"><span data-stu-id="88cb2-151">WIF Session Management</span></span>](../../../docs/framework/security/wif-session-management.md)