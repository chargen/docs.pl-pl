---
title: Powiązania niestandardowe
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: 6880b04a3f8a82c1e109c32674804c5241913a8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="custom-bindings"></a>Powiązania niestandardowe
Można użyć <xref:System.ServiceModel.Channels.CustomBinding> klasy, jeśli jedno z powiązań dostarczane przez system nie spełnia wymagania dotyczące usługi. Wszystkie powiązania są tworzone na podstawie uporządkowany zestaw elementów wiązania. Powiązania niestandardowe mogą być zbudowane z zestawu elementów powiązania dostarczane przez system, lub mogą zawierać elementy zdefiniowane przez użytkownika niestandardowego powiązania. Elementy wiązania niestandardowego, na przykład umożliwia korzystanie z nowego transportu lub koderów na punkt końcowy usługi. Przykłady pracy można znaleźć [przykłady powiązań niestandardowych](http://msdn.microsoft.com/library/657e8143-beb0-472d-9cfe-ed1a19c2ab08). Aby uzyskać więcej informacji, zobacz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
## <a name="construction-of-a-custom-binding"></a>Konstrukcja wiązania niestandardowego  
 Wiązanie niestandardowe jest tworzony przy użyciu <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> konstruktora z kolekcji elementów, które są "skumulowany" w określonej kolejności wiązania:  
  
-   U góry to opcjonalna <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> klasy, która umożliwia przepływu transakcji.  
  
-   Następnie to opcjonalna <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> klasy, która udostępnia sesję i kolejności mechanizmów zgodnie z definicją w specyfikacji WS-ReliableMessaging. Sesja może krzyżowe pośredników SOAP i transportu.  
  
-   Następnie to opcjonalna <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy, która udostępnia funkcje zabezpieczeń, takich jak autoryzacja, uwierzytelnianie, ochrony i poufności.  
  
-   Następnie to opcjonalna <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> klasy, która pozwala na dwóch sposób dupleksu komunikacji za pomocą protokołu transport, który nie obsługuje komunikację dupleksową natywnie, takich jak HTTP.  
  
-   Następnie to opcjonalna <xref:System.ServiceModel.Channels.OneWayBindingElement>) klasy, która zapewnia komunikację jednokierunkowe.  
  
-   Następnie jest opcjonalny strumienia elementu powiązania zabezpieczeń, które może być jedną z następujących czynności.  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   Obok jest element powiązania kodowania komunikatu wymagane. Można użyć kodera wiadomości lub jeden z trzech powiązania kodowania wiadomości:  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
 W dolnej części jest element wymagany transportu. Można użyć własnych transportu lub jednego z następujące elementy powiązania transportu, który udostępnia usługi Windows Communication Foundation (WCF):  
  
-   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
-   <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
 W poniższej tabeli przedstawiono opcje dla każdej warstwy.  
  
|Warstwy|Opcje|Wymagane|  
|-----------|-------------|--------------|  
|Transakcje|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Nie|  
|Niezawodność|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Nie|  
|Zabezpieczenia|<xref:System.ServiceModel.Channels.SecurityBindingElement>|Nie|  
|Kodowanie|Tekst, niestandardowe binary, komunikat transmisji optymalizacji mechanizmu (MTOM)|Tak|  
|Transportu|TCP, HTTP i HTTPS, nazwane potoki (znanej także jako IPC) między równorzędnych (P2P), Usługa kolejkowania komunikatów (MSMQ), niestandardowe|Tak|  
  
 Ponadto można definiować własne elementy powiązania i wstawione między dowolnymi z poprzednim zdefiniowane warstwy.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd tworzenia punktów końcowych](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Instrukcje: dostosowywanie powiązania udostępnionego przez system](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)  
 [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Powiązanie niestandardowe](../../../../docs/framework/wcf/samples/custom-binding.md)
