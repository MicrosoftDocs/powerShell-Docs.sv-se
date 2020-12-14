---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-information?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Information
ms.openlocfilehash: f15902c1c6c298dd02db3edf061d56e1446ecb1f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709372"
---
# <span data-ttu-id="fe3ac-102">Write-Information</span><span class="sxs-lookup"><span data-stu-id="fe3ac-102">Write-Information</span></span>

## <span data-ttu-id="fe3ac-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="fe3ac-103">SYNOPSIS</span></span>

<span data-ttu-id="fe3ac-104">Anger hur PowerShell hanterar informations Ströms data för ett kommando.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-104">Specifies how PowerShell handles information stream data for a command.</span></span>

## <span data-ttu-id="fe3ac-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fe3ac-105">SYNTAX</span></span>

```
Write-Information [-MessageData] <Object> [[-Tags] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="fe3ac-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="fe3ac-106">DESCRIPTION</span></span>

<span data-ttu-id="fe3ac-107">`Write-Information`Cmdleten anger hur PowerShell hanterar informations data Ströms data för ett kommando.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-107">The `Write-Information` cmdlet specifies how PowerShell handles information stream data for a command.</span></span>

<span data-ttu-id="fe3ac-108">Windows PowerShell 5,0 introducerar en ny, strukturerad informations ström.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-108">Windows PowerShell 5.0 introduces a new, structured information stream.</span></span> <span data-ttu-id="fe3ac-109">Du kan använda den här data strömmen för att skicka strukturerade data mellan ett skript och dess anropare eller värd programmet.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-109">You can use this stream to transmit structured data between a script and its callers or the host application.</span></span>
<span data-ttu-id="fe3ac-110">`Write-Information` låter dig lägga till ett informations meddelande i data strömmen och ange hur PowerShell hanterar informations data Ströms data för ett kommando.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-110">`Write-Information` lets you add an informational message to the stream, and specify how PowerShell handles information stream data for a command.</span></span> <span data-ttu-id="fe3ac-111">Informations strömmar fungerar också för `PowerShell.Streams` jobb och schemalagda aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-111">Information streams also work for `PowerShell.Streams`, jobs, and scheduled tasks.</span></span>

> [!NOTE]
> <span data-ttu-id="fe3ac-112">Informations data strömmen följer inte standard konventionen för att förlösa sina meddelanden med "[Stream Name]:".</span><span class="sxs-lookup"><span data-stu-id="fe3ac-112">The information stream does not follow the standard convention of prefixing its messages with "[Stream Name]:".</span></span> <span data-ttu-id="fe3ac-113">Detta var avsett för det kortfattat och visuell renlighet.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-113">This was intended for brevity and visual cleanliness.</span></span>

<span data-ttu-id="fe3ac-114">`$InformationPreference`Variabeln Preference avgör om det meddelande som du anger ska `Write-Information` visas vid den förväntade punkten i skriptets åtgärd.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-114">The `$InformationPreference` preference variable value determines whether the message you provide to `Write-Information` is displayed at the expected point in a script's operation.</span></span> <span data-ttu-id="fe3ac-115">Eftersom standardvärdet för den här variabeln är `SilentlyContinue` , visas inte informations meddelanden som standard.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-115">Because the default value of this variable is `SilentlyContinue`, by default, informational messages are not shown.</span></span> <span data-ttu-id="fe3ac-116">Om du inte vill ändra värdet för `$InformationPreference` kan du åsidosätta dess värde genom att lägga till den `InformationAction` gemensamma parametern i kommandot.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-116">If you don't want to change the value of `$InformationPreference`, you can override its value by adding the `InformationAction` common parameter to your command.</span></span> <span data-ttu-id="fe3ac-117">Mer information finns i [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) och [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="fe3ac-117">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) and [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="fe3ac-118">Från och med Windows PowerShell 5,0 `Write-Host` är en omslutning som `Write-Information` gör att du kan använda `Write-Host` för att generera utdata till informations strömmen.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-118">Starting in Windows PowerShell 5.0, `Write-Host` is a wrapper for `Write-Information` This allows you to use `Write-Host` to emit output to the information stream.</span></span> <span data-ttu-id="fe3ac-119">Detta gör det möjligt att **samla in** eller **undertrycka** data som skrivits med samtidigt som du `Write-Host` behåller bakåtkompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-119">This enables the **capture** or **suppression** of data written using `Write-Host` while preserving backwards compatibility.</span></span> <span data-ttu-id="fe3ac-120">Mer information finns i [Write-Host](Write-Host.md)</span><span class="sxs-lookup"><span data-stu-id="fe3ac-120">For more information see [Write-Host](Write-Host.md)</span></span>

<span data-ttu-id="fe3ac-121">`Write-Information` är också en arbets flödes aktivitet som stöds i PowerShell 5. x.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-121">`Write-Information` is also a supported workflow activity in PowerShell 5.x.</span></span>

## <span data-ttu-id="fe3ac-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="fe3ac-122">EXAMPLES</span></span>

### <span data-ttu-id="fe3ac-123">Exempel 1: Skriv information för Get-Results</span><span class="sxs-lookup"><span data-stu-id="fe3ac-123">Example 1: Write information for Get- results</span></span>

<span data-ttu-id="fe3ac-124">I det här exemplet visar du ett informations meddelande, "skaffa dina funktioner!", efter att du kört `Get-WindowsFeature` kommandot för att hitta alla funktioner som har ett namn värde som börjar med "p".</span><span class="sxs-lookup"><span data-stu-id="fe3ac-124">In this example, you show an informational message, "Got your features!", after running the `Get-WindowsFeature` command to find all features that have a Name value that starts with 'p'.</span></span>
<span data-ttu-id="fe3ac-125">Eftersom `$InformationPreference` variabeln fortfarande är inställd på standardvärdet, `SilentlyContinue` lägger du till `InformationAction` parametern för att åsidosätta `$InformationPreference` värdet och visa meddelandet.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-125">Because the `$InformationPreference` variable is still set to its default, `SilentlyContinue`, you add the `InformationAction` parameter to override the `$InformationPreference` value, and show the message.</span></span> <span data-ttu-id="fe3ac-126">`InformationAction`Värdet är Continue, vilket innebär att meddelandet visas, men skriptet eller kommandot fortsätter om det inte har slutförts ännu.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-126">The `InformationAction` value is Continue, which means that your message is shown, but the script or command continues, if it is not yet finished.</span></span>

```powershell
Get-WindowsFeature -Name p*
Write-Information -MessageData "Got your features!" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
Got your features!
```

### <span data-ttu-id="fe3ac-127">Exempel 2: Skriv information och tagga den</span><span class="sxs-lookup"><span data-stu-id="fe3ac-127">Example 2: Write information and tag it</span></span>

<span data-ttu-id="fe3ac-128">I det här exemplet använder du `Write-Information` för att meddela användarna att de behöver köra ett annat kommando när de är klar med det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-128">In this example, you use `Write-Information` to let users know they'll need to run another command after they're done running the current command.</span></span> <span data-ttu-id="fe3ac-129">I exemplet läggs etikett instruktionerna till i informations meddelandet.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-129">The example adds the tag Instructions to the informational message.</span></span> <span data-ttu-id="fe3ac-130">När du har kört det här kommandot, och om du söker i informations data strömmen efter taggade instruktioner, kommer det meddelande som anges här vara bland resultatet.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-130">After running this command, if you search the information stream for messages tagged Instructions, the message specified here would be among the results.</span></span>

```powershell
$message = "To filter your results for PowerShell, pipe your results to the Where-Object cmdlet."
Get-WindowsFeature -Name p*
Write-Information -MessageData $message -Tags "Instructions" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
To filter your results for PowerShell, pipe your results to the Where-Object cmdlet.
```

### <span data-ttu-id="fe3ac-131">Exempel 3: skriva information till en fil</span><span class="sxs-lookup"><span data-stu-id="fe3ac-131">Example 3: Write information to a file</span></span>

<span data-ttu-id="fe3ac-132">I det här exemplet omdirigerar du informations strömmen i funktionen till en `Info.txt` med hjälp av koden `6>` .</span><span class="sxs-lookup"><span data-stu-id="fe3ac-132">In this example, you redirect the information stream in the function to a `Info.txt` using the code `6>`.</span></span> <span data-ttu-id="fe3ac-133">När du öppnar `Info.txt` filen visas texten "här går du till".</span><span class="sxs-lookup"><span data-stu-id="fe3ac-133">When you open the `Info.txt` file, you see the text, "Here you go."</span></span>

```powershell
function Test-Info
{
    Get-Process P*
    Write-Information "Here you go"
}
Test-Info 6> Info.txt
```

### <span data-ttu-id="fe3ac-134">Exempel 4: skicka objekt för att skriva information</span><span class="sxs-lookup"><span data-stu-id="fe3ac-134">Example 4: Pass object to write information</span></span>

<span data-ttu-id="fe3ac-135">I det här exemplet kan du använda `Write-Information` för att skriva de 10 högsta processor användnings processerna från `Get-Process` objektets utdata som har passerat genom flera pipeliner.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-135">In this example, you can use `Write-Information` to write the top 10 highest CPU utilization processes from the `Get-Process` object output that has passes through multiple pipelines.</span></span>

```powershell
Get-Process | Sort-Object CPU -Descending |
    Select-Object Id, ProcessName, CPU -First 10 |
        Write-Information -InformationAction Continue
```

```Output
@{Id=12692; ProcessName=chrome; CPU=39431.296875}
@{Id=21292; ProcessName=OUTLOOK; CPU=23991.875}
@{Id=10548; ProcessName=CefSharp.BrowserSubprocess; CPU=20546.203125}
@{Id=312848; ProcessName=Taskmgr; CPU=13173.1875}
@{Id=10848; ProcessName=SnapClient; CPU=7014.265625}
@{Id=9760; ProcessName=Receiver; CPU=6792.359375}
@{Id=12040; ProcessName=Teams; CPU=5605.578125}
@{Id=498388; ProcessName=chrome; CPU=3062.453125}
@{Id=6900; ProcessName=chrome; CPU=2546.9375}
@{Id=9044; ProcessName=explorer; CPU=2358.765625}
```

## <span data-ttu-id="fe3ac-136">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="fe3ac-136">PARAMETERS</span></span>

### <span data-ttu-id="fe3ac-137">-MessageData</span><span class="sxs-lookup"><span data-stu-id="fe3ac-137">-MessageData</span></span>

<span data-ttu-id="fe3ac-138">Anger ett informations meddelande som ska visas för användarna när de kör ett skript eller kommando.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-138">Specifies an informational message that you want to display to users as they run a script or command.</span></span> <span data-ttu-id="fe3ac-139">För bästa resultat omger du informations meddelandet inom citat tecken.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-139">For best results, enclose the informational message in quotation marks.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fe3ac-140">– Taggar</span><span class="sxs-lookup"><span data-stu-id="fe3ac-140">-Tags</span></span>

<span data-ttu-id="fe3ac-141">Anger en enkel sträng som du kan använda för att sortera och filtrera meddelanden som du har lagt till i informations strömmen med `Write-Information` .</span><span class="sxs-lookup"><span data-stu-id="fe3ac-141">Specifies a simple string that you can use to sort and filter messages that you have added to the information stream with `Write-Information`.</span></span> <span data-ttu-id="fe3ac-142">Den här parametern fungerar på samma sätt som parametern **taggar** i `New-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="fe3ac-142">This parameter works similarly to the **Tags** parameter in `New-ModuleManifest`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe3ac-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fe3ac-143">CommonParameters</span></span>

<span data-ttu-id="fe3ac-144">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fe3ac-145">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fe3ac-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fe3ac-146">INDATA</span><span class="sxs-lookup"><span data-stu-id="fe3ac-146">INPUTS</span></span>

### <span data-ttu-id="fe3ac-147">System. Object</span><span class="sxs-lookup"><span data-stu-id="fe3ac-147">System.Object</span></span>

<span data-ttu-id="fe3ac-148">`Write-Information` accepterar skickas-objekt som skickas till informations strömmen.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-148">`Write-Information` accepts piped objects to pass to the information stream.</span></span>

## <span data-ttu-id="fe3ac-149">UTDATA</span><span class="sxs-lookup"><span data-stu-id="fe3ac-149">OUTPUTS</span></span>

### <span data-ttu-id="fe3ac-150">System. Management. Automation. InformationRecord</span><span class="sxs-lookup"><span data-stu-id="fe3ac-150">System.Management.Automation.InformationRecord</span></span>

## <span data-ttu-id="fe3ac-151">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="fe3ac-151">NOTES</span></span>

## <span data-ttu-id="fe3ac-152">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="fe3ac-152">RELATED LINKS</span></span>

[<span data-ttu-id="fe3ac-153">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="fe3ac-153">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="fe3ac-154">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="fe3ac-154">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="fe3ac-155">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fe3ac-155">about_CommonParameters</span></span>](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)

[<span data-ttu-id="fe3ac-156">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="fe3ac-156">about_Preference_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[<span data-ttu-id="fe3ac-157">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="fe3ac-157">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="fe3ac-158">Skriv-debug</span><span class="sxs-lookup"><span data-stu-id="fe3ac-158">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="fe3ac-159">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="fe3ac-159">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="fe3ac-160">Skriv information</span><span class="sxs-lookup"><span data-stu-id="fe3ac-160">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="fe3ac-161">Skriv förlopp</span><span class="sxs-lookup"><span data-stu-id="fe3ac-161">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="fe3ac-162">Skriv-verbose</span><span class="sxs-lookup"><span data-stu-id="fe3ac-162">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="fe3ac-163">Skriv varning</span><span class="sxs-lookup"><span data-stu-id="fe3ac-163">Write-Warning</span></span>](Write-Warning.md)

[<span data-ttu-id="fe3ac-164">Skriva-utdata</span><span class="sxs-lookup"><span data-stu-id="fe3ac-164">Write-Output</span></span>](Write-Output.md)
