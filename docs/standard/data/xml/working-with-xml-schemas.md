---
title: Praca z schematy XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83fddd00f44b184fa066f6c47b90b01fac7ef7bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-xml-schemas"></a>Praca z schematy XML
Aby zdefiniować strukturę dokumentu XML, a także jej relacje element, typy danych i ograniczeń zawartości, możesz użyć definicja typu dokumentu (DTD) ani schematu (XSD) języka definicji schematu XML. Mimo że dokument XML jest uznawany za poprawnie sformułowanym go spełnia wszystkie wymagania syntaktycznych zdefiniowane przez zalecenie sieci World Wide Web konsorcjum W3C Extensible Markup Language (XML) 1.0, nie jest traktowane prawidłowy chyba że oba jest poprawnie sformułowany i jest zgodna z ograniczeń zdefiniowanych przez jego definicja DTD lub schemat. W związku z tym mimo że wszystkich ważnych dokumentów XML są poprawnie sformułowany, nie wszystkie poprawnie sformułowanym dokumentów XML są prawidłowe.  
  
 Aby uzyskać więcej informacji na temat formatu XML, zobacz [W3C XML 1.0 zalecenie](https://www.w3.org/TR/REC-xml/). Aby uzyskać więcej informacji na temat schematu XML, zobacz [W3C XML schematu część 1: zalecenie struktury](https://www.w3.org/TR/xmlschema-1/) i [W3C XML schematu część 2: zalecenie typy danych](https://www.w3.org/TR/xmlschema-2/) zalecenia.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Model SOM (XML Schema Object Model)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 W tym artykule omówiono w modelu obiektu schematu (SOM) <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw, która udostępnia zestaw klas, który umożliwia odczytanie schematu definicji schematu języka (XSD) z pliku lub programowo tworzenie schematu w pamięci.  
  
 [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 W tym artykule omówiono <xref:System.Xml.Schema.XmlSchemaSet> klasy czyli pamięci podręcznej, gdzie schematów XSD mogą być przechowywane i sprawdzania poprawności.  
  
 [Weryfikacja oparta na wypchnięciach przy użyciu klasy XmlSchemaValidator](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 W tym artykule omówiono <xref:System.Xml.Schema.XmlSchemaValidator> klasy, która udostępnia mechanizm wydajne, wysokiej wydajności, aby sprawdzić poprawność danych XML względem schematów XSD w sposób wypychania.  
  
 [Wnioskowanie schematu XML](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 W tym artykule omówiono sposób użycia <xref:System.Xml.Schema.XmlSchemaInference> klasy na potrzeby wnioskowania dotyczącego schematu XSD ze struktury dokumentu XML.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Weryfikowanie dokumentu XML w modelu DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 W tym artykule omówiono sposób sprawdzania poprawności kodu XML w modelu DOM (Document Object). Sprawdzanie poprawności kodu XML, jak jest załadowane do modelu DOM lub sprawdzić wcześniej niezweryfikowanych dokumentu XML w modelu DOM.  
  
 [Weryfikacja schematu przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 W tym artykule omówiono sposób sprawdzania poprawności XML jest przejście i edytować za pomocą <xref:System.Xml.XPath.XPathNavigator> klasy.
