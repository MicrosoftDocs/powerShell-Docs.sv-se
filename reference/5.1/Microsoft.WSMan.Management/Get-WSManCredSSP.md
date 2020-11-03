---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmancredssp?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManCredSSP
ms.openlocfilehash: ce2046a9df5d4d02d718d6408c7a196a753c9914
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273152"
---
# <span data-ttu-id="b7a49-103">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b7a49-103">Get-WSManCredSSP</span></span>

## <span data-ttu-id="b7a49-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b7a49-104">SYNOPSIS</span></span>
<span data-ttu-id="b7a49-105">Hämtar den-relaterade konfigurationen för Credential Security Support providern för klienten.</span><span class="sxs-lookup"><span data-stu-id="b7a49-105">Gets the Credential Security Support Provider-related configuration for the client.</span></span>

## <span data-ttu-id="b7a49-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b7a49-106">SYNTAX</span></span>

```
Get-WSManCredSSP [<CommonParameters>]
```

## <span data-ttu-id="b7a49-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b7a49-107">DESCRIPTION</span></span>
<span data-ttu-id="b7a49-108">**Get-WSManCredSSP** -cmdlet: en hämtar providerns säkerhets support för Credential-relaterad konfiguration av klienten och servern.</span><span class="sxs-lookup"><span data-stu-id="b7a49-108">The **Get-WSManCredSSP** cmdlet gets the Credential Security Support Provider-related configuration of the client and the server.</span></span>
<span data-ttu-id="b7a49-109">Utdata visar om CredSSP-autentisering (Credential Security Support Provider) är aktive rad eller inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="b7a49-109">The output indicates whether Credential Security Support Provider (CredSSP) authentication is enabled or disabled.</span></span>
<span data-ttu-id="b7a49-110">Denna cmdlet visar också konfigurations information för **AllowFreshCredentials** -principen för CredSSP.</span><span class="sxs-lookup"><span data-stu-id="b7a49-110">This cmdlet also displays configuration information for the **AllowFreshCredentials** policy of CredSSP.</span></span>

<span data-ttu-id="b7a49-111">När du använder CredSSP-autentisering skickas användarautentiseringsuppgifter till en fjärrdator som ska autentiseras.</span><span class="sxs-lookup"><span data-stu-id="b7a49-111">When you use CredSSP authentication, the user credentials are passed to a remote computer to be authenticated.</span></span>
<span data-ttu-id="b7a49-112">Den här typen av autentisering är utformad för kommandon som skapar en fjärrsession från en annan fjärran sluten session.</span><span class="sxs-lookup"><span data-stu-id="b7a49-112">This type of authentication is designed for commands that create a remote session from another remote session.</span></span>
<span data-ttu-id="b7a49-113">Om du till exempel vill köra ett bakgrunds jobb på en fjärrdator använder du den här typen av autentisering.</span><span class="sxs-lookup"><span data-stu-id="b7a49-113">For example, if you want to run a background job on a remote computer, use this kind of authentication.</span></span>

<span data-ttu-id="b7a49-114">Cmdlet: en utför följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="b7a49-114">The cmdlet performs the following actions:</span></span>

- <span data-ttu-id="b7a49-115">Hämtar inställningen för WS-Management CredSSP på klienten ( **\<localhost|computername\> \Client\Auth\CredSSP** ).</span><span class="sxs-lookup"><span data-stu-id="b7a49-115">Gets the WS-Management CredSSP setting on the client ( **\<localhost|computername\>\Client\Auth\CredSSP** ).</span></span>
- <span data-ttu-id="b7a49-116">Hämtar princip inställningen för Windows CredSSP **AllowFreshCredentials**.</span><span class="sxs-lookup"><span data-stu-id="b7a49-116">Gets the Windows CredSSP policy setting **AllowFreshCredentials**.</span></span>
- <span data-ttu-id="b7a49-117">Hämtar inställningen för WS-Management CredSSP på servern ( **\<localhost|computername\> \Service\Auth\CredSSP** ).</span><span class="sxs-lookup"><span data-stu-id="b7a49-117">Gets the WS-Management CredSSP setting on the server ( **\<localhost|computername\>\Service\Auth\CredSSP** ).</span></span>

<span data-ttu-id="b7a49-118">Varning! CredSSP-autentisering delegerar användarautentiseringsuppgifter från den lokala datorn till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="b7a49-118">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="b7a49-119">Den här metoden ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="b7a49-119">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="b7a49-120">Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="b7a49-120">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="b7a49-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b7a49-121">EXAMPLES</span></span>

### <span data-ttu-id="b7a49-122">Exempel 1: Visa CredSSP-konfiguration</span><span class="sxs-lookup"><span data-stu-id="b7a49-122">Example 1: Display CredSSP configuration</span></span>

```
PS C:\> Get-WSManCredSSP
```

<span data-ttu-id="b7a49-123">Det här kommandot visar information om CredSSP-konfigurationen för både klienten och servern.</span><span class="sxs-lookup"><span data-stu-id="b7a49-123">This command displays CredSSP configuration information for both the client and server.</span></span>

<span data-ttu-id="b7a49-124">Utdata identifierar att datorn är eller inte har kon figurer ATS för CredSSP.</span><span class="sxs-lookup"><span data-stu-id="b7a49-124">The output identifies that this computer is or is not configured for CredSSP.</span></span>

<span data-ttu-id="b7a49-125">Om datorn är konfigurerad för CredSSP är detta utdata:</span><span class="sxs-lookup"><span data-stu-id="b7a49-125">If the computer is configured for CredSSP, this is the output:</span></span>

`The machine is configured to allow delegating fresh credentials to the following target(s): wsman/server02.accounting.fabrikam.com`

<span data-ttu-id="b7a49-126">Om datorn inte är konfigurerad för CredSSP är detta utdata:</span><span class="sxs-lookup"><span data-stu-id="b7a49-126">If the computer is not configured for CredSSP, this is the output:</span></span>

`The machine is not configured to allow delegating fresh credentials.`

## <span data-ttu-id="b7a49-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b7a49-127">PARAMETERS</span></span>

### <span data-ttu-id="b7a49-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b7a49-128">CommonParameters</span></span>
<span data-ttu-id="b7a49-129">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b7a49-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b7a49-130">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b7a49-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b7a49-131">INDATA</span><span class="sxs-lookup"><span data-stu-id="b7a49-131">INPUTS</span></span>

### <span data-ttu-id="b7a49-132">Inget</span><span class="sxs-lookup"><span data-stu-id="b7a49-132">None</span></span>
<span data-ttu-id="b7a49-133">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="b7a49-133">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="b7a49-134">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b7a49-134">OUTPUTS</span></span>

### <span data-ttu-id="b7a49-135">Inget</span><span class="sxs-lookup"><span data-stu-id="b7a49-135">None</span></span>
<span data-ttu-id="b7a49-136">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b7a49-136">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b7a49-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b7a49-137">NOTES</span></span>

* <span data-ttu-id="b7a49-138">Använd Disable-WSManCredSSP-cmdleten om du vill inaktivera CredSSP-autentisering.</span><span class="sxs-lookup"><span data-stu-id="b7a49-138">To disable CredSSP authentication, use the Disable-WSManCredSSP cmdlet.</span></span> <span data-ttu-id="b7a49-139">Använd Enable-WSManCredSSP-cmdleten om du vill aktivera CredSSP-autentisering.</span><span class="sxs-lookup"><span data-stu-id="b7a49-139">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

## <span data-ttu-id="b7a49-140">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b7a49-140">RELATED LINKS</span></span>

[<span data-ttu-id="b7a49-141">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="b7a49-141">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="b7a49-142">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b7a49-142">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="b7a49-143">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="b7a49-143">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="b7a49-144">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b7a49-144">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="b7a49-145">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b7a49-145">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="b7a49-146">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="b7a49-146">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="b7a49-147">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b7a49-147">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="b7a49-148">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="b7a49-148">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="b7a49-149">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b7a49-149">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="b7a49-150">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b7a49-150">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="b7a49-151">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="b7a49-151">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="b7a49-152">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="b7a49-152">Test-WSMan</span></span>](Test-WSMan.md)
