---
title: '&lt;Identyfikator URI&gt; elementu (ustawienia identyfikatorów Uri)'
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 05b2fb4255643f657f37012ec51a1b29ed68095d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="lturigt-element-uri-settings"></a>&lt;Identyfikator URI&gt; elementu (ustawienia identyfikatorów Uri)
Zawiera ustawienia, które określają, jak programu .NET Framework obsługuje adresy URL wyrazić przy użyciu uniform resource identifier (URI).  
  
## <a name="schema-hierarchy"></a>Schemat hierarchii  
 [\<Konfiguracja > — Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Identyfikator URI >](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[IDN](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|Określa, czy międzynarodowych nazw domen (IDN) podczas analizowania została zastosowana do nazw domen.|  
|[iriParsing](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|Określa identyfikator zasobu międzynarodowych (IRI) podczas analizowania odnosi się do <xref:System.Uri> i określa, czy powinny być stosowane IRI podczas analizowania reguły.|  
|[schemeSettings](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|Określa sposób <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Konfiguracja](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Zawiera ustawienia dla wszystkich obszarów nazw.|  
  
## <a name="remarks"></a>Uwagi  
 `uri` Element zawiera ustawienia dla członków <xref:System.Uri> klasy używane przez klasy w <xref:System.Net> przestrzeni nazw. Ustawienia skonfigurować obsługę IRI i IDN.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono konfiguracji używane przez <xref:System.Uri> klasy do obsługi analizowania IRI i nazwy IDN. Przykład także czyści wszystkie ustawienia systemu, a następnie dodaje obsługę nie anulowanie procent, kodowane ścieżki ograniczniki schemat http.  
  
### <a name="code"></a>Kod  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
