---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionoption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionOption
ms.openlocfilehash: c8d51054b2beb4da0e7d54280d85b9688928147e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267621"
---
# <span data-ttu-id="45036-103">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="45036-103">New-PSSessionOption</span></span>

## <span data-ttu-id="45036-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="45036-104">SYNOPSIS</span></span>
<span data-ttu-id="45036-105">Skapar ett objekt som innehåller avancerade alternativ för en PSSession.</span><span class="sxs-lookup"><span data-stu-id="45036-105">Creates an object that contains advanced options for a PSSession.</span></span>

## <span data-ttu-id="45036-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="45036-106">SYNTAX</span></span>

```
New-PSSessionOption [-MaximumRedirection <Int32>] [-NoCompression] [-NoMachineProfile] [-Culture <CultureInfo>]
 [-UICulture <CultureInfo>] [-MaximumReceivedDataSizePerCommand <Int32>] [-MaximumReceivedObjectSize <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-MaxConnectionRetryCount <Int32>]
 [-ApplicationArguments <PSPrimitiveDictionary>] [-OpenTimeout <Int32>] [-CancelTimeout <Int32>]
 [-IdleTimeout <Int32>] [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <AuthenticationMechanism>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [-IncludePortInSPN] [<CommonParameters>]
```

## <span data-ttu-id="45036-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="45036-107">DESCRIPTION</span></span>

<span data-ttu-id="45036-108">`New-PSSessionOption`Cmdleten skapar ett objekt som innehåller avancerade alternativ för en **PSSession** (User-Managed session).</span><span class="sxs-lookup"><span data-stu-id="45036-108">The `New-PSSessionOption` cmdlet creates an object that contains advanced options for a user-managed session ( **PSSession** ).</span></span> <span data-ttu-id="45036-109">Du kan använda objektet som värdet för parametern **SessionOption** för cmdletar som skapar en **PSSession** , till exempel, `New-PSSession` `Enter-PSSession` och `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="45036-109">You can use the object as the value of the **SessionOption** parameter of cmdlets that create a **PSSession** , such as `New-PSSession`, `Enter-PSSession`, and `Invoke-Command`.</span></span>

<span data-ttu-id="45036-110">Utan parametrar `New-PSSessionOption` genererar ett objekt som innehåller standardvärdena för alla alternativ.</span><span class="sxs-lookup"><span data-stu-id="45036-110">Without parameters, `New-PSSessionOption` generates an object that contains the default values for all of the options.</span></span> <span data-ttu-id="45036-111">Eftersom alla egenskaper kan redige ras kan du använda det resulterande objektet som mall och skapa standard alternativ objekt för ditt företag.</span><span class="sxs-lookup"><span data-stu-id="45036-111">Because all of the properties can be edited, you can use the resulting object as a template, and create standard option objects for your enterprise.</span></span>

<span data-ttu-id="45036-112">Du kan också spara ett alternativ för session i `$PSSessionOption` Preference-variabeln.</span><span class="sxs-lookup"><span data-stu-id="45036-112">You can also save a session option object in the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="45036-113">Värdena för den här variabeln upprättar nya standardvärden för session-alternativen.</span><span class="sxs-lookup"><span data-stu-id="45036-113">The values of this variable establish new default values for the session options.</span></span> <span data-ttu-id="45036-114">De träder i kraft när inga sessionsinställningar har ställts in för sessionen och de har företräde framför alternativ som angetts i konfigurationen av sessionen, men du kan åsidosätta dem genom att ange sessionsinställningar eller ett alternativ objekt för session i en cmdlet som skapar en session.</span><span class="sxs-lookup"><span data-stu-id="45036-114">They effective when no session options are set for the session and they take precedence over options set in the session configuration, but you can override them by specifying session options or a session option object in a cmdlet that creates a session.</span></span> <span data-ttu-id="45036-115">Mer information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="45036-115">For more information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="45036-116">När du använder ett alternativ objekt för session i en cmdlet som skapar en session, prioriteras värdena för sessions-alternativ framför standardvärden för sessioner som angetts i variabeln $PSSessionOption och i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="45036-116">When you use a session option object in a cmdlet that creates a session, the session option values take precedence over default values for sessions set in the $PSSessionOption preference variable and in the session configuration.</span></span> <span data-ttu-id="45036-117">De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="45036-117">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span> <span data-ttu-id="45036-118">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="45036-118">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="45036-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="45036-119">EXAMPLES</span></span>

### <span data-ttu-id="45036-120">Exempel 1: skapa ett standard alternativ för session</span><span class="sxs-lookup"><span data-stu-id="45036-120">Example 1: Create a default session option</span></span>

<span data-ttu-id="45036-121">Det här kommandot skapar ett alternativ för session som innehåller alla standardvärden.</span><span class="sxs-lookup"><span data-stu-id="45036-121">This command creates a session option object that has all of the default values.</span></span>

```powershell
New-PSSessionOption
```

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

### <span data-ttu-id="45036-122">Exempel 2: Konfigurera en session med hjälp av ett session alternativ-objekt</span><span class="sxs-lookup"><span data-stu-id="45036-122">Example 2: Configure a session by using a session option object</span></span>

<span data-ttu-id="45036-123">I det här exemplet visas hur du konfigurerar en session med hjälp av ett alternativ objekt för session.</span><span class="sxs-lookup"><span data-stu-id="45036-123">This example shows how to use a session option object to configure a session.</span></span>

```powershell
$pso = New-PSSessionOption -Culture "fr-fr" -MaximumReceivedObjectSize 10MB
New-PSSession -ComputerName Server01 -SessionOption $pso
```

<span data-ttu-id="45036-124">Det första kommandot skapar ett nytt alternativ för session och sparar det i `$pso` variabelns värde.</span><span class="sxs-lookup"><span data-stu-id="45036-124">The first command creates a new session option object and saves it in the value of the `$pso` variable.</span></span> <span data-ttu-id="45036-125">Det andra kommandot använder `New-PSSession` cmdleten för att skapa en session på Server01-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="45036-125">The second command uses the `New-PSSession` cmdlet to create a session on the Server01 remote computer.</span></span> <span data-ttu-id="45036-126">Kommandot använder Session-objektet i värdet för `$pso` variabeln som värdet för parametern **SessionOption** för kommandot.</span><span class="sxs-lookup"><span data-stu-id="45036-126">The command uses the session option object in the value of the `$pso` variable as the value of the **SessionOption** parameter of the command.</span></span>

### <span data-ttu-id="45036-127">Exempel 3: starta en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="45036-127">Example 3: Start an interactive session</span></span>

<span data-ttu-id="45036-128">Det här kommandot använder `Enter-PSSession` cmdleten för att starta en interaktiv session med Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="45036-128">This command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

```powershell
Enter-PSSession -ComputerName Server01 -SessionOption (New-PSSessionOption -NoEncryption -NoCompression)
```

<span data-ttu-id="45036-129">Värdet för parametern **SessionOption** är ett `New-PSSessionOption` kommando som har parametrarna Encryption och **nocompression** . **NoEncryption**</span><span class="sxs-lookup"><span data-stu-id="45036-129">The value of the **SessionOption** parameter is a `New-PSSessionOption` command that has the **NoEncryption** and **NoCompression** parameters.</span></span>

<span data-ttu-id="45036-130">`New-PSSessionOption`Kommandot omges av parenteser för att kontrol lera att det körs före `Enter-PSSession` kommandot.</span><span class="sxs-lookup"><span data-stu-id="45036-130">The `New-PSSessionOption` command is enclosed in parentheses to make sure that it runs before the `Enter-PSSession` command.</span></span>

### <span data-ttu-id="45036-131">Exempel 4: ändra ett alternativ objekt för session</span><span class="sxs-lookup"><span data-stu-id="45036-131">Example 4: Modify a session option object</span></span>

<span data-ttu-id="45036-132">Det här exemplet visar att du kan ändra objektet Session-alternativ.</span><span class="sxs-lookup"><span data-stu-id="45036-132">This example demonstrates that you can modify the session option object.</span></span> <span data-ttu-id="45036-133">Alla egenskaper har läs-/skriv värden.</span><span class="sxs-lookup"><span data-stu-id="45036-133">All properties have read/write values.</span></span>

```powershell
$a = New-PSSessionOption
$a.OpenTimeout
```

```Output
Days              : 0
Hours             : 0
Minutes           : 3
Seconds           : 0
Milliseconds      : 0
Ticks             : 1800000000
TotalDays         : 0.00208333333333333
TotalHours        : 0.05
TotalMinutes      : 3
TotalSeconds      : 180
TotalMilliseconds : 180000
```

```powershell
$a.UICulture = (Get-UICulture)
$a.OpenTimeout = (New-Timespan -Minutes 4)
$a.MaximumConnectionRedirectionCount = 1
$a
```

```Output
MaximumConnectionRedirectionCount : 1
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         : en-US
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:04:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

<span data-ttu-id="45036-134">Använd den här metoden för att skapa ett standard-sessionsobjekt för ditt företag och skapa sedan anpassade versioner av det för specifika användnings områden.</span><span class="sxs-lookup"><span data-stu-id="45036-134">Use this method to create a standard session object for your enterprise, and then create customized versions of it for particular uses.</span></span>

### <span data-ttu-id="45036-135">Exempel 5: skapa en inställnings variabel</span><span class="sxs-lookup"><span data-stu-id="45036-135">Example 5: Create a preference variable</span></span>

<span data-ttu-id="45036-136">Det här kommandot skapar en `$PSSessionOption` inställnings variabel.</span><span class="sxs-lookup"><span data-stu-id="45036-136">This command creates a `$PSSessionOption` preference variable.</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -OpenTimeOut 120000
```

<span data-ttu-id="45036-137">När `$PSSessionOption` Preference-variabeln inträffar i sessionen, fastställer den standardvärden för alternativ i de sessioner som skapas med hjälp av `New-PSSession` `Enter-PSSession` cmdletarna,, och `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="45036-137">When the `$PSSessionOption` preference variable occurs in the session, it establishes default values for options in the sessions that are created by using the `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="45036-138">Om du vill göra `$PSSessionOption` variabeln tillgänglig i alla sessioner lägger du till den i din PowerShell-session och i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="45036-138">To make the `$PSSessionOption` variable available in all sessions, add it to your PowerShell session and to your PowerShell profile.</span></span>

<span data-ttu-id="45036-139">Mer information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="45036-139">For more information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>
<span data-ttu-id="45036-140">Mer information om profiler finns [about_Profiles](About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="45036-140">For more information about profiles, see [about_Profiles](About/about_Profiles.md).</span></span>

### <span data-ttu-id="45036-141">Exempel 6: uppfylla kraven för en fjärrsessions-konfiguration</span><span class="sxs-lookup"><span data-stu-id="45036-141">Example 6: Fulfill the requirements for a remote session configuration</span></span>

<span data-ttu-id="45036-142">Det här exemplet visar hur du använder ett **SessionOption** -objekt för att uppfylla kraven för en fjärrsessions-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="45036-142">This example shows how to use a **SessionOption** object to fulfill the requirements for a remote session configuration.</span></span>

```powershell
$skipCN = New-PSSessionOption -SkipCNCheck
New-PSSession -ComputerName 171.09.21.207 -UseSSL -Credential Domain01\User01 -SessionOption $SkipCN
```

<span data-ttu-id="45036-143">Det första kommandot använder `New-PSSessionOption` cmdleten för att skapa ett session-objekt som har egenskapen **SkipCNCheck** .</span><span class="sxs-lookup"><span data-stu-id="45036-143">The first command uses the `New-PSSessionOption` cmdlet to create a session option object that has the **SkipCNCheck** property.</span></span> <span data-ttu-id="45036-144">Kommandot sparar det resulterande sessions-objektet i `$skipCN` variabeln.</span><span class="sxs-lookup"><span data-stu-id="45036-144">The command saves the resulting session object in the `$skipCN` variable.</span></span>

<span data-ttu-id="45036-145">Det andra kommandot använder `New-PSSession` cmdleten för att skapa en ny session på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="45036-145">The second command uses the `New-PSSession` cmdlet to create a new session on a remote computer.</span></span> <span data-ttu-id="45036-146">`$skipCN`Check variabeln används i värdet för parametern **SessionOption** .</span><span class="sxs-lookup"><span data-stu-id="45036-146">The `$skipCN` check variable is used in the value of the **SessionOption** parameter.</span></span>

<span data-ttu-id="45036-147">Eftersom datorn identifieras med IP-adressen matchar inte värdet för parametern **computername** något av de gemensamma namnen i certifikatet som används för Secure SOCKETS Layer (SSL).</span><span class="sxs-lookup"><span data-stu-id="45036-147">Because the computer is identified by its IP address, the value of the **ComputerName** parameter does not match any of the common names in the certificate that is used for Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="45036-148">Därför krävs alternativet **SkipCNCheck** .</span><span class="sxs-lookup"><span data-stu-id="45036-148">As a result, the **SkipCNCheck** option is required.</span></span>

### <span data-ttu-id="45036-149">Exempel 7: gör argument tillgängliga för en fjärrsession</span><span class="sxs-lookup"><span data-stu-id="45036-149">Example 7: Make arguments available to a remote session</span></span>

<span data-ttu-id="45036-150">Det här exemplet visar hur du använder **ApplicationArguments** -parametern för `New-PSSessionOption` cmdleten för att göra ytterligare data tillgängliga för fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="45036-150">This example shows how to use the **ApplicationArguments** parameter of the `New-PSSessionOption` cmdlet to make additional data available to the remote session.</span></span>

```powershell
$team = @{Team="IT"; Use="Testing"}
$TeamOption = New-PSSessionOption -ApplicationArguments $team
$s = New-PSSession -ComputerName Server01 -SessionOption $TeamOption
Invoke-Command -Session $s {$PSSenderInfo.ApplicationArguments}
```

```Output
Name                 Value
----                 -----
Team                 IT
Use                  Testing
PSVersionTable       {CLRVersion, BuildVersion, PSVersion, WSManStackVersion...}
```

```powershell
Invoke-Command -Session $s {
  if ($PSSenderInfo.ApplicationArguments.Use -ne "Testing") {
    .\logFiles.ps1
  }
  else {
    "Just testing."
  }
}
```

```Output
Just testing.
```

<span data-ttu-id="45036-151">Det första kommandot skapar en hash-tabell med två nycklar, **team** och **användning**.</span><span class="sxs-lookup"><span data-stu-id="45036-151">The first command creates a hash table with two keys, **Team** and **Use**.</span></span> <span data-ttu-id="45036-152">Kommandot sparar hash-tabellen i `$team` variabeln.</span><span class="sxs-lookup"><span data-stu-id="45036-152">The command saves the hash table in the `$team` variable.</span></span> <span data-ttu-id="45036-153">Mer information om hash-tabeller finns i [about_Hash_Tables](about/about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="45036-153">For more information about hash tables, see [about_Hash_Tables](about/about_Hash_Tables.md).</span></span>

<span data-ttu-id="45036-154">Därefter `New-PSSessionOption` skapar cmdleten med hjälp av parametern **ApplicationArguments** ett alternativ för session som sparats i `$team` variabeln.</span><span class="sxs-lookup"><span data-stu-id="45036-154">Next, the `New-PSSessionOption` cmdlet, using the **ApplicationArguments** parameter, creates a session option object saved in the `$team` variable.</span></span> <span data-ttu-id="45036-155">När `New-PSSessionOption` skapar objektet Session, konverterar det automatiskt hash-tabellen i värdet för parametern **ApplicationArguments** till en primitiv ord lista så att data kan överföras till fjärrsessionen på ett tillförlitligt sätt.</span><span class="sxs-lookup"><span data-stu-id="45036-155">When `New-PSSessionOption` creates the session option object, it automatically converts the hash table in the value of the **ApplicationArguments** parameter to a primitive dictionary so the data can be reliably transmitted to the remote session.</span></span>

<span data-ttu-id="45036-156">`New-PSSession`Cmdleten startar en session på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="45036-156">The `New-PSSession` cmdlet starts a session on the Server01 computer.</span></span> <span data-ttu-id="45036-157">Parametern **SessionOption** används för att inkludera alternativen i `$teamOption` variabeln.</span><span class="sxs-lookup"><span data-stu-id="45036-157">It uses the **SessionOption** parameter to include the options in the `$teamOption` variable.</span></span>

<span data-ttu-id="45036-158">`Invoke-Command`Cmdleten visar att data i `$team` variabeln är tillgängliga för kommandon i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="45036-158">The `Invoke-Command` cmdlet demonstrates that the data in the `$team` variable is available to commands in the remote session.</span></span> <span data-ttu-id="45036-159">Data visas i egenskapen **ApplicationArguments** för den `$PSSenderInfo` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="45036-159">The data appears in the **ApplicationArguments** property of the `$PSSenderInfo` automatic variable.</span></span>

<span data-ttu-id="45036-160">Den slutgiltiga `Invoke-Command` visar hur data kan användas.</span><span class="sxs-lookup"><span data-stu-id="45036-160">The final `Invoke-Command` shows how the data might be used.</span></span>

## <span data-ttu-id="45036-161">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="45036-161">PARAMETERS</span></span>

### <span data-ttu-id="45036-162">-ApplicationArguments</span><span class="sxs-lookup"><span data-stu-id="45036-162">-ApplicationArguments</span></span>

<span data-ttu-id="45036-163">Anger en primitiv ord lista som skickas till fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="45036-163">Specifies a primitive dictionary that is sent to the remote session.</span></span> <span data-ttu-id="45036-164">Kommandon och skript i fjärrsessionen, inklusive start skript i konfigurationen av sessionen, kan hitta den här ord listan i egenskapen **ApplicationArguments** för den `$PSSenderInfo` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="45036-164">Commands and scripts in the remote session, including startup scripts in the session configuration, can find this dictionary in the **ApplicationArguments** property of the `$PSSenderInfo` automatic variable.</span></span> <span data-ttu-id="45036-165">Du kan använda den här parametern för att skicka data till fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="45036-165">You can use this parameter to send data to the remote session.</span></span>

<span data-ttu-id="45036-166">Mer information finns i [about_Hash_Tables](about/about_Hash_Tables.md), [about_Session_Configurations](About/about_Session_Configurations.md)och [about_Automatic_Variables](about/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="45036-166">For more information, see [about_Hash_Tables](about/about_Hash_Tables.md), [about_Session_Configurations](About/about_Session_Configurations.md), and [about_Automatic_Variables](about/about_Automatic_Variables.md).</span></span>

```yaml
Type: System.Management.Automation.PSPrimitiveDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45036-167">-CancelTimeout</span><span class="sxs-lookup"><span data-stu-id="45036-167">-CancelTimeout</span></span>

<span data-ttu-id="45036-168">Anger hur lång tid PowerShell väntar på att en avbrotts åtgärd (CTRL + C) ska slutföras innan den slutar.</span><span class="sxs-lookup"><span data-stu-id="45036-168">Determines how long PowerShell waits for a cancel operation (CTRL+C) to finish before ending it.</span></span>
<span data-ttu-id="45036-169">Ange ett värde i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="45036-169">Enter a value in milliseconds.</span></span>

<span data-ttu-id="45036-170">Standardvärdet är 60000 (en minut).</span><span class="sxs-lookup"><span data-stu-id="45036-170">The default value is 60000 (one minute).</span></span> <span data-ttu-id="45036-171">Värdet 0 (noll) innebär ingen tids gräns. kommandot fortsätter på obestämd tid.</span><span class="sxs-lookup"><span data-stu-id="45036-171">A value of 0 (zero) means no time-out; the command continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: CancelTimeoutMSec

Required: False
Position: Named
Default value: 60000
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45036-172">– Kultur</span><span class="sxs-lookup"><span data-stu-id="45036-172">-Culture</span></span>

<span data-ttu-id="45036-173">Anger kulturen som ska användas för sessionen.</span><span class="sxs-lookup"><span data-stu-id="45036-173">Specifies the culture to use for the session.</span></span> <span data-ttu-id="45036-174">Ange ett kultur namn i `<languagecode2>-<country/regioncode2>` formatet (t `ja-JP` . ex.), en variabel som innehåller ett **CultureInfo** -objekt eller ett kommando som hämtar ett **CultureInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="45036-174">Enter a culture name in `<languagecode2>-<country/regioncode2>` format (like `ja-JP`), a variable that contains a **CultureInfo** object, or a command that gets a **CultureInfo** object.</span></span>

<span data-ttu-id="45036-175">Standardvärdet är `$Null` och kulturen som anges i operativ systemet används i sessionen.</span><span class="sxs-lookup"><span data-stu-id="45036-175">The default value is `$Null`, and the culture that is set in the operating system is used in the session.</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45036-176">-IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="45036-176">-IdleTimeout</span></span>

<span data-ttu-id="45036-177">Anger hur länge sessionen förblir öppen om fjärrdatorn inte får någon kommunikation från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="45036-177">Determines how long the session stays open if the remote computer does not receive any communication from the local computer.</span></span> <span data-ttu-id="45036-178">Detta inkluderar pulsslags signalen.</span><span class="sxs-lookup"><span data-stu-id="45036-178">This includes the heartbeat signal.</span></span> <span data-ttu-id="45036-179">När intervallet går ut stängs sessionen.</span><span class="sxs-lookup"><span data-stu-id="45036-179">When the interval expires, the session closes.</span></span>

<span data-ttu-id="45036-180">Värdet för tids gräns för inaktivitet är av stor betydelse om du vill koppla från och återansluta till en session.</span><span class="sxs-lookup"><span data-stu-id="45036-180">The idle time-out value is of significant importance if you intend to disconnect and reconnect to a session.</span></span> <span data-ttu-id="45036-181">Du kan bara återansluta om sessionen inte har uppnådde sin tids gräns.</span><span class="sxs-lookup"><span data-stu-id="45036-181">You can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="45036-182">Ange ett värde i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="45036-182">Enter a value in milliseconds.</span></span> <span data-ttu-id="45036-183">Det minsta värdet är 60000 (1 minut).</span><span class="sxs-lookup"><span data-stu-id="45036-183">The minimum value is 60000 (1 minute).</span></span> <span data-ttu-id="45036-184">Det maximala värdet är värdet för **MaxIdleTimeoutms** -egenskapen i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="45036-184">The maximum is the value of the **MaxIdleTimeoutms** property of the session configuration.</span></span> <span data-ttu-id="45036-185">Standardvärdet,-1, anger inte en tids gräns för inaktivitet.</span><span class="sxs-lookup"><span data-stu-id="45036-185">The default value, -1, does not set an idle time-out.</span></span>

<span data-ttu-id="45036-186">Sessionen använder tids gränsen för inaktivitet som anges i sessionens alternativ, om det finns några.</span><span class="sxs-lookup"><span data-stu-id="45036-186">The session uses the idle time-out that is set in the session options, if any.</span></span> <span data-ttu-id="45036-187">Om inget anges (-1) använder sessionen värdet för **IdleTimeoutMs** -egenskapen i sessionen eller värdet för WSMan-gränssnittets timeout ( `WSMan:\<ComputerName>\Shell\IdleTimeout` ), beroende på vilket som är kortast.</span><span class="sxs-lookup"><span data-stu-id="45036-187">If none is set (-1), the session uses the value of the **IdleTimeoutMs** property of the session configuration or the WSMan shell time-out value (`WSMan:\<ComputerName>\Shell\IdleTimeout`), whichever is shortest.</span></span>

<span data-ttu-id="45036-188">Om tids gränsen för inaktivitet som anges i session-alternativen överskrider värdet för **MaxIdleTimeoutMs** -egenskapen i konfigurationen för sessionen, Miss lyckas kommandot för att skapa en session.</span><span class="sxs-lookup"><span data-stu-id="45036-188">If the idle timeout set in the session options exceeds the value of the **MaxIdleTimeoutMs** property of the session configuration, the command to create a session fails.</span></span>

<span data-ttu-id="45036-189">**IdleTimeoutMs** -värdet för standard konfigurationen av **Microsoft. PowerShell** -sessionen är 7200000 millisekunder (2 timmar).</span><span class="sxs-lookup"><span data-stu-id="45036-189">The **IdleTimeoutMs** value of the default **Microsoft.PowerShell** session configuration is 7200000 milliseconds (2 hours).</span></span> <span data-ttu-id="45036-190">Dess **MaxIdleTimeoutMs** -värde är 2147483647 millisekunder ( \> 24 dagar).</span><span class="sxs-lookup"><span data-stu-id="45036-190">Its **MaxIdleTimeoutMs** value is 2147483647 milliseconds (\>24 days).</span></span> <span data-ttu-id="45036-191">Standardvärdet för WSMan-gränssnittets inaktiva timeout ( `WSMan:\<ComputerName>\Shell\IdleTimeout` ) är 7200000 millisekunder (2 timmar).</span><span class="sxs-lookup"><span data-stu-id="45036-191">The default value of the WSMan shell idle time-out (`WSMan:\<ComputerName>\Shell\IdleTimeout`) is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="45036-192">Timeout-värdet för inaktivitet i en session kan också ändras när du kopplar från en-session eller återansluter till en session.</span><span class="sxs-lookup"><span data-stu-id="45036-192">The idle time-out value of a session can also be changed when disconnecting from a session or reconnecting to a session.</span></span> <span data-ttu-id="45036-193">Mer information finns i `Disconnect-PSSession` och `Connect-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="45036-193">For more information, see `Disconnect-PSSession` and `Connect-PSSession`.</span></span>

<span data-ttu-id="45036-194">I Windows PowerShell 2,0 är standardvärdet för **idleTimeout** -parametern 240000 (4 minuter).</span><span class="sxs-lookup"><span data-stu-id="45036-194">In Windows PowerShell 2.0, the default value of the **IdleTimeout** parameter is 240000 (4 minutes).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: IdleTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45036-195">-IncludePortInSPN</span><span class="sxs-lookup"><span data-stu-id="45036-195">-IncludePortInSPN</span></span>

<span data-ttu-id="45036-196">Inkluderar port numret i tjänstens huvud namn (SPN) som används för Kerberos-autentisering, till exempel `HTTP://<ComputerName>:5985` .</span><span class="sxs-lookup"><span data-stu-id="45036-196">Includes the port number in the Service Principal Name (SPN) used for Kerberos authentication, for example, `HTTP://<ComputerName>:5985`.</span></span> <span data-ttu-id="45036-197">Det här alternativet tillåter en klient som använder ett SPN-namn som inte är standard för att autentisera mot en fjärrdator som använder Kerberos-autentisering.</span><span class="sxs-lookup"><span data-stu-id="45036-197">This option allows a client that uses a non-default SPN to authenticate against a remote computer that uses Kerberos authentication.</span></span>

<span data-ttu-id="45036-198">Alternativet är utformat för företag där flera tjänster som stöder Kerberos-autentisering körs under olika användar konton.</span><span class="sxs-lookup"><span data-stu-id="45036-198">The option is designed for enterprises where multiple services that support Kerberos authentication are running under different user accounts.</span></span> <span data-ttu-id="45036-199">Till exempel kan ett IIS-program som tillåter Kerberos-autentisering kräva att standard-SPN registreras på ett användar konto som skiljer sig från dator kontot.</span><span class="sxs-lookup"><span data-stu-id="45036-199">For example, an IIS application that allows for Kerberos authentication can require the default SPN to be registered to a user account that differs from the computer account.</span></span> <span data-ttu-id="45036-200">I sådana fall kan PowerShell-fjärrkommunikation inte använda Kerberos för att autentisera eftersom det kräver ett SPN som är registrerat på dator kontot.</span><span class="sxs-lookup"><span data-stu-id="45036-200">In such cases, PowerShell remoting cannot use Kerberos to authenticate because it requires an SPN that is registered to the computer account.</span></span> <span data-ttu-id="45036-201">För att lösa det här problemet kan administratörer skapa olika SPN-namn, till exempel genom att använda **Setspn.exe** som är registrerade för olika användar konton och kan skilja mellan dem genom att inkludera port numret i SPN.</span><span class="sxs-lookup"><span data-stu-id="45036-201">To resolve this problem, administrators can create different SPNs, such as by using **Setspn.exe** , that are registered to different user accounts and can distinguish between them by including the port number in the SPN.</span></span>

<span data-ttu-id="45036-202">Mer information finns i [Översikt över Setspn](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="45036-202">For more information, see [Setspn Overview](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).</span></span>

<span data-ttu-id="45036-203">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="45036-203">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="45036-204">-MaxConnectionRetryCount</span><span class="sxs-lookup"><span data-stu-id="45036-204">-MaxConnectionRetryCount</span></span>

<span data-ttu-id="45036-205">Anger hur många gånger PowerShell försöker upprätta en anslutning till en måldator om det aktuella försöket Miss lyckas på grund av nätverks problem.</span><span class="sxs-lookup"><span data-stu-id="45036-205">Specifies the number of times that PowerShell attempts to make a connection to a target machine if the current attempt fails due to network issues.</span></span> <span data-ttu-id="45036-206">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="45036-206">The default value is 5.</span></span>

<span data-ttu-id="45036-207">Den här parametern har lagts till för PowerShell version 5,0.</span><span class="sxs-lookup"><span data-stu-id="45036-207">This parameter was added for PowerShell version 5.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45036-208">-MaximumReceivedDataSizePerCommand</span><span class="sxs-lookup"><span data-stu-id="45036-208">-MaximumReceivedDataSizePerCommand</span></span>

<span data-ttu-id="45036-209">Anger det maximala antalet byte som den lokala datorn kan ta emot från fjärrdatorn i ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="45036-209">Specifies the maximum number of bytes that the local computer can receive from the remote computer in a single command.</span></span> <span data-ttu-id="45036-210">Ange ett värde i byte.</span><span class="sxs-lookup"><span data-stu-id="45036-210">Enter a value in bytes.</span></span> <span data-ttu-id="45036-211">Som standard finns det ingen data storleks gräns.</span><span class="sxs-lookup"><span data-stu-id="45036-211">By default, there is no data size limit.</span></span>

<span data-ttu-id="45036-212">Det här alternativet är utformat för att skydda resurserna på klient datorn.</span><span class="sxs-lookup"><span data-stu-id="45036-212">This option is designed to protect the resources on the client computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45036-213">-MaximumReceivedObjectSize</span><span class="sxs-lookup"><span data-stu-id="45036-213">-MaximumReceivedObjectSize</span></span>

<span data-ttu-id="45036-214">Anger den maximala storleken på ett objekt som den lokala datorn kan ta emot från fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="45036-214">Specifies the maximum size of an object that the local computer can receive from the remote computer.</span></span> <span data-ttu-id="45036-215">Det här alternativet är utformat för att skydda resurserna på klient datorn.</span><span class="sxs-lookup"><span data-stu-id="45036-215">This option is designed to protect the resources on the client computer.</span></span> <span data-ttu-id="45036-216">Ange ett värde i byte.</span><span class="sxs-lookup"><span data-stu-id="45036-216">Enter a value in bytes.</span></span>

<span data-ttu-id="45036-217">Om du utelämnar den här parametern i Windows PowerShell 2,0 finns det ingen storleks gräns för objekt.</span><span class="sxs-lookup"><span data-stu-id="45036-217">In Windows PowerShell 2.0, if you omit this parameter, there is no object size limit.</span></span> <span data-ttu-id="45036-218">Från och med Windows PowerShell 3,0 är standardvärdet 200 MB om du utelämnar den här parametern.</span><span class="sxs-lookup"><span data-stu-id="45036-218">Beginning in Windows PowerShell 3.0, if you omit this parameter, the default value is 200 MB.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 200 MB
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45036-219">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="45036-219">-MaximumRedirection</span></span>

<span data-ttu-id="45036-220">Anger hur många gånger PowerShell omdirigerar en anslutning till en alternativ Uniform Resource Identifier (URI) innan anslutningen Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="45036-220">Determines how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="45036-221">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="45036-221">The default value is 5.</span></span> <span data-ttu-id="45036-222">Värdet 0 (noll) förhindrar all omdirigering.</span><span class="sxs-lookup"><span data-stu-id="45036-222">A value of 0 (zero) prevents all redirection.</span></span>

<span data-ttu-id="45036-223">Det här alternativet används endast i sessionen när parametern **AllowRedirection** används i kommandot som skapar sessionen.</span><span class="sxs-lookup"><span data-stu-id="45036-223">This option is used in the session only when the **AllowRedirection** parameter is used in the command that creates the session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45036-224">-Nocompression</span><span class="sxs-lookup"><span data-stu-id="45036-224">-NoCompression</span></span>

<span data-ttu-id="45036-225">Inaktiverar paket komprimering i sessionen.</span><span class="sxs-lookup"><span data-stu-id="45036-225">Turns off packet compression in the session.</span></span> <span data-ttu-id="45036-226">Komprimering använder fler processor cykler, men det gör överföringen snabbare.</span><span class="sxs-lookup"><span data-stu-id="45036-226">Compression uses more processor cycles, but it makes transmission faster.</span></span>

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

### <span data-ttu-id="45036-227">– Encryption</span><span class="sxs-lookup"><span data-stu-id="45036-227">-NoEncryption</span></span>

<span data-ttu-id="45036-228">Inaktiverar data kryptering.</span><span class="sxs-lookup"><span data-stu-id="45036-228">Turns off data encryption.</span></span>

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

### <span data-ttu-id="45036-229">-NoMachineProfile</span><span class="sxs-lookup"><span data-stu-id="45036-229">-NoMachineProfile</span></span>

<span data-ttu-id="45036-230">Förhindrar inläsning av användarens Windows-användarprofil.</span><span class="sxs-lookup"><span data-stu-id="45036-230">Prevents loading the user's Windows user profile.</span></span> <span data-ttu-id="45036-231">Därför kan sessionen skapas snabbare, men användarspecifika register inställningar, objekt som miljövariabler och certifikat är inte tillgängliga i sessionen.</span><span class="sxs-lookup"><span data-stu-id="45036-231">As a result, the session might be created faster, but user-specific registry settings, items such as environment variables, and certificates are not available in the session.</span></span>

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

### <span data-ttu-id="45036-232">-Opentimey</span><span class="sxs-lookup"><span data-stu-id="45036-232">-OpenTimeout</span></span>

<span data-ttu-id="45036-233">Anger hur länge klient datorn väntar på att sessionen ska upprättas.</span><span class="sxs-lookup"><span data-stu-id="45036-233">Determines how long the client computer waits for the session connection to be established.</span></span> <span data-ttu-id="45036-234">När intervallet går ut Miss lyckas kommandot för att upprätta anslutningen.</span><span class="sxs-lookup"><span data-stu-id="45036-234">When the interval expires, the command to establish the connection fails.</span></span> <span data-ttu-id="45036-235">Ange ett värde i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="45036-235">Enter a value in milliseconds.</span></span>

<span data-ttu-id="45036-236">Standardvärdet är 180000 (3 minuter).</span><span class="sxs-lookup"><span data-stu-id="45036-236">The default value is 180000 (3 minutes).</span></span> <span data-ttu-id="45036-237">Värdet 0 (noll) innebär ingen tids gräns. kommandot fortsätter på obestämd tid.</span><span class="sxs-lookup"><span data-stu-id="45036-237">A value of 0 (zero) means no time-out; the command continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OpenTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45036-238">-OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="45036-238">-OperationTimeout</span></span>

<span data-ttu-id="45036-239">Fastställer den längsta tid som en åtgärd i sessionen kan köras.</span><span class="sxs-lookup"><span data-stu-id="45036-239">Determines the maximum time that any operation in the session can run.</span></span> <span data-ttu-id="45036-240">När intervallet går ut Miss lyckas åtgärden.</span><span class="sxs-lookup"><span data-stu-id="45036-240">When the interval expires, the operation fails.</span></span> <span data-ttu-id="45036-241">Ange ett värde i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="45036-241">Enter a value in milliseconds.</span></span>

<span data-ttu-id="45036-242">Standardvärdet är 180000 (3 minuter).</span><span class="sxs-lookup"><span data-stu-id="45036-242">The default value is 180000 (3 minutes).</span></span> <span data-ttu-id="45036-243">Värdet 0 (noll) innebär ingen tids gräns. åtgärden fortsätter på obestämd tid.</span><span class="sxs-lookup"><span data-stu-id="45036-243">A value of 0 (zero) means no time-out; the operation continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45036-244">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="45036-244">-OutputBufferingMode</span></span>

<span data-ttu-id="45036-245">Anger hur kommandoutdata hanteras i frånkopplade sessioner när utdatabufferten blir full.</span><span class="sxs-lookup"><span data-stu-id="45036-245">Determines how command output is managed in disconnected sessions when the output buffer becomes full.</span></span>

<span data-ttu-id="45036-246">Om buffring av utdata inte har ställts in i sessionen eller i konfigurationen av sessionen är standardvärdet **block**.</span><span class="sxs-lookup"><span data-stu-id="45036-246">If the output buffering mode is not set in the session or in the session configuration, the default value is **Block**.</span></span> <span data-ttu-id="45036-247">Användare kan också ändra läget för buffring av utdata när de kopplar från sessionen.</span><span class="sxs-lookup"><span data-stu-id="45036-247">Users can also change the output buffering mode when disconnecting the session.</span></span>

<span data-ttu-id="45036-248">Om du utelämnar den här parametern, är värdet för **OutputBufferingMode** för Session-objektet none.</span><span class="sxs-lookup"><span data-stu-id="45036-248">If you omit this parameter, the value of the **OutputBufferingMode** of the session option object is None.</span></span> <span data-ttu-id="45036-249">Värdet **block** eller **Drop** åsidosätter transport alternativet utdata buffer i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="45036-249">A value of **Block** or **Drop** overrides the output buffering mode transport option set in the session configuration.</span></span> <span data-ttu-id="45036-250">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="45036-250">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="45036-251">Undantaget.</span><span class="sxs-lookup"><span data-stu-id="45036-251">Block.</span></span> <span data-ttu-id="45036-252">När utdatabufferten är full pausas körningen tills bufferten är klar.</span><span class="sxs-lookup"><span data-stu-id="45036-252">When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="45036-253">Skugg.</span><span class="sxs-lookup"><span data-stu-id="45036-253">Drop.</span></span> <span data-ttu-id="45036-254">När utdatabufferten är full fortsätter körningen.</span><span class="sxs-lookup"><span data-stu-id="45036-254">When the output buffer is full, execution continues.</span></span> <span data-ttu-id="45036-255">När nya utdata sparas, ignoreras det äldsta resultatet.</span><span class="sxs-lookup"><span data-stu-id="45036-255">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="45036-256">Inga.</span><span class="sxs-lookup"><span data-stu-id="45036-256">None.</span></span> <span data-ttu-id="45036-257">Inget utdata buffer-läge har angetts.</span><span class="sxs-lookup"><span data-stu-id="45036-257">No output buffering mode is specified.</span></span>

<span data-ttu-id="45036-258">Mer information om transport alternativet för buffring av utdata finns i `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="45036-258">For more information about the output buffering mode transport option, see `New-PSTransportOption`.</span></span>

<span data-ttu-id="45036-259">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="45036-259">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45036-260">-ProxyAccessType</span><span class="sxs-lookup"><span data-stu-id="45036-260">-ProxyAccessType</span></span>

<span data-ttu-id="45036-261">Bestämmer vilken mekanism som används för att matcha värd namnet.</span><span class="sxs-lookup"><span data-stu-id="45036-261">Determines which mechanism is used to resolve the host name.</span></span> <span data-ttu-id="45036-262">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="45036-262">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="45036-263">IEConfig</span><span class="sxs-lookup"><span data-stu-id="45036-263">IEConfig</span></span>
- <span data-ttu-id="45036-264">WinHttpConfig</span><span class="sxs-lookup"><span data-stu-id="45036-264">WinHttpConfig</span></span>
- <span data-ttu-id="45036-265">Identifiera automatiskt</span><span class="sxs-lookup"><span data-stu-id="45036-265">AutoDetect</span></span>
- <span data-ttu-id="45036-266">NoProxyServer</span><span class="sxs-lookup"><span data-stu-id="45036-266">NoProxyServer</span></span>
- <span data-ttu-id="45036-267">Inget</span><span class="sxs-lookup"><span data-stu-id="45036-267">None</span></span>

<span data-ttu-id="45036-268">Standardvärdet är none.</span><span class="sxs-lookup"><span data-stu-id="45036-268">The default value is None.</span></span>

<span data-ttu-id="45036-269">Information om värdena för den här parametern finns i [ProxyAccessType-uppräkning](/dotnet/api/system.management.automation.remoting.proxyaccesstype?redirectedfrom=MSDN&view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="45036-269">For information about the values of this parameter, see [ProxyAccessType Enumeration](/dotnet/api/system.management.automation.remoting.proxyaccesstype?redirectedfrom=MSDN&view=powershellsdk-1.1.0).</span></span>

```yaml
Type: System.Management.Automation.Remoting.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: None, IEConfig, WinHttpConfig, AutoDetect, NoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45036-270">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="45036-270">-ProxyAuthentication</span></span>

<span data-ttu-id="45036-271">Anger den autentiseringsmetod som används för proxy-matchning.</span><span class="sxs-lookup"><span data-stu-id="45036-271">Specifies the authentication method that is used for proxy resolution.</span></span> <span data-ttu-id="45036-272">De acceptabla värdena för den här parametern är: **Basic** , **Digest** och **Negotiate**.</span><span class="sxs-lookup"><span data-stu-id="45036-272">The acceptable values for this parameter are: **Basic** , **Digest** , and **Negotiate**.</span></span> <span data-ttu-id="45036-273">Standardvärdet är **Negotiate**.</span><span class="sxs-lookup"><span data-stu-id="45036-273">The default value is **Negotiate**.</span></span>

<span data-ttu-id="45036-274">Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?redirectedfrom=MSDN&view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="45036-274">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?redirectedfrom=MSDN&view=powershellsdk-1.1.0).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Negotiate
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45036-275">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="45036-275">-ProxyCredential</span></span>

<span data-ttu-id="45036-276">Anger de autentiseringsuppgifter som ska användas för proxyautentisering.</span><span class="sxs-lookup"><span data-stu-id="45036-276">Specifies the credentials to use for proxy authentication.</span></span> <span data-ttu-id="45036-277">Ange en variabel som innehåller ett **PSCredential** -objekt eller ett kommando som hämtar ett **PSCredential** -objekt, t `Get-Credential` . ex. ett kommando.</span><span class="sxs-lookup"><span data-stu-id="45036-277">Enter a variable that contains a **PSCredential** object or a command that gets a **PSCredential** object, such as a `Get-Credential` command.</span></span> <span data-ttu-id="45036-278">Om det här alternativet inte anges anges inga autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="45036-278">If this option is not set, no credentials are specified.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45036-279">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="45036-279">-SkipCACheck</span></span>

<span data-ttu-id="45036-280">Anger att när den ansluter via HTTPS, verifierar inte klienten att Server certifikatet är signerat av en betrodd certifikat utfärdare (CA).</span><span class="sxs-lookup"><span data-stu-id="45036-280">Specifies that when it connects over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>

<span data-ttu-id="45036-281">Använd bara det här alternativet när fjärrdatorn är betrodd genom att använda en annan mekanism, till exempel när fjärrdatorn är en del av ett nätverk som är fysiskt säkert och isolerat eller när fjärrdatorn visas som en betrodd värd i en WinRM-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="45036-281">Use this option only when the remote computer is trusted by using another mechanism, such as when the remote computer is part of a network that is physically secure and isolated or when the remote computer is listed as a trusted host in a WinRM configuration.</span></span>

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

### <span data-ttu-id="45036-282">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="45036-282">-SkipCNCheck</span></span>

<span data-ttu-id="45036-283">Anger att serverns certifikats allmänna namn inte behöver matcha serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="45036-283">Specifies that the certificate common name (CN) of the server does not have to match the host name of the server.</span></span> <span data-ttu-id="45036-284">Det här alternativet används endast i fjärråtgärder som använder HTTPS-protokollet.</span><span class="sxs-lookup"><span data-stu-id="45036-284">This option is used only in remote operations that use the HTTPS protocol.</span></span>

<span data-ttu-id="45036-285">Använd endast det här alternativet för betrodda datorer.</span><span class="sxs-lookup"><span data-stu-id="45036-285">Use this option only for trusted computers.</span></span>

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

### <span data-ttu-id="45036-286">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="45036-286">-SkipRevocationCheck</span></span>

<span data-ttu-id="45036-287">Verifierar inte Server certifikatets återkallnings status.</span><span class="sxs-lookup"><span data-stu-id="45036-287">Does not validate the revocation status of the server certificate.</span></span>

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

### <span data-ttu-id="45036-288">– Värdet</span><span class="sxs-lookup"><span data-stu-id="45036-288">-UICulture</span></span>

<span data-ttu-id="45036-289">Anger användar gränssnitts kulturen som ska användas för sessionen.</span><span class="sxs-lookup"><span data-stu-id="45036-289">Specifies the UI culture to use for the session.</span></span>

<span data-ttu-id="45036-290">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="45036-290">Valid values include:</span></span>

- <span data-ttu-id="45036-291">Ett kultur namn i `<languagecode2>-<country/regioncode2>` format, t. ex. `ja-JP`</span><span class="sxs-lookup"><span data-stu-id="45036-291">A culture name in `<languagecode2>-<country/regioncode2>` format, such as `ja-JP`</span></span>
- <span data-ttu-id="45036-292">En variabel som innehåller ett **CultureInfo** -objekt</span><span class="sxs-lookup"><span data-stu-id="45036-292">A variable that contains a **CultureInfo** object</span></span>
- <span data-ttu-id="45036-293">Ett kommando som hämtar ett **CultureInfo** -objekt, till exempel `Get-Culture`</span><span class="sxs-lookup"><span data-stu-id="45036-293">A command that gets a **CultureInfo** object, such as `Get-Culture`</span></span>

<span data-ttu-id="45036-294">Standardvärdet är `$null` och den användar gränssnitts kultur som anges i operativ systemet när sessionen skapas används i sessionen.</span><span class="sxs-lookup"><span data-stu-id="45036-294">The default value is `$null`, and the UI culture that is set in the operating system when the session is created is used in the session.</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45036-295">-UseUTF16</span><span class="sxs-lookup"><span data-stu-id="45036-295">-UseUTF16</span></span>

<span data-ttu-id="45036-296">Anger att denna cmdlet kodar begäran i UTF16-format istället för UTF8-format.</span><span class="sxs-lookup"><span data-stu-id="45036-296">Indicates that this cmdlet encodes the request in UTF16 format instead of UTF8 format.</span></span>

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

### <span data-ttu-id="45036-297">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="45036-297">CommonParameters</span></span>

<span data-ttu-id="45036-298">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="45036-298">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="45036-299">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="45036-299">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="45036-300">INDATA</span><span class="sxs-lookup"><span data-stu-id="45036-300">INPUTS</span></span>

### <span data-ttu-id="45036-301">Inget</span><span class="sxs-lookup"><span data-stu-id="45036-301">None</span></span>

<span data-ttu-id="45036-302">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="45036-302">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="45036-303">UTDATA</span><span class="sxs-lookup"><span data-stu-id="45036-303">OUTPUTS</span></span>

### <span data-ttu-id="45036-304">System. Management. Automation. Remoting. PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="45036-304">System.Management.Automation.Remoting.PSSessionOption</span></span>

## <span data-ttu-id="45036-305">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="45036-305">NOTES</span></span>

<span data-ttu-id="45036-306">Om parametern **SessionOption** inte används i ett kommando för att skapa en **PSSession** , bestäms sessions alternativen av egenskapsvärdena för `$PSSessionOption` Preference-variabeln, om den har angetts.</span><span class="sxs-lookup"><span data-stu-id="45036-306">If the **SessionOption** parameter is not used in a command to create a **PSSession** , the session options are determined by the property values of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="45036-307">Mer information om `$PSSessionOption` variabeln finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="45036-307">For more information about the `$PSSessionOption` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="45036-308">Egenskaperna för ett konfigurations objekt för en session varierar beroende på vilka alternativ som har angetts för konfigurationen av sessionen och värdena för dessa alternativ.</span><span class="sxs-lookup"><span data-stu-id="45036-308">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="45036-309">Dessutom har sessionsinställningar som använder en konfigurations fil för sessionen ytterligare egenskaper.</span><span class="sxs-lookup"><span data-stu-id="45036-309">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="45036-310">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="45036-310">RELATED LINKS</span></span>

[<span data-ttu-id="45036-311">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="45036-311">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="45036-312">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="45036-312">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="45036-313">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="45036-313">New-PSSession</span></span>](New-PSSession.md)

