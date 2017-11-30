---
title: Komunikacji asynchronicznej
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1b9435342d73fc5cb292ee72781362146604ce9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronous-communication"></a>Komunikacji asynchronicznej
W tym przykładzie pokazano sposób komunikacji między dwóch różnych [!INCLUDE[wf](../../../../includes/wf-md.md)] usług jest wykonywane asynchronicznie domyślnie.  
  
## <a name="demonstrates"></a>Demonstracje  
 Asynchroniczną komunikację między [!INCLUDE[wf1](../../../../includes/wf1-md.md)] usług.  
  
## <a name="discussion"></a>Omówienie  
 W tym przykładzie pokazano sposób komunikacji między [!INCLUDE[wf1](../../../../includes/wf1-md.md)] aplikacji jest wykonywane asynchronicznie za pomocą działania obsługi komunikatów dostarczonych przez .NET Framework.  
  
 W tym przykładzie składa się z następujących trzech projektach.  
  
 CreditCheckService  
 Ta usługa odbiera wynik środki danej osoby lub wartość elementu uzyskanie, a następnie decyduje o tym, czy środków znajduje się z osobą.  
  
 RentalApprovalService  
 Ta usługa odbiera aplikacji od osoby, która wymaga certyfikat. Ta usługa komunikuje asynchronicznie `CreditCheckService` zdecydować, czy aplikacja kredytowej jest prawidłowy.  
  
 Klient  
 Klient komunikuje się synchronicznie z `RentalApprovalService` wiedzieć, czy jest zatwierdzona środków.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Kliknij prawym przyciskiem myszy **AsynchronousCommunication** rozwiązania i wybierz **właściwości**.  
  
2.  W **wspólne właściwości**, wybierz pozycję **projekt startowy**i wybierz **wiele projektów startowych**.  
  
3.  Przenieś **RentalApprovalService** na pierwszą pozycję na liście, a następnie **CreditCheckService**, a następnie **klienta**. Ustaw **Start** akcji we wszystkich trzech projektach.  
  
4.  Kliknij przycisk **OK**, i naciśnij klawisz F5, aby uruchomić przykład.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`