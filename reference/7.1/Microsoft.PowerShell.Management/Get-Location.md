---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-location?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Location
ms.openlocfilehash: 79d6337574c2e354e49926fa894415fca2469ba7
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/14/2020
ms.locfileid: "93269210"
---
# <span data-ttu-id="5c6b7-103">Get-Location</span><span class="sxs-lookup"><span data-stu-id="5c6b7-103">Get-Location</span></span>

## <span data-ttu-id="5c6b7-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5c6b7-104">SYNOPSIS</span></span>
<span data-ttu-id="5c6b7-105">Hämtar information om den aktuella arbets platsen eller en plats stack.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-105">Gets information about the current working location or a location stack.</span></span>

## <span data-ttu-id="5c6b7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5c6b7-106">SYNTAX</span></span>

### <span data-ttu-id="5c6b7-107">Plats (standard)</span><span class="sxs-lookup"><span data-stu-id="5c6b7-107">Location (Default)</span></span>

```
Get-Location [-PSProvider <String[]>] [-PSDrive <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="5c6b7-108">Stack</span><span class="sxs-lookup"><span data-stu-id="5c6b7-108">Stack</span></span>

```
Get-Location [-Stack] [-StackName <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="5c6b7-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5c6b7-109">DESCRIPTION</span></span>

<span data-ttu-id="5c6b7-110">`Get-Location`Cmdleten hämtar ett objekt som representerar den aktuella katalogen, ungefär som utskrifts arbets katalog kommandot (PWD).</span><span class="sxs-lookup"><span data-stu-id="5c6b7-110">The `Get-Location` cmdlet gets an object that represents the current directory, much like the print working directory (pwd) command.</span></span>

<span data-ttu-id="5c6b7-111">När du flyttar mellan PowerShell-enheter behåller PowerShell din plats i varje enhet.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-111">When you move between PowerShell drives, PowerShell retains your location in each drive.</span></span> <span data-ttu-id="5c6b7-112">Du kan använda den här cmdleten för att hitta din plats på varje enhet.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-112">You can use this cmdlet to find your location in each drive.</span></span>

<span data-ttu-id="5c6b7-113">Du kan använda den här cmdleten för att hämta den aktuella katalogen vid körning och använda den i funktioner och skript, till exempel i en funktion som visar den aktuella katalogen i PowerShell-prompten.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-113">You can use this cmdlet to get the current directory at run time and use it in functions and scripts, such as in a function that displays the current directory in the PowerShell prompt.</span></span>

<span data-ttu-id="5c6b7-114">Du kan också använda den här cmdleten för att Visa platserna i en plats stack.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-114">You can also use this cmdlet to display the locations in a location stack.</span></span> <span data-ttu-id="5c6b7-115">Mer information finns i anteckningarna och beskrivningarna av parametrarna **stack** och **StackName** .</span><span class="sxs-lookup"><span data-stu-id="5c6b7-115">For more information, see the Notes and the descriptions of the **Stack** and **StackName** parameters.</span></span>

## <span data-ttu-id="5c6b7-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5c6b7-116">EXAMPLES</span></span>

### <span data-ttu-id="5c6b7-117">Exempel 1: Visa din aktuella enhets plats</span><span class="sxs-lookup"><span data-stu-id="5c6b7-117">Example 1: Display your current drive location</span></span>

<span data-ttu-id="5c6b7-118">Det här kommandot visar din plats i den aktuella PowerShell-enheten.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-118">This command displays your location in the current PowerShell drive.</span></span>

```powershell
PS C:\Windows> Get-Location
```

```Output
Path
----
C:\Windows
```

<span data-ttu-id="5c6b7-119">Om du till exempel befinner dig i `Windows` `C:` enhetens katalog visas sökvägen till den katalogen.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-119">For instance, if you are in the `Windows` directory of the `C:` drive, it displays the path to that directory.</span></span>

### <span data-ttu-id="5c6b7-120">Exempel 2: Visa din aktuella plats för olika enheter</span><span class="sxs-lookup"><span data-stu-id="5c6b7-120">Example 2: Display your current location for different drives</span></span>

<span data-ttu-id="5c6b7-121">Det här exemplet visar hur `Get-Location` du använder för att visa din aktuella plats i olika PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-121">This example demonstrates the use of `Get-Location` to display your current location in different PowerShell drives.</span></span> <span data-ttu-id="5c6b7-122">`Set-Location` används för att ändra platsen till flera olika sökvägar på olika PSDrives.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-122">`Set-Location` is used to change the location to several different paths on different PSDrives.</span></span>

```powershell
PS C:\> Set-Location C:\Windows
PS C:\Windows> Set-Location HKLM:\Software\Microsoft
PS HKLM:\Software\Microsoft> Set-Location "HKCU:\Control Panel\Input Method"
PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive C

Path
----
C:\Windows

PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive HKLM

Path
----
HKLM:\Software\Microsoft

PS HKCU:\Control Panel\Input Method> Set-Location C:
PS C:\Windows> Get-Location -PSProvider Registry

Path
----
HKCU:\Control Panel\Input Method
```

### <span data-ttu-id="5c6b7-123">Exempel 3: Hämta platser med hjälp av stackar</span><span class="sxs-lookup"><span data-stu-id="5c6b7-123">Example 3: Get locations using stacks</span></span>

<span data-ttu-id="5c6b7-124">Det här exemplet visar hur du använder **stack** -och **StackName** -parametrarna för `Get-Location` för att visa en lista över platserna i den aktuella platsens stack och alternativa plats stackar.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-124">This example shows how to use the **Stack** and **StackName** parameters of `Get-Location` to list the locations in the current location stack and alternate location stacks.</span></span>

<span data-ttu-id="5c6b7-125">`Push-Location`Cmdleten används för att ändra till tre olika platser.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-125">The `Push-Location` cmdlet is used to change into three different locations.</span></span> <span data-ttu-id="5c6b7-126">Den tredje push-enheten använder ett annat stack namn.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-126">The third push uses a different stack name.</span></span> <span data-ttu-id="5c6b7-127">**Stack** -parametern för `Get-Location` visar innehållet i standard stacken.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-127">The **Stack** parameter of `Get-Location` displays the contents of the default stack.</span></span> <span data-ttu-id="5c6b7-128">Parametern **StackName** i `Get-Location` visar innehållet i stacken med namnet `Stack2` .</span><span class="sxs-lookup"><span data-stu-id="5c6b7-128">The **StackName** parameter of `Get-Location` displays the contents of the stack named `Stack2`.</span></span>

```powershell
PS C:\> Push-Location C:\Windows
PS C:\Windows>Push-Location System32
PS C:\Windows\System32>Push-Location WindowsPowerShell -StackName Stack2
C:\Windows\System32\WindowsPowerShell>Get-Location -Stack

Path
----
C:\Windows
C:\

C:\Windows\System32\WindowsPowerShell>Get-Location -StackName Stack2

Path
----
C:\Windows\System32
```

### <span data-ttu-id="5c6b7-129">Exempel 4: anpassa PowerShell-prompten</span><span class="sxs-lookup"><span data-stu-id="5c6b7-129">Example 4: Customize the PowerShell prompt</span></span>

<span data-ttu-id="5c6b7-130">Det här exemplet visar hur du anpassar PowerShell-prompten.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-130">This example shows how to customize the PowerShell prompt.</span></span>

```powershell
PS C:\>
function prompt { 'PowerShell: ' + (Get-Location) + '> '}
PowerShell: C:\>
```

<span data-ttu-id="5c6b7-131">Funktionen som definierar prompten innehåller ett `Get-Location` -kommando som körs när meddelandet visas i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-131">The function that defines the prompt includes a `Get-Location` command, which is run whenever the prompt appears in the console.</span></span>

<span data-ttu-id="5c6b7-132">Formatet för standard-PowerShell-prompten definieras av en särskild funktion med namnet `prompt` .</span><span class="sxs-lookup"><span data-stu-id="5c6b7-132">The format of the default PowerShell prompt is defined by a special function named `prompt`.</span></span> <span data-ttu-id="5c6b7-133">Du kan ändra prompten i-konsolen genom att skapa en ny funktion med namnet `prompt` .</span><span class="sxs-lookup"><span data-stu-id="5c6b7-133">You can change the prompt in your console by creating a new function named `prompt`.</span></span>

<span data-ttu-id="5c6b7-134">Skriv följande kommando för att se den aktuella prompt-funktionen: `Get-Content Function:\prompt`</span><span class="sxs-lookup"><span data-stu-id="5c6b7-134">To see the current prompt function, type the following command: `Get-Content Function:\prompt`</span></span>

## <span data-ttu-id="5c6b7-135">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5c6b7-135">PARAMETERS</span></span>

### <span data-ttu-id="5c6b7-136">-PSDrive</span><span class="sxs-lookup"><span data-stu-id="5c6b7-136">-PSDrive</span></span>

<span data-ttu-id="5c6b7-137">Hämtar den aktuella platsen i den angivna PowerShell-enheten.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-137">Gets the current location in the specified PowerShell drive.</span></span>

<span data-ttu-id="5c6b7-138">Om du till exempel är i `Cert:` enheten kan du använda den här parametern för att hitta din aktuella plats i `C:` enheten.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-138">For instance, if you are in the `Cert:` drive, you can use this parameter to find your current location in the `C:` drive.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5c6b7-139">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="5c6b7-139">-PSProvider</span></span>

<span data-ttu-id="5c6b7-140">Hämtar den aktuella platsen i enheten som stöds av den angivna PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-140">Gets the current location in the drive supported by the specified PowerShell provider.</span></span>
<span data-ttu-id="5c6b7-141">Om den angivna providern har stöd för mer än en enhet, returnerar denna cmdlet platsen på den senast använda enheten.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-141">If the specified provider supports more than one drive, this cmdlet returns the location on the most recently accessed drive.</span></span>

<span data-ttu-id="5c6b7-142">Om du till exempel är i `C:` enheten kan du använda den här parametern för att hitta din aktuella plats i diskarna i PowerShell- **registerposten** .</span><span class="sxs-lookup"><span data-stu-id="5c6b7-142">For example, if you are in the `C:` drive, you can use this parameter to find your current location in the drives of the PowerShell **Registry** provider.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5c6b7-143">-Stack</span><span class="sxs-lookup"><span data-stu-id="5c6b7-143">-Stack</span></span>

<span data-ttu-id="5c6b7-144">Anger att den här cmdleten visar de platser som lagts till i den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-144">Indicates that this cmdlet displays the locations added to the current location stack.</span></span> <span data-ttu-id="5c6b7-145">Du kan lägga till platser i stackar med hjälp av `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-145">You can add locations to stacks by using the `Push-Location` cmdlet.</span></span>

<span data-ttu-id="5c6b7-146">Om du vill visa platserna i en annan plats stack använder du parametern **StackName** .</span><span class="sxs-lookup"><span data-stu-id="5c6b7-146">To display the locations in a different location stack, use the **StackName** parameter.</span></span> <span data-ttu-id="5c6b7-147">Information om plats stackar finns i [anteckningarna](#notes).</span><span class="sxs-lookup"><span data-stu-id="5c6b7-147">For information about location stacks, see the [Notes](#notes).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5c6b7-148">-StackName</span><span class="sxs-lookup"><span data-stu-id="5c6b7-148">-StackName</span></span>

<span data-ttu-id="5c6b7-149">Anger, som en sträng mat ris, stacken för den namngivna platsen.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-149">Specifies, as a string array, the named location stacks.</span></span> <span data-ttu-id="5c6b7-150">Ange ett eller flera plats stack namn.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-150">Enter one or more location stack names.</span></span>

<span data-ttu-id="5c6b7-151">Om du vill visa platserna i den aktuella plats stacken använder du **stack** -parametern.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-151">To display the locations in the current location stack, use the **Stack** parameter.</span></span> <span data-ttu-id="5c6b7-152">Använd cmdleten för att skapa en plats stack för den aktuella plats stacken `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="5c6b7-152">To make a location stack the current location stack, use the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="5c6b7-153">Denna cmdlet kan inte Visa platserna i den namnlösa standardstacken om den inte är den aktuella stacken.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-153">This cmdlet cannot display the locations in the unnamed default stack unless it is the current stack.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5c6b7-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5c6b7-154">CommonParameters</span></span>

<span data-ttu-id="5c6b7-155">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5c6b7-156">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5c6b7-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5c6b7-157">INDATA</span><span class="sxs-lookup"><span data-stu-id="5c6b7-157">INPUTS</span></span>

### <span data-ttu-id="5c6b7-158">Inget</span><span class="sxs-lookup"><span data-stu-id="5c6b7-158">None</span></span>

<span data-ttu-id="5c6b7-159">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-159">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="5c6b7-160">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5c6b7-160">OUTPUTS</span></span>

### <span data-ttu-id="5c6b7-161">System. Management. Automation. PathInfo eller system. Management. Automation. PathInfoStack</span><span class="sxs-lookup"><span data-stu-id="5c6b7-161">System.Management.Automation.PathInfo or System.Management.Automation.PathInfoStack</span></span>

<span data-ttu-id="5c6b7-162">Om du använder **stack** -eller **StackName** -parametrarna returnerar denna cmdlet ett **PathInfoStack** -objekt.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-162">If you use the **Stack** or **StackName** parameters, this cmdlet returns a **PathInfoStack** object.</span></span> <span data-ttu-id="5c6b7-163">Annars returnerar den ett **PathInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-163">Otherwise, it returns a **PathInfo** object.</span></span>

## <span data-ttu-id="5c6b7-164">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5c6b7-164">NOTES</span></span>

<span data-ttu-id="5c6b7-165">PowerShell stöder flera körnings utrymmen per process.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-165">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="5c6b7-166">Varje körnings utrymme har sin egen _aktuella katalog_.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-166">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="5c6b7-167">Detta är inte samma som `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="5c6b7-167">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="5c6b7-168">Det här problemet kan vara ett problem när du anropar .NET-API: er eller kör ursprungliga program utan att ange explicita katalog Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-168">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>
<span data-ttu-id="5c6b7-169">`Get-Location`Cmdleten returnerar den aktuella katalogen för den aktuella PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-169">The `Get-Location` cmdlet returns the current directory of the current PowerShell runspace.</span></span>

<span data-ttu-id="5c6b7-170">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-170">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="5c6b7-171">Om du vill visa en lista över providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="5c6b7-171">To list the providers in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="5c6b7-172">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="5c6b7-172">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="5c6b7-173">Hur **PSProvider** -, **PSDrive** -, **stack** -och **StackName** -parametrarna interagerar beror på providern.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-173">The ways that the **PSProvider** , **PSDrive** , **Stack** , and **StackName** parameters interact depends on the provider.</span></span> <span data-ttu-id="5c6b7-174">Vissa kombinationer resulterar i fel, t. ex. att ange både en enhet och en provider som inte visar den enheten.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-174">Some combinations will result in errors, such as specifying both a drive and a provider that does not expose that drive.</span></span> <span data-ttu-id="5c6b7-175">Om inga parametrar anges returnerar denna cmdlet **PathInfo** -objektet för den provider som innehåller den aktuella arbets platsen.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-175">If no parameters are specified, this cmdlet returns the **PathInfo** object for the provider that contains the current working location.</span></span>

<span data-ttu-id="5c6b7-176">En stack är en sista ingångs punkt som endast det objekt som lagts till senast har åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-176">A stack is a last-in, first-out list in which only the most recently added item is accessible.</span></span> <span data-ttu-id="5c6b7-177">Du lägger till objekt i en stack i den ordning som du använder dem och hämtar dem sedan för användning i omvänd ordning.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-177">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="5c6b7-178">Med PowerShell kan du lagra leverantörs platser i plats stackar.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-178">PowerShell lets you store provider locations in location stacks.</span></span> <span data-ttu-id="5c6b7-179">PowerShell skapar en namnlös standard plats stack och du kan skapa flera namngivna plats stackar.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-179">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="5c6b7-180">Om du inte anger något stack namn använder PowerShell den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-180">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="5c6b7-181">Som standard är den namnlösa standard platsen den aktuella plats stacken, men du kan använda `Set-Location` cmdleten för att ändra den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-181">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="5c6b7-182">Om du vill hantera plats stackar använder du PowerShell `*-Location` -cmdletarna enligt följande.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-182">To manage location stacks, use the PowerShell `*-Location` cmdlets, as follows.</span></span>

- <span data-ttu-id="5c6b7-183">Om du vill lägga till en plats i en plats stack använder du `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-183">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="5c6b7-184">Använd cmdleten för att hämta en plats från en plats stack `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="5c6b7-184">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="5c6b7-185">Om du vill visa platserna i den aktuella platsens stack, använder du cmdlet-parametern **stack** `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="5c6b7-185">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span> <span data-ttu-id="5c6b7-186">Om du vill visa platserna i en namngiven plats stack använder du parametern **StackName** för `Get-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-186">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="5c6b7-187">Om du vill skapa en ny plats stack använder du parametern **StackName** för `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-187">To create a new location stack, use the **StackName** parameter of the `Push-Location` cmdlet.</span></span>
  <span data-ttu-id="5c6b7-188">Om du anger en stack som inte finns `Push-Location` skapar stacken.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-188">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="5c6b7-189">Om du vill skapa en plats stack för den aktuella plats stacken använder du parametern **StackName** för `Set-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-189">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="5c6b7-190">Den namnlösa standard plats stacken är endast tillgänglig när den är den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-190">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="5c6b7-191">Om du skapar en namngiven plats stack för den aktuella plats stacken kan du inte längre använda `Push-Location` `Pop-Location` cmdletarna eller för att lägga till eller hämta objekt från standard stacken eller använda denna cmdlet för att Visa platserna i den namnlösa stacken.</span><span class="sxs-lookup"><span data-stu-id="5c6b7-191">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use this cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="5c6b7-192">Om du vill göra den namnlösa stacken till den aktuella stacken använder du parametern **StackName** för `Set-Location` cmdleten med värdet `$null` eller en tom sträng ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="5c6b7-192">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

## <span data-ttu-id="5c6b7-193">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5c6b7-193">RELATED LINKS</span></span>

[<span data-ttu-id="5c6b7-194">Pop-location</span><span class="sxs-lookup"><span data-stu-id="5c6b7-194">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="5c6b7-195">Push-plats</span><span class="sxs-lookup"><span data-stu-id="5c6b7-195">Push-Location</span></span>](Push-Location.md)

[<span data-ttu-id="5c6b7-196">Ange plats</span><span class="sxs-lookup"><span data-stu-id="5c6b7-196">Set-Location</span></span>](Set-Location.md)

