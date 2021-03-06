---
title: Usługi hostingowe
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
ms.openlocfilehash: d4fb974cdfec87606f13b5cbd83be2c86f2a1ae5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="hosting-services"></a>Usługi hostingowe
Staje się aktywny, usługa musi być hostowany w środowisku czasu wykonywania, która tworzy go i kontroluje jego kontekstu i okresem istnienia. Usługi Windows Communication Foundation (WCF) zostały zaprojektowane do uruchamiania w dowolnym procesie systemu Windows obsługuje kodu zarządzanego.  
  
 WCF oferuje ujednolicony model programowania do tworzenia aplikacji korzystających z usług. Ten model programowania pozostaje spójna i jest niezależna od środowisko wykonawcze wdrażania usługi. W praktyce oznacza to, że kod dla usług wygląda tego samego niezależnie od opcji hostingu.  
  
 Te hosting różnorodne opcje uruchomionych w aplikacji konsoli do środowiska serwera, takie jak Windows usługa uruchomiona w ramach procesu roboczego zarządzane przez Internet Information Services (IIS) lub przez usługę aktywacji procesów systemu Windows (WAS). Deweloperzy wybierz środowiska macierzystego, który spełnia wymagania dotyczące wdrażania usługi. Te wymagania mogą pochodzić z platformy, na którym aplikacja jest wdrażana, transport, na którym muszą wysyłać i odbierać wiadomości, lub typ odtwarzanie procesów i inne wymagane w celu zapewnienia dostępności odpowiednich zarządzania procesu lub w przypadku niektórych inne wymagania zarządzania lub niezawodności. Następna sekcja zawiera informacje i wskazówki dotyczące obsługi opcje.  
  
## <a name="hosting-options"></a>Opcje hostingu  
  
#### <a name="self-hosting-in-a-managed-application"></a>Hostingu samodzielnego w zarządzanej aplikacji  
 Usługi WCF, mogą być hostowane w dowolnej aplikacji zarządzanych. Jest to najbardziej elastycznym opcja, ponieważ wymaga co najmniej infrastruktury do wdrożenia. Osadzanie kodu dla usługi w kodzie aplikacji zarządzanych a następnie utwórz i otwórz wystąpienie <xref:System.ServiceModel.ServiceHost> udostępnić usługę. Aby uzyskać więcej informacji, zobacz [porady: hostowanie usługi WCF w zarządzanej aplikacji](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Ta opcja umożliwia dwóch typowych scenariuszy: uruchomionych w aplikacji konsoli i aplikacje wzbogaconego klienta, takich jak usługi WCF na podstawie Windows Presentation Foundation (WPF) lub program Windows Forms (WinForms). Hosting w aplikacji konsoli usługi WCF jest zazwyczaj przydatne w fazie programowanie aplikacji. Z tego powodu łatwy do debugowania, łatwo uzyskać informacje o śledzeniu na, aby dowiedzieć się, co dzieje się wewnątrz aplikacji i łatwo przenosić, kopiując je do nowej lokalizacji. Ta opcja hostingu ułatwia także dla zaawansowanych aplikacji klienckich, takich jak [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] i WinForms aplikacji, aby komunikować się na zewnątrz. Na przykład klient współpracy peer-to-peer, który używa [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] interfejs użytkownika, a także obsługuje usługi WCF, która umożliwia innym klientom nawiązania połączenia i udostępnianie informacji.  
  
#### <a name="managed-windows-services"></a>Usługi zarządzanej systemu Windows  
 Ta opcja hostingu składa się z rejestrowania domeny aplikacji (AppDomain), która obsługuje usługę WCF jako zarządzanych usług systemu Windows (wcześniej znane jako usługa NT) tak, że okres istnienia procesu usługi jest kontrolowany przez Menedżera sterowania usługami (SCM) Usługi systemu Windows. Podobnie jak opcji własnym hostingu środowiska macierzystego tego typu wymaga, że niektóre hostingu kod jest zapisywany jako części aplikacji. Usługa jest wdrażana jako usługą systemu Windows oraz jako usługa WCF przez powodowania dziedziczyć <xref:System.ServiceProcess.ServiceBase> klasy, a także z WCF usługi interfejsu kontraktu. <xref:System.ServiceModel.ServiceHost> Jest następnie utworzony i otwarty w przesłoniętych <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> — metoda i zamknięte w zastąpiona <xref:System.ServiceProcess.ServiceBase.OnStop> metody. Instalator klasy, która dziedziczy <xref:System.Configuration.Install.Installer> również musi być implementowana zezwolić programowi zainstalowania przez narzędzie Installutil.exe jako usługa systemu Windows. Aby uzyskać więcej informacji, zobacz [porady: hostowanie usługi WCF w usłudze Windows zarządzany](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md). Scenariusz, korzystając z opcji obsługi zarządzanej usługi systemu Windows jest to, że długotrwałe usługi WCF hostowanej poza usług IIS w zabezpieczonym środowisku, który nie został aktywowany do wiadomości. Okres istnienia usługi steruje zamiast tego systemu operacyjnego. Ta opcja obsługi jest dostępna we wszystkich wersjach systemu Windows.  
  
#### <a name="internet-information-services-iis"></a>Internet Information Services (IIS)  
 Opcji obsługi usług IIS jest zintegrowany z [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] i korzysta z funkcji oferują tych technologii, takich jak proces zamykania odtwarzania, bezczynności, monitorowanie kondycji procesu i aktywacji opartej na komunikat. Na [!INCLUDE[wxp](../../../includes/wxp-md.md)] i [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] systemów operacyjnych, jest to preferowane rozwiązanie do hostowania aplikacji usługi sieci Web, które muszą być wysokiej dostępności i wysoce skalowalna. Usługi IIS oferują także zintegrowane możliwości zarządzania, którzy klienci z klasy korporacyjnej serwera produktu. Ta opcja hostingu wymaga usług IIS zostać prawidłowo skonfigurowane, ale nie wymaga się, że każdy kod hostingu można zapisywać w ramach aplikacji. Aby uzyskać więcej informacji o sposobie konfigurowania programu IIS hosting dla usługi WCF, zobacz [porady: hostowanie usługi WCF w programie IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
 Należy pamiętać, że usług hostowanych przez usługi IIS można używać tylko protokołu HTTP. Jego wykonania w wersji 5.1 usług IIS wprowadziła kilka ograniczeń [!INCLUDE[wxp](../../../includes/wxp-md.md)]. Aktywacji opartej na komunikat, podany dla usługi WCF w programie IIS 5.1 na [!INCLUDE[wxp](../../../includes/wxp-md.md)] blokuje innych siebie usługi WCF na tym samym komputerze z do komunikowania się przy użyciu portu 80. Usługi WCF mogą być uruchamiane w tym samym procesie puli/proces roboczy elementu AppDomain/aplikacji, co inne aplikacje, gdy obsługiwanych przez [!INCLUDE[iis601](../../../includes/iis601-md.md)] na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Jednak ponieważ WCF i [!INCLUDE[iis601](../../../includes/iis601-md.md)] oba rozwiązania używają trybu jądra stosu protokołu HTTP (HTTP.sys), [!INCLUDE[iis601](../../../includes/iis601-md.md)] można udostępniać port 80 innych własnym hostowanej usługi WCF uruchomiona na tym samym komputerze, w przeciwieństwie do usługi IIS 5.1.  
  
#### <a name="windows-process-activation-service-was"></a>Usługa aktywacji procesów systemu Windows (WAS)  
 Usługa aktywacji procesów systemu Windows (WAS) jest nowy proces aktywacji mechanizm [!INCLUDE[lserver](../../../includes/lserver-md.md)] jest również dostępna w [!INCLUDE[wv](../../../includes/wv-md.md)]. Zachowuje znanych [!INCLUDE[iis601](../../../includes/iis601-md.md)] modelu procesów (pul aplikacji i aktywacji opartej na komunikatach procesów) oraz obsługi funkcji (na przykład natychmiastową ochronę przed błędami, monitorowanie kondycji oraz odzyskiwanie), ale usuwa zależność od protokołu HTTP z aktywacji Architektura. [!INCLUDE[iisver](../../../includes/iisver-md.md)] używa WAS wykonywania aktywacji opartej na komunikatach za pośrednictwem protokołu HTTP. Dodatkowe składniki programu WCF także podłączyć do WAS zapewnienie aktywacji opartej na komunikatach za pośrednictwem protokołów, które obsługuje WCF, takie jak TCP, MSMQ i nazwanych potoków. Dzięki temu aplikacje, które umożliwia korzystanie z funkcji usług IIS jak odtwarzanie procesów, szybkie protokołów komunikacyjnych niepowodzenie ochrony i wspólny system konfiguracji, które tylko były dostępne dla aplikacji oparte na protokole HTTP.  
  
 Ta opcja hostingu wymaga, który został skonfigurowany w sposób prawidłowo, ale nie jest wymagane do pisania kodu macierzystego jako części aplikacji. Więcej informacji na temat sposobu konfigurowania został hostingu można znaleźć [porady: hostowanie usługi WCF w WAS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="choosing-a-hosting-environment"></a>Wybieranie środowiska macierzystego  
 W poniższej tabeli przedstawiono niektóre kluczowe korzyści i scenariusze skojarzone z każdą z opcji hostingu.  
  
|Środowisko macierzyste|Typowe scenariusze|Najważniejsze korzyści i ograniczenia|  
|-------------------------|----------------------|----------------------------------|  
|Zarządzanej aplikacji ("hosta samodzielnego")|— Używany podczas tworzenia aplikacji konsoli.<br />-Sformatowanego formularza systemu Windows i [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] dostęp do usług aplikacji klienta.|-Elastyczne.<br />-Łatwa do wdrożenia.<br />-Nie rozwiązania enterprise dla usługi.|  
|Usługi systemu Windows (wcześniej znane jako usługi NT)|-Długotrwałe usługi WCF hostowanej poza usług IIS.|-Usługi okres istnienia procesu kontrolowane przez system operacyjny nie Aktywacja komunikatów.<br />-Obsługiwane przez wszystkie wersje systemu Windows.<br />-Bezpiecznym środowisku.|  
|USŁUGI IIS 5.1 [!INCLUDE[iis601](../../../includes/iis601-md.md)]|-Systemem WCF usługi side-by-side z [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] zawartości w Internecie przy użyciu protokołu HTTP.|-Odtwarzania procesu.<br />— Shutdown bezczynności.<br />-Monitorowania kondycji procesu.<br />-Oparta na komunikatach aktywacji.<br />-Tylko protokół HTTP.|  
|Usługa aktywacji procesów systemu Windows (WAS)|-Uruchomienie usługi WCF bez instalowania usług IIS w Internecie przy użyciu różnych protokołów transportu.|-Usług IIS nie jest wymagane.<br />-Odtwarzania procesu.<br />— Shutdown bezczynności.<br />-Monitorowania kondycji procesu.<br />-Oparta na komunikatach aktywacji.<br />-Współdziała z HTTP, TCP potoków nazwanych i usługi MSMQ.|  
|IIS 7.0|-Systemem WCF usługi z [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] zawartości.<br />-Uruchomione usługi WCF w Internecie przy użyciu różnych protokołów transportu.|-ZOSTAŁ korzyści.<br />— Zintegrowane z [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] i zawartości usługi IIS.|  
  
 Wybór środowisko macierzyste zależy od wersji systemu Windows, na którym została wdrożona, transport wymaga do wysyłania wiadomości i typ procesu i odtwarzania domen aplikacji, które wymaga. Poniższa tabela zawiera podsumowanie danych dotyczących tych wymagań.  
  
|Środowisko macierzyste|Dostępne platformy|Transporty obsługiwane|Proces i odtwarzania domeny aplikacji|  
|-------------------------|---------------------------|--------------------------|-------------------------------------|  
|Zarządzane aplikacje ("hosta samodzielnego")|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> NET.TCP,<br /><br /> NET.pipe,<br /><br /> NET.MSMQ|Nie|  
|Usługi systemu Windows (wcześniej znane jako usługi NT)|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> NET.TCP,<br /><br /> NET.pipe,<br /><br /> NET.MSMQ|Nie|  
|USŁUGI IIS 5.1|[!INCLUDE[wxp](../../../includes/wxp-md.md)]|HTTP|Tak|  
|[!INCLUDE[iis601](../../../includes/iis601-md.md)]|[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]|HTTP|Tak|  
|Usługa aktywacji procesów systemu Windows (WAS)|[!INCLUDE[wv](../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> NET.TCP,<br /><br /> NET.pipe,<br /><br /> NET.MSMQ|Tak|  
  
 Należy zauważyć, że uruchomione usługi lub dowolnego rozszerzenia zabezpieczeń dokonywania niezaufanych hosta. Ponadto należy pamiętać, że podczas otwierania <xref:System.ServiceModel.ServiceHost> w ramach personifikacji, aplikacja musi zapewnić, że użytkownik nie jest zalogowany, na przykład przez buforowanie <xref:System.Security.Principal.WindowsIdentity> użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Wymagania systemowe](../../../docs/framework/wcf/wcf-system-requirements.md)  
 [Podstawowy cykl życia programowania](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md)  
 [Instrukcje: hostowanie usługi WCF w programie IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [Instrukcje: hostowanie usługi WCF w usłudze WAS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)  
 [Instrukcje: hostowanie usługi WCF w usłudze zarządzanej systemu Windows](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Instrukcje: hostowanie usługi WCF w zarządzanej aplikacji](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
