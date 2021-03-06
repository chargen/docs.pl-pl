---
title: ICorProfilerObjectEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum
helpviewer_keywords:
- ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 13e1651c-9523-40ef-bfd7-87fb94519f8b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3478364a415b145bed879cda5cc5c41cf22254c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerobjectenum-interface"></a>ICorProfilerObjectEnum — Interfejs
Udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji zablokowane obiekty, które są generowane przez [Ngen.exe (Generator obrazu natywnego)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Clone, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-clone-method.md)|Pobiera wskaźnika interfejsu kopię `ICorProfilerObjectEnum` interfejsu.|  
|[GetCount, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-getcount-method.md)|Pobiera całkowitą liczbę obiektów zablokowane w kolekcji.|  
|[Next, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-next-method.md)|Pobiera określoną liczbę obiektów ciągłe z sekwencyjną kolekcją obiektów, zaczynając od modułu wyliczającego bieżącej pozycji w sekwencji.|  
|[Reset, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-reset-method.md)|Przesuwa kursor ten moduł wyliczający pozycji początkowej sekwencji.|  
|[Skip, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-skip-method.md)|Przesuwa kursor tego modułu wyliczającego z jego bieżącym położeniu, dzięki czemu określoną liczbę elementów są pomijane.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorProfilerObjectEnum` Interfejs jest moduł wyliczający. Umożliwia odbiorcy tablicy do ściągania elementów od nadawcy szybkością, który jest odpowiedni dla odbiornika. Innymi słowy odbiorca jest w stanie jawnie sterowanie przepływem elementów tablicy, zapobiegając problemy związane z przekazywanie dużych tablic jako parametrów metody.  
  
 Użyj [ICorProfilerInfo2::EnumModuleFrozenObjects](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md) uzyskać wskaźnik do `ICorProfilerObjectEnum` interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [EnumModuleFrozenObjects, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)
