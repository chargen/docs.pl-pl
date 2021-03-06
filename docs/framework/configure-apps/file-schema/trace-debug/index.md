---
title: Schemat ustawień śledzenia i debugowania
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [.NET Framework], trace and debug settings schema
- configuration schema [.NET Framework], trace and debug settings
- configuration settings [.NET Framework], tracing
- schema configuration settings
- configuration settings [.NET Framework], debugging
- trace listeners, trace and debug settings schema
- configuration sections [.NET Framework]
- elements [.NET Framework], trace and debug settings
ms.assetid: 277ca5f6-e1c4-41b6-a47f-3a67ce5b94ac
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4014f17cbbb4eb1bd2ec41d1fca5d4187ffa56b5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="trace-and-debug-settings-schema"></a>Schemat ustawień śledzenia i debugowania
Ustawienia śledzenia i debugowania Określ obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.  
  
 W poniższej tabeli opisano funkcję każdy element Ustawienia śledzenia i debugowania.  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|Dodaje odbiornika do `Listeners` kolekcji źródła śledzenia.|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Dodaje odbiornika do `Listeners` kolekcji.|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-sharedlisteners.md)|Dodaje odbiornika do `sharedListeners` kolekcji.|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|Określa poziom, gdy jest ustawiona przełącznik śledzenia.|  
|[\<Assert >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|Określa, czy wyświetlać okno komunikatu po wywołaniu <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metody; określa także nazwę pliku do zapisania komunikatów.|  
|[\<Wyczyść >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|Czyści `Listeners` kolekcji źródła śledzenia.|  
|[\<Wyczyść >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|Czyści `Listeners` kolekcji do śledzenia.|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|Dodaje filtr do odbiornika w `Listeners` kolekcji źródła śledzenia.|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|Dodaje filtr do odbiornika w `Listeners` kolekcji do śledzenia.|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|Dodaje filtr do odbiornika w `sharedListeners` kolekcji.|  
|[\<obiekty nasłuchujące >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|Określa odbiorników dla `Listeners` kolekcji źródła śledzenia.|  
|[\<obiekty nasłuchujące >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|Określa odbiorników dla `Listeners` kolekcji do śledzenia.|  
|[\<liczniki wydajności >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|Określa rozmiar pamięci globalnej współużytkowane przez liczniki wydajności.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|Usuwa odbiornik z `Listeners` kolekcji do śledzenia.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|Usuwa odbiornik z `Listeners` kolekcji źródła śledzenia.|  
|[\<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|Zawiera nasłuchujących może odwoływać się wszystkie źródła lub element śledzenia.|  
|[\<źródeł >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|Zawiera źródła śledzenia, które inicjują śledzenia wiadomości.|  
|[\<źródło >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|Określa źródło śledzenia, który inicjuje śledzenia wiadomości.|  
|[\<przełączniki >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|Zawiera przełączniki śledzenia i poziom, gdzie są ustawione przełączniki śledzenia.|  
|[\<System.Diagnostics >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/system-diagnostics-element.md)|Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.|  
|[\<śledzenia >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|Zawiera nasłuchujących zbierania, przechowywania i trasy śledzenia wiadomości.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.Debug>  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
