---
title: Uporządkowane pobierania węzła według indeksu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5412c90f-2703-4aa8-a9c4-1b8a35183c37
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3cfa371394e76aab832c3dd4b065eb811413322
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ordered-node-retrieval-by-index"></a>Uporządkowane pobierania węzła według indeksu
Sieci World Wide Web konsorcjum W3C XML modelu DOM (Document Object) opisano również wstawienia, który ma możliwość obsługi uporządkowaną listę węzłów, w przeciwieństwie do zestawu nieuporządkowaną obsługiwane przez **XmlNamedNodeMap**. Wstawienia programu Microsoft .NET Framework jest nazywany **XmlNodeList**. Metody i właściwości, które zwracają **XmlNodeList** są:  
  
-   XmlNode.ChildNodes  
  
-   XmlDocument.GetElementsByTagName  
  
-   XmlElement.GetElementsByTagName  
  
-   XmlNode.SelectNodes  
  
 **XmlNodeList** ma **liczba** właściwość, która może być użyty do zapisu pętli w celu wykonania iteracji w węzłach **XmlNodeList**, jak pokazano w poniższym przykładzie kodu:  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
   doc.Load("books.xml")  
  
    ' Retrieve all book titles.  
    Dim root as XmlElement = doc.DocumentElement  
    Dim elemList as XmlNodeList = root.GetElementsByTagName("title")  
    Dim i as integer  
    for i=0  to elemList.Count-1  
        ' Display all book titles in the Node List.  
        Console.WriteLine(elemList.ItemOf(i).InnerXml)  
    next  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
// Retrieve all book titles.  
XmlElement root = doc.DocumentElement;  
XmlNodeList elemList = root.GetElementsByTagName("title");  
for (int i=0; i < elemList.Count; i++)  
{     
   // Display all book titles in the Node List.  
   Console.WriteLine(elemList[i].InnerXml);  
}   
```  
  
 Oprócz **liczba** właściwości, istnieje **GetEnumerator** metoda zapewniająca, `foreach` styl iteracji w kolekcji węzły w **XmlNodeList**. W poniższym przykładzie pokazano sposób użycia `foreach` instrukcji.  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("books.xml")  
  
' Get book titles.  
Dim root As XmlElement = doc.DocumentElement  
Dim elemList As XmlNodeList = root.GetElementsByTagName("title")  
Dim ienum As IEnumerator = elemList.GetEnumerator()  
' Loop over the XmlNodeList using the enumerator ienum          
While ienum.MoveNext()  
    ' Display the book title.  
    Dim title As XmlNode = CType(ienum.Current, XmlNode)  
    Console.WriteLine(title.InnerText)  
End While  
```  
  
```csharp  
{  
     XmlDocument doc = new XmlDocument();  
     doc.Load("books.xml");  
  
     // Get book titles.  
     XmlElement root = doc.DocumentElement;  
     XmlNodeList elemList = root.GetElementsByTagName("title");  
     IEnumerator ienum = elemList.GetEnumerator();    
     // Loop over the XmlNodeList using the enumerator ienum          
     while (ienum.MoveNext())  
     {  
          // Display the book title.  
           XmlNode title = (XmlNode) ienum.Current;  
           Console.WriteLine(title.InnerText);  
     }  
  }  
```  
  
 Aby uzyskać więcej informacji na temat metod i właściwości dostępnych na **XmlNodeList**, zobacz <xref:System.Xml.XmlNodeList>.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
