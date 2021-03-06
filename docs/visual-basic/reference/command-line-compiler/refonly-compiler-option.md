---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8f6c15084ac9b1a07aef8a0311edfcc4a93337c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-refonly-visual-basic"></a>-refonly (Visual Basic)

**- Refonly** opcja wskazuje, czy główny wynik kompilacji powinien być zestaw odwołania, zamiast zestawu implementacji. `-refonly` Parametr dyskretnie wyłącza Generowanie plików PDB, jak zestawy odwołań nie może zostać wykonana.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Składnia

```console
-refonly
```

## <a name="remarks"></a>Uwagi

Obsługa języka Visual Basic `-refout` przełącznika, począwszy od wersji 15 ustęp 3.

Zestawy referencyjne są tylko metadane zestawy, które zawierają metadanych, ale żaden kod implementacji. Obejmują one informacje o wszystkim poza typy anonimowe typu i element członkowski. Przyczyna przy użyciu `throw null` jest jednostki (w przeciwieństwie do treści), dzięki czemu PEVerify można uruchamiać i przekazywania (w związku z tym sprawdzanie poprawności kompletności metadanych).

Zestawy referencyjne obejmuje dane poziomu zestawu [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atrybutu. Ten atrybut można określić w źródle (następnie kompilator nie będzie trzeba go syntetyzowania). Z powodu tego atrybutu środowisk uruchomieniowych będzie odmawiał załadowania zestawów odwołań do wykonania (ale nadal może być załadowany w kontekstu reflection-only). Narzędzia, które odzwierciedlać zestawów konieczne upewnij się, że są ładowane zestawów odwołań jako tylko do odbicia. w przeciwnym razie zwraca środowiska uruchomieniowego <xref:System.BadImageFormatException>.

`-refonly` i [ `-refout` ](refout-compiler-option.md) wykluczają się wzajemnie.

## <a name="see-also"></a>Zobacz także
[-refout](refout-compiler-option.md)   
[Kompilator w wierszu polecenia programu Visual Basic](index.md)  
[Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)   
