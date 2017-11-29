---
title: "Pojęcia dotyczące serializacji"
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
ms.assetid: e1ff4740-20a1-4c76-a8ad-d857db307054
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 82349611fe127da46bed8998ac883c10c5164cd3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="serialization-concepts"></a><span data-ttu-id="716fb-102">Pojęcia dotyczące serializacji</span><span class="sxs-lookup"><span data-stu-id="716fb-102">Serialization concepts</span></span>
<span data-ttu-id="716fb-103">Dlaczego czy chcesz użyć serializacji?</span><span class="sxs-lookup"><span data-stu-id="716fb-103">Why would you want to use serialization?</span></span> <span data-ttu-id="716fb-104">Dwie najważniejsze przyczyny są, aby zachować stan obiektu na nośniku, dokładna kopia może zostać ponownie utworzone na późniejszym etapie, a aby wysłać obiekt przez wartość z domeny w jednej aplikacji na inny.</span><span class="sxs-lookup"><span data-stu-id="716fb-104">The two most important reasons are to persist the state of an object to a storage medium so an exact copy can be re-created at a later stage, and to send the object by value from one application domain to another.</span></span> <span data-ttu-id="716fb-105">Na przykład serializacji służy do zapisywania stanu sesji w programie ASP.NET i skopiować obiekty do Schowka w formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="716fb-105">For example, serialization is used to save session state in ASP.NET and to copy objects to the Clipboard in Windows Forms.</span></span> <span data-ttu-id="716fb-106">On również używany łącząc do przekazywania obiektów przez wartość z domeny jedną aplikację do innego.</span><span class="sxs-lookup"><span data-stu-id="716fb-106">It is also used by remoting to pass objects by value from one application domain to another.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="persistent-storage"></a><span data-ttu-id="716fb-107">Trwałego magazynu</span><span class="sxs-lookup"><span data-stu-id="716fb-107">Persistent storage</span></span>
<span data-ttu-id="716fb-108">Często jest to niezbędne do przechowywania wartości pól obiektu na dysku, a następnie później, pobrania tych danych.</span><span class="sxs-lookup"><span data-stu-id="716fb-108">It is often necessary to store the value of the fields of an object to disk and then, later, retrieve this data.</span></span> <span data-ttu-id="716fb-109">Jest to łatwa do osiągnięcia bez polegania na serializacji, ta metoda jest często skomplikowane i błąd podatnych na błędy i staje się stopniowo bardziej złożone, gdy zachodzi potrzeba śledzenia hierarchii obiektów.</span><span class="sxs-lookup"><span data-stu-id="716fb-109">Although this is easy to achieve without relying on serialization, this approach is often cumbersome and error prone, and becomes progressively more complex when you need to track a hierarchy of objects.</span></span> <span data-ttu-id="716fb-110">Wyobraź sobie aplikacji dużych firm, który zawiera tysiące obiektów, zapisywania i konieczności pisania kodu do zapisywania i przywracania pola i właściwości do i z dysku dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="716fb-110">Imagine writing a large business application, that contains thousands of objects, and having to write code to save and restore the fields and properties to and from disk for each object.</span></span> <span data-ttu-id="716fb-111">Serializacja oferuje wygodny mechanizm do osiągnięcia tego celu.</span><span class="sxs-lookup"><span data-stu-id="716fb-111">Serialization provides a convenient mechanism for achieving this objective.</span></span>

<span data-ttu-id="716fb-112">Środowisko uruchomieniowe języka wspólnego zarządza, w jaki sposób obiekty są przechowywane w pamięci i udostępnia mechanizm serializacji zautomatyzowanych za pomocą [odbicia](../../../docs/framework/reflection-and-codedom/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="716fb-112">The common language runtime manages how objects are stored in memory and provides an automated serialization mechanism by using [reflection](../../../docs/framework/reflection-and-codedom/reflection.md).</span></span> <span data-ttu-id="716fb-113">Gdy obiekt jest serializowany, nazwa klasy, zestaw i wszystkie składowe danych wystąpienia klasy są zapisywane w pamięci masowej.</span><span class="sxs-lookup"><span data-stu-id="716fb-113">When an object is serialized, the name of the class, the assembly, and all the data members of the class instance are written to storage.</span></span> <span data-ttu-id="716fb-114">Obiekty przechowywania często odwołuje się do innych wystąpień w zmiennych elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="716fb-114">Objects often store references to other instances in member variables.</span></span> <span data-ttu-id="716fb-115">Klasa jest serializowana, mechanizm serializacji śledzi występujących w odwołaniu dla obiektów, już, aby upewnić się, że ten sam obiekt nie jest serializowana więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="716fb-115">When the class is serialized, the serialization engine tracks referenced objects, already serialized, to ensure that the same object is not serialized more than once.</span></span> <span data-ttu-id="716fb-116">Architektura serializacji dołączonym do [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] poprawnie obsługuje wykresy i obiektów odwołania cykliczne automatycznie.</span><span class="sxs-lookup"><span data-stu-id="716fb-116">The serialization architecture provided with the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] correctly handles object graphs and circular references automatically.</span></span> <span data-ttu-id="716fb-117">Jedynym wymaganiem dotyczącymi wykresów obiektów jest, że wszystkie obiekty odwołuje się Zserializowany obiekt musi być oznaczona jako `Serializable` (Aby uzyskać więcej informacji, zobacz [podstawowe serializacji](basic-serialization.md)).</span><span class="sxs-lookup"><span data-stu-id="716fb-117">The only requirement placed on object graphs is that all objects, referenced by the serialized object, must also be marked as `Serializable` (for more information, see [Basic Serialization](basic-serialization.md)).</span></span> <span data-ttu-id="716fb-118">Jeśli nie jest to wykonywane, zostanie zwrócony wyjątek serializator próba serializacji obiektu nieoznaczone.</span><span class="sxs-lookup"><span data-stu-id="716fb-118">If this is not done, an exception will be thrown when the serializer attempts to serialize the unmarked object.</span></span>

<span data-ttu-id="716fb-119">Podczas deserializacji jest klasa serializacji, zostaje odtworzone klasy i automatycznie zostaną przywrócone wartości wszystkich elementów członkowskich danych.</span><span class="sxs-lookup"><span data-stu-id="716fb-119">When the serialized class is deserialized, the class is recreated and the values of all the data members are automatically restored.</span></span>

## <a name="marshal-by-value"></a><span data-ttu-id="716fb-120">Kierowanie przez wartość</span><span class="sxs-lookup"><span data-stu-id="716fb-120">Marshal by value</span></span>
<span data-ttu-id="716fb-121">Obiekty są prawidłowe tylko w domenie aplikacji, w którym zostały utworzone.</span><span class="sxs-lookup"><span data-stu-id="716fb-121">Objects are valid only in the application domain where they are created.</span></span> <span data-ttu-id="716fb-122">Każda próba przekazania obiektu jako parametr lub przywrócić go w związku z tym zakończy się niepowodzeniem, chyba że obiekt jest pochodną `MarshalByRefObject` lub jest oznaczony jako `Serializable`.</span><span class="sxs-lookup"><span data-stu-id="716fb-122">Any attempt to pass the object as a parameter or return it as a result will fail unless the object derives from `MarshalByRefObject` or is marked as `Serializable`.</span></span> <span data-ttu-id="716fb-123">Jeśli obiekt jest oznaczona jako `Serializable`, obiekt zostanie automatycznie serializacji, transportowane z domeny w jednej aplikacji do innych i następnie deserializowany, aby wygenerować dokładne kopię obiektu w drugiej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="716fb-123">If the object is marked as `Serializable`, the object will automatically be serialized, transported from the one application domain to the other, and then deserialized to produce an exact copy of the object in the second application domain.</span></span> <span data-ttu-id="716fb-124">Ten proces jest zwykle określany jako marshal przez wartość.</span><span class="sxs-lookup"><span data-stu-id="716fb-124">This process is typically referred to as marshal-by-value.</span></span>
 
<span data-ttu-id="716fb-125">Gdy obiekt jest pochodną `MarshalByRefObject`, odwołanie do obiektu jest przekazywany z aplikacji jednej domeny do innej domeny, a nie samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="716fb-125">When an object derives from `MarshalByRefObject`, an object reference is passed from one application domain to another, rather than the object itself.</span></span> <span data-ttu-id="716fb-126">Można również oznaczyć obiektu pochodzącego od `MarshalByRefObject` jako `Serializable`.</span><span class="sxs-lookup"><span data-stu-id="716fb-126">You can also mark an object that derives from `MarshalByRefObject` as `Serializable`.</span></span> <span data-ttu-id="716fb-127">Jeśli ten obiekt jest używany z usług zdalnych, element formatujący odpowiedzialny za serializacji, wstępnie z selektorem dwuskładnikowego (`SurrogateSelector`), przejmuje kontrolę nad procesu serializacji i zastępuje wszystkie obiekty pochodne `MarshalByRefObject` z Serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="716fb-127">When this object is used with remoting, the formatter responsible for serialization, which has been preconfigured with a surrogate selector (`SurrogateSelector`), takes control of the serialization process, and replaces all objects derived from `MarshalByRefObject` with a proxy.</span></span> <span data-ttu-id="716fb-128">Bez `SurrogateSelector` w miejscu, architektura serializacji regułom standardowe serializacji opisanego w [kroki w procesie serializacji](steps-in-the-serialization-process.md).</span><span class="sxs-lookup"><span data-stu-id="716fb-128">Without the `SurrogateSelector` in place, the serialization architecture follows the standard serialization rules described in [Steps in the Serialization Process](steps-in-the-serialization-process.md).</span></span>  

## <a name="related-sections"></a><span data-ttu-id="716fb-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="716fb-129">Related sections</span></span>  
 [<span data-ttu-id="716fb-130">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="716fb-130">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
 <span data-ttu-id="716fb-131">Opisuje mechanizm serializacji binarnej, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="716fb-131">Describes the binary serialization mechanism that is included with the common language runtime.</span></span>  
  
 [<span data-ttu-id="716fb-132">Obiekty zdalnego</span><span class="sxs-lookup"><span data-stu-id="716fb-132">Remote Objects</span></span>](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58)  
 <span data-ttu-id="716fb-133">Opis różnych metod komunikacji dostępnych w programie .NET Framework do komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="716fb-133">Describes the various communications methods available in the .NET Framework for remote communications.</span></span>  
  
 [<span data-ttu-id="716fb-134">XML i serializacji SOAP</span><span class="sxs-lookup"><span data-stu-id="716fb-134">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 <span data-ttu-id="716fb-135">Opisuje mechanizm serializacji XML i protokołu SOAP, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="716fb-135">Describes the XML and SOAP serialization mechanism that is included with the common language runtime.</span></span>