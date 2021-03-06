---
title: Procedury w Visual Basic
ms.date: 04/28/2017
helpviewer_keywords:
- procedures [Visual Basic], structured code
- Visual Basic code, procedures
- procedures [Visual Basic], types of
- structured code [Visual Basic], procedures
- procedures
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
ms.openlocfilehash: a4a168fd1fad75f5038044d49886782f391ceb1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="procedures-in-visual-basic"></a>Procedury w Visual Basic
A *procedury* jest blok instrukcji języka Visual Basic ujęty w instrukcji deklaracji (`Function`, `Sub`, `Operator`, `Get`, `Set`) i odpowiadający mu `End` deklaracji. Wszystkie instrukcje wykonywalne w języku Visual Basic musi znajdować się w niektórych procedury.  
  
## <a name="calling-a-procedure"></a>Wywołanie procedury  
 Wywołuje procedurę w innym miejscu w kodzie. Jest to nazywane *wywołania procedury*. Po zakończeniu procedury uruchomiona, zwraca sterowania do kodu, która wywołana, i nosi nazwę *wywołanie kodu*. Kod wywołujący jest instrukcja lub wyrażenie w instrukcji, określa nazwę procedury i przekazuje sterowanie do niego.  
  
## <a name="returning-from-a-procedure"></a>Zwracanie z procedury  
 Po zakończeniu procedury zwraca do kontroli do wywołującego kodu. Aby to zrobić, można użyć [zwracać instrukcji](../../../../visual-basic/language-reference/statements/return-statement.md), odpowiednie [instrukcji Zakończ](../../../../visual-basic/language-reference/statements/exit-statement.md) instrukcji dla procedury lub procedury [zakończenia \<— słowo kluczowe > instrukcji](../../../../visual-basic/language-reference/statements/end-keyword-statement.md)instrukcji. Formant następnie przekazuje do wywołującego kod następujący punkt wywołaniu procedury.  
  
-   Z `Return` instrukcji sterowania zwraca natychmiast do wywołującego kodu. Poniższe instrukcje `Return` instrukcja nie jest uruchomiony. Może mieć więcej niż jeden `Return` instrukcji w tej samej procedury.  
  
-   Z `Exit Sub` lub `Exit Function` instrukcji sterowania zwraca natychmiast do wywołującego kodu. Poniższe instrukcje `Exit` instrukcja nie jest uruchomiony. Może mieć więcej niż jeden `Exit` można łączyć instrukcji w tej samej procedury, a `Return` i `Exit` instrukcje w tej samej procedury.  
  
-   Jeśli nie ma procedury `Return` lub `Exit` instrukcji zawiera z `End Sub` lub `End Function`, `End Get`, lub `End Set` instrukcji następującej po ostatniej instrukcji w treści procedury. `End` Instrukcja zwraca kontroli natychmiast do wywołującego kodu. Może mieć tylko jeden `End` instrukcji procedury.  
  
## <a name="parameters-and-arguments"></a>Parametry i argumenty  
 W większości przypadków musi działać na różnych danych zawsze należy wywołać procedurę. Informacje te można przekazać do procedury jako część wywołania procedury. Definiuje procedurę zero lub więcej *parametry*, każdy z których reprezentuje wartość oczekuje, że do przekazywania do niej. Odpowiadający każdego parametru w definicji procedura jest *argument* w wywołaniu procedury. Argument reprezentuje wartość, którą można przekazać do odpowiadającego mu parametru w wywołaniu procedury danego.  
  
## <a name="types-of-procedures"></a>Rodzaje procedur  
 Visual Basic korzysta kilka typów procedur:  
  
-   [Procedury Sub](./sub-procedures.md) wykonywać działania, ale nie zwracać wartości do wywołującego kodu.  
  
-   Procedury obsługi zdarzeń są `Sub` procedur, które są wykonywane w odpowiedzi na zdarzenie zgłaszane przez akcję użytkownika lub przez wystąpienia w programie.  
  
-   [Procedury funkcji](./function-procedures.md) zwracają wartość do wywołującego kodu. Mogą one wykonywać inne akcje przed zwróceniem.

    Niektóre funkcje napisany w C# powrotu *odwołania do wartości zwracanej*. Wywołań funkcji można zmodyfikować zwracanej wartości, a ta modyfikacja ta jest uwzględniana w stanie wywołany obiekt. Począwszy od 2017 Visual Basic, kod Visual Basic, jaką może wykorzystać zwracanych wartości odwołania, ale go nie może zwracać wartość przez odwołanie. Aby uzyskać więcej informacji, zobacz [odwołanie zwracane wartości](ref-return-values.md).
  
-   [Procedury własności](./property-procedures.md) powrócić i przypisz wartości właściwości do obiektów lub modułów.  
  
-   [Procedury operatorów](./operator-procedures.md) definiują zachowania standardowe operatora, gdy jeden lub oba argumenty operacji jest nowo zdefiniowanej klasy lub struktury.  
  
-   [Procedury ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) zdefiniować co najmniej jeden *parametry typu* oprócz ich parametry normalnej, więc kod wywołujący może przekazać określonych danych typów czasu nawiązuje połączenie.  
  
## <a name="procedures-and-structured-code"></a>Procedury i węzeł strukturalny  
 Każdy wiersz kodu wykonywalnego w aplikacji musi znajdować się wewnątrz niektóre procedury, takich jak `Main`, `calculate`, lub `Button1_Click`. W przypadku bardzo dużych procedur można podzielić na mniejsze, aplikacja jest bardziej czytelne.  
  
 Procedury są przydatne w przypadku wykonywania wielokrotnego lub udostępnionego zadania, takie jak często używanych obliczeń, manipulowanie tekstu i kontrolowania i operacji w bazie danych. Procedurę można wywołać z wielu różnych miejscach w kodzie, dzięki czemu można użyć procedury jako bloków konstrukcyjnych dla aplikacji.  
  
 Struktury kodu za pomocą procedury zapewnia następujące korzyści:  
  
-   Procedury umożliwiają Podziel programy na osobne jednostki logiczne. Można łatwo debugowania oddzielnych zespołów więcej niż można debugować całego programu bez procedur.  
  
-   Po należy opracować procedury do użycia w jednym programie, można używać ich w innych programów, często z żadnych modyfikacji. Dzięki temu można uniknąć zduplikowania kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: tworzenie procedury](./how-to-create-a-procedure.md)  
 [Sub, procedury](./sub-procedures.md)  
 [Procedury funkcji](./function-procedures.md)  
 [Procedury właściwości](./property-procedures.md)  
 [Procedury operatorów](./operator-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Procedury rekursywne](./recursive-procedures.md)  
 [Przeciążanie procedury](./procedure-overloading.md)  
 [Procedury ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
