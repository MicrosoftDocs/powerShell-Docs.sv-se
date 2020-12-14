---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 10/02/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmanquickconfig?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManQuickConfig
ms.openlocfilehash: e5d50af0551a183b8e9e1995fbd722c331a48486
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708318"
---
# <span data-ttu-id="5d74b-102">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="5d74b-102">Set-WSManQuickConfig</span></span>

## <span data-ttu-id="5d74b-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5d74b-103">SYNOPSIS</span></span>
<span data-ttu-id="5d74b-104">Konfigurerar den lokala datorn för fjärrhantering.</span><span class="sxs-lookup"><span data-stu-id="5d74b-104">Configures the local computer for remote management.</span></span>

## <span data-ttu-id="5d74b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5d74b-105">SYNTAX</span></span>

### <span data-ttu-id="5d74b-106">Alla</span><span class="sxs-lookup"><span data-stu-id="5d74b-106">All</span></span>

```
Set-WSManQuickConfig [-UseSSL] [-Force] [-SkipNetworkProfileCheck] [<CommonParameters>]
```

## <span data-ttu-id="5d74b-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5d74b-107">DESCRIPTION</span></span>

<span data-ttu-id="5d74b-108">`Set-WSManQuickConfig`Cmdleten konfigurerar datorn att ta emot PowerShell-fjärrkommandon som skickas med hjälp av WS-Management-tekniken (Web Services for Management).</span><span class="sxs-lookup"><span data-stu-id="5d74b-108">The `Set-WSManQuickConfig` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the Web Services for Management (WS-Management) technology.</span></span>

<span data-ttu-id="5d74b-109">`Set-WSManQuickConfig` utför följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="5d74b-109">`Set-WSManQuickConfig` performs the following actions:</span></span>

- <span data-ttu-id="5d74b-110">Kontrollerar om WinRM-tjänsten körs.</span><span class="sxs-lookup"><span data-stu-id="5d74b-110">Checks whether the WinRM service is running.</span></span> <span data-ttu-id="5d74b-111">Om WinRM-tjänsten inte körs startas tjänsten.</span><span class="sxs-lookup"><span data-stu-id="5d74b-111">If the WinRM service isn't running, the service is started.</span></span>
- <span data-ttu-id="5d74b-112">Anger start typen för WinRM-tjänsten till automatisk.</span><span class="sxs-lookup"><span data-stu-id="5d74b-112">Sets the WinRM service startup type to automatic.</span></span>
- <span data-ttu-id="5d74b-113">Skapar en lyssnare som accepterar begär Anden på alla IP-adresser.</span><span class="sxs-lookup"><span data-stu-id="5d74b-113">Creates a listener to accept requests on any IP address.</span></span> <span data-ttu-id="5d74b-114">Standard transporten är **http**.</span><span class="sxs-lookup"><span data-stu-id="5d74b-114">The default transport is **HTTP**.</span></span>
- <span data-ttu-id="5d74b-115">Aktiverar ett brand Väggs undantag för WinRM-trafik.</span><span class="sxs-lookup"><span data-stu-id="5d74b-115">Enables a firewall exception for WinRM traffic.</span></span>

<span data-ttu-id="5d74b-116">`Set-WSManQuickConfig`Starta PowerShell med alternativet **Kör som administratör** för att köra.</span><span class="sxs-lookup"><span data-stu-id="5d74b-116">To run `Set-WSManQuickConfig`, start PowerShell with the **Run as Administrator** option.</span></span>

## <span data-ttu-id="5d74b-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5d74b-117">EXAMPLES</span></span>

### <span data-ttu-id="5d74b-118">Exempel 1: aktivera fjärrhantering av den lokala datorn via HTTP</span><span class="sxs-lookup"><span data-stu-id="5d74b-118">Example 1: Enable remote management of the local computer over HTTP</span></span>

<span data-ttu-id="5d74b-119">I det här exemplet anges konfigurationen som krävs för att aktivera fjärrhantering av den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="5d74b-119">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="5d74b-120">Som standard skapar det här kommandot en WS-Management lyssnare på **http**.</span><span class="sxs-lookup"><span data-stu-id="5d74b-120">By default, this command creates a WS-Management listener on **HTTP**.</span></span>

```powershell
Set-WSManQuickConfig
```

### <span data-ttu-id="5d74b-121">Exempel 2: aktivera fjärrhantering av den lokala datorn via HTTPS</span><span class="sxs-lookup"><span data-stu-id="5d74b-121">Example 2: Enable remote management of the local computer over HTTPS</span></span>

<span data-ttu-id="5d74b-122">I det här exemplet anges konfigurationen som krävs för att aktivera fjärrhantering av den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="5d74b-122">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="5d74b-123">Parametern **UseSSL** anger att **https** används för att kommunicera med datorn.</span><span class="sxs-lookup"><span data-stu-id="5d74b-123">The **UseSSL** parameter specifies that **HTTPS** is used to communicate with the computer.</span></span>

```powershell
Set-WSManQuickConfig -UseSSL
```

> [!NOTE]
> <span data-ttu-id="5d74b-124">**Https** kräver manuell konfiguration.</span><span class="sxs-lookup"><span data-stu-id="5d74b-124">**HTTPS** requires manual configuration.</span></span> <span data-ttu-id="5d74b-125">Mer information finns i Beskrivning av **UseSSL** -parametern.</span><span class="sxs-lookup"><span data-stu-id="5d74b-125">For more information, see the **UseSSL** parameter's description.</span></span>

## <span data-ttu-id="5d74b-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5d74b-126">PARAMETERS</span></span>

### <span data-ttu-id="5d74b-127">-Force</span><span class="sxs-lookup"><span data-stu-id="5d74b-127">-Force</span></span>

<span data-ttu-id="5d74b-128">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="5d74b-128">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="5d74b-129">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="5d74b-129">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="5d74b-130">Konfigurerar Windows-klientversioner för fjärr kommunikation när datorn finns i ett offentligt nätverk.</span><span class="sxs-lookup"><span data-stu-id="5d74b-130">Configures Windows client versions for remoting when the computer is on a public network.</span></span> <span data-ttu-id="5d74b-131">Med den här parametern kan du använda en brand Väggs regel för offentliga nätverk som endast tillåter fjärråtkomst från datorer i samma lokala undernät.</span><span class="sxs-lookup"><span data-stu-id="5d74b-131">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="5d74b-132">Den här parametern har ingen påverkan på Server versioner av Windows, som standard har en brand Väggs regel för lokalt undernät för offentliga nätverk.</span><span class="sxs-lookup"><span data-stu-id="5d74b-132">This parameter has no effect on server versions of Windows, that by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="5d74b-133">Om den lokala brand Väggs regeln är inaktive rad på Server versionen av Windows återaktiverar `Enable-PSRemoting` den, oavsett den här parameterns värde.</span><span class="sxs-lookup"><span data-stu-id="5d74b-133">If the local subnet firewall rule is disabled on the server version of Windows, `Enable-PSRemoting` re-enables it, regardless of this parameter's value.</span></span>

<span data-ttu-id="5d74b-134">Om du vill ta bort den lokala under näts begränsningen och aktivera fjärråtkomst från alla platser i offentliga nätverk använder du `Set-NetFirewallRule` cmdleten i modulen **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="5d74b-134">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="5d74b-135">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5d74b-135">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="5d74b-136">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="5d74b-136">-UseSSL</span></span>

<span data-ttu-id="5d74b-137">Anger att Secure Sockets Layer-protokollet (SSL) används för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="5d74b-137">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span> <span data-ttu-id="5d74b-138">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="5d74b-138">By default, SSL isn't used.</span></span>

<span data-ttu-id="5d74b-139">WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="5d74b-139">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="5d74b-140">Med parametern **UseSSL** kan du ange ytterligare skydd av https i stället för http.</span><span class="sxs-lookup"><span data-stu-id="5d74b-140">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="5d74b-141">Om du använder den här parametern och SSL inte är tillgängligt på porten som används för anslutningen, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="5d74b-141">If you use this parameter and SSL isn't available on the port that's used for the connection, the command fails.</span></span>

<span data-ttu-id="5d74b-142">**Https** kräver manuell konfiguration av WinRM-och brand Väggs regler.</span><span class="sxs-lookup"><span data-stu-id="5d74b-142">**HTTPS** requires manual configuration of WinRM and firewall rules.</span></span> <span data-ttu-id="5d74b-143">Mer information finns i [så här gör du för att: Konfigurera WINRM för https](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https).</span><span class="sxs-lookup"><span data-stu-id="5d74b-143">For more information, see [How To: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https).</span></span>

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

### <span data-ttu-id="5d74b-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5d74b-144">CommonParameters</span></span>

<span data-ttu-id="5d74b-145">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5d74b-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5d74b-146">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5d74b-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5d74b-147">INDATA</span><span class="sxs-lookup"><span data-stu-id="5d74b-147">INPUTS</span></span>

### <span data-ttu-id="5d74b-148">Inga</span><span class="sxs-lookup"><span data-stu-id="5d74b-148">None</span></span>

<span data-ttu-id="5d74b-149">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="5d74b-149">This cmdlet doesn't accept any input.</span></span>

## <span data-ttu-id="5d74b-150">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5d74b-150">OUTPUTS</span></span>

### <span data-ttu-id="5d74b-151">Inga</span><span class="sxs-lookup"><span data-stu-id="5d74b-151">None</span></span>

<span data-ttu-id="5d74b-152">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="5d74b-152">This cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="5d74b-153">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5d74b-153">NOTES</span></span>

## <span data-ttu-id="5d74b-154">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5d74b-154">RELATED LINKS</span></span>

[<span data-ttu-id="5d74b-155">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="5d74b-155">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="5d74b-156">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="5d74b-156">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="5d74b-157">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="5d74b-157">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="5d74b-158">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="5d74b-158">Enable-PSRemoting</span></span>](../Microsoft.PowerShell.Core/Enable-PSRemoting.md)

[<span data-ttu-id="5d74b-159">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="5d74b-159">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="5d74b-160">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="5d74b-160">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="5d74b-161">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="5d74b-161">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="5d74b-162">Gör så här: Konfigurera WINRM för HTTPS</span><span class="sxs-lookup"><span data-stu-id="5d74b-162">How To: Configure WINRM for HTTPS</span></span>](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)

[<span data-ttu-id="5d74b-163">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="5d74b-163">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="5d74b-164">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="5d74b-164">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="5d74b-165">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="5d74b-165">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="5d74b-166">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="5d74b-166">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="5d74b-167">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="5d74b-167">Test-WSMan</span></span>](Test-WSMan.md)

