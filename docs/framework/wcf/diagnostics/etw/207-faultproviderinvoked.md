---
title: "207 — FaultProviderInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fe3698653be04119c84c5f423207458e9d033dc1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="4b540-102">207 — FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="4b540-102">207 - FaultProviderInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="4b540-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4b540-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4b540-104">ID</span><span class="sxs-lookup"><span data-stu-id="4b540-104">ID</span></span>|<span data-ttu-id="4b540-105">207</span><span class="sxs-lookup"><span data-stu-id="4b540-105">207</span></span>|  
|<span data-ttu-id="4b540-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="4b540-106">Keywords</span></span>|<span data-ttu-id="4b540-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4b540-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="4b540-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="4b540-108">Level</span></span>|<span data-ttu-id="4b540-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="4b540-109">Information</span></span>|  
|<span data-ttu-id="4b540-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="4b540-110">Channel</span></span>|<span data-ttu-id="4b540-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="4b540-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4b540-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4b540-112">Description</span></span>  
 <span data-ttu-id="4b540-113">To zdarzenie jest emitowany po `FaultProvider` została wywołana.</span><span class="sxs-lookup"><span data-stu-id="4b540-113">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4b540-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="4b540-114">Message</span></span>  
 <span data-ttu-id="4b540-115">Dyspozytor wywołał obiekt FaultProvider typu "%1" za pomocą wyjątku typu '%2'.</span><span class="sxs-lookup"><span data-stu-id="4b540-115">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4b540-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="4b540-116">Details</span></span>  
  
|<span data-ttu-id="4b540-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="4b540-117">Data Item Name</span></span>|<span data-ttu-id="4b540-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="4b540-118">Data Item Type</span></span>|<span data-ttu-id="4b540-119">Opis</span><span class="sxs-lookup"><span data-stu-id="4b540-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4b540-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="4b540-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="4b540-121">Imię i nazwisko CLR typu wywołanej `FaultProvider`.</span><span class="sxs-lookup"><span data-stu-id="4b540-121">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="4b540-122">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="4b540-122">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="4b540-123">Imię i nazwisko CLR wyjątku, który `FaultProvider` działał na.</span><span class="sxs-lookup"><span data-stu-id="4b540-123">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="4b540-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="4b540-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="4b540-125">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4b540-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="4b540-126">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="4b540-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="4b540-127">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="4b540-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="4b540-128">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="4b540-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4b540-129">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4b540-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|