---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 08/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/enable-wsmancredssp?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManCredSSP
ms.openlocfilehash: 48429114a8e174351f4323acb501f89261e4a40a
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268479"
---
# <span data-ttu-id="ca600-103">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="ca600-103">Enable-WSManCredSSP</span></span>

## <span data-ttu-id="ca600-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ca600-104">SYNOPSIS</span></span>
<span data-ttu-id="ca600-105">Aktiverar autentisering med CredSSP (Credential Security Support Provider) på en dator.</span><span class="sxs-lookup"><span data-stu-id="ca600-105">Enables Credential Security Support Provider (CredSSP) authentication on a computer.</span></span>

## <span data-ttu-id="ca600-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ca600-106">SYNTAX</span></span>

### <span data-ttu-id="ca600-107">Alla</span><span class="sxs-lookup"><span data-stu-id="ca600-107">All</span></span>

```
Enable-WSManCredSSP [[-DelegateComputer] <String[]>] [-Force] [-Role] <String> [<CommonParameters>]
```

## <span data-ttu-id="ca600-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ca600-108">DESCRIPTION</span></span>

<span data-ttu-id="ca600-109">`Enable-WSManCredSSP`Cmdlet: en aktiverar CredSSP-autentisering på en klient eller på en serverdator.</span><span class="sxs-lookup"><span data-stu-id="ca600-109">The `Enable-WSManCredSSP` cmdlet enables CredSSP authentication on a client or on a server computer.</span></span>
<span data-ttu-id="ca600-110">När CredSSP-autentisering används skickas användarautentiseringsuppgifter till en fjärrdator som ska autentiseras.</span><span class="sxs-lookup"><span data-stu-id="ca600-110">When CredSSP authentication is used, the user credentials are passed to a remote computer to be authenticated.</span></span> <span data-ttu-id="ca600-111">Den här typen av autentisering är utformad för kommandon som skapar en fjärrsession från en annan fjärran sluten session.</span><span class="sxs-lookup"><span data-stu-id="ca600-111">This type of authentication is designed for commands that create a remote session from another remote session.</span></span> <span data-ttu-id="ca600-112">Om du till exempel vill köra ett bakgrunds jobb på en fjärrdator använder du den här typen av autentisering.</span><span class="sxs-lookup"><span data-stu-id="ca600-112">For example, if you want to run a background job on a remote computer, use this kind of authentication.</span></span>

<span data-ttu-id="ca600-113">`Enable-WSManCredSSP` kan aktivera CredSSP på en **klient** eller **Server**.</span><span class="sxs-lookup"><span data-stu-id="ca600-113">`Enable-WSManCredSSP` can enable CredSSP on a **Client** or a **Server**.</span></span> <span data-ttu-id="ca600-114">Om du vill aktivera CredSSP på en klient anger du **client** i **roll** parametern.</span><span class="sxs-lookup"><span data-stu-id="ca600-114">To enable CredSSP on a client, specify **Client** in the **Role** parameter.</span></span> <span data-ttu-id="ca600-115">Klienterna delegerar explicita autentiseringsuppgifter till en server när serverautentisering uppnås.</span><span class="sxs-lookup"><span data-stu-id="ca600-115">Clients delegate explicit credentials to a server when server authentication is achieved.</span></span> <span data-ttu-id="ca600-116">Om du vill aktivera CredSSP på en server anger du **Server** i **roll** parametern.</span><span class="sxs-lookup"><span data-stu-id="ca600-116">To enable CredSSP on a server, specify **Server** in the **Role** parameter.</span></span> <span data-ttu-id="ca600-117">En server fungerar som ett ombud för-klienter.</span><span class="sxs-lookup"><span data-stu-id="ca600-117">A server acts as a delegate for clients.</span></span> <span data-ttu-id="ca600-118">Mer information finns i **roll** i avsnittet parametrar.</span><span class="sxs-lookup"><span data-stu-id="ca600-118">For more details, see **Role** in the Parameters section.</span></span>

> [!CAUTION]
> <span data-ttu-id="ca600-119">CredSSP-autentisering delegerar användarautentiseringsuppgifter från den lokala datorn till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="ca600-119">CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span> <span data-ttu-id="ca600-120">Den här metoden ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="ca600-120">This practice increases the security risk of the remote operation.</span></span> <span data-ttu-id="ca600-121">Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="ca600-121">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="ca600-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ca600-122">EXAMPLES</span></span>

### <span data-ttu-id="ca600-123">Exempel 1: delegera klientautentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="ca600-123">Example 1: Delegate client credentials</span></span>

<span data-ttu-id="ca600-124">Det här exemplet gör att klientautentiseringsuppgifterna kan delegeras till en dator genom att använda det fullständigt kvalificerade domän namnet.</span><span class="sxs-lookup"><span data-stu-id="ca600-124">This example allows the client credentials to be delegated to a computer by using the fully qualified domain name.</span></span>

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "Server02.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### <span data-ttu-id="ca600-125">Exempel 2: delegera klientautentiseringsuppgifter till alla datorer i en domän</span><span class="sxs-lookup"><span data-stu-id="ca600-125">Example 2: Delegate client credentials to all computers in a domain</span></span>

<span data-ttu-id="ca600-126">Det här exemplet gör att klientautentiseringsuppgifterna kan delegeras till alla datorer i **fabrikam.com** -domänen.</span><span class="sxs-lookup"><span data-stu-id="ca600-126">This example allows the client credentials to be delegated to all the computers in the **fabrikam.com** domain.</span></span> <span data-ttu-id="ca600-127">Jokertecknet asterisk ( `*` ) anger alla datorer.</span><span class="sxs-lookup"><span data-stu-id="ca600-127">The asterisk (`*`) wildcard specifies all computers.</span></span>

> [!NOTE]
> <span data-ttu-id="ca600-128">Med jokertecken med parametern **DelegateComputer** kan du aktivera CredSSP på fler datorer än vad som behövs.</span><span class="sxs-lookup"><span data-stu-id="ca600-128">Using wildcards with the **DelegateComputer** parameter can enable CredSSP on more computers than necessary.</span></span>

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "*.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### <span data-ttu-id="ca600-129">Exempel 3: delegera klientautentiseringsuppgifter till flera datorer</span><span class="sxs-lookup"><span data-stu-id="ca600-129">Example 3: Delegate client credentials to multiple computers</span></span>

<span data-ttu-id="ca600-130">Det här exemplet gör att klientautentiseringsuppgifterna kan delegeras till flera datorer.</span><span class="sxs-lookup"><span data-stu-id="ca600-130">This example allows the client credentials to be delegated to multiple computers.</span></span>

```powershell
$servers = "server02.fabrikam.com", "server03.fabrikam.com", "server04.fabrikam.com"
Enable-WSManCredSSP -Role "Client" -DelegateComputer $servers
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

<span data-ttu-id="ca600-131">`$servers`Variabeln innehåller en lista över Server namn.</span><span class="sxs-lookup"><span data-stu-id="ca600-131">The `$servers` variable contains a list of server names.</span></span> <span data-ttu-id="ca600-132">`Enable-WSManCredSSP` använder **roll** parametern för att ange **klient** rollen.</span><span class="sxs-lookup"><span data-stu-id="ca600-132">`Enable-WSManCredSSP` uses the **Role** parameter to specify the **Client** role.</span></span> <span data-ttu-id="ca600-133">**DelegateComputer** hämtar dator namnen från `$servers` variabeln.</span><span class="sxs-lookup"><span data-stu-id="ca600-133">The **DelegateComputer** gets the computer names from the `$servers` variable.</span></span>

### <span data-ttu-id="ca600-134">Exempel 4: Tillåt att en dator fungerar som ett ombud</span><span class="sxs-lookup"><span data-stu-id="ca600-134">Example 4: Allow a computer to act as a delegate</span></span>

<span data-ttu-id="ca600-135">I det här exemplet kan en dator fungera som ett ombud för en annan.</span><span class="sxs-lookup"><span data-stu-id="ca600-135">This example allows a computer to act as a delegate for another.</span></span> <span data-ttu-id="ca600-136">`Enable-WSManCredSSP`Cmdleten, som visas i de tidigare exemplen, aktiverar endast CredSSP-autentisering på klienten och anger de fjärrdatorer som kan agera för dess räkning.</span><span class="sxs-lookup"><span data-stu-id="ca600-136">The `Enable-WSManCredSSP` cmdlet, shown in the earlier examples, only enables CredSSP authentication on the client, and specifies the remote computers that can act on its behalf.</span></span> <span data-ttu-id="ca600-137">För att fjärrdatorn ska fungera som ett ombud för klienten måste CredSSP-objektet i noden **tjänst** för WSMan anges till true.</span><span class="sxs-lookup"><span data-stu-id="ca600-137">In order for the remote computer to act as a delegate for the client, the CredSSP item in the **Service** node of WSMan must be set to true.</span></span> <span data-ttu-id="ca600-138">I det här exemplet anges CredSSP-objektet i **tjänst-** noden för WSMan till true.</span><span class="sxs-lookup"><span data-stu-id="ca600-138">This example sets the CredSSP item in the **Service** node of WSMan to true.</span></span>

```powershell
Enable-WSManCredSSP -Role "Server"
```

### <span data-ttu-id="ca600-139">Exempel 5: Tillåt att en dator fungerar som ett ombud med hjälp av Set-Item</span><span class="sxs-lookup"><span data-stu-id="ca600-139">Example 5: Allow a computer to act as a delegate by using Set-Item</span></span>

<span data-ttu-id="ca600-140">I det här exemplet kan en dator fungera som ett ombud för en annan dator.</span><span class="sxs-lookup"><span data-stu-id="ca600-140">This example allows a computer to act as a delegate for another computer.</span></span> <span data-ttu-id="ca600-141">`Enable-WSManCredSSP`Kommandona, som visas i de tidigare exemplen, aktiverar endast CredSSP-autentisering på klient datorn och de anger fjärrdatorer som kan agera för klient datorns räkning.</span><span class="sxs-lookup"><span data-stu-id="ca600-141">The `Enable-WSManCredSSP` commands, shown in the earlier examples, enable CredSSP authentication only on the client computer, and they specify the remote computers that can act on behalf of the client computer.</span></span> <span data-ttu-id="ca600-142">För att fjärrdatorn ska fungera som ett ombud för klient datorn måste CredSSP-objektet i tjänst katalogen för WSMan-providern anges till sant.</span><span class="sxs-lookup"><span data-stu-id="ca600-142">For the remote computer to act as a delegate for the client computer, the CredSSP item in the Service directory of the WSMan provider must be set to true.</span></span>

```powershell
Connect-WSMan -ComputerName "server02"
Set-Item -Path "WSMan:\server02\service\auth\credSSP" -Value $True
```

<span data-ttu-id="ca600-143">`Connect-WSMan` skapar en anslutning till fjärrdatorn, server02.</span><span class="sxs-lookup"><span data-stu-id="ca600-143">`Connect-WSMan` creates a connection to the remote computer, server02.</span></span> <span data-ttu-id="ca600-144">`Set-Item` använder parametern **Path** för att ange platsen för **WSMan** -providern.</span><span class="sxs-lookup"><span data-stu-id="ca600-144">`Set-Item` uses the **Path** parameter to specify the **WSMan** provider's location.</span></span> <span data-ttu-id="ca600-145">Parametern **Value** anger **tjänst** inställningen till true.</span><span class="sxs-lookup"><span data-stu-id="ca600-145">The **Value** parameter sets the **Service** setting to true.</span></span>

## <span data-ttu-id="ca600-146">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ca600-146">PARAMETERS</span></span>

### <span data-ttu-id="ca600-147">-DelegateComputer</span><span class="sxs-lookup"><span data-stu-id="ca600-147">-DelegateComputer</span></span>

<span data-ttu-id="ca600-148">Anger servrar som klientautentiseringsuppgifterna är delegerade till.</span><span class="sxs-lookup"><span data-stu-id="ca600-148">Specifies servers to which client credentials are delegated.</span></span> <span data-ttu-id="ca600-149">Det bästa sättet är att använda fullständigt kvalificerade domän namn.</span><span class="sxs-lookup"><span data-stu-id="ca600-149">The best practice is to use fully qualified domain names.</span></span>

<span data-ttu-id="ca600-150">Jokertecken accepteras, men kan aktivera CredSSP på fler datorer än vad som behövs.</span><span class="sxs-lookup"><span data-stu-id="ca600-150">Wildcards are accepted, but can enable CredSSP on more computers than necessary.</span></span>

<span data-ttu-id="ca600-151">Om **roll** parametern är **klient** måste du ange den här parametern.</span><span class="sxs-lookup"><span data-stu-id="ca600-151">If the **Role** parameter is **Client** , you must specify this parameter.</span></span> <span data-ttu-id="ca600-152">Ange inte den här parametern om **rollen** är **Server**.</span><span class="sxs-lookup"><span data-stu-id="ca600-152">If **Role** is **Server** , don't specify this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="ca600-153">-Force</span><span class="sxs-lookup"><span data-stu-id="ca600-153">-Force</span></span>

<span data-ttu-id="ca600-154">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="ca600-154">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="ca600-155">-Roll</span><span class="sxs-lookup"><span data-stu-id="ca600-155">-Role</span></span>

<span data-ttu-id="ca600-156">Anger om CredSSP ska aktive ras som en klient eller som en server.</span><span class="sxs-lookup"><span data-stu-id="ca600-156">Specifies whether to enable CredSSP as a client or as a server.</span></span> <span data-ttu-id="ca600-157">De acceptabla värdena för den här parametern är: **klient** och **Server**.</span><span class="sxs-lookup"><span data-stu-id="ca600-157">The acceptable values for this parameter are: **Client** and **Server**.</span></span>

<span data-ttu-id="ca600-158">Om du anger **klient** utförs följande åtgärder.</span><span class="sxs-lookup"><span data-stu-id="ca600-158">If you specify **Client** , the following actions are performed.</span></span> <span data-ttu-id="ca600-159">De här inställningarna gör att klienten kan delegera explicita autentiseringsuppgifter till en server när serverautentisering uppnås.</span><span class="sxs-lookup"><span data-stu-id="ca600-159">These settings allow the client to delegate explicit credentials to a server when server authentication is achieved.</span></span>

- <span data-ttu-id="ca600-160">Aktiverar CredSSP på klienten.</span><span class="sxs-lookup"><span data-stu-id="ca600-160">Enables CredSSP on the client.</span></span>
- <span data-ttu-id="ca600-161">Ställer in WS-Management inställningen `\<localhost|computername\>\Client\Auth\CredSSP` till sant.</span><span class="sxs-lookup"><span data-stu-id="ca600-161">Sets the WS-Management setting `\<localhost|computername\>\Client\Auth\CredSSP` to true.</span></span>
- <span data-ttu-id="ca600-162">Anger Windows CredSSP-principen **AllowFreshCredentials** till **WSMan/delegaten** på klienten.</span><span class="sxs-lookup"><span data-stu-id="ca600-162">Sets the Windows CredSSP policy **AllowFreshCredentials** to **WSMan/Delegate** on the client.</span></span>

<span data-ttu-id="ca600-163">Om du anger **Server** utförs följande åtgärder.</span><span class="sxs-lookup"><span data-stu-id="ca600-163">If you specify **Server** , the following actions are performed.</span></span> <span data-ttu-id="ca600-164">Med den här princip inställningen kan servern agera som ombud för klienter.</span><span class="sxs-lookup"><span data-stu-id="ca600-164">This policy setting allows the server to act as a delegate for clients.</span></span>

- <span data-ttu-id="ca600-165">Aktiverar CredSSP på servern.</span><span class="sxs-lookup"><span data-stu-id="ca600-165">Enables CredSSP on the server.</span></span>
- <span data-ttu-id="ca600-166">Ställer in WS-Management inställningen `\<localhost|computername\>\Service\Auth\CredSSP` till sant.</span><span class="sxs-lookup"><span data-stu-id="ca600-166">Sets the WS-Management setting `\<localhost|computername\>\Service\Auth\CredSSP` to true.</span></span>

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

### <span data-ttu-id="ca600-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ca600-167">CommonParameters</span></span>

<span data-ttu-id="ca600-168">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ca600-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ca600-169">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ca600-169">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ca600-170">INDATA</span><span class="sxs-lookup"><span data-stu-id="ca600-170">INPUTS</span></span>

### <span data-ttu-id="ca600-171">Inget</span><span class="sxs-lookup"><span data-stu-id="ca600-171">None</span></span>

<span data-ttu-id="ca600-172">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="ca600-172">This cmdlet doesn't accept any input.</span></span>

## <span data-ttu-id="ca600-173">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ca600-173">OUTPUTS</span></span>

### <span data-ttu-id="ca600-174">System.Xml.Xml-element</span><span class="sxs-lookup"><span data-stu-id="ca600-174">System.Xml.XmlElement</span></span>

<span data-ttu-id="ca600-175">Om CredSSP-autentisering har Aktiver ATS genererar denna cmdlet ett **XMLElement** -objekt.</span><span class="sxs-lookup"><span data-stu-id="ca600-175">If CredSSP authentication is successfully enabled, this cmdlet generates an **XMLElement** object.</span></span>

## <span data-ttu-id="ca600-176">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ca600-176">NOTES</span></span>

<span data-ttu-id="ca600-177">Använd cmdleten om du vill inaktivera CredSSP-autentisering `Disable-WSManCredSSP` .</span><span class="sxs-lookup"><span data-stu-id="ca600-177">To disable CredSSP authentication, use the `Disable-WSManCredSSP` cmdlet.</span></span>

## <span data-ttu-id="ca600-178">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ca600-178">RELATED LINKS</span></span>

[<span data-ttu-id="ca600-179">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="ca600-179">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="ca600-180">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="ca600-180">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="ca600-181">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="ca600-181">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="ca600-182">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="ca600-182">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="ca600-183">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ca600-183">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="ca600-184">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="ca600-184">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="ca600-185">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ca600-185">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="ca600-186">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="ca600-186">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="ca600-187">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ca600-187">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="ca600-188">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ca600-188">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="ca600-189">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="ca600-189">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="ca600-190">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="ca600-190">Test-WSMan</span></span>](Test-WSMan.md)
