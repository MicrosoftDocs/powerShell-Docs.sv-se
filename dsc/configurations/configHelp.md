---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Skrivhjälp för DSC-konfigurationer
ms.openlocfilehash: 498ec0f594ed3229e097903c4ea2ae34d3da03a2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080194"
---
# <a name="writing-help-for-dsc-configurations"></a>Skrivhjälp för DSC-konfigurationer

>Gäller för: Windows PowerShell 5.0

Du kan använda kommentarbaserad hjälp i DSC-konfigurationer. Användare kan komma åt hjälp genom att anropa den **Configuration** med `-?`, eller genom att använda den [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet. Placera din direkt ovan kommentarbaserad hjälp de `Configuration` nyckelord.
Du kan placera parametern hjälp i linje med din kommentarblocket direkt ovanför Parameterdeklarationen eller båda som i exemplet nedan.

Mer information om PowerShell kommentarbaserad hjälp finns i [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

> [!NOTE]
> PowerShell utvecklingsmiljöer som VSCode och ISE har också kodfragment att automatiskt infoga kommentar block mallar.

I följande exempel visas ett skript som innehåller ett konfigurations- och kommentarbaserad hjälp för den. Det här exemplet visar en konfiguration med parametrar. Mer information om hur du använder parametrar i dina konfigurationer finns [lägga till parametrar till dina konfigurationer](add-parameters-to-a-configuration.md).

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

## <a name="viewing-configuration-help"></a>Visa hjälp om konfiguration

Du kan visa hjälpen för en konfiguration med den `Get-Help` cmdlet med namnet på funktionen, eller namnet på funktionen följt av `-?`. Följande är utdata från den tidigare konfigurationen som skickas till `Get-Help`.

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
> Syntax fält och parameterattribut genereras automatiskt åt dig av PowerShell.

## <a name="see-also"></a>Se även

- [DSC-konfigurationer](configurations.md)
- [Skriva, kompilera och tillämpa en konfiguration](write-compile-apply-configuration.md)
- [Lägg till parametrar till en konfiguration](add-parameters-to-a-configuration.md)
