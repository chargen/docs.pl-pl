---
title: Liczniki wydajności programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: 1d9e6b83a78967193c4cb0343f6c77560354a837
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-performance-counters"></a>Liczniki wydajności programu WCF
Windows Communication Foundation (WCF) zawiera duży zbiór liczników wydajności, aby ocenić wydajność aplikacji.  
  
## <a name="enabling-performance-counters"></a>Włączanie liczników wydajności  
 Liczniki wydajności dla usługi WCF można włączyć za pomocą pliku konfiguracji app.config usługi WCF w następujący sposób:  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 `performanceCounters` Atrybut można określać, aby włączyć liczniki wydajności dla określonego typu. Prawidłowe wartości to  
  
-   Wszystko: Wszystkie liczniki kategorii (ServiceModelService, ServiceModelEndpoint i ServiceModelOperation) są włączone.  
  
-   ServiceOnly: Tylko ServiceModelService kategorii liczników są włączone. Jest to wartość domyślna.  
  
-   Wyłączone: Liczniki wydajności modelu ServiceModel * są wyłączone.  
  
 Jeśli chcesz włączyć liczniki wydajności dla wszystkich aplikacji WCF, ustawienia konfiguracji można umieścić w pliku Machine.config.  Zobacz **zwiększyć rozmiar pamięci dla liczników wydajności** sekcji poniżej, aby uzyskać więcej informacji na temat konfigurowania wystarczającą ilość pamięci dla liczników wydajności na tym komputerze.  
  
 Jeśli używasz punkty rozszerzeń WCF, takich jak invokers operacja niestandardowa, powinny również Emituj liczniki wydajności. Jest to spowodowane zastosowanie punkcie rozszerzenia WCF może nie są już emitowane dane licznika wydajności standardowe w domyślnej ścieżce. Jeśli nie implementuje obsługi licznika wydajności ręczne, nie zobaczysz oczekiwane dane licznika wydajności.  
  
 Można również włączyć liczniki wydajności kod w następujący sposób  
  
```  
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## <a name="viewing-performance-data"></a>Wyświetlanie danych wydajności  
 Aby wyświetlić dane przechwycone przez liczniki wydajności, można użyć Monitora wydajności (Perfmon.exe) dołączoną do systemu Windows. Możesz uruchomić to narzędzie, przechodząc do **Start**i kliknij przycisk **Uruchom** i typu `perfmon.exe` w oknie dialogowym.  
  
> [!NOTE]
>  Wystąpienia liczników wydajności może zostać zwolniony przed ostatnim wiadomości są przetwarzane przez Dyspozytor punktu końcowego. Może to spowodować danych wydajności nie przechwycone kilka komunikatów.  
  
## <a name="increasing-memory-size-for-performance-counters"></a>Zwiększyć rozmiar pamięci dla liczników wydajności  
 Usługi WCF używa oddzielnych pamięci współużytkowanej jego kategorii licznika wydajności.  
  
 Domyślnie oddzielne pamięci współużytkowanej ustawiono kwartału rozmiar pamięci liczników wydajności globalnego. Domyślna pamięć licznika wydajności globalnego jest 524,288 bajtów. W związku z tym trzech kategorii licznika wydajności usługi WCF ma domyślny rozmiar około 128KB. W zależności od właściwości środowisko uruchomieniowe aplikacji WCF na maszynie, może wyczerpaniu pamięci liczników wydajności. W takim przypadku WCF zapisuje błąd w dzienniku zdarzeń aplikacji. Stany zawartości błędu nie można załadować licznika wydajności, czy wyjątek zawiera wpis "System.InvalidOperationException: za mało pamięci dla widoku pliku liczników niestandardowych." Jeśli śledzenie jest włączone na poziomie błąd, ten błąd jest również śledzone. Jeśli wyczerpaniu pamięci liczników wydajności kontynuowanie do uruchomienia aplikacji WCF z włączoną liczników wydajności może spowodować obniżenie wydajności. Jeśli jesteś administratorem komputera, należy skonfigurować ją przydzielić wystarczającej ilości pamięci do obsługi maksymalnie liczniki wydajności, które może występować w dowolnym momencie.  
  
 Można zmienić ilość pamięci liczników wydajności dla kategorii WCF w rejestrze. Aby to zrobić, należy dodać nową wartość DWORD o nazwie `FileMappingSize` do trzech następujących lokalizacji i ustaw ją na żądaną wartość w bajtach. Ponowny rozruch komputera, aby te zmiany są brane pod efekt.  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance  
  
 Gdy dużą liczbę obiektów (na przykład ServiceHost) są usuwane, ale oczekujących na przetworzenie zbierane pamięci `PrivateBytes` licznika wydajności zarejestruje wyjątkowo dużą liczbą. Aby rozwiązać ten problem, użytkownik może dodać własne liczniki specyficzne dla aplikacji, albo użyj `performanceCounters` atrybutu, aby włączyć liczniki tylko poziomu usług.  
  
## <a name="types-of-performance-counters"></a>Typy liczników wydajności  
 Liczniki wydajności są ograniczone do trzech różnych poziomów: usługi, punkt końcowy i operację.  
  
 Aby pobrać nazwę wystąpienia licznika wydajności przy użyciu usługi WMI. Na przykład  
  
-   Nazwa wystąpienia liczników usługi można uzyskać za pomocą usługi WMI [usługi](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) właściwość "CounterInstanceName" instancji.  
  
-   Nazwa wystąpienia liczników punktu końcowego można uzyskać za pomocą usługi WMI [punktu końcowego](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) właściwość "CounterInstanceName" instancji.  
  
-   Nazwa wystąpienia liczników operacji można otrzymać za pośrednictwem usługi WMI [punktu końcowego](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) wystąpienia metody "GetOperationCounterInstanceName".  
  
 Aby uzyskać więcej informacji dotyczących usługi WMI, zobacz [przy użyciu Instrumentacji zarządzania Windows dla diagnostyki](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
### <a name="service-performance-counters"></a>Liczniki wydajności usługi  
 Liczniki wydajności usługi zmierzyć zachowanie usługi jako całość i może służyć do diagnozowania wydajność całej usługi. Można go znaleźć w `ServiceModelService 4.0.0.0` obiekt wydajności w przypadku wyświetlania z Monitora wydajności. Wystąpienia są nazywane przy użyciu następującego wzorca:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 Licznik w zakresie usługi są agregowane z licznika w kolekcji punktów końcowych.  
  
 Liczniki wydajności służące do tworzenia wystąpienia usługi jest zwiększany, gdy jest tworzony nowy obiekt InstanceContext. Należy pamiętać, że tworzony jest nowy obiekt InstanceContext nawet po otrzymaniu wiadomości aktywowanie (z istniejącą usługę) lub gdy możesz połączyć się z wystąpieniem, z jedną sesję, zakończyć sesję i ponownego połączenia z innej sesji.  
  
### <a name="endpoint-performance-counters"></a>Liczniki wydajności punktu końcowego  
 Liczniki wydajności punktu końcowego umożliwiają wyszukiwanie danych w czasie wykonywania odbicia, jak punkt końcowy jest akceptowanie komunikatów. Można go znaleźć w `ServiceModelEndpoint 4.0.0.0` obiekt wydajności w przypadku wyświetlania korzystanie z Monitora wydajności. Wystąpienia są nazywane przy użyciu następującego wzorca:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Dane są podobne do czego są zbierane dla poszczególnych działań, ale tylko jest agregowana przez punkt końcowy.  
  
 Licznik w zakresie punktu końcowego są agregowane z liczników w to kolekcja operacji.  
  
> [!NOTE]
>  Jeśli dwa punkty końcowe mają identyczne nazwy i adresy, są mapowane do tego samego wystąpienia licznika.  
  
### <a name="operation-performance-counters"></a>Liczniki wydajności operacji  
 Liczniki wydajności operacji znajdują się w obszarze `ServiceModelOperation 4.0.0.0` obiekt wydajności w przypadku wyświetlania z Monitora wydajności. Każda operacja wymaga poszczególnych wystąpień. Oznacza to jeśli dany kontrakt operacji 10, 10 wystąpień licznika operacji są skojarzone z tej Umowy. Wystąpienia obiektu są nazywane przy użyciu następującego wzorca:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Ten licznik umożliwia pomiarów sposobu używania połączenia i jak wykonywanie operacji.  
  
 Liczniki są widoczne na wiele zakresów, danych zbieranych z wyższej zakresu są agregowane z danymi z niższym zakresów. Na przykład `Calls` w punkcie końcowym reprezentuje sumę wszystkich wywołań operacji w ramach punktu końcowego; `Calls` w punkcie usług jest sumą wszystkich połączeń do wszystkich punktów końcowych w ramach usługi.  
  
> [!NOTE]
>  Jeśli masz nazwy zduplikowanych operacji na kontrakt tylko uzyskać jednego wystąpienia liczników dla obu operacji.  
  
## <a name="programming-the-wcf-performance-counters"></a>Programowanie liczniki wydajności programu WCF  
 Niektóre pliki są instalowane w folderze instalacyjnym zestawu SDK, dzięki czemu programowy dostęp liczniki wydajności programu WCF. Te pliki znajdują się w następujący sposób.  
  
-   _ServiceModelEndpointPerfCounters.vrg  
  
-   _ServiceModelOperationPerfCounters.vrg  
  
-   _ServiceModelServicePerfCounters.vrg  
  
-   _SMSvcHostPerfCounters.vrg  
  
-   _TransactionBridgePerfCounters.vrg  
  
 Aby uzyskać więcej informacji na temat sposobu programowy dostęp liczniki, zobacz [Architektura programowania licznika wydajności](http://go.microsoft.com/fwlink/?LinkId=95179).  
  
## <a name="see-also"></a>Zobacz też  
 [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
