---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-computer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Computer
ms.openlocfilehash: 070a428530f4f3eecceb0ae3f520ad565097c1e0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709937"
---
# <span data-ttu-id="82f72-102">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="82f72-102">Rename-Computer</span></span>

## <span data-ttu-id="82f72-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="82f72-103">SYNOPSIS</span></span>
<span data-ttu-id="82f72-104">Byter namn på en dator.</span><span class="sxs-lookup"><span data-stu-id="82f72-104">Renames a computer.</span></span>

## <span data-ttu-id="82f72-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="82f72-105">SYNTAX</span></span>

```
Rename-Computer [-ComputerName <String>] [-PassThru] [-DomainCredential <PSCredential>]
 [-LocalCredential <PSCredential>] [-NewName] <String> [-Force] [-Restart] [-WsmanAuthentication <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="82f72-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="82f72-106">DESCRIPTION</span></span>

<span data-ttu-id="82f72-107">`Rename-Computer`Cmdleten byter namn på den lokala datorn eller en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="82f72-107">The `Rename-Computer` cmdlet renames the local computer or a remote computer.</span></span>
<span data-ttu-id="82f72-108">Det byter namn på en dator i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="82f72-108">It renames one computer in each command.</span></span>

<span data-ttu-id="82f72-109">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="82f72-109">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="82f72-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="82f72-110">EXAMPLES</span></span>

### <span data-ttu-id="82f72-111">Exempel 1: Byt namn på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="82f72-111">Example 1: Rename the local computer</span></span>

<span data-ttu-id="82f72-112">Det här kommandot byter namn på den lokala datorn till `Server044` och startar sedan om den för att ändringen ska börja gälla.</span><span class="sxs-lookup"><span data-stu-id="82f72-112">This command renames the local computer to `Server044` and then restarts it to make the change effective.</span></span>

```powershell
Rename-Computer -NewName "Server044" -DomainCredential Domain01\Admin01 -Restart
```

### <span data-ttu-id="82f72-113">Exempel 2: Byt namn på en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="82f72-113">Example 2: Rename a remote computer</span></span>

<span data-ttu-id="82f72-114">Det här kommandot byter namn på `Srv01` datorn till `Server001` .</span><span class="sxs-lookup"><span data-stu-id="82f72-114">This command renames the `Srv01` computer to `Server001`.</span></span> <span data-ttu-id="82f72-115">Datorn har inte startats om.</span><span class="sxs-lookup"><span data-stu-id="82f72-115">The computer is not restarted.</span></span>

<span data-ttu-id="82f72-116">Parametern **DomainCredential** anger autentiseringsuppgifterna för en användare som har behörighet att byta namn på datorer i domänen.</span><span class="sxs-lookup"><span data-stu-id="82f72-116">The **DomainCredential** parameter specifies the credentials of a user who has permission to rename computers in the domain.</span></span>

<span data-ttu-id="82f72-117">**Force** -parametern förhindrar bekräftelse frågan.</span><span class="sxs-lookup"><span data-stu-id="82f72-117">The **Force** parameter suppresses the confirmation prompt.</span></span>

```powershell
Rename-Computer -ComputerName "Srv01" -NewName "Server001" -DomainCredential Domain01\Admin01 -Force
```

## <span data-ttu-id="82f72-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="82f72-118">PARAMETERS</span></span>

### <span data-ttu-id="82f72-119">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="82f72-119">-ComputerName</span></span>

<span data-ttu-id="82f72-120">Byter namn på den angivna fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="82f72-120">Renames the specified remote computer.</span></span>
<span data-ttu-id="82f72-121">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="82f72-121">The default is the local computer.</span></span>

<span data-ttu-id="82f72-122">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="82f72-122">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="82f72-123">Om du vill ange den lokala datorn skriver du datorns namn, en punkt ( `.` ) eller `localhost` .</span><span class="sxs-lookup"><span data-stu-id="82f72-123">To specify the local computer, type the computer name, a dot (`.`), or `localhost`.</span></span>

<span data-ttu-id="82f72-124">Den här parametern är inte beroende av PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="82f72-124">This parameter does not rely on PowerShell remoting.</span></span>
<span data-ttu-id="82f72-125">Du kan använda parametern **computername** för `Rename-Computer` även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="82f72-125">You can use the **ComputerName** parameter of `Rename-Computer` even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local Computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="82f72-126">-DomainCredential</span><span class="sxs-lookup"><span data-stu-id="82f72-126">-DomainCredential</span></span>

<span data-ttu-id="82f72-127">Anger ett användar konto som har behörighet att ansluta till domänen.</span><span class="sxs-lookup"><span data-stu-id="82f72-127">Specifies a user account that has permission to connect to the domain.</span></span>
<span data-ttu-id="82f72-128">Explicita autentiseringsuppgifter krävs för att byta namn på en dator som är ansluten till en domän.</span><span class="sxs-lookup"><span data-stu-id="82f72-128">Explicit credentials are required to rename a computer that is joined to a domain.</span></span>

<span data-ttu-id="82f72-129">Ange ett användar namn, till exempel `User01` eller `Domain01\User01` , eller ange ett **PSCredential** -objekt, till exempel en som genereras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="82f72-129">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="82f72-130">Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="82f72-130">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="82f72-131">Om du vill ange ett användar konto som har behörighet att ansluta till den dator som anges av parametern **computername** , använder du parametern **LocalCredential** .</span><span class="sxs-lookup"><span data-stu-id="82f72-131">To specify a user account that has permission to connect to the computer that is specified by the **ComputerName** parameter, use the **LocalCredential** parameter.</span></span>

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

### <span data-ttu-id="82f72-132">-Force</span><span class="sxs-lookup"><span data-stu-id="82f72-132">-Force</span></span>

<span data-ttu-id="82f72-133">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="82f72-133">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="82f72-134">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="82f72-134">-LocalCredential</span></span>

<span data-ttu-id="82f72-135">Anger ett användar konto som har behörighet att ansluta till den dator som anges av parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="82f72-135">Specifies a user account that has permission to connect to the computer specified by the **ComputerName** parameter.</span></span> <span data-ttu-id="82f72-136">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="82f72-136">The default is the current user.</span></span>

<span data-ttu-id="82f72-137">Ange ett användar namn, till exempel `User01` eller `Domain01\User01` , eller ange ett **PSCredential** -objekt, till exempel en som genereras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="82f72-137">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="82f72-138">Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="82f72-138">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="82f72-139">Använd parametern **DomainCredential** för att ange ett användar konto som har behörighet att ansluta till domänen.</span><span class="sxs-lookup"><span data-stu-id="82f72-139">To specify a user account that has permission to connect to the domain, use the **DomainCredential** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current User
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82f72-140">-Nyttnamn</span><span class="sxs-lookup"><span data-stu-id="82f72-140">-NewName</span></span>

<span data-ttu-id="82f72-141">Anger ett nytt namn för datorn.</span><span class="sxs-lookup"><span data-stu-id="82f72-141">Specifies a new name for the computer.</span></span>
<span data-ttu-id="82f72-142">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="82f72-142">This parameter is required.</span></span>

<span data-ttu-id="82f72-143">Standard namn får innehålla bokstäver ( `a-z` ), ( `A-Z` ), siffror ( `0-9` ) och bindestreck ( `-` ), men inte blank steg eller punkter ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="82f72-143">Standard names may contain letters (`a-z`), (`A-Z`), numbers (`0-9`), and hyphens (`-`), but no spaces or periods (`.`).</span></span> <span data-ttu-id="82f72-144">Namnet får inte bestå av enbart siffror och får inte vara längre än 63 tecken</span><span class="sxs-lookup"><span data-stu-id="82f72-144">The name may not consist entirely of digits, and may not be longer than 63 characters</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="82f72-145">– PassThru</span><span class="sxs-lookup"><span data-stu-id="82f72-145">-PassThru</span></span>

<span data-ttu-id="82f72-146">Returnerar kommandots resultat.</span><span class="sxs-lookup"><span data-stu-id="82f72-146">Returns the results of the command.</span></span>
<span data-ttu-id="82f72-147">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="82f72-147">Otherwise, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="82f72-148">-Restart</span><span class="sxs-lookup"><span data-stu-id="82f72-148">-Restart</span></span>

<span data-ttu-id="82f72-149">Anger att den här cmdleten startar om datorn som har bytt namn.</span><span class="sxs-lookup"><span data-stu-id="82f72-149">Indicates that this cmdlet restarts the computer that was renamed.</span></span>
<span data-ttu-id="82f72-150">En omstart krävs ofta för att ändringen ska börja gälla.</span><span class="sxs-lookup"><span data-stu-id="82f72-150">A restart is often required to make the change effective.</span></span>

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

### <span data-ttu-id="82f72-151">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="82f72-151">-WsmanAuthentication</span></span>

<span data-ttu-id="82f72-152">Anger den mekanism som används för att autentisera användarautentiseringsuppgifter när denna cmdlet använder WSMan-protokollet.</span><span class="sxs-lookup"><span data-stu-id="82f72-152">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="82f72-153">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="82f72-153">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="82f72-154">**Basic**</span><span class="sxs-lookup"><span data-stu-id="82f72-154">**Basic**</span></span>
- <span data-ttu-id="82f72-155">**CredSSP**</span><span class="sxs-lookup"><span data-stu-id="82f72-155">**CredSSP**</span></span>
- <span data-ttu-id="82f72-156">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="82f72-156">**Default**</span></span>
- <span data-ttu-id="82f72-157">**Digest**</span><span class="sxs-lookup"><span data-stu-id="82f72-157">**Digest**</span></span>
- <span data-ttu-id="82f72-158">**Kerberos**</span><span class="sxs-lookup"><span data-stu-id="82f72-158">**Kerberos**</span></span>
- <span data-ttu-id="82f72-159">**Fram**</span><span class="sxs-lookup"><span data-stu-id="82f72-159">**Negotiate**</span></span>

<span data-ttu-id="82f72-160">Standardvärdet är **default**.</span><span class="sxs-lookup"><span data-stu-id="82f72-160">The default value is **Default**.</span></span>

<span data-ttu-id="82f72-161">Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="82f72-161">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="82f72-162">Autentisering av Credential Security Service Provider (CredSSP), där användarautentiseringsuppgifterna skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="82f72-162">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
> <span data-ttu-id="82f72-163">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="82f72-163">This mechanism increases the security risk of the remote operation.</span></span>
> <span data-ttu-id="82f72-164">Om fjärrdatorn komprometteras kan autentiseringsuppgifterna som skickas till den användas för att kontrol lera > nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="82f72-164">If the remote computer is compromised, the credentials that are passed to it can be used to control > the network session.</span></span>

<span data-ttu-id="82f72-165">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="82f72-165">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82f72-166">-Confirm</span><span class="sxs-lookup"><span data-stu-id="82f72-166">-Confirm</span></span>

<span data-ttu-id="82f72-167">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="82f72-167">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="82f72-168">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="82f72-168">-WhatIf</span></span>

<span data-ttu-id="82f72-169">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="82f72-169">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="82f72-170">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="82f72-170">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="82f72-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="82f72-171">CommonParameters</span></span>

<span data-ttu-id="82f72-172">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="82f72-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="82f72-173">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="82f72-173">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="82f72-174">INDATA</span><span class="sxs-lookup"><span data-stu-id="82f72-174">INPUTS</span></span>

### <span data-ttu-id="82f72-175">Inga</span><span class="sxs-lookup"><span data-stu-id="82f72-175">None</span></span>

<span data-ttu-id="82f72-176">Den här cmdleten har inte parametrar som tar in inaktuella värden.</span><span class="sxs-lookup"><span data-stu-id="82f72-176">This cmdlet does not have parameters that take input by value.</span></span> <span data-ttu-id="82f72-177">Du kan dock skicka vidare värdena för egenskaperna **computername** och **Nyttnamn** för objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="82f72-177">However, you can pipe the values of the **ComputerName** and **NewName** properties of objects to this cmdlet.</span></span>

## <span data-ttu-id="82f72-178">UTDATA</span><span class="sxs-lookup"><span data-stu-id="82f72-178">OUTPUTS</span></span>

### <span data-ttu-id="82f72-179">Microsoft. PowerShell. commands. ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="82f72-179">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="82f72-180">Denna cmdlet returnerar ett **ComputerChangeInfo** -objekt om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="82f72-180">This cmdlet returns a **ComputerChangeInfo** object, if you specify the **PassThru** parameter.</span></span>
<span data-ttu-id="82f72-181">Annars returneras inga utdata.</span><span class="sxs-lookup"><span data-stu-id="82f72-181">Otherwise, it does not return any output.</span></span>

## <span data-ttu-id="82f72-182">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="82f72-182">NOTES</span></span>

<span data-ttu-id="82f72-183">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="82f72-183">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="82f72-184">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="82f72-184">RELATED LINKS</span></span>

[<span data-ttu-id="82f72-185">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="82f72-185">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="82f72-186">Stoppa – dator</span><span class="sxs-lookup"><span data-stu-id="82f72-186">Stop-Computer</span></span>](Stop-Computer.md)
