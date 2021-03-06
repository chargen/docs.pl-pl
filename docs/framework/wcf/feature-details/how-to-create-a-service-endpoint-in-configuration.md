---
title: 'Porady: Tworzenie punktu końcowego usługi w konfiguracji'
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: f1a2696e2aeb8d0c704d008b064a8f8c8b0745d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a>Porady: Tworzenie punktu końcowego usługi w konfiguracji
Punkty końcowe udostępniać klientom dostęp do funkcji oferowanych przez usługi Windows Communication Foundation (WCF). Można określić jedną lub więcej punktów końcowych dla usługi przy użyciu kombinacji adresy punktów końcowych względne i bezwzględne lub jeśli żadnych punktów końcowych usługi nie jest zdefiniowana, środowiska uruchomieniowego zawiera niektóre domyślnie dla Ciebie. W tym temacie przedstawiono sposób dodawania punktów końcowych przy użyciu pliku konfiguracji, które zawierają zarówno względnych i bezwzględnych adresów.  
  
## <a name="example"></a>Przykład  
 Następująca konfiguracja usługi Określa adres bazowy i pięć punktów końcowych.  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
    <!-- This section is optional with the default configuration introduced  
         in .NET Framework 4. -->  
      <service  
          name="Microsoft.ServiceModel.Samples.CalculatorService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="/test"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="http://localhost:8001/hello/servicemodelsamples"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
                  binding="netTcpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is another relative address exposed at   
             http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
## <a name="example"></a>Przykład  
 Adres podstawowy jest określona za pomocą `add` elementu w obszarze usługi/hosta/baseAddress, jak pokazano w poniższym przykładzie.  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a>Przykład  
 Pierwszy definicji punktu końcowego pokazano w poniższym przykładzie określa adres względny, co oznacza, że adres punktu końcowego jest kombinacją adresu podstawowego i adres względny zgodnie z regułami kompozycji jednolity identyfikator zasobów (URI). Adres względny jest pusty (""), więc adres punktu końcowego jest taki sam jak adres podstawowy. Adres rzeczywisty punkt końcowy jest http://localhost:8000/servicemodelsamples/service.  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Przykład  
 Druga definicja punkt końcowy określa również adresem względnym, jak pokazano w poniższych Przykładowa konfiguracja. Adres względny "test", jest dołączany do adres podstawowy. Adres rzeczywisty punkt końcowy jest http://localhost:8000/servicemodelsamples/service/test.  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Przykład  
 Trzeci definicji punktu końcowego określa adresu bezwzględnego, jak pokazano w poniższych Przykładowa konfiguracja. Adres podstawowy pełni żadnej roli w adresie. Adres rzeczywisty punkt końcowy jest http://localhost:8001/hello/servicemodelsamples.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Przykład  
 Adres punktu końcowego czwarty Określa adres bezwzględny i innego transportu — TCP. Adres podstawowy pełni żadnej roli w adresie. Adres rzeczywisty punkt końcowy jest NET.TCP://localhost: 9000/servicemodelsamples/usług.  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Przykład  
 Aby użyć domyślnych punktów końcowych dostarczonym w czasie wykonywania, nie określaj żadnych punktów końcowych usługi w kodzie i pliku konfiguracji. W tym przykładzie środowiska uruchomieniowego tworzy domyślne punkty końcowe po otwarciu usługi. Aby uzyskać więcej informacji na temat domyślne punkty końcowe, powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```
