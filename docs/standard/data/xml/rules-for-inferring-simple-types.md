---
title: Wnioskowanie typów prostych reguł
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 394624d6-4da0-430a-8a88-46efe40f14de
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d265d9247d00a20770d401d62fd1e065e2ef1627
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="rules-for-inferring-simple-types"></a>Wnioskowanie typów prostych reguł
Opisuje sposób <xref:System.Xml.Schema.XmlSchemaInference> klasy wnioskuje typ danych dla atrybutów i elementów.  
  
 <xref:System.Xml.Schema.XmlSchemaInference> Klasy wnioskuje typ danych dla atrybuty i elementy jako typów prostych. W tej sekcji opisano potencjalne typów wykrywany, jak wiele różnych wartości są uzgodniony z pojedynczym typem oraz sposób definiowania schematu `xsi` atrybutów są obsługiwane.  
  
## <a name="inferred-types"></a>Wywnioskowane typów  
 <xref:System.Xml.Schema.XmlSchemaInference> Klasy wnioskuje element i atrybut wartości jako typy proste i zawiera atrybut typu w schemacie wynikowy. Wywnioskowane wszystkie typy są typów prostych. Brak typów podstawowych lub aspekty są dołączane jako część schematu wynikowy.  
  
 Wartości badane są indywidualnie, ponieważ są one napotkał w dokumencie XML. Typ jest wywnioskować wartości w czasie jej się zbadana. Jeśli typem zostało wywnioskowane dla elementu lub atrybutu i napotkano wartość dla elementu lub atrybutu jest niezgodny z aktualnie wnioskowany typ <xref:System.Xml.Schema.XmlSchemaInference> klasy wspiera typu dla każdego zestawu reguł. Reguły te omówiono w sekcji podwyższania poziomu typu w dalszej części tego tematu.  
  
 W poniższej tabeli wymieniono możliwych typów wnioskowany wynikowy schematu.  
  
|Typ prosty|Opis|  
|-----------------|-----------------|  
|wartość logiczna|True, false, 0, 1.|  
|byte|Liczby całkowite z zakresu – 128 do 127.|  
|unsignedByte|Liczby całkowite z zakresu od 0 do 255.|  
|short|Liczby całkowite z zakresu od –32768 do 32767.|  
|unsignedShort|Liczby całkowite z zakresu od 0 do 65535.|  
|int|Liczby całkowite z zakresu od –2147483648 do 2147483647.|  
|unsignedInt|Liczby całkowite z zakresu od 0 do 4294967295.|  
|long|Liczby całkowite z zakresu od –9223372036854775808 do 9223372036854775807.|  
|unsignedLong|Liczby całkowite z zakresu od 0 do 18446744073709551615 są.|  
|integer|Skończoną liczbę cyfr prawdopodobnie jest poprzedzony prefiksem "-".|  
|decimal|Wartości liczbowe, które zawierają z zakresu od 0 do 28 cyfr precyzji.|  
|float|Liczba cyfr dziesiętnych, opcjonalnie, "E" lub "e", po której następuje wartość całkowitą reprezentującą wykładnik. W zakresie-16777216 do 16777216 można wartości dziesiętnych. Wartości wykładnika mogą być w zakresie –149 do 104.<br /><br /> Float umożliwia specjalne wartości, aby reprezentować nieskończoności i wartości innych niż alfanumeryczne. Specjalne wartości typu float to: 0, 0, INF, -INF, NaN.|  
|double|Taki sam jak float, z wyjątkiem wartości dziesiętnych może znajdować się w zakresie-9007199254740992 do 9007199254740992 i wartości wykładnika mogą być w zakresie –1075 do 970.<br /><br /> Umożliwia o podwójnej precyzji dla specjalnych wartości, aby reprezentować nieskończoności i wartości nieliczbowe. Specjalne wartości typu float to: 0, 0, INF, -INF, NaN.|  
|czas trwania|Format czasu trwania W3C.|  
|Data i godzina|Format daty/godziny W3C.|  
|czas|Format czasu W3C.|  
|Data|Ograniczenia są wartości roku od 0001 do 9999.|  
|gYearMonth|Format miesiąc i rok kalendarza gregoriańskiego W3C.|  
|string|Co najmniej jeden znak Unicode.|  
  
## <a name="type-promotion"></a>Promocja typu  
 <xref:System.Xml.Schema.XmlSchemaInference> Klasa sprawdza wartości atrybutu i element co naraz. Jako wartości zostaną napotkane, jest wywnioskowany typ najbardziej restrykcyjne, bez znaku. Jeśli wywnioskowano typu dla elementu lub atrybutu i nową wartość okaże się, że nie jest zgodny z typem obecnie wykrywany, wnioskowany typ jest podwyższany do nowego typu, który dotyczy zarówno obecnie wnioskowany typ, jak i nowa wartość. <xref:System.Xml.Schema.XmlSchemaInference> Klasy należy wziąć pod uwagę poprzednie wartości podczas podwyższania poziomu wnioskowany typ.  
  
 Na przykład wziąć pod uwagę poniższe fragmenty XML z dwa dokumenty XML:  
  
 `<MyElement1 attr1="12" />`  
  
 `<MyElement1 attr1="52344" />`  
  
 Gdy pierwszy `attr1` napotkano wartość typu `attr1` jest wywnioskowany jako `unsignedByte` na podstawie wartości `12`. Gdy drugi `attr1` jest napotkano typ jest podwyższany do `unsignedShort` oparte na aktualnie wnioskowany typ `unsignedByte` i bieżącą wartość `52344`.  
  
 Teraz należy wziąć pod uwagę następujące XML z dwa dokumenty XML:  
  
 `<MyElement2 attr2="0" />`  
  
 `<MyElement2 attr2="true" />`  
  
 Gdy pierwszy `attr2` napotkano wartość typu `attr2` jest wywnioskowany jako `unsignedByte` na podstawie wartości `0`. Gdy drugi `attr2` jest napotkano typ jest podwyższany do `string` oparte na aktualnie wnioskowany typ `unsignedByte` i bieżącą wartość `true` ponieważ <xref:System.Xml.Schema.XmlSchemaInference> klasy należy wziąć pod uwagę poprzednie wartości podczas podwyższania poziomu wywnioskować typu. Jednak jeśli oba wystąpienia `attr2` napotkano w tym samym dokumencie XML, a nie w dwóch różnych dokumentów XML, jak pokazano powyżej, `attr2` czy wywnioskować jako `boolean`.  
  
### <a name="ignored-attributes-from-the-httpwwww3org2001xmlschema-instance-namespace"></a>Ignorowane atrybutów z http://www.w3.org/2001/XMLSchema-instance Namespace  
 Poniżej przedstawiono definiowania schematu atrybutów, które są ignorowane podczas wnioskowania schematu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`xsi:type`|Jeśli element z `xsi:type` określony, `xsi:type` jest ignorowana.|  
|`xsi:nil`|Jeśli element z `xsi:nil` napotkano atrybut, jego deklarację elementu w schemacie wnioskowany ma wartość `nillable="true"`. Element z `xsi:nil` określić dla atrybutu `true` nie może mieć elementów podrzędnych.|  
|`xsi:schemaLocation`|Jeśli `xsi:schemaLocation` jest napotkano jest ignorowana.|  
|`xsi:noNamespaceSchemaLocation`|Jeśli `xsi:noNamespaceSchemaLocation` jest napotkano jest ignorowana.|  
  
## <a name="see-also"></a>Zobacz też  
 [Model SOM (XML Schema Object Model)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 [Wnioskowanie schematów na podstawie dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)  
 [Zasady wnioskowania typów węzłów schematu i struktury](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
