---
title: Wykonania przepływu pracy w TransactionScope Imperatywne
ms.date: 03/30/2017
ms.assetid: bd0e8686-c1d0-4400-a541-da94ed03afc7
ms.openlocfilehash: 44efc13efaa45274068fb44cc154b515bd774a35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="execute-a-workflow-in-an-imperative-transactionscope"></a>Wykonania przepływu pracy w TransactionScope Imperatywne
W tym przykładzie pokazano, jak wykonywanie przepływu pracy za pomocą <xref:System.Activities.WorkflowInvoker> w obszarze <xref:System.Transactions.Transaction> z natury kodu C#.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 W trybie kod C# <xref:System.Transactions.TransactionScope> jest używany w celu hermetyzacji zestawu pracy, który wykonuje w tej samej transakcji. <xref:System.Transactions.TransactionScope> Polega na tworzeniu transakcja otoczenia i Inicjowanie <xref:System.Transactions.Transaction.Current%2A> właściwości, które następnie są dostępne dla każdej pracy wykonywanej w tym wątku.  
  
 Aby uzyskać równoważne zachowanie w przepływie pracy, środowisko uruchomieniowe ma wykonywać dodatkowe zadania inicjowania <xref:System.Transactions.Transaction.Current%2A> przed wykonaniem każde działanie, ponieważ przepływ pracy nie przechowuje koligacji wątku między działaniami. Z tym obsługa środowiska uruchomieniowego efekty jest to, że podczas wykonywania przepływu pracy z <xref:System.Activities.WorkflowInvoker> wewnątrz <xref:System.Transactions.TransactionScope>, wszystkie działania dotrą do uruchamiania w kontekście transakcja otoczenia utworzone przez <xref:System.Transactions.TransactionScope>.  
  
 Przepływ pracy może mieć tylko jeden transakcja otoczenia dla każdego wystąpienia przepływu pracy; Transakcje zagnieżdżone nie są dostępne. Nawet jeśli przepływ pracy zawiera <xref:System.Activities.Statements.TransactionScope> aktywności, to nie tworzy nową transakcję wewnętrzny. Zamiast tego ponownie to transakcja otoczenia, który został utworzony poza przepływ pracy.  
  
 Przykład rozpoczyna nową <xref:System.Transactions.TransactionScope>, wyświetla identyfikator transakcji i rozpocznie się za pomocą przepływu pracy <xref:System.Activities.WorkflowInvoker>. Przepływ pracy drukuje transakcji identyfikator ponownie, pokazujący, że jest tej samej transakcji, a następnie uruchamia <xref:System.Activities.Statements.TransactionScope>, następnie kończy. <xref:System.Activities.WorkflowInvoker.Invoke%2A> Wywołać <xref:System.Activities.WorkflowInvoker> jest synchroniczne, więc oryginalnego wątku blokuje do momentu ukończenia przepływu pracy. Po zakończeniu przepływu pracy zakończeniu transakcji, a zasoby usunięte.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania ImperativeTransactionSample.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\ImperativeTransaction`