---
title: Jak wykryć, czy wtyczka WPF dla Firefox jest zainstalowana
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: ba411d662a8e5b0c4727e23c8d507e8924b6e9e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>Jak wykryć, czy wtyczka WPF dla Firefox jest zainstalowana
Włącza Windows Presentation Foundation (WPF) dodatek plug-in dla przeglądarki Firefox [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] utrata plików XAML, aby uruchomić w przeglądarce Mozilla Firefox. Ten temat zawiera skrypt zapisywane w kodzie HTML i JavaScript, które Administratorzy mogą używać do określenia, czy jest zainstalowany dodatek plug-in dla przeglądarki Firefox WPF.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat Instalowanie, wdrażanie i wykrywanie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], zobacz [Zainstaluj program .NET Framework dla deweloperów](../../../../docs/framework/install/guide-for-developers.md).  
  
## <a name="example"></a>Przykład  
 Gdy [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] jest zainstalowane, komputer kliencki jest skonfigurowany z użyciem WPF dodatek plug-in dla przeglądarki Firefox. W poniższym przykładzie skryptu wyszukuje WPF dodatek plug-in dla przeglądarki Firefox, a następnie wyświetli komunikat o stanie odpowiednie.  
  
```  
<HTML>  
  
  <HEAD>  
    <TITLE>Test for the WPF plug-in for Firefox</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT type="text/javascript">  
    <!--  
    function OnLoad()  
    {  
  
       // Check for the WPF plug-in for Firefox and report  
       var msg = "The WPF plug-in for Firefox is ";  
       var wpfPlugin = navigator.plugins["Windows Presentation Foundation"];  
       if( wpfPlugin != null ) {  
          document.writeln(msg + " installed.");  
       }  
       else {  
          document.writeln(msg + " not installed. Please install or reinstall the .NET Framework 3.5.");  
       }  
    }  
    -->  
    </SCRIPT>  
  </HEAD>  
  
  <BODY onload="OnLoad()" />  
  
</HTML>  
```  
  
 Jeśli sprawdzanie WPF dodatek plug-in dla przeglądarki Firefox zakończy się pomyślnie, zostanie wyświetlony następujący komunikat o stanie:  
  
 `The WPF plug-in for Firefox is installed.`  
  
 W przeciwnym razie zostanie wyświetlony następujący komunikat stanu:  
  
 `The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`  
  
## <a name="see-also"></a>Zobacz też  
 [Wykrywanie, czy wtyczka .NET Framework 3.0 jest zainstalowana](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)  
 [Wykrywanie, czy wtyczka .NET Framework 3.5 jest zainstalowana](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-5-is-installed.md)  
 [Aplikacje przeglądarek WPF XAML — omówienie](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)
