---
title: '&lt;Element xmlSerializer&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: f80d41701f3e0d62e89a056701bde6fd69ef9ecb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltxmlserializergt-element"></a>&lt;Element xmlSerializer&gt; — Element
Określa, czy dodatkowe wyboru postęp <xref:System.Xml.Serialization.XmlSerializer> jest wykonywane.  
  
 \<Konfiguracja >  
\<System.XML.serialization >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true"|"false" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**checkDeserializeAdvances**|Określa, czy postęp <xref:System.Xml.Serialization.XmlSerializer> jest zaznaczone. Atrybut "prawda" lub "false". Wartość domyślna to "true".|  
|**useLegacySerializationGeneration**|Określa, czy <xref:System.Xml.Serialization.XmlSerializer> używa Generowanie starszego serializacji, generująca zestawy zapis do PLiku kodu C# i zestawiania do zestawu. Wartość domyślna to **false**.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)|Zawiera ustawienia konfiguracji dla <xref:System.Xml.Serialization.XmlSerializer> i <xref:System.Xml.Serialization.XmlSchemaImporter> klasy.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie <xref:System.Xml.Serialization.XmlSerializer> zapewnia dodatkową warstwę zabezpieczeń przed potencjalnym atakom typu odmowa usługi podczas deserializacji niezaufanych danych. Robi to za pomocą próby wykrycia podczas deserializacji w pętli nieskończonej. W przypadku wykrycia takim stanie, jest zwracany wyjątek z następującym komunikatem: "Błąd wewnętrzny: Deserializacja nie powiodła się z przechodzeniem do odpowiedniego strumienia do."  
  
 Odbieranie ten komunikat nie musi oznaczać, że typu "odmowa usługi" jest w toku. W niektórych sytuacjach szczególnych mechanizm wykrywania pętli nieskończonej tworzy fałszywego ostrzeżenia i wyjątku wiarygodnego wiadomości przychodzącej. Jeśli okaże się, że w szczególności aplikacji istotnych wiadomości są odrzucane przez ten dodatkową warstwę ochrony, należy ustawić **checkDeserializeAdvances** atrybutu na "false".  
  
## <a name="example"></a>Przykład  
 Poniższy kod przykładzie **checkDeserializeAdvances** atrybutu na "false".  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [Serializacja XML i SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)
