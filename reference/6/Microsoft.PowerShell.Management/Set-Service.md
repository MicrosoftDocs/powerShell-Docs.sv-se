---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: ad1fd47291cbe8977bd2f2ada4981589714c93a3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263786"
---
# <span data-ttu-id="1a5b8-103">Set-Service</span><span class="sxs-lookup"><span data-stu-id="1a5b8-103">Set-Service</span></span>

## <span data-ttu-id="1a5b8-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1a5b8-104">SYNOPSIS</span></span>
<span data-ttu-id="1a5b8-105">Startar, stoppar och pausar en tjänst och ändrar dess egenskaper.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-105">Starts, stops, and suspends a service, and changes its properties.</span></span>

## <span data-ttu-id="1a5b8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1a5b8-106">SYNTAX</span></span>

### <span data-ttu-id="1a5b8-107">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="1a5b8-107">Name (Default)</span></span>

```
Set-Service [-Name] <String> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-Status <String>] [-Force] [-PassThru]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1a5b8-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="1a5b8-108">InputObject</span></span>

```
Set-Service [-InputObject] <ServiceController> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-Status <String>] [-Force] [-PassThru]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1a5b8-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1a5b8-109">DESCRIPTION</span></span>

<span data-ttu-id="1a5b8-110">`Set-Service`Cmdleten ändrar egenskaperna för en tjänst, till exempel **status** , **Beskrivning** , **DisplayName** och **startuptype tjänst**.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-110">The `Set-Service` cmdlet changes the properties of a service such as the **Status** , **Description** , **DisplayName** , and **StartupType**.</span></span> <span data-ttu-id="1a5b8-111">`Set-Service` kan starta, stoppa, pausa eller pausa en tjänst.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-111">`Set-Service` can start, stop, suspend, or pause a service.</span></span> <span data-ttu-id="1a5b8-112">För att identifiera en tjänst anger du dess tjänst namn eller skickar ett tjänst objekt.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-112">To identify a service, enter its service name or submit a service object.</span></span> <span data-ttu-id="1a5b8-113">Eller skicka ett tjänst namn eller tjänst objekt nedåt i pipeline till `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="1a5b8-113">Or, send a service name or service object down the pipeline to `Set-Service`.</span></span>

## <span data-ttu-id="1a5b8-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1a5b8-114">EXAMPLES</span></span>

### <span data-ttu-id="1a5b8-115">Exempel 1: ändra ett visnings namn</span><span class="sxs-lookup"><span data-stu-id="1a5b8-115">Example 1: Change a display name</span></span>

<span data-ttu-id="1a5b8-116">I det här exemplet ändras en tjänsts visnings namn.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-116">In this example, a service's display name is changed.</span></span> <span data-ttu-id="1a5b8-117">Använd om du vill visa det ursprungliga visnings namnet `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="1a5b8-117">To view the original display name, use `Get-Service`.</span></span>

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

<span data-ttu-id="1a5b8-118">`Set-Service` använder **Name** -parametern för att ange tjänstens namn, **LanmanWorkstation**.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-118">`Set-Service` uses the **Name** parameter to specify the service's name, **LanmanWorkstation**.</span></span> <span data-ttu-id="1a5b8-119">Parametern **DisplayName** anger det nya visnings namnet, **LANMAN-arbetsstationen**.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-119">The **DisplayName** parameter specifies the new display name, **LanMan Workstation**.</span></span>

### <span data-ttu-id="1a5b8-120">Exempel 2: ändra start typen för tjänster</span><span class="sxs-lookup"><span data-stu-id="1a5b8-120">Example 2: Change the startup type of services</span></span>

<span data-ttu-id="1a5b8-121">Det här exemplet visar hur du ändrar Start typen för en tjänst.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-121">This example shows how to change a service's startup type.</span></span>

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

<span data-ttu-id="1a5b8-122">`Set-Service` använder **Name** -parametern för att ange tjänstens namn, **bitar**.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-122">`Set-Service` uses the **Name** parameter to specify the service's name, **BITS**.</span></span> <span data-ttu-id="1a5b8-123">Parametern **startuptype tjänst** anger att tjänsten ska vara **Automatisk**.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-123">The **StartupType** parameter sets the service to **Automatic**.</span></span>

<span data-ttu-id="1a5b8-124">`Get-Service` använder **Name** -parametern för att ange **BITS** -tjänsten och skickar objektet nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-124">`Get-Service` uses the **Name** parameter to specify the **BITS** service and sends the object down the pipeline.</span></span> <span data-ttu-id="1a5b8-125">`Select-Object` använder **egenskaps** parametern för att visa **BITS** -tjänstens status.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-125">`Select-Object` uses the **Property** parameter to display the **BITS** service's status.</span></span>

### <span data-ttu-id="1a5b8-126">Exempel 3: ändra beskrivningen av en tjänst</span><span class="sxs-lookup"><span data-stu-id="1a5b8-126">Example 3: Change the description of a service</span></span>

<span data-ttu-id="1a5b8-127">Det här exemplet ändrar beskrivningen av BITS-tjänsten och visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-127">This example changes the BITS service's description and displays the result.</span></span>

<span data-ttu-id="1a5b8-128">`Get-CimInstance`Cmdleten används eftersom den returnerar ett **Win32_Service** -objekt som innehåller tjänstens **Beskrivning**.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-128">The `Get-CimInstance` cmdlet is used because it returns a **Win32_Service** object that includes the service's **Description**.</span></span>

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

<span data-ttu-id="1a5b8-129">`Get-CimInstance` skickar objektet nedåt i pipeline till `Format-List` och visar tjänstens namn och beskrivning.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-129">`Get-CimInstance` sends the object down the pipeline to `Format-List` and displays the service's name and description.</span></span> <span data-ttu-id="1a5b8-130">I jämförelse syfte körs kommandot före och efter att beskrivningen har uppdaterats.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-130">For comparison purposes, the command is run before and after the description is updated.</span></span>

<span data-ttu-id="1a5b8-131">`Set-Service` använder **Name** -parametern för att ange **BITS** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-131">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="1a5b8-132">Parametern **Description** anger den uppdaterade texten för beskrivningen av tjänsterna.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-132">The **Description** parameter specifies the updated text for the services' description.</span></span>

### <span data-ttu-id="1a5b8-133">Exempel 4: starta en tjänst</span><span class="sxs-lookup"><span data-stu-id="1a5b8-133">Example 4: Start a service</span></span>

<span data-ttu-id="1a5b8-134">I det här exemplet startas en tjänst.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-134">In this example, a service is started.</span></span>

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

<span data-ttu-id="1a5b8-135">`Set-Service` använder parametern **Name** för att ange tjänsten, **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-135">`Set-Service` uses the **Name** parameter to specify the service, **WinRM**.</span></span> <span data-ttu-id="1a5b8-136">**Status** parametern använder det värde som **körs** för att starta tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-136">The **Status** parameter uses the value **Running** to start the service.</span></span> <span data-ttu-id="1a5b8-137">**Passthru** -parametern matar ut ett **ServiceController** -objekt som visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-137">The **PassThru** parameter outputs a **ServiceController** object that displays the results.</span></span>

### <span data-ttu-id="1a5b8-138">Exempel 5: inaktivera en tjänst</span><span class="sxs-lookup"><span data-stu-id="1a5b8-138">Example 5: Suspend a service</span></span>

<span data-ttu-id="1a5b8-139">I det här exemplet används pipelinen för att pausa tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-139">This example uses the pipeline to pause to service.</span></span>

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

<span data-ttu-id="1a5b8-140">`Get-Service` använder **Name** -parametern för att ange **schema** tjänsten och skickar objektet nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-140">`Get-Service` uses the **Name** parameter to specify the **Schedule** service, and sends the object down the pipeline.</span></span> <span data-ttu-id="1a5b8-141">`Set-Service` använder **status** parametern för att ange att tjänsten ska **pausas**.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-141">`Set-Service` uses the **Status** parameter to set the service to **Paused**.</span></span>

### <span data-ttu-id="1a5b8-142">Exempel 6: stoppa en tjänst</span><span class="sxs-lookup"><span data-stu-id="1a5b8-142">Example 6: Stop a service</span></span>

<span data-ttu-id="1a5b8-143">I det här exemplet används en variabel för att stoppa en tjänst.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-143">This example uses a variable to stop a service.</span></span>

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

<span data-ttu-id="1a5b8-144">`Get-Service` använder **Name** -parametern för att ange tjänsten, **schema**.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-144">`Get-Service` uses the **Name** parameter to specify the service, **Schedule**.</span></span> <span data-ttu-id="1a5b8-145">Objektet lagras i variabeln `$S` .</span><span class="sxs-lookup"><span data-stu-id="1a5b8-145">The object is stored in the variable, `$S`.</span></span> <span data-ttu-id="1a5b8-146">`Set-Service` använder parametern **InputObject** och anger objektet som lagras `$S` .</span><span class="sxs-lookup"><span data-stu-id="1a5b8-146">`Set-Service` uses the **InputObject** parameter and specifies the object stored `$S`.</span></span> <span data-ttu-id="1a5b8-147">**Status** parametern anger att tjänsten har **stoppats**.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-147">The **Status** parameter sets the service to **Stopped**.</span></span>

### <span data-ttu-id="1a5b8-148">Exempel 7: stoppa en tjänst på ett fjärrsystem</span><span class="sxs-lookup"><span data-stu-id="1a5b8-148">Example 7: Stop a service on a remote system</span></span>

<span data-ttu-id="1a5b8-149">I det här exemplet stoppas en tjänst på en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-149">This example stops a service on a remote computer.</span></span>
<span data-ttu-id="1a5b8-150">Mer information finns i [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="1a5b8-150">For more information, see [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```powershell
$Cred = Get-Credential
$S = Get-Service -Name Schedule
Invoke-Command -ComputerName server01.contoso.com -Credential $Cred -ScriptBlock {
  Set-Service -InputObject $S -Status Stopped
}
```

<span data-ttu-id="1a5b8-151">`Get-Credential` efterfrågar ett användar namn och lösen ord och lagrar autentiseringsuppgifterna i `$Cred` variabeln.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-151">`Get-Credential` prompts for a username and password, and stores the credentials in the `$Cred` variable.</span></span> <span data-ttu-id="1a5b8-152">`Get-Service` använder **Name** -parametern för att ange tjänsten **Schedule** .</span><span class="sxs-lookup"><span data-stu-id="1a5b8-152">`Get-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="1a5b8-153">Objektet lagras i variabeln `$S` .</span><span class="sxs-lookup"><span data-stu-id="1a5b8-153">The object is stored in the variable, `$S`.</span></span>

<span data-ttu-id="1a5b8-154">`Invoke-Command` använder parametern **computername** för att ange en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-154">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer.</span></span> <span data-ttu-id="1a5b8-155">Parametern **Credential** använder `$Cred` variabeln för att logga in på datorn.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-155">The **Credential** parameter uses the `$Cred` variable to sign on to the computer.</span></span> <span data-ttu-id="1a5b8-156">**Script block** -anrop `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="1a5b8-156">The **ScriptBlock** calls `Set-Service`.</span></span> <span data-ttu-id="1a5b8-157">Parametern **InputObject** anger det tjänst objekt som lagras `$S` .</span><span class="sxs-lookup"><span data-stu-id="1a5b8-157">The **InputObject** parameter specifies the service object stored `$S`.</span></span> <span data-ttu-id="1a5b8-158">**Status** parametern anger att tjänsten har **stoppats**.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-158">The **Status** parameter sets the service to **Stopped**.</span></span>

### <span data-ttu-id="1a5b8-159">Exempel 8: ändra autentiseringsuppgifter för en tjänst</span><span class="sxs-lookup"><span data-stu-id="1a5b8-159">Example 8: Change credential of a service</span></span>

<span data-ttu-id="1a5b8-160">Det här exemplet ändrar de autentiseringsuppgifter som används för att hantera en tjänst.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-160">This example changes the credentials that are used to manage a service.</span></span>

```powershell
$credential = Get-Credential
Set-Service -Name Schedule -Credential $credential
```

<span data-ttu-id="1a5b8-161">`Get-Credential` efterfrågar ett användar namn och lösen ord och lagrar autentiseringsuppgifterna i `$credential` variabeln.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-161">`Get-Credential` prompts for a username and password, and stores the credentials in the `$credential` variable.</span></span> <span data-ttu-id="1a5b8-162">`Set-Service` använder **Name** -parametern för att ange tjänsten **Schedule** .</span><span class="sxs-lookup"><span data-stu-id="1a5b8-162">`Set-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="1a5b8-163">Parametern **Credential** använder `$credential` variabeln och uppdaterar tjänsten **schema** .</span><span class="sxs-lookup"><span data-stu-id="1a5b8-163">The **Credential** parameter uses the `$credential` variable and updates the **Schedule** service.</span></span>

## <span data-ttu-id="1a5b8-164">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1a5b8-164">PARAMETERS</span></span>

### <span data-ttu-id="1a5b8-165">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1a5b8-165">-Confirm</span></span>

<span data-ttu-id="1a5b8-166">Du uppmanas att bekräfta innan du kör `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="1a5b8-166">Prompts you for confirmation before running `Set-Service`.</span></span>

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

### <span data-ttu-id="1a5b8-167">-Credential</span><span class="sxs-lookup"><span data-stu-id="1a5b8-167">-Credential</span></span>

<span data-ttu-id="1a5b8-168">Anger kontot som används av tjänsten som [tjänst inloggnings konto](/windows/desktop/ad/about-service-logon-accounts).</span><span class="sxs-lookup"><span data-stu-id="1a5b8-168">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="1a5b8-169">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-169">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="1a5b8-170">Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-170">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="1a5b8-171">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="1a5b8-171">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="1a5b8-172">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="1a5b8-172">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

<span data-ttu-id="1a5b8-173">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-173">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="1a5b8-174">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1a5b8-174">-Description</span></span>

<span data-ttu-id="1a5b8-175">Anger en ny Beskrivning av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-175">Specifies a new description for the service.</span></span>

<span data-ttu-id="1a5b8-176">Tjänst beskrivningen visas i **dator hantering, tjänster**.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-176">The service description appears in **Computer Management, Services**.</span></span> <span data-ttu-id="1a5b8-177">**Beskrivningen** är inte en egenskap för `Get-Service` **ServiceController** -objektet.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-177">The **Description** isn't a property of the `Get-Service` **ServiceController** object.</span></span> <span data-ttu-id="1a5b8-178">Om du vill se tjänst beskrivningen använder du `Get-CimInstance` som returnerar ett **Win32_Service** -objekt som representerar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-178">To see the service description, use `Get-CimInstance` that returns a **Win32_Service** object that represents the service.</span></span>

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

### <span data-ttu-id="1a5b8-179">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="1a5b8-179">-DisplayName</span></span>

<span data-ttu-id="1a5b8-180">Anger ett nytt visnings namn för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-180">Specifies a new display name for the service.</span></span>

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

### <span data-ttu-id="1a5b8-181">-Force</span><span class="sxs-lookup"><span data-stu-id="1a5b8-181">-Force</span></span>

<span data-ttu-id="1a5b8-182">Anger tjänstens stopp läge.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-182">Specifies the Stop mode of the service.</span></span> <span data-ttu-id="1a5b8-183">Den här parametern fungerar bara när `-Status Stopped` används.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-183">This parameter only works when `-Status Stopped` is used.</span></span> <span data-ttu-id="1a5b8-184">Om aktive rad stoppas `Set-Service` de beroende tjänsterna innan mål tjänsten stoppas.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-184">If enabled, `Set-Service` stops the dependent services before the target service is stopped.</span></span> <span data-ttu-id="1a5b8-185">Som standard höjs undantag när andra tjänster som körs är beroende av mål tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-185">By default, exceptions are raised when other running services depend on the target service.</span></span>

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

### <span data-ttu-id="1a5b8-186">– InputObject</span><span class="sxs-lookup"><span data-stu-id="1a5b8-186">-InputObject</span></span>

<span data-ttu-id="1a5b8-187">Anger ett **ServiceController** -objekt som representerar den tjänst som ska ändras.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-187">Specifies a **ServiceController** object that represents the service to change.</span></span> <span data-ttu-id="1a5b8-188">Ange en variabel som innehåller objektet eller Skriv ett kommando eller uttryck som hämtar objektet, till exempel ett `Get-Service` kommando.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-188">Enter a variable that contains the object, or type a command or expression that gets the object, such as a `Get-Service` command.</span></span> <span data-ttu-id="1a5b8-189">Du kan använda pipelinen för att skicka ett tjänst objekt till `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="1a5b8-189">You can use the pipeline to send a service object to `Set-Service`.</span></span>

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

### <span data-ttu-id="1a5b8-190">-Name</span><span class="sxs-lookup"><span data-stu-id="1a5b8-190">-Name</span></span>

<span data-ttu-id="1a5b8-191">Anger tjänst namnet på den tjänst som ska ändras.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-191">Specifies the service name of the service to be changed.</span></span> <span data-ttu-id="1a5b8-192">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-192">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="1a5b8-193">Du kan använda pipelinen för att skicka ett tjänst namn till `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="1a5b8-193">You can use the pipeline to send a service name to `Set-Service`.</span></span>

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

### <span data-ttu-id="1a5b8-194">– PassThru</span><span class="sxs-lookup"><span data-stu-id="1a5b8-194">-PassThru</span></span>

<span data-ttu-id="1a5b8-195">Returnerar ett **ServiceController** -objekt som representerar de tjänster som har ändrats.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-195">Returns a **ServiceController** object that represents the services that were changed.</span></span> <span data-ttu-id="1a5b8-196">Som standard `Set-Service` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-196">By default, `Set-Service` doesn't generate any output.</span></span>

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

### <span data-ttu-id="1a5b8-197">– Startuptype tjänst</span><span class="sxs-lookup"><span data-stu-id="1a5b8-197">-StartupType</span></span>

<span data-ttu-id="1a5b8-198">Anger tjänstens start läge.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-198">Specifies the start mode of the service.</span></span>

<span data-ttu-id="1a5b8-199">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="1a5b8-199">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1a5b8-200">**Automatiskt** – tjänsten startas eller startades av operativ systemet vid system start.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-200">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="1a5b8-201">Om en automatiskt startad tjänst är beroende av en manuellt startad tjänst startas automatiskt den manuellt startade tjänsten automatiskt vid system start.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-201">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="1a5b8-202">**AutomaticDelayedStart** – startar strax efter att systemet har startat.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-202">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="1a5b8-203">**Disabled** – tjänsten är inaktive rad och kan inte startas av en användare eller ett program.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-203">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="1a5b8-204">**InvalidValue** – har ingen inverkan.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-204">**InvalidValue** - Has no effect.</span></span> <span data-ttu-id="1a5b8-205">Cmdleten returnerar inte ett fel, men Startuptype tjänst för tjänsten har inte ändrats.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-205">The cmdlet does not return an error but the StartupType of the service is not changed.</span></span>
- <span data-ttu-id="1a5b8-206">**Manuell** – tjänsten startas endast manuellt, av en användare, med hjälp av tjänst hanteraren eller av ett program.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-206">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases: StartMode, SM, ST
Accepted values: Automatic, AutomaticDelayedStart, Disabled, InvalidValue, Manual

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a5b8-207">-Status</span><span class="sxs-lookup"><span data-stu-id="1a5b8-207">-Status</span></span>

<span data-ttu-id="1a5b8-208">Anger tjänstens status.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-208">Specifies the status for the service.</span></span>

<span data-ttu-id="1a5b8-209">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="1a5b8-209">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1a5b8-210">**Pausat**.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-210">**Paused**.</span></span> <span data-ttu-id="1a5b8-211">Pausar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-211">Suspends the service.</span></span>
- <span data-ttu-id="1a5b8-212">**Körs**.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-212">**Running**.</span></span> <span data-ttu-id="1a5b8-213">Startar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-213">Starts the service.</span></span>
- <span data-ttu-id="1a5b8-214">**Stoppades**.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-214">**Stopped**.</span></span> <span data-ttu-id="1a5b8-215">Stoppar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-215">Stops the service.</span></span>

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

### <span data-ttu-id="1a5b8-216">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1a5b8-216">-WhatIf</span></span>

<span data-ttu-id="1a5b8-217">Visar vad som händer om `Set-Service` körs.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-217">Shows what would happen if `Set-Service` runs.</span></span> <span data-ttu-id="1a5b8-218">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-218">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="1a5b8-219">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1a5b8-219">CommonParameters</span></span>

<span data-ttu-id="1a5b8-220">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-220">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1a5b8-221">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1a5b8-221">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1a5b8-222">INDATA</span><span class="sxs-lookup"><span data-stu-id="1a5b8-222">INPUTS</span></span>

### <span data-ttu-id="1a5b8-223">System. ServiceProcess. ServiceController, system. String</span><span class="sxs-lookup"><span data-stu-id="1a5b8-223">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="1a5b8-224">Du kan använda pipelinen för att skicka ett tjänst objekt eller en sträng som innehåller ett tjänst namn till `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="1a5b8-224">You can use the pipeline to send a service object or a string that contains a service name to `Set-Service`.</span></span>

## <span data-ttu-id="1a5b8-225">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1a5b8-225">OUTPUTS</span></span>

### <span data-ttu-id="1a5b8-226">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="1a5b8-226">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="1a5b8-227">Som standard `Set-Service` returnerar inte några objekt.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-227">By default, `Set-Service` doesn't return any objects.</span></span> <span data-ttu-id="1a5b8-228">Använd parametern **Passthru** för att mata ut ett **ServiceController** -objekt.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-228">Use the **PassThru** parameter to output a **ServiceController** object.</span></span>

## <span data-ttu-id="1a5b8-229">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1a5b8-229">NOTES</span></span>

<span data-ttu-id="1a5b8-230">`Set-Service` kräver förhöjd behörighet.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-230">`Set-Service` requires elevated permissions.</span></span> <span data-ttu-id="1a5b8-231">Använd alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="1a5b8-231">Use the **Run as administrator** option.</span></span>

<span data-ttu-id="1a5b8-232">`Set-Service` Det går bara att kontrol lera tjänster när den aktuella användaren har behörighet att hantera tjänster.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-232">`Set-Service` can only control services when the current user has permissions to manage services.</span></span> <span data-ttu-id="1a5b8-233">Om ett kommando inte fungerar som det ska kanske du inte har de behörigheter som krävs.</span><span class="sxs-lookup"><span data-stu-id="1a5b8-233">If a command doesn't work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="1a5b8-234">Använd om du vill hitta tjänstens namn eller visnings namn för tjänsten `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="1a5b8-234">To find a service's service name or display name, use `Get-Service`.</span></span> <span data-ttu-id="1a5b8-235">Tjänst namnen finns i kolumnen **namn** och visnings namnen är i kolumnen **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="1a5b8-235">The service names are in the **Name** column and the display names are in the **DisplayName** column.</span></span>

## <span data-ttu-id="1a5b8-236">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1a5b8-236">RELATED LINKS</span></span>

[<span data-ttu-id="1a5b8-237">Get-Service</span><span class="sxs-lookup"><span data-stu-id="1a5b8-237">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="1a5b8-238">New-Service</span><span class="sxs-lookup"><span data-stu-id="1a5b8-238">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="1a5b8-239">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="1a5b8-239">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="1a5b8-240">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="1a5b8-240">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="1a5b8-241">Start-Service</span><span class="sxs-lookup"><span data-stu-id="1a5b8-241">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="1a5b8-242">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="1a5b8-242">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="1a5b8-243">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="1a5b8-243">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="1a5b8-244">Remove-service</span><span class="sxs-lookup"><span data-stu-id="1a5b8-244">Remove-Service</span></span>](Remove-Service.md)
