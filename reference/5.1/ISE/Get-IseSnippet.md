---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/get-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-IseSnippet
ms.openlocfilehash: c43dae3f178ae778d78fe3718fa85fd2635eba86
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268113"
---
# <span data-ttu-id="2223a-103">Get-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="2223a-103">Get-IseSnippet</span></span>

## <span data-ttu-id="2223a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2223a-104">SYNOPSIS</span></span>
<span data-ttu-id="2223a-105">Hämtar kodfragment som användaren har skapat.</span><span class="sxs-lookup"><span data-stu-id="2223a-105">Gets snippets that the user created.</span></span>

## <span data-ttu-id="2223a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2223a-106">SYNTAX</span></span>

```
Get-IseSnippet [<CommonParameters>]
```

## <span data-ttu-id="2223a-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2223a-107">DESCRIPTION</span></span>

<span data-ttu-id="2223a-108">`Get-IseSnippet`Cmdlet: en hämtar de PS1XML-filer som innehåller återanvändbara text-kodfragment som användaren skapade.</span><span class="sxs-lookup"><span data-stu-id="2223a-108">The `Get-IseSnippet` cmdlet gets the PS1XML files that contain reusable text snippets that the user created.</span></span> <span data-ttu-id="2223a-109">Det fungerar bara i Windows PowerShell ISE (Integrated Scripting Environment).</span><span class="sxs-lookup"><span data-stu-id="2223a-109">It works only in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

<span data-ttu-id="2223a-110">När du använder `New-IseSnippet` cmdleten för att skapa ett kodfragment `New-IseSnippet` skapar en `<SnippetTitle>.Snippets.ps1xml` fil i `$home\Documents\WindowsPowerShell\Snippets` katalogen.</span><span class="sxs-lookup"><span data-stu-id="2223a-110">When you use the `New-IseSnippet` cmdlet to create a snippet, `New-IseSnippet` creates a `<SnippetTitle>.Snippets.ps1xml` file in the `$home\Documents\WindowsPowerShell\Snippets` directory.</span></span>
<span data-ttu-id="2223a-111">`Get-IseSnippet` hämtar kodfragments-filerna i katalogen kodfragment.</span><span class="sxs-lookup"><span data-stu-id="2223a-111">`Get-IseSnippet` gets the snippet files in the Snippets directory.</span></span>

<span data-ttu-id="2223a-112">Denna cmdlet tillhandahåller inte inbyggda kodfragment eller kodfragment som importeras från moduler via `Import-IseSnippet` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2223a-112">This cmdlet does not get built-in snippets or snippets that are imported from modules through the `Import-IseSnippet` cmdlet.</span></span>

<span data-ttu-id="2223a-113">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2223a-113">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="2223a-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2223a-114">EXAMPLES</span></span>

### <span data-ttu-id="2223a-115">Exempel 1: Hämta alla användardefinierade kod avsnitt</span><span class="sxs-lookup"><span data-stu-id="2223a-115">Example 1: Get all user-defined snippets</span></span>

<span data-ttu-id="2223a-116">Det här exemplet hämtar alla användardefinierade kod avsnitt i katalogen kodfragment.</span><span class="sxs-lookup"><span data-stu-id="2223a-116">This example gets all user-define snippets in the Snippets directory.</span></span>

```powershell
Get-IseSnippet
```

### <span data-ttu-id="2223a-117">Exempel 2: kopiera alla användardefinierade kod avsnitt från fjärrdatorer till en delad katalog</span><span class="sxs-lookup"><span data-stu-id="2223a-117">Example 2: Copy all user-defined snippets from remote computers to a shared directory</span></span>

<span data-ttu-id="2223a-118">I det här exemplet kopieras alla användare-skapade kodfragment från en grupp fjärrdatorer till en katalog med delade avsnitt.</span><span class="sxs-lookup"><span data-stu-id="2223a-118">This example copies all of the user-created snippets from a group of remote computers to a shared Snippets directory.</span></span>

```powershell
Invoke-Command -Computer (Get-Content Servers.txt) {Get-IseSnippet | Copy-Item -Destination \\Server01\Share01\Snippets}
```

<span data-ttu-id="2223a-119">`Invoke-Command` körs `Get-IseSnippet` på datorerna i `Servers.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="2223a-119">`Invoke-Command` runs `Get-IseSnippet` on the computers in the `Servers.txt` file.</span></span> <span data-ttu-id="2223a-120">En pipeline-operator ( `|` ) skickar kodfragmentet till `Copy-Item` cmdleten, som kopierar dem till den katalog som anges av **mål** parametern.</span><span class="sxs-lookup"><span data-stu-id="2223a-120">A pipeline operator (`|`) sends the snippet files to the `Copy-Item` cmdlet, which copies them to the directory that is specified by the **Destination** parameter.</span></span>

### <span data-ttu-id="2223a-121">Exempel 3: Visa rubrik och text för varje kod avsnitt på en lokal dator</span><span class="sxs-lookup"><span data-stu-id="2223a-121">Example 3: Display the title and text of each snippet on a local computer</span></span>

<span data-ttu-id="2223a-122">I det här exemplet `Get-IseSnippet` används `Select-Xml` cmdletarna och för att Visa rubrik och text för varje kodfragment på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="2223a-122">This example uses the `Get-IseSnippet` and `Select-Xml` cmdlets to display the title and text of each snippet on the local computer.</span></span>

```powershell
#Parse-Snippet Function
function Parse-Snippet {
  $SnippetFiles = Get-IseSnippet
  $SnippetNamespace = @{x="http://schemas.microsoft.com/PowerShell/Snippets"}
  foreach ($SnippetFile in $SnippetFiles) {
     Write-Host ""
     $Title = Select-Xml -Path $SnippetFile.FullName -Namespace $SnippetNamespace -XPath "//x:Title" |
       ForEach-Object {$_.Node.InnerXML}
     $Text = Select-Xml -Path $SnippetFile.FullName -Namespace $SnippetNamespace -XPath "//x:Script" |
       ForEach-Object {$_.Node.InnerText}
     Write-Host "Title: $Title"
     Write-Host "Text: $Text"
   }
}
```

```Output
Title: Mandatory
Text:
Param
(
  [parameter(Mandatory=True)]
  [String[]]
  $<ParameterName>
)

Title: Copyright
Text:  (c) Fabrikam, Inc. 2012
```

### <span data-ttu-id="2223a-123">Exempel 4: Visa rubriken och beskrivningen för alla kodfragment i sessionen</span><span class="sxs-lookup"><span data-stu-id="2223a-123">Example 4: Display the title and description of all snippets in the session</span></span>

<span data-ttu-id="2223a-124">I det här exemplet visas rubriken och beskrivningen av alla kodfragment i sessionen, inklusive inbyggda kodfragment, användardefinierade kodfragment och importerade kod avsnitt.</span><span class="sxs-lookup"><span data-stu-id="2223a-124">This example displays the title and description of all snippets in the session, including built-in snippets, user-defined snippets, and imported snippets.</span></span>

```powershell
$PSISE.CurrentPowerShellTab.Snippets | Format-Table DisplayTitle, Description
```

<span data-ttu-id="2223a-125">`$PSISE`Variabeln representerar Windows PowerShell ISE värd programmet.</span><span class="sxs-lookup"><span data-stu-id="2223a-125">The `$PSISE` variable represents the Windows PowerShell ISE host program.</span></span> <span data-ttu-id="2223a-126">Egenskapen **CurrentPowerShellTab** för `$PSISE` variabeln representerar den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="2223a-126">The **CurrentPowerShellTab** property of the `$PSISE` variable represent the current session.</span></span> <span data-ttu-id="2223a-127">Egenskapen **kodfragment** representerar kodfragment i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="2223a-127">The **Snippets** property represents snippets in the current session.</span></span>

<span data-ttu-id="2223a-128">`$PSISE.CurrentPowerShellTab.Snippets`Kommandot returnerar ett **Microsoft. PowerShell. Host. ISE. ISESnippet** -objekt som representerar ett kodfragment, till skillnad från `Get-IseSnippet` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2223a-128">The `$PSISE.CurrentPowerShellTab.Snippets` command returns a **Microsoft.PowerShell.Host.ISE.ISESnippet** object that represents a snippet, unlike the `Get-IseSnippet` cmdlet.</span></span> <span data-ttu-id="2223a-129">`Get-IseSnippet` Returnerar ett fil objekt (system. io. FileInfo) som representerar en kodfragments fil.</span><span class="sxs-lookup"><span data-stu-id="2223a-129">`Get-IseSnippet` returns a file object (System.Io.FileInfo) that represents a snippet file.</span></span>

<span data-ttu-id="2223a-130">`Format-Table`Cmdleten visar egenskaperna **DisplayTitle** och **Description** för kodfragmenten i en tabell.</span><span class="sxs-lookup"><span data-stu-id="2223a-130">The `Format-Table` cmdlet displays the **DisplayTitle** and **Description** properties of the snippets in a table.</span></span>

## <span data-ttu-id="2223a-131">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2223a-131">PARAMETERS</span></span>

### <span data-ttu-id="2223a-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2223a-132">CommonParameters</span></span>

<span data-ttu-id="2223a-133">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2223a-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2223a-134">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2223a-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2223a-135">INDATA</span><span class="sxs-lookup"><span data-stu-id="2223a-135">INPUTS</span></span>

## <span data-ttu-id="2223a-136">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2223a-136">OUTPUTS</span></span>

### <span data-ttu-id="2223a-137">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="2223a-137">System.IO.FileInfo</span></span>

<span data-ttu-id="2223a-138">Denna cmdlet returnerar ett fil objekt som representerar kodfragments filen.</span><span class="sxs-lookup"><span data-stu-id="2223a-138">This cmdlet returns a file object that represents the snippet file.</span></span>

## <span data-ttu-id="2223a-139">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2223a-139">NOTES</span></span>

* <span data-ttu-id="2223a-140">`New-IseSnippet`Cmdlet: en lagrar nya användare-skapade kodfragment i osignerade. ps1xml-filer.</span><span class="sxs-lookup"><span data-stu-id="2223a-140">The `New-IseSnippet` cmdlet stores new user-created snippets in unsigned .ps1xml files.</span></span> <span data-ttu-id="2223a-141">Det innebär att Windows PowerShell inte kan lägga till dem i en session där körnings principen är **AllSigned** eller **begränsad**.</span><span class="sxs-lookup"><span data-stu-id="2223a-141">As such, Windows PowerShell cannot add them to a session in which the execution policy is **AllSigned** or **Restricted**.</span></span> <span data-ttu-id="2223a-142">I en **begränsad** eller **AllSigned** session kan du skapa, hämta och importera osignerade kodfragment, men du kan inte använda dem i sessionen.</span><span class="sxs-lookup"><span data-stu-id="2223a-142">In a **Restricted** or **AllSigned** session, you can create, get, and import unsigned user-created snippets, but you cannot use them in the session.</span></span>

  <span data-ttu-id="2223a-143">Om du vill använda osignerade användar kods tycken som `Get-IseSnippet` cmdleten returnerar ändrar du körnings principen och startar sedan om Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2223a-143">To use unsigned user-created snippets that the `Get-IseSnippet` cmdlet returns, change the execution policy, and then restart Windows PowerShell ISE.</span></span>

  <span data-ttu-id="2223a-144">Mer information om körnings principer för Windows PowerShell finns i [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="2223a-144">For more information about Windows PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="2223a-145">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2223a-145">RELATED LINKS</span></span>

[<span data-ttu-id="2223a-146">New-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="2223a-146">New-IseSnippet</span></span>](New-IseSnippet.md)

[<span data-ttu-id="2223a-147">Importera – IseSnippet</span><span class="sxs-lookup"><span data-stu-id="2223a-147">Import-IseSnippet</span></span>](Import-IseSnippet.md)
