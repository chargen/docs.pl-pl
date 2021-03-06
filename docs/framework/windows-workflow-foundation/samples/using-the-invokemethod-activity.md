---
title: Za pomocą działania InvokeMethod
ms.date: 03/30/2017
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
ms.openlocfilehash: f6e32d002a4a2002037a6d74c5a2c3e275568efb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-invokemethod-activity"></a>Za pomocą działania InvokeMethod
W tym przykładzie przedstawiono sposób użycia <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) działania w celu wywołania metody publiczne klas publicznych. <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) Działanie zezwala przepływu pracy do wywołania metody obiektów, przekazywanie parametrów przechowywana wartość zwracana, określić typy metod ogólnych i określ, czy metoda jest synchroniczne lub asynchroniczne. 
  
Dostępna jest wersja nieogólnego <xref:System.Activities.Statements.InvokeMethod> działania, których wartość zwracana jest wartość <xref:System.Activities.Statements.InvokeMethod.Result%2A> właściwości i rodzajowy wersja <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) działania, w której jest zwracana wartość zwracana za pomocą <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> --> [ <code>System.Activities.Statements.InvokeMethod\`1.Result</code> ](https://msdn.microsoft.com/library/dd987724.aspx) właściwości typu `TResult`. 
  
 W tym przykładzie pokazano, jak wywołać metodę różnego. Poniższe szczegóły listy typów metody zostało to pokazane w tym przykładzie:  
  
-   Wywołanie metody wystąpienia bez parametrów.  
  
-   Wywołanie metody wystąpienia z dwoma parametrami (System.String i System.Int32).  
  
-   Wywołanie metody wystąpienia z dwóch parametrów (System.String i System.Int32) i tablicy parametrów typu System.String [].  
  
-   Wywołanie metody wystąpienia z dwoma parametrami (dwie liczb System.Int32) i wyniku typu System.Int32.  
  
     Wartość zwracana jest powiązany ze zmienną i wydrukować przy użyciu konsoli <xref:System.Activities.Statements.WriteLine> działania.  
  
-   Wywołanie metody statycznej z dwoma parametrami (System.String i System.Int32).  
  
-   Wywołanie metody wystąpienia z jednego parametru ogólnego (System.String).  
  
-   Wywołanie metody statycznej z dwa parametry ogólne (System.String i System.Int32).  
  
-   Wywołanie metody wystąpienia, który ma jeden parametr przekazywany przez odwołanie (System.String).  
  
     Parametr przywoływanego jest powiązany ze zmienną i wydrukować przy użyciu konsoli <xref:System.Activities.Statements.WriteLine> działania.  
  
-   Wywołanie metody asynchronicznej wystąpienia.  
  
## <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania InvokeMethodUsage.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`