---
title: Monitorowanie niepowodzeń operacji usługi
ms.date: 03/30/2017
ms.assetid: 59472ba3-8ebf-4479-bd7b-f440d5e636cb
ms.openlocfilehash: 3d708b537789c8d0decf75df780300c1e185c4c8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="monitoring-service-operation-failures"></a>Monitorowanie niepowodzeń operacji usługi
Jeśli śledzenie analityczne jest włączony dla aplikacji, błędów usługi łatwo można monitorować w Podglądzie zdarzeń.  W tym temacie przedstawiono sposób określania, kiedy operacji usługi nie powiedzie się i sposób określenia, jakie spowodował błąd.  
  
### <a name="determining-service-operation-failure-information"></a>Określanie informacji niepowodzenia operacji usługi  
  
1.  Otwórz Podgląd zdarzeń, klikając **Start**, **Uruchom**i wprowadzając `eventvwr.exe`.  
  
2.  Jeśli nie włączono śledzenie analityczne, rozwiń węzeł **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji serwera aplikacji** . Wybierz **widoku**, **wyświetlanie analityczne i debugowania dzienniki**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**. Pozostaw otwarte Podgląd zdarzeń, dzięki czemu można będzie wyświetlić dane śledzenia, po operacji usługi nie powiedzie się.  
  
3.  Następnie otwórz folder próbki utworzone w [Wprowadzenie — samouczek](../../../../../docs/framework/wcf/getting-started-tutorial.md) w [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] należy pamiętać, że trzeba uruchomić [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] jako administrator, dzięki czemu można utworzyć usługi. Jeśli masz zainstalowanych przykładów WCF, możesz otworzyć [wprowadzenie](../../../../../docs/framework/wcf/samples/getting-started-sample.md), zawierającą ukończone projekt utworzony w samouczku.  
  
4.  W pliku Program.cs w projekcie serwera, Dodaj następujący wiersz kodu na początku `Divide` metoda `CalculatorService` klasy:  
  
    ```  
    if (n2 == 0) throw new DivideByZeroException();  
    ```  
  
5.  W pliku Program.cs w projekcie klienta należy zmienić wartość przypisana do wartość2 od zera:  
  
    ```  
    //Call the Divide service operation  
    value1 = 22.00D;  
    value2 = 0.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0}, {1}) = {2}", value1, value2, result);  
    ```  
  
6.  Uruchom aplikację serwera bez debugowania, naciskając klawisz **Ctrl + F5**.  
  
7.  Otwórz wiersz polecenia programu Visual Studio.  Przejdź do katalogu klienta i wykonywania przez klienta z wiersza polecenia.  
  
8.  W Podglądzie zdarzeń Wyłącz i Odśwież dziennika analityczne i posortuj zdarzenia według identyfikatora zdarzenia.  Znajdź zdarzenie o identyfikatorze zdarzenia [219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md), która opisuje błąd usługi.  
  
    ```Output  
    There was an unhandled exception of type 'System.DivideByZeroException' during message processing.  Full Exception ToString: System.DivideByZeroException: Attempted to divide by zero.  
    ```  
  
    > [!NOTE]
    >  Zdarzenia są buforowane, gdy są wysyłane do podglądu zdarzeń; zdarzenia błędu nie może występować od razu.
