---
title: '&lt;message&gt; w &lt;wsDualHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75101744-eed8-4d61-91f4-5fc4473a21f2
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c2d4eda0a1975da4518d077b6cfa779a8e764a66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagegt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="6beeb-102">&lt;message&gt; w &lt;wsDualHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="6beeb-102">&lt;message&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="6beeb-103">Definiuje zabezpieczenia na poziomie komunikatu [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6beeb-103">Defines message-level security for the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="6beeb-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6beeb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6beeb-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="6beeb-105">\<bindings></span></span>  
<span data-ttu-id="6beeb-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="6beeb-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="6beeb-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="6beeb-107">\<binding></span></span>  
<span data-ttu-id="6beeb-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="6beeb-108">\<security></span></span>  
<span data-ttu-id="6beeb-109">\<komunikat ></span><span class="sxs-lookup"><span data-stu-id="6beeb-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6beeb-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="6beeb-110">Syntax</span></span>  
  
```xml  
<message   
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
     negotiateServiceCredential="Boolean"  
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"/>  
</message>  
```  
  
## <a name="type"></a><span data-ttu-id="6beeb-111">Typ</span><span class="sxs-lookup"><span data-stu-id="6beeb-111">Type</span></span>  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6beeb-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6beeb-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6beeb-113">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6beeb-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6beeb-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6beeb-114">Attributes</span></span>  
  
|<span data-ttu-id="6beeb-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6beeb-115">Attribute</span></span>|<span data-ttu-id="6beeb-116">Opis</span><span class="sxs-lookup"><span data-stu-id="6beeb-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6beeb-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="6beeb-117">algorithmSuite</span></span>|<span data-ttu-id="6beeb-118">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6beeb-118">Optional.</span></span> <span data-ttu-id="6beeb-119">Ustawia komunikat algorytmów szyfrowania i zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="6beeb-119">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="6beeb-120">Algorytmy i klucza rozmiary są określane przez <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> klasy.</span><span class="sxs-lookup"><span data-stu-id="6beeb-120">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="6beeb-121">Algorytmy te są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="6beeb-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="6beeb-122">Poniżej znajduje się możliwe wartości.</span><span class="sxs-lookup"><span data-stu-id="6beeb-122">See below for possible values.</span></span> <span data-ttu-id="6beeb-123">Wartość domyślna to `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="6beeb-123">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="6beeb-124">Właściwość clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="6beeb-124">clientCredentialType</span></span>|<span data-ttu-id="6beeb-125">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6beeb-125">Optional.</span></span> <span data-ttu-id="6beeb-126">Określa typ poświadczenia, które będą używane podczas wykonywania uwierzytelniania klienta za pomocą trybu zabezpieczeń jest `Message`.</span><span class="sxs-lookup"><span data-stu-id="6beeb-126">Specifies the type of credential to be used when performing client authentication using the security mode is `Message`.</span></span> <span data-ttu-id="6beeb-127">Poniżej znajduje się możliwe wartości.</span><span class="sxs-lookup"><span data-stu-id="6beeb-127">See below for possible values.</span></span> <span data-ttu-id="6beeb-128">Wartość domyślna to `Windows`.</span><span class="sxs-lookup"><span data-stu-id="6beeb-128">The default is `Windows`.</span></span><br /><br /> <span data-ttu-id="6beeb-129">Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="6beeb-129">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
|<span data-ttu-id="6beeb-130">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="6beeb-130">negotiateServiceCredential</span></span>|<span data-ttu-id="6beeb-131">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6beeb-131">Optional.</span></span> <span data-ttu-id="6beeb-132">Wartość logiczna określająca, czy poświadczenie usługi jest udostępniane po stronie klienta poza pasmem lub są uzyskiwane z usługi do klienta w procesie negocjacji.</span><span class="sxs-lookup"><span data-stu-id="6beeb-132">A Boolean value that specifies whether the service credential is provisioned at the client out of band or is obtained from the service to the client through a process of negotiation.</span></span> <span data-ttu-id="6beeb-133">Takie negocjacji jest macierzystych do programu exchange zwykle wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6beeb-133">Such a negotiation is a precursor to the usual message exchange.</span></span><br /><br /> <span data-ttu-id="6beeb-134">Jeśli `clientCredentialType` atrybut ma wartość None, nazwa użytkownika lub certyfikatu, ustawienie tego atrybutu na `false` oznacza, że certyfikat usługi jest dostępny po stronie klienta poza pasmem i że klienta należy określić certyfikat usługi (za pomocą [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) w [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="6beeb-134">If the `clientCredentialType` attribute equals to None, Username, or Certificate, setting this attribute to `false` implies that the service certificate is available at the client out of band and that the client needs to specify the service certificate (using the [\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) in the [\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) service behavior.</span></span> <span data-ttu-id="6beeb-135">Ten tryb jest współpraca z stosy SOAP, które implementują WS-Trust i WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="6beeb-135">This mode is interoperable with SOAP stacks which implement WS-Trust and WS-SecureConversation.</span></span><br /><br /> <span data-ttu-id="6beeb-136">Jeśli `ClientCredentialType` atrybut ma ustawioną `Windows`, ustawienie tego atrybutu na `false` określa uwierzytelniania opartego na protokołu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="6beeb-136">If the `ClientCredentialType` attribute is set to `Windows`, setting this attribute to `false` specifies Kerberos based authentication.</span></span> <span data-ttu-id="6beeb-137">Oznacza to, że klient i usługa muszą być częścią tej samej domeny protokołu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="6beeb-137">This means that the client and service must be part of the same Kerberos domain.</span></span> <span data-ttu-id="6beeb-138">Ten tryb jest współpraca z stosy SOAP, implementujące profilu token protokołu Kerberos (zgodnie z definicją w OASIS TC programu WSS) oraz protokołu WS-Trust i WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="6beeb-138">This mode is interoperable with SOAP stacks which implement the Kerberos token profile (as defined at OASIS WSS TC) as well as WS-Trust and WS-SecureConversation.</span></span> <span data-ttu-id="6beeb-139">Jeśli ten atrybut jest `true`, powoduje negocjacji .NET SOAP, który tuneli SPNego exchange za pośrednictwem wiadomości SOAP.</span><span class="sxs-lookup"><span data-stu-id="6beeb-139">When this attribute is `true`, it causes a .NET SOAP negotiation that tunnels SPNego exchange over SOAP messages.</span></span><br /><br /> <span data-ttu-id="6beeb-140">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="6beeb-140">The default is `true`.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="6beeb-141">algorithmSuite atrybutu</span><span class="sxs-lookup"><span data-stu-id="6beeb-141">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="6beeb-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="6beeb-142">Value</span></span>|<span data-ttu-id="6beeb-143">Opis</span><span class="sxs-lookup"><span data-stu-id="6beeb-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6beeb-144">Basic128</span><span class="sxs-lookup"><span data-stu-id="6beeb-144">Basic128</span></span>|<span data-ttu-id="6beeb-145">Użyj szyfrowania Aes128, Sha1 dla skrót wiadomości i Rsa-oaep-mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="6beeb-145">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6beeb-146">Basic192</span><span class="sxs-lookup"><span data-stu-id="6beeb-146">Basic192</span></span>|<span data-ttu-id="6beeb-147">Użyj szyfrowania Aes192, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="6beeb-147">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6beeb-148">Basic256</span><span class="sxs-lookup"><span data-stu-id="6beeb-148">Basic256</span></span>|<span data-ttu-id="6beeb-149">Użyj szyfrowania Aes256, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="6beeb-149">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6beeb-150">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="6beeb-150">Basic256Rsa15</span></span>|<span data-ttu-id="6beeb-151">Aes256 używany do szyfrowania wiadomości, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="6beeb-151">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6beeb-152">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="6beeb-152">Basic192Rsa15</span></span>|<span data-ttu-id="6beeb-153">Aes192 używany do szyfrowania wiadomości, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="6beeb-153">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6beeb-154">TripleDes</span><span class="sxs-lookup"><span data-stu-id="6beeb-154">TripleDes</span></span>|<span data-ttu-id="6beeb-155">Użyj szyfrowania TripleDes, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="6beeb-155">Use TripleDes encryption, , Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6beeb-156">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="6beeb-156">Basic128Rsa15</span></span>|<span data-ttu-id="6beeb-157">Aes128 używany do szyfrowania wiadomości, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="6beeb-157">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6beeb-158">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="6beeb-158">TripleDesRsa15</span></span>|<span data-ttu-id="6beeb-159">Użyj szyfrowania TripleDes, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="6beeb-159">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6beeb-160">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="6beeb-160">Basic128Sha256</span></span>|<span data-ttu-id="6beeb-161">Aes256 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="6beeb-161">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6beeb-162">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="6beeb-162">Basic192Sha256</span></span>|<span data-ttu-id="6beeb-163">Aes192 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="6beeb-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6beeb-164">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="6beeb-164">Basic256Sha256</span></span>|<span data-ttu-id="6beeb-165">Aes256 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="6beeb-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6beeb-166">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="6beeb-166">TripleDesSha256</span></span>|<span data-ttu-id="6beeb-167">TripleDes używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="6beeb-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6beeb-168">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="6beeb-168">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="6beeb-169">Aes128 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="6beeb-169">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6beeb-170">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="6beeb-170">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="6beeb-171">Aes192 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="6beeb-171">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6beeb-172">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="6beeb-172">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="6beeb-173">Aes256 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="6beeb-173">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6beeb-174">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="6beeb-174">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="6beeb-175">TripleDes używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="6beeb-175">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="6beeb-176">właściwości ClientCredentialType o wartości atrybutu</span><span class="sxs-lookup"><span data-stu-id="6beeb-176">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="6beeb-177">Wartość</span><span class="sxs-lookup"><span data-stu-id="6beeb-177">Value</span></span>|<span data-ttu-id="6beeb-178">Opis</span><span class="sxs-lookup"><span data-stu-id="6beeb-178">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6beeb-179">Brak</span><span class="sxs-lookup"><span data-stu-id="6beeb-179">None</span></span>|<span data-ttu-id="6beeb-180">Dzięki usłudze na współdziałanie z anonimowego klientów.</span><span class="sxs-lookup"><span data-stu-id="6beeb-180">This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="6beeb-181">Na stronie usługi oznacza to, że usługa nie wymaga żadnych poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="6beeb-181">On the service side, this indicates that the service does not require any client credential.</span></span> <span data-ttu-id="6beeb-182">Na komputerze klienckim oznacza to, klient nie ma żadnych poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="6beeb-182">On the client, this indicates that the client does not provide any client credential.</span></span>|  
|<span data-ttu-id="6beeb-183">Windows</span><span class="sxs-lookup"><span data-stu-id="6beeb-183">Windows</span></span>|<span data-ttu-id="6beeb-184">Umożliwia wymianę SOAP się pod uwierzytelnionego kontekstu poświadczenia systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6beeb-184">Allows the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="6beeb-185">Jeśli `negotiateServiceCredential` atrybut ma ustawioną `true`, to albo przeprowadza negocjowanie interfejsu SSPI protokołu Kerberos (interoperacyjne standard).</span><span class="sxs-lookup"><span data-stu-id="6beeb-185">If the `negotiateServiceCredential` attribute is set to `true`, this either performs an SSPI Negotiation or Kerberos (an interoperable standard).</span></span>|  
|<span data-ttu-id="6beeb-186">UserName</span><span class="sxs-lookup"><span data-stu-id="6beeb-186">UserName</span></span>|<span data-ttu-id="6beeb-187">Umożliwia usłudze wymagają który uwierzytelnienia klienta przy użyciu poświadczeń UserName.</span><span class="sxs-lookup"><span data-stu-id="6beeb-187">Allows the service to require that the client be authenticated using a UserName credential.</span></span> [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="6beeb-188">nie obsługuje wysyłanie skrótu hasła lub wyprowadzanie kluczy przy użyciu hasła i te klucze dla zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6beeb-188"> does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="6beeb-189">W efekcie [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] wymusza, czy transport jest zabezpieczone przy użyciu poświadczeń UserName.</span><span class="sxs-lookup"><span data-stu-id="6beeb-189">As such, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] enforces that the transport is secured when using UserName credentials.</span></span> <span data-ttu-id="6beeb-190">W tym trybie poświadczenia powoduje wymianę interoperacyjne lub -interoperacyjne negocjacji, na podstawie `negotiateServiceCredential` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6beeb-190">This credential mode results in either an interoperable exchange or a non-interoperable negotiation based on the `negotiateServiceCredential` attribute.</span></span>|  
|<span data-ttu-id="6beeb-191">certyfikat</span><span class="sxs-lookup"><span data-stu-id="6beeb-191">Certificate</span></span>|<span data-ttu-id="6beeb-192">Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="6beeb-192">Allows the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="6beeb-193">Jeśli używany jest tryb zabezpieczeń komunikatów i `negotiateServiceCredential` atrybut ma ustawioną `false`, klient musi zostać zainicjowana obsługa certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="6beeb-193">If message security mode is used and the `negotiateServiceCredential` attribute is set to `false`, the client needs to be provisioned with the service certificate.</span></span>|  
|<span data-ttu-id="6beeb-194">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="6beeb-194">IssuedToken</span></span>|<span data-ttu-id="6beeb-195">Określa niestandardowy token, zwykle wystawiane przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="6beeb-195">Specifies a custom token, usually issued by a Security Token Service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6beeb-196">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6beeb-196">Child Elements</span></span>  
 <span data-ttu-id="6beeb-197">Brak.</span><span class="sxs-lookup"><span data-stu-id="6beeb-197">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6beeb-198">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6beeb-198">Parent Elements</span></span>  
  
|<span data-ttu-id="6beeb-199">Element</span><span class="sxs-lookup"><span data-stu-id="6beeb-199">Element</span></span>|<span data-ttu-id="6beeb-200">Opis</span><span class="sxs-lookup"><span data-stu-id="6beeb-200">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6beeb-201">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="6beeb-201">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|<span data-ttu-id="6beeb-202">Możliwości zabezpieczeń definiuje [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6beeb-202">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6beeb-203">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6beeb-203">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSDualHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
 [<span data-ttu-id="6beeb-204">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="6beeb-204">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="6beeb-205">Powiązania</span><span class="sxs-lookup"><span data-stu-id="6beeb-205">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6beeb-206">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="6beeb-206">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="6beeb-207">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="6beeb-207">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="6beeb-208">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="6beeb-208">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)