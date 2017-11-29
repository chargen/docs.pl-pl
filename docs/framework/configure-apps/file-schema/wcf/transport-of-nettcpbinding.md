---
title: '&lt;transport&gt; w &lt;netTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: adec2ce082f063f5d3f2cff2c1c428a770aeb76d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltnettcpbindinggt"></a><span data-ttu-id="8b667-102">&lt;transport&gt; w &lt;netTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="8b667-102">&lt;transport&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="8b667-103">Określa typ zabezpieczenia na poziomie komunikatu wymagania dotyczące punkt końcowy skonfigurowany [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8b667-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="8b667-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8b667-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8b667-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="8b667-105">\<bindings></span></span>  
<span data-ttu-id="8b667-106">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="8b667-106">\<netTcpBinding></span></span>  
<span data-ttu-id="8b667-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="8b667-107">\<binding></span></span>  
<span data-ttu-id="8b667-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="8b667-108">\<security></span></span>  
<span data-ttu-id="8b667-109">\<transport ></span><span class="sxs-lookup"><span data-stu-id="8b667-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b667-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b667-110">Syntax</span></span>  
  
```xml  
<netTcpBinding>  
    <binding>  
        <security  
         mode="None|Transport|Message|TransportWithMessageCredential">  
            <transport clientCredentialType="None|Windows|Certificate"  
             protectionLevel="None|Sign|EncryptAndSign"             sslProtocols="Tls|Tls11|Tls12">  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</netTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b667-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8b667-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8b667-112">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8b667-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b667-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8b667-113">Attributes</span></span>  
  
|<span data-ttu-id="8b667-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8b667-114">Attribute</span></span>|<span data-ttu-id="8b667-115">Opis</span><span class="sxs-lookup"><span data-stu-id="8b667-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8b667-116">Właściwość clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="8b667-116">clientCredentialType</span></span>|<span data-ttu-id="8b667-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8b667-117">Optional.</span></span> <span data-ttu-id="8b667-118">Określa typ poświadczenia, które będą używane podczas uwierzytelniania klienta za pomocą zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="8b667-118">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="8b667-119">— Wartość domyślna to `Windows`.</span><span class="sxs-lookup"><span data-stu-id="8b667-119">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="8b667-120">— Ten atrybut jest typu <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="8b667-120">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="8b667-121">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="8b667-121">protectionLevel</span></span>|<span data-ttu-id="8b667-122">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8b667-122">Optional.</span></span> <span data-ttu-id="8b667-123">Definiuje zabezpieczeń na poziomie transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="8b667-123">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="8b667-124">Podpisywanie wiadomości zmniejsza ryzyko innych firm, manipulowanie wiadomości, gdy są przesyłane.</span><span class="sxs-lookup"><span data-stu-id="8b667-124">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="8b667-125">Szyfrowanie zapewnia ochronę poufności poziom danych podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="8b667-125">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="8b667-126">Wartość domyślna to `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="8b667-126">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="8b667-127">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="8b667-127">sslProtocols</span></span>|<span data-ttu-id="8b667-128">Wartość flagi wyliczenia SslProtocols określająca, które SslProtocols są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="8b667-128">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="8b667-129">Wartość domyślna to protokołu Tls &#124; Tls11 &#124; Tls12.</span><span class="sxs-lookup"><span data-stu-id="8b667-129">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="8b667-130">Właściwość policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="8b667-130">policyEnforcement</span></span>|<span data-ttu-id="8b667-131">To wyliczenie Określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> powinny być wymuszane.</span><span class="sxs-lookup"><span data-stu-id="8b667-131">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="8b667-132">1.  Nigdy nie — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="8b667-132">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="8b667-133">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochrony rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="8b667-133">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="8b667-134">3.  Zawsze — zasady zawsze są wymuszane.</span><span class="sxs-lookup"><span data-stu-id="8b667-134">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="8b667-135">Klienci, którzy nie obsługują ochrony rozszerzonej będzie mogło uwierzytelnić.</span><span class="sxs-lookup"><span data-stu-id="8b667-135">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="8b667-136">właściwości ClientCredentialType o wartości atrybutu</span><span class="sxs-lookup"><span data-stu-id="8b667-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="8b667-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="8b667-137">Value</span></span>|<span data-ttu-id="8b667-138">Opis</span><span class="sxs-lookup"><span data-stu-id="8b667-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8b667-139">Brak</span><span class="sxs-lookup"><span data-stu-id="8b667-139">None</span></span>|<span data-ttu-id="8b667-140">Klient jest anonimowy.</span><span class="sxs-lookup"><span data-stu-id="8b667-140">The client is anonymous.</span></span> <span data-ttu-id="8b667-141">Wymaga certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="8b667-141">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="8b667-142">Windows</span><span class="sxs-lookup"><span data-stu-id="8b667-142">Windows</span></span>|<span data-ttu-id="8b667-143">Określa uwierzytelnianie systemu Windows dla klienta przy użyciu negocjacji SP (negocjacji protokołu Kerberos).</span><span class="sxs-lookup"><span data-stu-id="8b667-143">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="8b667-144">certyfikat</span><span class="sxs-lookup"><span data-stu-id="8b667-144">Certificate</span></span>|<span data-ttu-id="8b667-145">Klient jest uwierzytelniany przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="8b667-145">The client is authenticated using a certificate.</span></span> <span data-ttu-id="8b667-146">Używa negocjacji w protokole SSL i wymaga certyfikatu dla usługi.</span><span class="sxs-lookup"><span data-stu-id="8b667-146">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="8b667-147">Atrybut protectionLevel</span><span class="sxs-lookup"><span data-stu-id="8b667-147">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="8b667-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="8b667-148">Value</span></span>|<span data-ttu-id="8b667-149">Opis</span><span class="sxs-lookup"><span data-stu-id="8b667-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8b667-150">Brak</span><span class="sxs-lookup"><span data-stu-id="8b667-150">None</span></span>|<span data-ttu-id="8b667-151">Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="8b667-151">No protection.</span></span>|  
|<span data-ttu-id="8b667-152">Zaloguj się</span><span class="sxs-lookup"><span data-stu-id="8b667-152">Sign</span></span>|<span data-ttu-id="8b667-153">Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="8b667-153">Messages are signed.</span></span>|  
|<span data-ttu-id="8b667-154">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="8b667-154">EncryptAndSign</span></span>|<span data-ttu-id="8b667-155">— Liczba komunikatów są zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="8b667-155">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b667-156">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8b667-156">Child Elements</span></span>  
 <span data-ttu-id="8b667-157">Brak</span><span class="sxs-lookup"><span data-stu-id="8b667-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b667-158">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8b667-158">Parent Elements</span></span>  
  
|<span data-ttu-id="8b667-159">Element</span><span class="sxs-lookup"><span data-stu-id="8b667-159">Element</span></span>|<span data-ttu-id="8b667-160">Opis</span><span class="sxs-lookup"><span data-stu-id="8b667-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b667-161">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="8b667-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="8b667-162">Określa możliwości zabezpieczeń [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8b667-162">Specifies the security capabilities of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b667-163">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b667-163">Remarks</span></span>  
 <span data-ttu-id="8b667-164">Należy użyć zabezpieczeń transportu, integralności i poufności komunikatu protokołu SOAP i do wzajemnego uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="8b667-164">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="8b667-165">Zaznaczenie tego trybu zabezpieczeń dla powiązania kanału stosu jest konfigurowana przy użyciu bezpiecznego transportu i wiadomości SOAP są zabezpieczone za pomocą zabezpieczeń transportu, takie jak Windows (Negotiate) lub protokołu SSL za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="8b667-165">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b667-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b667-166">See Also</span></span>  
 <xref:System.ServiceModel.TcpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="8b667-167">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="8b667-167">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="8b667-168">Powiązania</span><span class="sxs-lookup"><span data-stu-id="8b667-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8b667-169">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="8b667-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="8b667-170">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="8b667-170">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="8b667-171">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="8b667-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)