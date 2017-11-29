---
title: "Porady: tworzenie klawiszy dostępu za pomocą formantów etykiet formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- Label control [Windows Forms], creating access keys
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- Windows Forms controls, access keys
- UseMnemonic property [Windows Forms], Label control
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4ad6cd99a6399adea2e69cbf844b9f134d2e592e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a><span data-ttu-id="9db8d-102">Porady: tworzenie klawiszy dostępu za pomocą formantów etykiet formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9db8d-102">How to: Create Access Keys with Windows Forms Label Controls</span></span>
<span data-ttu-id="9db8d-103">Formularze systemu Windows <xref:System.Windows.Forms.Label> formanty może służyć do definiowania klucze dostępu dla innych formantów.</span><span class="sxs-lookup"><span data-stu-id="9db8d-103">Windows Forms <xref:System.Windows.Forms.Label> controls can be used to define access keys for other controls.</span></span> <span data-ttu-id="9db8d-104">Po zdefiniowaniu klawisza dostępu w formancie etykiety, użytkownik może nacisnąć klawisz ALT i znak wyznaczyć można przechodzić do formantu, który następuje w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="9db8d-104">When you define an access key in a label control, the user can press the ALT key plus the character you designate to move the focus to the control that follows it in the tab order.</span></span> <span data-ttu-id="9db8d-105">Ponieważ etykiet nie można ustawić fokusu, automatycznie fokusu do następnego formantu w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="9db8d-105">Because labels cannot receive focus, focus automatically moves to the next control in the tab order.</span></span> <span data-ttu-id="9db8d-106">Ten sposób można przypisać klucze dostępu do pola tekstowe, pola kombi, pola listy i siatki danych.</span><span class="sxs-lookup"><span data-stu-id="9db8d-106">Use this technique to assign access keys to text boxes, combo boxes, list boxes, and data grids.</span></span>  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a><span data-ttu-id="9db8d-107">Aby przypisać klucz dostępu do formantu z etykietą</span><span class="sxs-lookup"><span data-stu-id="9db8d-107">To assign an access key to a control with a label</span></span>  
  
1.  <span data-ttu-id="9db8d-108">Najpierw rysowania etykiety, a następnie narysuj inny formant.</span><span class="sxs-lookup"><span data-stu-id="9db8d-108">Draw the label first, and then draw the other control.</span></span>  
  
     <span data-ttu-id="9db8d-109">—lub—</span><span class="sxs-lookup"><span data-stu-id="9db8d-109">-or-</span></span>  
  
     <span data-ttu-id="9db8d-110">Narysować kontrolki w dowolnej kolejności i ustawić <xref:System.Windows.Forms.Control.TabIndex%2A> właściwość etykiety do jednego mniej niż inny formant.</span><span class="sxs-lookup"><span data-stu-id="9db8d-110">Draw the controls in any order and set the <xref:System.Windows.Forms.Control.TabIndex%2A> property of the label to one less than the other control.</span></span>  
  
2.  <span data-ttu-id="9db8d-111">Ustaw wartość etykiety <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="9db8d-111">Set the label's <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="9db8d-112">Użyj ampersand (&) na etykiecie <xref:System.Windows.Forms.Label.Text%2A> właściwość do przypisania klucz dostępu dla etykiety.</span><span class="sxs-lookup"><span data-stu-id="9db8d-112">Use an ampersand (&) in the label's <xref:System.Windows.Forms.Label.Text%2A> property to assign the access key for the label.</span></span> <span data-ttu-id="9db8d-113">Aby uzyskać więcej informacji, zobacz [tworzenie dostępu do kluczy dla formantów formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="9db8d-113">For more information, see [Creating Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9db8d-114">Możesz wyświetlić takie znaki w formancie etykiety, a nie ich używać do tworzenia kluczy dostępu.</span><span class="sxs-lookup"><span data-stu-id="9db8d-114">You may want to display ampersands in a label control, rather than use them to create access keys.</span></span> <span data-ttu-id="9db8d-115">Może to nastąpić, jeśli powiązanie formantu etykiety do pola w zestawie rekordów, w którym dane obejmują takie znaki.</span><span class="sxs-lookup"><span data-stu-id="9db8d-115">This may occur if you bind a label control to a field in a recordset where the data includes ampersands.</span></span> <span data-ttu-id="9db8d-116">Aby wyświetlić takie znaki w formancie etykiety, ustaw <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwości `false`.</span><span class="sxs-lookup"><span data-stu-id="9db8d-116">To display ampersands in a label control, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `false`.</span></span> <span data-ttu-id="9db8d-117">Jeśli chcesz wyświetlić ampersandu i mają klucz dostępu, należy ustawić <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwości `true` i wskazywać klucza dostępu z jednego handlowego "i" (&) i handlowego "i", aby wyświetlić dwa znakami.</span><span class="sxs-lookup"><span data-stu-id="9db8d-117">If you wish to display ampersands and also have an access key, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true` and indicate the access key with one ampersand (&) and the ampersand to display with two ampersands.</span></span>  
  
    ```vb  
    Label1.UseMnemonic = True  
    Label1.Text = "&Print"  
    Label2.UseMnemonic = True  
    Label2.Text = "&Copy && Paste"  
    ```  
  
    ```csharp  
    label1.UseMnemonic = true;  
    label1.Text = "&Print";  
    label2.UseMnemonic = true;  
    label2.Text = "&Copy && Paste";  
    ```  
  
    ```cpp  
    label1->UseMnemonic = true;  
    label1->Text = "&Print";  
    label2->UseMnemonic = true;  
    label2->Text = "&Copy && Paste";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9db8d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9db8d-118">See Also</span></span>  
 [<span data-ttu-id="9db8d-119">Porady: rozmiar formantu etykiety pasujący do jego zawartości formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9db8d-119">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 [<span data-ttu-id="9db8d-120">Informacje o formancie etykiety</span><span class="sxs-lookup"><span data-stu-id="9db8d-120">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [<span data-ttu-id="9db8d-121">Label — formant</span><span class="sxs-lookup"><span data-stu-id="9db8d-121">Label Control</span></span>](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)