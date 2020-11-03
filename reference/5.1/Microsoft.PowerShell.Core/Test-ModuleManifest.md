---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-modulemanifest?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ModuleManifest
ms.openlocfilehash: 6e05a9a8e2266422e05040f6781224744e481830
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264129"
---
# <span data-ttu-id="cb5ee-103">Test-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="cb5ee-103">Test-ModuleManifest</span></span>

## <span data-ttu-id="cb5ee-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="cb5ee-104">SYNOPSIS</span></span>
<span data-ttu-id="cb5ee-105">Verifierar att en modul manifest fil beskriver innehållet i en modul korrekt.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-105">Verifies that a module manifest file accurately describes the contents of a module.</span></span>

## <span data-ttu-id="cb5ee-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cb5ee-106">SYNTAX</span></span>

```
Test-ModuleManifest [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="cb5ee-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="cb5ee-107">DESCRIPTION</span></span>

<span data-ttu-id="cb5ee-108">Cmdleten **test-ModuleManifest** verifierar att filerna som listas i modul manifest filen (. psd1) verkligen finns i de angivna Sök vägarna.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-108">The **Test-ModuleManifest** cmdlet verifies that the files that are listed in the module manifest (.psd1) file are actually in the specified paths.</span></span>

<span data-ttu-id="cb5ee-109">Denna cmdlet är utformad för att hjälpa utvecklare att testa sina MANIFEST filer.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-109">This cmdlet is designed to help module authors test their manifest files.</span></span>
<span data-ttu-id="cb5ee-110">Module användare kan också använda denna cmdlet i skript och kommandon för att identifiera fel innan de kör skript som är beroende av modulen.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-110">Module users can also use this cmdlet in scripts and commands to detect errors before they run scripts that depend on the module.</span></span>

<span data-ttu-id="cb5ee-111">**Test-ModuleManifest** returnerar ett objekt som representerar modulen.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-111">**Test-ModuleManifest** returns an object that represents the module.</span></span>
<span data-ttu-id="cb5ee-112">Det här är samma typ av objekt som Get-Module returnerar.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-112">This is the same type of object that Get-Module returns.</span></span>
<span data-ttu-id="cb5ee-113">Om några filer inte finns på de platser som anges i manifestet genererar cmdleten också ett fel för varje fil som saknas.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-113">If any files are not in the locations specified in the manifest, the cmdlet also generates an error for each missing file.</span></span>

## <span data-ttu-id="cb5ee-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="cb5ee-114">EXAMPLES</span></span>

### <span data-ttu-id="cb5ee-115">Exempel 1: testa ett manifest</span><span class="sxs-lookup"><span data-stu-id="cb5ee-115">Example 1: Test a manifest</span></span>

```powershell
test-ModuleManifest -Path "$pshome\Modules\TestModule.psd1"
```

<span data-ttu-id="cb5ee-116">Det här kommandot testar manifestet för TestModule.psd1-modulen.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-116">This command tests the TestModule.psd1 module manifest.</span></span>

### <span data-ttu-id="cb5ee-117">Exempel 2: testa ett manifest med hjälp av pipelinen</span><span class="sxs-lookup"><span data-stu-id="cb5ee-117">Example 2: Test a manifest by using the pipeline</span></span>

```powershell
"$pshome\Modules\TestModule.psd1" | test-modulemanifest
```

```Output
Test-ModuleManifest : The specified type data file 'C:\Windows\System32\Wi
ndowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml' could not be processed because the file was not found. Please correct the path and try again.
At line:1 char:34
+ "$pshome\Modules\TestModule.psd1" | test-modulemanifest <<<<
+ CategoryInfo          : ResourceUnavailable: (C:\Windows\System32\WindowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml:String) [Test-ModuleManifest], FileNotFoundException
+ FullyQualifiedErrorId : Modules_TypeDataFileNotFound,Microsoft.PowerShell.Commands.TestModuleManifestCommandName

Name              : TestModule
Path              : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule\TestModule.psd1
Description       :
Guid              : 6f0f1387-cd25-4902-b7b4-22cff6aefa7b
Version           : 1.0
ModuleBase        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule
ModuleType        : Manifest
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {}
ExportedVariables : {}
NestedModules     : {}
```

<span data-ttu-id="cb5ee-118">Det här kommandot använder en pipeline-operator (|) för att skicka en Sök vägs sträng till **test-ModuleManifest**.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-118">This command uses a pipeline operator (|) to send a path string to **Test-ModuleManifest**.</span></span>

<span data-ttu-id="cb5ee-119">Kommandots utdata visar att testet misslyckades eftersom TestTypes.ps1XML-filen, som fanns i listan i manifestet, inte hittades.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-119">The command output shows that the test failed, because the TestTypes.ps1xml file, which was listed in the manifest, was not found.</span></span>

### <span data-ttu-id="cb5ee-120">Exempel 3: Skriv en funktion för att testa ett modul manifest</span><span class="sxs-lookup"><span data-stu-id="cb5ee-120">Example 3: Write a function to test a module manifest</span></span>

```powershell
function Test-ManifestBool ($path)
```

```Output
{$a = dir $path | Test-ModuleManifest -ErrorAction SilentlyContinue; $?}
```

<span data-ttu-id="cb5ee-121">Den här funktionen liknar **test-ModuleManifest** , men returnerar ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-121">This function is like **Test-ModuleManifest** , but it returns a Boolean value.</span></span>
<span data-ttu-id="cb5ee-122">Funktionen returnerar $True om manifestet godkände testet och $False annars.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-122">The function returns $True if the manifest passed the test and $False otherwise.</span></span>

<span data-ttu-id="cb5ee-123">Funktionen använder Get-ChildItem-cmdlet, alias = dir, för att hämta det modul manifest som anges av $path variabeln.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-123">The function uses the Get-ChildItem cmdlet, alias = dir, to get the module manifest specified by the $path variable.</span></span>
<span data-ttu-id="cb5ee-124">Kommandot använder en pipeline-operator (|) för att skicka filobjektet till **test-ModuleManifest**.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-124">The command uses a pipeline operator (|) to pass the file object to **Test-ModuleManifest**.</span></span>

<span data-ttu-id="cb5ee-125">**Test-ModuleManifest** använder den gemensamma parametern *ErrorAction* med värdet SilentlyContinue för att förhindra visning av eventuella fel som genereras av kommandot.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-125">**Test-ModuleManifest** uses the *ErrorAction* common parameter with a value of SilentlyContinue to suppress the display of any errors that the command generates.</span></span>
<span data-ttu-id="cb5ee-126">Det sparar också **PSModuleInfo** -objektet som **test-ModuleManifest** returnerar i variabeln $a.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-126">It also saves the **PSModuleInfo** object that **Test-ModuleManifest** returns in the $a variable.</span></span>
<span data-ttu-id="cb5ee-127">Därför visas inte objektet.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-127">Therefore, the object is not displayed.</span></span>

<span data-ttu-id="cb5ee-128">I ett separat kommando visar funktionen värdet $?</span><span class="sxs-lookup"><span data-stu-id="cb5ee-128">Then, in a separate command, the function displays the value of the $?</span></span>
<span data-ttu-id="cb5ee-129">automatisk variabel.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-129">automatic variable.</span></span>
<span data-ttu-id="cb5ee-130">Om föregående kommando inte genererar något fel, visar kommandot $True och $False annars.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-130">If the previous command generates no error, the command displays $True, and $False otherwise.</span></span>

<span data-ttu-id="cb5ee-131">Du kan använda den här funktionen i villkorliga uttryck, till exempel sådana som kan komma före ett **import-module-** kommando eller ett kommando som använder modulen.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-131">You can use this function in conditional statements, such as those that might precede an **Import-Module** command or a command that uses the module.</span></span>

## <span data-ttu-id="cb5ee-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="cb5ee-132">PARAMETERS</span></span>

### <span data-ttu-id="cb5ee-133">-Path</span><span class="sxs-lookup"><span data-stu-id="cb5ee-133">-Path</span></span>

<span data-ttu-id="cb5ee-134">Anger en sökväg och ett fil namn för manifest filen.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-134">Specifies a path and file name for the manifest file.</span></span>
<span data-ttu-id="cb5ee-135">Ange en valfri sökväg och ett namn för modulens manifest fil som har fil namns tillägget. psd1.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-135">Enter an optional path and name of the module manifest file that has the .psd1 file name extension.</span></span>
<span data-ttu-id="cb5ee-136">Standard platsen är den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-136">The default location is the current directory.</span></span>
<span data-ttu-id="cb5ee-137">Jokertecken stöds, men måste matchas till en enda moduls manifest fil.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-137">Wildcard characters are supported, but must resolve to a single module manifest file.</span></span>
<span data-ttu-id="cb5ee-138">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-138">This parameter is required.</span></span>
<span data-ttu-id="cb5ee-139">Du kan också skicka en sökväg till **test-ModuleManifest**.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-139">You can also pipe a path to **Test-ModuleManifest**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="cb5ee-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cb5ee-140">CommonParameters</span></span>

<span data-ttu-id="cb5ee-141">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cb5ee-142">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cb5ee-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cb5ee-143">INDATA</span><span class="sxs-lookup"><span data-stu-id="cb5ee-143">INPUTS</span></span>

### <span data-ttu-id="cb5ee-144">System. String</span><span class="sxs-lookup"><span data-stu-id="cb5ee-144">System.String</span></span>

<span data-ttu-id="cb5ee-145">Du kan skicka vidare sökvägen till ett modul manifest till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-145">You can pipe the path to a module manifest to this cmdlet.</span></span>

## <span data-ttu-id="cb5ee-146">UTDATA</span><span class="sxs-lookup"><span data-stu-id="cb5ee-146">OUTPUTS</span></span>

### <span data-ttu-id="cb5ee-147">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="cb5ee-147">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="cb5ee-148">Denna cmdlet returnerar ett **PSModuleInfo** -objekt som representerar modulen.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-148">This cmdlet returns a **PSModuleInfo** object that represents the module.</span></span>
<span data-ttu-id="cb5ee-149">Det returnerar objektet även om manifestet innehåller fel.</span><span class="sxs-lookup"><span data-stu-id="cb5ee-149">It returns this object even if the manifest has errors.</span></span>

## <span data-ttu-id="cb5ee-150">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="cb5ee-150">NOTES</span></span>

## <span data-ttu-id="cb5ee-151">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="cb5ee-151">RELATED LINKS</span></span>

[<span data-ttu-id="cb5ee-152">Exportera – ModuleMember</span><span class="sxs-lookup"><span data-stu-id="cb5ee-152">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="cb5ee-153">Hämta modul</span><span class="sxs-lookup"><span data-stu-id="cb5ee-153">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="cb5ee-154">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="cb5ee-154">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="cb5ee-155">Ny modul</span><span class="sxs-lookup"><span data-stu-id="cb5ee-155">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="cb5ee-156">New-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="cb5ee-156">New-ModuleManifest</span></span>](New-ModuleManifest.md)

[<span data-ttu-id="cb5ee-157">Ta bort modul</span><span class="sxs-lookup"><span data-stu-id="cb5ee-157">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="cb5ee-158">about_Modules</span><span class="sxs-lookup"><span data-stu-id="cb5ee-158">about_Modules</span></span>](About/about_Modules.md)
