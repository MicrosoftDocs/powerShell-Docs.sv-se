---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: f6d31980e27b73e884b46168606ab8255a64efb9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708379"
---
# <span data-ttu-id="84681-102">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="84681-102">Stop-Computer</span></span>

## <span data-ttu-id="84681-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="84681-103">SYNOPSIS</span></span>
<span data-ttu-id="84681-104">Stoppar (stänger av) lokala och fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="84681-104">Stops (shuts down) local and remote computers.</span></span>

## <span data-ttu-id="84681-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="84681-105">SYNTAX</span></span>

### <span data-ttu-id="84681-106">Alla</span><span class="sxs-lookup"><span data-stu-id="84681-106">All</span></span>

```
Stop-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="84681-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="84681-107">DESCRIPTION</span></span>

<span data-ttu-id="84681-108">`Stop-Computer`Cmdleten stänger av den lokala datorn och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="84681-108">The `Stop-Computer` cmdlet shuts down the local computer and remote computers.</span></span>

<span data-ttu-id="84681-109">Du kan använda parametrarna för `Stop-Computer` för att ange autentiseringsnivåer och alternativa autentiseringsuppgifter och för att framtvinga en omedelbar avstängning.</span><span class="sxs-lookup"><span data-stu-id="84681-109">You can use the parameters of `Stop-Computer` to specify the authentication levels and alternate credentials, and to force an immediate shut down.</span></span>

<span data-ttu-id="84681-110">I PowerShell 7,1 `Stop-Computer` lades till för Linux och MacOS.</span><span class="sxs-lookup"><span data-stu-id="84681-110">In PowerShell 7.1, `Stop-Computer` was added for Linux and macOS.</span></span> <span data-ttu-id="84681-111">Parametrarna har ingen påverkan på dessa plattformar.</span><span class="sxs-lookup"><span data-stu-id="84681-111">The parameters have no effect on these platforms.</span></span> <span data-ttu-id="84681-112">Cmdleten anropar bara det ursprungliga kommandot `/sbin/shutdown` .</span><span class="sxs-lookup"><span data-stu-id="84681-112">The cmdlet is just calling the native command `/sbin/shutdown`.</span></span>

## <span data-ttu-id="84681-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="84681-113">EXAMPLES</span></span>

### <span data-ttu-id="84681-114">Exempel 1: Stäng av den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="84681-114">Example 1: Shut down the local computer</span></span>

<span data-ttu-id="84681-115">I det här exemplet stängs den lokala datorn av.</span><span class="sxs-lookup"><span data-stu-id="84681-115">This example shuts down the local computer.</span></span>

```powershell
Stop-Computer -ComputerName localhost
```

### <span data-ttu-id="84681-116">Exempel 2: Stäng av två fjärranslutna datorer och den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="84681-116">Example 2: Shut down two remote computers and the local computer</span></span>

<span data-ttu-id="84681-117">I det här exemplet stoppas två fjärranslutna datorer och den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="84681-117">This example stops two remote computers and the local computer.</span></span>

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="84681-118">`Stop-Computer` använder parametern **computername** för att ange två fjärranslutna datorer och den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="84681-118">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers and the local computer.</span></span> <span data-ttu-id="84681-119">Varje dator stängs av.</span><span class="sxs-lookup"><span data-stu-id="84681-119">Each computer is shut down.</span></span>

### <span data-ttu-id="84681-120">Exempel 3: Stäng av fjärrdatorer som bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="84681-120">Example 3: Shut down remote computers as a background job</span></span>

<span data-ttu-id="84681-121">I det här exemplet `Stop-Computer` körs som ett bakgrunds jobb på två fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="84681-121">In this example, `Stop-Computer` runs as a background job on two remote computers.</span></span>

<span data-ttu-id="84681-122">Bakgrunds operatorn `&` kör `Stop-Computer` kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="84681-122">The background operator `&` runs the `Stop-Computer` command as a background job.</span></span> <span data-ttu-id="84681-123">Mer information finns i [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-).</span><span class="sxs-lookup"><span data-stu-id="84681-123">For more information, see [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-).</span></span>

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" &
$results = $j | Receive-Job
$results
```

<span data-ttu-id="84681-124">`Stop-Computer` använder parametern **computername** för att ange två fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="84681-124">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers.</span></span> <span data-ttu-id="84681-125">`&`Bakgrunds operatorn kör kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="84681-125">The `&` background operator runs the command as a background job.</span></span> <span data-ttu-id="84681-126">Jobb objekten lagras i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="84681-126">The job objects are stored in the `$j` variable.</span></span>

<span data-ttu-id="84681-127">Jobb objekt i `$j` variabeln skickas ned till pipelinen till `Receive-Job` , som hämtar jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="84681-127">The job objects in the `$j` variable are sent down the pipeline to `Receive-Job`, which gets the job results.</span></span> <span data-ttu-id="84681-128">Objekten lagras i `$results` variabeln.</span><span class="sxs-lookup"><span data-stu-id="84681-128">The objects are stored in the `$results` variable.</span></span> <span data-ttu-id="84681-129">`$results`Variabeln visar jobb informationen i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="84681-129">The `$results` variable displays the job information in the PowerShell console.</span></span>

### <span data-ttu-id="84681-130">Exempel 4: Stäng av en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="84681-130">Example 4: Shut down a remote computer</span></span>

<span data-ttu-id="84681-131">I det här exemplet stängs en fjärrdator med angiven autentisering.</span><span class="sxs-lookup"><span data-stu-id="84681-131">This example shuts down a remote computer using specified authentication.</span></span>

```powershell
Stop-Computer -ComputerName "Server01" -WsmanAuthentication Kerberos
```

<span data-ttu-id="84681-132">`Stop-Computer` använder parametern **computername** för att ange fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="84681-132">`Stop-Computer` uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="84681-133">Parametern **WsmanAuthentication** anger att Kerberos ska användas för att upprätta en fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="84681-133">The **WsmanAuthentication** parameter specifies to use Kerberos to establish a remote connection.</span></span>

### <span data-ttu-id="84681-134">Exempel 5: Stäng av datorer i en domän</span><span class="sxs-lookup"><span data-stu-id="84681-134">Example 5: Shut down computers in a domain</span></span>

<span data-ttu-id="84681-135">I det här exemplet tvingar kommandon en omedelbar avstängning av alla datorer i en angiven domän.</span><span class="sxs-lookup"><span data-stu-id="84681-135">In this example, the commands force an immediate shut down of all computers in a specified domain.</span></span>

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -Credential $c
```

<span data-ttu-id="84681-136">`Get-Content` använder parametern **Path** för att hämta en fil i den aktuella katalogen med listan över domän datorer.</span><span class="sxs-lookup"><span data-stu-id="84681-136">`Get-Content` uses the **Path** parameter to get a file in the current directory with the list of domain computers.</span></span> <span data-ttu-id="84681-137">Objekten lagras i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="84681-137">The objects are stored in the `$s` variable.</span></span>

<span data-ttu-id="84681-138">`Get-Credential` använder parametern **Credential** för att ange autentiseringsuppgifter för en domän administratör.</span><span class="sxs-lookup"><span data-stu-id="84681-138">`Get-Credential` uses the **Credential** parameter to specify the credentials of a domain administrator.</span></span> <span data-ttu-id="84681-139">Autentiseringsuppgifterna lagras i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="84681-139">The credentials are stored in the `$c` variable.</span></span>

<span data-ttu-id="84681-140">`Stop-Computer` stänger av datorerna som anges med parametern **computername** i listan över datorer i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="84681-140">`Stop-Computer` shuts down the computers specified with the **ComputerName** parameter's list of computers in the `$s` variable.</span></span> <span data-ttu-id="84681-141">**Force** -parametern tvingar en omedelbar avstängning.</span><span class="sxs-lookup"><span data-stu-id="84681-141">The **Force** parameter forces an immediate shutdown.</span></span> <span data-ttu-id="84681-142">Parametern **Credential** skickar de autentiseringsuppgifter som sparats i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="84681-142">The **Credential** parameter submits the credentials saved in the `$c` variable.</span></span>

## <span data-ttu-id="84681-143">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="84681-143">PARAMETERS</span></span>

### <span data-ttu-id="84681-144">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="84681-144">-ComputerName</span></span>

<span data-ttu-id="84681-145">Anger vilka datorer som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="84681-145">Specifies the computers to stop.</span></span> <span data-ttu-id="84681-146">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="84681-146">The default is the local computer.</span></span>

<span data-ttu-id="84681-147">Ange NETBIOS-namn, IP-adress eller fullständigt kvalificerat domän namn för en eller flera datorer i en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="84681-147">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="84681-148">Om du vill ange den lokala datorn skriver du datorns namn eller localhost.</span><span class="sxs-lookup"><span data-stu-id="84681-148">To specify the local computer, type the computer name or localhost.</span></span>

<span data-ttu-id="84681-149">Den här parametern är inte beroende av PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="84681-149">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="84681-150">Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="84681-150">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

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

### <span data-ttu-id="84681-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="84681-151">-Confirm</span></span>

<span data-ttu-id="84681-152">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="84681-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="84681-153">-Credential</span><span class="sxs-lookup"><span data-stu-id="84681-153">-Credential</span></span>

<span data-ttu-id="84681-154">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="84681-154">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="84681-155">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="84681-155">The default is the current user.</span></span>

<span data-ttu-id="84681-156">Ange ett användar namn, till exempel **user01** eller **Domain01\User01**, eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="84681-156">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="84681-157">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="84681-157">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="84681-158">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="84681-158">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="84681-159">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="84681-159">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="84681-160">-Force</span><span class="sxs-lookup"><span data-stu-id="84681-160">-Force</span></span>

<span data-ttu-id="84681-161">Tvingar fram en omedelbar avstängning av datorn.</span><span class="sxs-lookup"><span data-stu-id="84681-161">Forces an immediate shut down of the computer.</span></span>

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

### <span data-ttu-id="84681-162">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="84681-162">-WsmanAuthentication</span></span>

<span data-ttu-id="84681-163">Anger den mekanism som används för att autentisera användarautentiseringsuppgifter när denna cmdlet använder WSMan-protokollet.</span><span class="sxs-lookup"><span data-stu-id="84681-163">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="84681-164">Standardvärdet är **default**.</span><span class="sxs-lookup"><span data-stu-id="84681-164">The default value is **Default**.</span></span>

<span data-ttu-id="84681-165">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="84681-165">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="84681-166">Grundläggande</span><span class="sxs-lookup"><span data-stu-id="84681-166">Basic</span></span>
- <span data-ttu-id="84681-167">CredSSP</span><span class="sxs-lookup"><span data-stu-id="84681-167">CredSSP</span></span>
- <span data-ttu-id="84681-168">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="84681-168">Default</span></span>
- <span data-ttu-id="84681-169">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="84681-169">Digest</span></span>
- <span data-ttu-id="84681-170">Kerberos</span><span class="sxs-lookup"><span data-stu-id="84681-170">Kerberos</span></span>
- <span data-ttu-id="84681-171">Fram.</span><span class="sxs-lookup"><span data-stu-id="84681-171">Negotiate.</span></span>

<span data-ttu-id="84681-172">Mer information om värdena för den här parametern finns i [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="84681-172">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="84681-173">Autentisering av Credential Security Service Provider (CredSSP), där användarautentiseringsuppgifterna skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="84681-173">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="84681-174">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="84681-174">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="84681-175">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="84681-175">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="84681-176">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="84681-176">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="84681-177">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="84681-177">-WhatIf</span></span>

<span data-ttu-id="84681-178">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="84681-178">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="84681-179">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="84681-179">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="84681-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="84681-180">CommonParameters</span></span>

<span data-ttu-id="84681-181">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="84681-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="84681-182">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="84681-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="84681-183">INDATA</span><span class="sxs-lookup"><span data-stu-id="84681-183">INPUTS</span></span>

### <span data-ttu-id="84681-184">Inga</span><span class="sxs-lookup"><span data-stu-id="84681-184">None</span></span>

<span data-ttu-id="84681-185">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="84681-185">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="84681-186">UTDATA</span><span class="sxs-lookup"><span data-stu-id="84681-186">OUTPUTS</span></span>

### <span data-ttu-id="84681-187">Inga</span><span class="sxs-lookup"><span data-stu-id="84681-187">None</span></span>

## <span data-ttu-id="84681-188">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="84681-188">NOTES</span></span>

<span data-ttu-id="84681-189">Denna cmdlet använder metoden **Win32Shutdown** i klassen **Win32_OperatingSystem** WMI.</span><span class="sxs-lookup"><span data-stu-id="84681-189">This cmdlet uses the **Win32Shutdown** method of the **Win32_OperatingSystem** WMI class.</span></span> <span data-ttu-id="84681-190">Den här metoden kräver att **SeShutdownPrivilege** -behörighet aktive ras för det användar konto som används för att starta om datorn.</span><span class="sxs-lookup"><span data-stu-id="84681-190">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

<span data-ttu-id="84681-191">I PowerShell 7,1 `Stop-Computer` lades till för Linux och MacOS.</span><span class="sxs-lookup"><span data-stu-id="84681-191">In PowerShell 7.1, `Stop-Computer` was added for Linux and macOS.</span></span> <span data-ttu-id="84681-192">För dessa platorms anropar cmdleten det inbyggda kommandot `/sbin/shutdown` .</span><span class="sxs-lookup"><span data-stu-id="84681-192">For these platorms, the cmdlet calls the native command `/sbin/shutdown`.</span></span>

## <span data-ttu-id="84681-193">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="84681-193">RELATED LINKS</span></span>

[<span data-ttu-id="84681-194">Byt namn – dator</span><span class="sxs-lookup"><span data-stu-id="84681-194">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="84681-195">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="84681-195">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="84681-196">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="84681-196">Test-Connection</span></span>](Test-Connection.md)

