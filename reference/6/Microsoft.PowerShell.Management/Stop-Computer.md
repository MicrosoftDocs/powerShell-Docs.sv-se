---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: e7732c1eb243c0a4737c3f08a413fd20bbf2bf38
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268496"
---
# <span data-ttu-id="eec0c-103">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="eec0c-103">Stop-Computer</span></span>

## <span data-ttu-id="eec0c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="eec0c-104">SYNOPSIS</span></span>
<span data-ttu-id="eec0c-105">Stoppar (stänger av) lokala och fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="eec0c-105">Stops (shuts down) local and remote computers.</span></span>

## <span data-ttu-id="eec0c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="eec0c-106">SYNTAX</span></span>

### <span data-ttu-id="eec0c-107">Alla</span><span class="sxs-lookup"><span data-stu-id="eec0c-107">All</span></span>

```
Stop-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="eec0c-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="eec0c-108">DESCRIPTION</span></span>

<span data-ttu-id="eec0c-109">`Stop-Computer`Cmdleten stänger av den lokala datorn och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="eec0c-109">The `Stop-Computer` cmdlet shuts down the local computer and remote computers.</span></span>

<span data-ttu-id="eec0c-110">Du kan använda parametrarna för `Stop-Computer` för att ange autentiseringsnivåer och alternativa autentiseringsuppgifter och för att framtvinga en omedelbar avstängning.</span><span class="sxs-lookup"><span data-stu-id="eec0c-110">You can use the parameters of `Stop-Computer` to specify the authentication levels and alternate credentials, and to force an immediate shut down.</span></span>

## <span data-ttu-id="eec0c-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="eec0c-111">EXAMPLES</span></span>

### <span data-ttu-id="eec0c-112">Exempel 1: Stäng av den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="eec0c-112">Example 1: Shut down the local computer</span></span>

<span data-ttu-id="eec0c-113">I det här exemplet stängs den lokala datorn av.</span><span class="sxs-lookup"><span data-stu-id="eec0c-113">This example shuts down the local computer.</span></span>

```powershell
Stop-Computer -ComputerName localhost
```

### <span data-ttu-id="eec0c-114">Exempel 2: Stäng av två fjärranslutna datorer och den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="eec0c-114">Example 2: Shut down two remote computers and the local computer</span></span>

<span data-ttu-id="eec0c-115">I det här exemplet stoppas två fjärranslutna datorer och den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="eec0c-115">This example stops two remote computers and the local computer.</span></span>

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="eec0c-116">`Stop-Computer` använder parametern **computername** för att ange två fjärranslutna datorer och den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="eec0c-116">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers and the local computer.</span></span> <span data-ttu-id="eec0c-117">Varje dator stängs av.</span><span class="sxs-lookup"><span data-stu-id="eec0c-117">Each computer is shut down.</span></span>

### <span data-ttu-id="eec0c-118">Exempel 3: Stäng av fjärrdatorer som bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="eec0c-118">Example 3: Shut down remote computers as a background job</span></span>

<span data-ttu-id="eec0c-119">I det här exemplet `Stop-Computer` körs som ett bakgrunds jobb på två fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="eec0c-119">In this example, `Stop-Computer` runs as a background job on two remote computers.</span></span>

<span data-ttu-id="eec0c-120">Bakgrunds operatorn `&` kör `Stop-Computer` kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="eec0c-120">The background operator `&` runs the `Stop-Computer` command as a background job.</span></span> <span data-ttu-id="eec0c-121">Mer information finns i [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-).</span><span class="sxs-lookup"><span data-stu-id="eec0c-121">For more information, see [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-).</span></span>

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" &
$results = $j | Receive-Job
$results
```

<span data-ttu-id="eec0c-122">`Stop-Computer` använder parametern **computername** för att ange två fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="eec0c-122">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers.</span></span> <span data-ttu-id="eec0c-123">`&`Bakgrunds operatorn kör kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="eec0c-123">The `&` background operator runs the command as a background job.</span></span> <span data-ttu-id="eec0c-124">Jobb objekten lagras i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="eec0c-124">The job objects are stored in the `$j` variable.</span></span>

<span data-ttu-id="eec0c-125">Jobb objekt i `$j` variabeln skickas ned till pipelinen till `Receive-Job` , som hämtar jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="eec0c-125">The job objects in the `$j` variable are sent down the pipeline to `Receive-Job`, which gets the job results.</span></span> <span data-ttu-id="eec0c-126">Objekten lagras i `$results` variabeln.</span><span class="sxs-lookup"><span data-stu-id="eec0c-126">The objects are stored in the `$results` variable.</span></span> <span data-ttu-id="eec0c-127">`$results`Variabeln visar jobb informationen i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="eec0c-127">The `$results` variable displays the job information in the PowerShell console.</span></span>

### <span data-ttu-id="eec0c-128">Exempel 4: Stäng av en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="eec0c-128">Example 4: Shut down a remote computer</span></span>

<span data-ttu-id="eec0c-129">I det här exemplet stängs en fjärrdator med angiven autentisering.</span><span class="sxs-lookup"><span data-stu-id="eec0c-129">This example shuts down a remote computer using specified authentication.</span></span>

```powershell
Stop-Computer -ComputerName "Server01" -WsmanAuthentication Kerberos
```

<span data-ttu-id="eec0c-130">`Stop-Computer` använder parametern **computername** för att ange fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="eec0c-130">`Stop-Computer` uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="eec0c-131">Parametern **WsmanAuthentication** anger att Kerberos ska användas för att upprätta en fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="eec0c-131">The **WsmanAuthentication** parameter specifies to use Kerberos to establish a remote connection.</span></span>

### <span data-ttu-id="eec0c-132">Exempel 5: Stäng av datorer i en domän</span><span class="sxs-lookup"><span data-stu-id="eec0c-132">Example 5: Shut down computers in a domain</span></span>

<span data-ttu-id="eec0c-133">I det här exemplet tvingar kommandon en omedelbar avstängning av alla datorer i en angiven domän.</span><span class="sxs-lookup"><span data-stu-id="eec0c-133">In this example, the commands force an immediate shut down of all computers in a specified domain.</span></span>

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -Credential $c
```

<span data-ttu-id="eec0c-134">`Get-Content` använder parametern **Path** för att hämta en fil i den aktuella katalogen med listan över domän datorer.</span><span class="sxs-lookup"><span data-stu-id="eec0c-134">`Get-Content` uses the **Path** parameter to get a file in the current directory with the list of domain computers.</span></span> <span data-ttu-id="eec0c-135">Objekten lagras i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="eec0c-135">The objects are stored in the `$s` variable.</span></span>

<span data-ttu-id="eec0c-136">`Get-Credential` använder parametern **Credential** för att ange autentiseringsuppgifter för en domän administratör.</span><span class="sxs-lookup"><span data-stu-id="eec0c-136">`Get-Credential` uses the **Credential** parameter to specify the credentials of a domain administrator.</span></span> <span data-ttu-id="eec0c-137">Autentiseringsuppgifterna lagras i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="eec0c-137">The credentials are stored in the `$c` variable.</span></span>

<span data-ttu-id="eec0c-138">`Stop-Computer` stänger av datorerna som anges med parametern **computername** i listan över datorer i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="eec0c-138">`Stop-Computer` shuts down the computers specified with the **ComputerName** parameter's list of computers in the `$s` variable.</span></span> <span data-ttu-id="eec0c-139">**Force** -parametern tvingar en omedelbar avstängning.</span><span class="sxs-lookup"><span data-stu-id="eec0c-139">The **Force** parameter forces an immediate shutdown.</span></span> <span data-ttu-id="eec0c-140">Parametern **Credential** skickar de autentiseringsuppgifter som sparats i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="eec0c-140">The **Credential** parameter submits the credentials saved in the `$c` variable.</span></span>

## <span data-ttu-id="eec0c-141">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="eec0c-141">PARAMETERS</span></span>

### <span data-ttu-id="eec0c-142">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="eec0c-142">-ComputerName</span></span>

<span data-ttu-id="eec0c-143">Anger vilka datorer som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="eec0c-143">Specifies the computers to stop.</span></span> <span data-ttu-id="eec0c-144">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="eec0c-144">The default is the local computer.</span></span>

<span data-ttu-id="eec0c-145">Ange NETBIOS-namn, IP-adress eller fullständigt kvalificerat domän namn för en eller flera datorer i en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="eec0c-145">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="eec0c-146">Om du vill ange den lokala datorn skriver du datorns namn eller localhost.</span><span class="sxs-lookup"><span data-stu-id="eec0c-146">To specify the local computer, type the computer name or localhost.</span></span>

<span data-ttu-id="eec0c-147">Den här parametern är inte beroende av PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="eec0c-147">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="eec0c-148">Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="eec0c-148">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="eec0c-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="eec0c-149">-Confirm</span></span>

<span data-ttu-id="eec0c-150">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eec0c-150">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="eec0c-151">-Credential</span><span class="sxs-lookup"><span data-stu-id="eec0c-151">-Credential</span></span>

<span data-ttu-id="eec0c-152">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="eec0c-152">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="eec0c-153">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="eec0c-153">The default is the current user.</span></span>

<span data-ttu-id="eec0c-154">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eec0c-154">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="eec0c-155">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="eec0c-155">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="eec0c-156">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="eec0c-156">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="eec0c-157">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="eec0c-157">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eec0c-158">-Force</span><span class="sxs-lookup"><span data-stu-id="eec0c-158">-Force</span></span>

<span data-ttu-id="eec0c-159">Tvingar fram en omedelbar avstängning av datorn.</span><span class="sxs-lookup"><span data-stu-id="eec0c-159">Forces an immediate shut down of the computer.</span></span>

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

### <span data-ttu-id="eec0c-160">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="eec0c-160">-WsmanAuthentication</span></span>

<span data-ttu-id="eec0c-161">Anger den mekanism som används för att autentisera användarautentiseringsuppgifter när denna cmdlet använder WSMan-protokollet.</span><span class="sxs-lookup"><span data-stu-id="eec0c-161">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="eec0c-162">Standardvärdet är **default**.</span><span class="sxs-lookup"><span data-stu-id="eec0c-162">The default value is **Default**.</span></span>

<span data-ttu-id="eec0c-163">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="eec0c-163">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="eec0c-164">Basic</span><span class="sxs-lookup"><span data-stu-id="eec0c-164">Basic</span></span>
- <span data-ttu-id="eec0c-165">CredSSP</span><span class="sxs-lookup"><span data-stu-id="eec0c-165">CredSSP</span></span>
- <span data-ttu-id="eec0c-166">Default</span><span class="sxs-lookup"><span data-stu-id="eec0c-166">Default</span></span>
- <span data-ttu-id="eec0c-167">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="eec0c-167">Digest</span></span>
- <span data-ttu-id="eec0c-168">Kerberos</span><span class="sxs-lookup"><span data-stu-id="eec0c-168">Kerberos</span></span>
- <span data-ttu-id="eec0c-169">Fram.</span><span class="sxs-lookup"><span data-stu-id="eec0c-169">Negotiate.</span></span>

<span data-ttu-id="eec0c-170">Mer information om värdena för den här parametern finns i [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="eec0c-170">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="eec0c-171">Autentisering av Credential Security Service Provider (CredSSP), där användarautentiseringsuppgifterna skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="eec0c-171">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="eec0c-172">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="eec0c-172">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="eec0c-173">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="eec0c-173">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="eec0c-174">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="eec0c-174">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eec0c-175">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="eec0c-175">-WhatIf</span></span>

<span data-ttu-id="eec0c-176">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="eec0c-176">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="eec0c-177">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="eec0c-177">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="eec0c-178">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eec0c-178">CommonParameters</span></span>

<span data-ttu-id="eec0c-179">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="eec0c-179">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eec0c-180">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="eec0c-180">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="eec0c-181">INDATA</span><span class="sxs-lookup"><span data-stu-id="eec0c-181">INPUTS</span></span>

### <span data-ttu-id="eec0c-182">Inget</span><span class="sxs-lookup"><span data-stu-id="eec0c-182">None</span></span>

<span data-ttu-id="eec0c-183">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eec0c-183">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="eec0c-184">UTDATA</span><span class="sxs-lookup"><span data-stu-id="eec0c-184">OUTPUTS</span></span>

### <span data-ttu-id="eec0c-185">Inget</span><span class="sxs-lookup"><span data-stu-id="eec0c-185">None</span></span>

## <span data-ttu-id="eec0c-186">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="eec0c-186">NOTES</span></span>

<span data-ttu-id="eec0c-187">Den här cmdleten fungerar bara på Windows och använder **Win32Shutdown** -metoden i **Win32_OperatingSystem** WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="eec0c-187">This cmdlet only works on Windows and uses the **Win32Shutdown** method of the **Win32_OperatingSystem** WMI class.</span></span> <span data-ttu-id="eec0c-188">Den här metoden kräver att **SeShutdownPrivilege** -behörighet aktive ras för det användar konto som används för att starta om datorn.</span><span class="sxs-lookup"><span data-stu-id="eec0c-188">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

## <span data-ttu-id="eec0c-189">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="eec0c-189">RELATED LINKS</span></span>

[<span data-ttu-id="eec0c-190">Byt namn – dator</span><span class="sxs-lookup"><span data-stu-id="eec0c-190">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="eec0c-191">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="eec0c-191">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="eec0c-192">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="eec0c-192">Test-Connection</span></span>](Test-Connection.md)
