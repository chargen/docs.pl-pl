---
title: '&lt;UdpDiscoveryEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: 95c6550352d8f100c8674c2e7f630fcf55da01e2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltudpdiscoveryendpointgt"></a>&lt;UdpDiscoveryEndpoint&gt;
Ten element konfiguracji definiuje standardowy punkt końcowy, który jest wstępnie konfigurowany dla operacji odnajdowania za pośrednictwem protokołu UDP powiązanie multiemisji. Ten punkt końcowy ma stały kontraktu i obsługuje dwie wersje protokołu WS-Discovery. Ponadto ma stałym powiązaniem UDP i domyślny adres zgodnie ze specyfikacją WS-Discovery (WS-Discovery kwietnia 2005 lub WS-Discovery w wersji 1.1).  
  
 \<system.ServiceModel>  
\<standardEndpoints >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <discoveryEndpoint>           <standardEndpoint                  discoveryMode="Adhoc/Managed"                  discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"                  maxResponseDelay="Timespan"                  multicastAddress="Uri"                   name="String" />       </discoveryEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|discoveryMode|Ciąg, który określa tryb protokół RDP. Prawidłowe wartości to "Ad hoc" i "Zarządzany". W trybie zarządzanym protokołu zależy od serwera Proxy odnajdywania, która działa jako repozytorium wykrywalny usług. W trybie ad hoc wymagane używany protokół UDP mechanizmu multiemisji można znaleźć dostępne usługi. Ta wartość jest typu <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.|  
|discoveryVersion|Ciąg, który określa jeden z dwóch wersji protokołu WS-Discovery. Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005. Ta wartość jest typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.|  
|maxResponseDelay|Wartość Timespan określający maksymalną wartość opóźnienia odnajdywania protokołu będzie czekać przed wysłaniem niektóre komunikaty, takie jak sondowania Match lub rozwiązać dopasowania.<br /><br /> Jeśli wszystkie ProbeMatches są wysyłane w tym samym czasie, może spowodować storm sieci. Aby temu zapobiec, ProbeMatches są wysyłane z losowego opóźnienia między każdym ProbeMatch. Opóźnienie losowe jest z zakresu od 0 do wartości tego atrybutu. Jeśli ten atrybut jest ustawiony na 0, ProbeMatches komunikaty są wysyłane w pętli ścisłej bez opóźnień. W przeciwnym razie ProbeMatches komunikaty są wysyłane z niektórych losowe opóźnienie tak, aby całkowity czas wykonywania wszystkich wysyłać ProbeMatches nie przekracza maxResponseDelay. Ta wartość ma zastosowanie tylko dla usług, nie jest on używany przez klientów.|  
|multicastAddress|Identyfikator Uri, który określa adres multiemisji do użycia na potrzeby wysyłania i odbierania wiadomości odnajdywania. Wartość domyślna to adres multiemisji jako zgodna ze specyfikacją protokołu.|  
|`name`|Ciąg określający nazwę Konfiguracja standardowego punktu końcowego. Nazwa jest używana w `endpointConfiguration` atrybutu punktu końcowego usługi, aby połączyć standardowy punkt końcowy do konfiguracji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<udpTransportSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|Kolekcja ustawień, które pozwalają na skonfigurowanie transportu UDP dla punktu końcowego protokołu UDP.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowanych punktów końcowych z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano nasłuchiwanie odnajdywania komunikaty za pośrednictwem protokołu UDP usługi multiemisji transportu.  
  
```xml
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <endpoint binding="basicHttpBinding"   
              address="calculator" 
              contract="ICalculatorService" />  
    <endpoint name="DiscoveryEndpoint"  
              kind="udpDiscoveryEndpoint" />  
  </service>  
  <standardEndpoints>  
    <udpDiscoveryEndpoint>  
      <standardEndpoint name="DiscoveryEndpoint"                         
                        version="WSDiscoveryApril2005" />  
    </udpDiscoveryEndpoint>  
  </standardEndpoints>
</services>
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
