---
title: Wyrażenia języka C#
ms.date: 03/30/2017
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
ms.openlocfilehash: fa6ffd3b1828db03fd6850d4904aee2339df7f31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="c-expressions"></a>Wyrażenia języka C#
Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# wyrażenia są obsługiwane w systemie Windows Workflow Foundation (WF). Nowych projektów C# przepływu pracy utworzone w [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] kierowanych [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Użyj C# wyrażeń i projekty Visual Basic przepływu pracy, użyj wyrażenia języka Visual Basic. Istniejące [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] projektów przepływu pracy, które używają wyrażeń języka Visual Basic można poddać migracji do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] niezależnie od tego projektu języka i są obsługiwane. Ten temat zawiera omówienie wyrażeń C# w [!INCLUDE[wf1](../../../includes/wf1-md.md)].  
  
## <a name="using-c-expressions-in-workflows"></a>Za pomocą wyrażeń C# w przepływach pracy  
  
-   [Za pomocą wyrażeń C# w Projektancie przepływów pracy](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFDesigner)  
  
    -   [Zapewnienia zgodności](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#BackwardCompat)  
  
-   [Za pomocą wyrażeń C# w przepływach pracy kodu](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)  
  
-   [Za pomocą wyrażeń C# w przepływach pracy XAML](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#XamlWorkflows)  
  
    -   [Skompilowany Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
    -   [Luźne Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
-   [Za pomocą wyrażeń C# w XAMLX usług przepływu pracy](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFServices)  
  
###  <a name="WFDesigner"></a> Za pomocą wyrażeń C# w Projektancie przepływów pracy  
 Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# wyrażenia są obsługiwane w systemie Windows Workflow Foundation (WF). C# przepływu pracy projektów utworzonych w [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] kierowanych [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] używanie języka C# wyrażeń, gdy projekty Visual Basic przepływu pracy za pomocą wyrażeń języka Visual Basic. Aby określić żądaną wyrażenia języka C#, wpisz go w polu **wprowadź wyrażenie C#**. Etykieta jest wyświetlana w oknie właściwości, gdy działanie jest wybrane w projektancie, lub na działanie w Projektancie przepływów pracy. W poniższym przykładzie dwa `WriteLine` działania są zawarte w `Sequence` wewnątrz `NoPersistScope`.  
  
 ![Automatycznie utworzone działania sequence](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")  
  
> [!NOTE]
>  C# wyrażenia są obsługiwane tylko w programie Visual Studio i nie są obsługiwane w Projektancie ponownie hostowanej przepływu pracy. Aby uzyskać więcej informacji o nowych funkcjach WF45 obsługiwane w Projektancie ponownie hostowanej, zobacz [obsługę nowych funkcji Workflow Foundation 4.5 w Projektancie przepływów pracy Rehosted](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).  
  
####  <a name="BackwardCompat"></a> Zapewnienia zgodności  
 Wyrażenia języka Visual Basic w istniejących [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] C# przepływu pracy projektów, które zostały poddane migracji do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] są obsługiwane. Patrząc wyrażeń języka Visual Basic w Projektancie przepływów pracy tekst istniejących wyrażenia języka Visual Basic jest zastępowany **wartość została ustawiona w języku XAML**, chyba że wyrażenie języka Visual Basic jest prawidłowej składni języka C#. Jeśli wyrażenie języka Visual Basic jest prawidłowej składni języka C#, wyrażenie jest wyświetlany. Aby zaktualizować wyrażeń języka Visual Basic na język C#, można je edytować w Projektancie przepływów pracy i określ równoważne wyrażenie języka C#. Zaktualizuj wyrażenia języka Visual Basic, C#, ale po wyrażenia są aktualizowane w Projektancie przepływów pracy są konwertowane na język C# i nie można przywrócić w języku Visual Basic nie jest wymagane.  
  
###  <a name="CodeWorkflows"></a> Za pomocą wyrażeń C# w przepływach pracy kodu  
 C# wyrażenia są obsługiwane w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] przepływów pracy opartych na kodzie, ale przed przepływu pracy można wywołać wyrażenia języka C# musi być kompilowana przy użyciu <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>. Przepływ pracy autorzy mogą używać `CSharpValue` do reprezentowania r wyrażenia i `CSharpReference` do reprezentowania l wartości wyrażenia. W poniższym przykładzie przepływ pracy zostanie utworzona z `Assign` działania i `WriteLine` działań zawartych w `Sequence` działania. A `CSharpReference` określono `To` argument `Assign`i reprezentuje l wartość wyrażenia. A `CSharpValue` określono `Value` argument `Assign`oraz `Text` argument `WriteLine`i reprezentuje r dla tych dwóch wyrażeń.  
  
```csharp  
Variable<int> n = new Variable<int>  
{  
    Name = "n"  
};  
  
Activity wf = new Sequence  
{  
    Variables = { n },  
    Activities =  
    {  
        new Assign<int>  
        {  
            To = new CSharpReference<int>("n"),  
            Value = new CSharpValue<int>("new Random().Next(1, 101)")  
        },  
        new WriteLine  
        {  
            Text = new CSharpValue<string>("\"The number is \" + n")  
        }  
    }  
};  
  
CompileExpressions(wf);  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 Po przepływu pracy jest tworzony, wyrażeń języka C# są kompilowane przez wywołanie metody `CompileExpressions` wywoływana jest metoda pomocnika, a następnie przepływ pracy. Poniżej przedstawiono przykład `CompileExpressions` metody.  
  
```csharp  
static void CompileExpressions(Activity activity)  
{  
    // activityName is the Namespace.Type of the activity that contains the  
    // C# expressions.  
    string activityName = activity.GetType().ToString();  
  
    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name  
    // to represent the new type that represents the compiled expressions.  
    // Take everything after the last . for the type name.  
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";  
    // Take everything before the last . for the namespace.  
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());  
  
    // Create a TextExpressionCompilerSettings.  
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings  
    {  
        Activity = activity,  
        Language = "C#",  
        ActivityName = activityType,  
        ActivityNamespace = activityNamespace,  
        RootNamespace = null,  
        GenerateAsPartialClass = false,  
        AlwaysGenerateSource = true,  
        ForImplementation = false  
    };  
  
    // Compile the C# expression.  
    TextExpressionCompilerResults results =  
        new TextExpressionCompiler(settings).Compile();  
  
    // Any compilation errors are contained in the CompilerMessages.  
    if (results.HasErrors)  
    {  
        throw new Exception("Compilation failed.");  
    }  
  
    // Create an instance of the new compiled expression type.  
    ICompiledExpressionRoot compiledExpressionRoot =  
        Activator.CreateInstance(results.ResultType,  
            new object[] { activity }) as ICompiledExpressionRoot;  
  
    // Attach it to the activity.  
    CompiledExpressionInvoker.SetCompiledExpressionRoot(  
        activity, compiledExpressionRoot);  
}  
```  
  
> [!NOTE]
>  Jeśli nie są kompilowane wyrażeń C#, <xref:System.NotSupportedException> jest generowany, gdy przepływ pracy jest wywoływana z komunikatu podobnego do następującego: `Expression Activity type 'CSharpValue`1" wymaga kompilacji, aby można było uruchomić.  Upewnij się, że przepływ pracy został skompilowany. "  
  
 Jeśli przepływ pracy używa na podstawie niestandardowy kod `DynamicActivity`, następnie pewne zmiany do `CompileExpressions` metody są wymagane, jak pokazano w poniższym przykładzie kodu.  
  
```csharp  
static void CompileExpressions(DynamicActivity dynamicActivity)  
{  
    // activityName is the Namespace.Type of the activity that contains the  
    // C# expressions. For Dynamic Activities this can be retrieved using the  
    // name property , which must be in the form Namespace.Type.  
    string activityName = dynamicActivity.Name;  
  
    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name  
    // to represent the new type that represents the compiled expressions.  
    // Take everything after the last . for the type name.  
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";  
    // Take everything before the last . for the namespace.  
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());  
  
    // Create a TextExpressionCompilerSettings.  
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings  
    {  
        Activity = dynamicActivity,  
        Language = "C#",  
        ActivityName = activityType,  
        ActivityNamespace = activityNamespace,  
        RootNamespace = null,  
        GenerateAsPartialClass = false,  
        AlwaysGenerateSource = true,  
        ForImplementation = true  
    };  
  
    // Compile the C# expression.  
    TextExpressionCompilerResults results =  
        new TextExpressionCompiler(settings).Compile();  
  
    // Any compilation errors are contained in the CompilerMessages.  
    if (results.HasErrors)  
    {  
        throw new Exception("Compilation failed.");  
    }  
  
    // Create an instance of the new compiled expression type.  
    ICompiledExpressionRoot compiledExpressionRoot =  
        Activator.CreateInstance(results.ResultType,  
            new object[] { dynamicActivity }) as ICompiledExpressionRoot;  
  
    // Attach it to the activity.  
    CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation(  
        dynamicActivity, compiledExpressionRoot);  
}  
```  
  
 Istnieje kilka różnic w `CompileExpressions` przeciążenia kompilowany wyrażeń C# w działaniu dynamicznych.  
  
-   Parametr `CompileExpressions` jest `DynamicActivity`.  
  
-   Wpisz nazwę i przestrzeń nazw są pobierane przy użyciu `DynamicActivity.Name` właściwości.  
  
-   `TextExpressionCompilerSettings.ForImplementation` ustawiono `true`.  
  
-   `CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` jest wywoływana zamiast `CompiledExpressionInvoker.SetCompiledExpressionRoot`.  
  
 Aby uzyskać więcej informacji na temat pracy z wyrażeń w kodzie, zobacz [tworzenia przepływów pracy, działań i kod Imperatywne za pomocą wyrażenia](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).  
  
###  <a name="XamlWorkflows"></a> Za pomocą wyrażeń C# w przepływach pracy XAML  
 C# wyrażenia są obsługiwane w przepływach pracy XAML. Skompilowany przepływów pracy XAML są kompilowane na typ i utracić przepływów pracy XAML są załadowane w czasie wykonywania i skompilowany w drzewie działań podczas wykonywania przepływu pracy.  
  
-   [Skompilowany Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
-   [Luźne Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
####  <a name="CompiledXaml"></a> Skompilowany Xaml  
 C# wyrażenia są obsługiwane w skompilowanych przepływów pracy XAML, które są kompilowane do typu w ramach projektu przepływu pracy C# przeznaczonego [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. Domyślny typ przepływu pracy tworzenia w programie Visual Studio jest skompilowany XAML i projektów C# przepływu pracy utworzone w Visual Studio kierowanych [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] za pomocą wyrażeń C#.  
  
####  <a name="LooseXaml"></a> Luźne Xaml  
 C# wyrażenia są obsługiwane w utracić przepływów pracy XAML. Program hosta przepływu pracy, który ładuje i wywołuje utracić XAML przepływu pracy muszą wskazywać [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], i <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> musi mieć ustawioną `true` (wartość domyślna to `false`). Aby ustawić <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> do `true`, Utwórz <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> wystąpienia z jego <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> ustawioną właściwość `true`i przekaż go jako parametr <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>. Jeśli `CompileExpressions` nie jest ustawiony na `true`, <xref:System.NotSupportedException> zostanie wygenerowany komunikat podobny do następującego: `Expression Activity type 'CSharpValue`1" wymaga kompilacji, aby można było uruchomić.  Upewnij się, że przepływ pracy został skompilowany. "  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 Aby uzyskać więcej informacji na temat pracy z przepływów pracy XAML, zobacz [serializacji przepływów pracy i działań do i z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
###  <a name="WFServices"></a> Za pomocą wyrażeń C# w XAMLX usług przepływu pracy  
 C# wyrażenia są obsługiwane w XAMLX usług przepływu pracy. Gdy nie są wymagane żadne dodatkowe czynności, a następnie usługi przepływu pracy znajduje się w usługach IIS lub WAS, ale własnym znajduje się usługa XAML przepływu pracy, muszą być skompilowane wyrażenia języka C#. Aby skompilować wyrażeń C# własnym hostowanej usługi przepływu pracy XAMLX, najpierw załadować pliku XAMLX do `WorkflowService`, a następnie przekazać `Body` z `WorkflowService` do `CompileExpressions` metody opisane w poprzedniej [przy użyciu języka C# wyrażenia w przepływach pracy kodu](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) sekcji. W poniższym przykładzie jest ładowany XAMLX usługi przepływu pracy, są kompilowane wyrażeń C#, a następnie usługi przepływu pracy jest otwarty i czeka na żądania.  
  
```csharp  
// Load the XAMLX workflow service.  
WorkflowService workflow1 =  
    (WorkflowService)XamlServices.Load(xamlxPath);  
  
// Compile the C# expressions in the workflow by passing the Body to CompileExpressions.  
CompileExpressions(workflow1.Body);  
  
// Initialize the WorkflowServiceHost.  
var host = new WorkflowServiceHost(workflow1, new Uri("http://localhost:8293/Service1.xamlx"));  
  
// Enable Metadata publishing/  
ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
smb.HttpGetEnabled = true;  
smb.MetadataExporter.PolicyVersion = PolicyVersion.Policy15;  
host.Description.Behaviors.Add(smb);  
  
// Open the WorkflowServiceHost and wait for requests.  
host.Open();  
Console.WriteLine("Press enter to quit");  
Console.ReadLine();  
```  
  
 Jeśli nie są kompilowane wyrażeń C#, `Open` operacja zakończy się pomyślnie, ale przepływ pracy zakończy się niepowodzeniem, gdy jest wywoływana. Następujące `CompileExpressions` metody jest taka sama jak metoda z poprzedniej [wyrażenia przy użyciu języka C# w przepływach pracy kodu](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) sekcji.  
  
```csharp  
static void CompileExpressions(Activity activity)  
{  
    // activityName is the Namespace.Type of the activity that contains the  
    // C# expressions.  
    string activityName = activity.GetType().ToString();  
  
    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name  
    // to represent the new type that represents the compiled expressions.  
    // Take everything after the last . for the type name.  
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";  
    // Take everything before the last . for the namespace.  
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());  
  
    // Create a TextExpressionCompilerSettings.  
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings  
    {  
        Activity = activity,  
        Language = "C#",  
        ActivityName = activityType,  
        ActivityNamespace = activityNamespace,  
        RootNamespace = null,  
        GenerateAsPartialClass = false,  
        AlwaysGenerateSource = true,  
        ForImplementation = false  
    };  
  
    // Compile the C# expression.  
    TextExpressionCompilerResults results =  
        new TextExpressionCompiler(settings).Compile();  
  
    // Any compilation errors are contained in the CompilerMessages.  
    if (results.HasErrors)  
    {  
        throw new Exception("Compilation failed.");  
    }  
  
    // Create an instance of the new compiled expression type.  
    ICompiledExpressionRoot compiledExpressionRoot =  
        Activator.CreateInstance(results.ResultType,  
            new object[] { activity }) as ICompiledExpressionRoot;  
  
    // Attach it to the activity.  
    CompiledExpressionInvoker.SetCompiledExpressionRoot(  
        activity, compiledExpressionRoot);  
}  
```
