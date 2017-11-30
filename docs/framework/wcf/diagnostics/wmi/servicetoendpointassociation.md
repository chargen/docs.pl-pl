---
title: ServiceToEndpointAssociation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d2755294ba02b4d67bd7f62cf020a44525874d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation
Mapuje usługi do punktu końcowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa ServiceToEndpointAssociation nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa ServiceToEndpointAssociation ma następujące właściwości:  
  
### <a name="ref"></a>ref  
 Typ danych: usługi  
  
 Dostęp typu: tylko do odczytu  
Kwalifikatory: klucz  
  
 Usługa skojarzona z punktem końcowym.  
  
### <a name="ref"></a>ref  
 Typ danych: punktu końcowego  
  
 Dostęp typu: tylko do odczytu  
Kwalifikatory: klucz  
  
 Punkt końcowym skojarzony z usługą.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|