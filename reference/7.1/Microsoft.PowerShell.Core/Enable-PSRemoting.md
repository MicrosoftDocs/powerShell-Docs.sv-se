---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: 5b69a1ec6945f910815d5469fad77213b517d7b6
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342305"
---
# <span data-ttu-id="04154-103">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="04154-103">Enable-PSRemoting</span></span>

## <span data-ttu-id="04154-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="04154-104">SYNOPSIS</span></span>
<span data-ttu-id="04154-105">Konfigurerar datorn att ta emot fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="04154-105">Configures the computer to receive remote commands.</span></span>

## <span data-ttu-id="04154-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="04154-106">SYNTAX</span></span>

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="04154-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="04154-107">DESCRIPTION</span></span>

<span data-ttu-id="04154-108">`Enable-PSRemoting`Cmdleten konfigurerar datorn att ta emot PowerShell-fjärrkommandon som skickas med hjälp av WS-Management teknik.</span><span class="sxs-lookup"><span data-stu-id="04154-108">The `Enable-PSRemoting` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the WS-Management technology.</span></span> <span data-ttu-id="04154-109">WS-Management-baserad PowerShell-fjärrkommunikation stöds för närvarande endast på Windows-plattformen.</span><span class="sxs-lookup"><span data-stu-id="04154-109">WS-Management based PowerShell remoting is currently supported only on Windows platform.</span></span>

<span data-ttu-id="04154-110">PowerShell-fjärrkommunikation är aktiverat som standard på Windows Server-plattformar.</span><span class="sxs-lookup"><span data-stu-id="04154-110">PowerShell remoting is enabled by default on Windows Server platforms.</span></span> <span data-ttu-id="04154-111">Du kan använda `Enable-PSRemoting` för att aktivera PowerShell-fjärrkommunikation i andra versioner av Windows som stöds och återaktivera fjärr kommunikation om den blir inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="04154-111">You can use `Enable-PSRemoting` to enable PowerShell remoting on other supported versions of Windows and to re-enable remoting if it becomes disabled.</span></span>

<span data-ttu-id="04154-112">Du behöver bara köra det här kommandot en gången på varje dator som ska ta emot kommandon.</span><span class="sxs-lookup"><span data-stu-id="04154-112">You have to run this command only one time on each computer that will receive commands.</span></span> <span data-ttu-id="04154-113">Du behöver inte köra den på datorer som bara skickar kommandon.</span><span class="sxs-lookup"><span data-stu-id="04154-113">You do not have to run it on computers that only send commands.</span></span> <span data-ttu-id="04154-114">Eftersom konfigurationen startar lyssnare för att acceptera fjärr anslutningar, är det försiktig att bara köra den där det behövs.</span><span class="sxs-lookup"><span data-stu-id="04154-114">Because the configuration starts listeners to accept remote connections, it is prudent to run it only where it is needed.</span></span>

<span data-ttu-id="04154-115">Att aktivera PowerShell-fjärrkommunikation i klient versioner av Windows när datorn är i ett offentligt nätverk är normalt inte tillåten, men du kan hoppa över den här begränsningen genom att använda parametern **SkipNetworkProfileCheck** .</span><span class="sxs-lookup"><span data-stu-id="04154-115">Enabling PowerShell remoting on client versions of Windows when the computer is on a public network is normally disallowed, but you can skip this restriction by using the **SkipNetworkProfileCheck** parameter.</span></span> <span data-ttu-id="04154-116">Mer information finns i beskrivningen av parametern **SkipNetworkProfileCheck** .</span><span class="sxs-lookup"><span data-stu-id="04154-116">For more information, see the description of the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="04154-117">Det kan finnas flera PowerShell-installationer sida vid sida på en enda dator.</span><span class="sxs-lookup"><span data-stu-id="04154-117">Multiple PowerShell installations can exist side-by-side on a single computer.</span></span> <span data-ttu-id="04154-118">Vid körning `Enable-PSRemoting` konfigureras en slut punkt för Fjärrslutpunkter för den speciella installations version som du kör cmdleten i.</span><span class="sxs-lookup"><span data-stu-id="04154-118">Running `Enable-PSRemoting` will configure a remoting endpoint for the specific installation version that you are running the cmdlet in.</span></span> <span data-ttu-id="04154-119">Så om du kör `Enable-PSRemoting` powershell 6,2 konfigureras en slut punkt för fjärr kommunikation som kör powershell 6,2.</span><span class="sxs-lookup"><span data-stu-id="04154-119">So if you run `Enable-PSRemoting` while running PowerShell 6.2, a remoting endpoint will be configured that runs PowerShell 6.2.</span></span> <span data-ttu-id="04154-120">Om du kör `Enable-PSRemoting` PowerShell 7 – för hands version konfigureras en fjärrslutpunkt som kör PowerShell 7 – för hands version.</span><span class="sxs-lookup"><span data-stu-id="04154-120">If you run `Enable-PSRemoting` while running PowerShell 7-preview, a remoting endpoint will be configured that runs PowerShell 7-preview.</span></span>

<span data-ttu-id="04154-121">`Enable-PSRemoting` skapar två slut punkts konfigurationer för fjärrkörning vid behov.</span><span class="sxs-lookup"><span data-stu-id="04154-121">`Enable-PSRemoting` creates two remoting endpoint configurations as needed.</span></span> <span data-ttu-id="04154-122">Om slut punkts konfigurationerna redan finns är de bara säkra att de är aktiverade.</span><span class="sxs-lookup"><span data-stu-id="04154-122">If the endpoint configurations already exist, then they are simply ensured to be enabled.</span></span> <span data-ttu-id="04154-123">De skapade konfigurationerna är identiska men har olika namn.</span><span class="sxs-lookup"><span data-stu-id="04154-123">The created configurations are identical but have different names.</span></span> <span data-ttu-id="04154-124">Ett har ett enkelt namn som motsvarar den PowerShell-version som är värd för sessionen.</span><span class="sxs-lookup"><span data-stu-id="04154-124">One will have a simple name corresponding to the PowerShell version that hosts the session.</span></span> <span data-ttu-id="04154-125">Det andra konfigurations namnet innehåller mer detaljerad information om den PowerShell-version som är värd för sessionen.</span><span class="sxs-lookup"><span data-stu-id="04154-125">The other configuration name contains more detailed information about the PowerShell version which hosts the session.</span></span> <span data-ttu-id="04154-126">Om du till exempel kör `Enable-PSRemoting` i PowerShell 6,2 får du två konfigurerade slut punkter med namnet **PowerShell. 6** , **PowerShell. 6.2.2**.</span><span class="sxs-lookup"><span data-stu-id="04154-126">For example, when running `Enable-PSRemoting` in PowerShell 6.2, you will get two configured endpoints named **PowerShell.6** , **PowerShell.6.2.2**.</span></span>
<span data-ttu-id="04154-127">På så sätt kan du skapa en anslutning till den senaste PowerShell 6-värd versionen med hjälp av det enkla namnet **PowerShell. 6**.</span><span class="sxs-lookup"><span data-stu-id="04154-127">This allows you to create a connection to the latest PowerShell 6 host version by using the simple name **PowerShell.6**.</span></span> <span data-ttu-id="04154-128">Eller så kan du ansluta till en angiven PowerShell-värd version med längre namnet **PowerShell. 6.2.2**.</span><span class="sxs-lookup"><span data-stu-id="04154-128">Or you can connect to a specific PowerShell host version by using the longer name **PowerShell.6.2.2**.</span></span>

<span data-ttu-id="04154-129">Om du vill använda de nyligen aktiverade slut punkterna för fjärr kommunikation måste du ange dem med hjälp av namn med parametern **ConfigurationName** när du skapar en fjärr anslutning med `Invoke-Command` `New-PSSession` `Enter-PSSession` cmdletarna,,.</span><span class="sxs-lookup"><span data-stu-id="04154-129">To use the newly enabled remoting endpoints, you must specify them by name with the **ConfigurationName** parameter when creating a remote connection using the `Invoke-Command`,`New-PSSession`,`Enter-PSSession` cmdlets.</span></span> <span data-ttu-id="04154-130">Mer information finns i exempel 4.</span><span class="sxs-lookup"><span data-stu-id="04154-130">For more information, see Example 4.</span></span>

<span data-ttu-id="04154-131">`Enable-PSRemoting`Cmdleten utför följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="04154-131">The `Enable-PSRemoting` cmdlet performs the following operations:</span></span>

- <span data-ttu-id="04154-132">Kör cmdleten [set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) som utför följande uppgifter:</span><span class="sxs-lookup"><span data-stu-id="04154-132">Runs the [Set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) cmdlet, which performs the following tasks:</span></span>
  - <span data-ttu-id="04154-133">Startar tjänsten WinRM.</span><span class="sxs-lookup"><span data-stu-id="04154-133">Starts the WinRM service.</span></span>
  - <span data-ttu-id="04154-134">Ställer in start typen på WinRM-tjänsten till automatisk.</span><span class="sxs-lookup"><span data-stu-id="04154-134">Sets the startup type on the WinRM service to Automatic.</span></span>
  - <span data-ttu-id="04154-135">Skapar en lyssnare som accepterar begär Anden på alla IP-adresser.</span><span class="sxs-lookup"><span data-stu-id="04154-135">Creates a listener to accept requests on any IP address.</span></span>
  - <span data-ttu-id="04154-136">Aktiverar ett brand Väggs undantag för WS-Management kommunikation.</span><span class="sxs-lookup"><span data-stu-id="04154-136">Enables a firewall exception for WS-Management communications.</span></span>
  - <span data-ttu-id="04154-137">Skapar de enkla och långa namn för sessionens slut punkts konfiguration vid behov.</span><span class="sxs-lookup"><span data-stu-id="04154-137">Creates the simple and long name session endpoint configurations if needed.</span></span>
  - <span data-ttu-id="04154-138">Aktiverar alla konfigurationer för sessioner.</span><span class="sxs-lookup"><span data-stu-id="04154-138">Enables all session configurations.</span></span>
  - <span data-ttu-id="04154-139">Ändrar säkerhets beskrivningen för alla sessionsinställningar för att tillåta fjärråtkomst.</span><span class="sxs-lookup"><span data-stu-id="04154-139">Changes the security descriptor of all session configurations to allow remote access.</span></span>
- <span data-ttu-id="04154-140">Startar om WinRM-tjänsten för att göra föregående ändringar gällande.</span><span class="sxs-lookup"><span data-stu-id="04154-140">Restarts the WinRM service to make the preceding changes effective.</span></span>

<span data-ttu-id="04154-141">Om du vill köra denna cmdlet på Windows-plattformen startar du PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="04154-141">To run this cmdlet on the Windows platform, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="04154-142">Denna cmdlet är inte tillgänglig på Linux-eller MacOS-versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="04154-142">This cmdlet is not available on Linux or MacOS versions of PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="04154-143">Denna cmdlet påverkar inte konfigurationer för Fjärrslutpunkter som skapats av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="04154-143">This cmdlet does not affect remote endpoint configurations created by Windows PowerShell.</span></span>
> <span data-ttu-id="04154-144">Den påverkar bara slut punkter som skapats med PowerShell version 6 och senare.</span><span class="sxs-lookup"><span data-stu-id="04154-144">It only affects endpoints created with PowerShell version 6 and greater.</span></span> <span data-ttu-id="04154-145">Om du vill aktivera och inaktivera PowerShell-Fjärrslutpunkter som finns i Windows PowerShell kör du `Enable-PSRemoting` cmdleten inifrån en Windows PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="04154-145">To enable and disable PowerShell remoting endpoints that are hosted by Windows PowerShell, run the `Enable-PSRemoting` cmdlet from within a Windows PowerShell session.</span></span>

## <span data-ttu-id="04154-146">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="04154-146">EXAMPLES</span></span>

### <span data-ttu-id="04154-147">Exempel 1: Konfigurera en dator för att ta emot fjärrkommandon</span><span class="sxs-lookup"><span data-stu-id="04154-147">Example 1: Configure a computer to receive remote commands</span></span>

<span data-ttu-id="04154-148">Det här kommandot konfigurerar datorn att ta emot fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="04154-148">This command configures the computer to receive remote commands.</span></span>

```powershell
Enable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### <span data-ttu-id="04154-149">Exempel 2: Konfigurera en dator för att ta emot fjärrkommandon utan att bekräfta en bekräftelse</span><span class="sxs-lookup"><span data-stu-id="04154-149">Example 2: Configure a computer to receive remote commands without a confirmation prompt</span></span>

<span data-ttu-id="04154-150">Det här kommandot konfigurerar datorn att ta emot fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="04154-150">This command configures the computer to receive remote commands.</span></span>
<span data-ttu-id="04154-151">**Force** -parametern förhindrar användarens prompter.</span><span class="sxs-lookup"><span data-stu-id="04154-151">The **Force** parameter suppresses the user prompts.</span></span>

```powershell
Enable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### <span data-ttu-id="04154-152">Exempel 3: Tillåt fjärråtkomst på klienter</span><span class="sxs-lookup"><span data-stu-id="04154-152">Example 3: Allow remote access on clients</span></span>

<span data-ttu-id="04154-153">Det här exemplet visar hur du tillåter fjärråtkomst från offentliga nätverk på klient versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="04154-153">This example shows how to allow remote access from public networks on client versions of the Windows operating system.</span></span> <span data-ttu-id="04154-154">Namnet på brand Väggs regeln kan vara olika för olika versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="04154-154">The name of the firewall rule can be different for different versions of Windows.</span></span>
<span data-ttu-id="04154-155">Använd `Get-NetFirewallRule` om du vill visa en lista över regler.</span><span class="sxs-lookup"><span data-stu-id="04154-155">Use `Get-NetFirewallRule` to see a list of rules.</span></span> <span data-ttu-id="04154-156">Innan du aktiverar brand Väggs regeln kan du Visa säkerhets inställningarna i regeln för att kontrol lera att konfigurationen är lämplig för din miljö.</span><span class="sxs-lookup"><span data-stu-id="04154-156">Before enabling the firewall rule, view the security settings in the rule to verify that the configuration is appropriate for your environment.</span></span>

```powershell
Get-NetFirewallRule -Name 'WINRM*' | Select-Object Name
```

```Output
Name
----
WINRM-HTTP-In-TCP-NoScope
WINRM-HTTP-In-TCP
WINRM-HTTP-Compat-In-TCP-NoScope
WINRM-HTTP-Compat-In-TCP
```

```powershell
Enable-PSRemoting -SkipNetworkProfileCheck -Force
Set-NetFirewallRule -Name 'WINRM-HTTP-In-TCP' -RemoteAddress Any
```

<span data-ttu-id="04154-157">Som standard `Enable-PSRemoting` skapar nätverks regler som tillåter fjärråtkomst från privata nätverk och domän nätverk.</span><span class="sxs-lookup"><span data-stu-id="04154-157">By default, `Enable-PSRemoting` creates network rules that allow remote access from private and domain networks.</span></span> <span data-ttu-id="04154-158">Kommandot använder parametern **SkipNetworkProfileCheck** för att tillåta fjärråtkomst från offentliga nätverk i samma lokala undernät.</span><span class="sxs-lookup"><span data-stu-id="04154-158">The command uses the **SkipNetworkProfileCheck** parameter to allow remote access from public networks in the same local subnet.</span></span> <span data-ttu-id="04154-159">Kommandot anger **Force** -parametern för att ignorera bekräftelse meddelanden.</span><span class="sxs-lookup"><span data-stu-id="04154-159">The command specifies the **Force** parameter to suppress confirmation messages.</span></span>

<span data-ttu-id="04154-160">**SkipNetworkProfileCheck** -parametern påverkar inte Server versioner av Windows operativ system, som tillåter fjärråtkomst från offentliga nätverk i samma lokala undernät som standard.</span><span class="sxs-lookup"><span data-stu-id="04154-160">The **SkipNetworkProfileCheck** parameter does not affect server versions of the Windows operating system, which allow remote access from public networks in the same local subnet by default.</span></span>

<span data-ttu-id="04154-161">`Set-NetFirewallRule`Cmdleten i modulen **netsecurity** lägger till en brand Väggs regel som tillåter fjärråtkomst från offentliga nätverk från valfri fjärrplats.</span><span class="sxs-lookup"><span data-stu-id="04154-161">The `Set-NetFirewallRule` cmdlet in the **NetSecurity** module adds a firewall rule that allows remote access from public networks from any remote location.</span></span> <span data-ttu-id="04154-162">Detta omfattar platser i olika undernät.</span><span class="sxs-lookup"><span data-stu-id="04154-162">This includes locations in different subnets.</span></span>

### <span data-ttu-id="04154-163">Exempel 4: skapa en fjärrsession till den nyligen aktiverade slut punkts konfigurationen</span><span class="sxs-lookup"><span data-stu-id="04154-163">Example 4: Create a remote session to the newly enabled endpoint configuration</span></span>

<span data-ttu-id="04154-164">Det här exemplet visar hur du aktiverar PowerShell-fjärrkommunikation på en dator, hittar de konfigurerade slut punkts namnen och skapar en fjärrsession till en av slut punkterna.</span><span class="sxs-lookup"><span data-stu-id="04154-164">This example shows how to enable PowerShell remoting on a computer, find the configured endpoint names, and create a remote session to one of the endpoints.</span></span>

<span data-ttu-id="04154-165">Det första kommandot aktiverar PowerShell-fjärrkommunikation på datorn.</span><span class="sxs-lookup"><span data-stu-id="04154-165">The first command enables PowerShell remoting on the computer.</span></span>

<span data-ttu-id="04154-166">Det andra kommandot visar slut punkts konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="04154-166">The second command lists the endpoint configurations.</span></span>

<span data-ttu-id="04154-167">Det tredje kommandot skapar en PowerShell-fjärrsession till samma dator och anger **PowerShell. 6** -slutpunkten efter namn.</span><span class="sxs-lookup"><span data-stu-id="04154-167">The third command creates a remote PowerShell session to the same machine, specifying the **PowerShell.6** endpoint by name.</span></span> <span data-ttu-id="04154-168">Fjärrsessionen kommer att vara värd för den senaste PowerShell 6-versionen (6.2.2).</span><span class="sxs-lookup"><span data-stu-id="04154-168">The remote session will be hosted with the latest PowerShell 6 version (6.2.2).</span></span>

<span data-ttu-id="04154-169">Det sista kommandot använder `$PSVersionTable` variabeln i fjärrsessionen för att visa den PowerShell-version som är värd för sessionen.</span><span class="sxs-lookup"><span data-stu-id="04154-169">The last command accesses the `$PSVersionTable` variable in the remote session to display the PowerShell version that is hosting the session.</span></span>

```powershell
Enable-PSRemoting -Force

Get-PSSessionConfiguration

$session = New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6

Invoke-Command -Session $session -ScriptBlock { $PSVersionTable }
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name                           Value
----                           -----
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0…}
PSEdition                      Core
PSRemotingProtocolVersion      2.3
Platform                       Win32NT
SerializationVersion           1.1.0.1
GitCommitId                    6.2.2
WSManStackVersion              3.0
PSVersion                      6.2.2
OS                             Microsoft Windows 10.0.18363
```

> [!NOTE]
> <span data-ttu-id="04154-170">Namnet på brand Väggs regeln kan vara olika beroende på Windows-versionen.</span><span class="sxs-lookup"><span data-stu-id="04154-170">The name of the firewall rule can be different depending on the version of Windows.</span></span> <span data-ttu-id="04154-171">Använd `Get-NetFirewallRule` cmdleten för att visa namnen på reglerna i systemet.</span><span class="sxs-lookup"><span data-stu-id="04154-171">Use the `Get-NetFirewallRule` cmdlet to list the names of the rules on your system.</span></span>

## <span data-ttu-id="04154-172">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="04154-172">PARAMETERS</span></span>

### <span data-ttu-id="04154-173">-Confirm</span><span class="sxs-lookup"><span data-stu-id="04154-173">-Confirm</span></span>

<span data-ttu-id="04154-174">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="04154-174">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04154-175">-Force</span><span class="sxs-lookup"><span data-stu-id="04154-175">-Force</span></span>

<span data-ttu-id="04154-176">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="04154-176">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="04154-177">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="04154-177">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="04154-178">Anger att denna cmdlet aktiverar fjärr kommunikation på klient versioner av Windows operativ system när datorn är i ett offentligt nätverk.</span><span class="sxs-lookup"><span data-stu-id="04154-178">Indicates that this cmdlet enables remoting on client versions of the Windows operating system when the computer is on a public network.</span></span> <span data-ttu-id="04154-179">Med den här parametern kan du använda en brand Väggs regel för offentliga nätverk som endast tillåter fjärråtkomst från datorer i samma lokala undernät.</span><span class="sxs-lookup"><span data-stu-id="04154-179">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="04154-180">Den här parametern påverkar inte Server versioner av Windows operativ system, som som standard har en lokal brand Väggs regel för offentliga nätverk.</span><span class="sxs-lookup"><span data-stu-id="04154-180">This parameter does not affect server versions of the Windows operating system, which, by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="04154-181">Om den lokala brand Väggs regeln är inaktive rad på en server version `Enable-PSRemoting` aktiverar du den igen, oavsett värdet för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="04154-181">If the local subnet firewall rule is disabled on a server version, `Enable-PSRemoting` re-enables it, regardless of the value of this parameter.</span></span>

<span data-ttu-id="04154-182">Om du vill ta bort den lokala under näts begränsningen och aktivera fjärråtkomst från alla platser i offentliga nätverk använder du `Set-NetFirewallRule` cmdleten i modulen **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="04154-182">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="04154-183">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="04154-183">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="04154-184">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="04154-184">-WhatIf</span></span>

<span data-ttu-id="04154-185">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="04154-185">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="04154-186">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="04154-186">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04154-187">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="04154-187">CommonParameters</span></span>

<span data-ttu-id="04154-188">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="04154-188">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="04154-189">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="04154-189">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="04154-190">INDATA</span><span class="sxs-lookup"><span data-stu-id="04154-190">INPUTS</span></span>

### <span data-ttu-id="04154-191">Inget</span><span class="sxs-lookup"><span data-stu-id="04154-191">None</span></span>

<span data-ttu-id="04154-192">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="04154-192">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="04154-193">UTDATA</span><span class="sxs-lookup"><span data-stu-id="04154-193">OUTPUTS</span></span>

### <span data-ttu-id="04154-194">System. String</span><span class="sxs-lookup"><span data-stu-id="04154-194">System.String</span></span>

<span data-ttu-id="04154-195">Denna cmdlet returnerar strängar som beskriver dess resultat.</span><span class="sxs-lookup"><span data-stu-id="04154-195">This cmdlet returns strings that describe its results.</span></span>

## <span data-ttu-id="04154-196">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="04154-196">NOTES</span></span>

<span data-ttu-id="04154-197">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="04154-197">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="04154-198">I Server versioner av Windows-operativsystemet `Enable-PSRemoting` skapar brand Väggs regler för privata nätverk och domän nätverk som tillåter fjärråtkomst, och skapar en brand Väggs regel för offentliga nätverk som endast tillåter fjärråtkomst från datorer i samma lokala undernät.</span><span class="sxs-lookup"><span data-stu-id="04154-198">On server versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow remote access, and creates a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="04154-199">I klient versioner av Windows operativ system `Enable-PSRemoting` skapar brand Väggs regler för privata nätverk och domän nätverk som tillåter obegränsad fjärråtkomst.</span><span class="sxs-lookup"><span data-stu-id="04154-199">On client versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow unrestricted remote access.</span></span> <span data-ttu-id="04154-200">Om du vill skapa en brand Väggs regel för offentliga nätverk som tillåter fjärråtkomst från samma lokala undernät använder du parametern **SkipNetworkProfileCheck** .</span><span class="sxs-lookup"><span data-stu-id="04154-200">To create a firewall rule for public networks that allows remote access from the same local subnet, use the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="04154-201">På klient-eller Server versioner av Windows-operativsystemet, för att skapa en brand Väggs regel för offentliga nätverk som tar bort begränsningen lokalt undernät och tillåter fjärråtkomst, använder du `Set-NetFirewallRule` cmdleten i modulen netsecurity för att köra följande kommando: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span><span class="sxs-lookup"><span data-stu-id="04154-201">On client or server versions of the Windows operating system, to create a firewall rule for public networks that removes the local subnet restriction and allows remote access , use the `Set-NetFirewallRule` cmdlet in the NetSecurity module to run the following command: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span></span>

<span data-ttu-id="04154-202">`Enable-PSRemoting` aktiverar alla sessionsinställningar genom att ställa in värdet för egenskapen **Enabled** för alla sessioner till `$True` .</span><span class="sxs-lookup"><span data-stu-id="04154-202">`Enable-PSRemoting` enables all session configurations by setting the value of the **Enabled** property of all session configurations to `$True`.</span></span>

<span data-ttu-id="04154-203">`Enable-PSRemoting` tar bort inställningarna för **Deny_All** och **Network_Deny_All** .</span><span class="sxs-lookup"><span data-stu-id="04154-203">`Enable-PSRemoting` removes the **Deny_All** and **Network_Deny_All** settings.</span></span> <span data-ttu-id="04154-204">Detta ger fjärråtkomst till sessionsbaserade konfigurationer som har reserver ATS för lokal användning.</span><span class="sxs-lookup"><span data-stu-id="04154-204">This provides remote access to session configurations that were reserved for local use.</span></span>

## <span data-ttu-id="04154-205">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="04154-205">RELATED LINKS</span></span>

[<span data-ttu-id="04154-206">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="04154-206">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="04154-207">Aktivera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="04154-207">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="04154-208">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="04154-208">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="04154-209">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="04154-209">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="04154-210">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="04154-210">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="04154-211">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="04154-211">Disable-PSRemoting</span></span>](Disable-PSRemoting.md)

[<span data-ttu-id="04154-212">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="04154-212">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="04154-213">about_Remote</span><span class="sxs-lookup"><span data-stu-id="04154-213">about_Remote</span></span>](About/about_Remote.md)

[<span data-ttu-id="04154-214">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="04154-214">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)
