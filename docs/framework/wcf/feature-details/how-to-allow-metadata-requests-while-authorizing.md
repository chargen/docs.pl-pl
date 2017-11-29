---
title: "Instrukcje: Zezwalanie na żądania metadanych podczas autoryzowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 103aba5118810064c1cafb7c82634ef000ced667
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a><span data-ttu-id="15d0f-102">Instrukcje: Zezwalanie na żądania metadanych podczas autoryzowania</span><span class="sxs-lookup"><span data-stu-id="15d0f-102">How To: Allow Metadata Requests While Authorizing</span></span>
<span data-ttu-id="15d0f-103">Podczas przeprowadzania niestandardowej autoryzacji może być konieczne Zezwalaj na żądania metadanych do przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="15d0f-103">During custom authorization, it may be necessary to allow a request for metadata to be processed.</span></span> <span data-ttu-id="15d0f-104">Poniższy temat przeprowadzi Cię przez kroki, aby zweryfikować takie żądanie.</span><span class="sxs-lookup"><span data-stu-id="15d0f-104">The following topic walks through the steps to validate such a request.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="15d0f-105">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] autoryzacji, zobacz [autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="15d0f-105"> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] authorization, see [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
### <a name="to-allow-metadata-requests-during-authorization"></a><span data-ttu-id="15d0f-106">Aby zezwolić na żądania metadanych podczas autoryzowania</span><span class="sxs-lookup"><span data-stu-id="15d0f-106">To allow metadata requests during authorization</span></span>  
  
1.  <span data-ttu-id="15d0f-107">Tworzenie rozszerzenia <xref:System.ServiceModel.ServiceAuthorizationManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="15d0f-107">Create an extension of the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
2.  <span data-ttu-id="15d0f-108">Zastąpienie <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="15d0f-108">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="15d0f-109">Metoda zwraca `true` lub `false` w zależności od tego, czy jest dozwolone autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="15d0f-109">The method returns `true` or `false` depending on whether authorization is allowed.</span></span> <span data-ttu-id="15d0f-110">Informacje o bieżącej procedury znajduje się w <xref:System.ServiceModel.OperationContext> przekazany jako parametr do metody.</span><span class="sxs-lookup"><span data-stu-id="15d0f-110">Information about the current procedure is found in the <xref:System.ServiceModel.OperationContext> passed as a parameter to the method.</span></span>  
  
3.  <span data-ttu-id="15d0f-111">Na zastąpienie zaznacz Nazwa kontraktu, przestrzeń nazw i akcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="15d0f-111">In the override, check the contract name, namespace, and the action as shown in the following example.</span></span> <span data-ttu-id="15d0f-112">Jeśli warunki są prawidłowe, zwracany jest`true.`</span><span class="sxs-lookup"><span data-stu-id="15d0f-112">If the conditions are valid, then return `true.`</span></span>  
  
4.  <span data-ttu-id="15d0f-113">Użyj punktów rozszerzalności fragmentów klasy.</span><span class="sxs-lookup"><span data-stu-id="15d0f-113">Use the extensibility point to employ the class.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="15d0f-114">[Porady: tworzenie Menedżera autoryzacji niestandardowej dla usługi](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="15d0f-114"> [How to: Create a Custom Authorization Manager for a Service](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="15d0f-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="15d0f-115">Example</span></span>  
 <span data-ttu-id="15d0f-116">Poniższy przykład przedstawia Przesłonięcie elementu <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="15d0f-116">The following example shows an override of the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span>  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="15d0f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15d0f-117">See Also</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [<span data-ttu-id="15d0f-118">Autoryzacji</span><span class="sxs-lookup"><span data-stu-id="15d0f-118">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [<span data-ttu-id="15d0f-119">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="15d0f-119">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)