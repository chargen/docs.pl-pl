---
title: "CorFieldAttr — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorFieldAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorFieldAttr
helpviewer_keywords: CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b199764ea0fb2d02b01d7cf04d1fa8fad743109f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corfieldattr-enumeration"></a><span data-ttu-id="8ff44-102">CorFieldAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8ff44-102">CorFieldAttr Enumeration</span></span>
<span data-ttu-id="8ff44-103">Zawiera wartości, które opisują metadanych pola.</span><span class="sxs-lookup"><span data-stu-id="8ff44-103">Contains values that describe metadata about a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ff44-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ff44-104">Syntax</span></span>  
  
```  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="8ff44-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8ff44-105">Members</span></span>  
  
|<span data-ttu-id="8ff44-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8ff44-106">Member</span></span>|<span data-ttu-id="8ff44-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8ff44-107">Description</span></span>|  
|------------|-----------------|  
|`fdFieldAccessMask`|<span data-ttu-id="8ff44-108">Określa informacje o ułatwieniach dostępu.</span><span class="sxs-lookup"><span data-stu-id="8ff44-108">Specifies accessibility information.</span></span>|  
|`fdPrivateScope`|<span data-ttu-id="8ff44-109">Określa, czy pole nie może być przywoływany.</span><span class="sxs-lookup"><span data-stu-id="8ff44-109">Specifies that the field cannot be referenced.</span></span>|  
|`fdPrivate`|<span data-ttu-id="8ff44-110">Określa, że pole jest dostępne tylko dla jego typu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="8ff44-110">Specifies that the field is accessible only by its parent type.</span></span>|  
|`fdFamANDAssem`|<span data-ttu-id="8ff44-111">Określa, że pole jest dostępne dla klas pochodnych w jego zestaw.</span><span class="sxs-lookup"><span data-stu-id="8ff44-111">Specifies that the field is accessible by derived classes in its assembly.</span></span>|  
|`fdAssembly`|<span data-ttu-id="8ff44-112">Określa, że pole jest dostępne dla wszystkich typów w zestawie jej.</span><span class="sxs-lookup"><span data-stu-id="8ff44-112">Specifies that the field is accessible by all types in its assembly.</span></span>|  
|`fdFamily`|<span data-ttu-id="8ff44-113">Określa, czy pole jest dostępne tylko dla jego typu i klasach pochodnych.</span><span class="sxs-lookup"><span data-stu-id="8ff44-113">Specifies that the field is accessible only by its type and derived classes.</span></span>|  
|`fdFamORAssem`|<span data-ttu-id="8ff44-114">Określa, czy pole jest dostępny, za pomocą klasy pochodne i wszystkie typy w jego zestaw.</span><span class="sxs-lookup"><span data-stu-id="8ff44-114">Specifies that the field is accessible by derived classes and by all types in its assembly.</span></span>|  
|`fdPublic`|<span data-ttu-id="8ff44-115">Określa, że pole jest dostępne dla wszystkich typów z widocznością tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="8ff44-115">Specifies that the field is accessible by all types with visibility of this scope.</span></span>|  
|`fdStatic`|<span data-ttu-id="8ff44-116">Określa, że pole jest elementem członkowskim jego typu, a nie elementu członkowskiego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8ff44-116">Specifies that the field is a member of its type rather than an instance member.</span></span>|  
|`fdInitOnly`|<span data-ttu-id="8ff44-117">Określa, że nie można zmienić pola po jego inicjowania.</span><span class="sxs-lookup"><span data-stu-id="8ff44-117">Specifies that the field cannot be changed after it is initialized.</span></span>|  
|`fdLiteral`|<span data-ttu-id="8ff44-118">Określa, czy wartość pola jest stałą czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8ff44-118">Specifies that the field value is a compile-time constant.</span></span>|  
|`fdNotSerialized`|<span data-ttu-id="8ff44-119">Określa, czy pole nie jest serializowany, gdy jej typ jest zdalny.</span><span class="sxs-lookup"><span data-stu-id="8ff44-119">Specifies that the field is not serialized when its type is remoted.</span></span>|  
|`fdSpecialName`|<span data-ttu-id="8ff44-120">Określa, czy pole ma specjalne i że jego nazwa zawiera opis sposobu.</span><span class="sxs-lookup"><span data-stu-id="8ff44-120">Specifies that the field is special, and that its name describes how.</span></span>|  
|`fdPinvokeImpl`|<span data-ttu-id="8ff44-121">Określa, że implementacja pole jest przekazywany za pomocą funkcji PInvoke.</span><span class="sxs-lookup"><span data-stu-id="8ff44-121">Specifies that the field implementation is forwarded through PInvoke.</span></span>|  
|`fdReservedMask`|<span data-ttu-id="8ff44-122">Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="8ff44-122">Reserved for internal use by the common language runtime.</span></span>|  
|`fdRTSpecialName`|<span data-ttu-id="8ff44-123">Określa, że typowe metadane środowiska wykonawczego języka wewnętrznych interfejsów API należy sprawdzać kodowanie nazwy.</span><span class="sxs-lookup"><span data-stu-id="8ff44-123">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span></span>|  
|`fdHasFieldMarshal`|<span data-ttu-id="8ff44-124">Określa, czy pole zawiera informacji organizacyjnych.</span><span class="sxs-lookup"><span data-stu-id="8ff44-124">Specifies that the field contains marshaling information.</span></span>|  
|`fdHasDefault`|<span data-ttu-id="8ff44-125">Określa, czy pole ma wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="8ff44-125">Specifies that the field has a default value.</span></span>|  
|`fdHasFieldRVA`|<span data-ttu-id="8ff44-126">Określa, czy pole ma wirtualnego adresu względnego.</span><span class="sxs-lookup"><span data-stu-id="8ff44-126">Specifies that the field has a relative virtual address.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8ff44-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ff44-127">Requirements</span></span>  
 <span data-ttu-id="8ff44-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ff44-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ff44-129">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="8ff44-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8ff44-130">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ff44-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ff44-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ff44-131">See Also</span></span>  
 [<span data-ttu-id="8ff44-132">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="8ff44-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)