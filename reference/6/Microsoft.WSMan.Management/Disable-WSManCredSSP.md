---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disable-wsmancredssp?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManCredSSP
ms.openlocfilehash: 6b6cf6b4056dd5907f6a43cd9cf6d491bc7512b9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263996"
---
# <span data-ttu-id="4db33-103">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="4db33-103">Disable-WSManCredSSP</span></span>

## <span data-ttu-id="4db33-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4db33-104">SYNOPSIS</span></span>
<span data-ttu-id="4db33-105">Inaktiverar CredSSP-autentisering på en dator.</span><span class="sxs-lookup"><span data-stu-id="4db33-105">Disables CredSSP authentication on a computer.</span></span>

## <span data-ttu-id="4db33-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4db33-106">SYNTAX</span></span>

```
Disable-WSManCredSSP [-Role] <String> [<CommonParameters>]
```

## <span data-ttu-id="4db33-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4db33-107">DESCRIPTION</span></span>
<span data-ttu-id="4db33-108">Cmdlet **: en Disable-WSManCredSSP** inaktiverar CredSSP-autentisering (Credential Security Support Provider) på en klient eller på en serverdator.</span><span class="sxs-lookup"><span data-stu-id="4db33-108">The **Disable-WSManCredSSP** cmdlet disables Credential Security Support Provider (CredSSP) authentication on a client or on a server computer.</span></span>
<span data-ttu-id="4db33-109">När CredSSP-autentisering används skickas användarautentiseringsuppgifter till en fjärrdator som ska autentiseras.</span><span class="sxs-lookup"><span data-stu-id="4db33-109">When CredSSP authentication is used, the user credentials are passed to a remote computer to be authenticated.</span></span>

<span data-ttu-id="4db33-110">Använd denna cmdlet för att inaktivera CredSSP på klienten genom att ange klienten i *roll* parametern.</span><span class="sxs-lookup"><span data-stu-id="4db33-110">Use this cmdlet to disable CredSSP on the client by specifying Client in the *Role* parameter.</span></span>
<span data-ttu-id="4db33-111">Denna cmdlet utför följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="4db33-111">This cmdlet performs the following actions:</span></span>

- <span data-ttu-id="4db33-112">Inaktiverar CredSSP på klienten.</span><span class="sxs-lookup"><span data-stu-id="4db33-112">Disables CredSSP on the client.</span></span> <span data-ttu-id="4db33-113">Denna cmdlet anger WS-Management inställningen **\<localhost|computername\> \Client\Auth\CredSSP** till false.</span><span class="sxs-lookup"><span data-stu-id="4db33-113">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="4db33-114">Tar bort alla WSMan/\*-inställningar från Windows CredSSP-principen **AllowFreshCredentials** på klienten.</span><span class="sxs-lookup"><span data-stu-id="4db33-114">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="4db33-115">Använd denna cmdlet för att inaktivera CredSSP på servern genom att ange server i *roll*.</span><span class="sxs-lookup"><span data-stu-id="4db33-115">Use this cmdlet to disable CredSSP on the server by specifying Server in *Role*.</span></span>
<span data-ttu-id="4db33-116">Denna cmdlet utför följande åtgärd:</span><span class="sxs-lookup"><span data-stu-id="4db33-116">This cmdlet performs the following action:</span></span>

- <span data-ttu-id="4db33-117">Inaktiverar CredSSP på servern.</span><span class="sxs-lookup"><span data-stu-id="4db33-117">Disables CredSSP on the server.</span></span> <span data-ttu-id="4db33-118">Denna cmdlet anger WS-Management inställningen **\<localhost|computername\> \Service\Auth\CredSSP** till false.</span><span class="sxs-lookup"><span data-stu-id="4db33-118">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

<span data-ttu-id="4db33-119">Varning! CredSSP-autentisering delegerar användarautentiseringsuppgifter från den lokala datorn till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="4db33-119">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="4db33-120">Den här metoden ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="4db33-120">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="4db33-121">Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="4db33-121">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="4db33-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4db33-122">EXAMPLES</span></span>

### <span data-ttu-id="4db33-123">Exempel 1: inaktivera CredSSP på en klient</span><span class="sxs-lookup"><span data-stu-id="4db33-123">Example 1: Disable CredSSP on a client</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Client
```

<span data-ttu-id="4db33-124">Det här kommandot inaktiverar CredSSP på klienten, vilket förhindrar delegering till servrar.</span><span class="sxs-lookup"><span data-stu-id="4db33-124">This command disables CredSSP on the client, which prevents delegation to servers.</span></span>

### <span data-ttu-id="4db33-125">Exempel 2: inaktivera CredSSP på en server</span><span class="sxs-lookup"><span data-stu-id="4db33-125">Example 2: Disable CredSSP on a server</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Server
```

<span data-ttu-id="4db33-126">Det här kommandot inaktiverar CredSSP på servern, vilket förhindrar delegering från klienter.</span><span class="sxs-lookup"><span data-stu-id="4db33-126">This command disables CredSSP on the server, which prevents delegation from clients.</span></span>

## <span data-ttu-id="4db33-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4db33-127">PARAMETERS</span></span>

### <span data-ttu-id="4db33-128">-Roll</span><span class="sxs-lookup"><span data-stu-id="4db33-128">-Role</span></span>
<span data-ttu-id="4db33-129">Anger om CredSSP ska inaktive ras som en klient eller som en server.</span><span class="sxs-lookup"><span data-stu-id="4db33-129">Specifies whether to disable CredSSP as a client or as a server.</span></span>
<span data-ttu-id="4db33-130">De acceptabla värdena för den här parametern är: klient och server.</span><span class="sxs-lookup"><span data-stu-id="4db33-130">The acceptable values for this parameter are: Client and Server.</span></span>

<span data-ttu-id="4db33-131">Om du anger klient utför denna cmdlet följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="4db33-131">If you specify Client, this cmdlet performs the following actions:</span></span>

- <span data-ttu-id="4db33-132">Inaktiverar CredSSP på klienten.</span><span class="sxs-lookup"><span data-stu-id="4db33-132">Disables CredSSP on the client.</span></span> <span data-ttu-id="4db33-133">Den här cmdleten anger WS-Management anger **\<localhost|computername\> \Client\Auth\CredSSP** till false.</span><span class="sxs-lookup"><span data-stu-id="4db33-133">This cmdlet sets WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="4db33-134">Tar bort alla WSMan/\*-inställningar från Windows CredSSP-principen **AllowFreshCredentials** på klienten.</span><span class="sxs-lookup"><span data-stu-id="4db33-134">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="4db33-135">Om du anger Server utför denna cmdlet följande åtgärd:</span><span class="sxs-lookup"><span data-stu-id="4db33-135">If you specify Server, this cmdlet performs the following action:</span></span>

- <span data-ttu-id="4db33-136">Inaktiverar CredSSP på servern.</span><span class="sxs-lookup"><span data-stu-id="4db33-136">Disables CredSSP on the server.</span></span> <span data-ttu-id="4db33-137">Denna cmdlet anger WS-Management inställningen **\<localhost|computername\> \Service\Auth\CredSSP** till false.</span><span class="sxs-lookup"><span data-stu-id="4db33-137">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

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

### <span data-ttu-id="4db33-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4db33-138">CommonParameters</span></span>
<span data-ttu-id="4db33-139">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4db33-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4db33-140">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4db33-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4db33-141">INDATA</span><span class="sxs-lookup"><span data-stu-id="4db33-141">INPUTS</span></span>

### <span data-ttu-id="4db33-142">Inget</span><span class="sxs-lookup"><span data-stu-id="4db33-142">None</span></span>
<span data-ttu-id="4db33-143">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="4db33-143">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="4db33-144">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4db33-144">OUTPUTS</span></span>

### <span data-ttu-id="4db33-145">Inget</span><span class="sxs-lookup"><span data-stu-id="4db33-145">None</span></span>
<span data-ttu-id="4db33-146">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="4db33-146">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="4db33-147">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4db33-147">NOTES</span></span>

* <span data-ttu-id="4db33-148">Använd Enable-WSManCredSSP-cmdleten om du vill aktivera CredSSP-autentisering.</span><span class="sxs-lookup"><span data-stu-id="4db33-148">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

*

## <span data-ttu-id="4db33-149">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4db33-149">RELATED LINKS</span></span>

[<span data-ttu-id="4db33-150">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="4db33-150">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="4db33-151">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="4db33-151">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="4db33-152">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="4db33-152">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="4db33-153">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="4db33-153">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="4db33-154">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="4db33-154">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="4db33-155">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="4db33-155">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="4db33-156">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="4db33-156">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="4db33-157">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="4db33-157">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="4db33-158">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="4db33-158">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="4db33-159">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="4db33-159">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="4db33-160">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="4db33-160">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="4db33-161">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="4db33-161">Test-WSMan</span></span>](Test-WSMan.md)
