---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: c6aa8a16bd5ccbeb00252b872e997018b1997181
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346708"
---
# <span data-ttu-id="a462f-103">Set-Service</span><span class="sxs-lookup"><span data-stu-id="a462f-103">Set-Service</span></span>

## <span data-ttu-id="a462f-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a462f-104">SYNOPSIS</span></span>
<span data-ttu-id="a462f-105">Startar, stoppar och pausar en tjänst och ändrar dess egenskaper.</span><span class="sxs-lookup"><span data-stu-id="a462f-105">Starts, stops, and suspends a service, and changes its properties.</span></span>

## <span data-ttu-id="a462f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a462f-106">SYNTAX</span></span>

### <span data-ttu-id="a462f-107">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="a462f-107">Name (Default)</span></span>

```
Set-Service [-Name] <String> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-Status <String>]
 [-SecurityDescriptorSddl <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a462f-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="a462f-108">InputObject</span></span>

```
Set-Service [-InputObject] <ServiceController> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-SecurityDescriptorSddl <String>]
 [-Status <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a462f-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a462f-109">DESCRIPTION</span></span>

<span data-ttu-id="a462f-110">`Set-Service`Cmdleten ändrar egenskaperna för en tjänst, till exempel **status** , **Beskrivning** , **DisplayName** och **startuptype tjänst**.</span><span class="sxs-lookup"><span data-stu-id="a462f-110">The `Set-Service` cmdlet changes the properties of a service such as the **Status** , **Description** , **DisplayName** , and **StartupType**.</span></span> <span data-ttu-id="a462f-111">`Set-Service` kan starta, stoppa, pausa eller pausa en tjänst.</span><span class="sxs-lookup"><span data-stu-id="a462f-111">`Set-Service` can start, stop, suspend, or pause a service.</span></span> <span data-ttu-id="a462f-112">För att identifiera en tjänst anger du dess tjänst namn eller skickar ett tjänst objekt.</span><span class="sxs-lookup"><span data-stu-id="a462f-112">To identify a service, enter its service name or submit a service object.</span></span> <span data-ttu-id="a462f-113">Eller skicka ett tjänst namn eller tjänst objekt nedåt i pipeline till `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="a462f-113">Or, send a service name or service object down the pipeline to `Set-Service`.</span></span>

## <span data-ttu-id="a462f-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a462f-114">EXAMPLES</span></span>

### <span data-ttu-id="a462f-115">Exempel 1: ändra ett visnings namn</span><span class="sxs-lookup"><span data-stu-id="a462f-115">Example 1: Change a display name</span></span>

<span data-ttu-id="a462f-116">I det här exemplet ändras en tjänsts visnings namn.</span><span class="sxs-lookup"><span data-stu-id="a462f-116">In this example, a service's display name is changed.</span></span> <span data-ttu-id="a462f-117">Använd om du vill visa det ursprungliga visnings namnet `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="a462f-117">To view the original display name, use `Get-Service`.</span></span>

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

<span data-ttu-id="a462f-118">`Set-Service` använder **Name** -parametern för att ange tjänstens namn, **LanmanWorkstation**.</span><span class="sxs-lookup"><span data-stu-id="a462f-118">`Set-Service` uses the **Name** parameter to specify the service's name, **LanmanWorkstation**.</span></span> <span data-ttu-id="a462f-119">Parametern **DisplayName** anger det nya visnings namnet, **LANMAN-arbetsstationen**.</span><span class="sxs-lookup"><span data-stu-id="a462f-119">The **DisplayName** parameter specifies the new display name, **LanMan Workstation**.</span></span>

### <span data-ttu-id="a462f-120">Exempel 2: ändra start typen för tjänster</span><span class="sxs-lookup"><span data-stu-id="a462f-120">Example 2: Change the startup type of services</span></span>

<span data-ttu-id="a462f-121">Det här exemplet visar hur du ändrar Start typen för en tjänst.</span><span class="sxs-lookup"><span data-stu-id="a462f-121">This example shows how to change a service's startup type.</span></span>

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

<span data-ttu-id="a462f-122">`Set-Service` använder **Name** -parametern för att ange tjänstens namn, **bitar**.</span><span class="sxs-lookup"><span data-stu-id="a462f-122">`Set-Service` uses the **Name** parameter to specify the service's name, **BITS**.</span></span> <span data-ttu-id="a462f-123">Parametern **startuptype tjänst** anger att tjänsten ska vara **Automatisk**.</span><span class="sxs-lookup"><span data-stu-id="a462f-123">The **StartupType** parameter sets the service to **Automatic**.</span></span>

<span data-ttu-id="a462f-124">`Get-Service` använder **Name** -parametern för att ange **BITS** -tjänsten och skickar objektet nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a462f-124">`Get-Service` uses the **Name** parameter to specify the **BITS** service and sends the object down the pipeline.</span></span> <span data-ttu-id="a462f-125">`Select-Object` använder **egenskaps** parametern för att visa **BITS** -tjänstens status.</span><span class="sxs-lookup"><span data-stu-id="a462f-125">`Select-Object` uses the **Property** parameter to display the **BITS** service's status.</span></span>

### <span data-ttu-id="a462f-126">Exempel 3: ändra beskrivningen av en tjänst</span><span class="sxs-lookup"><span data-stu-id="a462f-126">Example 3: Change the description of a service</span></span>

<span data-ttu-id="a462f-127">Det här exemplet ändrar beskrivningen av BITS-tjänsten och visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="a462f-127">This example changes the BITS service's description and displays the result.</span></span>

<span data-ttu-id="a462f-128">`Get-CimInstance`Cmdleten används eftersom den returnerar ett **Win32_Service** -objekt som innehåller tjänstens **Beskrivning**.</span><span class="sxs-lookup"><span data-stu-id="a462f-128">The `Get-CimInstance` cmdlet is used because it returns a **Win32_Service** object that includes the service's **Description**.</span></span>

```powershell
Get-CimInstance Win32_Service -Filter 'Name = "BITS"'  | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth. If the service is
              disabled, then any applications that depend on BITS, such as Windows Update or MSN
              Explorer, will be unable to automatically download programs and other information.
```

```powershell
Set-Service -Name BITS -Description "Transfers files in the background using idle network bandwidth."
Get-CimInstance Win32_Service -Filter 'Name = "BITS"' | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth.
```

<span data-ttu-id="a462f-129">`Get-CimInstance` skickar objektet nedåt i pipeline till `Format-List` och visar tjänstens namn och beskrivning.</span><span class="sxs-lookup"><span data-stu-id="a462f-129">`Get-CimInstance` sends the object down the pipeline to `Format-List` and displays the service's name and description.</span></span> <span data-ttu-id="a462f-130">I jämförelse syfte körs kommandot före och efter att beskrivningen har uppdaterats.</span><span class="sxs-lookup"><span data-stu-id="a462f-130">For comparison purposes, the command is run before and after the description is updated.</span></span>

<span data-ttu-id="a462f-131">`Set-Service` använder **Name** -parametern för att ange **BITS** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a462f-131">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="a462f-132">Parametern **Description** anger den uppdaterade texten för beskrivningen av tjänsterna.</span><span class="sxs-lookup"><span data-stu-id="a462f-132">The **Description** parameter specifies the updated text for the services' description.</span></span>

### <span data-ttu-id="a462f-133">Exempel 4: starta en tjänst</span><span class="sxs-lookup"><span data-stu-id="a462f-133">Example 4: Start a service</span></span>

<span data-ttu-id="a462f-134">I det här exemplet startas en tjänst.</span><span class="sxs-lookup"><span data-stu-id="a462f-134">In this example, a service is started.</span></span>

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

<span data-ttu-id="a462f-135">`Set-Service` använder parametern **Name** för att ange tjänsten, **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="a462f-135">`Set-Service` uses the **Name** parameter to specify the service, **WinRM**.</span></span> <span data-ttu-id="a462f-136">**Status** parametern använder det värde som **körs** för att starta tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a462f-136">The **Status** parameter uses the value **Running** to start the service.</span></span> <span data-ttu-id="a462f-137">**Passthru** -parametern matar ut ett **ServiceController** -objekt som visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="a462f-137">The **PassThru** parameter outputs a **ServiceController** object that displays the results.</span></span>

### <span data-ttu-id="a462f-138">Exempel 5: inaktivera en tjänst</span><span class="sxs-lookup"><span data-stu-id="a462f-138">Example 5: Suspend a service</span></span>

<span data-ttu-id="a462f-139">I det här exemplet används pipelinen för att pausa tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a462f-139">This example uses the pipeline to pause to service.</span></span>

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

<span data-ttu-id="a462f-140">`Get-Service` använder **Name** -parametern för att ange **schema** tjänsten och skickar objektet nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a462f-140">`Get-Service` uses the **Name** parameter to specify the **Schedule** service, and sends the object down the pipeline.</span></span> <span data-ttu-id="a462f-141">`Set-Service` använder **status** parametern för att ange att tjänsten ska **pausas**.</span><span class="sxs-lookup"><span data-stu-id="a462f-141">`Set-Service` uses the **Status** parameter to set the service to **Paused**.</span></span>

### <span data-ttu-id="a462f-142">Exempel 6: stoppa en tjänst</span><span class="sxs-lookup"><span data-stu-id="a462f-142">Example 6: Stop a service</span></span>

<span data-ttu-id="a462f-143">I det här exemplet används en variabel för att stoppa en tjänst.</span><span class="sxs-lookup"><span data-stu-id="a462f-143">This example uses a variable to stop a service.</span></span>

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

<span data-ttu-id="a462f-144">`Get-Service` använder **Name** -parametern för att ange tjänsten, **schema**.</span><span class="sxs-lookup"><span data-stu-id="a462f-144">`Get-Service` uses the **Name** parameter to specify the service, **Schedule**.</span></span> <span data-ttu-id="a462f-145">Objektet lagras i variabeln `$S` .</span><span class="sxs-lookup"><span data-stu-id="a462f-145">The object is stored in the variable, `$S`.</span></span> <span data-ttu-id="a462f-146">`Set-Service` använder parametern **InputObject** och anger objektet som lagras `$S` .</span><span class="sxs-lookup"><span data-stu-id="a462f-146">`Set-Service` uses the **InputObject** parameter and specifies the object stored `$S`.</span></span> <span data-ttu-id="a462f-147">**Status** parametern anger att tjänsten har **stoppats**.</span><span class="sxs-lookup"><span data-stu-id="a462f-147">The **Status** parameter sets the service to **Stopped**.</span></span>

### <span data-ttu-id="a462f-148">Exempel 7: stoppa en tjänst på ett fjärrsystem</span><span class="sxs-lookup"><span data-stu-id="a462f-148">Example 7: Stop a service on a remote system</span></span>

<span data-ttu-id="a462f-149">I det här exemplet stoppas en tjänst på en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="a462f-149">This example stops a service on a remote computer.</span></span>
<span data-ttu-id="a462f-150">Mer information finns i [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="a462f-150">For more information, see [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```powershell
$Cred = Get-Credential
$S = Get-Service -Name Schedule
Invoke-Command -ComputerName server01.contoso.com -Credential $Cred -ScriptBlock {
  Set-Service -InputObject $S -Status Stopped
}
```

<span data-ttu-id="a462f-151">`Get-Credential` efterfrågar ett användar namn och lösen ord och lagrar autentiseringsuppgifterna i `$Cred` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a462f-151">`Get-Credential` prompts for a username and password, and stores the credentials in the `$Cred` variable.</span></span> <span data-ttu-id="a462f-152">`Get-Service` använder **Name** -parametern för att ange tjänsten **Schedule** .</span><span class="sxs-lookup"><span data-stu-id="a462f-152">`Get-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="a462f-153">Objektet lagras i variabeln `$S` .</span><span class="sxs-lookup"><span data-stu-id="a462f-153">The object is stored in the variable, `$S`.</span></span>

<span data-ttu-id="a462f-154">`Invoke-Command` använder parametern **computername** för att ange en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="a462f-154">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer.</span></span> <span data-ttu-id="a462f-155">Parametern **Credential** använder `$Cred` variabeln för att logga in på datorn.</span><span class="sxs-lookup"><span data-stu-id="a462f-155">The **Credential** parameter uses the `$Cred` variable to sign on to the computer.</span></span> <span data-ttu-id="a462f-156">**Script block** -anrop `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="a462f-156">The **ScriptBlock** calls `Set-Service`.</span></span> <span data-ttu-id="a462f-157">Parametern **InputObject** anger det tjänst objekt som lagras `$S` .</span><span class="sxs-lookup"><span data-stu-id="a462f-157">The **InputObject** parameter specifies the service object stored `$S`.</span></span> <span data-ttu-id="a462f-158">**Status** parametern anger att tjänsten har **stoppats**.</span><span class="sxs-lookup"><span data-stu-id="a462f-158">The **Status** parameter sets the service to **Stopped**.</span></span>

### <span data-ttu-id="a462f-159">Exempel 8: ändra autentiseringsuppgifter för en tjänst</span><span class="sxs-lookup"><span data-stu-id="a462f-159">Example 8: Change credential of a service</span></span>

<span data-ttu-id="a462f-160">Det här exemplet ändrar de autentiseringsuppgifter som används för att hantera en tjänst.</span><span class="sxs-lookup"><span data-stu-id="a462f-160">This example changes the credentials that are used to manage a service.</span></span>

```powershell
$credential = Get-Credential
Set-Service -Name Schedule -Credential $credential
```

<span data-ttu-id="a462f-161">`Get-Credential` efterfrågar ett användar namn och lösen ord och lagrar autentiseringsuppgifterna i `$credential` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a462f-161">`Get-Credential` prompts for a username and password, and stores the credentials in the `$credential` variable.</span></span> <span data-ttu-id="a462f-162">`Set-Service` använder **Name** -parametern för att ange tjänsten **Schedule** .</span><span class="sxs-lookup"><span data-stu-id="a462f-162">`Set-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="a462f-163">Parametern **Credential** använder `$credential` variabeln och uppdaterar tjänsten **schema** .</span><span class="sxs-lookup"><span data-stu-id="a462f-163">The **Credential** parameter uses the `$credential` variable and updates the **Schedule** service.</span></span>

### <span data-ttu-id="a462f-164">Exempel 9: ändra adtagent för en tjänst</span><span class="sxs-lookup"><span data-stu-id="a462f-164">Example 9: Change the SecurityDescriptor of a service</span></span>

<span data-ttu-id="a462f-165">Det här exemplet ändrar en tjänsts **adtagent**.</span><span class="sxs-lookup"><span data-stu-id="a462f-165">This example changes a service's **SecurityDescriptor**.</span></span>

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
Set-Service -Name "BITS" -SecurityDescriptorSddl $SDDL
```

<span data-ttu-id="a462f-166">**Adtagent** lagras i `$SDDL` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a462f-166">The **SecurityDescriptor** is stored in the `$SDDL` variable.</span></span> <span data-ttu-id="a462f-167">`Set-Service` använder **Name** -parametern för att ange **BITS** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a462f-167">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="a462f-168">Parametern **SecurityDescriptorSddl** använder `$SDDL` för att ändra **adtagent** för **BITS** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a462f-168">The **SecurityDescriptorSddl** parameter uses `$SDDL` to change the **SecurityDescriptor** for the **BITS** service.</span></span>

## <span data-ttu-id="a462f-169">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a462f-169">PARAMETERS</span></span>

### <span data-ttu-id="a462f-170">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a462f-170">-Confirm</span></span>

<span data-ttu-id="a462f-171">Du uppmanas att bekräfta innan du kör `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="a462f-171">Prompts you for confirmation before running `Set-Service`.</span></span>

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

### <span data-ttu-id="a462f-172">-Credential</span><span class="sxs-lookup"><span data-stu-id="a462f-172">-Credential</span></span>

<span data-ttu-id="a462f-173">Anger kontot som används av tjänsten som [tjänst inloggnings konto](/windows/desktop/ad/about-service-logon-accounts).</span><span class="sxs-lookup"><span data-stu-id="a462f-173">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="a462f-174">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a462f-174">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="a462f-175">Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a462f-175">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="a462f-176">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="a462f-176">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="a462f-177">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="a462f-177">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

<span data-ttu-id="a462f-178">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="a462f-178">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="a462f-179">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a462f-179">-Description</span></span>

<span data-ttu-id="a462f-180">Anger en ny Beskrivning av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a462f-180">Specifies a new description for the service.</span></span>

<span data-ttu-id="a462f-181">Tjänst beskrivningen visas i **dator hantering, tjänster**.</span><span class="sxs-lookup"><span data-stu-id="a462f-181">The service description appears in **Computer Management, Services**.</span></span> <span data-ttu-id="a462f-182">**Beskrivningen** är inte en egenskap för `Get-Service` **ServiceController** -objektet.</span><span class="sxs-lookup"><span data-stu-id="a462f-182">The **Description** isn't a property of the `Get-Service` **ServiceController** object.</span></span> <span data-ttu-id="a462f-183">Om du vill se tjänst beskrivningen använder du `Get-CimInstance` som returnerar ett **Win32_Service** -objekt som representerar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a462f-183">To see the service description, use `Get-CimInstance` that returns a **Win32_Service** object that represents the service.</span></span>

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

### <span data-ttu-id="a462f-184">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="a462f-184">-DisplayName</span></span>

<span data-ttu-id="a462f-185">Anger ett nytt visnings namn för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a462f-185">Specifies a new display name for the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: DN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a462f-186">-Force</span><span class="sxs-lookup"><span data-stu-id="a462f-186">-Force</span></span>

<span data-ttu-id="a462f-187">Anger tjänstens stopp läge.</span><span class="sxs-lookup"><span data-stu-id="a462f-187">Specifies the Stop mode of the service.</span></span> <span data-ttu-id="a462f-188">Den här parametern fungerar bara när `-Status Stopped` används.</span><span class="sxs-lookup"><span data-stu-id="a462f-188">This parameter only works when `-Status Stopped` is used.</span></span> <span data-ttu-id="a462f-189">Om aktive rad stoppas `Set-Service` de beroende tjänsterna innan mål tjänsten stoppas.</span><span class="sxs-lookup"><span data-stu-id="a462f-189">If enabled, `Set-Service` stops the dependent services before the target service is stopped.</span></span> <span data-ttu-id="a462f-190">Som standard höjs undantag när andra tjänster som körs är beroende av mål tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a462f-190">By default, exceptions are raised when other running services depend on the target service.</span></span>

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

### <span data-ttu-id="a462f-191">– InputObject</span><span class="sxs-lookup"><span data-stu-id="a462f-191">-InputObject</span></span>

<span data-ttu-id="a462f-192">Anger ett **ServiceController** -objekt som representerar den tjänst som ska ändras.</span><span class="sxs-lookup"><span data-stu-id="a462f-192">Specifies a **ServiceController** object that represents the service to change.</span></span> <span data-ttu-id="a462f-193">Ange en variabel som innehåller objektet eller Skriv ett kommando eller uttryck som hämtar objektet, till exempel ett `Get-Service` kommando.</span><span class="sxs-lookup"><span data-stu-id="a462f-193">Enter a variable that contains the object, or type a command or expression that gets the object, such as a `Get-Service` command.</span></span> <span data-ttu-id="a462f-194">Du kan använda pipelinen för att skicka ett tjänst objekt till `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="a462f-194">You can use the pipeline to send a service object to `Set-Service`.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a462f-195">-Name</span><span class="sxs-lookup"><span data-stu-id="a462f-195">-Name</span></span>

<span data-ttu-id="a462f-196">Anger tjänst namnet på den tjänst som ska ändras.</span><span class="sxs-lookup"><span data-stu-id="a462f-196">Specifies the service name of the service to be changed.</span></span> <span data-ttu-id="a462f-197">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a462f-197">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="a462f-198">Du kan använda pipelinen för att skicka ett tjänst namn till `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="a462f-198">You can use the pipeline to send a service name to `Set-Service`.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a462f-199">– PassThru</span><span class="sxs-lookup"><span data-stu-id="a462f-199">-PassThru</span></span>

<span data-ttu-id="a462f-200">Returnerar ett **ServiceController** -objekt som representerar de tjänster som har ändrats.</span><span class="sxs-lookup"><span data-stu-id="a462f-200">Returns a **ServiceController** object that represents the services that were changed.</span></span> <span data-ttu-id="a462f-201">Som standard `Set-Service` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="a462f-201">By default, `Set-Service` doesn't generate any output.</span></span>

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

### <span data-ttu-id="a462f-202">– Startuptype tjänst</span><span class="sxs-lookup"><span data-stu-id="a462f-202">-StartupType</span></span>

<span data-ttu-id="a462f-203">Anger tjänstens start läge.</span><span class="sxs-lookup"><span data-stu-id="a462f-203">Specifies the start mode of the service.</span></span>

<span data-ttu-id="a462f-204">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="a462f-204">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="a462f-205">**Automatiskt** – tjänsten startas eller startades av operativ systemet vid system start.</span><span class="sxs-lookup"><span data-stu-id="a462f-205">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="a462f-206">Om en automatiskt startad tjänst är beroende av en manuellt startad tjänst startas automatiskt den manuellt startade tjänsten automatiskt vid system start.</span><span class="sxs-lookup"><span data-stu-id="a462f-206">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="a462f-207">**AutomaticDelayedStart** – startar strax efter att systemet har startat.</span><span class="sxs-lookup"><span data-stu-id="a462f-207">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="a462f-208">**Disabled** – tjänsten är inaktive rad och kan inte startas av en användare eller ett program.</span><span class="sxs-lookup"><span data-stu-id="a462f-208">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="a462f-209">**InvalidValue** – har ingen inverkan.</span><span class="sxs-lookup"><span data-stu-id="a462f-209">**InvalidValue** - Has no effect.</span></span> <span data-ttu-id="a462f-210">Cmdleten returnerar inte ett fel, men Startuptype tjänst för tjänsten har inte ändrats.</span><span class="sxs-lookup"><span data-stu-id="a462f-210">The cmdlet does not return an error but the StartupType of the service is not changed.</span></span>
- <span data-ttu-id="a462f-211">**Manuell** – tjänsten startas endast manuellt, av en användare, med hjälp av tjänst hanteraren eller av ett program.</span><span class="sxs-lookup"><span data-stu-id="a462f-211">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases: StartMode, SM, ST, StartType
Accepted values: Automatic, AutomaticDelayedStart, Disabled, InvalidValue, Manual

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a462f-212">-Status</span><span class="sxs-lookup"><span data-stu-id="a462f-212">-Status</span></span>

<span data-ttu-id="a462f-213">Anger tjänstens status.</span><span class="sxs-lookup"><span data-stu-id="a462f-213">Specifies the status for the service.</span></span>

<span data-ttu-id="a462f-214">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="a462f-214">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="a462f-215">**Pausat**.</span><span class="sxs-lookup"><span data-stu-id="a462f-215">**Paused**.</span></span> <span data-ttu-id="a462f-216">Pausar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a462f-216">Suspends the service.</span></span>
- <span data-ttu-id="a462f-217">**Körs**.</span><span class="sxs-lookup"><span data-stu-id="a462f-217">**Running**.</span></span> <span data-ttu-id="a462f-218">Startar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a462f-218">Starts the service.</span></span>
- <span data-ttu-id="a462f-219">**Stoppades**.</span><span class="sxs-lookup"><span data-stu-id="a462f-219">**Stopped**.</span></span> <span data-ttu-id="a462f-220">Stoppar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a462f-220">Stops the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Paused, Running, Stopped

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a462f-221">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="a462f-221">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="a462f-222">Anger **adtagent** för tjänsten i **SDDL** -format.</span><span class="sxs-lookup"><span data-stu-id="a462f-222">Specifies the **SecurityDescriptor** for the service in **Sddl** format.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sd

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a462f-223">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a462f-223">-WhatIf</span></span>

<span data-ttu-id="a462f-224">Visar vad som händer om `Set-Service` körs.</span><span class="sxs-lookup"><span data-stu-id="a462f-224">Shows what would happen if `Set-Service` runs.</span></span> <span data-ttu-id="a462f-225">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="a462f-225">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="a462f-226">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a462f-226">CommonParameters</span></span>

<span data-ttu-id="a462f-227">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a462f-227">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a462f-228">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a462f-228">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a462f-229">INDATA</span><span class="sxs-lookup"><span data-stu-id="a462f-229">INPUTS</span></span>

### <span data-ttu-id="a462f-230">System. ServiceProcess. ServiceController, system. String</span><span class="sxs-lookup"><span data-stu-id="a462f-230">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="a462f-231">Du kan använda pipelinen för att skicka ett tjänst objekt eller en sträng som innehåller ett tjänst namn till `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="a462f-231">You can use the pipeline to send a service object or a string that contains a service name to `Set-Service`.</span></span>

## <span data-ttu-id="a462f-232">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a462f-232">OUTPUTS</span></span>

### <span data-ttu-id="a462f-233">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="a462f-233">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="a462f-234">Som standard `Set-Service` returnerar inte några objekt.</span><span class="sxs-lookup"><span data-stu-id="a462f-234">By default, `Set-Service` doesn't return any objects.</span></span> <span data-ttu-id="a462f-235">Använd parametern **Passthru** för att mata ut ett **ServiceController** -objekt.</span><span class="sxs-lookup"><span data-stu-id="a462f-235">Use the **PassThru** parameter to output a **ServiceController** object.</span></span>

## <span data-ttu-id="a462f-236">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a462f-236">NOTES</span></span>

<span data-ttu-id="a462f-237">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="a462f-237">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="a462f-238">`Set-Service` kräver förhöjd behörighet.</span><span class="sxs-lookup"><span data-stu-id="a462f-238">`Set-Service` requires elevated permissions.</span></span> <span data-ttu-id="a462f-239">Använd alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="a462f-239">Use the **Run as administrator** option.</span></span>

<span data-ttu-id="a462f-240">`Set-Service` Det går bara att kontrol lera tjänster när den aktuella användaren har behörighet att hantera tjänster.</span><span class="sxs-lookup"><span data-stu-id="a462f-240">`Set-Service` can only control services when the current user has permissions to manage services.</span></span> <span data-ttu-id="a462f-241">Om ett kommando inte fungerar som det ska kanske du inte har de behörigheter som krävs.</span><span class="sxs-lookup"><span data-stu-id="a462f-241">If a command doesn't work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="a462f-242">Använd om du vill hitta tjänstens namn eller visnings namn för tjänsten `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="a462f-242">To find a service's service name or display name, use `Get-Service`.</span></span> <span data-ttu-id="a462f-243">Tjänst namnen finns i kolumnen **namn** och visnings namnen är i kolumnen **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="a462f-243">The service names are in the **Name** column and the display names are in the **DisplayName** column.</span></span>

## <span data-ttu-id="a462f-244">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a462f-244">RELATED LINKS</span></span>

[<span data-ttu-id="a462f-245">Get-Service</span><span class="sxs-lookup"><span data-stu-id="a462f-245">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="a462f-246">New-Service</span><span class="sxs-lookup"><span data-stu-id="a462f-246">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="a462f-247">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="a462f-247">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="a462f-248">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="a462f-248">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="a462f-249">Start-Service</span><span class="sxs-lookup"><span data-stu-id="a462f-249">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="a462f-250">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="a462f-250">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="a462f-251">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="a462f-251">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="a462f-252">Remove-service</span><span class="sxs-lookup"><span data-stu-id="a462f-252">Remove-Service</span></span>](Remove-Service.md)
