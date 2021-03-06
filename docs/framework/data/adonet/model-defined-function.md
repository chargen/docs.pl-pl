---
title: funkcja zdefiniowana przez model
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 5c91c221735f3385370ec2fbb532d5b3c5dd2898
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="model-defined-function"></a>funkcja zdefiniowana przez model
A *funkcja zdefiniowana przez model* jest funkcją, która jest zdefiniowana w modelu koncepcyjnym. Treść funkcji zdefiniowanej przez model jest wyrażony w [SQL jednostki](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), dzięki czemu funkcję wyrażane niezależnie od zasady lub języki obsługiwane w źródle danych.  
  
 Definicji dla funkcji zdefiniowanej przez model zawiera następujące informacje:  
  
-   Nazwa funkcji. (Wymagane)  
  
-   Typ zwracanej wartości. (opcjonalnie)  
  
    > [!NOTE]
    >  Jeśli żaden typ zwracany jest określony, wartość zwracana jest nieważne.  
  
-   Informacje o parametrach. (opcjonalnie)  
  
-   [SQL jednostki](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) wyrażenie definiujące treści funkcji.  
  
 Należy pamiętać, że funkcje zdefiniowane przez model nie obsługują parametrów wyjściowych. To ograniczenie jest w miejscu, dzięki czemu mogą być składane funkcje zdefiniowane przez model.  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`.  
  
 ![Modelu z Data opublikowania](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujący plik CSDL definiuje funkcję w modelu koncepcyjnym zwracające liczbę lat od wystąpienia `Book` (na powyższym diagramie) został opublikowany.  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [Model danych jednostki: Typy danych pierwotnych](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
