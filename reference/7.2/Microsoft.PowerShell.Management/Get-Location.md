---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Location
ms.openlocfilehash: 57535b4f566a3bdd541d2035b61c8162e15b35f3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708391"
---
# <span data-ttu-id="d4cef-102">Get-Location</span><span class="sxs-lookup"><span data-stu-id="d4cef-102">Get-Location</span></span>

## <span data-ttu-id="d4cef-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="d4cef-103">SYNOPSIS</span></span>
<span data-ttu-id="d4cef-104">Hämtar information om den aktuella arbets platsen eller en plats stack.</span><span class="sxs-lookup"><span data-stu-id="d4cef-104">Gets information about the current working location or a location stack.</span></span>

## <span data-ttu-id="d4cef-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d4cef-105">SYNTAX</span></span>

### <span data-ttu-id="d4cef-106">Plats (standard)</span><span class="sxs-lookup"><span data-stu-id="d4cef-106">Location (Default)</span></span>

```
Get-Location [-PSProvider <String[]>] [-PSDrive <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="d4cef-107">Stack</span><span class="sxs-lookup"><span data-stu-id="d4cef-107">Stack</span></span>

```
Get-Location [-Stack] [-StackName <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="d4cef-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d4cef-108">DESCRIPTION</span></span>

<span data-ttu-id="d4cef-109">`Get-Location`Cmdleten hämtar ett objekt som representerar den aktuella katalogen, ungefär som utskrifts arbets katalog kommandot (PWD).</span><span class="sxs-lookup"><span data-stu-id="d4cef-109">The `Get-Location` cmdlet gets an object that represents the current directory, much like the print working directory (pwd) command.</span></span>

<span data-ttu-id="d4cef-110">När du flyttar mellan PowerShell-enheter behåller PowerShell din plats i varje enhet.</span><span class="sxs-lookup"><span data-stu-id="d4cef-110">When you move between PowerShell drives, PowerShell retains your location in each drive.</span></span> <span data-ttu-id="d4cef-111">Du kan använda den här cmdleten för att hitta din plats på varje enhet.</span><span class="sxs-lookup"><span data-stu-id="d4cef-111">You can use this cmdlet to find your location in each drive.</span></span>

<span data-ttu-id="d4cef-112">Du kan använda den här cmdleten för att hämta den aktuella katalogen vid körning och använda den i funktioner och skript, till exempel i en funktion som visar den aktuella katalogen i PowerShell-prompten.</span><span class="sxs-lookup"><span data-stu-id="d4cef-112">You can use this cmdlet to get the current directory at run time and use it in functions and scripts, such as in a function that displays the current directory in the PowerShell prompt.</span></span>

<span data-ttu-id="d4cef-113">Du kan också använda den här cmdleten för att Visa platserna i en plats stack.</span><span class="sxs-lookup"><span data-stu-id="d4cef-113">You can also use this cmdlet to display the locations in a location stack.</span></span> <span data-ttu-id="d4cef-114">Mer information finns i anteckningarna och beskrivningarna av parametrarna **stack** och **StackName** .</span><span class="sxs-lookup"><span data-stu-id="d4cef-114">For more information, see the Notes and the descriptions of the **Stack** and **StackName** parameters.</span></span>

## <span data-ttu-id="d4cef-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="d4cef-115">EXAMPLES</span></span>

### <span data-ttu-id="d4cef-116">Exempel 1: Visa din aktuella enhets plats</span><span class="sxs-lookup"><span data-stu-id="d4cef-116">Example 1: Display your current drive location</span></span>

<span data-ttu-id="d4cef-117">Det här kommandot visar din plats i den aktuella PowerShell-enheten.</span><span class="sxs-lookup"><span data-stu-id="d4cef-117">This command displays your location in the current PowerShell drive.</span></span>

```powershell
PS C:\Windows> Get-Location
```

```Output
Path
----
C:\Windows
```

<span data-ttu-id="d4cef-118">Om du till exempel befinner dig i `Windows` `C:` enhetens katalog visas sökvägen till den katalogen.</span><span class="sxs-lookup"><span data-stu-id="d4cef-118">For instance, if you are in the `Windows` directory of the `C:` drive, it displays the path to that directory.</span></span>

### <span data-ttu-id="d4cef-119">Exempel 2: Visa din aktuella plats för olika enheter</span><span class="sxs-lookup"><span data-stu-id="d4cef-119">Example 2: Display your current location for different drives</span></span>

<span data-ttu-id="d4cef-120">Det här exemplet visar hur `Get-Location` du använder för att visa din aktuella plats i olika PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="d4cef-120">This example demonstrates the use of `Get-Location` to display your current location in different PowerShell drives.</span></span> <span data-ttu-id="d4cef-121">`Set-Location` används för att ändra platsen till flera olika sökvägar på olika PSDrives.</span><span class="sxs-lookup"><span data-stu-id="d4cef-121">`Set-Location` is used to change the location to several different paths on different PSDrives.</span></span>

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

### <span data-ttu-id="d4cef-122">Exempel 3: Hämta platser med hjälp av stackar</span><span class="sxs-lookup"><span data-stu-id="d4cef-122">Example 3: Get locations using stacks</span></span>

<span data-ttu-id="d4cef-123">Det här exemplet visar hur du använder **stack** -och **StackName** -parametrarna för `Get-Location` för att visa en lista över platserna i den aktuella platsens stack och alternativa plats stackar.</span><span class="sxs-lookup"><span data-stu-id="d4cef-123">This example shows how to use the **Stack** and **StackName** parameters of `Get-Location` to list the locations in the current location stack and alternate location stacks.</span></span>

<span data-ttu-id="d4cef-124">`Push-Location`Cmdleten används för att ändra till tre olika platser.</span><span class="sxs-lookup"><span data-stu-id="d4cef-124">The `Push-Location` cmdlet is used to change into three different locations.</span></span> <span data-ttu-id="d4cef-125">Den tredje push-enheten använder ett annat stack namn.</span><span class="sxs-lookup"><span data-stu-id="d4cef-125">The third push uses a different stack name.</span></span> <span data-ttu-id="d4cef-126">**Stack** -parametern för `Get-Location` visar innehållet i standard stacken.</span><span class="sxs-lookup"><span data-stu-id="d4cef-126">The **Stack** parameter of `Get-Location` displays the contents of the default stack.</span></span> <span data-ttu-id="d4cef-127">Parametern **StackName** i `Get-Location` visar innehållet i stacken med namnet `Stack2` .</span><span class="sxs-lookup"><span data-stu-id="d4cef-127">The **StackName** parameter of `Get-Location` displays the contents of the stack named `Stack2`.</span></span>

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

### <span data-ttu-id="d4cef-128">Exempel 4: anpassa PowerShell-prompten</span><span class="sxs-lookup"><span data-stu-id="d4cef-128">Example 4: Customize the PowerShell prompt</span></span>

<span data-ttu-id="d4cef-129">Det här exemplet visar hur du anpassar PowerShell-prompten.</span><span class="sxs-lookup"><span data-stu-id="d4cef-129">This example shows how to customize the PowerShell prompt.</span></span>

```powershell
PS C:\>
function prompt { 'PowerShell: ' + (Get-Location) + '> '}
PowerShell: C:\>
```

<span data-ttu-id="d4cef-130">Funktionen som definierar prompten innehåller ett `Get-Location` -kommando som körs när meddelandet visas i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="d4cef-130">The function that defines the prompt includes a `Get-Location` command, which is run whenever the prompt appears in the console.</span></span>

<span data-ttu-id="d4cef-131">Formatet för standard-PowerShell-prompten definieras av en särskild funktion med namnet `prompt` .</span><span class="sxs-lookup"><span data-stu-id="d4cef-131">The format of the default PowerShell prompt is defined by a special function named `prompt`.</span></span> <span data-ttu-id="d4cef-132">Du kan ändra prompten i-konsolen genom att skapa en ny funktion med namnet `prompt` .</span><span class="sxs-lookup"><span data-stu-id="d4cef-132">You can change the prompt in your console by creating a new function named `prompt`.</span></span>

<span data-ttu-id="d4cef-133">Skriv följande kommando för att se den aktuella prompt-funktionen: `Get-Content Function:\prompt`</span><span class="sxs-lookup"><span data-stu-id="d4cef-133">To see the current prompt function, type the following command: `Get-Content Function:\prompt`</span></span>

## <span data-ttu-id="d4cef-134">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="d4cef-134">PARAMETERS</span></span>

### <span data-ttu-id="d4cef-135">-PSDrive</span><span class="sxs-lookup"><span data-stu-id="d4cef-135">-PSDrive</span></span>

<span data-ttu-id="d4cef-136">Hämtar den aktuella platsen i den angivna PowerShell-enheten.</span><span class="sxs-lookup"><span data-stu-id="d4cef-136">Gets the current location in the specified PowerShell drive.</span></span>

<span data-ttu-id="d4cef-137">Om du till exempel är i `Cert:` enheten kan du använda den här parametern för att hitta din aktuella plats i `C:` enheten.</span><span class="sxs-lookup"><span data-stu-id="d4cef-137">For instance, if you are in the `Cert:` drive, you can use this parameter to find your current location in the `C:` drive.</span></span>

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

### <span data-ttu-id="d4cef-138">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="d4cef-138">-PSProvider</span></span>

<span data-ttu-id="d4cef-139">Hämtar den aktuella platsen i enheten som stöds av den angivna PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="d4cef-139">Gets the current location in the drive supported by the specified PowerShell provider.</span></span>
<span data-ttu-id="d4cef-140">Om den angivna providern har stöd för mer än en enhet, returnerar denna cmdlet platsen på den senast använda enheten.</span><span class="sxs-lookup"><span data-stu-id="d4cef-140">If the specified provider supports more than one drive, this cmdlet returns the location on the most recently accessed drive.</span></span>

<span data-ttu-id="d4cef-141">Om du till exempel är i `C:` enheten kan du använda den här parametern för att hitta din aktuella plats i diskarna i PowerShell- **registerposten** .</span><span class="sxs-lookup"><span data-stu-id="d4cef-141">For example, if you are in the `C:` drive, you can use this parameter to find your current location in the drives of the PowerShell **Registry** provider.</span></span>

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

### <span data-ttu-id="d4cef-142">-Stack</span><span class="sxs-lookup"><span data-stu-id="d4cef-142">-Stack</span></span>

<span data-ttu-id="d4cef-143">Anger att den här cmdleten visar de platser som lagts till i den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="d4cef-143">Indicates that this cmdlet displays the locations added to the current location stack.</span></span> <span data-ttu-id="d4cef-144">Du kan lägga till platser i stackar med hjälp av `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d4cef-144">You can add locations to stacks by using the `Push-Location` cmdlet.</span></span>

<span data-ttu-id="d4cef-145">Om du vill visa platserna i en annan plats stack använder du parametern **StackName** .</span><span class="sxs-lookup"><span data-stu-id="d4cef-145">To display the locations in a different location stack, use the **StackName** parameter.</span></span> <span data-ttu-id="d4cef-146">Information om plats stackar finns i [anteckningarna](#notes).</span><span class="sxs-lookup"><span data-stu-id="d4cef-146">For information about location stacks, see the [Notes](#notes).</span></span>

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

### <span data-ttu-id="d4cef-147">-StackName</span><span class="sxs-lookup"><span data-stu-id="d4cef-147">-StackName</span></span>

<span data-ttu-id="d4cef-148">Anger, som en sträng mat ris, stacken för den namngivna platsen.</span><span class="sxs-lookup"><span data-stu-id="d4cef-148">Specifies, as a string array, the named location stacks.</span></span> <span data-ttu-id="d4cef-149">Ange ett eller flera plats stack namn.</span><span class="sxs-lookup"><span data-stu-id="d4cef-149">Enter one or more location stack names.</span></span>

<span data-ttu-id="d4cef-150">Om du vill visa platserna i den aktuella plats stacken använder du **stack** -parametern.</span><span class="sxs-lookup"><span data-stu-id="d4cef-150">To display the locations in the current location stack, use the **Stack** parameter.</span></span> <span data-ttu-id="d4cef-151">Använd cmdleten för att skapa en plats stack för den aktuella plats stacken `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="d4cef-151">To make a location stack the current location stack, use the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="d4cef-152">Denna cmdlet kan inte Visa platserna i den namnlösa standardstacken om den inte är den aktuella stacken.</span><span class="sxs-lookup"><span data-stu-id="d4cef-152">This cmdlet cannot display the locations in the unnamed default stack unless it is the current stack.</span></span>

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

### <span data-ttu-id="d4cef-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d4cef-153">CommonParameters</span></span>

<span data-ttu-id="d4cef-154">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d4cef-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d4cef-155">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d4cef-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d4cef-156">INDATA</span><span class="sxs-lookup"><span data-stu-id="d4cef-156">INPUTS</span></span>

### <span data-ttu-id="d4cef-157">Inga</span><span class="sxs-lookup"><span data-stu-id="d4cef-157">None</span></span>

<span data-ttu-id="d4cef-158">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d4cef-158">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d4cef-159">UTDATA</span><span class="sxs-lookup"><span data-stu-id="d4cef-159">OUTPUTS</span></span>

### <span data-ttu-id="d4cef-160">System. Management. Automation. PathInfo eller system. Management. Automation. PathInfoStack</span><span class="sxs-lookup"><span data-stu-id="d4cef-160">System.Management.Automation.PathInfo or System.Management.Automation.PathInfoStack</span></span>

<span data-ttu-id="d4cef-161">Om du använder **stack** -eller **StackName** -parametrarna returnerar denna cmdlet ett **PathInfoStack** -objekt.</span><span class="sxs-lookup"><span data-stu-id="d4cef-161">If you use the **Stack** or **StackName** parameters, this cmdlet returns a **PathInfoStack** object.</span></span> <span data-ttu-id="d4cef-162">Annars returnerar den ett **PathInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="d4cef-162">Otherwise, it returns a **PathInfo** object.</span></span>

## <span data-ttu-id="d4cef-163">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="d4cef-163">NOTES</span></span>

<span data-ttu-id="d4cef-164">PowerShell stöder flera körnings utrymmen per process.</span><span class="sxs-lookup"><span data-stu-id="d4cef-164">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="d4cef-165">Varje körnings utrymme har sin egen _aktuella katalog_.</span><span class="sxs-lookup"><span data-stu-id="d4cef-165">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="d4cef-166">Detta är inte samma som `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="d4cef-166">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="d4cef-167">Det här problemet kan vara ett problem när du anropar .NET-API: er eller kör ursprungliga program utan att ange explicita katalog Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="d4cef-167">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>
<span data-ttu-id="d4cef-168">`Get-Location`Cmdleten returnerar den aktuella katalogen för den aktuella PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="d4cef-168">The `Get-Location` cmdlet returns the current directory of the current PowerShell runspace.</span></span>

<span data-ttu-id="d4cef-169">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="d4cef-169">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="d4cef-170">Om du vill visa en lista över providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="d4cef-170">To list the providers in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="d4cef-171">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="d4cef-171">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="d4cef-172">Hur **PSProvider**-, **PSDrive**-, **stack**-och **StackName** -parametrarna interagerar beror på providern.</span><span class="sxs-lookup"><span data-stu-id="d4cef-172">The ways that the **PSProvider**, **PSDrive**, **Stack**, and **StackName** parameters interact depends on the provider.</span></span> <span data-ttu-id="d4cef-173">Vissa kombinationer resulterar i fel, t. ex. att ange både en enhet och en provider som inte visar den enheten.</span><span class="sxs-lookup"><span data-stu-id="d4cef-173">Some combinations will result in errors, such as specifying both a drive and a provider that does not expose that drive.</span></span> <span data-ttu-id="d4cef-174">Om inga parametrar anges returnerar denna cmdlet **PathInfo** -objektet för den provider som innehåller den aktuella arbets platsen.</span><span class="sxs-lookup"><span data-stu-id="d4cef-174">If no parameters are specified, this cmdlet returns the **PathInfo** object for the provider that contains the current working location.</span></span>

<span data-ttu-id="d4cef-175">En stack är en sista ingångs punkt som endast det objekt som lagts till senast har åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="d4cef-175">A stack is a last-in, first-out list in which only the most recently added item is accessible.</span></span> <span data-ttu-id="d4cef-176">Du lägger till objekt i en stack i den ordning som du använder dem och hämtar dem sedan för användning i omvänd ordning.</span><span class="sxs-lookup"><span data-stu-id="d4cef-176">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="d4cef-177">Med PowerShell kan du lagra leverantörs platser i plats stackar.</span><span class="sxs-lookup"><span data-stu-id="d4cef-177">PowerShell lets you store provider locations in location stacks.</span></span> <span data-ttu-id="d4cef-178">PowerShell skapar en namnlös standard plats stack och du kan skapa flera namngivna plats stackar.</span><span class="sxs-lookup"><span data-stu-id="d4cef-178">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="d4cef-179">Om du inte anger något stack namn använder PowerShell den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="d4cef-179">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="d4cef-180">Som standard är den namnlösa standard platsen den aktuella plats stacken, men du kan använda `Set-Location` cmdleten för att ändra den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="d4cef-180">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="d4cef-181">Om du vill hantera plats stackar använder du PowerShell `*-Location` -cmdletarna enligt följande.</span><span class="sxs-lookup"><span data-stu-id="d4cef-181">To manage location stacks, use the PowerShell `*-Location` cmdlets, as follows.</span></span>

- <span data-ttu-id="d4cef-182">Om du vill lägga till en plats i en plats stack använder du `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d4cef-182">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="d4cef-183">Använd cmdleten för att hämta en plats från en plats stack `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="d4cef-183">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="d4cef-184">Om du vill visa platserna i den aktuella platsens stack, använder du cmdlet-parametern **stack** `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="d4cef-184">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span> <span data-ttu-id="d4cef-185">Om du vill visa platserna i en namngiven plats stack använder du parametern **StackName** för `Get-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d4cef-185">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="d4cef-186">Om du vill skapa en ny plats stack använder du parametern **StackName** för `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d4cef-186">To create a new location stack, use the **StackName** parameter of the `Push-Location` cmdlet.</span></span>
  <span data-ttu-id="d4cef-187">Om du anger en stack som inte finns `Push-Location` skapar stacken.</span><span class="sxs-lookup"><span data-stu-id="d4cef-187">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="d4cef-188">Om du vill skapa en plats stack för den aktuella plats stacken använder du parametern **StackName** för `Set-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d4cef-188">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="d4cef-189">Den namnlösa standard plats stacken är endast tillgänglig när den är den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="d4cef-189">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="d4cef-190">Om du skapar en namngiven plats stack för den aktuella plats stacken kan du inte längre använda `Push-Location` `Pop-Location` cmdletarna eller för att lägga till eller hämta objekt från standard stacken eller använda denna cmdlet för att Visa platserna i den namnlösa stacken.</span><span class="sxs-lookup"><span data-stu-id="d4cef-190">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use this cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="d4cef-191">Om du vill göra den namnlösa stacken till den aktuella stacken använder du parametern **StackName** för `Set-Location` cmdleten med värdet `$null` eller en tom sträng ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="d4cef-191">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

## <span data-ttu-id="d4cef-192">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="d4cef-192">RELATED LINKS</span></span>

[<span data-ttu-id="d4cef-193">Pop-location</span><span class="sxs-lookup"><span data-stu-id="d4cef-193">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="d4cef-194">Push-plats</span><span class="sxs-lookup"><span data-stu-id="d4cef-194">Push-Location</span></span>](Push-Location.md)

[<span data-ttu-id="d4cef-195">Ange plats</span><span class="sxs-lookup"><span data-stu-id="d4cef-195">Set-Location</span></span>](Set-Location.md)
