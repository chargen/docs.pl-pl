---
title: Ustawianie właściwości Use i Style
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: 74d5baca77fd1af6260def762094b3ce01816179
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="setting-the-use-and-style-properties"></a>Ustawianie właściwości Use i Style
W tym przykładzie przedstawiono sposób użycia właściwości Use i Style na <xref:System.ServiceModel.XmlSerializerFormatAttribute> i <xref:System.ServiceModel.DataContractFormatAttribute>. Te właściwości mają wpływ na sposób sformatowanych komunikatów. Domyślnie treść komunikatu jest sformatowany przy użyciu stylu ustawioną <xref:System.ServiceModel.OperationFormatStyle.Document>. Te ustawienia można określić w poziomie kontrakt usługi lub na poziomie kontrakt operacji.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Właściwości stylu określa, jak metadanych WSDL usługi jest sformatowany. Możliwe wartości to <xref:System.ServiceModel.OperationFormatStyle.Document>, i <xref:System.ServiceModel.OperationFormatStyle.Rpc>. RPC oznacza, że reprezentacja wiadomości wymieniane operacji WSDL zawiera parametry, tak jakby był on zdalne wywołanie procedury. Poniżej przedstawiono przykład.  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="n1" type="xsd:double"/>  
  <wsdl:part name="n2" type="xsd:double"/>  
</wsdl:message>  
```  
  
 Ustawienie stylu <xref:System.ServiceModel.OperationFormatStyle.Document> oznacza, że reprezentacja WSDL zawiera pojedynczy element, który reprezentuje dokumentu, które są wymieniane dla danej operacji, jak pokazano w poniższym przykładzie.  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="parameters" element="tns:Add"/>  
</wsdl:message>  
```  
  
 <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> Właściwość określa format komunikatu. Możliwe wartości to <xref:System.ServiceModel.OperationFormatUse.Literal> i <xref:System.ServiceModel.OperationFormatUse.Encoded>; wartość domyślna to <xref:System.ServiceModel.OperationFormatUse.Literal>. Literał oznacza, że wiadomości jest literału wystąpienie schematu w formacie WSDL, jak pokazano w następującym dokumencie / literału przykład.  
  
```xml  
<Add xmlns="http://Microsoft.ServiceModel.Samples">  
  <n1>100</n1>  
  <n2>15.99</n2>  
</Add>  
```  
  
 Zakodowany oznacza, że schematy w formacie WSDL są specyfikacje abstrakcyjna, które są zakodowane zgodnie z regułami w SOAP 1.1 sekcji 5. Poniżej przedstawiono przykład RPC/Encoded.  
  
```xml  
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">  
  <n1 xsi:type="xsd:double" xmlns="">100</n1>  
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>  
</q1:Add>  
```  
  
 WS-I podstawowe 1.0 profilu zabrania stosowania <xref:System.ServiceModel.OperationFormatUse.Encoded> i należy używać tylko gdy wymagane przez starszej wersji usługi. `Encoded` Format komunikatu jest dostępna tylko, gdy użycie XmlSerializer.  
  
 Aby umożliwić wyświetlanie wiadomości wysyłanych i odbieranych, w tym przykładzie jest oparta na [śledzenie i rejestrowanie komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md). Konfiguracji usługi i kod źródłowy został zmodyfikowany w celu włączenia i wykorzystania śledzenie i rejestrowanie komunikatów. Ponadto <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> został skonfigurowany bez zabezpieczeń, dlatego zarejestrowane komunikaty, które można wyświetlić w niezaszyfrowanej postaci. Wynikowy dzienniki śledzenia (System.ServiceModel.e2e i Message.log) powinien wyświetlać przy użyciu [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Dane śledzenia są skonfigurowane do utworzenia w folderze C:\LOGS. Przed uruchomieniem próbki, należy utworzyć folder. Zaznacz, aby wyświetlić zawartość wiadomości w narzędziu Podgląd śledzenia **wiadomości** zarówno lewego i prawego okienka narzędzia.  
  
 Poniższy kod przedstawia kontraktu usługi o <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> ustawioną właściwość <xref:System.ServiceModel.OperationFormatUse> i zmienić formatu treści wiadomości z domyślnego <xref:System.ServiceModel.OperationFormatStyle> do <xref:System.ServiceModel.OperationFormatStyle.Document>.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
XmlSerializerFormat(Style = OperationFormatStyle.Rpc,   
                                 Use = OperationFormatUse.Encoded)]  
public interface IUseAndStyleCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 Różnice między różnymi <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> i <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> ustawienia, zmodyfikuj je w usłudze, ponownie wygenerować klienta uruchomić przykładowy i zapoznaj się z plikiem c:\logs\message.logs za pomocą narzędzia podglądu śledzenia usługi. Również obserwować wpływ na metadane, wyświetlając http://localhost/ServiceModelSamples/service.svc?wsdl. Metadane dla usługi jest zwykle podzielony na wiele stron. Na stronie głównej wsdl zawiera powiązania WSDL, ale wyświetlać http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0 obserwować definicje wiadomości.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Utwórz katalog C:\LOGS rejestrowanie komunikatów. Przyznać użytkownikowi uprawnienia do tego katalogu zapisu usługi sieciowej.  
  
3.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`  
  
## <a name="see-also"></a>Zobacz też
