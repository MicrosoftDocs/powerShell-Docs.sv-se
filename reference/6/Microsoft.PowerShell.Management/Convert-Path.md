---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/convert-path?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-Path
ms.openlocfilehash: c7ab1143b406af08c921d2ce27c5c60470b2f11e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264002"
---
# <span data-ttu-id="7f129-103">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="7f129-103">Convert-Path</span></span>

## <span data-ttu-id="7f129-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7f129-104">SYNOPSIS</span></span>
<span data-ttu-id="7f129-105">Konverterar en sökväg från en PowerShell-sökväg till en PowerShell-providerns sökväg.</span><span class="sxs-lookup"><span data-stu-id="7f129-105">Converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="7f129-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7f129-106">SYNTAX</span></span>

### <span data-ttu-id="7f129-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="7f129-107">Path (Default)</span></span>

```
Convert-Path [-Path] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="7f129-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7f129-108">LiteralPath</span></span>

```
Convert-Path -LiteralPath <String[]> [<CommonParameters>]
```

## <span data-ttu-id="7f129-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7f129-109">DESCRIPTION</span></span>

<span data-ttu-id="7f129-110">`Convert-Path`Cmdleten konverterar en sökväg från en PowerShell-sökväg till en PowerShell-providerns sökväg.</span><span class="sxs-lookup"><span data-stu-id="7f129-110">The `Convert-Path` cmdlet converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="7f129-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7f129-111">EXAMPLES</span></span>

### <span data-ttu-id="7f129-112">Exempel 1: konvertera arbets katalogen till en standard fil system Sök väg</span><span class="sxs-lookup"><span data-stu-id="7f129-112">Example 1: Convert the working directory to a standard file system path</span></span>

<span data-ttu-id="7f129-113">I det här exemplet konverteras den aktuella arbets katalogen, som representeras av en punkt ( `.` ), till en standard fil Sök väg.</span><span class="sxs-lookup"><span data-stu-id="7f129-113">This example converts the current working directory, which is represented by a dot (`.`), to a standard FileSystem path.</span></span>

```
PS C:\> Convert-Path .
C:\
```

### <span data-ttu-id="7f129-114">Exempel 2: konvertera en provider-sökväg till en standard register Sök väg</span><span class="sxs-lookup"><span data-stu-id="7f129-114">Example 2: Convert a provider path to a standard registry path</span></span>

<span data-ttu-id="7f129-115">I det här exemplet konverteras PowerShell-providerns sökväg till en standard register Sök väg.</span><span class="sxs-lookup"><span data-stu-id="7f129-115">This example converts the PowerShell provider path to a standard registry path.</span></span>

```powershell
PS C:\> Convert-Path HKLM:\Software\Microsoft
HKEY_LOCAL_MACHINE\Software\Microsoft
```

### <span data-ttu-id="7f129-116">Exempel 3: konvertera en sökväg till en sträng</span><span class="sxs-lookup"><span data-stu-id="7f129-116">Example 3: Convert a path to a string</span></span>

<span data-ttu-id="7f129-117">I det här exemplet konverteras sökvägen till den aktuella providerns Hem Katalog, vilket är fil Systems leverantören, till en sträng.</span><span class="sxs-lookup"><span data-stu-id="7f129-117">This example converts the path to the home directory of the current provider, which is the FileSystem provider, to a string.</span></span>

```powershell
PS C:\> Convert-Path ~
C:\Users\User01
```

## <span data-ttu-id="7f129-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7f129-118">PARAMETERS</span></span>

### <span data-ttu-id="7f129-119">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7f129-119">-LiteralPath</span></span>

<span data-ttu-id="7f129-120">Anger, som en sträng mat ris, den sökväg som ska konverteras.</span><span class="sxs-lookup"><span data-stu-id="7f129-120">Specifies, as a string array, the path to be converted.</span></span> <span data-ttu-id="7f129-121">Värdet för parametern **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="7f129-121">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="7f129-122">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="7f129-122">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="7f129-123">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="7f129-123">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="7f129-124">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="7f129-124">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7f129-125">-Path</span><span class="sxs-lookup"><span data-stu-id="7f129-125">-Path</span></span>

<span data-ttu-id="7f129-126">Anger den PowerShell-sökväg som ska konverteras.</span><span class="sxs-lookup"><span data-stu-id="7f129-126">Specifies the PowerShell path to be converted.</span></span>

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

### <span data-ttu-id="7f129-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7f129-127">CommonParameters</span></span>

<span data-ttu-id="7f129-128">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7f129-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7f129-129">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7f129-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7f129-130">INDATA</span><span class="sxs-lookup"><span data-stu-id="7f129-130">INPUTS</span></span>

### <span data-ttu-id="7f129-131">System. String</span><span class="sxs-lookup"><span data-stu-id="7f129-131">System.String</span></span>

<span data-ttu-id="7f129-132">Du kan skicka en sökväg, men inte en literal sökväg, till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7f129-132">You can pipe a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="7f129-133">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7f129-133">OUTPUTS</span></span>

### <span data-ttu-id="7f129-134">System. String</span><span class="sxs-lookup"><span data-stu-id="7f129-134">System.String</span></span>

<span data-ttu-id="7f129-135">Den här cmdleten returnerar en sträng som innehåller den konverterade sökvägen.</span><span class="sxs-lookup"><span data-stu-id="7f129-135">This cmdlet returns a string that contains the converted path.</span></span>

## <span data-ttu-id="7f129-136">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7f129-136">NOTES</span></span>

<span data-ttu-id="7f129-137">Cmdlet: arna som innehåller sökvägen Substantiv ändrar Sök vägs namn och returnerar namnen i ett koncist format som alla PowerShell-leverantörer kan tolka.</span><span class="sxs-lookup"><span data-stu-id="7f129-137">The cmdlets that contain the Path noun manipulate path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="7f129-138">De är utformade för användning i program och skript där du vill visa hela eller delar av ett Sök vägs namn i ett visst format.</span><span class="sxs-lookup"><span data-stu-id="7f129-138">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="7f129-139">Använd dem på samma sätt som du använder **logsdirectory** , **Normpath** , **realpath** , **Join** eller andra Sök vägs manipulerare.</span><span class="sxs-lookup"><span data-stu-id="7f129-139">Use them like you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

<span data-ttu-id="7f129-140">Du kan använda Sök vägs-cmdlet: ar med flera providers, inklusive fil systemet system, register och certifikat leverantörer.</span><span class="sxs-lookup"><span data-stu-id="7f129-140">You can use the path cmdlets with several providers, including the FileSystem, Registry, and Certificate providers.</span></span>

<span data-ttu-id="7f129-141">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="7f129-141">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="7f129-142">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="7f129-142">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="7f129-143">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="7f129-143">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="7f129-144">`Convert-Path` konverterar bara befintliga sökvägar.</span><span class="sxs-lookup"><span data-stu-id="7f129-144">`Convert-Path` only converts existing paths.</span></span> <span data-ttu-id="7f129-145">Den kan inte användas för att konvertera en plats som ännu inte finns.</span><span class="sxs-lookup"><span data-stu-id="7f129-145">It cannot be used to convert a location that does not exist yet.</span></span>

## <span data-ttu-id="7f129-146">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7f129-146">RELATED LINKS</span></span>

[<span data-ttu-id="7f129-147">Anslut till sökväg</span><span class="sxs-lookup"><span data-stu-id="7f129-147">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="7f129-148">Lös-sökväg</span><span class="sxs-lookup"><span data-stu-id="7f129-148">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="7f129-149">Dela-sökväg</span><span class="sxs-lookup"><span data-stu-id="7f129-149">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="7f129-150">Test-sökväg</span><span class="sxs-lookup"><span data-stu-id="7f129-150">Test-Path</span></span>](Test-Path.md)

[<span data-ttu-id="7f129-151">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="7f129-151">Get-PSProvider</span></span>](Get-PSProvider.md)
