---
title: "Porady: zapisywanie tekstu do plików w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cfdae490a7d78e44f230e22f8431d5ee91461c22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a>Porady: zapisywanie tekstu do plików w Visual Basic
<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metody umożliwia zapisywanie tekstu do plików. Jeśli określony plik nie istnieje, jest tworzony.  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-write-text-to-a-file"></a>Pisanie do pliku  
  
-   Użyj `WriteAllText` metodę zapisywanie tekstu do pliku, określając plików i tekst, który ma zostać zapisany. W tym przykładzie zapisuje linię `"This is new text."` pliku o nazwie `test.txt`, dodanie go do istniejącego tekstu w pliku.  
  
     [!code-vb[VbFileIOWrite#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_1.vb)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a>Do zapisu w pliku serii ciągów  
  
-   Pętli kolekcji ciągów. Użyj `WriteAllText` metoda próbę zapisania tekstu do pliku, określając pliku docelowego i ciąg do dodania i ustawienie `append` do `True`.  
  
     W tym przykładzie zapisuje nazwy plików w `Documents and Settings` do katalogu `FileList.txt`, wstawianie karetki zwracać między nimi w celu zwiększenia czytelności.  
  
     [!code-vb[VbFileIOWrite#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_2.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `File`wskazuje na ścieżkę, która nie istnieje (<xref:System.IO.FileNotFoundException> lub <xref:System.IO.DirectoryNotFoundException>).  
  
-   Plik jest używany przez inny proces lub błąd We/Wy (<xref:System.IO.IOException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).  
  
-   Nazwę pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).  
  
-   Dysk jest pełny i wywołanie `WriteAllText` nie powiedzie się (<xref:System.IO.IOException>).  
  
 Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek, ze względu na niewystarczające uprawnienia. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](https://msdn.microsoft.com/library/33tceax8).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 [Porady: Odczyt z plików tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)