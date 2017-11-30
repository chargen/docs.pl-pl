---
title: "Modyfikowanie węzłów, zawartość i wartości w dokumencie XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 761773e0-db72-4986-b9f5-a522213d8397
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 00b923edb95852d9434db1b393df68fd9d0c8a1a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-nodes-content-and-values-in-an-xml-document"></a>Modyfikowanie węzłów, zawartość i wartości w dokumencie XML
Istnieje wiele sposobów, można zmodyfikować węzłów i zawartości w dokumencie. Można:  
  
-   Zmień wartość węzłów za pomocą <xref:System.Xml.XmlNode.Value%2A> właściwości.  
  
-   Zmodyfikuj cały zestaw węzłów przez zamianę węzły nowe węzły. Jest to realizowane przy użyciu <xref:System.Xml.XmlNode.InnerXml%2A> właściwości.  
  
-   Zamień istniejące węzły nowe węzły za pomocą <xref:System.Xml.XmlNode.RemoveChild%2A> metody.  
  
-   Dodaj dodatkowe znaki do węzłów, które dziedziczą z <xref:System.Xml.XmlCharacterData> przy użyciu <xref:System.Xml.XmlCharacterData.AppendData%2A>, <xref:System.Xml.XmlCharacterData.InsertData%2A>, lub <xref:System.Xml.XmlCharacterData.ReplaceData%2A> metody.  
  
-   Zmiany zawartości przez usunięcie zakres znaków za pomocą <xref:System.Xml.XmlCharacterData.DeleteData%2A> metody na typy węzłów, które dziedziczą z <xref:System.Xml.XmlCharacterData>.  
  
 Prosta technika w przypadku zmiany wartości węzła jest użycie `node.Value = "new value";`. W poniższej tabeli wymieniono typy węzłów, które działa ten pojedynczy wiersz kodu na i dokładnie danych dla tego typu węzła zostanie zmieniona.  
  
|Typ węzła|Zmienione dane|  
|---------------|------------------|  
|Atrybut|Wartość atrybutu.|  
|CDATASection|Zawartość CDATASection.|  
|Komentarz|Zawartość komentarza.|  
|ProcessingInstruction|Zawartość, z wyłączeniem obiektu docelowego.|  
|Tekst|Zawartość tekstu.|  
|XmlDeclaration|Treść deklaracji, z wyłączeniem `<?xml` i `?>` znaczników.|  
|Odstępu|Wartość biały znak. Można ustawić wartość na jedną z czterech rozpoznanym białe znaki XML: miejsca, kartę, Karetki i wysuwu wiersza.|  
|Typu SignificantWhitespace|Wartość znaczący biały znak. Można ustawić wartość na jedną z czterech rozpoznanym białe znaki XML: miejsca, kartę, Karetki i wysuwu wiersza.|  
  
 Dowolny typ węzła nie są wymienione w tabeli nie jest typem prawidłowego węzła do ustawienia wartości. Ustawienie wartości w przypadku dowolnego innego typu węzła zgłasza <xref:System.InvalidOperationException>.  
  
 <xref:System.Xml.XmlNode.InnerXml%2A> Zmiany właściwości kod znaczników węzły podrzędne dla bieżącego węzła. Ustawienie tej właściwości zastępuje węzłów podrzędnych przy użyciu analizowanej zawartości dany ciąg znaków. Analiza odbywa się w bieżącym kontekście przestrzeni nazw. Ponadto <xref:System.Xml.XmlNode.InnerXml%2A> usuwa nadmiarowe przestrzeń nazw — deklaracje. Jako wynik wiele wycinanie i wklejanie operacje nie zwiększają rozmiar dokumentu z deklaracjami nadmiarowe przestrzeni nazw. Na przykład kod, przedstawiający efekt przestrzeni nazw na <xref:System.Xml.XmlNode.InnerXml%2A> operacji, zobacz <xref:System.Xml.XmlDocument.InnerXml%2A> właściwości.  
  
 Korzystając z <xref:System.Xml.XmlCharacterData.ReplaceData%2A> i <xref:System.Xml.XmlNode.RemoveChild%2A> metody, metody zwracają węzła zastąpionego lub usunięty. Ten węzeł może następnie ponownie gdzieś else w XML modelu DOM (Document Object). <xref:System.Xml.XmlCharacterData.ReplaceData%2A> Metoda wykonuje dwie sprawdzanie poprawności w węźle wstawiane do dokumentu. Pierwszy wyboru gwarantuje, że staje się węzeł podrzędny węzła, który może mieć węzłów podrzędnych jego typu. Drugi wyboru zapewnia, że wstawiany węzeł nie jest elementem nadrzędnym węzła, który staje się elementem podrzędnym. Naruszenie jednego z tych warunków zgłasza <xref:System.InvalidOperationException>.  
  
 Jest on prawidłowy, aby dodać lub usunąć element podrzędny tylko do odczytu z węzła, który można edytować. Jednak zgłasza wyjątek próbuje zmodyfikować sam węzeł tylko do odczytu <xref:System.InvalidOperationException>. Na przykład modyfikuje elementy podrzędne <xref:System.Xml.XmlEntityReference> węzła. Elementy podrzędne są tylko do odczytu i nie może być modyfikowany. Próby ich modyfikować zgłasza <xref:System.InvalidOperationException>.  
  
## <a name="see-also"></a>Zobacz też  
 [Modelu obiektu dokumentu XML modelu DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)