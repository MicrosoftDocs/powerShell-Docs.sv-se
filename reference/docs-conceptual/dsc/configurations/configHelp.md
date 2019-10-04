---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Skrivhjälp för DSC-konfigurationer
ms.openlocfilehash: 498ec0f594ed3229e097903c4ea2ae34d3da03a2
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942078"
---
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="f7267-103">Skrivhjälp för DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="f7267-103">Writing help for DSC configurations</span></span>

><span data-ttu-id="f7267-104">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="f7267-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="f7267-105">Du kan använda kommenterings-baserad hjälp i DSC-konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="f7267-105">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="f7267-106">Användare kan komma åt hjälpen genom att anropa **konfigurationen** med `-?` eller med hjälp av cmdleten [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) .</span><span class="sxs-lookup"><span data-stu-id="f7267-106">Users can access the help by calling the **Configuration** with `-?`, or by using the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.</span></span> <span data-ttu-id="f7267-107">Placera din kommenterings-baserade hjälp direkt ovanför nyckelordet `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="f7267-107">Place your Comment-based help directly above the `Configuration` keyword.</span></span>
<span data-ttu-id="f7267-108">Du kan placera parameter hjälpen i rad med ditt kommentar block, direkt ovanför parameter deklarationen eller båda som i exemplet nedan.</span><span class="sxs-lookup"><span data-stu-id="f7267-108">You can place parameter help in-line with your comment block, directly above the parameter declaration, or both as in the example below.</span></span>

<span data-ttu-id="f7267-109">Mer information om PowerShell comment-baserad hjälp finns i [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="f7267-109">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

> [!NOTE]
> <span data-ttu-id="f7267-110">PowerShell-utvecklings miljöer, t. ex. VSCode och ISE, har också kodfragment som gör att du automatiskt kan infoga mallar för kommenterings block.</span><span class="sxs-lookup"><span data-stu-id="f7267-110">PowerShell development environments, like VSCode and the ISE, also have snippets to allow you to automatically insert comment block templates.</span></span>

<span data-ttu-id="f7267-111">I följande exempel visas ett skript som innehåller en konfiguration och en kommenterings-baserad hjälp för det.</span><span class="sxs-lookup"><span data-stu-id="f7267-111">The following example shows a script that contains a configuration and comment-based help for it.</span></span> <span data-ttu-id="f7267-112">I det här exemplet visas en konfiguration med parametrar.</span><span class="sxs-lookup"><span data-stu-id="f7267-112">This example shows a Configuration with parameters.</span></span> <span data-ttu-id="f7267-113">Mer information om hur du använder parametrar i dina konfigurationer finns i [lägga till parametrar i dina konfigurationer](add-parameters-to-a-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="f7267-113">To learn more about using parameters in your Configurations, see [Add Parameters to your Configurations](add-parameters-to-a-configuration.md).</span></span>

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each configuration.


.PARAMETER ComputerName
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
(and their descriptions) appear in help topic. To change the order, change the syntax.

.EXAMPLE
HelpSample -ComputerName localhost

A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.
.EXAMPLE
HelpSample -FilePath "C:\output.txt"

This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>
configuration HelpSample1
{
    param
    (
        [string]$ComputerName = 'localhost',
        # Provide a PARAMETER section for each parameter that your script or function accepts.
        [string]$FilePath = 'C:\Destination.txt'
    )

    Node $ComputerName
    {
        File HelloWorld
        {
            Contents="Hello World"
            DestinationPath = $FilePath
        }
    }
}
```

## <a name="viewing-configuration-help"></a><span data-ttu-id="f7267-114">Visa konfigurations hjälp</span><span class="sxs-lookup"><span data-stu-id="f7267-114">Viewing configuration help</span></span>

<span data-ttu-id="f7267-115">Om du vill visa hjälpen för en konfiguration använder du cmdleten `Get-Help` med namnet på funktionen eller skriver namnet på funktionen följt av `-?`.</span><span class="sxs-lookup"><span data-stu-id="f7267-115">To view the help for a configuration, use the `Get-Help` cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="f7267-116">Följande är resultatet av den föregående konfigurationen som skickades till `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="f7267-116">The following is the output of the previous Configuration passed to `Get-Help`.</span></span>

```powershell
Get-Help HelpSample1 -Detailed
```

```output
NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-PsDscRunAsCredential] <PSCredential>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName] <String>] [[-FilePath] <String>] [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


PARAMETERS
    -InstanceName <String>

    -DependsOn <String[]>

    -PsDscRunAsCredential <PSCredential>

    -OutputPath <String>

    -ConfigurationData <Hashtable>

    -ComputerName <String>
        The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

        Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
        Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
        The description can include paragraph breaks.

        The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
        (and their descriptions) appear in help topic. To change the order, change the syntax.

    -FilePath <String>
        Provide a PARAMETER section for each parameter that your script or function accepts.

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (https:/go.microsoft.com/fwlink/?LinkID=113216).

    -------------------------- EXAMPLE 1 --------------------------

    PS C:\>HelpSample -ComputerName localhost

    A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
    PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

    If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.




    -------------------------- EXAMPLE 2 --------------------------

    PS C:\>HelpSample -FilePath "C:\output.txt"

    This example will be labeled "EXAMPLE 2" when help is displayed to the user.




REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

> [!NOTE]
> <span data-ttu-id="f7267-117">Syntax-fält och parameter-attribut genereras automatiskt av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7267-117">Syntax fields and parameter attributes are automatically generated for you by PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7267-118">Se även</span><span class="sxs-lookup"><span data-stu-id="f7267-118">See Also</span></span>

- [<span data-ttu-id="f7267-119">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="f7267-119">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="f7267-120">Skriva, kompilera och tillämpa en konfiguration</span><span class="sxs-lookup"><span data-stu-id="f7267-120">Write, Compile, and Apply a Configuration</span></span>](write-compile-apply-configuration.md)
- [<span data-ttu-id="f7267-121">Lägga till parametrar till en konfiguration</span><span class="sxs-lookup"><span data-stu-id="f7267-121">Add Parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
