---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/convert-path?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-Path
ms.openlocfilehash: a442d8ff9f021e1ec05671d9190d35ef97ff4d72
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266217"
---
# <span data-ttu-id="aad62-103">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="aad62-103">Convert-Path</span></span>

## <span data-ttu-id="aad62-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="aad62-104">SYNOPSIS</span></span>
<span data-ttu-id="aad62-105">Konverterar en sökväg från en PowerShell-sökväg till en PowerShell-providerns sökväg.</span><span class="sxs-lookup"><span data-stu-id="aad62-105">Converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="aad62-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aad62-106">SYNTAX</span></span>

### <span data-ttu-id="aad62-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="aad62-107">Path (Default)</span></span>

```
Convert-Path [-Path] <String[]> [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="aad62-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="aad62-108">LiteralPath</span></span>

```
Convert-Path -LiteralPath <String[]> [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="aad62-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="aad62-109">DESCRIPTION</span></span>

<span data-ttu-id="aad62-110">`Convert-Path`Cmdleten konverterar en sökväg från en PowerShell-sökväg till en PowerShell-providerns sökväg.</span><span class="sxs-lookup"><span data-stu-id="aad62-110">The `Convert-Path` cmdlet converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="aad62-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="aad62-111">EXAMPLES</span></span>

### <span data-ttu-id="aad62-112">Exempel 1: konvertera arbets katalogen till en standard fil system Sök väg</span><span class="sxs-lookup"><span data-stu-id="aad62-112">Example 1: Convert the working directory to a standard file system path</span></span>

<span data-ttu-id="aad62-113">I det här exemplet konverteras den aktuella arbets katalogen, som representeras av en punkt ( `.` ), till en standard fil Sök väg.</span><span class="sxs-lookup"><span data-stu-id="aad62-113">This example converts the current working directory, which is represented by a dot (`.`), to a standard FileSystem path.</span></span>

```
PS C:\> Convert-Path .
C:\
```

### <span data-ttu-id="aad62-114">Exempel 2: konvertera en provider-sökväg till en standard register Sök väg</span><span class="sxs-lookup"><span data-stu-id="aad62-114">Example 2: Convert a provider path to a standard registry path</span></span>

<span data-ttu-id="aad62-115">I det här exemplet konverteras PowerShell-providerns sökväg till en standard register Sök väg.</span><span class="sxs-lookup"><span data-stu-id="aad62-115">This example converts the PowerShell provider path to a standard registry path.</span></span>

```powershell
PS C:\> Convert-Path HKLM:\Software\Microsoft
HKEY_LOCAL_MACHINE\Software\Microsoft
```

### <span data-ttu-id="aad62-116">Exempel 3: konvertera en sökväg till en sträng</span><span class="sxs-lookup"><span data-stu-id="aad62-116">Example 3: Convert a path to a string</span></span>

<span data-ttu-id="aad62-117">I det här exemplet konverteras sökvägen till den aktuella providerns Hem Katalog, vilket är fil Systems leverantören, till en sträng.</span><span class="sxs-lookup"><span data-stu-id="aad62-117">This example converts the path to the home directory of the current provider, which is the FileSystem provider, to a string.</span></span>

```powershell
PS C:\> Convert-Path ~
C:\Users\User01
```

## <span data-ttu-id="aad62-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="aad62-118">PARAMETERS</span></span>

### <span data-ttu-id="aad62-119">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="aad62-119">-LiteralPath</span></span>

<span data-ttu-id="aad62-120">Anger, som en sträng mat ris, den sökväg som ska konverteras.</span><span class="sxs-lookup"><span data-stu-id="aad62-120">Specifies, as a string array, the path to be converted.</span></span> <span data-ttu-id="aad62-121">Värdet för parametern **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="aad62-121">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="aad62-122">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="aad62-122">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="aad62-123">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="aad62-123">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="aad62-124">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="aad62-124">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aad62-125">-Path</span><span class="sxs-lookup"><span data-stu-id="aad62-125">-Path</span></span>

<span data-ttu-id="aad62-126">Anger den PowerShell-sökväg som ska konverteras.</span><span class="sxs-lookup"><span data-stu-id="aad62-126">Specifies the PowerShell path to be converted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="aad62-127">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="aad62-127">-UseTransaction</span></span>
<span data-ttu-id="aad62-128">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="aad62-128">Includes the command in the active transaction.</span></span>
<span data-ttu-id="aad62-129">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="aad62-129">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="aad62-130">Mer information finns i about_transactions.</span><span class="sxs-lookup"><span data-stu-id="aad62-130">For more information, see about_transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aad62-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aad62-131">CommonParameters</span></span>

<span data-ttu-id="aad62-132">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aad62-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aad62-133">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="aad62-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aad62-134">INDATA</span><span class="sxs-lookup"><span data-stu-id="aad62-134">INPUTS</span></span>

### <span data-ttu-id="aad62-135">System. String</span><span class="sxs-lookup"><span data-stu-id="aad62-135">System.String</span></span>

<span data-ttu-id="aad62-136">Du kan skicka en sökväg, men inte en literal sökväg, till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aad62-136">You can pipe a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="aad62-137">UTDATA</span><span class="sxs-lookup"><span data-stu-id="aad62-137">OUTPUTS</span></span>

### <span data-ttu-id="aad62-138">System. String</span><span class="sxs-lookup"><span data-stu-id="aad62-138">System.String</span></span>

<span data-ttu-id="aad62-139">Den här cmdleten returnerar en sträng som innehåller den konverterade sökvägen.</span><span class="sxs-lookup"><span data-stu-id="aad62-139">This cmdlet returns a string that contains the converted path.</span></span>

## <span data-ttu-id="aad62-140">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="aad62-140">NOTES</span></span>

<span data-ttu-id="aad62-141">Cmdlet: arna som innehåller sökvägen Substantiv ändrar Sök vägs namn och returnerar namnen i ett koncist format som alla PowerShell-leverantörer kan tolka.</span><span class="sxs-lookup"><span data-stu-id="aad62-141">The cmdlets that contain the Path noun manipulate path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="aad62-142">De är utformade för användning i program och skript där du vill visa hela eller delar av ett Sök vägs namn i ett visst format.</span><span class="sxs-lookup"><span data-stu-id="aad62-142">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="aad62-143">Använd dem på samma sätt som du använder **logsdirectory** , **Normpath** , **realpath** , **Join** eller andra Sök vägs manipulerare.</span><span class="sxs-lookup"><span data-stu-id="aad62-143">Use them like you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

<span data-ttu-id="aad62-144">Du kan använda Sök vägs-cmdlet: ar med flera providers, inklusive fil systemet system, register och certifikat leverantörer.</span><span class="sxs-lookup"><span data-stu-id="aad62-144">You can use the path cmdlets with several providers, including the FileSystem, Registry, and Certificate providers.</span></span>

<span data-ttu-id="aad62-145">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="aad62-145">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="aad62-146">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="aad62-146">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="aad62-147">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="aad62-147">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="aad62-148">`Convert-Path` konverterar bara befintliga sökvägar.</span><span class="sxs-lookup"><span data-stu-id="aad62-148">`Convert-Path` only converts existing paths.</span></span> <span data-ttu-id="aad62-149">Den kan inte användas för att konvertera en plats som ännu inte finns.</span><span class="sxs-lookup"><span data-stu-id="aad62-149">It cannot be used to convert a location that does not exist yet.</span></span>

## <span data-ttu-id="aad62-150">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="aad62-150">RELATED LINKS</span></span>

[<span data-ttu-id="aad62-151">Anslut till sökväg</span><span class="sxs-lookup"><span data-stu-id="aad62-151">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="aad62-152">Lös-sökväg</span><span class="sxs-lookup"><span data-stu-id="aad62-152">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="aad62-153">Dela-sökväg</span><span class="sxs-lookup"><span data-stu-id="aad62-153">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="aad62-154">Test-sökväg</span><span class="sxs-lookup"><span data-stu-id="aad62-154">Test-Path</span></span>](Test-Path.md)

[<span data-ttu-id="aad62-155">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="aad62-155">Get-PSProvider</span></span>](Get-PSProvider.md)
