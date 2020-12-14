---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disable-wsmancredssp?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManCredSSP
ms.openlocfilehash: 3260c88d57e98c0072af8621600a02901c561acb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710326"
---
# <span data-ttu-id="6b1b9-102">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="6b1b9-102">Disable-WSManCredSSP</span></span>

## <span data-ttu-id="6b1b9-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6b1b9-103">SYNOPSIS</span></span>
<span data-ttu-id="6b1b9-104">Inaktiverar CredSSP-autentisering på en dator.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-104">Disables CredSSP authentication on a computer.</span></span>

## <span data-ttu-id="6b1b9-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6b1b9-105">SYNTAX</span></span>

```
Disable-WSManCredSSP [-Role] <String> [<CommonParameters>]
```

## <span data-ttu-id="6b1b9-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6b1b9-106">DESCRIPTION</span></span>
<span data-ttu-id="6b1b9-107">Cmdlet **: en Disable-WSManCredSSP** inaktiverar CredSSP-autentisering (Credential Security Support Provider) på en klient eller på en serverdator.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-107">The **Disable-WSManCredSSP** cmdlet disables Credential Security Support Provider (CredSSP) authentication on a client or on a server computer.</span></span>
<span data-ttu-id="6b1b9-108">När CredSSP-autentisering används skickas användarautentiseringsuppgifter till en fjärrdator som ska autentiseras.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-108">When CredSSP authentication is used, the user credentials are passed to a remote computer to be authenticated.</span></span>

<span data-ttu-id="6b1b9-109">Använd denna cmdlet för att inaktivera CredSSP på klienten genom att ange klienten i *roll* parametern.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-109">Use this cmdlet to disable CredSSP on the client by specifying Client in the *Role* parameter.</span></span>
<span data-ttu-id="6b1b9-110">Denna cmdlet utför följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="6b1b9-110">This cmdlet performs the following actions:</span></span>

- <span data-ttu-id="6b1b9-111">Inaktiverar CredSSP på klienten.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-111">Disables CredSSP on the client.</span></span> <span data-ttu-id="6b1b9-112">Denna cmdlet anger WS-Management inställningen **\<localhost|computername\> \Client\Auth\CredSSP** till false.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-112">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="6b1b9-113">Tar bort alla WSMan/\*-inställningar från Windows CredSSP-principen **AllowFreshCredentials** på klienten.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-113">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="6b1b9-114">Använd denna cmdlet för att inaktivera CredSSP på servern genom att ange server i *roll*.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-114">Use this cmdlet to disable CredSSP on the server by specifying Server in *Role*.</span></span>
<span data-ttu-id="6b1b9-115">Denna cmdlet utför följande åtgärd:</span><span class="sxs-lookup"><span data-stu-id="6b1b9-115">This cmdlet performs the following action:</span></span>

- <span data-ttu-id="6b1b9-116">Inaktiverar CredSSP på servern.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-116">Disables CredSSP on the server.</span></span> <span data-ttu-id="6b1b9-117">Denna cmdlet anger WS-Management inställningen **\<localhost|computername\> \Service\Auth\CredSSP** till false.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-117">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

<span data-ttu-id="6b1b9-118">Varning! CredSSP-autentisering delegerar användarautentiseringsuppgifter från den lokala datorn till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-118">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="6b1b9-119">Den här metoden ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-119">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="6b1b9-120">Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-120">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="6b1b9-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6b1b9-121">EXAMPLES</span></span>

### <span data-ttu-id="6b1b9-122">Exempel 1: inaktivera CredSSP på en klient</span><span class="sxs-lookup"><span data-stu-id="6b1b9-122">Example 1: Disable CredSSP on a client</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Client
```

<span data-ttu-id="6b1b9-123">Det här kommandot inaktiverar CredSSP på klienten, vilket förhindrar delegering till servrar.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-123">This command disables CredSSP on the client, which prevents delegation to servers.</span></span>

### <span data-ttu-id="6b1b9-124">Exempel 2: inaktivera CredSSP på en server</span><span class="sxs-lookup"><span data-stu-id="6b1b9-124">Example 2: Disable CredSSP on a server</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Server
```

<span data-ttu-id="6b1b9-125">Det här kommandot inaktiverar CredSSP på servern, vilket förhindrar delegering från klienter.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-125">This command disables CredSSP on the server, which prevents delegation from clients.</span></span>

## <span data-ttu-id="6b1b9-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6b1b9-126">PARAMETERS</span></span>

### <span data-ttu-id="6b1b9-127">-Roll</span><span class="sxs-lookup"><span data-stu-id="6b1b9-127">-Role</span></span>
<span data-ttu-id="6b1b9-128">Anger om CredSSP ska inaktive ras som en klient eller som en server.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-128">Specifies whether to disable CredSSP as a client or as a server.</span></span>
<span data-ttu-id="6b1b9-129">De acceptabla värdena för den här parametern är: klient och server.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-129">The acceptable values for this parameter are: Client and Server.</span></span>

<span data-ttu-id="6b1b9-130">Om du anger klient utför denna cmdlet följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="6b1b9-130">If you specify Client, this cmdlet performs the following actions:</span></span>

- <span data-ttu-id="6b1b9-131">Inaktiverar CredSSP på klienten.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-131">Disables CredSSP on the client.</span></span> <span data-ttu-id="6b1b9-132">Den här cmdleten anger WS-Management anger **\<localhost|computername\> \Client\Auth\CredSSP** till false.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-132">This cmdlet sets WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="6b1b9-133">Tar bort alla WSMan/\*-inställningar från Windows CredSSP-principen **AllowFreshCredentials** på klienten.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-133">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="6b1b9-134">Om du anger Server utför denna cmdlet följande åtgärd:</span><span class="sxs-lookup"><span data-stu-id="6b1b9-134">If you specify Server, this cmdlet performs the following action:</span></span>

- <span data-ttu-id="6b1b9-135">Inaktiverar CredSSP på servern.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-135">Disables CredSSP on the server.</span></span> <span data-ttu-id="6b1b9-136">Denna cmdlet anger WS-Management inställningen **\<localhost|computername\> \Service\Auth\CredSSP** till false.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-136">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Client, Server

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6b1b9-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6b1b9-137">CommonParameters</span></span>
<span data-ttu-id="6b1b9-138">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6b1b9-139">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6b1b9-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6b1b9-140">INDATA</span><span class="sxs-lookup"><span data-stu-id="6b1b9-140">INPUTS</span></span>

### <span data-ttu-id="6b1b9-141">Inga</span><span class="sxs-lookup"><span data-stu-id="6b1b9-141">None</span></span>
<span data-ttu-id="6b1b9-142">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-142">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="6b1b9-143">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6b1b9-143">OUTPUTS</span></span>

### <span data-ttu-id="6b1b9-144">Inga</span><span class="sxs-lookup"><span data-stu-id="6b1b9-144">None</span></span>
<span data-ttu-id="6b1b9-145">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-145">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="6b1b9-146">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6b1b9-146">NOTES</span></span>

* <span data-ttu-id="6b1b9-147">Använd Enable-WSManCredSSP-cmdleten om du vill aktivera CredSSP-autentisering.</span><span class="sxs-lookup"><span data-stu-id="6b1b9-147">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

*

## <span data-ttu-id="6b1b9-148">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6b1b9-148">RELATED LINKS</span></span>

[<span data-ttu-id="6b1b9-149">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="6b1b9-149">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="6b1b9-150">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="6b1b9-150">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="6b1b9-151">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="6b1b9-151">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="6b1b9-152">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="6b1b9-152">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="6b1b9-153">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="6b1b9-153">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="6b1b9-154">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="6b1b9-154">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="6b1b9-155">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="6b1b9-155">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="6b1b9-156">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="6b1b9-156">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="6b1b9-157">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="6b1b9-157">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="6b1b9-158">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="6b1b9-158">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="6b1b9-159">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="6b1b9-159">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="6b1b9-160">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="6b1b9-160">Test-WSMan</span></span>](Test-WSMan.md)

