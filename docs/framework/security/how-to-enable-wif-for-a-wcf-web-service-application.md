---
title: 'Porady: Włączanie programu WIF dla aplikacji usługi sieci Web WCF'
ms.date: 03/30/2017
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: bd0ad5392010772c3205d8f148c985de2706de01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a>Porady: Włączanie programu WIF dla aplikacji usługi sieci Web WCF
## <a name="applies-to"></a>Dotyczy:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Microsoft® Windows® Communication Foundation (WCF)  
  
## <a name="summary"></a>Podsumowanie  
 Niniejszy instruktaż zawiera szczegółowe procedury krok po kroku służące do włączania środowiska WIF w usłudze internetowej WCF. Znajdują się tu również instrukcje testowania aplikacji pozwalające sprawdzić, czy usługa internetowa poprawnie przedstawia oświadczenia w trakcie działania aplikacji. Instruktaż nie zawiera szczegółowych instrukcji tworzenia usługi tokenów zabezpieczających (STS). Zamiast tego wykorzystuje deweloperską usługę STS wbudowaną w narzędziu Tożsamość i dostęp. Deweloperska usługa STS nie wykonuje faktycznego uwierzytelniania i jest przeznaczona tylko do celów testowych. Narzędzie Tożsamość i dostęp jest koniecznie do ukończenia całego instruktażu. Można go pobrać z następującej lokalizacji: [tożsamości i dostępu do narzędzia](http://go.microsoft.com/fwlink/?LinkID=245849)  
  
## <a name="contents"></a>Spis treści  
  
-   Cele  
  
-   Omówienie  
  
-   Zestawienie czynności  
  
-   Krok 1 — Utworzenie prostej usługi WCF  
  
-   Krok 2 — Utworzenie aplikacji klienckiej dla usługi WCF  
  
-   Krok 3 — Przetestowanie rozwiązania  
  
## <a name="objectives"></a>Cele  
  
-   Utworzenie usługi WCF wymagającej wystawionych tokenów  
  
-   Utworzenie klienta WCF, który wymaga tokenu od usługi STS, po czym przekazuje go do usługi WCF  
  
## <a name="overview"></a>Omówienie  
 Ten instruktaż ma pokazać, jak programista może używać funkcji federacyjnego uwierzytelniania podczas tworzenia usług WCF. Oto kilka najważniejszych zalet stosowania mechanizmu federacji w usługach WCF:  
  
1.  Wyprowadzenie logiki uwierzytelniania poza kod usługi WCF  
  
2.  Wykorzystanie istniejących rozwiązań do zarządzania tożsamościami  
  
3.  Współpraca z innymi systemami zarządzania tożsamością  
  
4.  Elastyczność i odporność na przyszłe zmiany  
  
 Środowisko WIF wraz z towarzyszącym narzędziem Tożsamość i dostęp ułatwia tworzenie oraz testowanie usług WCF dzięki wykorzystaniu funkcjonalności federacyjnego uwierzytelniania. Pokazano to poniżej.  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
-   Krok 1 — Utworzenie prostej usługi WCF  
  
-   Krok 2 — Utworzenie aplikacji klienckiej dla usługi WCF  
  
-   Krok 3 — Przetestowanie rozwiązania  
  
## <a name="step-1--create-a-simple-wcf-service"></a>Krok 1 — Utworzenie prostej usługi WCF  
 W tym kroku utworzysz nową usługę WCF, która wykorzystuje deweloperską usługę STS dołączoną do narzędzia Tożsamość i dostęp.  
  
#### <a name="to-create-a-simple-wcf-service"></a>Aby utworzyć prostą usługę WCF  
  
1.  Uruchom program Visual Studio w trybie podwyższonych uprawnień jako administrator.  
  
2.  W programie Visual Studio, kliknij przycisk **pliku**, kliknij przycisk **nowy**, a następnie kliknij przycisk **projektu**.  
  
3.  W **nowy projekt** okna, kliknij przycisk **aplikacji usługi WCF**.  
  
4.  W **nazwa**, wprowadź `TestService` i naciśnij klawisz **OK**.  
  
5.  Kliknij prawym przyciskiem myszy **TestService** projektu w obszarze **Eksploratora rozwiązań**, a następnie wybierz pozycję **tożsamościami i dostępem**.  
  
6.  **Tożsamościami i dostępem** zostanie wyświetlone okno. W obszarze **dostawców**, wybierz pozycję **testowania aplikacji z lokalnej usługi STS programowanie**, następnie kliknij przycisk **Zastosuj**. Tożsamość i narzędzia dostępu do konfigurowania usługi do używania WIF i zewnętrzny uwierzytelniania do rozwoju lokalnej usługi STS (**LocalSTS**) przez dodanie elementów konfiguracji do *Web.config* pliku.  
  
7.  W *Service1.svc.cs* plików, dodawanie `using` dyrektywy dla **System.Security.Claims** przestrzeni nazw i Zastąp istniejący kod poniżej, a następnie zapisz plik:  
  
    ```csharp  
    public class Service1 : IService1  
    {  
        public string ComputeResponse(string input)  
        {  
            // Get the caller's identity from ClaimsPrincipal.Current  
            ClaimsPrincipal claimsPrincipal = OperationContext.Current.ClaimsPrincipal;  
  
            // Start generating the output  
            StringBuilder builder = new StringBuilder();  
            builder.AppendLine("Computed by ClaimsAwareWebService");  
            builder.AppendLine("Input received from client:" + input);  
  
            if (claimsPrincipal != null)  
            {  
                // Display the claims from the caller. Do not use this code in a production application.  
                ClaimsIdentity identity = claimsPrincipal.Identity as ClaimsIdentity;  
                builder.AppendLine("Client Name:" + identity.Name);  
                builder.AppendLine("IsAuthenticated:" + identity.IsAuthenticated);  
                builder.AppendLine("The service received the following issued claims of the client:");  
  
                // Iterate over the caller’s claims and append to the output  
                foreach (Claim claim in claimsPrincipal.Claims)  
                {  
                    builder.AppendLine("ClaimType :" + claim.Type + "   ClaimValue:" + claim.Value);  
                }  
            }  
  
            return builder.ToString();  
        }  
    }  
    ```  
  
     `ComputeResponse` Metoda Wyświetla właściwości różne oświadczenia, które są wystawiane przez **LocalSTS**.  
  
8.  W *IService1.cs* pliku, Zastąp istniejący kod następującym kodem, a następnie zapisz plik:  
  
    ```csharp  
    [ServiceContract]  
    public interface IService1  
    {  
        [OperationContract]  
        string ComputeResponse(string input);  
    }  
    ```  
  
9. Skompiluj projekt.  
  
10. Naciśnij klawisz **Ctrl-F5** do uruchamiania usługi bez konieczności uruchamiania debugera. Należy otworzyć stronę sieci Web na potrzeby usługi i sprawdź, czy **LocalSTS** działa przez wyszukiwanie w obszarze powiadomień (na pasku zadań).  
  
    > [!IMPORTANT]
    >  Zarówno **TestService** i **LocalSTS** musi być uruchomiona podczas dodawania odwołania do usługi do aplikacji klienckiej w następnym kroku.  
  
## <a name="step-2--create-a-client-application-for-the-wcf-service"></a>Krok 2 — Utworzenie aplikacji klienckiej dla usługi WCF  
 W tym kroku utworzysz aplikację konsoli, która za pomocą deweloperskiej usługi STS będzie się uwierzytelniać w usłudze WCF utworzonej w poprzednim kroku.  
  
#### <a name="to-create-a-client-application"></a>Aby utworzyć aplikację kliencką  
  
1.  W programie Visual Studio, kliknij prawym przyciskiem myszy rozwiązanie, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy projekt**.  
  
2.  W **Dodawanie nowego projektu** wybierz **aplikacji konsoli** z **Visual C#** szablony list, wprowadź `Client`, a następnie naciśnij klawisz **OK**. Nowy projekt zostanie utworzony w folderze rozwiązania.  
  
3.  Kliknij prawym przyciskiem myszy **odwołania** w obszarze **klienta** projektu, a następnie kliknij przycisk **Dodaj odwołanie do usługi**.  
  
4.  W **Dodaj odwołanie do usługi** okna, kliknij strzałkę listy rozwijanej w **odnajdowania** przycisk **usług w rozwiązaniu**. **Adres** zostaną wypełnione automatycznie z usługą WCF został utworzony wcześniej, i **Namespace** zostanie ustawiona do **ServiceReference1**. Kliknij przycisk **OK**.  
  
    > [!IMPORTANT]
    >  Zarówno **TestService** i **LocalSTS** musi być uruchomiona podczas dodawania odwołania do usługi do klienta.  
  
5.  Program Visual Studio wygeneruje klasy serwera proxy dla usługi WCF i doda wszystkie niezbędne parametry odwołań. Spowoduje to również dodanie elementów do *App.config* plik, aby skonfigurować klienta do pobrania tokenu z STS do uwierzytelniania w usłudze. Po zakończeniu tego procesu **Program.cs** plik zostanie otwarty. Dodaj `using` dyrektywy dla **System.ServiceModel** i drugi dla **Client.ServiceReference1**, Zastąp **Main** metodę z następującym kodem, a następnie Zapisz plik:  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        // Create the client for the service  
        Service1Client client = new Service1Client();  
        Console.WriteLine("-------------WCF Client Application--------------\n");  
  
        while (!ShouldQuitApplication())  
        {  
            try  
            {  
                Console.WriteLine(client.ComputeResponse("Hello World"));  
            }  
            catch (CommunicationException e)  
            {  
                Console.WriteLine(e.Message);  
                Console.WriteLine(e.StackTrace);  
                Exception ex = e.InnerException;  
                while (ex != null)  
                {  
                    Console.WriteLine("===========================");  
                    Console.WriteLine(ex.Message);  
                    Console.WriteLine(ex.StackTrace);  
                    ex = ex.InnerException;  
                }  
            }  
            catch (TimeoutException)  
            {  
                Console.WriteLine("Timed out...");  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("An unexpected exception occurred.");  
                Console.WriteLine(e.StackTrace);  
            }  
        }  
  
        client.Close();  
  
        if (client != null)  
        {  
            client.Abort();  
        }  
    }  
  
    static bool ShouldQuitApplication()  
    {  
        Console.WriteLine("---------------------------------------------------------------------");  
        Console.WriteLine("Press Enter key to invoke service, any other key to quit application:");  
        Console.WriteLine("----------------------------------------------------------------------");  
  
        ConsoleKeyInfo keyInfo = Console.ReadKey();  
        if (keyInfo.Key == ConsoleKey.Enter)  
            return false;  
        return true;  
    }  
    ```  
  
6.  Otwórz *App.config* i Dodaj następujący kod XML jako pierwszy element podrzędny w `<system.serviceModel>` elementu, a następnie zapisz ten plik:  
  
    ```xml  
    <behaviors>  
       <endpointBehaviors>  
         <behavior>  
           <clientCredentials>  
             <serviceCertificate>  
               <authentication certificateValidationMode="None"/>  
             </serviceCertificate>  
           </clientCredentials>  
         </behavior>  
       </endpointBehaviors>  
     </behaviors>  
    ```  
  
     Spowoduje to wyłączenie mechanizmu sprawdzania poprawności certyfikatów.  
  
7.  Kliknij prawym przyciskiem myszy **TestService** rozwiązania i kliknij pozycję **Ustaw projekty startowe**. **Projekt startowy** zostanie otwarta strona właściwości. W **projekt startowy** strony właściwości, wybierz opcję **wiele projektów startowych** kliknięcie w **akcji** dla każdego projektu i wybierz pole **Start** z menu rozwijanego. Kliknij przycisk **OK** Aby zapisać ustawienia.  
  
8.  Skompiluj rozwiązanie.  
  
## <a name="step-3--test-your-solution"></a>Krok 3 — Przetestowanie rozwiązania  
 W tym kroku przetestujesz aplikację WCF korzystającą ze środowiska WIF i sprawdzisz, czy są prezentowane oświadczenia.  
  
#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a>Aby przetestować aplikację WCF używającą środowiska WIF pod kątem oświadczeń  
  
1.  Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację. Powinny być prezentowane z okna konsoli i następujący tekst: **naciśnij klawisz Enter, klucz do wywołania usługi, dowolny klawisz, aby zakończyć pracę aplikacji:**  
  
2.  Naciśnij klawisz **Enter**, oraz następujących informacji oświadczeń powinny być wyświetlane w konsoli:  
  
    ```  
    Computed by Service1  
    Input received from client: Hello World  
    Client Name: Terry  
    IsAuthenticated: True  
    The service received the following issued claims of the client:  
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name    ClaimValue:Terry  
    ClaimType :http://schema.xmlsoap.org/ws/2005/05/identity/claims/surname    ClaimValue:Adams  
    ClaimType :http://schemas.microsoft.com/ws/2008/06/identity/claims/role    ClaimValue:developer  
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress    ClaimValue:terry@contoso.com  
    ```  
  
    > [!IMPORTANT]
    >  Zarówno **TestService** i **LocalSTS** musi być uruchomiona przed naciśnięciem przycisku **Enter**. Należy otworzyć stronę sieci Web na potrzeby usługi i sprawdź, czy **LocalSTS** działa przez wyszukiwanie w obszarze powiadomień (na pasku zadań).  
  
3.  Jeśli te oświadczenia widać w konsoli, dokonano pomyślnego uwierzytelnienia w usłudze STS pozwalającego na wyświetlanie oświadczeń z usługi WCF.
