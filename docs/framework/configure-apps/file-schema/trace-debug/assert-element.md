---
title: "&lt;Assert&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 520dfec180157c9a05c5fc3beb51b5fc17f9088b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltassertgt-element"></a><span data-ttu-id="b8f77-102">&lt;Assert&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="b8f77-102">&lt;assert&gt; Element</span></span>
<span data-ttu-id="b8f77-103">Określa, czy wyświetlać okno komunikatu po wywołaniu <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metody; określa także nazwę pliku do zapisania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="b8f77-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  
  
 <span data-ttu-id="b8f77-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="b8f77-104">\<configuration></span></span>  
<span data-ttu-id="b8f77-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="b8f77-105">\<system.diagnostics></span></span>  
<span data-ttu-id="b8f77-106">\<Assert ></span><span class="sxs-lookup"><span data-stu-id="b8f77-106">\<assert></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8f77-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8f77-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8f77-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b8f77-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b8f77-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b8f77-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8f77-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b8f77-110">Attributes</span></span>  
  
|<span data-ttu-id="b8f77-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b8f77-111">Attribute</span></span>|<span data-ttu-id="b8f77-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b8f77-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="b8f77-113">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b8f77-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b8f77-114">Określa, czy do wyświetlenia komunikatu dialogowe **Debug.Assert** daje w wyniku metody **false**.</span><span class="sxs-lookup"><span data-stu-id="b8f77-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="b8f77-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b8f77-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b8f77-116">Określa nazwę pliku do zapisu, jeśli komunikat **Debug.Assert** daje w wyniku **false**.</span><span class="sxs-lookup"><span data-stu-id="b8f77-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="b8f77-117">assertuienabled atrybutu</span><span class="sxs-lookup"><span data-stu-id="b8f77-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="b8f77-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="b8f77-118">Value</span></span>|<span data-ttu-id="b8f77-119">Opis</span><span class="sxs-lookup"><span data-stu-id="b8f77-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="b8f77-120">Wyświetla okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b8f77-120">Displays the message box.</span></span> <span data-ttu-id="b8f77-121">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="b8f77-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="b8f77-122">Nie są wyświetlane w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b8f77-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8f77-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b8f77-123">Child Elements</span></span>  
 <span data-ttu-id="b8f77-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="b8f77-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8f77-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b8f77-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b8f77-126">Element</span><span class="sxs-lookup"><span data-stu-id="b8f77-126">Element</span></span>|<span data-ttu-id="b8f77-127">Opis</span><span class="sxs-lookup"><span data-stu-id="b8f77-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b8f77-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8f77-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b8f77-129">Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b8f77-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8f77-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8f77-130">Remarks</span></span>  
 <span data-ttu-id="b8f77-131">Oba atrybuty w  **\<assert >** elementu są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="b8f77-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="b8f77-132">Pola komunikatów można wyłączyć bez określania pliku do zapisywania wiadomości, lub w przypadku określenia pliku do zapisu komunikaty podczas opuszczania komunikatu zaznaczone pola.</span><span class="sxs-lookup"><span data-stu-id="b8f77-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8f77-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="b8f77-133">Example</span></span>  
 <span data-ttu-id="b8f77-134">Poniższy przykład przedstawia sposób Wyłącz wyświetlanie pola komunikatu podczas wywoływania **Debug.Assert** i zapisu wiadomości `c:\log.txt`.</span><span class="sxs-lookup"><span data-stu-id="b8f77-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8f77-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8f77-135">See Also</span></span>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="b8f77-136">Schemat ustawień debugowania i śledzenia</span><span class="sxs-lookup"><span data-stu-id="b8f77-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)