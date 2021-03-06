---
title: Projektowanie i implementowanie usług
ms.date: 03/30/2017
helpviewer_keywords:
- defining service contracts [WCF]
ms.assetid: 036fae20-7c55-4002-b71d-ac4466e167a3
ms.openlocfilehash: d4d4fb3600a25f05865dd56c220e7a8ade246f08
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="designing-and-implementing-services"></a>Projektowanie i implementowanie usług
W tej sekcji przedstawiono sposób definiowania i implementowanie kontraktów usług WCF. Kontrakt usługi określa punkt końcowy komunikuje się publicznie. Na poziomie bardziej konkretną jest oświadczenie o zestaw określonych komunikatów podzielone na wzorce wymiany wiadomości podstawowe (MEPs), takich jak żądanie/odpowiedź, jednokierunkowe i dupleksowych. Jeśli kontrakt usługi to zestaw logicznie powiązanych wymiany komunikatów, operacji usługi jest exchange pojedynczym komunikacie. Na przykład `Hello` operacji oczywiście zaakceptować jeden komunikat (aby wywołujący może poinformować o powitanie) i może lub nie może zwracać komunikat (w zależności od uprzejmości operacji).  
  
 Aby uzyskać więcej informacji na temat kontraktów i inne podstawowe pojęcia Windows Communication Foundation (WCF), zobacz [podstawowe pojęcia programu Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md). Ten temat koncentruje się na kontraktów usług. Aby uzyskać więcej informacji o sposobie budowania klientów, którzy używają kontraktów usług do nawiązania połączenia usługi, zobacz [Przegląd klienta programu WCF](../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Omówienie  
 Ten temat zawiera wysokiego poziomu orientacji koncepcyjnej na projektowanie i Implementowanie usług WCF. Tematy podrzędne zawierają bardziej szczegółowe informacje o szczegółowe informacje na temat projektowania i implementacji. Przed projektowanie i wdrażanie aplikacji WCF, zalecane jest ten użytkownik:  
  
-   Zrozumienie kontraktu usługi, jak to działa i jak go utworzyć.  
  
-   Zrozumienie, że kontrakty stanu minimalnych wymagań tej konfiguracji środowiska uruchomieniowego lub środowisko macierzyste mogą nie obsługiwać.  
  
## <a name="service-contracts"></a>Kontrakty usług  
 Kontrakt usługi określa:  
  
-   Opisuje kontrakt operacji.  
  
-   Podpis operacje kategoriach wiadomości wymieniane.  
  
-   Typy danych tych wiadomości.  
  
-   Lokalizacja operacje.  
  
-   Określonych protokołów i formatów serializacji, które są używane do obsługi łączność z usługą.  
  
 Na przykład może być kontrakt zamówienia zakupu `CreateOrder` operacja, która akceptuje dane wejściowe informacji o zamówieniu typów i zwraca informacje o powodzeniu lub niepowodzeniu, tym identyfikator zamówienia. Może także mieć `GetOrderStatus` operacji, które akceptuje identyfikator kolejności i zwraca informacje o stanie zamówienia. Określ tego rodzaju kontraktu usługi:  
  
1.  Czy kontrakt zamówienia zakupu obejmował `CreateOrder` i `GetOrderStatus` operacji.  
  
2.  Określono operacje wejścia wiadomości i wyjścia wiadomości.  
  
3.  Dane, które umożliwiają wykonanie tych wiadomości.  
  
4.  Podzielone na kategorie instrukcje dotyczące infrastruktury komunikacji niezbędne do pomyślnie przetwarzania komunikatów. Informacje te zawierają na przykład czy i jakie rodzaje zabezpieczeń są wymagane do nawiązania komunikacji powiodło się.  
  
 Do przekazywania informacji do innych aplikacji na wiele platform (takie jak platformy firmy Microsoft) tego rodzaju, kontraktów usług XML publicznie wyrażone są w standardowych formatów XML, takich jak [Web Services Description Language](http://go.microsoft.com/fwlink/?LinkId=94952) () WSDL) i [schematu XML](http://go.microsoft.com/fwlink/?LinkId=94953) (XSD), między innymi. Deweloperzy dla wielu platform mogą używać tych informacji publicznego kontraktu do tworzenia aplikacji, które mogą komunikować się z usługą, zarówno ponieważ zrozumieniu języka specyfikacji i pozwalają włączyć współdziałanie języków przez opisujące publicznego formularzy, formaty i protokołów obsługiwanych przez usługę. Aby uzyskać więcej informacji na temat obsługi WCF tego rodzaju informacje, zobacz [metadanych](../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Kontrakty można wyrazić na wiele sposobów i podczas WSDL i XSD to doskonałe języki do opisywania usług w łatwy sposób, języki trudne do użycia bezpośrednio i są jedynie opisy usługi, nie implementacji kontraktu usługi. W związku z tym WCF aplikacje używają klasy, interfejsy i atrybuty zarządzanych do definiowania struktury usługi i go zaimplementować.  
  
 Wynikowa kontrakt zdefiniowany w zarządzanym typów może być *wyeksportowane* jak metadanych — WSDL oraz XSD — w razie potrzeby przez klientów lub innych implementacji usługi. Wynik jest model programowania prostego opisane (przy użyciu metadanych publicznych) dla wszystkich aplikacji klienckich. Szczegóły podstawowej wiadomości SOAP transportu i informacji związanych z zabezpieczeniami i tak dalej, możesz je zostawić do usługi WCF, która automatycznie wykonuje niezbędne konwersje do i z systemu typ kontraktu usługi w systemie typu XML.  
  
 Aby uzyskać więcej informacji na temat opracowywania umów, zobacz [projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md). Aby uzyskać więcej informacji na temat Implementowanie kontraktów, zobacz [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
### <a name="messages-up-front-and-center"></a>Komunikaty w górę Centrum  
 Przy użyciu zarządzane interfejsy, klasy i metody do operacji usługi modelu jest proste, gdy są używane do zdalnego wywołania procedury (RPC) — styl podpisy metod, w których przekazywanie parametrów do metody i odbieranie wartości zwracane jest normalne formę żądania funkcji z obiektem lub innego typu kodu. Na przykład Programiści używający zarządzanych języków, takich jak Visual Basic i C++ COM można zastosować wiedzy podejścia stylu wywołania RPC (czy przy użyciu interfejsów lub obiektów) do utworzenia kontraktów usług WCF bez występują problemy związane z Obiekt systemów rozproszonych się w stylu wywołania RPC. Orientacji usługi zapewnia korzyści luźno powiązanych, zorientowany programowania przy zachowaniu łatwość i znajomości RPC, środowisko programowania.  
  
 Wielu programistów jest wygodniejsze z interfejsów, takich jak kolejki komunikatów, takie jak Microsoft MSMQ programowania aplikacji zorientowany <xref:System.Messaging> przestrzeni nazw w .NET Framework lub wysyłania XML bez struktury w żądaniach HTTP kilka. Aby uzyskać więcej informacji na temat programowania na poziomie komunikatu, zobacz [za pomocą kontraktów komunikatu](../../../docs/framework/wcf/feature-details/using-message-contracts.md), [programowania na poziomie kanału usługi](../../../docs/framework/wcf/extending/service-channel-level-programming.md), i [współdziałanie z aplikacjami POX](../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Opis hierarchii wymagania  
 Kontrakt usługi grup działań; Określa wymiany komunikatów, typów wiadomości i danych typów przenoszące tych wiadomości; wskazuje kategorie implementacja musi mieć do obsługi kontrakt zachowania w czasie wykonywania (na przykład może wymagać zaszyfrowana i podpisana wiadomości). Kontrakt usługi nie został określony dokładnie jak te warunki zostały spełnione, tylko że muszą być. Typ szyfrowania lub sposób, w którym jest podpisany komunikatu zależy od implementacji i konfiguracji usługi zgodne.  
  
 Zwróć uwagę, czy kontrakt wymaga pewne zagadnienia implementacji kontraktu usługi i konfigurację środowiska wykonawczego, aby dodać zachowanie sposób. Zestaw wymagań, które muszą zostać spełnione do udostępnienia usługi do użycia opiera się na poprzedni zestaw wymagań. Jeśli kontrakt sprawia, że wymagania dotyczące wdrażania, implementacja może wymagać jeszcze więcej konfiguracji i powiązania, które Włącz usługę w celu uruchomienia. Ponadto aplikacja hosta muszą również obsługiwać wszelkie wymagania, które Dodaj konfigurację usługi i powiązania.  
  
 Ten proces dodawania wymaganie ważne jest, aby mieć na uwadze podczas projektowania, wdrażania, konfigurowanie i hosting aplikacji usługi Windows Communication Foundation (WCF). Na przykład kontrakt można określić, że musi obsługiwać sesji. Jeśli tak, musisz skonfigurować powiązania w celu spełnienia tego wymagania umownymi lub implementacji usługi nie będą działać. Lub jeśli usługa wymaga zintegrowanego uwierzytelniania systemu Windows i znajduje się w Internet Information Services (IIS), aplikacji sieci Web, w którym znajduje się usługa musi mieć włączone zintegrowane uwierzytelnianie systemu Windows i obsługa anonimowe wyłączone. Aby uzyskać więcej informacji o funkcjach i wpływ typów aplikacji hosta innej usługi, zobacz [Hosting usług](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md)  
 [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md)
