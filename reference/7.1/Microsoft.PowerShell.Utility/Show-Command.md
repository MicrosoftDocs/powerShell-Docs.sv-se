---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/29/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Command
ms.openlocfilehash: 86253a8a0bd02a60980cc3655af7bb961acf88ac
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263426"
---
# <span data-ttu-id="716a2-103">Show-Command</span><span class="sxs-lookup"><span data-stu-id="716a2-103">Show-Command</span></span>

## <span data-ttu-id="716a2-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="716a2-104">SYNOPSIS</span></span>
<span data-ttu-id="716a2-105">Visar PowerShell-kommando information i ett grafiskt fönster.</span><span class="sxs-lookup"><span data-stu-id="716a2-105">Displays PowerShell command information in a graphical window.</span></span>

## <span data-ttu-id="716a2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="716a2-106">SYNTAX</span></span>

```
Show-Command [[-Name] <String>] [-Height <Double>] [-Width <Double>] [-NoCommonParameter]
 [-ErrorPopup] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="716a2-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="716a2-107">DESCRIPTION</span></span>

<span data-ttu-id="716a2-108">Med `Show-Command` cmdleten kan du skapa ett PowerShell-kommando i ett kommando fönster.</span><span class="sxs-lookup"><span data-stu-id="716a2-108">The `Show-Command` cmdlet lets you create a PowerShell command in a command window.</span></span> <span data-ttu-id="716a2-109">Du kan använda funktionerna i kommando fönstret för att köra kommandot eller låta det returnera kommandot till dig.</span><span class="sxs-lookup"><span data-stu-id="716a2-109">You can use the features of the command window to run the command or have it return the command to you.</span></span>

<span data-ttu-id="716a2-110">`Show-Command` är ett mycket användbart undervisnings-och utbildnings verktyg.</span><span class="sxs-lookup"><span data-stu-id="716a2-110">`Show-Command` is a very useful teaching and learning tool.</span></span> <span data-ttu-id="716a2-111">`Show-Command` fungerar på alla kommando typer, inklusive cmdlets, functions, arbetsflöden och CIM-kommandon.</span><span class="sxs-lookup"><span data-stu-id="716a2-111">`Show-Command` works on all command types, including cmdlets, functions, workflows and CIM commands.</span></span>

<span data-ttu-id="716a2-112">Utan parametrar `Show-Command` visar ett kommando fönster som visar alla tillgängliga kommandon i alla installerade moduler.</span><span class="sxs-lookup"><span data-stu-id="716a2-112">Without parameters, `Show-Command` displays a command window that lists all available commands in all installed modules.</span></span> <span data-ttu-id="716a2-113">Om du vill hitta kommandona i en modul väljer du modulen i list rutan moduler.</span><span class="sxs-lookup"><span data-stu-id="716a2-113">To find the commands in a module, select the module from the Modules drop-down list.</span></span> <span data-ttu-id="716a2-114">Klicka på kommando namnet för att välja ett kommando.</span><span class="sxs-lookup"><span data-stu-id="716a2-114">To select a command, click the command name.</span></span>

<span data-ttu-id="716a2-115">Om du vill använda kommando fönstret väljer du ett kommando, antingen genom att använda namnet eller genom att klicka på kommando namnet i listan **kommandon** .</span><span class="sxs-lookup"><span data-stu-id="716a2-115">To use the command window, select a command, either by using the Name or by clicking the command name in the **Commands** list.</span></span> <span data-ttu-id="716a2-116">Varje parameter uppsättning visas på en separat flik. Asterisker visar de obligatoriska parametrarna.</span><span class="sxs-lookup"><span data-stu-id="716a2-116">Each parameter set is displayed on a separate tab. Asterisks indicate the mandatory parameters.</span></span> <span data-ttu-id="716a2-117">Ange värden för en parameter genom att skriva värdet i text rutan eller välja värdet i list rutan.</span><span class="sxs-lookup"><span data-stu-id="716a2-117">To enter values for a parameter, type the value in the text box or select the value from the drop-down box.</span></span> <span data-ttu-id="716a2-118">Klicka för att markera kryss rutan parameter för att lägga till en växlings parameter.</span><span class="sxs-lookup"><span data-stu-id="716a2-118">To add a switch parameter, click to select the parameter check box.</span></span>

<span data-ttu-id="716a2-119">När du är klar kan du klicka på **Kopiera** för att kopiera kommandot som du har skapat till Urklipp eller klicka på **Kör** för att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="716a2-119">When you're ready, you can click **Copy** to copy the command that you've created to the clipboard or click **Run** to run the command.</span></span> <span data-ttu-id="716a2-120">Du kan också använda parametern **Passthru** för att returnera kommandot till värd programmet, till exempel PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="716a2-120">You can also use the **PassThru** parameter to return the command to the host program, such as the PowerShell console.</span></span> <span data-ttu-id="716a2-121">Om du vill avbryta kommando markeringen och återgå till vyn som visar alla kommandon, trycker du på CTRL och klickar på det valda kommandot.</span><span class="sxs-lookup"><span data-stu-id="716a2-121">To cancel the command selection and return to the view that displays all commands, press Ctrl and click the selected command.</span></span>

<span data-ttu-id="716a2-122">I PowerShell ISE (Integrated Scripting Environment) visas en variant av `Show-Command` fönstret som standard.</span><span class="sxs-lookup"><span data-stu-id="716a2-122">In the PowerShell Integrated Scripting Environment (ISE), a variation of the `Show-Command` window is displayed by default.</span></span> <span data-ttu-id="716a2-123">Information om hur du använder det här kommando fönstret finns i hjälp avsnitten för PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="716a2-123">For information about using this command window, see the PowerShell ISE Help topics.</span></span>

<span data-ttu-id="716a2-124">Den här cmdleten introducerades om i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="716a2-124">This cmdlet was reintroduced in PowerShell 7.</span></span> 

<span data-ttu-id="716a2-125">Eftersom denna cmdlet kräver ett användar gränssnitt fungerar den inte på Windows Server Core eller Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="716a2-125">Because this cmdlet requires a user interface, it does not work on Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="716a2-126">Den här cmdleten är endast tillgänglig på Windows-system som stöder Windows-skrivbordet.</span><span class="sxs-lookup"><span data-stu-id="716a2-126">This cmdlet is only available on Windows systems that support the Windows Desktop.</span></span>

## <span data-ttu-id="716a2-127">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="716a2-127">EXAMPLES</span></span>

### <span data-ttu-id="716a2-128">Exempel 1: Öppna kommando fönstret</span><span class="sxs-lookup"><span data-stu-id="716a2-128">Example 1: Open the Commands window</span></span>

<span data-ttu-id="716a2-129">I det här exemplet visas standardvyn för `Show-Command` fönstret.</span><span class="sxs-lookup"><span data-stu-id="716a2-129">This example displays the default view of the `Show-Command` window.</span></span> <span data-ttu-id="716a2-130">**Kommando** fönstret visar en lista över alla kommandon i alla moduler som är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="716a2-130">The **Commands** window displays a list of all commands in all modules that are installed on the computer.</span></span>

```powershell
Show-Command
```

### <span data-ttu-id="716a2-131">Exempel 2: öppna en cmdlet i kommando fönstret</span><span class="sxs-lookup"><span data-stu-id="716a2-131">Example 2: Open a cmdlet in the Commands window</span></span>

<span data-ttu-id="716a2-132">I det här exemplet visas `Invoke-Command` cmdlet: en i **kommando** fönstret.</span><span class="sxs-lookup"><span data-stu-id="716a2-132">This example display the `Invoke-Command` cmdlet in the **Command** window.</span></span> <span data-ttu-id="716a2-133">Du kan använda den här vyn för att köra `Invoke-Command` kommandon.</span><span class="sxs-lookup"><span data-stu-id="716a2-133">You can use this display to run `Invoke-Command` commands.</span></span>

```powershell
Show-Command -Name "Invoke-Command"
```

### <span data-ttu-id="716a2-134">Exempel 3: öppna en cmdlet med angivna parametrar</span><span class="sxs-lookup"><span data-stu-id="716a2-134">Example 3: Open a cmdlet with specified parameters</span></span>

<span data-ttu-id="716a2-135">Det här kommandot öppnar ett `Show-Command` fönster för `Connect-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="716a2-135">This command opens a `Show-Command` window for the`Connect-PSSession`cmdlet.</span></span>

```powershell
Show-Command -Name "Connect-PSSession" -Height 700 -Width 1000 -ErrorPopup
```

<span data-ttu-id="716a2-136">Parametrarna **height** och **width** anger dimensionen för kommando fönstret.</span><span class="sxs-lookup"><span data-stu-id="716a2-136">The **Height** and **Width** parameters specify the dimension of the command window.</span></span> <span data-ttu-id="716a2-137">**ErrorPopup** -parametern visar fel kommando fönstret.</span><span class="sxs-lookup"><span data-stu-id="716a2-137">The **ErrorPopup** parameter displays the error command window.</span></span>

<span data-ttu-id="716a2-138">När du klickar på **Kör** `Connect-PSSession` körs kommandot, precis som om du skrev `Connect-PSSession` kommandot på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="716a2-138">When you click **Run** , the `Connect-PSSession` command runs, just as would if you typed the `Connect-PSSession` command at the command line.</span></span>

### <span data-ttu-id="716a2-139">Exempel 4: Ange nya standard parameter värden för en cmdlet</span><span class="sxs-lookup"><span data-stu-id="716a2-139">Example 4: Specify new default parameter values for a cmdlet</span></span>

<span data-ttu-id="716a2-140">I det här exemplet används den `$PSDefaultParameterValues` automatiska variabeln för att ange nya standardvärden för parametrarna **height** , **width** och **ErrorPopup** för `Show-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="716a2-140">This example uses the `$PSDefaultParameterValues` automatic variable to set new default values for the **Height** , **Width** , and **ErrorPopup** parameters of the `Show-Command` cmdlet.</span></span>

```powershell
$PSDefaultParameterValues = @{
    "Show-Command:Height" = 700
    "Show-Command:Width" = 1000
    "Show-Command:ErrorPopup" = $True
}
```

<span data-ttu-id="716a2-141">Nu när du kör ett `Show-Command` kommando tillämpas de nya standardvärdena automatiskt.</span><span class="sxs-lookup"><span data-stu-id="716a2-141">Now when you run a `Show-Command` command, the new defaults are applied automatically.</span></span> <span data-ttu-id="716a2-142">Om du vill använda standardvärdena i varje PowerShell-session lägger du till `$PSDefaultParameterValues` variabeln i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="716a2-142">To use these default values in every PowerShell session, add the `$PSDefaultParameterValues` variable to your PowerShell profile.</span></span> <span data-ttu-id="716a2-143">Mer information finns i [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) och [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md).</span><span class="sxs-lookup"><span data-stu-id="716a2-143">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) and [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md).</span></span>

### <span data-ttu-id="716a2-144">Exempel 5: skicka utdata till en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="716a2-144">Example 5: Send output to a grid view</span></span>

<span data-ttu-id="716a2-145">Det här kommandot visar hur du använder- `Show-Command` och- `Out-GridView` cmdletarna tillsammans.</span><span class="sxs-lookup"><span data-stu-id="716a2-145">This command shows how to use the `Show-Command` and `Out-GridView` cmdlets together.</span></span>

```powershell
Show-Command Get-ChildItem | Out-GridView
```

<span data-ttu-id="716a2-146">Kommandot använder `Show-Command` cmdleten för att öppna ett kommando fönster för `Get-ChildItem` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="716a2-146">The command uses the `Show-Command` cmdlet to open a command window for the`Get-ChildItem`cmdlet.</span></span>
<span data-ttu-id="716a2-147">När du klickar på **Kör** -knappen `Get-ChildItem` körs kommandot och genererar utdata.</span><span class="sxs-lookup"><span data-stu-id="716a2-147">When you click the **Run** button, the `Get-ChildItem` command runs and generates output.</span></span> <span data-ttu-id="716a2-148">Pipeline-operatorn (|) skickar utdata från `Get-ChildItem` kommandot till `Out-GridView` cmdleten, som visar `Get-ChildItem` utdata i ett interaktivt fönster.</span><span class="sxs-lookup"><span data-stu-id="716a2-148">The pipeline operator ( | ) sends the output of the `Get-ChildItem` command to the `Out-GridView` cmdlet, which displays the `Get-ChildItem` output in an interactive window.</span></span>

### <span data-ttu-id="716a2-149">Exempel 6: Visa ett kommando som du skapar i kommando fönstret</span><span class="sxs-lookup"><span data-stu-id="716a2-149">Example 6: Display a command that you create in the Commands window</span></span>

<span data-ttu-id="716a2-150">I det här exemplet visas kommandot som du skapade i `Show-Command` fönstret.</span><span class="sxs-lookup"><span data-stu-id="716a2-150">This example shows the command that you created in the `Show-Command` window.</span></span> <span data-ttu-id="716a2-151">Kommandot använder parametern **Passthru** , som returnerar `Show-Command` resultatet i en sträng.</span><span class="sxs-lookup"><span data-stu-id="716a2-151">The command uses the **PassThru** parameter, which returns the `Show-Command` results in a string.</span></span>

```powershell
Show-Command -PassThru
```

```Output
Get-EventLog -LogName "Windows PowerShell" -Newest 5
```

<span data-ttu-id="716a2-152">Om du till exempel använder `Show-Command` fönstret för att skapa ett `Get-EventLog` kommando som hämtar de fem senaste händelserna i händelse loggen i Windows PowerShell, och sedan klickar på **OK** , returnerar kommandot de utdata som visas ovan.</span><span class="sxs-lookup"><span data-stu-id="716a2-152">For example, if you use the `Show-Command` window to create a `Get-EventLog` command that gets the five newest events in the Windows PowerShell event log, and then click **OK** , the command returns the output shown above.</span></span> <span data-ttu-id="716a2-153">Du kan lära dig mer om PowerShell genom att visa kommando strängen.</span><span class="sxs-lookup"><span data-stu-id="716a2-153">Viewing the command string helps you learn PowerShell.</span></span>

### <span data-ttu-id="716a2-154">Exempel 7: Spara ett kommando till en variabel</span><span class="sxs-lookup"><span data-stu-id="716a2-154">Example 7: Save a command to a variable</span></span>

<span data-ttu-id="716a2-155">Det här exemplet visar hur du kör kommando strängen som du får när du använder **Passthru** -parametern för `Show-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="716a2-155">This example shows how to run the command string that you get when you use the **PassThru** parameter of the `Show-Command` cmdlet.</span></span> <span data-ttu-id="716a2-156">Med den här strategin kan du se kommandot och använda det.</span><span class="sxs-lookup"><span data-stu-id="716a2-156">This strategy lets you see the command and use it.</span></span>

```powershell
$C = Show-Command -PassThru
$C
Invoke-Expression $C
```

```Output
Get-EventLog -LogName "PowerShell" -Newest 5

Index Time          EntryType   Source                 InstanceID Message
----- ----          ---------   ------                 ---------- -------
11520 Dec 16 16:37  Information Windows PowerShell            400 Engine state is changed from None to Available...
11519 Dec 16 16:37  Information Windows PowerShell            600 Provider "Variable" is Started. ...
11518 Dec 16 16:37  Information Windows PowerShell            600 Provider "Registry" is Started. ...
11517 Dec 16 16:37  Information Windows PowerShell            600 Provider "Function" is Started. ...
11516 Dec 16 16:37  Information Windows PowerShell            600 Provider "FileSystem" is Started. ...
```

<span data-ttu-id="716a2-157">Det första kommandot använder **Passthru** -parametern för `Show-Command` cmdleten och sparar resultatet av kommandot i `$C` variabeln.</span><span class="sxs-lookup"><span data-stu-id="716a2-157">The first command uses the **PassThru** parameter of the `Show-Command` cmdlet and saves the results of the command in the `$C` variable.</span></span> <span data-ttu-id="716a2-158">I det här fallet använder vi `Show-Command` fönstret för att skapa ett `Get-EventLog` kommando som hämtar de fem senaste händelserna i händelse loggen i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="716a2-158">In this case, we use the `Show-Command` window to create a `Get-EventLog` command that gets the five newest events in the Windows PowerShell event log.</span></span> <span data-ttu-id="716a2-159">När du klickar **OK** på OK `Show-Command` returneras kommando strängen som sparas i `$C` variabeln.</span><span class="sxs-lookup"><span data-stu-id="716a2-159">When you click **OK** , `Show-Command` returns the command string, which is saved in the `$C` variable.</span></span>

### <span data-ttu-id="716a2-160">Exempel 8: spara utdata från ett kommando till en variabel</span><span class="sxs-lookup"><span data-stu-id="716a2-160">Example 8: Save the output of a command to a variable</span></span>

<span data-ttu-id="716a2-161">I det här exemplet används parametern **ErrorPopup** för att spara utdata från ett kommando i en variabel.</span><span class="sxs-lookup"><span data-stu-id="716a2-161">This example uses the **ErrorPopup** parameter to save the output of a command in a variable.</span></span>

```powershell
$P = Show-Command Get-Process -ErrorPopup
$P
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    473      33    94096     112532   709     2.06   4492 powershell
```

<span data-ttu-id="716a2-162">Förutom att visa fel i ett fönster returnerar **ErrorPopup** kommandoutdata till det aktuella kommandot, i stället för att skapa ett nytt kommando.</span><span class="sxs-lookup"><span data-stu-id="716a2-162">In addition to displaying errors in a window, **ErrorPopup** returns command output to the current command, instead of creating a new command.</span></span> <span data-ttu-id="716a2-163">När du kör det här kommandot `Show-Command` öppnas fönstret.</span><span class="sxs-lookup"><span data-stu-id="716a2-163">When you run this command, the `Show-Command` window opens.</span></span> <span data-ttu-id="716a2-164">Du kan använda fönster funktionerna för att ange parameter värden.</span><span class="sxs-lookup"><span data-stu-id="716a2-164">You can use the window features to set parameter values.</span></span> <span data-ttu-id="716a2-165">Kör kommandot genom att klicka på knappen **Kör** i `Show-Command` fönstret.</span><span class="sxs-lookup"><span data-stu-id="716a2-165">To run the command, click the **Run** button in the `Show-Command` window.</span></span>

## <span data-ttu-id="716a2-166">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="716a2-166">PARAMETERS</span></span>

### <span data-ttu-id="716a2-167">-ErrorPopup</span><span class="sxs-lookup"><span data-stu-id="716a2-167">-ErrorPopup</span></span>

<span data-ttu-id="716a2-168">Anger att cmdleten visar fel i ett popup-fönster, förutom att visa dem på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="716a2-168">Indicates that the cmdlet displays errors in a pop-up window, in addition to displaying them at the command line.</span></span> <span data-ttu-id="716a2-169">Som standard visas felet bara på kommando raden när ett kommando som körs i ett `Show-Command` fönster genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="716a2-169">By default, when a command that is run in a `Show-Command` window generates an error, the error is displayed only at the command line.</span></span>

<span data-ttu-id="716a2-170">När du kör kommandot (med knappen **Kör** i `Show-Command` fönstret) returnerar parametern **ErrorPopup** kommando resultatet till det aktuella kommandot, i stället för att köra kommandot och returnera utdata till ett nytt kommando.</span><span class="sxs-lookup"><span data-stu-id="716a2-170">Also, when you run the command (by using the **Run** button in the `Show-Command` window), the **ErrorPopup** parameter returns the command results to the current command, instead of running the command and returning its output to a new command.</span></span> <span data-ttu-id="716a2-171">Du kan använda den här funktionen för att spara kommando resultatet i en variabel.</span><span class="sxs-lookup"><span data-stu-id="716a2-171">You can use this feature to save the command results in a variable.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="716a2-172">-Höjd</span><span class="sxs-lookup"><span data-stu-id="716a2-172">-Height</span></span>

<span data-ttu-id="716a2-173">Anger `Show-Command` fönstrets höjd i bild punkter.</span><span class="sxs-lookup"><span data-stu-id="716a2-173">Specifies the height of the `Show-Command` window in pixels.</span></span> <span data-ttu-id="716a2-174">Ange ett värde mellan 300 och antalet bild punkter i skärmupplösningen.</span><span class="sxs-lookup"><span data-stu-id="716a2-174">Enter a value between 300 and the number of pixels in the screen resolution.</span></span> <span data-ttu-id="716a2-175">Om värdet är för stort för att visa kommando fönstret på skärmen `Show-Command` genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="716a2-175">If the value is too large to display the command window on the screen, `Show-Command` generates an error.</span></span> <span data-ttu-id="716a2-176">Standard höjden är 600 bild punkter.</span><span class="sxs-lookup"><span data-stu-id="716a2-176">The default height is 600 pixels.</span></span> <span data-ttu-id="716a2-177">För ett `Show-Command` kommando som innehåller parametern **Name** är standard höjden 300 bild punkter.</span><span class="sxs-lookup"><span data-stu-id="716a2-177">For a `Show-Command` command that includes the **Name** parameter, the default height is 300 pixels.</span></span>

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="716a2-178">-Name</span><span class="sxs-lookup"><span data-stu-id="716a2-178">-Name</span></span>

<span data-ttu-id="716a2-179">Visar ett kommando fönster för det angivna kommandot.</span><span class="sxs-lookup"><span data-stu-id="716a2-179">Displays a command window for the specified command.</span></span> <span data-ttu-id="716a2-180">Ange namnet på ett kommando, till exempel namnet på ett cmdlet-, Function-eller CIM-kommando.</span><span class="sxs-lookup"><span data-stu-id="716a2-180">Enter the name of one command, such as the name of a cmdlet, function, or CIM command.</span></span> <span data-ttu-id="716a2-181">Om du utelämnar den här parametern `Show-Command` visas ett kommando fönster som visar alla PowerShell-kommandon i alla moduler som är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="716a2-181">If you omit this parameter, `Show-Command` displays a command window that lists all of the PowerShell commands in all modules installed on the computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CommandName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="716a2-182">-NoCommonParameter</span><span class="sxs-lookup"><span data-stu-id="716a2-182">-NoCommonParameter</span></span>

<span data-ttu-id="716a2-183">Anger att denna cmdlet utelämnar avsnittet gemensamma parametrar i kommando visningen.</span><span class="sxs-lookup"><span data-stu-id="716a2-183">Indicates that this cmdlet omits the Common Parameters section of the command display.</span></span> <span data-ttu-id="716a2-184">Som standard visas de gemensamma parametrarna i ett expanderat avsnitt längst ned i kommando fönstret.</span><span class="sxs-lookup"><span data-stu-id="716a2-184">By default, the Common Parameters appear in an expandable section at the bottom of the command window.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="716a2-185">– PassThru</span><span class="sxs-lookup"><span data-stu-id="716a2-185">-PassThru</span></span>

<span data-ttu-id="716a2-186">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="716a2-186">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="716a2-187">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="716a2-187">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="716a2-188">Om du vill köra kommando strängen kopierar du och klistrar in den i kommando tolken eller sparar den i en variabel och använder `Invoke-Expression` cmdleten för att köra strängen i variabeln.</span><span class="sxs-lookup"><span data-stu-id="716a2-188">To run the command string, copy and paste it at the command prompt or save it in a variable and use the `Invoke-Expression` cmdlet to run the string in the variable.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="716a2-189">-Bredd</span><span class="sxs-lookup"><span data-stu-id="716a2-189">-Width</span></span>

<span data-ttu-id="716a2-190">Anger `Show-Command` fönstrets bredd i bild punkter.</span><span class="sxs-lookup"><span data-stu-id="716a2-190">Specifies the width of the `Show-Command` window in pixels.</span></span> <span data-ttu-id="716a2-191">Ange ett värde mellan 300 och antalet bild punkter i skärmupplösningen.</span><span class="sxs-lookup"><span data-stu-id="716a2-191">Enter a value between 300 and the number of pixels in the screen resolution.</span></span> <span data-ttu-id="716a2-192">Om värdet är för stort för att visa kommando fönstret på skärmen `Show-Command` genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="716a2-192">If the value is too large to display the command window on the screen, `Show-Command` generates an error.</span></span> <span data-ttu-id="716a2-193">Standard bredden är 300 bild punkter.</span><span class="sxs-lookup"><span data-stu-id="716a2-193">The default width is 300 pixels.</span></span>

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="716a2-194">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="716a2-194">CommonParameters</span></span>

<span data-ttu-id="716a2-195">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="716a2-195">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="716a2-196">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="716a2-196">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="716a2-197">INDATA</span><span class="sxs-lookup"><span data-stu-id="716a2-197">INPUTS</span></span>

### <span data-ttu-id="716a2-198">Inget</span><span class="sxs-lookup"><span data-stu-id="716a2-198">None</span></span>

<span data-ttu-id="716a2-199">Du kan inte skicka pipe-ininformation till `Show-Command` .</span><span class="sxs-lookup"><span data-stu-id="716a2-199">You cannot pipe input to `Show-Command`.</span></span>

## <span data-ttu-id="716a2-200">UTDATA</span><span class="sxs-lookup"><span data-stu-id="716a2-200">OUTPUTS</span></span>

### <span data-ttu-id="716a2-201">Ingen, system. String, system. Object</span><span class="sxs-lookup"><span data-stu-id="716a2-201">None, System.String, System.Object</span></span>

<span data-ttu-id="716a2-202">När du använder parametern **Passthru** `Show-Command` returneras en kommando sträng.</span><span class="sxs-lookup"><span data-stu-id="716a2-202">When you use the **PassThru** parameter, `Show-Command` returns a command string.</span></span> <span data-ttu-id="716a2-203">När du använder parametern **ErrorPopup** `Show-Command` returneras kommandoutdata (alla objekt).</span><span class="sxs-lookup"><span data-stu-id="716a2-203">When you use the **ErrorPopup** parameter, `Show-Command` returns the command output (any object).</span></span> <span data-ttu-id="716a2-204">Annars `Show-Command` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="716a2-204">Otherwise, `Show-Command` does not generate any output.</span></span>

## <span data-ttu-id="716a2-205">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="716a2-205">NOTES</span></span>

<span data-ttu-id="716a2-206">`Show-Command` fungerar inte i fjärrsessioner.</span><span class="sxs-lookup"><span data-stu-id="716a2-206">`Show-Command` does not work in remote sessions.</span></span>

## <span data-ttu-id="716a2-207">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="716a2-207">RELATED LINKS</span></span>

