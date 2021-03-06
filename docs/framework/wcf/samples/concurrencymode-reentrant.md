---
title: Procedura wielobieżna ConcurrencyMode
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: d0ecd4b0c39c6a736a176a61490f454c2bab2e20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="concurrencymode-reentrant"></a>Procedura wielobieżna ConcurrencyMode
W przykładzie pokazano konieczność i zagadnień dotyczących używania pomocą właściwości ConcurrencyMode.Reentrant implementacji usługi. Pomocą właściwości ConcurrencyMode.Reentrant oznacza, że usługa (lub wywołania zwrotnego) przetwarza tylko jeden komunikat w danym momencie (odpowiednikiem `ConcurencyMode.Single`). Aby zapewnić bezpieczeństwo wątków, blokuje Windows Communication Foundation (WCF) `InstanceContext` przetwarza komunikat, że nie inne komunikaty mogą być przetwarzane. W przypadku trybu współużytkowane `InstanceContext` jest odblokowany, tuż przed usługa wykonuje wywołanie wychodzące, umożliwiając kolejne wywołania (która może być współużytkowane, jak pokazano w przykładzie) można uzyskać blokady następnym pochodzi z usługą. Aby zademonstrować zachowanie, próbki pokazuje, jak klient i usługa może wysyłać wiadomości między sobą za pomocą kontraktu dwukierunkowego.  
  
 Kontrakt zdefiniowany jest kontrakt dupleksu `Ping` Metoda implementowana przez usługę i metodę wywołania zwrotnego `Pong` implementowana przez klienta. Klient wywołuje serwera `Ping` metody za pomocą znaczników liczba, tym samym inicjowanie wywołanie. Usługa sprawdza, czy liczba cykli nie jest równa 0, a następnie wywołuje wywołania zwrotne `Pong` metoda podczas zmniejszanie liczby znaczników. Jest to realizowane przez następujący kod w próbce.  
  
```  
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
```  
  
 Wywołanie zwrotne `Pong` implementacji ma tej samej logiki, `Ping` implementacji. Oznacza to, sprawdza, czy liczba cykli nie jest równa zero, a następnie wywołuje `Ping` metody w kanale wywołania zwrotnego (w tym przypadku jest kanału, który został użyty do wysłania oryginalnej `Ping` wiadomości) o znaczników liczba zmniejszany przez 1. Liczba cykli wynosić 0, metoda zwraca co momentu odkodowywania wszystkie odpowiedzi do pierwsze wywołanie przez klienta, który zainicjował rozmowę telefoniczną. Przedstawiono to w celu wykonania wywołania zwrotnego.  
  
```  
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
```  
  
 Zarówno `Ping` i `Pong` metody są żądania/odpowiedzi, co oznacza, że w pierwszym wywołaniu `Ping` nie powróci do wywołania `CallbackChannel<T>.Pong()` zwraca. Na komputerze klienckim `Pong` nie może zwracać aż do następnego `Ping` wywołanie, że on zwraca. Ponieważ zarówno wywołania zwrotnego, jak i usługi musi być wychodzące żądania/odpowiedzi przed ich odpowiedzieć oczekujące żądania, zachowanie pomocą właściwości ConcurrencyMode.Reentrant muszą być oznaczone zarówno implementacji.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="demonstrates"></a>Demonstracje  
 Aby uruchomić przykład, kompilacji projektów klienta i serwera. Następnie otwórz dwa okna polecenia i przejdź do \<próbki > \CS\Service\bin\debug i \<próbki > \CS\Client\bin\debug katalogów. Następnie uruchom usługę, wpisując `service.exe` , a następnie wywołać Client.exe o początkowej wartości Takty przekazany jako argument wejściowy. Przedstawiono przykładowe dane wyjściowe do 10 znaczniki osi.  
  
```  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
```  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
  
## <a name="see-also"></a>Zobacz też
