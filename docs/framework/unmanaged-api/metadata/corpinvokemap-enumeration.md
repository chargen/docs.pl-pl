---
title: CorPinvokeMap — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: edb45c9ceefb242e5a72e8602dc93ecd39b2df09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap — Wyliczenie
Określa opcje dla wywołania funkcji PInvoke.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,   
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`pmNoMangle`|Użyj nazwy elementów członkowskich określonych.|  
|`pmCharSetMask`|Zastrzeżone.|  
|`pmCharSetNotSpec`|Zastrzeżone.|  
|`pmCharSetAnsi`|Kierowanie ciągi jako ciągi wielu bajtowych wartości znakowych.|  
|`pmCharSetUnicode`|Kierowanie ciągów Unicode 2-bajtowych znaków.|  
|`pmCharSetAuto`|Automatyczne kierowanie ciągów odpowiednio dla docelowego systemu operacyjnego. Wartość domyślna to Unicode na systemu Windows NT, Windows 2000, Windows XP i z rodziny Windows Server 2003; Wartość domyślna to ANSI w systemach Windows 98 i systemu Windows.|  
|`pmBestFitUseAssem`|Zastrzeżone.|  
|`pmBestFitEnabled`|Przeprowadź mapowanie najlepszego dopasowania znaków Unicode, których brakuje dokładnego dopasowania w zestawie znaków ANSI.|  
|`pmBestFitDisabled`|Nie wykonuj mapowanie najlepszego dopasowania znaków Unicode. W takim przypadku zostanie zastąpiona zmapować znakami "?".|  
|`pmBestFitMask`|Zastrzeżone.|  
|`pmThrowOnUnmappableCharUseAssem`|Zastrzeżone.|  
|`pmThrowOnUnmappableCharEnabled`|Zgłoś wyjątek, gdy znak zmapować napotka międzyoperacyjnego organizatora.|  
|`pmThrowOnUnmappableCharDisabled`|Nie Zgłoś wyjątek, gdy znak zmapować napotka międzyoperacyjnego organizatora.|  
|`pmThrowOnUnmappableCharMask`|Zastrzeżone|  
|`pmSupportsLastError`|Zezwalaj na wywoływany do wywołania Win32 `SetLastError` funkcja przed powrotem z metody oparte na atrybutach.|  
|`pmCallConvMask`|Zastrzeżone|  
|`pmCallConvWinapi`|Za pomocą platformy domyślnej konwencji wywoływania. Na przykład w systemie Windows wartość domyślna to `StdCall` i na Windows CE .NET jest `Cdecl`.|  
|`pmCallConvCdecl`|Użyj `Cdecl` konwencji wywoływania. W takim przypadku obiekt wywołujący czyści stosu. Dzięki temu wywoływanie funkcji z `varargs` (to znaczy, funkcje, które zaakceptować zmienną liczbę parametrów).|  
|`pmCallConvStdcall`|Użyj `StdCall` konwencji wywoływania. W takim przypadku wywoływany czyści stosu. Jest domyślnej konwencji wywołania wywoływanie niezarządzanych funkcji z platformą.|  
|`pmCallConvThiscall`|Użyj `ThisCall` konwencji wywoływania. W tym przypadku jest pierwszym parametrem `this` wskaźnik i są przechowywane w rejestrze ECX. Inne parametry są przenoszone na stosie. `ThisCall` Konwencji wywoływania są używane do wywoływania metod w klasach wyeksportowane z niezarządzanej DLL.|  
|`pmCallConvFastcall`|Zastrzeżone.|  
|`pmMaxValue`|Zastrzeżone.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
