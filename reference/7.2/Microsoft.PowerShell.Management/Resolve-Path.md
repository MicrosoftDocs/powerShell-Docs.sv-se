---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resolve-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resolve-Path
ms.openlocfilehash: 0481526aead285e3d5fb494218d1573e03216f2e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709930"
---
# <span data-ttu-id="a54f7-102">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="a54f7-102">Resolve-Path</span></span>

## <span data-ttu-id="a54f7-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a54f7-103">SYNOPSIS</span></span>
<span data-ttu-id="a54f7-104">Matchar jokertecken i en sökväg och visar Sök vägs innehållet.</span><span class="sxs-lookup"><span data-stu-id="a54f7-104">Resolves the wildcard characters in a path, and displays the path contents.</span></span>

## <span data-ttu-id="a54f7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a54f7-105">SYNTAX</span></span>

### <span data-ttu-id="a54f7-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="a54f7-106">Path (Default)</span></span>

```
Resolve-Path [-Path] <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="a54f7-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a54f7-107">LiteralPath</span></span>

```
Resolve-Path -LiteralPath <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="a54f7-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a54f7-108">DESCRIPTION</span></span>

<span data-ttu-id="a54f7-109">`Resolve-Path`Cmdleten visar de objekt och behållare som matchar jokertecken på den angivna platsen.</span><span class="sxs-lookup"><span data-stu-id="a54f7-109">The `Resolve-Path` cmdlet displays the items and containers that match the wildcard pattern at the location specified.</span></span> <span data-ttu-id="a54f7-110">Matchningen kan innehålla filer, mappar, register nycklar eller andra objekt som är tillgängliga från en PSDrive-Provider.</span><span class="sxs-lookup"><span data-stu-id="a54f7-110">The match can include files, folders, registry keys, or any other object accessible from a PSDrive provider.</span></span>

## <span data-ttu-id="a54f7-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a54f7-111">EXAMPLES</span></span>

### <span data-ttu-id="a54f7-112">Exempel 1: matcha Arbetsmappens sökväg</span><span class="sxs-lookup"><span data-stu-id="a54f7-112">Example 1: Resolve the home folder path</span></span>

<span data-ttu-id="a54f7-113">Tilde-tecknet (~) är en kort SKRIFTS notation för den aktuella användarens arbetsmapp.</span><span class="sxs-lookup"><span data-stu-id="a54f7-113">The tilde character (~) is shorthand notation for the current user's home folder.</span></span> <span data-ttu-id="a54f7-114">I det här exemplet visas `Resolve-Path` det fullständiga värdet för sökvägen som returneras.</span><span class="sxs-lookup"><span data-stu-id="a54f7-114">This example shows `Resolve-Path` returning the fully qualified path value.</span></span>

```powershell
PS C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

### <span data-ttu-id="a54f7-115">Exempel 2: matcha sökvägen till Windows-mappen</span><span class="sxs-lookup"><span data-stu-id="a54f7-115">Example 2: Resolve the path of the Windows folder</span></span>

```powershell
PS C:\> Resolve-Path -Path "windows"
```

```Output
Path
----
C:\Windows
```

<span data-ttu-id="a54f7-116">När det körs från roten på C:-enheten returnerar det här kommandot sökvägen till Windows-mappen på enheten C:.</span><span class="sxs-lookup"><span data-stu-id="a54f7-116">When run from the root of the C: drive, this command returns the path of the Windows folder in the C: drive.</span></span>

### <span data-ttu-id="a54f7-117">Exempel 3: Hämta alla sökvägar i Windows-mappen</span><span class="sxs-lookup"><span data-stu-id="a54f7-117">Example 3: Get all paths in the Windows folder</span></span>

```powershell
PS C:\> "C:\windows\*" | Resolve-Path
```

<span data-ttu-id="a54f7-118">Det här kommandot returnerar alla mappar i mappen C:\Windows.</span><span class="sxs-lookup"><span data-stu-id="a54f7-118">This command returns all of the folders in the C:\Windows folder.</span></span> <span data-ttu-id="a54f7-119">Kommandot använder en pipeline-operator (|) för att skicka en Sök vägs sträng till `Resolve-Path` .</span><span class="sxs-lookup"><span data-stu-id="a54f7-119">The command uses a pipeline operator (|) to send a path string to `Resolve-Path`.</span></span>

### <span data-ttu-id="a54f7-120">Exempel 4: matcha en UNC-sökväg</span><span class="sxs-lookup"><span data-stu-id="a54f7-120">Example 4: Resolve a UNC path</span></span>

```powershell
PS C:\> Resolve-Path -Path "\\Server01\public"
```

<span data-ttu-id="a54f7-121">Det här kommandot löser en Universal Naming Convention-sökväg (UNC) och returnerar resurserna i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="a54f7-121">This command resolves a Universal Naming Convention (UNC) path and returns the shares in the path.</span></span>

### <span data-ttu-id="a54f7-122">Exempel 5: Hämta relativa sökvägar</span><span class="sxs-lookup"><span data-stu-id="a54f7-122">Example 5: Get relative paths</span></span>

```powershell
PS C:\> Resolve-Path -Path "c:\prog*" -Relative
```

```Output
.\Program Files
.\Program Files (x86)
.\programs.txt
```

<span data-ttu-id="a54f7-123">Det här kommandot returnerar relativa sökvägar för katalogerna i roten på enheten C:.</span><span class="sxs-lookup"><span data-stu-id="a54f7-123">This command returns relative paths for the directories at the root of the C: drive.</span></span>

### <span data-ttu-id="a54f7-124">Exempel 6: matcha en sökväg som innehåller hakparenteser</span><span class="sxs-lookup"><span data-stu-id="a54f7-124">Example 6: Resolve a path containing brackets</span></span>

<span data-ttu-id="a54f7-125">I det här exemplet används parametern **LiteralPath** för att matcha sökvägen till \[ undermappen test-XML \] .</span><span class="sxs-lookup"><span data-stu-id="a54f7-125">This example uses the **LiteralPath** parameter to resolve the path of the Test\[xml\] subfolder.</span></span>
<span data-ttu-id="a54f7-126">Om du använder **LiteralPath** behandlas hakparenteserna som vanliga tecken i stället för ett reguljärt uttryck.</span><span class="sxs-lookup"><span data-stu-id="a54f7-126">Using **LiteralPath** causes the brackets to be treated as normal characters rather than a regular expression.</span></span>

```powershell
PS C:\> Resolve-Path -LiteralPath 'test[xml]'
```

## <span data-ttu-id="a54f7-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a54f7-127">PARAMETERS</span></span>

### <span data-ttu-id="a54f7-128">-Credential</span><span class="sxs-lookup"><span data-stu-id="a54f7-128">-Credential</span></span>

<span data-ttu-id="a54f7-129">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="a54f7-129">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="a54f7-130">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="a54f7-130">The default is the current user.</span></span>

<span data-ttu-id="a54f7-131">Ange ett användar namn, till exempel user01 eller Domain01\User01, eller skicka ett **PSCredential** -objekt.</span><span class="sxs-lookup"><span data-stu-id="a54f7-131">Type a user name, such as User01 or Domain01\User01, or pass a **PSCredential** object.</span></span> <span data-ttu-id="a54f7-132">Du kan skapa ett **PSCredential** -objekt med hjälp av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a54f7-132">You can create a **PSCredential** object using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="a54f7-133">Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a54f7-133">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="a54f7-134">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a54f7-134">This parameter is not supported by any providers installed with PowerShell.</span></span>

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

### <span data-ttu-id="a54f7-135">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a54f7-135">-LiteralPath</span></span>

<span data-ttu-id="a54f7-136">Anger den sökväg som ska matchas.</span><span class="sxs-lookup"><span data-stu-id="a54f7-136">Specifies the path to be resolved.</span></span>
<span data-ttu-id="a54f7-137">Värdet för parametern **LiteralPath** används precis som det skrivs.</span><span class="sxs-lookup"><span data-stu-id="a54f7-137">The value of the **LiteralPath** parameter is used exactly as typed.</span></span>
<span data-ttu-id="a54f7-138">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="a54f7-138">No characters are interpreted as wildcard characters.</span></span>
<span data-ttu-id="a54f7-139">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="a54f7-139">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="a54f7-140">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="a54f7-140">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="a54f7-141">-Path</span><span class="sxs-lookup"><span data-stu-id="a54f7-141">-Path</span></span>

<span data-ttu-id="a54f7-142">Anger PowerShell-sökvägen som ska lösas.</span><span class="sxs-lookup"><span data-stu-id="a54f7-142">Specifies the PowerShell path to resolve.</span></span>
<span data-ttu-id="a54f7-143">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="a54f7-143">This parameter is required.</span></span>
<span data-ttu-id="a54f7-144">Du kan också skicka en Sök vägs sträng till `Resolve-Path` .</span><span class="sxs-lookup"><span data-stu-id="a54f7-144">You can also pipe a path string to `Resolve-Path`.</span></span>
<span data-ttu-id="a54f7-145">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a54f7-145">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="a54f7-146">– Relativ</span><span class="sxs-lookup"><span data-stu-id="a54f7-146">-Relative</span></span>

<span data-ttu-id="a54f7-147">Anger att denna cmdlet returnerar en relativ sökväg.</span><span class="sxs-lookup"><span data-stu-id="a54f7-147">Indicates that this cmdlet returns a relative path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a54f7-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a54f7-148">CommonParameters</span></span>

<span data-ttu-id="a54f7-149">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a54f7-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a54f7-150">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="a54f7-150">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a54f7-151">INDATA</span><span class="sxs-lookup"><span data-stu-id="a54f7-151">INPUTS</span></span>

### <span data-ttu-id="a54f7-152">System. String</span><span class="sxs-lookup"><span data-stu-id="a54f7-152">System.String</span></span>

<span data-ttu-id="a54f7-153">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet</span><span class="sxs-lookup"><span data-stu-id="a54f7-153">You can pipe a string that contains a path to this cmdlet</span></span>

## <span data-ttu-id="a54f7-154">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a54f7-154">OUTPUTS</span></span>

### <span data-ttu-id="a54f7-155">System. Management. Automation. PathInfo, system. String</span><span class="sxs-lookup"><span data-stu-id="a54f7-155">System.Management.Automation.PathInfo, System.String</span></span>

<span data-ttu-id="a54f7-156">Returnerar ett **PathInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="a54f7-156">Returns a **PathInfo** object.</span></span> <span data-ttu-id="a54f7-157">Returnerar ett sträng värde för den matchade sökvägen om du anger en **relativ** parameter.</span><span class="sxs-lookup"><span data-stu-id="a54f7-157">Returns a string value for the resolved path if you specify the **Relative** parameter.</span></span>

## <span data-ttu-id="a54f7-158">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a54f7-158">NOTES</span></span>

<span data-ttu-id="a54f7-159">`*-Path`Cmdletarna fungerar med fil systemet system, register och certifikat.</span><span class="sxs-lookup"><span data-stu-id="a54f7-159">The `*-Path` cmdlets work with the FileSystem, Registry, and Certificate providers.</span></span>

<span data-ttu-id="a54f7-160">`Resolve-Path` är utformad för att fungera med alla providrar.</span><span class="sxs-lookup"><span data-stu-id="a54f7-160">`Resolve-Path` is designed to work with any provider.</span></span> <span data-ttu-id="a54f7-161">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="a54f7-161">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="a54f7-162">Mer information finns i [about_providers](../microsoft.powershell.core/about/about_providers.md).</span><span class="sxs-lookup"><span data-stu-id="a54f7-162">For more information, see [about_providers](../microsoft.powershell.core/about/about_providers.md).</span></span>

<span data-ttu-id="a54f7-163">`Resolve-Path` matchar bara befintliga sökvägar.</span><span class="sxs-lookup"><span data-stu-id="a54f7-163">`Resolve-Path` only resolves existing paths.</span></span> <span data-ttu-id="a54f7-164">Det går inte att använda den för att lösa en plats som ännu inte finns.</span><span class="sxs-lookup"><span data-stu-id="a54f7-164">It cannot be used to resolve a location that does not exist yet.</span></span>

## <span data-ttu-id="a54f7-165">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a54f7-165">RELATED LINKS</span></span>

[<span data-ttu-id="a54f7-166">Konvertera-sökväg</span><span class="sxs-lookup"><span data-stu-id="a54f7-166">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="a54f7-167">Anslut till sökväg</span><span class="sxs-lookup"><span data-stu-id="a54f7-167">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="a54f7-168">Dela-sökväg</span><span class="sxs-lookup"><span data-stu-id="a54f7-168">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="a54f7-169">Test-sökväg</span><span class="sxs-lookup"><span data-stu-id="a54f7-169">Test-Path</span></span>](Test-Path.md)

