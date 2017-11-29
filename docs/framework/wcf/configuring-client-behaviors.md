---
title: "Konfigurowanie zachowań klienta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6f16f32128c7223fa600802ae593d36286847dc8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="d2d21-102">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="d2d21-102">Configuring Client Behaviors</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="d2d21-103">Konfiguruje zachowań na dwa sposoby: poprzez odwołujących się do konfiguracji zachowania — które są zdefiniowane w `<behavior>` sekcji pliku konfiguracji aplikacji klienta — lub programowo w aplikacji wywołującej.</span><span class="sxs-lookup"><span data-stu-id="d2d21-103"> configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="d2d21-104">W tym temacie opisano obu podejść.</span><span class="sxs-lookup"><span data-stu-id="d2d21-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="d2d21-105">Podczas korzystania z pliku konfiguracji, konfiguracji zachowanie jest nazwany zestaw ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d2d21-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="d2d21-106">Nazwa konfiguracji każdego zachowanie musi być unikatowa.</span><span class="sxs-lookup"><span data-stu-id="d2d21-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="d2d21-107">Ten ciąg jest używany w `behaviorConfiguration` atrybutu konfiguracji punktu końcowego do łączenia punktu końcowego do zachowania.</span><span class="sxs-lookup"><span data-stu-id="d2d21-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2d21-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2d21-108">Example</span></span>  
 <span data-ttu-id="d2d21-109">Poniższy kod konfiguracji definiuje zachowanie nazywane `myBehavior`.</span><span class="sxs-lookup"><span data-stu-id="d2d21-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="d2d21-110">Punkt końcowy klienta odwołuje się do tego zachowania w `behaviorConfiguration` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d2d21-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="myBehavior">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="myBinding" maxReceivedMessageSize="10000" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="myAddress" binding="basicHttpBinding" bindingConfiguration="myBinding" behaviorConfiguration="myBehavior" contract="myContract" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="d2d21-111">Programowo za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="d2d21-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="d2d21-112">Można również skonfigurować lub wstawić zachowania programowo dzięki umieszczeniu odpowiednie `Behaviors` właściwość [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] obiektu klienta lub w obiekcie fabryki kanału klienta przed otwarciem klienta.</span><span class="sxs-lookup"><span data-stu-id="d2d21-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2d21-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2d21-113">Example</span></span>  
 <span data-ttu-id="d2d21-114">Poniższy przykładowy kod przedstawia sposób programowane Wstawianie zachowanie po zalogowaniu się do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> właściwość <xref:System.ServiceModel.Description.ServiceEndpoint> zwrócony z <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> właściwości przed utworzenia obiektu kanału.</span><span class="sxs-lookup"><span data-stu-id="d2d21-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="d2d21-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2d21-115">See Also</span></span>  
 [<span data-ttu-id="d2d21-116">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="d2d21-116">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)