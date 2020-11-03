---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-computer?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Computer
ms.openlocfilehash: aeffc496e78a447af828737980429a91a74b5a6b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93261939"
---
# <span data-ttu-id="ee364-103">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="ee364-103">Rename-Computer</span></span>

## <span data-ttu-id="ee364-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ee364-104">SYNOPSIS</span></span>
<span data-ttu-id="ee364-105">Byter namn på en dator.</span><span class="sxs-lookup"><span data-stu-id="ee364-105">Renames a computer.</span></span>

## <span data-ttu-id="ee364-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ee364-106">SYNTAX</span></span>

```
Rename-Computer [-ComputerName <String>] [-PassThru] [-DomainCredential <PSCredential>]
 [-LocalCredential <PSCredential>] [-NewName] <String> [-Force] [-Restart] [-WsmanAuthentication <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ee364-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ee364-107">DESCRIPTION</span></span>

<span data-ttu-id="ee364-108">`Rename-Computer`Cmdleten byter namn på den lokala datorn eller en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="ee364-108">The `Rename-Computer` cmdlet renames the local computer or a remote computer.</span></span>
<span data-ttu-id="ee364-109">Det byter namn på en dator i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="ee364-109">It renames one computer in each command.</span></span>

<span data-ttu-id="ee364-110">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ee364-110">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="ee364-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ee364-111">EXAMPLES</span></span>

### <span data-ttu-id="ee364-112">Exempel 1: Byt namn på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="ee364-112">Example 1: Rename the local computer</span></span>

<span data-ttu-id="ee364-113">Det här kommandot byter namn på den lokala datorn till `Server044` och startar sedan om den för att ändringen ska börja gälla.</span><span class="sxs-lookup"><span data-stu-id="ee364-113">This command renames the local computer to `Server044` and then restarts it to make the change effective.</span></span>

```powershell
Rename-Computer -NewName "Server044" -DomainCredential Domain01\Admin01 -Restart
```

### <span data-ttu-id="ee364-114">Exempel 2: Byt namn på en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="ee364-114">Example 2: Rename a remote computer</span></span>

<span data-ttu-id="ee364-115">Det här kommandot byter namn på `Srv01` datorn till `Server001` .</span><span class="sxs-lookup"><span data-stu-id="ee364-115">This command renames the `Srv01` computer to `Server001`.</span></span> <span data-ttu-id="ee364-116">Datorn har inte startats om.</span><span class="sxs-lookup"><span data-stu-id="ee364-116">The computer is not restarted.</span></span>

<span data-ttu-id="ee364-117">Parametern **DomainCredential** anger autentiseringsuppgifterna för en användare som har behörighet att byta namn på datorer i domänen.</span><span class="sxs-lookup"><span data-stu-id="ee364-117">The **DomainCredential** parameter specifies the credentials of a user who has permission to rename computers in the domain.</span></span>

<span data-ttu-id="ee364-118">**Force** -parametern förhindrar bekräftelse frågan.</span><span class="sxs-lookup"><span data-stu-id="ee364-118">The **Force** parameter suppresses the confirmation prompt.</span></span>

```powershell
Rename-Computer -ComputerName "Srv01" -NewName "Server001" -DomainCredential Domain01\Admin01 -Force
```

## <span data-ttu-id="ee364-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ee364-119">PARAMETERS</span></span>

### <span data-ttu-id="ee364-120">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="ee364-120">-ComputerName</span></span>

<span data-ttu-id="ee364-121">Byter namn på den angivna fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="ee364-121">Renames the specified remote computer.</span></span>
<span data-ttu-id="ee364-122">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ee364-122">The default is the local computer.</span></span>

<span data-ttu-id="ee364-123">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="ee364-123">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="ee364-124">Om du vill ange den lokala datorn skriver du datorns namn, en punkt ( `.` ) eller `localhost` .</span><span class="sxs-lookup"><span data-stu-id="ee364-124">To specify the local computer, type the computer name, a dot (`.`), or `localhost`.</span></span>

<span data-ttu-id="ee364-125">Den här parametern är inte beroende av PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="ee364-125">This parameter does not rely on PowerShell remoting.</span></span>
<span data-ttu-id="ee364-126">Du kan använda parametern **computername** för `Rename-Computer` även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="ee364-126">You can use the **ComputerName** parameter of `Rename-Computer` even if your computer is not configured to run remote commands.</span></span>

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

### <span data-ttu-id="ee364-127">-DomainCredential</span><span class="sxs-lookup"><span data-stu-id="ee364-127">-DomainCredential</span></span>

<span data-ttu-id="ee364-128">Anger ett användar konto som har behörighet att ansluta till domänen.</span><span class="sxs-lookup"><span data-stu-id="ee364-128">Specifies a user account that has permission to connect to the domain.</span></span>
<span data-ttu-id="ee364-129">Explicita autentiseringsuppgifter krävs för att byta namn på en dator som är ansluten till en domän.</span><span class="sxs-lookup"><span data-stu-id="ee364-129">Explicit credentials are required to rename a computer that is joined to a domain.</span></span>

<span data-ttu-id="ee364-130">Ange ett användar namn, till exempel `User01` eller `Domain01\User01` , eller ange ett **PSCredential** -objekt, till exempel en som genereras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ee364-130">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="ee364-131">Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ee364-131">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="ee364-132">Om du vill ange ett användar konto som har behörighet att ansluta till den dator som anges av parametern **computername** , använder du parametern **LocalCredential** .</span><span class="sxs-lookup"><span data-stu-id="ee364-132">To specify a user account that has permission to connect to the computer that is specified by the **ComputerName** parameter, use the **LocalCredential** parameter.</span></span>

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

### <span data-ttu-id="ee364-133">-Force</span><span class="sxs-lookup"><span data-stu-id="ee364-133">-Force</span></span>

<span data-ttu-id="ee364-134">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="ee364-134">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="ee364-135">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="ee364-135">-LocalCredential</span></span>

<span data-ttu-id="ee364-136">Anger ett användar konto som har behörighet att ansluta till den dator som anges av parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="ee364-136">Specifies a user account that has permission to connect to the computer specified by the **ComputerName** parameter.</span></span> <span data-ttu-id="ee364-137">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="ee364-137">The default is the current user.</span></span>

<span data-ttu-id="ee364-138">Ange ett användar namn, till exempel `User01` eller `Domain01\User01` , eller ange ett **PSCredential** -objekt, till exempel en som genereras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ee364-138">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="ee364-139">Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ee364-139">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="ee364-140">Använd parametern **DomainCredential** för att ange ett användar konto som har behörighet att ansluta till domänen.</span><span class="sxs-lookup"><span data-stu-id="ee364-140">To specify a user account that has permission to connect to the domain, use the **DomainCredential** parameter.</span></span>

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

### <span data-ttu-id="ee364-141">-Nyttnamn</span><span class="sxs-lookup"><span data-stu-id="ee364-141">-NewName</span></span>

<span data-ttu-id="ee364-142">Anger ett nytt namn för datorn.</span><span class="sxs-lookup"><span data-stu-id="ee364-142">Specifies a new name for the computer.</span></span>
<span data-ttu-id="ee364-143">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="ee364-143">This parameter is required.</span></span>

<span data-ttu-id="ee364-144">Standard namn får innehålla bokstäver ( `a-z` ), ( `A-Z` ), siffror ( `0-9` ) och bindestreck ( `-` ), men inte blank steg eller punkter ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="ee364-144">Standard names may contain letters (`a-z`), (`A-Z`), numbers (`0-9`), and hyphens (`-`), but no spaces or periods (`.`).</span></span> <span data-ttu-id="ee364-145">Namnet får inte bestå av enbart siffror och får inte vara längre än 63 tecken</span><span class="sxs-lookup"><span data-stu-id="ee364-145">The name may not consist entirely of digits, and may not be longer than 63 characters</span></span>

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

### <span data-ttu-id="ee364-146">– PassThru</span><span class="sxs-lookup"><span data-stu-id="ee364-146">-PassThru</span></span>

<span data-ttu-id="ee364-147">Returnerar kommandots resultat.</span><span class="sxs-lookup"><span data-stu-id="ee364-147">Returns the results of the command.</span></span>
<span data-ttu-id="ee364-148">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="ee364-148">Otherwise, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="ee364-149">-Restart</span><span class="sxs-lookup"><span data-stu-id="ee364-149">-Restart</span></span>

<span data-ttu-id="ee364-150">Anger att den här cmdleten startar om datorn som har bytt namn.</span><span class="sxs-lookup"><span data-stu-id="ee364-150">Indicates that this cmdlet restarts the computer that was renamed.</span></span>
<span data-ttu-id="ee364-151">En omstart krävs ofta för att ändringen ska börja gälla.</span><span class="sxs-lookup"><span data-stu-id="ee364-151">A restart is often required to make the change effective.</span></span>

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

### <span data-ttu-id="ee364-152">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="ee364-152">-WsmanAuthentication</span></span>

<span data-ttu-id="ee364-153">Anger den mekanism som används för att autentisera användarautentiseringsuppgifter när denna cmdlet använder WSMan-protokollet.</span><span class="sxs-lookup"><span data-stu-id="ee364-153">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="ee364-154">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="ee364-154">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ee364-155">**Basic**</span><span class="sxs-lookup"><span data-stu-id="ee364-155">**Basic**</span></span>
- <span data-ttu-id="ee364-156">**CredSSP**</span><span class="sxs-lookup"><span data-stu-id="ee364-156">**CredSSP**</span></span>
- <span data-ttu-id="ee364-157">**Default**</span><span class="sxs-lookup"><span data-stu-id="ee364-157">**Default**</span></span>
- <span data-ttu-id="ee364-158">**Digest**</span><span class="sxs-lookup"><span data-stu-id="ee364-158">**Digest**</span></span>
- <span data-ttu-id="ee364-159">**Kerberos**</span><span class="sxs-lookup"><span data-stu-id="ee364-159">**Kerberos**</span></span>
- <span data-ttu-id="ee364-160">**Fram**</span><span class="sxs-lookup"><span data-stu-id="ee364-160">**Negotiate**</span></span>

<span data-ttu-id="ee364-161">Standardvärdet är **default**.</span><span class="sxs-lookup"><span data-stu-id="ee364-161">The default value is **Default**.</span></span>

<span data-ttu-id="ee364-162">Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="ee364-162">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="ee364-163">Autentisering av Credential Security Service Provider (CredSSP), där användarautentiseringsuppgifterna skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="ee364-163">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
> <span data-ttu-id="ee364-164">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="ee364-164">This mechanism increases the security risk of the remote operation.</span></span>
> <span data-ttu-id="ee364-165">Om fjärrdatorn komprometteras kan autentiseringsuppgifterna som skickas till den användas för att kontrol lera > nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee364-165">If the remote computer is compromised, the credentials that are passed to it can be used to control > the network session.</span></span>

<span data-ttu-id="ee364-166">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ee364-166">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="ee364-167">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ee364-167">-Confirm</span></span>

<span data-ttu-id="ee364-168">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ee364-168">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ee364-169">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ee364-169">-WhatIf</span></span>

<span data-ttu-id="ee364-170">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="ee364-170">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ee364-171">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="ee364-171">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ee364-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ee364-172">CommonParameters</span></span>

<span data-ttu-id="ee364-173">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ee364-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ee364-174">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="ee364-174">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="ee364-175">INDATA</span><span class="sxs-lookup"><span data-stu-id="ee364-175">INPUTS</span></span>

### <span data-ttu-id="ee364-176">Inget</span><span class="sxs-lookup"><span data-stu-id="ee364-176">None</span></span>

<span data-ttu-id="ee364-177">Den här cmdleten har inte parametrar som tar in inaktuella värden.</span><span class="sxs-lookup"><span data-stu-id="ee364-177">This cmdlet does not have parameters that take input by value.</span></span>
<span data-ttu-id="ee364-178">Du kan dock skicka vidare värdena för egenskaperna **computername** och **Nyttnamn** för objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ee364-178">However, you can pipe the values of the **ComputerName** and **NewName** properties of objects to this cmdlet.</span></span>

## <span data-ttu-id="ee364-179">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ee364-179">OUTPUTS</span></span>

### <span data-ttu-id="ee364-180">Microsoft. PowerShell. commands. ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="ee364-180">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="ee364-181">Denna cmdlet returnerar ett **ComputerChangeInfo** -objekt om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="ee364-181">This cmdlet returns a **ComputerChangeInfo** object, if you specify the **PassThru** parameter.</span></span>
<span data-ttu-id="ee364-182">Annars returneras inga utdata.</span><span class="sxs-lookup"><span data-stu-id="ee364-182">Otherwise, it does not return any output.</span></span>

## <span data-ttu-id="ee364-183">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ee364-183">NOTES</span></span>

## <span data-ttu-id="ee364-184">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ee364-184">RELATED LINKS</span></span>

[<span data-ttu-id="ee364-185">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="ee364-185">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="ee364-186">Stoppa – dator</span><span class="sxs-lookup"><span data-stu-id="ee364-186">Stop-Computer</span></span>](Stop-Computer.md)
