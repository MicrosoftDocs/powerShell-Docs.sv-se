---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 10/02/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmanquickconfig?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManQuickConfig
ms.openlocfilehash: 5b22eb9334510267d9c4e3757b39810cfdba1fd3
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273086"
---
# <span data-ttu-id="6a915-103">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="6a915-103">Set-WSManQuickConfig</span></span>

## <span data-ttu-id="6a915-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6a915-104">SYNOPSIS</span></span>
<span data-ttu-id="6a915-105">Konfigurerar den lokala datorn för fjärrhantering.</span><span class="sxs-lookup"><span data-stu-id="6a915-105">Configures the local computer for remote management.</span></span>

## <span data-ttu-id="6a915-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6a915-106">SYNTAX</span></span>

### <span data-ttu-id="6a915-107">Alla</span><span class="sxs-lookup"><span data-stu-id="6a915-107">All</span></span>

```
Set-WSManQuickConfig [-UseSSL] [-Force] [-SkipNetworkProfileCheck] [<CommonParameters>]
```

## <span data-ttu-id="6a915-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6a915-108">DESCRIPTION</span></span>

<span data-ttu-id="6a915-109">`Set-WSManQuickConfig`Cmdleten konfigurerar datorn att ta emot PowerShell-fjärrkommandon som skickas med hjälp av WS-Management-tekniken (Web Services for Management).</span><span class="sxs-lookup"><span data-stu-id="6a915-109">The `Set-WSManQuickConfig` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the Web Services for Management (WS-Management) technology.</span></span>

<span data-ttu-id="6a915-110">`Set-WSManQuickConfig` utför följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="6a915-110">`Set-WSManQuickConfig` performs the following actions:</span></span>

- <span data-ttu-id="6a915-111">Kontrollerar om WinRM-tjänsten körs.</span><span class="sxs-lookup"><span data-stu-id="6a915-111">Checks whether the WinRM service is running.</span></span> <span data-ttu-id="6a915-112">Om WinRM-tjänsten inte körs startas tjänsten.</span><span class="sxs-lookup"><span data-stu-id="6a915-112">If the WinRM service isn't running, the service is started.</span></span>
- <span data-ttu-id="6a915-113">Anger start typen för WinRM-tjänsten till automatisk.</span><span class="sxs-lookup"><span data-stu-id="6a915-113">Sets the WinRM service startup type to automatic.</span></span>
- <span data-ttu-id="6a915-114">Skapar en lyssnare som accepterar begär Anden på alla IP-adresser.</span><span class="sxs-lookup"><span data-stu-id="6a915-114">Creates a listener to accept requests on any IP address.</span></span> <span data-ttu-id="6a915-115">Standard transporten är **http**.</span><span class="sxs-lookup"><span data-stu-id="6a915-115">The default transport is **HTTP**.</span></span>
- <span data-ttu-id="6a915-116">Aktiverar ett brand Väggs undantag för WinRM-trafik.</span><span class="sxs-lookup"><span data-stu-id="6a915-116">Enables a firewall exception for WinRM traffic.</span></span>

<span data-ttu-id="6a915-117">`Set-WSManQuickConfig`Starta PowerShell med alternativet **Kör som administratör** för att köra.</span><span class="sxs-lookup"><span data-stu-id="6a915-117">To run `Set-WSManQuickConfig`, start PowerShell with the **Run as Administrator** option.</span></span>

## <span data-ttu-id="6a915-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6a915-118">EXAMPLES</span></span>

### <span data-ttu-id="6a915-119">Exempel 1: aktivera fjärrhantering av den lokala datorn via HTTP</span><span class="sxs-lookup"><span data-stu-id="6a915-119">Example 1: Enable remote management of the local computer over HTTP</span></span>

<span data-ttu-id="6a915-120">I det här exemplet anges konfigurationen som krävs för att aktivera fjärrhantering av den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6a915-120">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="6a915-121">Som standard skapar det här kommandot en WS-Management lyssnare på **http**.</span><span class="sxs-lookup"><span data-stu-id="6a915-121">By default, this command creates a WS-Management listener on **HTTP**.</span></span>

```powershell
Set-WSManQuickConfig
```

### <span data-ttu-id="6a915-122">Exempel 2: aktivera fjärrhantering av den lokala datorn via HTTPS</span><span class="sxs-lookup"><span data-stu-id="6a915-122">Example 2: Enable remote management of the local computer over HTTPS</span></span>

<span data-ttu-id="6a915-123">I det här exemplet anges konfigurationen som krävs för att aktivera fjärrhantering av den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6a915-123">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="6a915-124">Parametern **UseSSL** anger att **https** används för att kommunicera med datorn.</span><span class="sxs-lookup"><span data-stu-id="6a915-124">The **UseSSL** parameter specifies that **HTTPS** is used to communicate with the computer.</span></span>

```powershell
Set-WSManQuickConfig -UseSSL
```

> [!NOTE]
> <span data-ttu-id="6a915-125">**Https** kräver manuell konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6a915-125">**HTTPS** requires manual configuration.</span></span> <span data-ttu-id="6a915-126">Mer information finns i Beskrivning av **UseSSL** -parametern.</span><span class="sxs-lookup"><span data-stu-id="6a915-126">For more information, see the **UseSSL** parameter's description.</span></span>

## <span data-ttu-id="6a915-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6a915-127">PARAMETERS</span></span>

### <span data-ttu-id="6a915-128">-Force</span><span class="sxs-lookup"><span data-stu-id="6a915-128">-Force</span></span>

<span data-ttu-id="6a915-129">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="6a915-129">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="6a915-130">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="6a915-130">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="6a915-131">Konfigurerar Windows-klientversioner för fjärr kommunikation när datorn finns i ett offentligt nätverk.</span><span class="sxs-lookup"><span data-stu-id="6a915-131">Configures Windows client versions for remoting when the computer is on a public network.</span></span> <span data-ttu-id="6a915-132">Med den här parametern kan du använda en brand Väggs regel för offentliga nätverk som endast tillåter fjärråtkomst från datorer i samma lokala undernät.</span><span class="sxs-lookup"><span data-stu-id="6a915-132">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="6a915-133">Den här parametern har ingen påverkan på Server versioner av Windows, som standard har en brand Väggs regel för lokalt undernät för offentliga nätverk.</span><span class="sxs-lookup"><span data-stu-id="6a915-133">This parameter has no effect on server versions of Windows, that by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="6a915-134">Om den lokala brand Väggs regeln är inaktive rad på Server versionen av Windows återaktiverar `Enable-PSRemoting` den, oavsett den här parameterns värde.</span><span class="sxs-lookup"><span data-stu-id="6a915-134">If the local subnet firewall rule is disabled on the server version of Windows, `Enable-PSRemoting` re-enables it, regardless of this parameter's value.</span></span>

<span data-ttu-id="6a915-135">Om du vill ta bort den lokala under näts begränsningen och aktivera fjärråtkomst från alla platser i offentliga nätverk använder du `Set-NetFirewallRule` cmdleten i modulen **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="6a915-135">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="6a915-136">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6a915-136">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="6a915-137">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="6a915-137">-UseSSL</span></span>

<span data-ttu-id="6a915-138">Anger att Secure Sockets Layer-protokollet (SSL) används för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="6a915-138">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span> <span data-ttu-id="6a915-139">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="6a915-139">By default, SSL isn't used.</span></span>

<span data-ttu-id="6a915-140">WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="6a915-140">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="6a915-141">Med parametern **UseSSL** kan du ange ytterligare skydd av https i stället för http.</span><span class="sxs-lookup"><span data-stu-id="6a915-141">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="6a915-142">Om du använder den här parametern och SSL inte är tillgängligt på porten som används för anslutningen, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="6a915-142">If you use this parameter and SSL isn't available on the port that's used for the connection, the command fails.</span></span>

<span data-ttu-id="6a915-143">**Https** kräver manuell konfiguration av WinRM-och brand Väggs regler.</span><span class="sxs-lookup"><span data-stu-id="6a915-143">**HTTPS** requires manual configuration of WinRM and firewall rules.</span></span> <span data-ttu-id="6a915-144">Mer information finns i [så här gör du för att: Konfigurera WINRM för https](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https).</span><span class="sxs-lookup"><span data-stu-id="6a915-144">For more information, see [How To: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https).</span></span>

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

### <span data-ttu-id="6a915-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6a915-145">CommonParameters</span></span>

<span data-ttu-id="6a915-146">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6a915-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6a915-147">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6a915-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6a915-148">INDATA</span><span class="sxs-lookup"><span data-stu-id="6a915-148">INPUTS</span></span>

### <span data-ttu-id="6a915-149">Inget</span><span class="sxs-lookup"><span data-stu-id="6a915-149">None</span></span>

<span data-ttu-id="6a915-150">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="6a915-150">This cmdlet doesn't accept any input.</span></span>

## <span data-ttu-id="6a915-151">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6a915-151">OUTPUTS</span></span>

### <span data-ttu-id="6a915-152">Inget</span><span class="sxs-lookup"><span data-stu-id="6a915-152">None</span></span>

<span data-ttu-id="6a915-153">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="6a915-153">This cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="6a915-154">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6a915-154">NOTES</span></span>

## <span data-ttu-id="6a915-155">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6a915-155">RELATED LINKS</span></span>

[<span data-ttu-id="6a915-156">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="6a915-156">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="6a915-157">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="6a915-157">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="6a915-158">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="6a915-158">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="6a915-159">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="6a915-159">Enable-PSRemoting</span></span>](../Microsoft.PowerShell.Core/Enable-PSRemoting.md)

[<span data-ttu-id="6a915-160">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="6a915-160">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="6a915-161">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="6a915-161">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="6a915-162">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="6a915-162">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="6a915-163">Gör så här: Konfigurera WINRM för HTTPS</span><span class="sxs-lookup"><span data-stu-id="6a915-163">How To: Configure WINRM for HTTPS</span></span>](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)

[<span data-ttu-id="6a915-164">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="6a915-164">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="6a915-165">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="6a915-165">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="6a915-166">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="6a915-166">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="6a915-167">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="6a915-167">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="6a915-168">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="6a915-168">Test-WSMan</span></span>](Test-WSMan.md)
