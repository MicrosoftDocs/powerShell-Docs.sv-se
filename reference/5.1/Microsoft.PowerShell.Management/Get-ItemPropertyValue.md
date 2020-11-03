---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itempropertyvalue?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemPropertyValue
ms.openlocfilehash: 2dbbbfeac3810f79b976b6a68ab3089e91707fb3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266121"
---
# <span data-ttu-id="8c2c2-103">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="8c2c2-103">Get-ItemPropertyValue</span></span>

## <span data-ttu-id="8c2c2-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8c2c2-104">SYNOPSIS</span></span>
<span data-ttu-id="8c2c2-105">Hämtar värdet för en eller flera egenskaper för ett angivet objekt.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-105">Gets the value for one or more properties of a specified item.</span></span>

## <span data-ttu-id="8c2c2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8c2c2-106">SYNTAX</span></span>

### <span data-ttu-id="8c2c2-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="8c2c2-107">Path (Default)</span></span>

```
Get-ItemPropertyValue [[-Path] <String[]>] [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="8c2c2-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8c2c2-108">LiteralPath</span></span>

```
Get-ItemPropertyValue -LiteralPath <String[]> [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="8c2c2-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8c2c2-109">DESCRIPTION</span></span>

<span data-ttu-id="8c2c2-110">`Get-ItemPropertyValue`Hämtar det aktuella värdet för en egenskap som du anger när du använder parametern *Name* , som finns i en sökväg som du anger med antingen *sökvägen* eller *LiteralPath* -parametrarna.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-110">The `Get-ItemPropertyValue` gets the current value for a property that you specify when you use the *Name* parameter, located in a path that you specify with either the *Path* or *LiteralPath* parameters.</span></span>

## <span data-ttu-id="8c2c2-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8c2c2-111">EXAMPLES</span></span>

### <span data-ttu-id="8c2c2-112">Exempel 1: Hämta värdet för egenskapen ProductID</span><span class="sxs-lookup"><span data-stu-id="8c2c2-112">Example 1: Get the value of the ProductID property</span></span>

<span data-ttu-id="8c2c2-113">Det här kommandot hämtar värdet för egenskapen **ProductID** för objektet "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" i Windows Registry-providern.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-113">This command gets the value of the **ProductID** property of the "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" object in the Windows Registry provider.</span></span>

```powershell
Get-ItemPropertyValue 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion' -Name ProductID
```

```output
94253-50000-11141-AA785
```

### <span data-ttu-id="8c2c2-114">Exempel 2: hämta den senaste skrivnings tiden för en fil eller mapp</span><span class="sxs-lookup"><span data-stu-id="8c2c2-114">Example 2: Get the last write time of a file or folder</span></span>

<span data-ttu-id="8c2c2-115">Detta kommando hämtar värdet för egenskapen **LastWriteTime** , eller när en fil eller mapp senast ändrades, från mappen "C:\Users\Test\Documents\ModuleToAssembly", som arbetar i fil namns leverantören.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-115">This command gets the value of the **LastWriteTime** property, or the last time a file or folder was changed, from the "C:\Users\Test\Documents\ModuleToAssembly" folder, working in the FileSystem provider.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime
```

```output
Wednesday, September 3, 2014 2:53:22 PM
```

### <span data-ttu-id="8c2c2-116">Exempel 3: Hämta flera egenskaps värden för en fil eller mapp</span><span class="sxs-lookup"><span data-stu-id="8c2c2-116">Example 3: Get multiple property values of a file or folder</span></span>

<span data-ttu-id="8c2c2-117">Det här kommandot hämtar värdena för **LastWriteTime** , **CreationTime** och **rot** egenskaper för en mapp.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-117">This command gets the values of the **LastWriteTime** , **CreationTime** , and **Root** properties of a folder.</span></span>
<span data-ttu-id="8c2c2-118">Egenskaps värden returneras i den ordning som du har angett egenskaps namnen.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-118">The property values are returned in the order in which you specified the property names.</span></span>

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

## <span data-ttu-id="8c2c2-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8c2c2-119">PARAMETERS</span></span>

### <span data-ttu-id="8c2c2-120">-Credential</span><span class="sxs-lookup"><span data-stu-id="8c2c2-120">-Credential</span></span>

<span data-ttu-id="8c2c2-121">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-121">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="8c2c2-122">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-122">The default is the current user.</span></span>

<span data-ttu-id="8c2c2-123">Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-123">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="8c2c2-124">Om du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-124">If you type a user name, you are prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="8c2c2-125">Den här parametern stöds inte av några providrar som installeras med Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-125">This parameter is not supported by any providers installed with Windows PowerShell.</span></span>

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

### <span data-ttu-id="8c2c2-126">-Undanta</span><span class="sxs-lookup"><span data-stu-id="8c2c2-126">-Exclude</span></span>

<span data-ttu-id="8c2c2-127">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar från åtgärden.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-127">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="8c2c2-128">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="8c2c2-128">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="8c2c2-129">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="8c2c2-129">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="8c2c2-130">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-130">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="8c2c2-131">-Filter</span><span class="sxs-lookup"><span data-stu-id="8c2c2-131">-Filter</span></span>

<span data-ttu-id="8c2c2-132">Anger ett filter i formatet eller språket för providern.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-132">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="8c2c2-133">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="8c2c2-133">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="8c2c2-134">Syntaxen för filtret, inklusive användning av jokertecken, är beroende av providern.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-134">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="8c2c2-135">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-135">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="8c2c2-136">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="8c2c2-136">-Include</span></span>

<span data-ttu-id="8c2c2-137">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-137">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="8c2c2-138">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="8c2c2-138">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="8c2c2-139">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="8c2c2-139">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="8c2c2-140">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-140">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="8c2c2-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8c2c2-141">-LiteralPath</span></span>

<span data-ttu-id="8c2c2-142">Anger sökvägen till egenskapens aktuella plats.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-142">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="8c2c2-143">Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-143">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="8c2c2-144">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-144">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="8c2c2-145">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-145">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="8c2c2-146">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="8c2c2-147">-Name</span><span class="sxs-lookup"><span data-stu-id="8c2c2-147">-Name</span></span>

<span data-ttu-id="8c2c2-148">Anger namnet på egenskapen eller egenskaperna som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-148">Specifies the name of the property or properties to retrieve.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c2c2-149">-Path</span><span class="sxs-lookup"><span data-stu-id="8c2c2-149">-Path</span></span>

<span data-ttu-id="8c2c2-150">Anger sökvägen till objektet eller objekten.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-150">Specifies the path to the item or items.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8c2c2-151">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="8c2c2-151">-UseTransaction</span></span>

<span data-ttu-id="8c2c2-152">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-152">Includes the command in the active transaction.</span></span>
<span data-ttu-id="8c2c2-153">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-153">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="8c2c2-154">Mer information finns i about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-154">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="8c2c2-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8c2c2-155">CommonParameters</span></span>

<span data-ttu-id="8c2c2-156">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="8c2c2-156">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="8c2c2-157">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="8c2c2-157">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="8c2c2-158">INDATA</span><span class="sxs-lookup"><span data-stu-id="8c2c2-158">INPUTS</span></span>

### <span data-ttu-id="8c2c2-159">System. String</span><span class="sxs-lookup"><span data-stu-id="8c2c2-159">System.String</span></span>

<span data-ttu-id="8c2c2-160">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-160">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="8c2c2-161">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8c2c2-161">OUTPUTS</span></span>

### <span data-ttu-id="8c2c2-162">System. Boolean, system. String, system. DateTime</span><span class="sxs-lookup"><span data-stu-id="8c2c2-162">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="8c2c2-163">Den här cmdleten returnerar ett objekt för varje objekt egenskaps värde som det får.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-163">This cmdlet returns an object for each item property value that it gets.</span></span>
<span data-ttu-id="8c2c2-164">Objekt typen beror på egenskap svärdet som hämtades.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-164">The object type depends on the property value that is retrieved.</span></span>
<span data-ttu-id="8c2c2-165">I en fil system enhet kan exempelvis cmdlet: en returnera en fil eller mapp.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-165">For example, in a file system drive, the cmdlet might return a file or folder.</span></span>

## <span data-ttu-id="8c2c2-166">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8c2c2-166">NOTES</span></span>

<span data-ttu-id="8c2c2-167">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-167">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="8c2c2-168">Om du vill visa en lista över tillgängliga providers i sessionen kör du `Get-PSProvider` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-168">To list the providers available in your session, run the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="8c2c2-169">Mer information finns i about_Providers.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-169">For more information, see about_Providers.</span></span>

## <span data-ttu-id="8c2c2-170">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8c2c2-170">RELATED LINKS</span></span>

[<span data-ttu-id="8c2c2-171">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8c2c2-171">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="8c2c2-172">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8c2c2-172">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="8c2c2-173">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8c2c2-173">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="8c2c2-174">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8c2c2-174">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="8c2c2-175">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8c2c2-175">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="8c2c2-176">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8c2c2-176">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="8c2c2-177">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8c2c2-177">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="8c2c2-178">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8c2c2-178">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="8c2c2-179">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="8c2c2-179">Get-PSProvider</span></span>](Get-PSProvider.md)
