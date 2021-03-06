---
title: IMetaDataDispenser::DefineScope — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11382f00839917185ba3c85b8fbae5c32d0b0d4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatadispenserdefinescope-method"></a>IMetaDataDispenser::DefineScope — Metoda
Tworzy nowy obszar w pamięci, w którym można utworzyć nowe metadane.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rclsid`  
 [in] Identyfikator CLSID wersji struktur metadanych ma zostać utworzony. Ta wartość musi być CLSID_CorMetaDataRuntime dla programu .NET Framework w wersji 2.0.  
  
 `dwCreateFlags`  
 [in] Flagi, które określają opcje. Ta wartość musi wynosić zero dla programu .NET Framework 2.0.  
  
 `riid`  
 [in] Uzyskanie identyfikatora IID interfejsu odpowiednie metadane zwrócone; obiekt wywołujący będą używać interfejsu, aby utworzyć nowe metadane.  
  
 Wartość `riid` należy określić jeden z interfejsów "Emituj". Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit lub IID_IMetaDataEmit2.  
  
 `ppIUnk`  
 [out] Wskaźnik do interfejsu zwrócony.  
  
## <a name="remarks"></a>Uwagi  
 `DefineScope` Tworzy zestaw tabel metadanych w pamięci, generuje unikatowy identyfikator GUID (identyfikator wersji modułu lub identyfikatora MVID) metadanych i tworzy wpis w tabeli modułu dla jednostki kompilacji jest emitowany.  
  
 Możesz dołączyć atrybuty do zakresu metadanych jako całość przy użyciu [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) lub [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) metody, zależnie od potrzeb.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataDispenser, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [IMetaDataDispenserEx, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
