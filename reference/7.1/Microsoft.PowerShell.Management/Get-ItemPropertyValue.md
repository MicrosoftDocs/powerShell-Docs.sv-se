---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itempropertyvalue?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemPropertyValue
ms.openlocfilehash: 96fc9ce21b320710181fe97b6a47edbab8cc65a1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266493"
---
# <span data-ttu-id="d144e-103">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="d144e-103">Get-ItemPropertyValue</span></span>

## <span data-ttu-id="d144e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="d144e-104">SYNOPSIS</span></span>
<span data-ttu-id="d144e-105">Hämtar värdet för en eller flera egenskaper för ett angivet objekt.</span><span class="sxs-lookup"><span data-stu-id="d144e-105">Gets the value for one or more properties of a specified item.</span></span>

## <span data-ttu-id="d144e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d144e-106">SYNTAX</span></span>

### <span data-ttu-id="d144e-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="d144e-107">Path (Default)</span></span>

```
Get-ItemPropertyValue [[-Path] <String[]>] [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="d144e-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d144e-108">LiteralPath</span></span>

```
Get-ItemPropertyValue -LiteralPath <String[]> [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="d144e-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d144e-109">DESCRIPTION</span></span>

<span data-ttu-id="d144e-110">`Get-ItemPropertyValue`Hämtar det aktuella värdet för en egenskap som du anger när du använder parametern *Name* , som finns i en sökväg som du anger med antingen *sökvägen* eller *LiteralPath* -parametrarna.</span><span class="sxs-lookup"><span data-stu-id="d144e-110">The `Get-ItemPropertyValue` gets the current value for a property that you specify when you use the *Name* parameter, located in a path that you specify with either the *Path* or *LiteralPath* parameters.</span></span>

## <span data-ttu-id="d144e-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="d144e-111">EXAMPLES</span></span>

### <span data-ttu-id="d144e-112">Exempel 1: Hämta värdet för egenskapen ProductID</span><span class="sxs-lookup"><span data-stu-id="d144e-112">Example 1: Get the value of the ProductID property</span></span>

<span data-ttu-id="d144e-113">Det här kommandot hämtar värdet för egenskapen **ProductID** för objektet "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" i Windows Registry-providern.</span><span class="sxs-lookup"><span data-stu-id="d144e-113">This command gets the value of the **ProductID** property of the "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" object in the Windows Registry provider.</span></span>

```powershell
Get-ItemPropertyValue 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion' -Name ProductID
```

```output
94253-50000-11141-AA785
```

### <span data-ttu-id="d144e-114">Exempel 2: hämta den senaste skrivnings tiden för en fil eller mapp</span><span class="sxs-lookup"><span data-stu-id="d144e-114">Example 2: Get the last write time of a file or folder</span></span>

<span data-ttu-id="d144e-115">Detta kommando hämtar värdet för egenskapen **LastWriteTime** , eller när en fil eller mapp senast ändrades, från mappen "C:\Users\Test\Documents\ModuleToAssembly", som arbetar i fil namns leverantören.</span><span class="sxs-lookup"><span data-stu-id="d144e-115">This command gets the value of the **LastWriteTime** property, or the last time a file or folder was changed, from the "C:\Users\Test\Documents\ModuleToAssembly" folder, working in the FileSystem provider.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime
```

```output
Wednesday, September 3, 2014 2:53:22 PM
```

### <span data-ttu-id="d144e-116">Exempel 3: Hämta flera egenskaps värden för en fil eller mapp</span><span class="sxs-lookup"><span data-stu-id="d144e-116">Example 3: Get multiple property values of a file or folder</span></span>

<span data-ttu-id="d144e-117">Det här kommandot hämtar värdena för **LastWriteTime** , **CreationTime** och **rot** egenskaper för en mapp.</span><span class="sxs-lookup"><span data-stu-id="d144e-117">This command gets the values of the **LastWriteTime** , **CreationTime** , and **Root** properties of a folder.</span></span> <span data-ttu-id="d144e-118">Egenskaps värden returneras i den ordning som du har angett egenskaps namnen.</span><span class="sxs-lookup"><span data-stu-id="d144e-118">The property values are returned in the order in which you specified the property names.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime,CreationTime,Root
```

```output
Wednesday, September 3, 2014 2:53:22 PM
Wednesday, September 3, 2014 2:53:10 PM

Name              : C:\
Parent            :
Exists            : True
Root              : C:\
FullName          : C:\
Extension         :
CreationTime      : 9/1/2014 4:59:45 AM
CreationTimeUtc   : 9/1/2014 11:59:45 AM
LastAccessTime    : 9/27/2014 5:22:02 PM
LastAccessTimeUtc : 9/28/2014 12:22:02 AM
LastWriteTime     : 9/27/2014 5:22:02 PM
LastWriteTimeUtc  : 9/28/2014 12:22:02 AM
Attributes        : Hidden, System, Directory
BaseName          : C:\
Target            :
LinkType          :
Mode              : d--hs-
```

## <span data-ttu-id="d144e-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="d144e-119">PARAMETERS</span></span>

### <span data-ttu-id="d144e-120">-Credential</span><span class="sxs-lookup"><span data-stu-id="d144e-120">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="d144e-121">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d144e-121">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="d144e-122">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="d144e-122">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d144e-123">-Undanta</span><span class="sxs-lookup"><span data-stu-id="d144e-123">-Exclude</span></span>

<span data-ttu-id="d144e-124">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="d144e-124">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="d144e-125">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="d144e-125">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="d144e-126">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="d144e-126">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="d144e-127">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="d144e-127">Wildcard characters are permitted.</span></span> <span data-ttu-id="d144e-128">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="d144e-128">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="d144e-129">-Filter</span><span class="sxs-lookup"><span data-stu-id="d144e-129">-Filter</span></span>

<span data-ttu-id="d144e-130">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="d144e-130">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="d144e-131">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="d144e-131">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="d144e-132">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="d144e-132">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="d144e-133">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="d144e-133">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="d144e-134">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="d144e-134">-Include</span></span>

<span data-ttu-id="d144e-135">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="d144e-135">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="d144e-136">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="d144e-136">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="d144e-137">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="d144e-137">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="d144e-138">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="d144e-138">Wildcard characters are permitted.</span></span> <span data-ttu-id="d144e-139">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="d144e-139">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="d144e-140">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d144e-140">-LiteralPath</span></span>

<span data-ttu-id="d144e-141">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="d144e-141">Specifies a path to one or more locations.</span></span> <span data-ttu-id="d144e-142">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="d144e-142">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="d144e-143">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="d144e-143">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="d144e-144">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="d144e-144">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="d144e-145">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="d144e-145">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="d144e-146">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="d144e-146">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="d144e-147">-Name</span><span class="sxs-lookup"><span data-stu-id="d144e-147">-Name</span></span>

<span data-ttu-id="d144e-148">Anger namnet på egenskapen eller egenskaperna som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="d144e-148">Specifies the name of the property or properties to retrieve.</span></span>
<span data-ttu-id="d144e-149">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="d144e-149">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="d144e-150">-Path</span><span class="sxs-lookup"><span data-stu-id="d144e-150">-Path</span></span>

<span data-ttu-id="d144e-151">Anger sökvägen till objektet eller objekten.</span><span class="sxs-lookup"><span data-stu-id="d144e-151">Specifies the path to the item or items.</span></span>
<span data-ttu-id="d144e-152">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="d144e-152">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="d144e-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d144e-153">CommonParameters</span></span>

<span data-ttu-id="d144e-154">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="d144e-154">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="d144e-155">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="d144e-155">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="d144e-156">INDATA</span><span class="sxs-lookup"><span data-stu-id="d144e-156">INPUTS</span></span>

### <span data-ttu-id="d144e-157">System. String</span><span class="sxs-lookup"><span data-stu-id="d144e-157">System.String</span></span>

<span data-ttu-id="d144e-158">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d144e-158">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="d144e-159">UTDATA</span><span class="sxs-lookup"><span data-stu-id="d144e-159">OUTPUTS</span></span>

### <span data-ttu-id="d144e-160">System. Boolean, system. String, system. DateTime</span><span class="sxs-lookup"><span data-stu-id="d144e-160">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="d144e-161">Den här cmdleten returnerar ett objekt för varje objekt egenskaps värde som det får.</span><span class="sxs-lookup"><span data-stu-id="d144e-161">This cmdlet returns an object for each item property value that it gets.</span></span>
<span data-ttu-id="d144e-162">Objekt typen beror på egenskap svärdet som hämtades.</span><span class="sxs-lookup"><span data-stu-id="d144e-162">The object type depends on the property value that is retrieved.</span></span>
<span data-ttu-id="d144e-163">I en fil system enhet kan exempelvis cmdlet: en returnera en fil eller mapp.</span><span class="sxs-lookup"><span data-stu-id="d144e-163">For example, in a file system drive, the cmdlet might return a file or folder.</span></span>

## <span data-ttu-id="d144e-164">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="d144e-164">NOTES</span></span>

<span data-ttu-id="d144e-165">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="d144e-165">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="d144e-166">Om du vill visa en lista över tillgängliga providers i sessionen kör du `Get-PSProvider` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d144e-166">To list the providers available in your session, run the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="d144e-167">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="d144e-167">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="d144e-168">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="d144e-168">RELATED LINKS</span></span>

[<span data-ttu-id="d144e-169">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d144e-169">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="d144e-170">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d144e-170">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="d144e-171">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d144e-171">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="d144e-172">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="d144e-172">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="d144e-173">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d144e-173">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="d144e-174">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d144e-174">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="d144e-175">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d144e-175">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="d144e-176">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d144e-176">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="d144e-177">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d144e-177">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="d144e-178">about_Providers</span><span class="sxs-lookup"><span data-stu-id="d144e-178">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

