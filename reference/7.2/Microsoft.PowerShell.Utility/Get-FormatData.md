---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FormatData
ms.openlocfilehash: 28eab1709de12ec5d391009aacccfd4e973a8b9b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708659"
---
# <span data-ttu-id="12868-102">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="12868-102">Get-FormatData</span></span>

## <span data-ttu-id="12868-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="12868-103">SYNOPSIS</span></span>
<span data-ttu-id="12868-104">Hämtar formaterings data i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="12868-104">Gets the formatting data in the current session.</span></span>

## <span data-ttu-id="12868-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="12868-105">SYNTAX</span></span>

```
Get-FormatData [[-TypeName] <String[]>] [-PowerShellVersion <Version>] [<CommonParameters>]
```

## <span data-ttu-id="12868-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="12868-106">DESCRIPTION</span></span>

<span data-ttu-id="12868-107">`Get-FormatData`Cmdleten hämtar formateringen i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="12868-107">The `Get-FormatData` cmdlet gets the formatting data in the current session.</span></span>

<span data-ttu-id="12868-108">Formateringen i sessionen innehåller formatering av data från `Format.ps1xml` filer, till exempel i `$PSHOME` katalogen, formatering av data för moduler som du importerar till sessionen och hur du formaterar data för kommandon som du importerar i sessionen med hjälp av `Import-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="12868-108">The formatting data in the session includes formatting data from `Format.ps1xml` formatting files, such as those in the `$PSHOME` directory, formatting data for modules that you import into the session, and formatting data for commands that you import into your session by using the `Import-PSSession` cmdlet.</span></span>

<span data-ttu-id="12868-109">Du kan använda den här cmdleten för att undersöka formaterings data.</span><span class="sxs-lookup"><span data-stu-id="12868-109">You can use this cmdlet to examine the formatting data.</span></span> <span data-ttu-id="12868-110">Sedan kan du använda `Export-FormatData` cmdleten för att serialisera objekten, konvertera dem till XML och spara dem i `Format.ps1xml` filer.</span><span class="sxs-lookup"><span data-stu-id="12868-110">Then, you can use the `Export-FormatData` cmdlet to serialize the objects, convert them to XML, and save them in `Format.ps1xml` files.</span></span>

<span data-ttu-id="12868-111">Mer information om hur du formaterar filer i PowerShell finns i [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="12868-111">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="12868-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="12868-112">EXAMPLES</span></span>

### <span data-ttu-id="12868-113">Exempel 1: Hämta alla format data</span><span class="sxs-lookup"><span data-stu-id="12868-113">Example 1: Get all formatting data</span></span>

<span data-ttu-id="12868-114">Det här exemplet hämtar alla formaterings data i sessionen.</span><span class="sxs-lookup"><span data-stu-id="12868-114">This example gets all the formatting data in the session.</span></span>

```powershell
Get-FormatData
```

### <span data-ttu-id="12868-115">Exempel 2: Hämta formatering av data efter typnamn</span><span class="sxs-lookup"><span data-stu-id="12868-115">Example 2: Get formatting data by type name</span></span>

<span data-ttu-id="12868-116">Det här exemplet hämtar de format data objekt vars namn börjar med `System.Management.Automation.Cmd` .</span><span class="sxs-lookup"><span data-stu-id="12868-116">This example gets the formatting data items whose names begin with `System.Management.Automation.Cmd`.</span></span>

```powershell
Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
```

### <span data-ttu-id="12868-117">Exempel 3: granska formatering av data objekt</span><span class="sxs-lookup"><span data-stu-id="12868-117">Example 3: Examine a formatting data object</span></span>

<span data-ttu-id="12868-118">Det här exemplet visar hur du hämtar ett formaterat data objekt och granskar dess egenskaper.</span><span class="sxs-lookup"><span data-stu-id="12868-118">This example shows how to get a formatting data object and examine its properties.</span></span>

```powershell
$F = Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
$F
```

```Output
TypeName        FormatViewDefinition
--------        --------------------
HelpInfoShort   {help , TableControl}
```

```powershell
$F.FormatViewDefinition[0].control
```

```Output
Headers          : {System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader}
Rows             : {System.Management.Automation.TableControlRow}
AutoSize         : False
HideTableHeaders : False
GroupBy          :
OutOfBand        : False
```

```powershell
$F.FormatViewDefinition[0].control.Headers
```

```Output
Label       Alignment Width
-----       --------- -----
CommandType Undefined    15
Name        Undefined    50
Version     Undefined    10
Source      Undefined     0
```

### <span data-ttu-id="12868-119">Exempel 4: Hämta formatering av data och exportera dem</span><span class="sxs-lookup"><span data-stu-id="12868-119">Example 4: Get formatting data and export it</span></span>

<span data-ttu-id="12868-120">Det här exemplet visar hur du använder `Get-FormatData` och `Export-FormatData` för att exportera de format data som läggs till av en modul.</span><span class="sxs-lookup"><span data-stu-id="12868-120">This example shows how to use `Get-FormatData` and `Export-FormatData` to export the formatting data that is added by a module.</span></span>

```powershell
$A = Get-FormatData
Import-Module bitstransfer
$B = Get-FormatData
Compare-Object $A $B
```

```Output
InputObject                                                SideIndicator
-----------                                                -------------
Microsoft.BackgroundIntelligentTransfer.Management.BitsJob =>
```

```powershell
Get-FormatData *bits* | Export-FormatData -FilePath c:\test\bits.format.ps1xml
Get-Content c:\test\bits.format.ps1xml
```

```Output
<?xml version="1.0" encoding="utf-8"?><Configuration><ViewDefinitions>
<View><Name>Microsoft.BackgroundIntelligentTransfer.Management.BitsJob</Name>
...
```

<span data-ttu-id="12868-121">De första fyra kommandona använder `Get-FormatData` `Import-Module` `Compare-Object` cmdletarna, och för att identifiera den format typ som **BitsTransfer** -modulen lägger till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="12868-121">The first four commands use the `Get-FormatData`, `Import-Module`, and `Compare-Object` cmdlets to identify the format type that the **BitsTransfer** module adds to the session.</span></span>

<span data-ttu-id="12868-122">Det femte kommandot använder `Get-FormatData` cmdleten för att hämta den format typ som **BitsTransfer** -modulen lägger till.</span><span class="sxs-lookup"><span data-stu-id="12868-122">The fifth command uses the `Get-FormatData` cmdlet to get the format type that the **BitsTransfer** module adds.</span></span> <span data-ttu-id="12868-123">Den använder en pipeline-operator ( `|` ) för att skicka format typs objektet till `Export-FormatData` cmdleten, vilket konverterar tillbaka det till XML och sparar det i den angivna `format.ps1xml` filen.</span><span class="sxs-lookup"><span data-stu-id="12868-123">It uses a pipeline operator (`|`) to send the format type object to the `Export-FormatData` cmdlet, which converts it back to XML and saves it in the specified `format.ps1xml` file.</span></span>

<span data-ttu-id="12868-124">Det sista kommandot visar ett utdrag av `format.ps1xml` fil innehållet.</span><span class="sxs-lookup"><span data-stu-id="12868-124">The final command shows an excerpt of the `format.ps1xml` file content.</span></span>

### <span data-ttu-id="12868-125">Exempel 5: Hämta formatering av data baserat på den angivna versionen av PowerShell</span><span class="sxs-lookup"><span data-stu-id="12868-125">Example 5: Get formatting data based on the specified version of PowerShell</span></span>

<span data-ttu-id="12868-126">Det här exemplet visar hur du kan använda `Get-FormatData` för att hämta format data för ett angivet **TypeName** och en PowerShell-version.</span><span class="sxs-lookup"><span data-stu-id="12868-126">This example shows how to use `Get-FormatData` to get format data for a specified **TypeName** and PowerShell version.</span></span>

```powershell
Get-FormatData -TypeName 'Microsoft.Powershell.Utility.FileHash' -PowerShellVersion $PSVersionTable.PSVersion

TypeNames                               FormatViewDefinition
---------                               --------------------
{Microsoft.Powershell.Utility.FileHash} {Microsoft.Powershell.Utility.FileHash}
```

## <span data-ttu-id="12868-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="12868-127">PARAMETERS</span></span>

### <span data-ttu-id="12868-128">– PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="12868-128">-PowerShellVersion</span></span>

<span data-ttu-id="12868-129">Ange den version av PowerShell som denna cmdlet hämtar för att formatera data.</span><span class="sxs-lookup"><span data-stu-id="12868-129">Specify the version of PowerShell this cmdlet gets for the formatting data.</span></span> <span data-ttu-id="12868-130">Ange ett tvåsiffrigt tal avgränsat med en punkt.</span><span class="sxs-lookup"><span data-stu-id="12868-130">Enter a two digit number separated by a period.</span></span>

<span data-ttu-id="12868-131">Den här parametern lades till i PowerShell 5,1 för att förbättra kompatibiliteten när fjärrdatorer som kör äldre versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="12868-131">This parameter was added in PowerShell 5.1 to improve compatibility when remoting computers running older versions of PowerShell.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12868-132">-TypeName</span><span class="sxs-lookup"><span data-stu-id="12868-132">-TypeName</span></span>

<span data-ttu-id="12868-133">Anger typ namnen som denna cmdlet hämtar för att formatera data.</span><span class="sxs-lookup"><span data-stu-id="12868-133">Specifies the type names that this cmdlet gets for the formatting data.</span></span>
<span data-ttu-id="12868-134">Ange typ namn.</span><span class="sxs-lookup"><span data-stu-id="12868-134">Enter the type names.</span></span>
<span data-ttu-id="12868-135">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="12868-135">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="12868-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12868-136">CommonParameters</span></span>

<span data-ttu-id="12868-137">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="12868-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12868-138">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="12868-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="12868-139">INDATA</span><span class="sxs-lookup"><span data-stu-id="12868-139">INPUTS</span></span>

### <span data-ttu-id="12868-140">Inga</span><span class="sxs-lookup"><span data-stu-id="12868-140">None</span></span>

<span data-ttu-id="12868-141">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="12868-141">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="12868-142">UTDATA</span><span class="sxs-lookup"><span data-stu-id="12868-142">OUTPUTS</span></span>

### <span data-ttu-id="12868-143">System. Management. Automation. ExtendedTypeDefinition</span><span class="sxs-lookup"><span data-stu-id="12868-143">System.Management.Automation.ExtendedTypeDefinition</span></span>

## <span data-ttu-id="12868-144">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="12868-144">NOTES</span></span>

## <span data-ttu-id="12868-145">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="12868-145">RELATED LINKS</span></span>

[<span data-ttu-id="12868-146">Exportera – FormatData</span><span class="sxs-lookup"><span data-stu-id="12868-146">Export-FormatData</span></span>](Export-FormatData.md)

[<span data-ttu-id="12868-147">Uppdatera – FormatData</span><span class="sxs-lookup"><span data-stu-id="12868-147">Update-FormatData</span></span>](Update-FormatData.md)
