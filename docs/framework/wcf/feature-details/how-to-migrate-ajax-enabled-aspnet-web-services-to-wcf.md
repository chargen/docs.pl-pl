---
title: 'Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF'
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 048408adf8678c243a225a233cb1173c9b7f869f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a>Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF
W tym temacie przedstawiono procedury migracji podstawowej usługi ASP.NET AJAX równoważne usługi z obsługą technologii AJAX Windows Communication Foundation (WCF). Widoczny jest sposób utworzyć taką samą wersję usługi ASP.NET AJAX WCF. Te dwie usługi mogą być następnie używane obok siebie lub usługi WCF może być używany do zastąpienia usługi ASP.NET AJAX.  
  
 Migrowanie istniejących ASP.NET AJAX usługi z usługą WCF AJAX zapewnia następujące korzyści:  
  
-   Usługa AJAX mogą uwidaczniać jako usługa SOAP z minimalną konfiguracją dodatkowe.  
  
-   Korzystanie z funkcji WCF, takie jak śledzenie i tak dalej.  
  
 W poniższych procedurach założono, że używasz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
 Kod, który jest wynikiem procedury opisane w tym temacie podano w przykładzie zamieszczonym procedur.  
  
 Aby uzyskać więcej informacji na temat udostępnianie usług WCF za pomocą punktu końcowego z włączoną obsługą technologii AJAX, zobacz [porady: Użyj konfiguracji można dodać punktu końcowego AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) tematu.  
  
### <a name="to-create-and-test-the-aspnet-web-service-application"></a>Tworzenie i testowanie aplikacji usługi sieci Web ASP.NET  
  
1.  Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Z **pliku** menu, wybierz opcję **nowy**, następnie **projektu**, następnie **sieci Web**, a następnie wybierz **aplikacji usługi sieci Web ASP.NET** .  
  
3.  Nazwij projekt `ASPHello` i kliknij przycisk **OK**.  
  
4.  Usuń znaczniki komentarza wiersza w pliku Service1.asmx.cs, który zawiera `System.Web.Script.Services.ScriptService]` umożliwiające AJAX dla tej usługi.  
  
5.  Z **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.  
  
6.  Z **debugowania** menu, wybierz opcję **uruchomić bez debugowania**.  
  
7.  Na stronie sieci Web wygenerowane, wybierz `HelloWorld` operacji.  
  
8.  Kliknij przycisk **Invoke** znajdującego się na `HelloWorld` strony testowej. Powinien zostać wyświetlony następujący odpowiedzi XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <string xmlns="http://tempuri.org/">Hello World</string>  
    ```  
  
9. Ta odpowiedź potwierdza, że teraz działa usługa ASP.NET AJAX i, w szczególności, że usługa ma teraz widoczne punkt końcowy pod Service1.asmx/HelloWorld, który odpowiada na HTTP POST żądania i zwraca XML.  
  
     Teraz można przystąpić do przekonwertowania tej usługi do korzystania z usługi WCF w technologii AJAX.  
  
### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a>Aby utworzyć aplikację usługi równoważne WCF AJAX  
  
1.  Kliknij prawym przyciskiem myszy **ASPHello** projekt i wybierz **Dodaj**, następnie **nowy element**, a następnie **usługi WCF z włączoną obsługą technologii AJAX**.  
  
2.  Nazwa usługi `WCFHello` i kliknij przycisk **Dodaj**.  
  
3.  Otwórz plik WCFHello.svc.cs.  
  
4.  Service1.asmx.cs, skopiuj następujące wykonania `HelloWorld` operacji.  
  
    ```  
    public string HelloWorld()  
    {  
         return "Hello World";  
    }  
    ```  
  
5.  Wklej skopiowane wdrażanie `HelloWorld` operacji do pliku WCFHello.svc.cs zamiast poniższy kod.  
  
    ```  
    public void DoWork()  
    {  
          // Add your operation implementation here  
          return;  
    }  
    ```  
  
6.  Określ `Namespace` atrybutu dla <xref:System.ServiceModel.ServiceContractAttribute> jako `WCFHello`.  
  
    ```  
    [ServiceContract(Namespace="WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]  
    public class WCFHello  
    { … }  
    ```  
  
7.  Dodaj <xref:System.ServiceModel.Web.WebInvokeAttribute> do `HelloWorld` operacji i zestawu <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> właściwości do zwrócenia <xref:System.ServiceModel.Web.WebMessageFormat.Xml>. Należy pamiętać, że, jeśli nie jest ustawiony, domyślny typ zwracany jest <xref:System.ServiceModel.Web.WebMessageFormat.Json>.  
  
    ```  
    [OperationContract]  
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
    public string HelloWorld()  
    {  
        return "Hello World";  
    }  
    ```  
  
8.  Z **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.  
  
9. Otwórz plik WCFHello.svc i z **debugowania** menu, wybierz opcję **uruchomić bez debugowania**.  
  
10. Usługa udostępnia teraz punkt końcowy pod `WCFHello.svc/HelloWorld`, która odpowiada na żądania HTTP POST. Nie można przetestować żądania HTTP POST z przeglądarki, ale punkt końcowy zwraca XML po XML.  
  
    ```xml  
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>  
    ```  
  
11. `WCFHello.svc/HelloWorld` i `Service1.aspx/HelloWorld` punkty końcowe są teraz taką samą funkcję.  
  
## <a name="example"></a>Przykład  
 Kod, który jest wynikiem procedury opisane w tym temacie podano w poniższym przykładzie.  
  
```  
//This is the ASP.NET code in the Service1.asmx.cs file.  
  
using System;  
using System.Collections;  
using System.ComponentModel;  
using System.Data;  
using System.Linq;  
using System.Web;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using System.Xml.Linq;  
using System.Web.Script.Services;  
  
namespace ASPHello  
{  
    /// <summary>  
    /// Summary description for Service1.  
    /// </summary>  
    [WebService(Namespace = "http://tempuri.org/")]  
    [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]  
    [ToolboxItem(false)]  
    // To allow this Web Service to be called from script, using ASP.NET AJAX, uncomment the following line.   
    [System.Web.Script.Services.ScriptService]  
    public class Service1 : System.Web.Services.WebService  
    {  
  
        [WebMethod]  
        public string HelloWorld()  
        {  
            return "Hello World";  
        }  
    }  
}   
  
//This is the WCF code in the WCFHello.svc.cs file.  
using System;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Activation;  
using System.ServiceModel.Web;  
  
namespace ASPHello  
{  
    [ServiceContract(Namespace = "WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
    public class WCFHello  
    {  
        // Add [WebInvoke] attribute to use HTTP GET.  
        [OperationContract]  
        [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
        public string HelloWorld()  
        {  
            return "Hello World";  
        }  
  
        // Add more operations here and mark them with [OperationContract].  
    }  
}  
```  
  
 <xref:System.Xml.XmlDocument> Typ nie jest obsługiwany przez <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> , ponieważ nie jest możliwy do serializacji przez <xref:System.Xml.Serialization.XmlSerializer>. Możesz użyć dowolnej <xref:System.Xml.Linq.XDocument> wpisz lub serializować <xref:System.Xml.XmlDocument.DocumentElement%2A> zamiast tego.  
  
 Jeśli usługi sieci Web ASMX uaktualniania i migracji side-by-side do usługi WCF, należy unikać mapowania dwa typy do tej samej nazwie na kliencie. Powoduje to, że wystąpił wyjątek w serializatorów w przypadku używania tego samego typu w <xref:System.Web.Services.WebMethodAttribute> i <xref:System.ServiceModel.ServiceContractAttribute>:  
  
-   Jeśli usługa WCF zostanie dodany jako pierwszy, wywołanie metody usługi sieci Web ASMX powoduje, że wyjątek w <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> ponieważ definicji stylu WCF w kolejności serwer proxy ma pierwszeństwo.  
  
-   Jeśli usługa sieci Web ASMX zostanie dodany jako pierwszy, wywoływanie metody dla usługi WCF powoduje, że wyjątek w <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ponieważ definicji stylu kolejności na serwerze proxy usługi sieci Web ma pierwszeństwo.  
  
 Są istotne różnice w zachowaniu między <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> i ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>. Na przykład <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> reprezentuje słownik jako tablica par klucz/wartość, podczas gdy ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> reprezentuje słownik jako rzeczywisty obiektów JSON. Dlatego poniżej znajduje się słownik reprezentowane w technologii ASP.NET AJAX.  
  
```  
Dictionary<string, int> d = new Dictionary<string, int>();  
d.Add("one", 1);  
d.Add("two", 2);  
```  
  
 Ten słownik jest reprezentowana w obiektów JSON, jak pokazano na poniższej liście:  
  
-   [{"Klucza": "Jeden", "Value": 1}, {"Klucza": "Dwa", "Value": 2}] według <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>  
  
-   {"jeden": 1, "dwa": 2} przez ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>  
  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Jest bardziej zaawansowanych, w tym sensie, że może obsługiwać słowniki gdzie typ klucza nie jest ciągiem, gdy <xref:System.Web.Script.Serialization.JavaScriptSerializer> nie. Ale nie jest bardziej przyjazny JSON.  
  
 Istotne różnice między tymi serializatorów podsumowano w poniższej tabeli.  
  
|Kategoria różnic|Klasa DataContractJsonSerializer|ASP.NET AJAX JavaScriptSerializer|  
|-----------------------------|--------------------------------|---------------------------------------|  
|Podczas deserializacji pustego buforu (nowe byte[0]) do <xref:System.Object> (lub <xref:System.Uri>, lub niektóre inne klasy).|SerializationException|null|  
|Serializacja <xref:System.DBNull.Value>|{} (lub {"__type": "#System"})|Null|  
|Serializacja prywatne elementy członkowskie typów [Serializable].|serializowany|nie serializacji|  
|Serializacja właściwości publicznej <xref:System.Runtime.Serialization.ISerializable> typów.|nie serializacji|serializowany|  
|"Rozszerzenia" JSON|Jest zgodna ze specyfikacją JSON, co wymaga cudzysłowów wokół nazwy elementów członkowskich obiektu ({"": "tekst hello"}).|Obsługuje nazwy elementów członkowskich obiektu bez cudzysłowów ({a: "tekst hello"}).|  
|<xref:System.DateTime> Uniwersalny czas koordynowany (UTC)|Nie obsługuje formatu "\\/Date(123456789U)\\/" lub "\\/data\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\\\/)".|Obsługuje format "\\/Date(123456789U)\\/" i "\\/data\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\ \\/) "jako wartości daty/godziny.|  
|Reprezentacja słowników|Tablica KeyValuePair\<K, V >, obsługuje typów kluczy, które nie są ciągami.|Jako rzeczywisty obiektów JSON -, ale tylko typów kluczy dojść, które są ciągami.|  
|Znaki zmienionym|Zawsze z ucieczki ukośnika (/); nigdy nie umożliwia niezmieniony nieprawidłowe znaki JSON, takie jak "\n".|Z ucieczki ukośnika (/) dla wartości daty/godziny.|  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
