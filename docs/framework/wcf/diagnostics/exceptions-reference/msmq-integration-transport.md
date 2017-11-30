---
title: "Transport integracji usługi MSMQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bf9893a-fbd1-41fc-b6de-a41a44279936
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 49bde10ed614a97752f0a378e16c548eb605db32
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="msmq-integration-transport"></a>Transport integracji usługi MSMQ
W tym temacie wymieniono wszystkie wyjątki generowane przez Transport integracji usługi MSMQ.  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|MessageSizeMustBeInIntegerRange|Ta fabryka buforuje wiadomości, więc rozmiary wiadomości muszą być z zakresu liczb całkowitych.|  
|MsmqByteArrayBodyExpected|Wystąpiła niezgodność między formatem serializacji określonym i treści wiadomości MSMQ. Wiadomość nie może być wysyłane lub odbierane. Format serializacji ByteArray wymaga, aby treść wiadomości MSMQ była typu byte [].|  
|MsmqCannotDeserializeActiveXMessage|Wystąpił błąd serializacji ActiveX. Wiadomość nie może być wysyłane lub odbierane. Określony typ wariantu dla treści jest niezgodny z rzeczywistą treścią wiadomości MSMQ.|  
|MsmqCannotUseBodyTypeWithActiveXSerialization|Właściwości wiadomości są niezgodne. Wiadomość nie może być wysyłane lub odbierane. Właściwości wiadomości BodyType nie może być określony, jeśli został użyty format serializacji ActiveX.|  
|MsmqInvalidServiceOperationForMsmqIntegrationBinding|Nie można sprawdzić poprawności elementu MsmqIntegrationBinding. Nie można uruchomić punktu końcowego usługi. Określone powiązanie nie obsługuje podpisu metody dla operacji usługi określony w kontrakcie określony. Popraw operację usługi, aby użyć elementu MsmqIntegrationBinding.|  
|MsmqInvalidTypeDeserialization|Formantu ActiveX nie powiodło się, ponieważ nie można rozpoznać formatu serializacji. Wiadomość nie może być wysyłane lub odbierane.|  
|MsmqInvalidTypeSerialization|Nie rozpoznano typu variant. Formantu ActiveX nie powiodło się. Wiadomość nie może być wysyłane lub odbierane. Określony typ wariantu nie jest obsługiwane.|  
|MsmqStreamBodyExpected|Występuje niezgodność między formatem serializacji i treści zawartości. Komunikat nie może być wysyłane lub odbierane. Tylko treści strumienia typu mogą być wysyłane lub odbierane przy użyciu tryb serializacji strumienia.|