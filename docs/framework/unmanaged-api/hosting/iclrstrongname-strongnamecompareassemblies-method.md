---
title: ICLRStrongName::StrongNameCompareAssemblies — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5020c31f590f527856f966ede512e98c07496ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a>ICLRStrongName::StrongNameCompareAssemblies — Metoda
Określa, czy dwa zestawy różnią się tylko ich podpisów silnej nazwy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszAssembly1`  
 [in] Ścieżka do pierwszego zestawu.  
  
 `wszAssembly2`  
 [in] Ścieżka do drugiego zestawu.  
  
 `pdwResult`  
 [out] Jedna z następujących wartości:  
  
-   `SN_CMP_DIFFERENT` (0) — określa, czy zestawy zawierać innych danych.  
  
-   `SN_CMP_IDENTICAL` (1) — określa, czy zestawy są dokładnie takie same, w tym ich podpisów i sumy kontrolnej.  
  
-   `SN_CMP_SIGONLY` (2) — określa, czy zestawy różnią się jedynie podpisu i sumy kontrolnej.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="remarks"></a>Uwagi  
 Podpis silnej nazwy zestawu składa się z zestawu tekst nazwę, wersję, kulturę i token klucza publicznego.  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
