---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: 0c8c386ab376afde3d15fcd29b3f653b3f738f63
ms.sourcegitcommit: 0e0f45d0d8deb8c9088a4f4a32218edde052b686
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/17/2020
ms.locfileid: "93268065"
---
# <span data-ttu-id="ee9ee-103">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="ee9ee-103">Enable-PSRemoting</span></span>

## <span data-ttu-id="ee9ee-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ee9ee-104">SYNOPSIS</span></span>
<span data-ttu-id="ee9ee-105">Konfigurerar datorn att ta emot fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-105">Configures the computer to receive remote commands.</span></span>

## <span data-ttu-id="ee9ee-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ee9ee-106">SYNTAX</span></span>

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ee9ee-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ee9ee-107">DESCRIPTION</span></span>

<span data-ttu-id="ee9ee-108">`Enable-PSRemoting`Cmdleten konfigurerar datorn att ta emot PowerShell-fjärrkommandon som skickas med hjälp av WS-Management teknik.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-108">The `Enable-PSRemoting` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the WS-Management technology.</span></span>

<span data-ttu-id="ee9ee-109">PowerShell-fjärrkommunikation är aktiverat som standard på Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-109">PowerShell remoting is enabled by default on Windows Server 2012.</span></span> <span data-ttu-id="ee9ee-110">Du kan använda `Enable-PSRemoting` för att aktivera PowerShell-fjärrkommunikation i andra versioner av Windows som stöds och återaktivera fjärr kommunikation på Windows Server 2012 om den inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-110">You can use `Enable-PSRemoting` to enable PowerShell remoting on other supported versions of Windows and to re-enable remoting on Windows Server 2012 if it becomes disabled.</span></span>

<span data-ttu-id="ee9ee-111">Du behöver bara köra det här kommandot en gången på varje dator som ska ta emot kommandon.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-111">You have to run this command only one time on each computer that will receive commands.</span></span> <span data-ttu-id="ee9ee-112">Du behöver inte köra den på datorer som bara skickar kommandon.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-112">You do not have to run it on computers that only send commands.</span></span> <span data-ttu-id="ee9ee-113">Eftersom konfigurationen startar lyssnare, är det försiktig att bara köra den där det behövs.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-113">Because the configuration starts listeners, it is prudent to run it only where it is needed.</span></span>

<span data-ttu-id="ee9ee-114">Från och med PowerShell 3,0 `Enable-PSRemoting` kan cmdlet: en aktivera PowerShell-fjärrkommunikation på klient versioner av Windows när datorn finns i ett offentligt nätverk.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-114">Beginning in PowerShell 3.0, the `Enable-PSRemoting` cmdlet can enable PowerShell remoting on client versions of Windows when the computer is on a public network.</span></span> <span data-ttu-id="ee9ee-115">Mer information finns i beskrivningen av parametern **SkipNetworkProfileCheck** .</span><span class="sxs-lookup"><span data-stu-id="ee9ee-115">For more information, see the description of the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="ee9ee-116">`Enable-PSRemoting`Cmdleten utför följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="ee9ee-116">The `Enable-PSRemoting` cmdlet performs the following operations:</span></span>

- <span data-ttu-id="ee9ee-117">Kör cmdleten [set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) som utför följande uppgifter:</span><span class="sxs-lookup"><span data-stu-id="ee9ee-117">Runs the [Set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) cmdlet, which performs the following tasks:</span></span>
  - <span data-ttu-id="ee9ee-118">Startar tjänsten WinRM.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-118">Starts the WinRM service.</span></span>
  - <span data-ttu-id="ee9ee-119">Ställer in start typen på WinRM-tjänsten till automatisk.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-119">Sets the startup type on the WinRM service to Automatic.</span></span>
  - <span data-ttu-id="ee9ee-120">Skapar en lyssnare som accepterar begär Anden på alla IP-adresser.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-120">Creates a listener to accept requests on any IP address.</span></span>
  - <span data-ttu-id="ee9ee-121">Aktiverar ett brand Väggs undantag för WS-Management kommunikation.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-121">Enables a firewall exception for WS-Management communications.</span></span>
  - <span data-ttu-id="ee9ee-122">Registrerar konfigurationerna för **Microsoft. PowerShell** och **Microsoft. PowerShell. Workflow** -sessioner, om de inte redan har registrerats.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-122">Registers the **Microsoft.PowerShell** and **Microsoft.PowerShell.Workflow** session configurations, if it they are not already registered.</span></span>
  - <span data-ttu-id="ee9ee-123">Registrerar konfigurationen för **Microsoft. PowerShell32** -sessionen på 64-bitars datorer, om den inte redan är registrerad.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-123">Registers the **Microsoft.PowerShell32** session configuration on 64-bit computers, if it is not already registered.</span></span>
  - <span data-ttu-id="ee9ee-124">Aktiverar alla konfigurationer för sessioner.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-124">Enables all session configurations.</span></span>
  - <span data-ttu-id="ee9ee-125">Ändrar säkerhets beskrivningen för alla sessionsinställningar för att tillåta fjärråtkomst.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-125">Changes the security descriptor of all session configurations to allow remote access.</span></span>
- <span data-ttu-id="ee9ee-126">Startar om WinRM-tjänsten för att göra föregående ändringar gällande.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-126">Restarts the WinRM service to make the preceding changes effective.</span></span>

<span data-ttu-id="ee9ee-127">Om du vill köra denna cmdlet på Windows-plattformen startar du PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-127">To run this cmdlet on the Windows platform, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="ee9ee-128">Detta gäller inte för Linux-eller MacOS-versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-128">This does not apply to Linux or MacOS versions of PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="ee9ee-129">På system som har både PowerShell 3,0 och PowerShell 2,0 ska du inte använda PowerShell 2,0 för att köra `Enable-PSRemoting` `Disable-PSRemoting` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-129">On systems that have both PowerShell 3.0 and PowerShell 2.0, do not use PowerShell 2.0 to run the `Enable-PSRemoting` and `Disable-PSRemoting` cmdlets.</span></span> <span data-ttu-id="ee9ee-130">Kommandona kan verka fungera, men fjärrkommunikationen är inte korrekt konfigurerad.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-130">The commands might appear to succeed, but the remoting is not configured correctly.</span></span> <span data-ttu-id="ee9ee-131">Fjärrkommandon och senare försöker aktivera och inaktivera fjärr kommunikation fungerar sannolikt inte.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-131">Remote commands and later attempts to enable and disable remoting, are likely to fail.</span></span>

## <span data-ttu-id="ee9ee-132">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ee9ee-132">EXAMPLES</span></span>

### <span data-ttu-id="ee9ee-133">Exempel 1: Konfigurera en dator för att ta emot fjärrkommandon</span><span class="sxs-lookup"><span data-stu-id="ee9ee-133">Example 1: Configure a computer to receive remote commands</span></span>

<span data-ttu-id="ee9ee-134">Det här kommandot konfigurerar datorn att ta emot fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-134">This command configures the computer to receive remote commands.</span></span>

```powershell
Enable-PSRemoting
```

### <span data-ttu-id="ee9ee-135">Exempel 2: Konfigurera en dator för att ta emot fjärrkommandon utan att bekräfta en bekräftelse</span><span class="sxs-lookup"><span data-stu-id="ee9ee-135">Example 2: Configure a computer to receive remote commands without a confirmation prompt</span></span>

<span data-ttu-id="ee9ee-136">Det här kommandot konfigurerar datorn att ta emot fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-136">This command configures the computer to receive remote commands.</span></span>
<span data-ttu-id="ee9ee-137">**Force** -parametern förhindrar användarens prompter.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-137">The **Force** parameter suppresses the user prompts.</span></span>

```powershell
Enable-PSRemoting -Force
```

### <span data-ttu-id="ee9ee-138">Exempel 3: Tillåt fjärråtkomst på klienter</span><span class="sxs-lookup"><span data-stu-id="ee9ee-138">Example 3: Allow remote access on clients</span></span>

<span data-ttu-id="ee9ee-139">Det här exemplet visar hur du tillåter fjärråtkomst från offentliga nätverk på klient versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-139">This example shows how to allow remote access from public networks on client versions of the Windows operating system.</span></span> <span data-ttu-id="ee9ee-140">Namnet på brand Väggs regeln kan vara olika för olika versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-140">The name of the firewall rule can be different for different versions of Windows.</span></span>
<span data-ttu-id="ee9ee-141">Använd `Get-NetFirewallRule` om du vill visa en lista över regler.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-141">Use `Get-NetFirewallRule` to see a list of rules.</span></span> <span data-ttu-id="ee9ee-142">Innan du aktiverar brand Väggs regeln kan du Visa säkerhets inställningarna i regeln för att kontrol lera att konfigurationen är lämplig för din miljö.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-142">Before enabling the firewall rule, view the security settings in the rule to verify that the configuration is appropriate for your environment.</span></span>

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

<span data-ttu-id="ee9ee-143">Som standard `Enable-PSRemoting` skapar nätverks regler som tillåter fjärråtkomst från privata nätverk och domän nätverk.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-143">By default, `Enable-PSRemoting` creates network rules that allow remote access from private and domain networks.</span></span> <span data-ttu-id="ee9ee-144">Kommandot använder parametern **SkipNetworkProfileCheck** för att tillåta fjärråtkomst från offentliga nätverk i samma lokala undernät.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-144">The command uses the **SkipNetworkProfileCheck** parameter to allow remote access from public networks in the same local subnet.</span></span> <span data-ttu-id="ee9ee-145">Kommandot anger **Force** -parametern för att ignorera bekräftelse meddelanden.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-145">The command specifies the **Force** parameter to suppress confirmation messages.</span></span>

<span data-ttu-id="ee9ee-146">**SkipNetworkProfileCheck** -parametern påverkar inte Server versioner av Windows operativ system, som tillåter fjärråtkomst från offentliga nätverk i samma lokala undernät som standard.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-146">The **SkipNetworkProfileCheck** parameter does not affect server versions of the Windows operating system, which allow remote access from public networks in the same local subnet by default.</span></span>

<span data-ttu-id="ee9ee-147">`Set-NetFirewallRule`Cmdleten i modulen **netsecurity** lägger till en brand Väggs regel som tillåter fjärråtkomst från offentliga nätverk från valfri fjärrplats.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-147">The `Set-NetFirewallRule` cmdlet in the **NetSecurity** module adds a firewall rule that allows remote access from public networks from any remote location.</span></span> <span data-ttu-id="ee9ee-148">Detta omfattar platser i olika undernät.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-148">This includes locations in different subnets.</span></span>

> [!NOTE]
> <span data-ttu-id="ee9ee-149">Namnet på brand Väggs regeln kan vara olika beroende på Windows-versionen.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-149">The name of the firewall rule can be different depending on the version of Windows.</span></span> <span data-ttu-id="ee9ee-150">Använd `Get-NetFirewallRule` cmdleten för att visa namnen på reglerna i systemet.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-150">Use the `Get-NetFirewallRule` cmdlet to list the names of the rules on your system.</span></span>

## <span data-ttu-id="ee9ee-151">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ee9ee-151">PARAMETERS</span></span>

### <span data-ttu-id="ee9ee-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ee9ee-152">-Confirm</span></span>

<span data-ttu-id="ee9ee-153">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ee9ee-154">-Force</span><span class="sxs-lookup"><span data-stu-id="ee9ee-154">-Force</span></span>

<span data-ttu-id="ee9ee-155">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-155">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="ee9ee-156">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="ee9ee-156">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="ee9ee-157">Anger att denna cmdlet aktiverar fjärr kommunikation på klient versioner av Windows operativ system när datorn är i ett offentligt nätverk.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-157">Indicates that this cmdlet enables remoting on client versions of the Windows operating system when the computer is on a public network.</span></span> <span data-ttu-id="ee9ee-158">Med den här parametern kan du använda en brand Väggs regel för offentliga nätverk som endast tillåter fjärråtkomst från datorer i samma lokala undernät.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-158">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="ee9ee-159">Den här parametern påverkar inte Server versioner av Windows operativ system, som som standard har en lokal brand Väggs regel för offentliga nätverk.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-159">This parameter does not affect server versions of the Windows operating system, which, by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="ee9ee-160">Om den lokala brand Väggs regeln är inaktive rad på en server version `Enable-PSRemoting` aktiverar du den igen, oavsett värdet för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-160">If the local subnet firewall rule is disabled on a server version, `Enable-PSRemoting` re-enables it, regardless of the value of this parameter.</span></span>

<span data-ttu-id="ee9ee-161">Om du vill ta bort den lokala under näts begränsningen och aktivera fjärråtkomst från alla platser i offentliga nätverk använder du `Set-NetFirewallRule` cmdleten i modulen **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="ee9ee-161">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="ee9ee-162">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-162">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="ee9ee-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ee9ee-163">-WhatIf</span></span>

<span data-ttu-id="ee9ee-164">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-164">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ee9ee-165">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-165">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ee9ee-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ee9ee-166">CommonParameters</span></span>

<span data-ttu-id="ee9ee-167">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ee9ee-168">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ee9ee-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ee9ee-169">INDATA</span><span class="sxs-lookup"><span data-stu-id="ee9ee-169">INPUTS</span></span>

### <span data-ttu-id="ee9ee-170">Inget</span><span class="sxs-lookup"><span data-stu-id="ee9ee-170">None</span></span>

<span data-ttu-id="ee9ee-171">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-171">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="ee9ee-172">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ee9ee-172">OUTPUTS</span></span>

### <span data-ttu-id="ee9ee-173">System. String</span><span class="sxs-lookup"><span data-stu-id="ee9ee-173">System.String</span></span>

<span data-ttu-id="ee9ee-174">Denna cmdlet returnerar strängar som beskriver dess resultat.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-174">This cmdlet returns strings that describe its results.</span></span>

## <span data-ttu-id="ee9ee-175">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ee9ee-175">NOTES</span></span>

<span data-ttu-id="ee9ee-176">I PowerShell 3,0 `Enable-PSRemoting` skapar följande brand Väggs undantag för WS-Management kommunikation.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-176">In PowerShell 3.0, `Enable-PSRemoting` creates the following firewall exceptions for WS-Management communications.</span></span>

<span data-ttu-id="ee9ee-177">I Server versioner av Windows-operativsystemet `Enable-PSRemoting` skapar brand Väggs regler för privata nätverk och domän nätverk som tillåter fjärråtkomst, och skapar en brand Väggs regel för offentliga nätverk som endast tillåter fjärråtkomst från datorer i samma lokala undernät.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-177">On server versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow remote access, and creates a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="ee9ee-178">I PowerShell 3,0 i klient versioner av Windows operativ system `Enable-PSRemoting` skapas brand Väggs regler för privata nätverk och domän nätverk som tillåter obegränsad fjärråtkomst.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-178">On client versions of the Windows operating system, `Enable-PSRemoting` in PowerShell 3.0 creates firewall rules for private and domain networks that allow unrestricted remote access.</span></span> <span data-ttu-id="ee9ee-179">Om du vill skapa en brand Väggs regel för offentliga nätverk som tillåter fjärråtkomst från samma lokala undernät använder du parametern **SkipNetworkProfileCheck** .</span><span class="sxs-lookup"><span data-stu-id="ee9ee-179">To create a firewall rule for public networks that allows remote access from the same local subnet, use the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="ee9ee-180">På klient-eller Server versioner av Windows-operativsystemet, för att skapa en brand Väggs regel för offentliga nätverk som tar bort begränsningen lokalt undernät och tillåter fjärråtkomst, använder du `Set-NetFirewallRule` cmdleten i modulen netsecurity för att köra följande kommando: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span><span class="sxs-lookup"><span data-stu-id="ee9ee-180">On client or server versions of the Windows operating system, to create a firewall rule for public networks that removes the local subnet restriction and allows remote access , use the `Set-NetFirewallRule` cmdlet in the NetSecurity module to run the following command: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span></span>

<span data-ttu-id="ee9ee-181">I PowerShell 2,0 `Enable-PSRemoting` skapar följande brand Väggs undantag för WS-Management kommunikation.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-181">In PowerShell 2.0, `Enable-PSRemoting` creates the following firewall exceptions for WS-Management communications.</span></span>

<span data-ttu-id="ee9ee-182">I Server versioner av Windows operativ system skapas brand Väggs regler för alla nätverk som tillåter fjärråtkomst.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-182">On server versions of the Windows operating system, it creates firewall rules for all networks that allow remote access.</span></span>

<span data-ttu-id="ee9ee-183">`Enable-PSRemoting`I PowerShell 2,0 skapar ett brand Väggs undantag endast för domän platser och privata nätverks platser på klient versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-183">On client versions of the Windows operating system, `Enable-PSRemoting` in PowerShell 2.0 creates a firewall exception only for domain and private network locations.</span></span> <span data-ttu-id="ee9ee-184">För att minimera säkerhets riskerna `Enable-PSRemoting` skapar inte en brand Väggs regel för offentliga nätverk på klient versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-184">To minimize security risks, `Enable-PSRemoting` does not create a firewall rule for public networks on client versions of Windows.</span></span> <span data-ttu-id="ee9ee-185">När den aktuella nätverks platsen är offentlig `Enable-PSRemoting` returnerar följande meddelande: det går inte att kontrol lera status för brand väggen.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-185">When the current network location is public, `Enable-PSRemoting` returns the following message: Unable to check the status of the firewall.</span></span>

<span data-ttu-id="ee9ee-186">Med början i PowerShell 3,0, `Enable-PSRemoting` aktiverar alla sessionsinställningar genom att ställa in värdet för egenskapen **Enabled** för alla sessioner `$True` .</span><span class="sxs-lookup"><span data-stu-id="ee9ee-186">Starting in PowerShell 3.0, `Enable-PSRemoting` enables all session configurations by setting the value of the **Enabled** property of all session configurations to `$True`.</span></span>

<span data-ttu-id="ee9ee-187">I PowerShell 2,0 `Enable-PSRemoting` tar bort inställningen **Deny_All** från säkerhets beskrivningen för sessionsbaserade.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-187">In PowerShell 2.0, `Enable-PSRemoting` removes the **Deny_All** setting from the security descriptor of session configurations.</span></span> <span data-ttu-id="ee9ee-188">I PowerShell 3,0 `Enable-PSRemoting` tar bort **Deny_All** och **Network_Deny_All** inställningar.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-188">In PowerShell 3.0, `Enable-PSRemoting` removes the **Deny_All** and **Network_Deny_All** settings.</span></span> <span data-ttu-id="ee9ee-189">Detta ger fjärråtkomst till sessionsbaserade konfigurationer som har reserver ATS för lokal användning.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-189">This provides remote access to session configurations that were reserved for local use.</span></span>

## <span data-ttu-id="ee9ee-190">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ee9ee-190">RELATED LINKS</span></span>

[<span data-ttu-id="ee9ee-191">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee9ee-191">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="ee9ee-192">Aktivera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee9ee-192">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="ee9ee-193">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee9ee-193">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="ee9ee-194">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee9ee-194">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="ee9ee-195">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee9ee-195">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="ee9ee-196">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="ee9ee-196">Disable-PSRemoting</span></span>](Disable-PSRemoting.md)

[<span data-ttu-id="ee9ee-197">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="ee9ee-197">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="ee9ee-198">about_Remote</span><span class="sxs-lookup"><span data-stu-id="ee9ee-198">about_Remote</span></span>](About/about_Remote.md)

[<span data-ttu-id="ee9ee-199">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="ee9ee-199">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)
