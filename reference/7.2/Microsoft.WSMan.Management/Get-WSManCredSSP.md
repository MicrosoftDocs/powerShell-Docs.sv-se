---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmancredssp?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManCredSSP
ms.openlocfilehash: 9830d1feb31e9cca735a7ac8d2ed9d2ec50380b5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708327"
---
# <span data-ttu-id="d2d32-102">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="d2d32-102">Get-WSManCredSSP</span></span>

## <span data-ttu-id="d2d32-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="d2d32-103">SYNOPSIS</span></span>
<span data-ttu-id="d2d32-104">Hämtar den-relaterade konfigurationen för Credential Security Support providern för klienten.</span><span class="sxs-lookup"><span data-stu-id="d2d32-104">Gets the Credential Security Support Provider-related configuration for the client.</span></span>

## <span data-ttu-id="d2d32-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d2d32-105">SYNTAX</span></span>

```
Get-WSManCredSSP [<CommonParameters>]
```

## <span data-ttu-id="d2d32-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d2d32-106">DESCRIPTION</span></span>
<span data-ttu-id="d2d32-107">**Get-WSManCredSSP** -cmdlet: en hämtar providerns säkerhets support för Credential-relaterad konfiguration av klienten och servern.</span><span class="sxs-lookup"><span data-stu-id="d2d32-107">The **Get-WSManCredSSP** cmdlet gets the Credential Security Support Provider-related configuration of the client and the server.</span></span>
<span data-ttu-id="d2d32-108">Utdata visar om CredSSP-autentisering (Credential Security Support Provider) är aktive rad eller inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="d2d32-108">The output indicates whether Credential Security Support Provider (CredSSP) authentication is enabled or disabled.</span></span>
<span data-ttu-id="d2d32-109">Denna cmdlet visar också konfigurations information för **AllowFreshCredentials** -principen för CredSSP.</span><span class="sxs-lookup"><span data-stu-id="d2d32-109">This cmdlet also displays configuration information for the **AllowFreshCredentials** policy of CredSSP.</span></span>

<span data-ttu-id="d2d32-110">När du använder CredSSP-autentisering skickas användarautentiseringsuppgifter till en fjärrdator som ska autentiseras.</span><span class="sxs-lookup"><span data-stu-id="d2d32-110">When you use CredSSP authentication, the user credentials are passed to a remote computer to be authenticated.</span></span>
<span data-ttu-id="d2d32-111">Den här typen av autentisering är utformad för kommandon som skapar en fjärrsession från en annan fjärran sluten session.</span><span class="sxs-lookup"><span data-stu-id="d2d32-111">This type of authentication is designed for commands that create a remote session from another remote session.</span></span>
<span data-ttu-id="d2d32-112">Om du till exempel vill köra ett bakgrunds jobb på en fjärrdator använder du den här typen av autentisering.</span><span class="sxs-lookup"><span data-stu-id="d2d32-112">For example, if you want to run a background job on a remote computer, use this kind of authentication.</span></span>

<span data-ttu-id="d2d32-113">Cmdlet: en utför följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="d2d32-113">The cmdlet performs the following actions:</span></span>

- <span data-ttu-id="d2d32-114">Hämtar inställningen för WS-Management CredSSP på klienten (**\<localhost|computername\> \Client\Auth\CredSSP**).</span><span class="sxs-lookup"><span data-stu-id="d2d32-114">Gets the WS-Management CredSSP setting on the client (**\<localhost|computername\>\Client\Auth\CredSSP**).</span></span>
- <span data-ttu-id="d2d32-115">Hämtar princip inställningen för Windows CredSSP **AllowFreshCredentials**.</span><span class="sxs-lookup"><span data-stu-id="d2d32-115">Gets the Windows CredSSP policy setting **AllowFreshCredentials**.</span></span>
- <span data-ttu-id="d2d32-116">Hämtar inställningen för WS-Management CredSSP på servern (**\<localhost|computername\> \Service\Auth\CredSSP**).</span><span class="sxs-lookup"><span data-stu-id="d2d32-116">Gets the WS-Management CredSSP setting on the server (**\<localhost|computername\>\Service\Auth\CredSSP**).</span></span>

<span data-ttu-id="d2d32-117">Varning! CredSSP-autentisering delegerar användarautentiseringsuppgifter från den lokala datorn till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="d2d32-117">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="d2d32-118">Den här metoden ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="d2d32-118">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="d2d32-119">Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="d2d32-119">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="d2d32-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="d2d32-120">EXAMPLES</span></span>

### <span data-ttu-id="d2d32-121">Exempel 1: Visa CredSSP-konfiguration</span><span class="sxs-lookup"><span data-stu-id="d2d32-121">Example 1: Display CredSSP configuration</span></span>

```
PS C:\> Get-WSManCredSSP
```

<span data-ttu-id="d2d32-122">Det här kommandot visar information om CredSSP-konfigurationen för både klienten och servern.</span><span class="sxs-lookup"><span data-stu-id="d2d32-122">This command displays CredSSP configuration information for both the client and server.</span></span>

<span data-ttu-id="d2d32-123">Utdata identifierar att datorn är eller inte har kon figurer ATS för CredSSP.</span><span class="sxs-lookup"><span data-stu-id="d2d32-123">The output identifies that this computer is or is not configured for CredSSP.</span></span>

<span data-ttu-id="d2d32-124">Om datorn är konfigurerad för CredSSP är detta utdata:</span><span class="sxs-lookup"><span data-stu-id="d2d32-124">If the computer is configured for CredSSP, this is the output:</span></span>

`The machine is configured to allow delegating fresh credentials to the following target(s): wsman/server02.accounting.fabrikam.com`

<span data-ttu-id="d2d32-125">Om datorn inte är konfigurerad för CredSSP är detta utdata:</span><span class="sxs-lookup"><span data-stu-id="d2d32-125">If the computer is not configured for CredSSP, this is the output:</span></span>

`The machine is not configured to allow delegating fresh credentials.`

## <span data-ttu-id="d2d32-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="d2d32-126">PARAMETERS</span></span>

### <span data-ttu-id="d2d32-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d2d32-127">CommonParameters</span></span>
<span data-ttu-id="d2d32-128">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d2d32-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d2d32-129">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d2d32-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d2d32-130">INDATA</span><span class="sxs-lookup"><span data-stu-id="d2d32-130">INPUTS</span></span>

### <span data-ttu-id="d2d32-131">Inga</span><span class="sxs-lookup"><span data-stu-id="d2d32-131">None</span></span>
<span data-ttu-id="d2d32-132">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="d2d32-132">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="d2d32-133">UTDATA</span><span class="sxs-lookup"><span data-stu-id="d2d32-133">OUTPUTS</span></span>

### <span data-ttu-id="d2d32-134">Inga</span><span class="sxs-lookup"><span data-stu-id="d2d32-134">None</span></span>
<span data-ttu-id="d2d32-135">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="d2d32-135">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d2d32-136">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="d2d32-136">NOTES</span></span>

* <span data-ttu-id="d2d32-137">Använd Disable-WSManCredSSP-cmdleten om du vill inaktivera CredSSP-autentisering.</span><span class="sxs-lookup"><span data-stu-id="d2d32-137">To disable CredSSP authentication, use the Disable-WSManCredSSP cmdlet.</span></span> <span data-ttu-id="d2d32-138">Använd Enable-WSManCredSSP-cmdleten om du vill aktivera CredSSP-autentisering.</span><span class="sxs-lookup"><span data-stu-id="d2d32-138">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

## <span data-ttu-id="d2d32-139">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="d2d32-139">RELATED LINKS</span></span>

[<span data-ttu-id="d2d32-140">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="d2d32-140">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="d2d32-141">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="d2d32-141">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="d2d32-142">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="d2d32-142">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="d2d32-143">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="d2d32-143">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="d2d32-144">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="d2d32-144">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="d2d32-145">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="d2d32-145">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="d2d32-146">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="d2d32-146">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="d2d32-147">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="d2d32-147">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="d2d32-148">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="d2d32-148">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="d2d32-149">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="d2d32-149">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="d2d32-150">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="d2d32-150">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="d2d32-151">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="d2d32-151">Test-WSMan</span></span>](Test-WSMan.md)

