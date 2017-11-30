---
title: 119 - WorkflowInstanceUpdatedRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32485d0a-dcdb-45bc-b1e3-79fa9ad9439b
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b838f764b1f86b0477dc797620dca5f99bb13d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="119---workflowinstanceupdatedrecord"></a>119 - WorkflowInstanceUpdatedRecord
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|119|  
|Słowa kluczowe|HealthMonitoring, WFTracking|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez uczestnika śledzenia zdarzeń systemu Windows po zaktualizowaniu wystąpienia przepływu pracy.  
  
## <a name="message"></a>Komunikat  
 TrackRecord = WorkflowInstanceUpdatedRecord, identyfikator wystąpienia = %1, RecordNumber = %2, EventTime = %3, obiekt ActivityDefinitionId = %4, stan = %5, OriginalDefinitionIdentity = %6, UpdatedDefinitionIdentity = %7, adnotacje = %8, ProfileName = %9  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Identyfikator wystąpienia|xs:GUID|Identyfikator wystąpienia przepływu pracy|  
|RecordNumber|xs:Long|Numer sekwencyjny emitowany rekordu|  
|eventTime|xs: DateTime|Godzina w formacie UTC podczas zdarzenia zostały wyemitowane|  
|Obiekt ActivityDefinitionId|xs:String|Nazwa działania głównego w przepływie pracy|  
|Stan|xs:String|Bieżący stan przepływu pracy.|  
|OriginalDefinitionIdentity|xs:String|Identyfikator oryginalnej definicji przepływu pracy|  
|UpdatedDefinitionIdentity|xs:String|Identyfikator definicji zaktualizowany przepływ pracy|  
|Adnotacje|xs:String|Adnotacje, które zostały dodane do tego zdarzenia. Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</elementu > \< /elementy >. Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar bufora ETW lub max ładunku zdarzenia ETW. Jeśli limity ETW przekracza rozmiar zdarzenia, a następnie zdarzenia został obcięty przez usunięcie adnotacje i zastąpienie wartości adnotacji z \<elementy >...  \< /elementy >.|  
|ProfileName|xs:String|Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowany|  
|WorkflowDefinitionIdentity|xs:String|Identyfikator definicji przepływu pracy|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|