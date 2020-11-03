---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/04/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Computer
ms.openlocfilehash: 89e43220a8d5ac675ea232db09cf3edec2ca2b97
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265485"
---
# <span data-ttu-id="e191a-103">Remove-Computer</span><span class="sxs-lookup"><span data-stu-id="e191a-103">Remove-Computer</span></span>

## <span data-ttu-id="e191a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e191a-104">SYNOPSIS</span></span>
<span data-ttu-id="e191a-105">Tar bort den lokala datorn från dess domän.</span><span class="sxs-lookup"><span data-stu-id="e191a-105">Removes the local computer from its domain.</span></span>

## <span data-ttu-id="e191a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e191a-106">SYNTAX</span></span>

### <span data-ttu-id="e191a-107">Lokalt (standard)</span><span class="sxs-lookup"><span data-stu-id="e191a-107">Local (Default)</span></span>

```
Remove-Computer [[-UnjoinDomainCredential] <PSCredential>] [-Restart] [-Force] [-PassThru]
 [-WorkgroupName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e191a-108">Fjärransluten</span><span class="sxs-lookup"><span data-stu-id="e191a-108">Remote</span></span>

```
Remove-Computer -UnjoinDomainCredential <PSCredential> [-LocalCredential <PSCredential>] [-Restart]
 [-ComputerName <String[]>] [-Force] [-PassThru] [-WorkgroupName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="e191a-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e191a-109">DESCRIPTION</span></span>

<span data-ttu-id="e191a-110">`Remove-Computer`Cmdleten tar bort den lokala datorn och fjärrdatorerna från deras aktuella domäner.</span><span class="sxs-lookup"><span data-stu-id="e191a-110">The `Remove-Computer` cmdlet removes the local computer and remote computers from their current domains.</span></span>

<span data-ttu-id="e191a-111">När du tar bort en dator från en domän `Remove-Computer` inaktive ras även domän kontot för datorn.</span><span class="sxs-lookup"><span data-stu-id="e191a-111">When you remove a computer from a domain, `Remove-Computer` also disables the domain account of the computer.</span></span> <span data-ttu-id="e191a-112">Du måste ange explicita autentiseringsuppgifter för att kunna koppla från datorn från dess domän, även om de är autentiseringsuppgifterna för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="e191a-112">You must provide explicit credentials to unjoin the computer from its domain, even when they are the credentials of the current user.</span></span> <span data-ttu-id="e191a-113">Du måste starta om datorn för att ändringen ska börja gälla.</span><span class="sxs-lookup"><span data-stu-id="e191a-113">You must restart the computer to make the change effective.</span></span> <span data-ttu-id="e191a-114">När du tar bort en dator från en domän måste du också flytta den till en arbets grupp.</span><span class="sxs-lookup"><span data-stu-id="e191a-114">Also, when you remove a computer from a domain, you must move it to a workgroup.</span></span> <span data-ttu-id="e191a-115">Använd parametern **WorkgroupName** för att ange arbets gruppen.</span><span class="sxs-lookup"><span data-stu-id="e191a-115">Use the **WorkgroupName** parameter to specify the workgroup.</span></span>

<span data-ttu-id="e191a-116">Om du vill flytta en dator från en arbets grupp till en domän, från en arbets grupp till en annan, eller från en domän till en annan, använder du `Add-Computer` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e191a-116">To move a computer from a workgroup to a domain, from one workgroup to another, or from one domain to another, use the `Add-Computer` cmdlet.</span></span>

<span data-ttu-id="e191a-117">Om du vill hämta resultatet av kommandot använder du parametrarna **verbose** och **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="e191a-117">To get the results of the command, use the **Verbose** and **PassThru** parameters.</span></span> <span data-ttu-id="e191a-118">Använd **Force** -parametern för att utelämna användar frågan.</span><span class="sxs-lookup"><span data-stu-id="e191a-118">To suppress the user prompt, use the **Force** parameter.</span></span>

<span data-ttu-id="e191a-119">`Remove-Computer` tar bort den lokala datorn och fjärrdatorer från domäner.</span><span class="sxs-lookup"><span data-stu-id="e191a-119">`Remove-Computer` removes the local computer and remote computers from domains.</span></span> <span data-ttu-id="e191a-120">Den innehåller parametrar för autentiseringsuppgifter som anger alternativa autentiseringsuppgifter för att ansluta till fjärrdatorer och att koppla från en domän, en **omstarts** parameter för att starta om de berörda datorerna och en **WorkgroupName** -parameter för att ange namnet på arbets gruppen som datorer läggs till i.</span><span class="sxs-lookup"><span data-stu-id="e191a-120">It includes credential parameters that specify alternate credentials for connecting to remote computers, and unjoining from a domain, a **Restart** parameter for restarting the affected computers, and a **WorkgroupName** parameter for specifying the name of the workgroup to which computers are added.</span></span>

## <span data-ttu-id="e191a-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e191a-121">EXAMPLES</span></span>

### <span data-ttu-id="e191a-122">Exempel 1: ta bort den lokala datorn från dess domän</span><span class="sxs-lookup"><span data-stu-id="e191a-122">Example 1: Remove the local computer from its domain</span></span>

<span data-ttu-id="e191a-123">Det här exemplet tar bort den lokala datorn från den domän som den är ansluten till.</span><span class="sxs-lookup"><span data-stu-id="e191a-123">This example removes the local computer from the domain to which it is joined.</span></span>

```powershell
Remove-Computer -UnjoinDomaincredential Domain01\Admin01 -PassThru -Verbose -Restart
```

<span data-ttu-id="e191a-124">Parametern **UnjoinDomainCredential** innehåller autentiseringsuppgifterna för en domän administratör.</span><span class="sxs-lookup"><span data-stu-id="e191a-124">The **UnjoinDomainCredential** parameter provides the credentials of a domain administrator.</span></span> <span data-ttu-id="e191a-125">**Passthru** och de **utförliga** gemensamma parametrarna visar information om kommandot lyckades eller misslyckades.</span><span class="sxs-lookup"><span data-stu-id="e191a-125">The **PassThru** and the **Verbose** common parameters display information about the success or failure of the command.</span></span> <span data-ttu-id="e191a-126">Parametern **restart** startar om datorn för att slutföra borttagnings åtgärden.</span><span class="sxs-lookup"><span data-stu-id="e191a-126">The **Restart** parameter restarts the computer to complete the remove operation.</span></span>

<span data-ttu-id="e191a-127">När inget arbets grupps namn har angetts flyttas datorn till arbets gruppen med namnet när den har tagits bort från domänen.</span><span class="sxs-lookup"><span data-stu-id="e191a-127">When no workgroup name is specified, the computer is moved to the workgroup named after it is removed from its domain.</span></span>

### <span data-ttu-id="e191a-128">Exempel 2: flytta flera datorer till en äldre arbets grupp</span><span class="sxs-lookup"><span data-stu-id="e191a-128">Example 2: Move several computers to a legacy workgroup</span></span>

<span data-ttu-id="e191a-129">Det här exemplet tar bort alla datorer som listas i `OldServers.txt` filen från sina domäner och flyttar dem till den **äldre** arbets gruppen.</span><span class="sxs-lookup"><span data-stu-id="e191a-129">This example removes all the computers listed in the `OldServers.txt` file from their domains and moves them into the **Legacy** workgroup.</span></span>

```powershell
Remove-Computer -ComputerName (Get-Content OldServers.txt) -LocalCredential Domain01\Admin01 -UnJoinDomainCredential Domain01\Admin01 -WorkgroupName "Legacy" -Force -Restart
```

<span data-ttu-id="e191a-130">Parametern **LocalCredential** innehåller autentiseringsuppgifterna för en användare som har behörighet att ansluta till fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="e191a-130">The **LocalCredential** parameter provides the credentials of a user who has permission to connect to remote computers.</span></span> <span data-ttu-id="e191a-131">Parametern **UnjoinDomainCredential** innehåller autentiseringsuppgifterna för en användare som har behörighet att ta bort datorerna från sina domäner.</span><span class="sxs-lookup"><span data-stu-id="e191a-131">The **UnjoinDomainCredential** parameter provides the credentials of a user who has permission to remove the computers from their domains.</span></span> <span data-ttu-id="e191a-132">**Force** -parametern utelämnar bekräftelse frågorna för varje dator.</span><span class="sxs-lookup"><span data-stu-id="e191a-132">The **Force** parameter suppresses the confirmation prompts for each computer.</span></span> <span data-ttu-id="e191a-133">Parametern **restart** startar om var och en av datorerna när den har tagits bort från domänen.</span><span class="sxs-lookup"><span data-stu-id="e191a-133">The **Restart** parameter restarts each of the computers after it is removed from its domain.</span></span>

### <span data-ttu-id="e191a-134">Exempel 3: ta bort datorer från en arbets grupp utan bekräftelse</span><span class="sxs-lookup"><span data-stu-id="e191a-134">Example 3: Remove computers from a workgroup without confirmation</span></span>

<span data-ttu-id="e191a-135">Det här exemplet tar bort fjärrdatorn, Server01 och den lokala datorn från deras domäner och lägger till dem i den **lokala** arbets gruppen.</span><span class="sxs-lookup"><span data-stu-id="e191a-135">This example removes the remote computer, Server01, and the local computer from their domains and adds them to the **Local** workgroup.</span></span>

```powershell
Remove-Computer -ComputerName "Server01", "localhost" -UnjoinDomainCredential Domain01\Admin01 -WorkgroupName "Local" -Restart -Force
```

<span data-ttu-id="e191a-136">**Force** -parametern undertrycker bekräftelse frågan för varje dator.</span><span class="sxs-lookup"><span data-stu-id="e191a-136">The **Force** parameter suppresses the confirmation prompt for each computer.</span></span> <span data-ttu-id="e191a-137">Parametern **restart** startar om datorerna för att ändringen ska börja gälla.</span><span class="sxs-lookup"><span data-stu-id="e191a-137">The **Restart** parameter restarts the computers to make the change effective.</span></span>

## <span data-ttu-id="e191a-138">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e191a-138">PARAMETERS</span></span>

### <span data-ttu-id="e191a-139">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="e191a-139">-ComputerName</span></span>

<span data-ttu-id="e191a-140">Anger vilka datorer som ska tas bort från sina domäner.</span><span class="sxs-lookup"><span data-stu-id="e191a-140">Specifies the computers to be removed from their domains.</span></span> <span data-ttu-id="e191a-141">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e191a-141">The default is the local computer.</span></span>

<span data-ttu-id="e191a-142">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn (FQDN) för fjärrdatorerna.</span><span class="sxs-lookup"><span data-stu-id="e191a-142">Type the NetBIOS name, an IP address, or a fully qualified domain name (FQDN) of the remote computers.</span></span> <span data-ttu-id="e191a-143">Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller localhost.</span><span class="sxs-lookup"><span data-stu-id="e191a-143">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="e191a-144">Den här parametern är inte beroende av PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="e191a-144">This parameter does not rely on PowerShell remoting.</span></span> <span data-ttu-id="e191a-145">Du kan använda parametern **computername** för `Remove-Computer` även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="e191a-145">You can use the **ComputerName** parameter of `Remove-Computer` even if your computer is not configured to run remote commands.</span></span>

<span data-ttu-id="e191a-146">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e191a-146">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e191a-147">-Force</span><span class="sxs-lookup"><span data-stu-id="e191a-147">-Force</span></span>

<span data-ttu-id="e191a-148">Förhindrar att användaren tillfrågas.</span><span class="sxs-lookup"><span data-stu-id="e191a-148">Suppresses the user prompt.</span></span> <span data-ttu-id="e191a-149">Som standard `Remove-Computer` uppmanas du att bekräfta innan du tar bort varje dator.</span><span class="sxs-lookup"><span data-stu-id="e191a-149">By default, `Remove-Computer` prompts you for confirmation before removing each computer.</span></span>

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

### <span data-ttu-id="e191a-150">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="e191a-150">-LocalCredential</span></span>

<span data-ttu-id="e191a-151">Anger ett användar konto som har behörighet att ansluta till de datorer som parametern **computername** anger.</span><span class="sxs-lookup"><span data-stu-id="e191a-151">Specifies a user account that has permission to connect to the computers that the **ComputerName** parameter specifies.</span></span> <span data-ttu-id="e191a-152">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="e191a-152">The default is the current user.</span></span>

<span data-ttu-id="e191a-153">Ange ett användar namn, till exempel `User01` eller `Domain01\User01` , eller ange ett **PSCredential** -objekt, till exempel en som genereras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e191a-153">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="e191a-154">Om du anger ett användar namn, uppmanas du att ange ett lösen ord för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e191a-154">If you type a user name, the cmdlet prompts you for a password.</span></span> <span data-ttu-id="e191a-155">Använd parametern **UnjoinDomainCredential** om du vill ange ett användar konto som har behörighet att ta bort datorn från den aktuella domänen.</span><span class="sxs-lookup"><span data-stu-id="e191a-155">To specify a user account that has permission to remove the computer from its current domain, use the **UnjoinDomainCredential** parameter.</span></span>

<span data-ttu-id="e191a-156">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e191a-156">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e191a-157">– PassThru</span><span class="sxs-lookup"><span data-stu-id="e191a-157">-PassThru</span></span>

<span data-ttu-id="e191a-158">Returnerar kommandots resultat.</span><span class="sxs-lookup"><span data-stu-id="e191a-158">Returns the results of the command.</span></span> <span data-ttu-id="e191a-159">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="e191a-159">Otherwise, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="e191a-160">-Restart</span><span class="sxs-lookup"><span data-stu-id="e191a-160">-Restart</span></span>

<span data-ttu-id="e191a-161">Anger att den här cmdleten startar om de datorer som tas bort.</span><span class="sxs-lookup"><span data-stu-id="e191a-161">Indicates that this cmdlet restarts the computers that are being removed.</span></span> <span data-ttu-id="e191a-162">En omstart krävs ofta för att ändringen ska börja gälla.</span><span class="sxs-lookup"><span data-stu-id="e191a-162">A restart is often required to make the change effective.</span></span>

<span data-ttu-id="e191a-163">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e191a-163">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="e191a-164">-UnjoinDomainCredential</span><span class="sxs-lookup"><span data-stu-id="e191a-164">-UnjoinDomainCredential</span></span>

<span data-ttu-id="e191a-165">Anger ett användar konto som har behörighet att ta bort datorerna från deras aktuella domäner.</span><span class="sxs-lookup"><span data-stu-id="e191a-165">Specifies a user account that has permission to remove the computers from their current domains.</span></span>
<span data-ttu-id="e191a-166">Explicita autentiseringsuppgifter som anges i den här parametern krävs för att ta bort fjärrdatorer från en domän, även om värdet är den aktuella användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="e191a-166">Explicit credentials, as provided by this parameter, are required to remove remote computers from a domain, even when the value is the credentials of the current user.</span></span>

<span data-ttu-id="e191a-167">Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, t. ex. ett som genereras av `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="e191a-167">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by `Get-Credential`.</span></span> <span data-ttu-id="e191a-168">Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e191a-168">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="e191a-169">Använd parametern **LocalCredential** för att ange ett användar konto som har behörighet att ansluta till fjärrdatorerna.</span><span class="sxs-lookup"><span data-stu-id="e191a-169">To specify a user account that has permission to connect to the remote computers, use the **LocalCredential** parameter.</span></span>

<span data-ttu-id="e191a-170">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e191a-170">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Local, Remote
Aliases: Credential

Required: False (Local), True (Remote)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e191a-171">-WorkgroupName</span><span class="sxs-lookup"><span data-stu-id="e191a-171">-WorkgroupName</span></span>

<span data-ttu-id="e191a-172">Anger namnet på en arbets grupp som datorerna läggs till i när de tas bort från deras domäner.</span><span class="sxs-lookup"><span data-stu-id="e191a-172">Specifies the name of a workgroup to which the computers are added when they are removed from their domains.</span></span> <span data-ttu-id="e191a-173">Standardvärdet är **Workgroup**.</span><span class="sxs-lookup"><span data-stu-id="e191a-173">The default value is **WORKGROUP**.</span></span> <span data-ttu-id="e191a-174">När du tar bort en dator från en domän måste du lägga till den i en arbets grupp.</span><span class="sxs-lookup"><span data-stu-id="e191a-174">When you remove a computer from a domain, you must add it to a workgroup.</span></span>

<span data-ttu-id="e191a-175">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e191a-175">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e191a-176">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e191a-176">-Confirm</span></span>

<span data-ttu-id="e191a-177">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e191a-177">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e191a-178">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e191a-178">-WhatIf</span></span>

<span data-ttu-id="e191a-179">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="e191a-179">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="e191a-180">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="e191a-180">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e191a-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e191a-181">CommonParameters</span></span>

<span data-ttu-id="e191a-182">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e191a-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e191a-183">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e191a-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e191a-184">INDATA</span><span class="sxs-lookup"><span data-stu-id="e191a-184">INPUTS</span></span>

### <span data-ttu-id="e191a-185">System. String</span><span class="sxs-lookup"><span data-stu-id="e191a-185">System.String</span></span>

<span data-ttu-id="e191a-186">Du kan skicka pipe-dator namn till thiscmdlet.</span><span class="sxs-lookup"><span data-stu-id="e191a-186">You can pipe computer names to thiscmdlet.</span></span>

## <span data-ttu-id="e191a-187">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e191a-187">OUTPUTS</span></span>

### <span data-ttu-id="e191a-188">Microsoft. PowerShell. commands. ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="e191a-188">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="e191a-189">När du använder parametern **Passthru** `Remove-Computer` returnerar ett **ComputerChangeInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="e191a-189">When you use the **PassThru** parameter, `Remove-Computer` returns a **ComputerChangeInfo** object.</span></span>
<span data-ttu-id="e191a-190">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="e191a-190">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e191a-191">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e191a-191">NOTES</span></span>

<span data-ttu-id="e191a-192">Den här cmdleten tar inte bort datorer från arbets grupper.</span><span class="sxs-lookup"><span data-stu-id="e191a-192">This cmdlet does not remove computers from workgroups.</span></span>

## <span data-ttu-id="e191a-193">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e191a-193">RELATED LINKS</span></span>

[<span data-ttu-id="e191a-194">Lägg till dator</span><span class="sxs-lookup"><span data-stu-id="e191a-194">Add-Computer</span></span>](Add-Computer.md)

[<span data-ttu-id="e191a-195">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="e191a-195">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="e191a-196">Ta bort dator</span><span class="sxs-lookup"><span data-stu-id="e191a-196">Remove-Computer</span></span>](Remove-Computer.md)

[<span data-ttu-id="e191a-197">Byt namn – dator</span><span class="sxs-lookup"><span data-stu-id="e191a-197">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="e191a-198">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="e191a-198">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="e191a-199">Återställa-dator</span><span class="sxs-lookup"><span data-stu-id="e191a-199">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="e191a-200">Stoppa – dator</span><span class="sxs-lookup"><span data-stu-id="e191a-200">Stop-Computer</span></span>](Stop-Computer.md)

[<span data-ttu-id="e191a-201">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="e191a-201">Test-Connection</span></span>](Test-Connection.md)
