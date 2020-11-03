---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-modulemember?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ModuleMember
ms.openlocfilehash: 8d99f861a9cbdc72d30975275c49c6cd5bde2bed
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93263103"
---
# <span data-ttu-id="59414-103">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="59414-103">Export-ModuleMember</span></span>

## <span data-ttu-id="59414-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="59414-104">SYNOPSIS</span></span>
<span data-ttu-id="59414-105">Anger de modul medlemmar som exporteras.</span><span class="sxs-lookup"><span data-stu-id="59414-105">Specifies the module members that are exported.</span></span>

## <span data-ttu-id="59414-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="59414-106">SYNTAX</span></span>

```
Export-ModuleMember [[-Function] <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="59414-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="59414-107">DESCRIPTION</span></span>

<span data-ttu-id="59414-108">Cmdlet: en **export-ModuleMember** anger de modul medlemmar som exporteras från en skriptfil (. psm1) eller från en dynamisk modul som skapats med hjälp av New-Module cmdlet.</span><span class="sxs-lookup"><span data-stu-id="59414-108">The **Export-ModuleMember** cmdlet specifies the module members that are exported from a script module (.psm1) file, or from a dynamic module created by using the New-Module cmdlet.</span></span>
<span data-ttu-id="59414-109">Modul medlemmar är cmdlets, functions, Variables och alias.</span><span class="sxs-lookup"><span data-stu-id="59414-109">Module members include cmdlets, functions, variables, and aliases.</span></span>
<span data-ttu-id="59414-110">Denna cmdlet kan endast användas i en skript fil eller en dynamisk modul.</span><span class="sxs-lookup"><span data-stu-id="59414-110">This cmdlet can be used only in a script module file or a dynamic module.</span></span>

<span data-ttu-id="59414-111">Om en skript-modul inte innehåller ett **export-ModuleMember-** kommando, exporteras funktionerna och aliasen i modulen skript, men variablerna är inte.</span><span class="sxs-lookup"><span data-stu-id="59414-111">If a script module does not include an **Export-ModuleMember** command, the functions and aliases in the script module are exported, but the variables are not.</span></span>
<span data-ttu-id="59414-112">När en skript-modul innehåller **export-ModuleMember-** kommandon, exporteras bara de medlemmar som anges i **export-ModuleMember-** kommandona.</span><span class="sxs-lookup"><span data-stu-id="59414-112">When a script module includes **Export-ModuleMember** commands, only the members specified in the **Export-ModuleMember** commands are exported.</span></span>
<span data-ttu-id="59414-113">Du kan också använda **export-ModuleMember** för att undertrycka eller exportera medlemmar som-modulen importerar från andra moduler.</span><span class="sxs-lookup"><span data-stu-id="59414-113">You can also use **Export-ModuleMember** to suppress or export members that the script module imports from other modules.</span></span>

<span data-ttu-id="59414-114">Ett **export-ModuleMember-** kommando är valfritt, men det är en bra metod.</span><span class="sxs-lookup"><span data-stu-id="59414-114">An **Export-ModuleMember** command is optional, but it is a best practice.</span></span>
<span data-ttu-id="59414-115">Även om kommandot bekräftar standardvärdena, visar det avsikten med modulens författare.</span><span class="sxs-lookup"><span data-stu-id="59414-115">Even if the command confirms the default values, it demonstrates the intention of the module author.</span></span>

## <span data-ttu-id="59414-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="59414-116">EXAMPLES</span></span>

### <span data-ttu-id="59414-117">Exempel 1: exportera funktioner och alias i en skriptbaserad modul</span><span class="sxs-lookup"><span data-stu-id="59414-117">Example 1: Export functions and aliases in a script module</span></span>

```powershell
Export-ModuleMember -Function * -Alias *
```

<span data-ttu-id="59414-118">Det här kommandot exporterar alla funktioner och alias som definierats i modulen script.</span><span class="sxs-lookup"><span data-stu-id="59414-118">This command exports all the functions and aliases defined in the script module.</span></span>

### <span data-ttu-id="59414-119">Exempel 2: exportera vissa alias och funktioner</span><span class="sxs-lookup"><span data-stu-id="59414-119">Example 2: Export specific aliases and functions</span></span>

```powershell
Export-ModuleMember -Function Get-Test, New-Test, Start-Test -Alias gtt, ntt, stt
```

<span data-ttu-id="59414-120">Det här kommandot exporterar tre alias och tre funktioner som definierats i modulen script.</span><span class="sxs-lookup"><span data-stu-id="59414-120">This command exports three aliases and three functions defined in the script module.</span></span>

<span data-ttu-id="59414-121">Du kan använda det här kommando formatet för att ange namnen på modul medlemmar.</span><span class="sxs-lookup"><span data-stu-id="59414-121">You can use this command format to specify the names of module members.</span></span>

### <span data-ttu-id="59414-122">Exempel 3: exportera inga medlemmar</span><span class="sxs-lookup"><span data-stu-id="59414-122">Example 3: Export no members</span></span>

```powershell
Export-ModuleMember
```

<span data-ttu-id="59414-123">Det här kommandot anger att inga medlemmar som har definierats i modulen för skript ska exporteras.</span><span class="sxs-lookup"><span data-stu-id="59414-123">This command specifies that no members defined in the script module are exported.</span></span>

<span data-ttu-id="59414-124">Det här kommandot förhindrar att modul medlemmar exporteras, men döljer inte medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="59414-124">This command prevents the module members from being exported, but it does not hide the members.</span></span>
<span data-ttu-id="59414-125">Användare kan läsa och kopiera module-medlemmar eller använda anrops operatorn (&) för att anropa modul medlemmar som inte exporteras.</span><span class="sxs-lookup"><span data-stu-id="59414-125">Users can read and copy module members or use the call operator (&) to invoke module members that are not exported.</span></span>

### <span data-ttu-id="59414-126">Exempel 4: exportera en speciell variabel</span><span class="sxs-lookup"><span data-stu-id="59414-126">Example 4: Export a specific variable</span></span>

```powershell
Export-ModuleMember -Variable increment
```

<span data-ttu-id="59414-127">Det här kommandot exporterar endast $increment-variabeln från modulen script.</span><span class="sxs-lookup"><span data-stu-id="59414-127">This command exports only the $increment variable from the script module.</span></span>
<span data-ttu-id="59414-128">Inga andra medlemmar exporteras.</span><span class="sxs-lookup"><span data-stu-id="59414-128">No other members are exported.</span></span>

<span data-ttu-id="59414-129">Om du vill exportera en variabel, förutom att exportera funktionerna i en modul, måste kommandot **export-ModuleMember** innehålla namnen på alla funktioner och namnet på variabeln.</span><span class="sxs-lookup"><span data-stu-id="59414-129">If you want to export a variable, in addition to exporting the functions in a module, the **Export-ModuleMember** command must include the names of all of the functions and the name of the variable.</span></span>

### <span data-ttu-id="59414-130">Exempel 5: flera export kommandon</span><span class="sxs-lookup"><span data-stu-id="59414-130">Example 5: Multiple export commands</span></span>

```powershell
# From TestModule.psm1
Function New-Test
{
    Write-Output 'I am New-Test function'
}
Export-ModuleMember -Function New-Test

function Validate-Test
{
    Write-Output 'I am Validate-Test function'
}
function Start-Test
{
    Write-Output 'I am Start-Test function'
}
Set-Alias stt Start-Test
Export-ModuleMember -Function Start-Test -Alias stt
```

<span data-ttu-id="59414-131">De här kommandona visar hur flera **export-ModuleMember** -kommandon tolkas i en skriptfil (. psm1)-fil.</span><span class="sxs-lookup"><span data-stu-id="59414-131">These commands show how multiple **Export-ModuleMember** commands are interpreted in a script module (.psm1) file.</span></span>

<span data-ttu-id="59414-132">Dessa kommandon skapar tre funktioner och ett alias och exporterar sedan två av funktionerna och aliaset.</span><span class="sxs-lookup"><span data-stu-id="59414-132">These commands create three functions and one alias, and then they export two of the functions and the alias.</span></span>

<span data-ttu-id="59414-133">Utan **export-ModuleMember-** kommandona exporteras alla tre funktionerna och aliaset.</span><span class="sxs-lookup"><span data-stu-id="59414-133">Without the **Export-ModuleMember** commands, all three of the functions and the alias would be exported.</span></span>
<span data-ttu-id="59414-134">Med **export-ModuleMember-** kommandona exporteras endast funktionerna **New-test** och **Start-test** och STT alias.</span><span class="sxs-lookup"><span data-stu-id="59414-134">With the **Export-ModuleMember** commands, only the **New-Test** and **Start-Test** functions and the STT alias are exported.</span></span>

### <span data-ttu-id="59414-135">Exempel 6: exportera medlemmar i en dynamisk modul</span><span class="sxs-lookup"><span data-stu-id="59414-135">Example 6: Export members in a dynamic module</span></span>

```powershell
New-Module -Script {function SayHello {"Hello!"}; Set-Alias Hi SayHello; Export-ModuleMember -Alias Hi -Function SayHello}
```

<span data-ttu-id="59414-136">Det här kommandot visar hur du använder Export-ModuleMember i en dynamisk modul som skapas med hjälp av cmdleten **New-module** .</span><span class="sxs-lookup"><span data-stu-id="59414-136">This command shows how to use Export-ModuleMember in a dynamic module that is created by using the **New-Module** cmdlet.</span></span>

<span data-ttu-id="59414-137">I det här exemplet används **export-ModuleMember** för att exportera både det Hi-alias och **SayHello** -funktionen i den dynamiska modulen.</span><span class="sxs-lookup"><span data-stu-id="59414-137">In this example, **Export-ModuleMember** is used to export both the Hi alias and the **SayHello** function in the dynamic module.</span></span>

### <span data-ttu-id="59414-138">Exempel 7: deklarera och exportera en funktion i ett enda kommando</span><span class="sxs-lookup"><span data-stu-id="59414-138">Example 7: Declare and export a function in a single command</span></span>

```powershell
# From TestModule.psm1
function Export
{
  param (
    [Parameter(Mandatory=$true)]
    [ValidateSet("function","variable")]
    $Type,
    [Parameter(Mandatory=$true)]
    $Name,
    [Parameter(Mandatory=$true)]
    $Value
    )

    if ($Type -eq "function")
    {
        Set-item "function:script:$Name" $Value
        Export-ModuleMember $Name
    }
    else
    {
    Set-Variable -scope Script $Name $Value
    Export-ModuleMember -variable $Name
    }
}

Export function New-Test {Write-Output 'I am New-Test function'}
function helper {Write-Output 'I am helper function'}

Export variable Interval 0
$Interval = 2
```

<span data-ttu-id="59414-139">Det här exemplet innehåller en funktion med namnet **export** som deklarerar en funktion eller skapar en variabel och skriver sedan ett `Export-ModuleMember` kommando för funktionen eller variabeln.</span><span class="sxs-lookup"><span data-stu-id="59414-139">This example includes a function named **Export** that declares a function or creates a variable, and then writes an `Export-ModuleMember` command for the function or variable.</span></span>
<span data-ttu-id="59414-140">På så sätt kan du deklarera och exportera en funktion eller variabel i ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="59414-140">This lets you declare and export a function or variable in a single command.</span></span>

<span data-ttu-id="59414-141">Om du vill använda funktionen **Exportera** inkluderar du den i modulen skript.</span><span class="sxs-lookup"><span data-stu-id="59414-141">To use the **Export** function, include it in your script module.</span></span>
<span data-ttu-id="59414-142">Om du vill exportera en funktion skriver du in `Export` före nyckelordet **Function** .</span><span class="sxs-lookup"><span data-stu-id="59414-142">To export a function, type `Export` before the **Function** keyword.</span></span>

<span data-ttu-id="59414-143">Om du vill exportera en variabel använder du följande format för att deklarera variabeln och ange dess värde:</span><span class="sxs-lookup"><span data-stu-id="59414-143">To export a variable, use the following format to declare the variable and set its value:</span></span>

`Export variable <variable-name> <value>`

<span data-ttu-id="59414-144">Kommandona i exemplet visar rätt format.</span><span class="sxs-lookup"><span data-stu-id="59414-144">The commands in the example show the correct format.</span></span>
<span data-ttu-id="59414-145">I det här exemplet exporteras endast funktionen **New-test** och $Interval variabeln.</span><span class="sxs-lookup"><span data-stu-id="59414-145">In this example, only the **New-Test** function and the $Interval variable are exported.</span></span>

## <span data-ttu-id="59414-146">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="59414-146">PARAMETERS</span></span>

### <span data-ttu-id="59414-147">-Alias</span><span class="sxs-lookup"><span data-stu-id="59414-147">-Alias</span></span>

<span data-ttu-id="59414-148">Anger de alias som exporteras från filen script module.</span><span class="sxs-lookup"><span data-stu-id="59414-148">Specifies the aliases that are exported from the script module file.</span></span>
<span data-ttu-id="59414-149">Ange namnen på alias.</span><span class="sxs-lookup"><span data-stu-id="59414-149">Enter the alias names.</span></span>
<span data-ttu-id="59414-150">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="59414-150">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="59414-151">-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="59414-151">-Cmdlet</span></span>

<span data-ttu-id="59414-152">Anger de cmdletar som exporteras från filen script module.</span><span class="sxs-lookup"><span data-stu-id="59414-152">Specifies the cmdlets that are exported from the script module file.</span></span>
<span data-ttu-id="59414-153">Ange cmdlet-namnen.</span><span class="sxs-lookup"><span data-stu-id="59414-153">Enter the cmdlet names.</span></span>
<span data-ttu-id="59414-154">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="59414-154">Wildcard characters are permitted.</span></span>

<span data-ttu-id="59414-155">Det går inte att skapa cmdletar i en skript fil, men du kan importera cmdletar från en binär modul till en-modul och exportera dem igen från-modulen.</span><span class="sxs-lookup"><span data-stu-id="59414-155">You cannot create cmdlets in a script module file, but you can import cmdlets from a binary module into a script module and re-export them from the script module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="59414-156">– Funktion</span><span class="sxs-lookup"><span data-stu-id="59414-156">-Function</span></span>

<span data-ttu-id="59414-157">Anger de funktioner som exporteras från filen script module.</span><span class="sxs-lookup"><span data-stu-id="59414-157">Specifies the functions that are exported from the script module file.</span></span>
<span data-ttu-id="59414-158">Ange funktions namnen.</span><span class="sxs-lookup"><span data-stu-id="59414-158">Enter the function names.</span></span>
<span data-ttu-id="59414-159">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="59414-159">Wildcard characters are permitted.</span></span>
<span data-ttu-id="59414-160">Du kan också använda funktions namn strängar för att **Exportera-ModuleMember**.</span><span class="sxs-lookup"><span data-stu-id="59414-160">You can also pipe function name strings to **Export-ModuleMember**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="59414-161">– Variabel</span><span class="sxs-lookup"><span data-stu-id="59414-161">-Variable</span></span>

<span data-ttu-id="59414-162">Anger de variabler som exporteras från filen script module.</span><span class="sxs-lookup"><span data-stu-id="59414-162">Specifies the variables that are exported from the script module file.</span></span>
<span data-ttu-id="59414-163">Ange variabel namn, utan dollar tecken.</span><span class="sxs-lookup"><span data-stu-id="59414-163">Enter the variable names, without a dollar sign.</span></span>
<span data-ttu-id="59414-164">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="59414-164">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="59414-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="59414-165">CommonParameters</span></span>

<span data-ttu-id="59414-166">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="59414-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="59414-167">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="59414-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="59414-168">INDATA</span><span class="sxs-lookup"><span data-stu-id="59414-168">INPUTS</span></span>

### <span data-ttu-id="59414-169">System. String</span><span class="sxs-lookup"><span data-stu-id="59414-169">System.String</span></span>

<span data-ttu-id="59414-170">Du kan skicka funktions namn strängar till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="59414-170">You can pipe function name strings to this cmdlet.</span></span>

## <span data-ttu-id="59414-171">UTDATA</span><span class="sxs-lookup"><span data-stu-id="59414-171">OUTPUTS</span></span>

### <span data-ttu-id="59414-172">Inget</span><span class="sxs-lookup"><span data-stu-id="59414-172">None</span></span>

<span data-ttu-id="59414-173">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="59414-173">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="59414-174">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="59414-174">NOTES</span></span>

* <span data-ttu-id="59414-175">Om du vill undanta en medlem från listan över exporterade medlemmar lägger du till ett **export-ModuleMember-** kommando som visar alla andra medlemmar men utelämnar den medlem som du vill undanta.</span><span class="sxs-lookup"><span data-stu-id="59414-175">To exclude a member from the list of exported members, add an **Export-ModuleMember** command that lists all other members but omits the member that you want to exclude.</span></span>

## <span data-ttu-id="59414-176">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="59414-176">RELATED LINKS</span></span>

[<span data-ttu-id="59414-177">Hämta modul</span><span class="sxs-lookup"><span data-stu-id="59414-177">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="59414-178">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="59414-178">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="59414-179">Ta bort modul</span><span class="sxs-lookup"><span data-stu-id="59414-179">Remove-Module</span></span>](Remove-Module.md)
