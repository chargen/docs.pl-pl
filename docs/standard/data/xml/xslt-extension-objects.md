---
title: Obiekty rozszerzenia XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69fcd4bd8426bb349c090fc52f7a1f1a262378ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xslt-extension-objects"></a>Obiekty rozszerzenia XSLT
Obiekty rozszerzenia są używane do rozszerzyć funkcjonalność arkuszy stylów. Obiekty rozszerzenia są obsługiwane przez <xref:System.Xml.Xsl.XsltArgumentList> klasy.  
  
 Poniżej przedstawiono zalety korzystania z obiektu rozszerzenia, a nie osadzony skrypt:  
  
-   Zapewnia lepszą hermetyzacji i ponowne użycie klasy.  
  
-   Umożliwia arkusze stylów mniejsze i łatwiejsze do utrzymania.  
  
 Obiekty rozszerzenia XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektem rozszerzenia o tej godzinie.  
  
> [!NOTE]
>  Zestaw uprawnień FullTrust jest wymagany do wywołania <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) i [NIB: nazwane zestawy uprawnień](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).  
  
 Typy danych zwracane z obiektów rozszerzeń są jedną z czterech podstawowych XPath typy danych `number`, `string`, `Boolean`, i `node set`.  
  
 Wszystkie metody, która jest zdefiniowana z `params` — słowo kluczowe, umożliwiający nieokreślony liczba parametrów nie jest obsługiwana przez <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Arkusze stylów XSLT wykorzystujące dowolnej metody zdefiniowane z `params` — słowo kluczowe nie będą działać poprawnie. Aby uzyskać więcej informacji, zobacz [params](~/docs/csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>Aby użyć obiektu rozszerzenia XSLT  
  
1.  Utwórz <xref:System.Xml.Xsl.XsltArgumentList> obiektu i dodać za pomocą obiektu rozszerzenia <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody.  
  
2.  Wywołanie obiektu rozszerzenia z arkusza stylów.  
  
3.  Przekaż <xref:System.Xml.Xsl.XsltArgumentList> do obiektu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [Zagadnienia dotyczące bezpieczeństwa danych XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md)
