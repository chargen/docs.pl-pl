---
title: "Najlepsze praktyki: Elementy pośredniczące"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3185761ef784051c7508c3684d46997521483f04
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="best-practices-intermediaries"></a><span data-ttu-id="458be-102">Najlepsze praktyki: Elementy pośredniczące</span><span class="sxs-lookup"><span data-stu-id="458be-102">Best Practices: Intermediaries</span></span>
<span data-ttu-id="458be-103">Należy uważać poprawnie obsłużyć błędy podczas wywoływania metody pośredników, aby upewnić się, że kanały po stronie usługi na pośrednik zostały prawidłowo zamknięte.</span><span class="sxs-lookup"><span data-stu-id="458be-103">Care must be taken to handle faults correctly when calling intermediaries to make sure service side channels on the intermediary are closed properly.</span></span>  
  
 <span data-ttu-id="458be-104">Rozważmy poniższy scenariusz.</span><span class="sxs-lookup"><span data-stu-id="458be-104">Consider the following scenario.</span></span> <span data-ttu-id="458be-105">Klient nawiązuje połączenie pośrednika, który wywołuje usługi zaplecza.</span><span class="sxs-lookup"><span data-stu-id="458be-105">A client makes a call to an intermediary which then calls a back-end service.</span></span>  <span data-ttu-id="458be-106">Usługi zaplecza definiuje kontrakt nie błędu, więc winy wyjątek od tej usługi będzie traktowana jako błąd wyrażeniami bez typu.</span><span class="sxs-lookup"><span data-stu-id="458be-106">The back-end service defines no fault contract, so any fault thrown from that service will be treated as an un-typed fault.</span></span>  <span data-ttu-id="458be-107">Zwraca usługi zaplecza <xref:System.ApplicationException> i WCF poprawnie przerywa kanału po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="458be-107">The back-end service throws an <xref:System.ApplicationException> and WCF correctly aborts the service-side channel.</span></span> <span data-ttu-id="458be-108"><xref:System.ApplicationException> Następnie powierzchnie <xref:System.ServiceModel.FaultException> który jest zgłaszany do pośrednika.</span><span class="sxs-lookup"><span data-stu-id="458be-108">The <xref:System.ApplicationException> then surfaces as a <xref:System.ServiceModel.FaultException> that is thrown to the intermediary.</span></span> <span data-ttu-id="458be-109">Ponownie zgłasza wyjątek pośrednik <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="458be-109">The intermediary re-throws the <xref:System.ApplicationException>.</span></span> <span data-ttu-id="458be-110">Usługi WCF interpretuje jako błąd wyrażeniami bez typu z pośrednik i przekazuje je do klienta.</span><span class="sxs-lookup"><span data-stu-id="458be-110">WCF interprets this as an un-typed fault from the intermediary and forwards it on to the client.</span></span> <span data-ttu-id="458be-111">Po odebraniu usterki, zarówno klient, jak i pośrednik fault ich kanały po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="458be-111">Upon receiving the fault, both the intermediary and the client fault their client-side channels.</span></span> <span data-ttu-id="458be-112">Kanału po stronie usługi pośrednika jednak pozostanie otwarty, ponieważ WCF nie może ustalić, czy błąd jest krytyczny.</span><span class="sxs-lookup"><span data-stu-id="458be-112">The intermediary’s service-side channel however remains open because WCF doesn’t know the fault is fatal.</span></span>  
  
 <span data-ttu-id="458be-113">Najlepszym rozwiązaniem w tym scenariuszu jest wykryć, czy jest krytyczny błąd przesyłanych przez usługę, a jeśli tak pośrednik powinien fault kanału po stronie serwera, jak pokazano w poniższy fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="458be-113">The best practice in this scenario is to detect if the fault coming from the service is fatal and if so the intermediary should fault its service-side channel as shown in the following code snippet.</span></span>  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    Else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="458be-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="458be-114">See Also</span></span>  
 [<span data-ttu-id="458be-115">Obsługa błędów programu WCF</span><span class="sxs-lookup"><span data-stu-id="458be-115">WCF Error Handling</span></span>](../../../docs/framework/wcf/wcf-error-handling.md)  
 [<span data-ttu-id="458be-116">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="458be-116">Specifying and Handling Faults in Contracts and Services</span></span>](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)