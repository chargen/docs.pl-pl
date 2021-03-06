---
title: Usługa AJAX z formatami JSON i XML — przykład
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: 32964c287b0064daf529aa4c1e28f0927d29a6d5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ajax-service-with-json-and-xml-sample"></a>Usługa AJAX z formatami JSON i XML — przykład
W tym przykładzie pokazano, jak używać usługi Windows Communication Foundation (WCF) do tworzenia usługi asynchronicznego JavaScript i XML (AJAX), która zwraca dane JavaScript Object Notation (JSON) lub XML. Usługa AJAX mogą korzystać za pomocą kodu JavaScript w kliencie przeglądarki sieci Web. Ten przykład jest oparty na [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki.  
  
 W przeciwieństwie do innych próbek AJAX, w tym przykładzie nie korzysta z kodu ASP.NET AJAX i <xref:System.Web.UI.ScriptManager> formantu. Dzięki dodatkowej konfiguracji usług WCF AJAX można uzyskać z dowolnej strony HTML przy użyciu języka JavaScript i pokazane w tym scenariuszu. Na przykład przy użyciu programu WCF z ASP.NET AJAX, zobacz [przykłady AJAX](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
 W tym przykładzie pokazano, jak typ odpowiedzi operacji między formatami JSON i XML przełącznika. Ta funkcja jest dostępna, niezależnie od tego, czy usługa jest skonfigurowana można uzyskać dostępu do środowiska ASP.NET AJAX lub stronę klienta HTML/JavaScript.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Aby umożliwić korzystanie z klientów z systemem innym niż ASP.NET AJAX, użyj <xref:System.ServiceModel.Activation.WebServiceHostFactory> (nie <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) w pliku svc. <xref:System.ServiceModel.Activation.WebServiceHostFactory> dodaje <xref:System.ServiceModel.Description.WebHttpEndpoint> standardowy punkt końcowy do usługi. Punkt końcowy jest skonfigurowana na pusty adres względem pliku svc; oznacza to, że adres usługi http://localhost/ServiceModelSamples/service.svc, z nie dodatkowe sufiksy na inną niż nazwa operacji.  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
```  
  
 Następujących sekcji w pliku Web.config mogą służyć do wprowadzenia dodatkowych zmian konfiguracyjnych do punktu końcowego. Można usunąć, jeśli są potrzebne żadne dodatkowe zmiany.  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name="" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Format danych domyślnych <xref:System.ServiceModel.Description.WebHttpEndpoint> jest podczas domyślny format danych XML, <xref:System.ServiceModel.Description.WebScriptEndpoint> jest JSON. Aby uzyskać więcej informacji, zobacz [tworzenie usług AJAX WCF bez platformy ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).  
  
 Usługi w poniższym przykładzie jest standardowe usługi WCF za pomocą dwóch operacji. Zarówno operacje wymagają <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> treści w stylu <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybuty, które dotyczą `webHttp` zachowania i nie ma żadnego wpływu na przełączniku format danych JSON/XML.  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```

 Format odpowiedzi dla operacji jest określony jako XML, co jest ustawieniem domyślnym dla [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) zachowanie. Jednak dobrze jest jawnie określić format odpowiedzi.  
  
 Używa innej operacji `WebInvokeAttribute` atrybutu i jawnie określa JSON zamiast XML dla odpowiedzi.  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```

 Należy pamiętać, że w obu przypadkach operacje zwracać typu złożonego `MathResult`, która jest standardowa typu kontraktu danych WCF.  
  
 Klient XmlAjaxClientPage.htm strony sieci Web zawiera kod JavaScript, który wywołuje jednego z poprzednich dwóch operacji, gdy użytkownik kliknie **obliczanie (zwracany JSON)** lub **obliczanie (zwracany XML)**  przyciski na stronie. Kod, aby wywołać usługę konstruuje treść kodu JSON i wysyła je przy użyciu metody POST protokołu HTTP. Żądanie jest tworzony ręcznie w języku JavaScript, w odróżnieniu od [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki i przykłady, za pomocą kodu ASP.NET AJAX.  

```csharp
// Create HTTP request  
var xmlHttp;  
// Request instantiation code omitted…  
// Result handler code omitted…  
  
// Build the operation URL  
var url = "service.svc/ajaxEndpoint/";  
url = url + operation;  
  
// Build the body of the JSON message  
var body = '{"n1":';  
body = body + document.getElementById("num1").value + ',"n2":';  
body = body + document.getElementById("num2").value + '}';  
  
// Send the HTTP request  
xmlHttp.open("POST", url, true);  
xmlHttp.setRequestHeader("Content-type", "application/json");  
xmlHttp.send(body);  
```

 Gdy usługa odpowiada, odpowiedź zostanie wyświetlona bez dalszego przetwarzania w polu tekstowym na stronie. To jest zaimplementowany dla celów demonstracyjnych, co pozwala na bezpośrednio Sprawdź formaty danych XML i JSON, używane.  

```javascript
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```

> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Skompiluj rozwiązanie XmlAjaxService.sln zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Przejdź do http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm (nie należy otwierać XmlAjaxClientPage.htm w przeglądarce z katalogu projektu).  
  
## <a name="see-also"></a>Zobacz też  
 [Usługa AJAX używająca żądań POST protokołu HTTP](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
