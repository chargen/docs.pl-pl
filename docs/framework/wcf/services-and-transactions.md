---
title: Usługi i transakcje
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 85792584660bd742ad3d313bf04ef1ce88bddcc2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="services-and-transactions"></a>Usługi i transakcje
Aplikacje systemu Windows Communication Foundation (WCF) można zainicjować transakcji od klienta programu i koordynacji transakcji w operacji usługi. Klienci mogą zainicjować transakcji i wywołać kilka operacji usługi i upewnij się, że operacje usługi są zatwierdzona lub wycofana jako pojedyncza jednostka.  
  
 Zachowanie transakcji w kontrakcie usługi można włączyć, określając <xref:System.ServiceModel.ServiceBehaviorAttribute> i ustawienie jej <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> i <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> właściwości dla operacji usługi, które wymagają klienta transakcji. <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Parametr określa, czy transakcja, w której wykonuje metodę jest wprowadzana automatycznie, jeśli nie nieobsługiwane wyjątki są zgłaszane. Aby uzyskać więcej informacji o tych atrybutów, zobacz [atrybuty transakcji elementu ServiceModel](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
 Praca jest wykonywana w ramach operacji usługi i zarządzany przez Menedżera zasobów, takich jak rejestrowanie aktualizacje bazy danych jest częścią transakcji klienta.  
  
 W poniższym przykładzie pokazano użycie <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> atrybuty do kontrolowania zachowania transakcji po stronie serwera.  
  
```  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog(String.Format("Added {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog(String.Format("Subtracted {0} from {1}", n1, n2));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog(String.Format("Multiplied {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog(String.Format("Divided {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
}  
```  
  
 Można włączyć transakcji i transakcji przepływać przez skonfigurowanie klienta i usługi powiązania do korzystania z protokołu WS-AtomicTransaction oraz ustawienie [ \<transactionFlow >](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) elementu `true`, jak pokazano w poniższych Przykładowa konfiguracja.  
  
```xml  
<client>  
    <endpoint address="net.tcp://localhost/ServiceModelSamples/service"   
          binding="netTcpBinding"   
          bindingConfiguration="netTcpBindingWSAT"   
          contract="Microsoft.ServiceModel.Samples.ICalculatorLog" />  
</client>  
  
<bindings>  
    <netTcpBinding>  
        <binding name="netTcpBindingWSAT"  
                transactionFlow="true"  
                transactionProtocol="WSAtomicTransactionOctober2004" />  
     </netTcpBinding>  
</bindings>  
```  
  
 Klientów można rozpocząć transakcji, tworząc <xref:System.Transactions.TransactionScope> i wywoływanie operacji usługi w zakresie transakcji.  
  
```  
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa transakcyjna w elemencie System.ServiceModel](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)  
 [Modele transakcji](../../../docs/framework/wcf/feature-details/transaction-models.md)  
 [Przepływ transakcji WS](../../../docs/framework/wcf/samples/ws-transaction-flow.md)
