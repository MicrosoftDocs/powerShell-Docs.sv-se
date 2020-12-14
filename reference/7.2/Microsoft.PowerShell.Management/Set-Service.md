---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: 0c6cac03f1acbda35069780f0c53eaf6685813ff
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710393"
---
# <span data-ttu-id="4543c-102">Set-Service</span><span class="sxs-lookup"><span data-stu-id="4543c-102">Set-Service</span></span>

## <span data-ttu-id="4543c-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4543c-103">SYNOPSIS</span></span>
<span data-ttu-id="4543c-104">Startar, stoppar och pausar en tjänst och ändrar dess egenskaper.</span><span class="sxs-lookup"><span data-stu-id="4543c-104">Starts, stops, and suspends a service, and changes its properties.</span></span>

## <span data-ttu-id="4543c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4543c-105">SYNTAX</span></span>

### <span data-ttu-id="4543c-106">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="4543c-106">Name (Default)</span></span>

```
Set-Service [-Name] <String> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-Status <String>]
 [-SecurityDescriptorSddl <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4543c-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="4543c-107">InputObject</span></span>

```
Set-Service [-InputObject] <ServiceController> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-SecurityDescriptorSddl <String>]
 [-Status <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4543c-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4543c-108">DESCRIPTION</span></span>

<span data-ttu-id="4543c-109">`Set-Service`Cmdleten ändrar egenskaperna för en tjänst, till exempel **status**, **Beskrivning**, **DisplayName** och **startuptype tjänst**.</span><span class="sxs-lookup"><span data-stu-id="4543c-109">The `Set-Service` cmdlet changes the properties of a service such as the **Status**, **Description**, **DisplayName**, and **StartupType**.</span></span> <span data-ttu-id="4543c-110">`Set-Service` kan starta, stoppa, pausa eller pausa en tjänst.</span><span class="sxs-lookup"><span data-stu-id="4543c-110">`Set-Service` can start, stop, suspend, or pause a service.</span></span> <span data-ttu-id="4543c-111">För att identifiera en tjänst anger du dess tjänst namn eller skickar ett tjänst objekt.</span><span class="sxs-lookup"><span data-stu-id="4543c-111">To identify a service, enter its service name or submit a service object.</span></span> <span data-ttu-id="4543c-112">Eller skicka ett tjänst namn eller tjänst objekt nedåt i pipeline till `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="4543c-112">Or, send a service name or service object down the pipeline to `Set-Service`.</span></span>

## <span data-ttu-id="4543c-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4543c-113">EXAMPLES</span></span>

### <span data-ttu-id="4543c-114">Exempel 1: ändra ett visnings namn</span><span class="sxs-lookup"><span data-stu-id="4543c-114">Example 1: Change a display name</span></span>

<span data-ttu-id="4543c-115">I det här exemplet ändras en tjänsts visnings namn.</span><span class="sxs-lookup"><span data-stu-id="4543c-115">In this example, a service's display name is changed.</span></span> <span data-ttu-id="4543c-116">Använd om du vill visa det ursprungliga visnings namnet `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="4543c-116">To view the original display name, use `Get-Service`.</span></span>

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

<span data-ttu-id="4543c-117">`Set-Service` använder **Name** -parametern för att ange tjänstens namn, **LanmanWorkstation**.</span><span class="sxs-lookup"><span data-stu-id="4543c-117">`Set-Service` uses the **Name** parameter to specify the service's name, **LanmanWorkstation**.</span></span> <span data-ttu-id="4543c-118">Parametern **DisplayName** anger det nya visnings namnet, **LANMAN-arbetsstationen**.</span><span class="sxs-lookup"><span data-stu-id="4543c-118">The **DisplayName** parameter specifies the new display name, **LanMan Workstation**.</span></span>

### <span data-ttu-id="4543c-119">Exempel 2: ändra start typen för tjänster</span><span class="sxs-lookup"><span data-stu-id="4543c-119">Example 2: Change the startup type of services</span></span>

<span data-ttu-id="4543c-120">Det här exemplet visar hur du ändrar Start typen för en tjänst.</span><span class="sxs-lookup"><span data-stu-id="4543c-120">This example shows how to change a service's startup type.</span></span>

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

<span data-ttu-id="4543c-121">`Set-Service` använder **Name** -parametern för att ange tjänstens namn, **bitar**.</span><span class="sxs-lookup"><span data-stu-id="4543c-121">`Set-Service` uses the **Name** parameter to specify the service's name, **BITS**.</span></span> <span data-ttu-id="4543c-122">Parametern **startuptype tjänst** anger att tjänsten ska vara **Automatisk**.</span><span class="sxs-lookup"><span data-stu-id="4543c-122">The **StartupType** parameter sets the service to **Automatic**.</span></span>

<span data-ttu-id="4543c-123">`Get-Service` använder **Name** -parametern för att ange **BITS** -tjänsten och skickar objektet nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="4543c-123">`Get-Service` uses the **Name** parameter to specify the **BITS** service and sends the object down the pipeline.</span></span> <span data-ttu-id="4543c-124">`Select-Object` använder **egenskaps** parametern för att visa **BITS** -tjänstens status.</span><span class="sxs-lookup"><span data-stu-id="4543c-124">`Select-Object` uses the **Property** parameter to display the **BITS** service's status.</span></span>

### <span data-ttu-id="4543c-125">Exempel 3: ändra beskrivningen av en tjänst</span><span class="sxs-lookup"><span data-stu-id="4543c-125">Example 3: Change the description of a service</span></span>

<span data-ttu-id="4543c-126">Det här exemplet ändrar beskrivningen av BITS-tjänsten och visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="4543c-126">This example changes the BITS service's description and displays the result.</span></span>

<span data-ttu-id="4543c-127">`Get-CimInstance`Cmdleten används eftersom den returnerar ett **Win32_Service** -objekt som innehåller tjänstens **Beskrivning**.</span><span class="sxs-lookup"><span data-stu-id="4543c-127">The `Get-CimInstance` cmdlet is used because it returns a **Win32_Service** object that includes the service's **Description**.</span></span>

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

<span data-ttu-id="4543c-128">`Get-CimInstance` skickar objektet nedåt i pipeline till `Format-List` och visar tjänstens namn och beskrivning.</span><span class="sxs-lookup"><span data-stu-id="4543c-128">`Get-CimInstance` sends the object down the pipeline to `Format-List` and displays the service's name and description.</span></span> <span data-ttu-id="4543c-129">I jämförelse syfte körs kommandot före och efter att beskrivningen har uppdaterats.</span><span class="sxs-lookup"><span data-stu-id="4543c-129">For comparison purposes, the command is run before and after the description is updated.</span></span>

<span data-ttu-id="4543c-130">`Set-Service` använder **Name** -parametern för att ange **BITS** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4543c-130">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="4543c-131">Parametern **Description** anger den uppdaterade texten för beskrivningen av tjänsterna.</span><span class="sxs-lookup"><span data-stu-id="4543c-131">The **Description** parameter specifies the updated text for the services' description.</span></span>

### <span data-ttu-id="4543c-132">Exempel 4: starta en tjänst</span><span class="sxs-lookup"><span data-stu-id="4543c-132">Example 4: Start a service</span></span>

<span data-ttu-id="4543c-133">I det här exemplet startas en tjänst.</span><span class="sxs-lookup"><span data-stu-id="4543c-133">In this example, a service is started.</span></span>

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

<span data-ttu-id="4543c-134">`Set-Service` använder parametern **Name** för att ange tjänsten, **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="4543c-134">`Set-Service` uses the **Name** parameter to specify the service, **WinRM**.</span></span> <span data-ttu-id="4543c-135">**Status** parametern använder det värde som **körs** för att starta tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4543c-135">The **Status** parameter uses the value **Running** to start the service.</span></span> <span data-ttu-id="4543c-136">**Passthru** -parametern matar ut ett **ServiceController** -objekt som visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="4543c-136">The **PassThru** parameter outputs a **ServiceController** object that displays the results.</span></span>

### <span data-ttu-id="4543c-137">Exempel 5: inaktivera en tjänst</span><span class="sxs-lookup"><span data-stu-id="4543c-137">Example 5: Suspend a service</span></span>

<span data-ttu-id="4543c-138">I det här exemplet används pipelinen för att pausa tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4543c-138">This example uses the pipeline to pause to service.</span></span>

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

<span data-ttu-id="4543c-139">`Get-Service` använder **Name** -parametern för att ange **schema** tjänsten och skickar objektet nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="4543c-139">`Get-Service` uses the **Name** parameter to specify the **Schedule** service, and sends the object down the pipeline.</span></span> <span data-ttu-id="4543c-140">`Set-Service` använder **status** parametern för att ange att tjänsten ska **pausas**.</span><span class="sxs-lookup"><span data-stu-id="4543c-140">`Set-Service` uses the **Status** parameter to set the service to **Paused**.</span></span>

### <span data-ttu-id="4543c-141">Exempel 6: stoppa en tjänst</span><span class="sxs-lookup"><span data-stu-id="4543c-141">Example 6: Stop a service</span></span>

<span data-ttu-id="4543c-142">I det här exemplet används en variabel för att stoppa en tjänst.</span><span class="sxs-lookup"><span data-stu-id="4543c-142">This example uses a variable to stop a service.</span></span>

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

<span data-ttu-id="4543c-143">`Get-Service` använder **Name** -parametern för att ange tjänsten, **schema**.</span><span class="sxs-lookup"><span data-stu-id="4543c-143">`Get-Service` uses the **Name** parameter to specify the service, **Schedule**.</span></span> <span data-ttu-id="4543c-144">Objektet lagras i variabeln `$S` .</span><span class="sxs-lookup"><span data-stu-id="4543c-144">The object is stored in the variable, `$S`.</span></span> <span data-ttu-id="4543c-145">`Set-Service` använder parametern **InputObject** och anger objektet som lagras `$S` .</span><span class="sxs-lookup"><span data-stu-id="4543c-145">`Set-Service` uses the **InputObject** parameter and specifies the object stored `$S`.</span></span> <span data-ttu-id="4543c-146">**Status** parametern anger att tjänsten har **stoppats**.</span><span class="sxs-lookup"><span data-stu-id="4543c-146">The **Status** parameter sets the service to **Stopped**.</span></span>

### <span data-ttu-id="4543c-147">Exempel 7: stoppa en tjänst på ett fjärrsystem</span><span class="sxs-lookup"><span data-stu-id="4543c-147">Example 7: Stop a service on a remote system</span></span>

<span data-ttu-id="4543c-148">I det här exemplet stoppas en tjänst på en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="4543c-148">This example stops a service on a remote computer.</span></span>
<span data-ttu-id="4543c-149">Mer information finns i [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="4543c-149">For more information, see [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```powershell
$Cred = Get-Credential
$S = Get-Service -Name Schedule
Invoke-Command -ComputerName server01.contoso.com -Credential $Cred -ScriptBlock {
  Set-Service -InputObject $S -Status Stopped
}
```

<span data-ttu-id="4543c-150">`Get-Credential` efterfrågar ett användar namn och lösen ord och lagrar autentiseringsuppgifterna i `$Cred` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4543c-150">`Get-Credential` prompts for a username and password, and stores the credentials in the `$Cred` variable.</span></span> <span data-ttu-id="4543c-151">`Get-Service` använder **Name** -parametern för att ange tjänsten **Schedule** .</span><span class="sxs-lookup"><span data-stu-id="4543c-151">`Get-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="4543c-152">Objektet lagras i variabeln `$S` .</span><span class="sxs-lookup"><span data-stu-id="4543c-152">The object is stored in the variable, `$S`.</span></span>

<span data-ttu-id="4543c-153">`Invoke-Command` använder parametern **computername** för att ange en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="4543c-153">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer.</span></span> <span data-ttu-id="4543c-154">Parametern **Credential** använder `$Cred` variabeln för att logga in på datorn.</span><span class="sxs-lookup"><span data-stu-id="4543c-154">The **Credential** parameter uses the `$Cred` variable to sign on to the computer.</span></span> <span data-ttu-id="4543c-155">**Script block** -anrop `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="4543c-155">The **ScriptBlock** calls `Set-Service`.</span></span> <span data-ttu-id="4543c-156">Parametern **InputObject** anger det tjänst objekt som lagras `$S` .</span><span class="sxs-lookup"><span data-stu-id="4543c-156">The **InputObject** parameter specifies the service object stored `$S`.</span></span> <span data-ttu-id="4543c-157">**Status** parametern anger att tjänsten har **stoppats**.</span><span class="sxs-lookup"><span data-stu-id="4543c-157">The **Status** parameter sets the service to **Stopped**.</span></span>

### <span data-ttu-id="4543c-158">Exempel 8: ändra autentiseringsuppgifter för en tjänst</span><span class="sxs-lookup"><span data-stu-id="4543c-158">Example 8: Change credential of a service</span></span>

<span data-ttu-id="4543c-159">Det här exemplet ändrar de autentiseringsuppgifter som används för att hantera en tjänst.</span><span class="sxs-lookup"><span data-stu-id="4543c-159">This example changes the credentials that are used to manage a service.</span></span>

```powershell
$credential = Get-Credential
Set-Service -Name Schedule -Credential $credential
```

<span data-ttu-id="4543c-160">`Get-Credential` efterfrågar ett användar namn och lösen ord och lagrar autentiseringsuppgifterna i `$credential` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4543c-160">`Get-Credential` prompts for a username and password, and stores the credentials in the `$credential` variable.</span></span> <span data-ttu-id="4543c-161">`Set-Service` använder **Name** -parametern för att ange tjänsten **Schedule** .</span><span class="sxs-lookup"><span data-stu-id="4543c-161">`Set-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="4543c-162">Parametern **Credential** använder `$credential` variabeln och uppdaterar tjänsten **schema** .</span><span class="sxs-lookup"><span data-stu-id="4543c-162">The **Credential** parameter uses the `$credential` variable and updates the **Schedule** service.</span></span>

### <span data-ttu-id="4543c-163">Exempel 9: ändra adtagent för en tjänst</span><span class="sxs-lookup"><span data-stu-id="4543c-163">Example 9: Change the SecurityDescriptor of a service</span></span>

<span data-ttu-id="4543c-164">Det här exemplet ändrar en tjänsts **adtagent**.</span><span class="sxs-lookup"><span data-stu-id="4543c-164">This example changes a service's **SecurityDescriptor**.</span></span>

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
Set-Service -Name "BITS" -SecurityDescriptorSddl $SDDL
```

<span data-ttu-id="4543c-165">**Adtagent** lagras i `$SDDL` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4543c-165">The **SecurityDescriptor** is stored in the `$SDDL` variable.</span></span> <span data-ttu-id="4543c-166">`Set-Service` använder **Name** -parametern för att ange **BITS** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4543c-166">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="4543c-167">Parametern **SecurityDescriptorSddl** använder `$SDDL` för att ändra **adtagent** för **BITS** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4543c-167">The **SecurityDescriptorSddl** parameter uses `$SDDL` to change the **SecurityDescriptor** for the **BITS** service.</span></span>

## <span data-ttu-id="4543c-168">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4543c-168">PARAMETERS</span></span>

### <span data-ttu-id="4543c-169">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4543c-169">-Confirm</span></span>

<span data-ttu-id="4543c-170">Du uppmanas att bekräfta innan du kör `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="4543c-170">Prompts you for confirmation before running `Set-Service`.</span></span>

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

### <span data-ttu-id="4543c-171">-Credential</span><span class="sxs-lookup"><span data-stu-id="4543c-171">-Credential</span></span>

<span data-ttu-id="4543c-172">Anger kontot som används av tjänsten som [tjänst inloggnings konto](/windows/desktop/ad/about-service-logon-accounts).</span><span class="sxs-lookup"><span data-stu-id="4543c-172">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="4543c-173">Ange ett användar namn, till exempel **user01** eller **Domain01\User01**, eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4543c-173">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="4543c-174">Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4543c-174">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="4543c-175">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="4543c-175">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="4543c-176">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="4543c-176">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

<span data-ttu-id="4543c-177">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="4543c-177">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="4543c-178">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4543c-178">-Description</span></span>

<span data-ttu-id="4543c-179">Anger en ny Beskrivning av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4543c-179">Specifies a new description for the service.</span></span>

<span data-ttu-id="4543c-180">Tjänst beskrivningen visas i **dator hantering, tjänster**.</span><span class="sxs-lookup"><span data-stu-id="4543c-180">The service description appears in **Computer Management, Services**.</span></span> <span data-ttu-id="4543c-181">**Beskrivningen** är inte en egenskap för `Get-Service` **ServiceController** -objektet.</span><span class="sxs-lookup"><span data-stu-id="4543c-181">The **Description** isn't a property of the `Get-Service` **ServiceController** object.</span></span> <span data-ttu-id="4543c-182">Om du vill se tjänst beskrivningen använder du `Get-CimInstance` som returnerar ett **Win32_Service** -objekt som representerar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4543c-182">To see the service description, use `Get-CimInstance` that returns a **Win32_Service** object that represents the service.</span></span>

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

### <span data-ttu-id="4543c-183">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="4543c-183">-DisplayName</span></span>

<span data-ttu-id="4543c-184">Anger ett nytt visnings namn för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4543c-184">Specifies a new display name for the service.</span></span>

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

### <span data-ttu-id="4543c-185">-Force</span><span class="sxs-lookup"><span data-stu-id="4543c-185">-Force</span></span>

<span data-ttu-id="4543c-186">Anger tjänstens stopp läge.</span><span class="sxs-lookup"><span data-stu-id="4543c-186">Specifies the Stop mode of the service.</span></span> <span data-ttu-id="4543c-187">Den här parametern fungerar bara när `-Status Stopped` används.</span><span class="sxs-lookup"><span data-stu-id="4543c-187">This parameter only works when `-Status Stopped` is used.</span></span> <span data-ttu-id="4543c-188">Om aktive rad stoppas `Set-Service` de beroende tjänsterna innan mål tjänsten stoppas.</span><span class="sxs-lookup"><span data-stu-id="4543c-188">If enabled, `Set-Service` stops the dependent services before the target service is stopped.</span></span> <span data-ttu-id="4543c-189">Som standard höjs undantag när andra tjänster som körs är beroende av mål tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4543c-189">By default, exceptions are raised when other running services depend on the target service.</span></span>

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

### <span data-ttu-id="4543c-190">– InputObject</span><span class="sxs-lookup"><span data-stu-id="4543c-190">-InputObject</span></span>

<span data-ttu-id="4543c-191">Anger ett **ServiceController** -objekt som representerar den tjänst som ska ändras.</span><span class="sxs-lookup"><span data-stu-id="4543c-191">Specifies a **ServiceController** object that represents the service to change.</span></span> <span data-ttu-id="4543c-192">Ange en variabel som innehåller objektet eller Skriv ett kommando eller uttryck som hämtar objektet, till exempel ett `Get-Service` kommando.</span><span class="sxs-lookup"><span data-stu-id="4543c-192">Enter a variable that contains the object, or type a command or expression that gets the object, such as a `Get-Service` command.</span></span> <span data-ttu-id="4543c-193">Du kan använda pipelinen för att skicka ett tjänst objekt till `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="4543c-193">You can use the pipeline to send a service object to `Set-Service`.</span></span>

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

### <span data-ttu-id="4543c-194">-Name</span><span class="sxs-lookup"><span data-stu-id="4543c-194">-Name</span></span>

<span data-ttu-id="4543c-195">Anger tjänst namnet på den tjänst som ska ändras.</span><span class="sxs-lookup"><span data-stu-id="4543c-195">Specifies the service name of the service to be changed.</span></span> <span data-ttu-id="4543c-196">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="4543c-196">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="4543c-197">Du kan använda pipelinen för att skicka ett tjänst namn till `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="4543c-197">You can use the pipeline to send a service name to `Set-Service`.</span></span>

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

### <span data-ttu-id="4543c-198">– PassThru</span><span class="sxs-lookup"><span data-stu-id="4543c-198">-PassThru</span></span>

<span data-ttu-id="4543c-199">Returnerar ett **ServiceController** -objekt som representerar de tjänster som har ändrats.</span><span class="sxs-lookup"><span data-stu-id="4543c-199">Returns a **ServiceController** object that represents the services that were changed.</span></span> <span data-ttu-id="4543c-200">Som standard `Set-Service` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="4543c-200">By default, `Set-Service` doesn't generate any output.</span></span>

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

### <span data-ttu-id="4543c-201">– Startuptype tjänst</span><span class="sxs-lookup"><span data-stu-id="4543c-201">-StartupType</span></span>

<span data-ttu-id="4543c-202">Anger tjänstens start läge.</span><span class="sxs-lookup"><span data-stu-id="4543c-202">Specifies the start mode of the service.</span></span>

<span data-ttu-id="4543c-203">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="4543c-203">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="4543c-204">**Automatiskt** – tjänsten startas eller startades av operativ systemet vid system start.</span><span class="sxs-lookup"><span data-stu-id="4543c-204">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="4543c-205">Om en automatiskt startad tjänst är beroende av en manuellt startad tjänst startas automatiskt den manuellt startade tjänsten automatiskt vid system start.</span><span class="sxs-lookup"><span data-stu-id="4543c-205">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="4543c-206">**AutomaticDelayedStart** – startar strax efter att systemet har startat.</span><span class="sxs-lookup"><span data-stu-id="4543c-206">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="4543c-207">**Disabled** – tjänsten är inaktive rad och kan inte startas av en användare eller ett program.</span><span class="sxs-lookup"><span data-stu-id="4543c-207">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="4543c-208">**InvalidValue** – har ingen inverkan.</span><span class="sxs-lookup"><span data-stu-id="4543c-208">**InvalidValue** - Has no effect.</span></span> <span data-ttu-id="4543c-209">Cmdleten returnerar inte ett fel, men Startuptype tjänst för tjänsten har inte ändrats.</span><span class="sxs-lookup"><span data-stu-id="4543c-209">The cmdlet does not return an error but the StartupType of the service is not changed.</span></span>
- <span data-ttu-id="4543c-210">**Manuell** – tjänsten startas endast manuellt, av en användare, med hjälp av tjänst hanteraren eller av ett program.</span><span class="sxs-lookup"><span data-stu-id="4543c-210">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

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

### <span data-ttu-id="4543c-211">-Status</span><span class="sxs-lookup"><span data-stu-id="4543c-211">-Status</span></span>

<span data-ttu-id="4543c-212">Anger tjänstens status.</span><span class="sxs-lookup"><span data-stu-id="4543c-212">Specifies the status for the service.</span></span>

<span data-ttu-id="4543c-213">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="4543c-213">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="4543c-214">**Pausat**.</span><span class="sxs-lookup"><span data-stu-id="4543c-214">**Paused**.</span></span> <span data-ttu-id="4543c-215">Pausar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4543c-215">Suspends the service.</span></span>
- <span data-ttu-id="4543c-216">**Körs**.</span><span class="sxs-lookup"><span data-stu-id="4543c-216">**Running**.</span></span> <span data-ttu-id="4543c-217">Startar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4543c-217">Starts the service.</span></span>
- <span data-ttu-id="4543c-218">**Stoppades**.</span><span class="sxs-lookup"><span data-stu-id="4543c-218">**Stopped**.</span></span> <span data-ttu-id="4543c-219">Stoppar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4543c-219">Stops the service.</span></span>

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

### <span data-ttu-id="4543c-220">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="4543c-220">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="4543c-221">Anger **adtagent** för tjänsten i **SDDL** -format.</span><span class="sxs-lookup"><span data-stu-id="4543c-221">Specifies the **SecurityDescriptor** for the service in **Sddl** format.</span></span>

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

### <span data-ttu-id="4543c-222">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4543c-222">-WhatIf</span></span>

<span data-ttu-id="4543c-223">Visar vad som händer om `Set-Service` körs.</span><span class="sxs-lookup"><span data-stu-id="4543c-223">Shows what would happen if `Set-Service` runs.</span></span> <span data-ttu-id="4543c-224">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="4543c-224">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="4543c-225">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4543c-225">CommonParameters</span></span>

<span data-ttu-id="4543c-226">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4543c-226">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4543c-227">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4543c-227">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4543c-228">INDATA</span><span class="sxs-lookup"><span data-stu-id="4543c-228">INPUTS</span></span>

### <span data-ttu-id="4543c-229">System. ServiceProcess. ServiceController, system. String</span><span class="sxs-lookup"><span data-stu-id="4543c-229">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="4543c-230">Du kan använda pipelinen för att skicka ett tjänst objekt eller en sträng som innehåller ett tjänst namn till `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="4543c-230">You can use the pipeline to send a service object or a string that contains a service name to `Set-Service`.</span></span>

## <span data-ttu-id="4543c-231">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4543c-231">OUTPUTS</span></span>

### <span data-ttu-id="4543c-232">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="4543c-232">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="4543c-233">Som standard `Set-Service` returnerar inte några objekt.</span><span class="sxs-lookup"><span data-stu-id="4543c-233">By default, `Set-Service` doesn't return any objects.</span></span> <span data-ttu-id="4543c-234">Använd parametern **Passthru** för att mata ut ett **ServiceController** -objekt.</span><span class="sxs-lookup"><span data-stu-id="4543c-234">Use the **PassThru** parameter to output a **ServiceController** object.</span></span>

## <span data-ttu-id="4543c-235">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4543c-235">NOTES</span></span>

<span data-ttu-id="4543c-236">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="4543c-236">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="4543c-237">`Set-Service` kräver förhöjd behörighet.</span><span class="sxs-lookup"><span data-stu-id="4543c-237">`Set-Service` requires elevated permissions.</span></span> <span data-ttu-id="4543c-238">Använd alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="4543c-238">Use the **Run as administrator** option.</span></span>

<span data-ttu-id="4543c-239">`Set-Service` Det går bara att kontrol lera tjänster när den aktuella användaren har behörighet att hantera tjänster.</span><span class="sxs-lookup"><span data-stu-id="4543c-239">`Set-Service` can only control services when the current user has permissions to manage services.</span></span> <span data-ttu-id="4543c-240">Om ett kommando inte fungerar som det ska kanske du inte har de behörigheter som krävs.</span><span class="sxs-lookup"><span data-stu-id="4543c-240">If a command doesn't work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="4543c-241">Använd om du vill hitta tjänstens namn eller visnings namn för tjänsten `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="4543c-241">To find a service's service name or display name, use `Get-Service`.</span></span> <span data-ttu-id="4543c-242">Tjänst namnen finns i kolumnen **namn** och visnings namnen är i kolumnen **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="4543c-242">The service names are in the **Name** column and the display names are in the **DisplayName** column.</span></span>

## <span data-ttu-id="4543c-243">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4543c-243">RELATED LINKS</span></span>

[<span data-ttu-id="4543c-244">Get-Service</span><span class="sxs-lookup"><span data-stu-id="4543c-244">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="4543c-245">New-Service</span><span class="sxs-lookup"><span data-stu-id="4543c-245">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="4543c-246">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="4543c-246">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="4543c-247">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="4543c-247">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="4543c-248">Start-Service</span><span class="sxs-lookup"><span data-stu-id="4543c-248">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="4543c-249">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="4543c-249">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="4543c-250">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="4543c-250">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="4543c-251">Remove-service</span><span class="sxs-lookup"><span data-stu-id="4543c-251">Remove-Service</span></span>](Remove-Service.md)
