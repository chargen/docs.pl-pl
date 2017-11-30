---
title: Zabezpieczenia formularzy systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5cdac074b873d3a627e6971d440fdd1f98952b08
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="windows-forms-security"></a>Zabezpieczenia formularzy systemu Windows
Formularze systemu Windows funkcji modelu zabezpieczeń, które jest oparte na kodzie (zabezpieczenia są ustawione przez kod, niezależnie od kodu użytkownika dla poziomów). Jest to oprócz żadnych schematów zabezpieczeń, które mogą być spełnione już na komputerze. Mogą to być te przeglądarki (np. na podstawie strefy zabezpieczeń programu Internet Explorer) lub system operacyjny (na przykład zabezpieczenia oparte na dostęp do poświadczeń systemu Windows NT).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zabezpieczenia w formularzach systemu Windows-omówienie](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 Krótko opisano model zabezpieczeń .NET Framework i podstawowe kroki niezbędne do zapewnienia formularzy systemu Windows w aplikacji to bezpieczne.  
  
 [Plik bezpieczniejsze i dostęp do danych w formularzach systemu Windows](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 Opisuje sposób dostępu do plików i danych w częściowo zaufanym środowisku.  
  
 [Bezpieczniejsze drukowanie w formularzach systemu Windows](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 Opisuje sposób uzyskiwać dostęp do funkcji drukowania w częściowo zaufanym środowisku.  
  
 [Zagadnienia dotyczące zabezpieczeń w formularzach systemu Windows](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 W tym artykule opisano wykonywania manipulowanie okna, korzystanie ze Schowka i wykonywania wywołań do kodu niezarządzanego w częściowo zaufanym środowisku.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [NIB: Domyślnych zasad zabezpieczeń](http://msdn.microsoft.com/en-us/2c086873-0894-4f4d-8f7e-47427c1a3b55)  
 Zawiera listę domyślnych uprawnień w zestawy uprawnień pełnego zaufania, lokalny Intranet i Internet.  
  
 [NIB: Administrowanie zasadami zabezpieczeń Ogólne](http://msdn.microsoft.com/en-us/5121fe35-f0e3-402c-94ab-4f35b0a87b4b)  
 Zawiera informacje dotyczące administrowania zasadami zabezpieczeń .NET Framework i podnoszenia uprawnień.  
  
 [Niebezpieczne uprawnienia i administrowanie zasadami](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md)  
 Omówiono niektóre środowiska.NET Framework uprawnienia, które umożliwia systemu zabezpieczeń obejść.  
  
 [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)  
 Linki do tematów dotyczących najlepszych rozwiązań dotyczących bezpiecznego pisanie kodu dla programu .NET Framework.  
  
 [NIB: Żądanie uprawnień](http://msdn.microsoft.com/en-us/0447c49d-8cba-45e4-862c-ff0b59bebdc2)  
 W tym artykule omówiono korzystanie z atrybutów, aby umożliwić środowiska uruchomieniowego wiedzieć, jakie uprawnienia kodu musi być uruchamiane.  
  
 [Główne pojęcia dotyczące zabezpieczeń](../../../docs/standard/security/key-security-concepts.md)  
 Linki do tematów, które obejmuje podstawowych kwestii zabezpieczeń kodu.  
  
 [Podstawy zabezpieczeń dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md)  
 W tym artykule omówiono podstawowe informacje dotyczące pracy z programu .NET Framework zasady zabezpieczeń w czasie uruchamiania.  
  
 [NIB: Określanie, kiedy należy zmodyfikować zasady zabezpieczeń](http://msdn.microsoft.com/en-us/af749b17-e461-409d-84b9-a3d44789db16)  
 Wyjaśniono sposób określania, kiedy aplikacje muszą różnią się od domyślnych zasad zabezpieczeń.  
  
 [NIB: Wdrażanie zasad zabezpieczeń](http://msdn.microsoft.com/en-us/f936c1e5-033b-4bd9-a3bd-a39ba733a681)  
 W tym artykule omówiono najlepsze sposób wdrażania zmian zasad zabezpieczeń.