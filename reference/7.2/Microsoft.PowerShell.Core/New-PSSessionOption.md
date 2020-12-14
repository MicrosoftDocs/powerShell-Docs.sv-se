---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionOption
ms.openlocfilehash: d07942797bad3666a263e017fa8372e672936041
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710207"
---
# <span data-ttu-id="43f4d-102">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="43f4d-102">New-PSSessionOption</span></span>

## <span data-ttu-id="43f4d-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="43f4d-103">SYNOPSIS</span></span>
<span data-ttu-id="43f4d-104">Skapar ett objekt som innehåller avancerade alternativ för en PSSession.</span><span class="sxs-lookup"><span data-stu-id="43f4d-104">Creates an object that contains advanced options for a PSSession.</span></span>

## <span data-ttu-id="43f4d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="43f4d-105">SYNTAX</span></span>

```
New-PSSessionOption [-MaximumRedirection <Int32>] [-NoCompression] [-NoMachineProfile] [-Culture <CultureInfo>]
 [-UICulture <CultureInfo>] [-MaximumReceivedDataSizePerCommand <Int32>] [-MaximumReceivedObjectSize <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-MaxConnectionRetryCount <Int32>]
 [-ApplicationArguments <PSPrimitiveDictionary>] [-OpenTimeout <Int32>] [-CancelTimeout <Int32>]
 [-IdleTimeout <Int32>] [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <AuthenticationMechanism>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [-IncludePortInSPN] [<CommonParameters>]
```

## <span data-ttu-id="43f4d-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="43f4d-106">DESCRIPTION</span></span>

<span data-ttu-id="43f4d-107">`New-PSSessionOption`Cmdleten skapar ett objekt som innehåller avancerade alternativ för en **PSSession**(User-Managed session).</span><span class="sxs-lookup"><span data-stu-id="43f4d-107">The `New-PSSessionOption` cmdlet creates an object that contains advanced options for a user-managed session (**PSSession**).</span></span> <span data-ttu-id="43f4d-108">Du kan använda objektet som värdet för parametern **SessionOption** för cmdletar som skapar en **PSSession**, till exempel, `New-PSSession` `Enter-PSSession` och `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="43f4d-108">You can use the object as the value of the **SessionOption** parameter of cmdlets that create a **PSSession**, such as `New-PSSession`, `Enter-PSSession`, and `Invoke-Command`.</span></span>

<span data-ttu-id="43f4d-109">Utan parametrar `New-PSSessionOption` genererar ett objekt som innehåller standardvärdena för alla alternativ.</span><span class="sxs-lookup"><span data-stu-id="43f4d-109">Without parameters, `New-PSSessionOption` generates an object that contains the default values for all of the options.</span></span> <span data-ttu-id="43f4d-110">Eftersom alla egenskaper kan redige ras kan du använda det resulterande objektet som mall och skapa standard alternativ objekt för ditt företag.</span><span class="sxs-lookup"><span data-stu-id="43f4d-110">Because all of the properties can be edited, you can use the resulting object as a template, and create standard option objects for your enterprise.</span></span>

<span data-ttu-id="43f4d-111">Du kan också spara ett alternativ för session i `$PSSessionOption` Preference-variabeln.</span><span class="sxs-lookup"><span data-stu-id="43f4d-111">You can also save a session option object in the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="43f4d-112">Värdena för den här variabeln upprättar nya standardvärden för session-alternativen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-112">The values of this variable establish new default values for the session options.</span></span> <span data-ttu-id="43f4d-113">De träder i kraft när inga sessionsinställningar har ställts in för sessionen och de har företräde framför alternativ som angetts i konfigurationen av sessionen, men du kan åsidosätta dem genom att ange sessionsinställningar eller ett alternativ objekt för session i en cmdlet som skapar en session.</span><span class="sxs-lookup"><span data-stu-id="43f4d-113">They effective when no session options are set for the session and they take precedence over options set in the session configuration, but you can override them by specifying session options or a session option object in a cmdlet that creates a session.</span></span> <span data-ttu-id="43f4d-114">Mer information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="43f4d-114">For more information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="43f4d-115">När du använder ett alternativ objekt för session i en cmdlet som skapar en session, prioriteras värdena för sessions-alternativ framför standardvärden för sessioner som angetts i variabeln $PSSessionOption och i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-115">When you use a session option object in a cmdlet that creates a session, the session option values take precedence over default values for sessions set in the $PSSessionOption preference variable and in the session configuration.</span></span> <span data-ttu-id="43f4d-116">De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-116">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span> <span data-ttu-id="43f4d-117">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="43f4d-117">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="43f4d-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="43f4d-118">EXAMPLES</span></span>

### <span data-ttu-id="43f4d-119">Exempel 1: skapa ett standard alternativ för session</span><span class="sxs-lookup"><span data-stu-id="43f4d-119">Example 1: Create a default session option</span></span>

<span data-ttu-id="43f4d-120">Det här kommandot skapar ett alternativ för session som innehåller alla standardvärden.</span><span class="sxs-lookup"><span data-stu-id="43f4d-120">This command creates a session option object that has all of the default values.</span></span>

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

### <span data-ttu-id="43f4d-121">Exempel 2: Konfigurera en session med hjälp av ett session alternativ-objekt</span><span class="sxs-lookup"><span data-stu-id="43f4d-121">Example 2: Configure a session by using a session option object</span></span>

<span data-ttu-id="43f4d-122">I det här exemplet visas hur du konfigurerar en session med hjälp av ett alternativ objekt för session.</span><span class="sxs-lookup"><span data-stu-id="43f4d-122">This example shows how to use a session option object to configure a session.</span></span>

```powershell
$pso = New-PSSessionOption -Culture "fr-fr" -MaximumReceivedObjectSize 10MB
New-PSSession -ComputerName Server01 -SessionOption $pso
```

<span data-ttu-id="43f4d-123">Det första kommandot skapar ett nytt alternativ för session och sparar det i `$pso` variabelns värde.</span><span class="sxs-lookup"><span data-stu-id="43f4d-123">The first command creates a new session option object and saves it in the value of the `$pso` variable.</span></span> <span data-ttu-id="43f4d-124">Det andra kommandot använder `New-PSSession` cmdleten för att skapa en session på Server01-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="43f4d-124">The second command uses the `New-PSSession` cmdlet to create a session on the Server01 remote computer.</span></span> <span data-ttu-id="43f4d-125">Kommandot använder Session-objektet i värdet för `$pso` variabeln som värdet för parametern **SessionOption** för kommandot.</span><span class="sxs-lookup"><span data-stu-id="43f4d-125">The command uses the session option object in the value of the `$pso` variable as the value of the **SessionOption** parameter of the command.</span></span>

### <span data-ttu-id="43f4d-126">Exempel 3: starta en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="43f4d-126">Example 3: Start an interactive session</span></span>

<span data-ttu-id="43f4d-127">Det här kommandot använder `Enter-PSSession` cmdleten för att starta en interaktiv session med Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="43f4d-127">This command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

```powershell
Enter-PSSession -ComputerName Server01 -SessionOption (New-PSSessionOption -NoEncryption -NoCompression)
```

<span data-ttu-id="43f4d-128">Värdet för parametern **SessionOption** är ett `New-PSSessionOption` kommando som har parametrarna Encryption och **nocompression** . </span><span class="sxs-lookup"><span data-stu-id="43f4d-128">The value of the **SessionOption** parameter is a `New-PSSessionOption` command that has the **NoEncryption** and **NoCompression** parameters.</span></span>

<span data-ttu-id="43f4d-129">`New-PSSessionOption`Kommandot omges av parenteser för att kontrol lera att det körs före `Enter-PSSession` kommandot.</span><span class="sxs-lookup"><span data-stu-id="43f4d-129">The `New-PSSessionOption` command is enclosed in parentheses to make sure that it runs before the `Enter-PSSession` command.</span></span>

### <span data-ttu-id="43f4d-130">Exempel 4: ändra ett alternativ objekt för session</span><span class="sxs-lookup"><span data-stu-id="43f4d-130">Example 4: Modify a session option object</span></span>

<span data-ttu-id="43f4d-131">Det här exemplet visar att du kan ändra objektet Session-alternativ.</span><span class="sxs-lookup"><span data-stu-id="43f4d-131">This example demonstrates that you can modify the session option object.</span></span> <span data-ttu-id="43f4d-132">Alla egenskaper har läs-/skriv värden.</span><span class="sxs-lookup"><span data-stu-id="43f4d-132">All properties have read/write values.</span></span>

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

<span data-ttu-id="43f4d-133">Använd den här metoden för att skapa ett standard-sessionsobjekt för ditt företag och skapa sedan anpassade versioner av det för specifika användnings områden.</span><span class="sxs-lookup"><span data-stu-id="43f4d-133">Use this method to create a standard session object for your enterprise, and then create customized versions of it for particular uses.</span></span>

### <span data-ttu-id="43f4d-134">Exempel 5: skapa en inställnings variabel</span><span class="sxs-lookup"><span data-stu-id="43f4d-134">Example 5: Create a preference variable</span></span>

<span data-ttu-id="43f4d-135">Det här kommandot skapar en `$PSSessionOption` inställnings variabel.</span><span class="sxs-lookup"><span data-stu-id="43f4d-135">This command creates a `$PSSessionOption` preference variable.</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -OpenTimeOut 120000
```

<span data-ttu-id="43f4d-136">När `$PSSessionOption` Preference-variabeln inträffar i sessionen, fastställer den standardvärden för alternativ i de sessioner som skapas med hjälp av `New-PSSession` `Enter-PSSession` cmdletarna,, och `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="43f4d-136">When the `$PSSessionOption` preference variable occurs in the session, it establishes default values for options in the sessions that are created by using the `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="43f4d-137">Om du vill göra `$PSSessionOption` variabeln tillgänglig i alla sessioner lägger du till den i din PowerShell-session och i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="43f4d-137">To make the `$PSSessionOption` variable available in all sessions, add it to your PowerShell session and to your PowerShell profile.</span></span>

<span data-ttu-id="43f4d-138">Mer information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="43f4d-138">For more information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>
<span data-ttu-id="43f4d-139">Mer information om profiler finns [about_Profiles](About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="43f4d-139">For more information about profiles, see [about_Profiles](About/about_Profiles.md).</span></span>

### <span data-ttu-id="43f4d-140">Exempel 6: uppfylla kraven för en fjärrsessions-konfiguration</span><span class="sxs-lookup"><span data-stu-id="43f4d-140">Example 6: Fulfill the requirements for a remote session configuration</span></span>

<span data-ttu-id="43f4d-141">Det här exemplet visar hur du använder ett **SessionOption** -objekt för att uppfylla kraven för en fjärrsessions-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="43f4d-141">This example shows how to use a **SessionOption** object to fulfill the requirements for a remote session configuration.</span></span>

```powershell
$skipCN = New-PSSessionOption -SkipCNCheck
New-PSSession -ComputerName 171.09.21.207 -UseSSL -Credential Domain01\User01 -SessionOption $SkipCN
```

<span data-ttu-id="43f4d-142">Det första kommandot använder `New-PSSessionOption` cmdleten för att skapa ett session-objekt som har egenskapen **SkipCNCheck** .</span><span class="sxs-lookup"><span data-stu-id="43f4d-142">The first command uses the `New-PSSessionOption` cmdlet to create a session option object that has the **SkipCNCheck** property.</span></span> <span data-ttu-id="43f4d-143">Kommandot sparar det resulterande sessions-objektet i `$skipCN` variabeln.</span><span class="sxs-lookup"><span data-stu-id="43f4d-143">The command saves the resulting session object in the `$skipCN` variable.</span></span>

<span data-ttu-id="43f4d-144">Det andra kommandot använder `New-PSSession` cmdleten för att skapa en ny session på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="43f4d-144">The second command uses the `New-PSSession` cmdlet to create a new session on a remote computer.</span></span> <span data-ttu-id="43f4d-145">`$skipCN`Check variabeln används i värdet för parametern **SessionOption** .</span><span class="sxs-lookup"><span data-stu-id="43f4d-145">The `$skipCN` check variable is used in the value of the **SessionOption** parameter.</span></span>

<span data-ttu-id="43f4d-146">Eftersom datorn identifieras med IP-adressen matchar inte värdet för parametern **computername** något av de gemensamma namnen i certifikatet som används för Secure SOCKETS Layer (SSL).</span><span class="sxs-lookup"><span data-stu-id="43f4d-146">Because the computer is identified by its IP address, the value of the **ComputerName** parameter does not match any of the common names in the certificate that is used for Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="43f4d-147">Därför krävs alternativet **SkipCNCheck** .</span><span class="sxs-lookup"><span data-stu-id="43f4d-147">As a result, the **SkipCNCheck** option is required.</span></span>

### <span data-ttu-id="43f4d-148">Exempel 7: gör argument tillgängliga för en fjärrsession</span><span class="sxs-lookup"><span data-stu-id="43f4d-148">Example 7: Make arguments available to a remote session</span></span>

<span data-ttu-id="43f4d-149">Det här exemplet visar hur du använder **ApplicationArguments** -parametern för `New-PSSessionOption` cmdleten för att göra ytterligare data tillgängliga för fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-149">This example shows how to use the **ApplicationArguments** parameter of the `New-PSSessionOption` cmdlet to make additional data available to the remote session.</span></span>

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

<span data-ttu-id="43f4d-150">Det första kommandot skapar en hash-tabell med två nycklar, **team** och **användning**.</span><span class="sxs-lookup"><span data-stu-id="43f4d-150">The first command creates a hash table with two keys, **Team** and **Use**.</span></span> <span data-ttu-id="43f4d-151">Kommandot sparar hash-tabellen i `$team` variabeln.</span><span class="sxs-lookup"><span data-stu-id="43f4d-151">The command saves the hash table in the `$team` variable.</span></span> <span data-ttu-id="43f4d-152">Mer information om hash-tabeller finns i [about_Hash_Tables](about/about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="43f4d-152">For more information about hash tables, see [about_Hash_Tables](about/about_Hash_Tables.md).</span></span>

<span data-ttu-id="43f4d-153">Därefter `New-PSSessionOption` skapar cmdleten med hjälp av parametern **ApplicationArguments** ett alternativ för session som sparats i `$team` variabeln.</span><span class="sxs-lookup"><span data-stu-id="43f4d-153">Next, the `New-PSSessionOption` cmdlet, using the **ApplicationArguments** parameter, creates a session option object saved in the `$team` variable.</span></span> <span data-ttu-id="43f4d-154">När `New-PSSessionOption` skapar objektet Session, konverterar det automatiskt hash-tabellen i värdet för parametern **ApplicationArguments** till en primitiv ord lista så att data kan överföras till fjärrsessionen på ett tillförlitligt sätt.</span><span class="sxs-lookup"><span data-stu-id="43f4d-154">When `New-PSSessionOption` creates the session option object, it automatically converts the hash table in the value of the **ApplicationArguments** parameter to a primitive dictionary so the data can be reliably transmitted to the remote session.</span></span>

<span data-ttu-id="43f4d-155">`New-PSSession`Cmdleten startar en session på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="43f4d-155">The `New-PSSession` cmdlet starts a session on the Server01 computer.</span></span> <span data-ttu-id="43f4d-156">Parametern **SessionOption** används för att inkludera alternativen i `$teamOption` variabeln.</span><span class="sxs-lookup"><span data-stu-id="43f4d-156">It uses the **SessionOption** parameter to include the options in the `$teamOption` variable.</span></span>

<span data-ttu-id="43f4d-157">`Invoke-Command`Cmdleten visar att data i `$team` variabeln är tillgängliga för kommandon i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-157">The `Invoke-Command` cmdlet demonstrates that the data in the `$team` variable is available to commands in the remote session.</span></span> <span data-ttu-id="43f4d-158">Data visas i egenskapen **ApplicationArguments** för den `$PSSenderInfo` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="43f4d-158">The data appears in the **ApplicationArguments** property of the `$PSSenderInfo` automatic variable.</span></span>

<span data-ttu-id="43f4d-159">Den slutgiltiga `Invoke-Command` visar hur data kan användas.</span><span class="sxs-lookup"><span data-stu-id="43f4d-159">The final `Invoke-Command` shows how the data might be used.</span></span>

## <span data-ttu-id="43f4d-160">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="43f4d-160">PARAMETERS</span></span>

### <span data-ttu-id="43f4d-161">-ApplicationArguments</span><span class="sxs-lookup"><span data-stu-id="43f4d-161">-ApplicationArguments</span></span>

<span data-ttu-id="43f4d-162">Anger en primitiv ord lista som skickas till fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-162">Specifies a primitive dictionary that is sent to the remote session.</span></span> <span data-ttu-id="43f4d-163">Kommandon och skript i fjärrsessionen, inklusive start skript i konfigurationen av sessionen, kan hitta den här ord listan i egenskapen **ApplicationArguments** för den `$PSSenderInfo` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="43f4d-163">Commands and scripts in the remote session, including startup scripts in the session configuration, can find this dictionary in the **ApplicationArguments** property of the `$PSSenderInfo` automatic variable.</span></span> <span data-ttu-id="43f4d-164">Du kan använda den här parametern för att skicka data till fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-164">You can use this parameter to send data to the remote session.</span></span>

<span data-ttu-id="43f4d-165">Mer information finns i [about_Hash_Tables](about/about_Hash_Tables.md), [about_Session_Configurations](About/about_Session_Configurations.md)och [about_Automatic_Variables](about/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="43f4d-165">For more information, see [about_Hash_Tables](about/about_Hash_Tables.md), [about_Session_Configurations](About/about_Session_Configurations.md), and [about_Automatic_Variables](about/about_Automatic_Variables.md).</span></span>

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

### <span data-ttu-id="43f4d-166">-CancelTimeout</span><span class="sxs-lookup"><span data-stu-id="43f4d-166">-CancelTimeout</span></span>

<span data-ttu-id="43f4d-167">Anger hur lång tid PowerShell väntar på att en avbrotts åtgärd (CTRL + C) ska slutföras innan den slutar.</span><span class="sxs-lookup"><span data-stu-id="43f4d-167">Determines how long PowerShell waits for a cancel operation (CTRL+C) to finish before ending it.</span></span>
<span data-ttu-id="43f4d-168">Ange ett värde i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="43f4d-168">Enter a value in milliseconds.</span></span>

<span data-ttu-id="43f4d-169">Standardvärdet är 60000 (en minut).</span><span class="sxs-lookup"><span data-stu-id="43f4d-169">The default value is 60000 (one minute).</span></span> <span data-ttu-id="43f4d-170">Värdet 0 (noll) innebär ingen tids gräns. kommandot fortsätter på obestämd tid.</span><span class="sxs-lookup"><span data-stu-id="43f4d-170">A value of 0 (zero) means no time-out; the command continues indefinitely.</span></span>

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

### <span data-ttu-id="43f4d-171">– Kultur</span><span class="sxs-lookup"><span data-stu-id="43f4d-171">-Culture</span></span>

<span data-ttu-id="43f4d-172">Anger kulturen som ska användas för sessionen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-172">Specifies the culture to use for the session.</span></span> <span data-ttu-id="43f4d-173">Ange ett kultur namn i `<languagecode2>-<country/regioncode2>` formatet (t `ja-JP` . ex.), en variabel som innehåller ett **CultureInfo** -objekt eller ett kommando som hämtar ett **CultureInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="43f4d-173">Enter a culture name in `<languagecode2>-<country/regioncode2>` format (like `ja-JP`), a variable that contains a **CultureInfo** object, or a command that gets a **CultureInfo** object.</span></span>

<span data-ttu-id="43f4d-174">Standardvärdet är `$Null` och kulturen som anges i operativ systemet används i sessionen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-174">The default value is `$Null`, and the culture that is set in the operating system is used in the session.</span></span>

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

### <span data-ttu-id="43f4d-175">-IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="43f4d-175">-IdleTimeout</span></span>

<span data-ttu-id="43f4d-176">Anger hur länge sessionen förblir öppen om fjärrdatorn inte får någon kommunikation från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="43f4d-176">Determines how long the session stays open if the remote computer does not receive any communication from the local computer.</span></span> <span data-ttu-id="43f4d-177">Detta inkluderar pulsslags signalen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-177">This includes the heartbeat signal.</span></span> <span data-ttu-id="43f4d-178">När intervallet går ut stängs sessionen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-178">When the interval expires, the session closes.</span></span>

<span data-ttu-id="43f4d-179">Värdet för tids gräns för inaktivitet är av stor betydelse om du vill koppla från och återansluta till en session.</span><span class="sxs-lookup"><span data-stu-id="43f4d-179">The idle time-out value is of significant importance if you intend to disconnect and reconnect to a session.</span></span> <span data-ttu-id="43f4d-180">Du kan bara återansluta om sessionen inte har uppnådde sin tids gräns.</span><span class="sxs-lookup"><span data-stu-id="43f4d-180">You can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="43f4d-181">Ange ett värde i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="43f4d-181">Enter a value in milliseconds.</span></span> <span data-ttu-id="43f4d-182">Det minsta värdet är 60000 (1 minut).</span><span class="sxs-lookup"><span data-stu-id="43f4d-182">The minimum value is 60000 (1 minute).</span></span> <span data-ttu-id="43f4d-183">Det maximala värdet är värdet för **MaxIdleTimeoutms** -egenskapen i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-183">The maximum is the value of the **MaxIdleTimeoutms** property of the session configuration.</span></span> <span data-ttu-id="43f4d-184">Standardvärdet,-1, anger inte en tids gräns för inaktivitet.</span><span class="sxs-lookup"><span data-stu-id="43f4d-184">The default value, -1, does not set an idle time-out.</span></span>

<span data-ttu-id="43f4d-185">Sessionen använder tids gränsen för inaktivitet som anges i sessionens alternativ, om det finns några.</span><span class="sxs-lookup"><span data-stu-id="43f4d-185">The session uses the idle time-out that is set in the session options, if any.</span></span> <span data-ttu-id="43f4d-186">Om inget anges (-1) använder sessionen värdet för **IdleTimeoutMs** -egenskapen i sessionen eller värdet för WSMan-gränssnittets timeout ( `WSMan:\<ComputerName>\Shell\IdleTimeout` ), beroende på vilket som är kortast.</span><span class="sxs-lookup"><span data-stu-id="43f4d-186">If none is set (-1), the session uses the value of the **IdleTimeoutMs** property of the session configuration or the WSMan shell time-out value (`WSMan:\<ComputerName>\Shell\IdleTimeout`), whichever is shortest.</span></span>

<span data-ttu-id="43f4d-187">Om tids gränsen för inaktivitet som anges i session-alternativen överskrider värdet för **MaxIdleTimeoutMs** -egenskapen i konfigurationen för sessionen, Miss lyckas kommandot för att skapa en session.</span><span class="sxs-lookup"><span data-stu-id="43f4d-187">If the idle timeout set in the session options exceeds the value of the **MaxIdleTimeoutMs** property of the session configuration, the command to create a session fails.</span></span>

<span data-ttu-id="43f4d-188">**IdleTimeoutMs** -värdet för standard konfigurationen av **Microsoft. PowerShell** -sessionen är 7200000 millisekunder (2 timmar).</span><span class="sxs-lookup"><span data-stu-id="43f4d-188">The **IdleTimeoutMs** value of the default **Microsoft.PowerShell** session configuration is 7200000 milliseconds (2 hours).</span></span> <span data-ttu-id="43f4d-189">Dess **MaxIdleTimeoutMs** -värde är 2147483647 millisekunder ( \> 24 dagar).</span><span class="sxs-lookup"><span data-stu-id="43f4d-189">Its **MaxIdleTimeoutMs** value is 2147483647 milliseconds (\>24 days).</span></span> <span data-ttu-id="43f4d-190">Standardvärdet för WSMan-gränssnittets inaktiva timeout ( `WSMan:\<ComputerName>\Shell\IdleTimeout` ) är 7200000 millisekunder (2 timmar).</span><span class="sxs-lookup"><span data-stu-id="43f4d-190">The default value of the WSMan shell idle time-out (`WSMan:\<ComputerName>\Shell\IdleTimeout`) is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="43f4d-191">Timeout-värdet för inaktivitet i en session kan också ändras när du kopplar från en-session eller återansluter till en session.</span><span class="sxs-lookup"><span data-stu-id="43f4d-191">The idle time-out value of a session can also be changed when disconnecting from a session or reconnecting to a session.</span></span> <span data-ttu-id="43f4d-192">Mer information finns i `Disconnect-PSSession` och `Connect-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="43f4d-192">For more information, see `Disconnect-PSSession` and `Connect-PSSession`.</span></span>

<span data-ttu-id="43f4d-193">I Windows PowerShell 2,0 är standardvärdet för **idleTimeout** -parametern 240000 (4 minuter).</span><span class="sxs-lookup"><span data-stu-id="43f4d-193">In Windows PowerShell 2.0, the default value of the **IdleTimeout** parameter is 240000 (4 minutes).</span></span>

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

### <span data-ttu-id="43f4d-194">-IncludePortInSPN</span><span class="sxs-lookup"><span data-stu-id="43f4d-194">-IncludePortInSPN</span></span>

<span data-ttu-id="43f4d-195">Inkluderar port numret i tjänstens huvud namn (SPN) som används för Kerberos-autentisering, till exempel `HTTP://<ComputerName>:5985` .</span><span class="sxs-lookup"><span data-stu-id="43f4d-195">Includes the port number in the Service Principal Name (SPN) used for Kerberos authentication, for example, `HTTP://<ComputerName>:5985`.</span></span> <span data-ttu-id="43f4d-196">Det här alternativet tillåter en klient som använder ett SPN-namn som inte är standard för att autentisera mot en fjärrdator som använder Kerberos-autentisering.</span><span class="sxs-lookup"><span data-stu-id="43f4d-196">This option allows a client that uses a non-default SPN to authenticate against a remote computer that uses Kerberos authentication.</span></span>

<span data-ttu-id="43f4d-197">Alternativet är utformat för företag där flera tjänster som stöder Kerberos-autentisering körs under olika användar konton.</span><span class="sxs-lookup"><span data-stu-id="43f4d-197">The option is designed for enterprises where multiple services that support Kerberos authentication are running under different user accounts.</span></span> <span data-ttu-id="43f4d-198">Till exempel kan ett IIS-program som tillåter Kerberos-autentisering kräva att standard-SPN registreras på ett användar konto som skiljer sig från dator kontot.</span><span class="sxs-lookup"><span data-stu-id="43f4d-198">For example, an IIS application that allows for Kerberos authentication can require the default SPN to be registered to a user account that differs from the computer account.</span></span> <span data-ttu-id="43f4d-199">I sådana fall kan PowerShell-fjärrkommunikation inte använda Kerberos för att autentisera eftersom det kräver ett SPN som är registrerat på dator kontot.</span><span class="sxs-lookup"><span data-stu-id="43f4d-199">In such cases, PowerShell remoting cannot use Kerberos to authenticate because it requires an SPN that is registered to the computer account.</span></span> <span data-ttu-id="43f4d-200">För att lösa det här problemet kan administratörer skapa olika SPN-namn, till exempel genom att använda **Setspn.exe** som är registrerade för olika användar konton och kan skilja mellan dem genom att inkludera port numret i SPN.</span><span class="sxs-lookup"><span data-stu-id="43f4d-200">To resolve this problem, administrators can create different SPNs, such as by using **Setspn.exe**, that are registered to different user accounts and can distinguish between them by including the port number in the SPN.</span></span>

<span data-ttu-id="43f4d-201">Mer information finns i [Översikt över Setspn](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="43f4d-201">For more information, see [Setspn Overview](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).</span></span>

<span data-ttu-id="43f4d-202">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="43f4d-202">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="43f4d-203">-MaxConnectionRetryCount</span><span class="sxs-lookup"><span data-stu-id="43f4d-203">-MaxConnectionRetryCount</span></span>

<span data-ttu-id="43f4d-204">Anger hur många gånger PowerShell försöker upprätta en anslutning till en måldator om det aktuella försöket Miss lyckas på grund av nätverks problem.</span><span class="sxs-lookup"><span data-stu-id="43f4d-204">Specifies the number of times that PowerShell attempts to make a connection to a target machine if the current attempt fails due to network issues.</span></span> <span data-ttu-id="43f4d-205">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="43f4d-205">The default value is 5.</span></span>

<span data-ttu-id="43f4d-206">Den här parametern har lagts till för PowerShell version 5,0.</span><span class="sxs-lookup"><span data-stu-id="43f4d-206">This parameter was added for PowerShell version 5.0.</span></span>

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

### <span data-ttu-id="43f4d-207">-MaximumReceivedDataSizePerCommand</span><span class="sxs-lookup"><span data-stu-id="43f4d-207">-MaximumReceivedDataSizePerCommand</span></span>

<span data-ttu-id="43f4d-208">Anger det maximala antalet byte som den lokala datorn kan ta emot från fjärrdatorn i ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="43f4d-208">Specifies the maximum number of bytes that the local computer can receive from the remote computer in a single command.</span></span> <span data-ttu-id="43f4d-209">Ange ett värde i byte.</span><span class="sxs-lookup"><span data-stu-id="43f4d-209">Enter a value in bytes.</span></span> <span data-ttu-id="43f4d-210">Som standard finns det ingen data storleks gräns.</span><span class="sxs-lookup"><span data-stu-id="43f4d-210">By default, there is no data size limit.</span></span>

<span data-ttu-id="43f4d-211">Det här alternativet är utformat för att skydda resurserna på klient datorn.</span><span class="sxs-lookup"><span data-stu-id="43f4d-211">This option is designed to protect the resources on the client computer.</span></span>

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

### <span data-ttu-id="43f4d-212">-MaximumReceivedObjectSize</span><span class="sxs-lookup"><span data-stu-id="43f4d-212">-MaximumReceivedObjectSize</span></span>

<span data-ttu-id="43f4d-213">Anger den maximala storleken på ett objekt som den lokala datorn kan ta emot från fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="43f4d-213">Specifies the maximum size of an object that the local computer can receive from the remote computer.</span></span> <span data-ttu-id="43f4d-214">Det här alternativet är utformat för att skydda resurserna på klient datorn.</span><span class="sxs-lookup"><span data-stu-id="43f4d-214">This option is designed to protect the resources on the client computer.</span></span> <span data-ttu-id="43f4d-215">Ange ett värde i byte.</span><span class="sxs-lookup"><span data-stu-id="43f4d-215">Enter a value in bytes.</span></span>

<span data-ttu-id="43f4d-216">Om du utelämnar den här parametern i Windows PowerShell 2,0 finns det ingen storleks gräns för objekt.</span><span class="sxs-lookup"><span data-stu-id="43f4d-216">In Windows PowerShell 2.0, if you omit this parameter, there is no object size limit.</span></span> <span data-ttu-id="43f4d-217">Från och med Windows PowerShell 3,0 är standardvärdet 200 MB om du utelämnar den här parametern.</span><span class="sxs-lookup"><span data-stu-id="43f4d-217">Beginning in Windows PowerShell 3.0, if you omit this parameter, the default value is 200 MB.</span></span>

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

### <span data-ttu-id="43f4d-218">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="43f4d-218">-MaximumRedirection</span></span>

<span data-ttu-id="43f4d-219">Anger hur många gånger PowerShell omdirigerar en anslutning till en alternativ Uniform Resource Identifier (URI) innan anslutningen Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="43f4d-219">Determines how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="43f4d-220">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="43f4d-220">The default value is 5.</span></span> <span data-ttu-id="43f4d-221">Värdet 0 (noll) förhindrar all omdirigering.</span><span class="sxs-lookup"><span data-stu-id="43f4d-221">A value of 0 (zero) prevents all redirection.</span></span>

<span data-ttu-id="43f4d-222">Det här alternativet används endast i sessionen när parametern **AllowRedirection** används i kommandot som skapar sessionen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-222">This option is used in the session only when the **AllowRedirection** parameter is used in the command that creates the session.</span></span>

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

### <span data-ttu-id="43f4d-223">-Nocompression</span><span class="sxs-lookup"><span data-stu-id="43f4d-223">-NoCompression</span></span>

<span data-ttu-id="43f4d-224">Inaktiverar paket komprimering i sessionen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-224">Turns off packet compression in the session.</span></span> <span data-ttu-id="43f4d-225">Komprimering använder fler processor cykler, men det gör överföringen snabbare.</span><span class="sxs-lookup"><span data-stu-id="43f4d-225">Compression uses more processor cycles, but it makes transmission faster.</span></span>

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

### <span data-ttu-id="43f4d-226">– Encryption</span><span class="sxs-lookup"><span data-stu-id="43f4d-226">-NoEncryption</span></span>

<span data-ttu-id="43f4d-227">Inaktiverar data kryptering.</span><span class="sxs-lookup"><span data-stu-id="43f4d-227">Turns off data encryption.</span></span>

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

### <span data-ttu-id="43f4d-228">-NoMachineProfile</span><span class="sxs-lookup"><span data-stu-id="43f4d-228">-NoMachineProfile</span></span>

<span data-ttu-id="43f4d-229">Förhindrar inläsning av användarens Windows-användarprofil.</span><span class="sxs-lookup"><span data-stu-id="43f4d-229">Prevents loading the user's Windows user profile.</span></span> <span data-ttu-id="43f4d-230">Därför kan sessionen skapas snabbare, men användarspecifika register inställningar, objekt som miljövariabler och certifikat är inte tillgängliga i sessionen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-230">As a result, the session might be created faster, but user-specific registry settings, items such as environment variables, and certificates are not available in the session.</span></span>

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

### <span data-ttu-id="43f4d-231">-Opentimey</span><span class="sxs-lookup"><span data-stu-id="43f4d-231">-OpenTimeout</span></span>

<span data-ttu-id="43f4d-232">Anger hur länge klient datorn väntar på att sessionen ska upprättas.</span><span class="sxs-lookup"><span data-stu-id="43f4d-232">Determines how long the client computer waits for the session connection to be established.</span></span> <span data-ttu-id="43f4d-233">När intervallet går ut Miss lyckas kommandot för att upprätta anslutningen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-233">When the interval expires, the command to establish the connection fails.</span></span> <span data-ttu-id="43f4d-234">Ange ett värde i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="43f4d-234">Enter a value in milliseconds.</span></span>

<span data-ttu-id="43f4d-235">Standardvärdet är 180000 (3 minuter).</span><span class="sxs-lookup"><span data-stu-id="43f4d-235">The default value is 180000 (3 minutes).</span></span> <span data-ttu-id="43f4d-236">Värdet 0 (noll) innebär ingen tids gräns. kommandot fortsätter på obestämd tid.</span><span class="sxs-lookup"><span data-stu-id="43f4d-236">A value of 0 (zero) means no time-out; the command continues indefinitely.</span></span>

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

### <span data-ttu-id="43f4d-237">-OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="43f4d-237">-OperationTimeout</span></span>

<span data-ttu-id="43f4d-238">Fastställer den längsta tid som en åtgärd i sessionen kan köras.</span><span class="sxs-lookup"><span data-stu-id="43f4d-238">Determines the maximum time that any operation in the session can run.</span></span> <span data-ttu-id="43f4d-239">När intervallet går ut Miss lyckas åtgärden.</span><span class="sxs-lookup"><span data-stu-id="43f4d-239">When the interval expires, the operation fails.</span></span> <span data-ttu-id="43f4d-240">Ange ett värde i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="43f4d-240">Enter a value in milliseconds.</span></span>

<span data-ttu-id="43f4d-241">Standardvärdet är 180000 (3 minuter).</span><span class="sxs-lookup"><span data-stu-id="43f4d-241">The default value is 180000 (3 minutes).</span></span> <span data-ttu-id="43f4d-242">Värdet 0 (noll) innebär ingen tids gräns. åtgärden fortsätter på obestämd tid.</span><span class="sxs-lookup"><span data-stu-id="43f4d-242">A value of 0 (zero) means no time-out; the operation continues indefinitely.</span></span>

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

### <span data-ttu-id="43f4d-243">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="43f4d-243">-OutputBufferingMode</span></span>

<span data-ttu-id="43f4d-244">Anger hur kommandoutdata hanteras i frånkopplade sessioner när utdatabufferten blir full.</span><span class="sxs-lookup"><span data-stu-id="43f4d-244">Determines how command output is managed in disconnected sessions when the output buffer becomes full.</span></span>

<span data-ttu-id="43f4d-245">Om buffring av utdata inte har ställts in i sessionen eller i konfigurationen av sessionen är standardvärdet **block**.</span><span class="sxs-lookup"><span data-stu-id="43f4d-245">If the output buffering mode is not set in the session or in the session configuration, the default value is **Block**.</span></span> <span data-ttu-id="43f4d-246">Användare kan också ändra läget för buffring av utdata när de kopplar från sessionen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-246">Users can also change the output buffering mode when disconnecting the session.</span></span>

<span data-ttu-id="43f4d-247">Om du utelämnar den här parametern, är värdet för **OutputBufferingMode** för Session-objektet none.</span><span class="sxs-lookup"><span data-stu-id="43f4d-247">If you omit this parameter, the value of the **OutputBufferingMode** of the session option object is None.</span></span> <span data-ttu-id="43f4d-248">Värdet **block** eller **Drop** åsidosätter transport alternativet utdata buffer i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-248">A value of **Block** or **Drop** overrides the output buffering mode transport option set in the session configuration.</span></span> <span data-ttu-id="43f4d-249">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="43f4d-249">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="43f4d-250">Undantaget.</span><span class="sxs-lookup"><span data-stu-id="43f4d-250">Block.</span></span> <span data-ttu-id="43f4d-251">När utdatabufferten är full pausas körningen tills bufferten är klar.</span><span class="sxs-lookup"><span data-stu-id="43f4d-251">When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="43f4d-252">Skugg.</span><span class="sxs-lookup"><span data-stu-id="43f4d-252">Drop.</span></span> <span data-ttu-id="43f4d-253">När utdatabufferten är full fortsätter körningen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-253">When the output buffer is full, execution continues.</span></span> <span data-ttu-id="43f4d-254">När nya utdata sparas, ignoreras det äldsta resultatet.</span><span class="sxs-lookup"><span data-stu-id="43f4d-254">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="43f4d-255">Inga.</span><span class="sxs-lookup"><span data-stu-id="43f4d-255">None.</span></span> <span data-ttu-id="43f4d-256">Inget utdata buffer-läge har angetts.</span><span class="sxs-lookup"><span data-stu-id="43f4d-256">No output buffering mode is specified.</span></span>

<span data-ttu-id="43f4d-257">Mer information om transport alternativet för buffring av utdata finns i `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="43f4d-257">For more information about the output buffering mode transport option, see `New-PSTransportOption`.</span></span>

<span data-ttu-id="43f4d-258">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="43f4d-258">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="43f4d-259">-ProxyAccessType</span><span class="sxs-lookup"><span data-stu-id="43f4d-259">-ProxyAccessType</span></span>

<span data-ttu-id="43f4d-260">Bestämmer vilken mekanism som används för att matcha värd namnet.</span><span class="sxs-lookup"><span data-stu-id="43f4d-260">Determines which mechanism is used to resolve the host name.</span></span> <span data-ttu-id="43f4d-261">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="43f4d-261">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="43f4d-262">IEConfig</span><span class="sxs-lookup"><span data-stu-id="43f4d-262">IEConfig</span></span>
- <span data-ttu-id="43f4d-263">WinHttpConfig</span><span class="sxs-lookup"><span data-stu-id="43f4d-263">WinHttpConfig</span></span>
- <span data-ttu-id="43f4d-264">Identifiera automatiskt</span><span class="sxs-lookup"><span data-stu-id="43f4d-264">AutoDetect</span></span>
- <span data-ttu-id="43f4d-265">NoProxyServer</span><span class="sxs-lookup"><span data-stu-id="43f4d-265">NoProxyServer</span></span>
- <span data-ttu-id="43f4d-266">Inga</span><span class="sxs-lookup"><span data-stu-id="43f4d-266">None</span></span>

<span data-ttu-id="43f4d-267">Standardvärdet är none.</span><span class="sxs-lookup"><span data-stu-id="43f4d-267">The default value is None.</span></span>

<span data-ttu-id="43f4d-268">Information om värdena för den här parametern finns i [ProxyAccessType-uppräkning](/dotnet/api/system.management.automation.remoting.proxyaccesstype).</span><span class="sxs-lookup"><span data-stu-id="43f4d-268">For information about the values of this parameter, see [ProxyAccessType Enumeration](/dotnet/api/system.management.automation.remoting.proxyaccesstype).</span></span>

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

### <span data-ttu-id="43f4d-269">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="43f4d-269">-ProxyAuthentication</span></span>

<span data-ttu-id="43f4d-270">Anger den autentiseringsmetod som används för proxy-matchning.</span><span class="sxs-lookup"><span data-stu-id="43f4d-270">Specifies the authentication method that is used for proxy resolution.</span></span> <span data-ttu-id="43f4d-271">De acceptabla värdena för den här parametern är: **Basic**, **Digest** och **Negotiate**.</span><span class="sxs-lookup"><span data-stu-id="43f4d-271">The acceptable values for this parameter are: **Basic**, **Digest**, and **Negotiate**.</span></span> <span data-ttu-id="43f4d-272">Standardvärdet är **Negotiate**.</span><span class="sxs-lookup"><span data-stu-id="43f4d-272">The default value is **Negotiate**.</span></span>

<span data-ttu-id="43f4d-273">Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="43f4d-273">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

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

### <span data-ttu-id="43f4d-274">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="43f4d-274">-ProxyCredential</span></span>

<span data-ttu-id="43f4d-275">Anger de autentiseringsuppgifter som ska användas för proxyautentisering.</span><span class="sxs-lookup"><span data-stu-id="43f4d-275">Specifies the credentials to use for proxy authentication.</span></span> <span data-ttu-id="43f4d-276">Ange en variabel som innehåller ett **PSCredential** -objekt eller ett kommando som hämtar ett **PSCredential** -objekt, t `Get-Credential` . ex. ett kommando.</span><span class="sxs-lookup"><span data-stu-id="43f4d-276">Enter a variable that contains a **PSCredential** object or a command that gets a **PSCredential** object, such as a `Get-Credential` command.</span></span> <span data-ttu-id="43f4d-277">Om det här alternativet inte anges anges inga autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="43f4d-277">If this option is not set, no credentials are specified.</span></span>

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

### <span data-ttu-id="43f4d-278">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="43f4d-278">-SkipCACheck</span></span>

<span data-ttu-id="43f4d-279">Anger att när den ansluter via HTTPS, verifierar inte klienten att Server certifikatet är signerat av en betrodd certifikat utfärdare (CA).</span><span class="sxs-lookup"><span data-stu-id="43f4d-279">Specifies that when it connects over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>

<span data-ttu-id="43f4d-280">Använd bara det här alternativet när fjärrdatorn är betrodd genom att använda en annan mekanism, till exempel när fjärrdatorn är en del av ett nätverk som är fysiskt säkert och isolerat eller när fjärrdatorn visas som en betrodd värd i en WinRM-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="43f4d-280">Use this option only when the remote computer is trusted by using another mechanism, such as when the remote computer is part of a network that is physically secure and isolated or when the remote computer is listed as a trusted host in a WinRM configuration.</span></span>

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

### <span data-ttu-id="43f4d-281">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="43f4d-281">-SkipCNCheck</span></span>

<span data-ttu-id="43f4d-282">Anger att serverns certifikats allmänna namn inte behöver matcha serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="43f4d-282">Specifies that the certificate common name (CN) of the server does not have to match the host name of the server.</span></span> <span data-ttu-id="43f4d-283">Det här alternativet används endast i fjärråtgärder som använder HTTPS-protokollet.</span><span class="sxs-lookup"><span data-stu-id="43f4d-283">This option is used only in remote operations that use the HTTPS protocol.</span></span>

<span data-ttu-id="43f4d-284">Använd endast det här alternativet för betrodda datorer.</span><span class="sxs-lookup"><span data-stu-id="43f4d-284">Use this option only for trusted computers.</span></span>

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

### <span data-ttu-id="43f4d-285">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="43f4d-285">-SkipRevocationCheck</span></span>

<span data-ttu-id="43f4d-286">Verifierar inte Server certifikatets återkallnings status.</span><span class="sxs-lookup"><span data-stu-id="43f4d-286">Does not validate the revocation status of the server certificate.</span></span>

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

### <span data-ttu-id="43f4d-287">– Värdet</span><span class="sxs-lookup"><span data-stu-id="43f4d-287">-UICulture</span></span>

<span data-ttu-id="43f4d-288">Anger användar gränssnitts kulturen som ska användas för sessionen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-288">Specifies the UI culture to use for the session.</span></span>

<span data-ttu-id="43f4d-289">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="43f4d-289">Valid values include:</span></span>

- <span data-ttu-id="43f4d-290">Ett kultur namn i `<languagecode2>-<country/regioncode2>` format, t. ex. `ja-JP`</span><span class="sxs-lookup"><span data-stu-id="43f4d-290">A culture name in `<languagecode2>-<country/regioncode2>` format, such as `ja-JP`</span></span>
- <span data-ttu-id="43f4d-291">En variabel som innehåller ett **CultureInfo** -objekt</span><span class="sxs-lookup"><span data-stu-id="43f4d-291">A variable that contains a **CultureInfo** object</span></span>
- <span data-ttu-id="43f4d-292">Ett kommando som hämtar ett **CultureInfo** -objekt, till exempel `Get-Culture`</span><span class="sxs-lookup"><span data-stu-id="43f4d-292">A command that gets a **CultureInfo** object, such as `Get-Culture`</span></span>

<span data-ttu-id="43f4d-293">Standardvärdet är `$null` och den användar gränssnitts kultur som anges i operativ systemet när sessionen skapas används i sessionen.</span><span class="sxs-lookup"><span data-stu-id="43f4d-293">The default value is `$null`, and the UI culture that is set in the operating system when the session is created is used in the session.</span></span>

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

### <span data-ttu-id="43f4d-294">-UseUTF16</span><span class="sxs-lookup"><span data-stu-id="43f4d-294">-UseUTF16</span></span>

<span data-ttu-id="43f4d-295">Anger att denna cmdlet kodar begäran i UTF16-format istället för UTF8-format.</span><span class="sxs-lookup"><span data-stu-id="43f4d-295">Indicates that this cmdlet encodes the request in UTF16 format instead of UTF8 format.</span></span>

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

### <span data-ttu-id="43f4d-296">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="43f4d-296">CommonParameters</span></span>

<span data-ttu-id="43f4d-297">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="43f4d-297">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="43f4d-298">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="43f4d-298">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="43f4d-299">INDATA</span><span class="sxs-lookup"><span data-stu-id="43f4d-299">INPUTS</span></span>

### <span data-ttu-id="43f4d-300">Inga</span><span class="sxs-lookup"><span data-stu-id="43f4d-300">None</span></span>

<span data-ttu-id="43f4d-301">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="43f4d-301">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="43f4d-302">UTDATA</span><span class="sxs-lookup"><span data-stu-id="43f4d-302">OUTPUTS</span></span>

### <span data-ttu-id="43f4d-303">System. Management. Automation. Remoting. PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="43f4d-303">System.Management.Automation.Remoting.PSSessionOption</span></span>

## <span data-ttu-id="43f4d-304">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="43f4d-304">NOTES</span></span>

<span data-ttu-id="43f4d-305">Om parametern **SessionOption** inte används i ett kommando för att skapa en **PSSession**, bestäms sessions alternativen av egenskapsvärdena för `$PSSessionOption` Preference-variabeln, om den har angetts.</span><span class="sxs-lookup"><span data-stu-id="43f4d-305">If the **SessionOption** parameter is not used in a command to create a **PSSession**, the session options are determined by the property values of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="43f4d-306">Mer information om `$PSSessionOption` variabeln finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="43f4d-306">For more information about the `$PSSessionOption` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="43f4d-307">Egenskaperna för ett konfigurations objekt för en session varierar beroende på vilka alternativ som har angetts för konfigurationen av sessionen och värdena för dessa alternativ.</span><span class="sxs-lookup"><span data-stu-id="43f4d-307">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="43f4d-308">Dessutom har sessionsinställningar som använder en konfigurations fil för sessionen ytterligare egenskaper.</span><span class="sxs-lookup"><span data-stu-id="43f4d-308">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="43f4d-309">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="43f4d-309">RELATED LINKS</span></span>

[<span data-ttu-id="43f4d-310">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="43f4d-310">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="43f4d-311">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="43f4d-311">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="43f4d-312">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="43f4d-312">New-PSSession</span></span>](New-PSSession.md)
