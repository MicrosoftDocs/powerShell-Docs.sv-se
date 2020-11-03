---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-computersecurechannel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ComputerSecureChannel
ms.openlocfilehash: 20ea76e725a8ab53d7090078dc819a6297a639ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265323"
---
# <span data-ttu-id="c8ab2-103">Test-ComputerSecureChannel</span><span class="sxs-lookup"><span data-stu-id="c8ab2-103">Test-ComputerSecureChannel</span></span>

## <span data-ttu-id="c8ab2-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c8ab2-104">SYNOPSIS</span></span>
<span data-ttu-id="c8ab2-105">Testar och reparerar den säkra kanalen mellan den lokala datorn och dess domän.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-105">Tests and repairs the secure channel between the local computer and its domain.</span></span>

## <span data-ttu-id="c8ab2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c8ab2-106">SYNTAX</span></span>

```
Test-ComputerSecureChannel [-Repair] [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="c8ab2-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c8ab2-107">DESCRIPTION</span></span>
<span data-ttu-id="c8ab2-108">Cmdleten **test-ComputerSecureChannel** verifierar att kanalen mellan den lokala datorn och dess domän fungerar som den ska genom att kontrol lera status för dess förtroende relationer.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-108">The **Test-ComputerSecureChannel** cmdlet verifies that the channel between the local computer and its domain is working correctly by checking the status of its trust relationships.</span></span>
<span data-ttu-id="c8ab2-109">Om anslutningen Miss lyckas kan du använda *reparations* parametern för att försöka återställa den.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-109">If a connection fails, you can use the *Repair* parameter to try to restore it.</span></span>

<span data-ttu-id="c8ab2-110">**Test-ComputerSecureChannel** returnerar $true om kanalen fungerar korrekt och $false om den inte är det.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-110">**Test-ComputerSecureChannel** returns $True if the channel is working correctly and $False if it is not.</span></span>
<span data-ttu-id="c8ab2-111">Detta innebär att du kan använda-cmdleten i villkorliga uttryck i funktioner och skript.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-111">This result lets you use the cmdlet in conditional statements in functions and scripts.</span></span>
<span data-ttu-id="c8ab2-112">Använd *verbose* -parametern för att få mer detaljerade test resultat.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-112">To get more detailed test results, use the *Verbose* parameter.</span></span>

<span data-ttu-id="c8ab2-113">Denna cmdlet fungerar ungefär som NetDom.exe.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-113">This cmdlet works much like NetDom.exe.</span></span>
<span data-ttu-id="c8ab2-114">Både NetDom och **test-ComputerSecureChannel** använder tjänsten **Netlogon** för att utföra åtgärderna.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-114">Both NetDom and **Test-ComputerSecureChannel** use the **NetLogon** service to perform the actions.</span></span>

## <span data-ttu-id="c8ab2-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c8ab2-115">EXAMPLES</span></span>

### <span data-ttu-id="c8ab2-116">Exempel 1: testa en kanal mellan den lokala datorn och dess domän</span><span class="sxs-lookup"><span data-stu-id="c8ab2-116">Example 1: Test a channel between the local computer and its domain</span></span>

```
PS C:\> Test-ComputerSecureChannel
True
```

<span data-ttu-id="c8ab2-117">Det här kommandot testar kanalen mellan den lokala datorn och den domän som den är ansluten till.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-117">This command tests the channel between the local computer and the domain to which it is joined.</span></span>

### <span data-ttu-id="c8ab2-118">Exempel 2: testa en kanal mellan den lokala datorn och en domänkontrollant</span><span class="sxs-lookup"><span data-stu-id="c8ab2-118">Example 2: Test a channel between the local computer and a domain controller</span></span>

```
PS C:\> Test-ComputerSecureChannel -Server "DCName.fabrikam.com"
True
```

<span data-ttu-id="c8ab2-119">Det här kommandot anger en prioriterad domänkontrollant för testet.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-119">This command specifies a preferred domain controller for the test.</span></span>

### <span data-ttu-id="c8ab2-120">Exempel 3: återställa kanalen mellan den lokala datorn och dess domän</span><span class="sxs-lookup"><span data-stu-id="c8ab2-120">Example 3: Reset the channel between the local computer and its domain</span></span>

```
PS C:\> Test-ComputerSecureChannel -Repair
True
```

<span data-ttu-id="c8ab2-121">Det här kommandot återställer kanalen mellan den lokala datorn och dess domän.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-121">This command resets the channel between the local computer and its domain.</span></span>

### <span data-ttu-id="c8ab2-122">Exempel 4: Visa detaljerad information om testet</span><span class="sxs-lookup"><span data-stu-id="c8ab2-122">Example 4: Display detailed information about the test</span></span>

```
PS C:\> Test-ComputerSecureChannel -verbose
VERBOSE: Performing operation "Test-ComputerSecureChannel" on Target "SERVER01".
True
VERBOSE: "The secure channel between 'SERVER01' and 'net.fabrikam.com' is alive and working correctly."
```

<span data-ttu-id="c8ab2-123">Detta kommando använder den *utförliga* gemensamma parametern för att begära detaljerade meddelanden om åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-123">This command uses the *Verbose* common parameter to request detailed messages about the operation.</span></span>
<span data-ttu-id="c8ab2-124">Mer information om *verbose* finns about_CommonParameters.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-124">For more information about *Verbose* , see about_CommonParameters.</span></span>

### <span data-ttu-id="c8ab2-125">Exempel 5: testa en anslutning innan du kör ett skript</span><span class="sxs-lookup"><span data-stu-id="c8ab2-125">Example 5: Test a connection before you run a script</span></span>

```
PS C:\> Set-Alias tcsc Test-ComputerSecureChannel
if (!(tcsc))
{Write-Host "Connection failed. Reconnect and retry."}
else { &(.\Get-Servers.ps1) }
```

<span data-ttu-id="c8ab2-126">Det här exemplet visar hur du använder **test-ComputerSecureChannel** för att testa en anslutning innan du kör ett skript som kräver anslutningen.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-126">This example shows how to use **Test-ComputerSecureChannel** to test a connection before you run a script that requires the connection.</span></span>

<span data-ttu-id="c8ab2-127">Det första kommandot använder cmdleten Set-Alias för att skapa ett alias för cmdlet-namnet.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-127">The first command uses the Set-Alias cmdlet to create an alias for the cmdlet name.</span></span>
<span data-ttu-id="c8ab2-128">Detta sparar utrymme och förhindrar skrivfel.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-128">This saves space and prevents typing errors.</span></span>

<span data-ttu-id="c8ab2-129">Instruktionen **IF** kontrollerar värdet som **test-ComputerSecureChannel** returnerar innan ett skript körs.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-129">The **If** statement checks the value that **Test-ComputerSecureChannel** returns before it runs a script.</span></span>

## <span data-ttu-id="c8ab2-130">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c8ab2-130">PARAMETERS</span></span>

### <span data-ttu-id="c8ab2-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="c8ab2-131">-Credential</span></span>
<span data-ttu-id="c8ab2-132">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-132">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="c8ab2-133">Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, till exempel ett som Get-Credential cmdlet returnerar.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-133">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one that the Get-Credential cmdlet returns.</span></span>
<span data-ttu-id="c8ab2-134">Som standard använder cmdleten autentiseringsuppgifterna för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-134">By default, the cmdlet uses the credentials of the current user.</span></span>

<span data-ttu-id="c8ab2-135">Parametern *Credential* är utformad för att användas i kommandon som använder *Repair* -parametern för att reparera kanalen mellan datorn och domänen.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-135">The *Credential* parameter is designed for use in commands that use the *Repair* parameter to repair the channel between the computer and the domain.</span></span>

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

### <span data-ttu-id="c8ab2-136">-Reparera</span><span class="sxs-lookup"><span data-stu-id="c8ab2-136">-Repair</span></span>
<span data-ttu-id="c8ab2-137">Anger att den här cmdleten tar bort och sedan återupprättar kanalen som upprättats av tjänsten NetLogon.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-137">Indicates that this cmdlet removes and then rebuilds the channel established by the NetLogon service.</span></span>
<span data-ttu-id="c8ab2-138">Använd den här parametern om du vill försöka återställa en anslutning som har misslyckats med testet.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-138">Use this parameter to try to restore a connection that has failed the test.</span></span>

<span data-ttu-id="c8ab2-139">Om du vill använda den här parametern måste den aktuella användaren vara medlem i gruppen Administratörer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-139">To use this parameter, the current user must be a member of the Administrators group on the local computer.</span></span>

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

### <span data-ttu-id="c8ab2-140">-Server</span><span class="sxs-lookup"><span data-stu-id="c8ab2-140">-Server</span></span>
<span data-ttu-id="c8ab2-141">Anger den domänkontrollant som ska köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-141">Specifies the domain controller to run the command.</span></span>
<span data-ttu-id="c8ab2-142">Om den här parametern inte anges, väljer denna cmdlet en Standarddomänkontrollant för åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-142">If this parameter is not specified, this cmdlet selects a default domain controller for the operation.</span></span>

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

### <span data-ttu-id="c8ab2-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c8ab2-143">-Confirm</span></span>
<span data-ttu-id="c8ab2-144">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-144">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c8ab2-145">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c8ab2-145">-WhatIf</span></span>
<span data-ttu-id="c8ab2-146">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-146">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c8ab2-147">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-147">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c8ab2-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c8ab2-148">CommonParameters</span></span>
<span data-ttu-id="c8ab2-149">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c8ab2-150">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c8ab2-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c8ab2-151">INDATA</span><span class="sxs-lookup"><span data-stu-id="c8ab2-151">INPUTS</span></span>

### <span data-ttu-id="c8ab2-152">Inget</span><span class="sxs-lookup"><span data-stu-id="c8ab2-152">None</span></span>
<span data-ttu-id="c8ab2-153">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-153">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c8ab2-154">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c8ab2-154">OUTPUTS</span></span>

### <span data-ttu-id="c8ab2-155">System. Boolean</span><span class="sxs-lookup"><span data-stu-id="c8ab2-155">System.Boolean</span></span>
<span data-ttu-id="c8ab2-156">Den här cmdleten returnerar $True om anslutningen fungerar korrekt och $False om den inte är det.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-156">This cmdlet returns $True if the connection is working correctly and $False if it is not.</span></span>

## <span data-ttu-id="c8ab2-157">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c8ab2-157">NOTES</span></span>

* <span data-ttu-id="c8ab2-158">Om du vill köra ett **test-ComputerSecureChannel** kommando i Windows Vista och senare versioner av Windows operativ system öppnar du Windows PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-158">To run a **Test-ComputerSecureChannel** command on Windows Vista and later versions of the Windows operating system, open Windows PowerShell by using the Run as administrator option.</span></span>
* <span data-ttu-id="c8ab2-159">**Test-ComputerSecureChannel** implementeras med hjälp av funktionen **I_NetLogonControl2** som styr olika aspekter av tjänsten Netlogon.</span><span class="sxs-lookup"><span data-stu-id="c8ab2-159">**Test-ComputerSecureChannel** is implemented by using the **I_NetLogonControl2** function, which controls various aspects of the Netlogon service.</span></span>

## <span data-ttu-id="c8ab2-160">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c8ab2-160">RELATED LINKS</span></span>

[<span data-ttu-id="c8ab2-161">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="c8ab2-161">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="c8ab2-162">Återställ-ComputerMachinePassword</span><span class="sxs-lookup"><span data-stu-id="c8ab2-162">Reset-ComputerMachinePassword</span></span>](Reset-ComputerMachinePassword.md)

[<span data-ttu-id="c8ab2-163">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="c8ab2-163">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="c8ab2-164">Stoppa – dator</span><span class="sxs-lookup"><span data-stu-id="c8ab2-164">Stop-Computer</span></span>](Stop-Computer.md)
