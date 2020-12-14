---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: 39c03ec53056c5ec8e2d68f9b71a17a6f4a8ea8a
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890424"
---
# <span data-ttu-id="94f8c-103">New-Service</span><span class="sxs-lookup"><span data-stu-id="94f8c-103">New-Service</span></span>

## <span data-ttu-id="94f8c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="94f8c-104">SYNOPSIS</span></span>
<span data-ttu-id="94f8c-105">Skapar en ny Windows-tjänst.</span><span class="sxs-lookup"><span data-stu-id="94f8c-105">Creates a new Windows service.</span></span>

## <span data-ttu-id="94f8c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="94f8c-106">SYNTAX</span></span>

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-SecurityDescriptorSddl <String>] [-StartupType <ServiceStartupType>] [-Credential <PSCredential>]
 [-DependsOn <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="94f8c-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="94f8c-107">DESCRIPTION</span></span>

<span data-ttu-id="94f8c-108">`New-Service`Cmdleten skapar en ny post för en Windows-tjänst i registret och i tjänst databasen.</span><span class="sxs-lookup"><span data-stu-id="94f8c-108">The `New-Service` cmdlet creates a new entry for a Windows service in the registry and in the service database.</span></span> <span data-ttu-id="94f8c-109">En ny tjänst kräver en körbar fil som körs under tjänsten.</span><span class="sxs-lookup"><span data-stu-id="94f8c-109">A new service requires an executable file that runs during the service.</span></span>

<span data-ttu-id="94f8c-110">Med parametrarna för denna cmdlet kan du ange visnings namn, beskrivning, start typ och beroenden för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="94f8c-110">The parameters of this cmdlet let you set the display name, description, startup type, and dependencies of the service.</span></span>

## <span data-ttu-id="94f8c-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="94f8c-111">EXAMPLES</span></span>

### <span data-ttu-id="94f8c-112">Exempel 1: skapa en tjänst</span><span class="sxs-lookup"><span data-stu-id="94f8c-112">Example 1: Create a service</span></span>

```powershell
New-Service -Name "TestService" -BinaryPathName '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
```

<span data-ttu-id="94f8c-113">Det här kommandot skapar en tjänst med namnet TestService.</span><span class="sxs-lookup"><span data-stu-id="94f8c-113">This command creates a service named TestService.</span></span>

### <span data-ttu-id="94f8c-114">Exempel 2: skapa en tjänst som innehåller beskrivning, start typ och visnings namn</span><span class="sxs-lookup"><span data-stu-id="94f8c-114">Example 2: Create a service that includes description, startup type, and display name</span></span>

```powershell
$params = @{
  Name = "TestService"
  BinaryPathName = '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
  DependsOn = "NetLogon"
  DisplayName = "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
}
New-Service @params
```

<span data-ttu-id="94f8c-115">Det här kommandot skapar en tjänst med namnet TestService.</span><span class="sxs-lookup"><span data-stu-id="94f8c-115">This command creates a service named TestService.</span></span> <span data-ttu-id="94f8c-116">Den använder parametrarna för `New-Service` för att ange en beskrivning, starttyp och visnings namn för den nya tjänsten.</span><span class="sxs-lookup"><span data-stu-id="94f8c-116">It uses the parameters of `New-Service` to specify a description, startup type, and display name for the new service.</span></span>

### <span data-ttu-id="94f8c-117">Exempel 3: Visa den nya tjänsten</span><span class="sxs-lookup"><span data-stu-id="94f8c-117">Example 3: View the new service</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -Filter "Name='testservice'"
```

```Output
ExitCode  : 0
Name      : testservice
ProcessId : 0
StartMode : Auto
State     : Stopped
Status    : OK
```

<span data-ttu-id="94f8c-118">Det här kommandot används `Get-CimInstance` för att hämta **Win32_Service** -objektet för den nya tjänsten.</span><span class="sxs-lookup"><span data-stu-id="94f8c-118">This command uses `Get-CimInstance` to get the **Win32_Service** object for the new service.</span></span> <span data-ttu-id="94f8c-119">Det här objektet innehåller start-och tjänst beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="94f8c-119">This object includes the start mode and the service description.</span></span>

### <span data-ttu-id="94f8c-120">Exempel 4: Ange adtagent för en tjänst när du skapar.</span><span class="sxs-lookup"><span data-stu-id="94f8c-120">Example 4: Set the SecurityDescriptor of a service when creating.</span></span>

<span data-ttu-id="94f8c-121">Det här exemplet lägger till **adtagent** för den tjänst som skapas.</span><span class="sxs-lookup"><span data-stu-id="94f8c-121">This example adds the **SecurityDescriptor** of the service being created.</span></span>

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
$params = @{
  BinaryPathName = '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
  DependsOn = "NetLogon"
  DisplayName "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
  SecurityDescriptorSddl = $SDDL
}
New-Service @params
```

<span data-ttu-id="94f8c-122">**Adtagent** lagras i `$SDDLToSet` variabeln.</span><span class="sxs-lookup"><span data-stu-id="94f8c-122">The **SecurityDescriptor** is stored in the `$SDDLToSet` variable.</span></span> <span data-ttu-id="94f8c-123">**SecurityDescriptorSddl** -parametern använder `$SDDL` för att ange **adtagent** för den nya tjänsten.</span><span class="sxs-lookup"><span data-stu-id="94f8c-123">The **SecurityDescriptorSddl** parameter uses `$SDDL` to set the **SecurityDescriptor** of the new service.</span></span>

## <span data-ttu-id="94f8c-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="94f8c-124">PARAMETERS</span></span>

### <span data-ttu-id="94f8c-125">-BinaryPathName</span><span class="sxs-lookup"><span data-stu-id="94f8c-125">-BinaryPathName</span></span>

<span data-ttu-id="94f8c-126">Anger sökvägen till tjänstens körbara fil.</span><span class="sxs-lookup"><span data-stu-id="94f8c-126">Specifies the path of the executable file for the service.</span></span> <span data-ttu-id="94f8c-127">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="94f8c-127">This parameter is required.</span></span>

<span data-ttu-id="94f8c-128">Den fullständigt kvalificerade sökvägen till den binära filen för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="94f8c-128">The fully qualified path to the service binary file.</span></span> <span data-ttu-id="94f8c-129">Om sökvägen innehåller ett blank steg måste den vara citerad så att den tolkas korrekt.</span><span class="sxs-lookup"><span data-stu-id="94f8c-129">If the path contains a space, it must be quoted so that it is correctly interpreted.</span></span> <span data-ttu-id="94f8c-130">Ska till exempel `d:\my share\myservice.exe` anges som `'"d:\my share\myservice.exe"'` .</span><span class="sxs-lookup"><span data-stu-id="94f8c-130">For example, `d:\my share\myservice.exe` should be specified as `'"d:\my share\myservice.exe"'`.</span></span>

<span data-ttu-id="94f8c-131">Sökvägen kan även innehålla argument för en tjänst för automatisk start.</span><span class="sxs-lookup"><span data-stu-id="94f8c-131">The path can also include arguments for an auto-start service.</span></span> <span data-ttu-id="94f8c-132">Ett exempel är `'"d:\myshare\myservice.exe arg1 arg2"'`.</span><span class="sxs-lookup"><span data-stu-id="94f8c-132">For example, `'"d:\myshare\myservice.exe arg1 arg2"'`.</span></span> <span data-ttu-id="94f8c-133">Dessa argument skickas till tjänst start punkten.</span><span class="sxs-lookup"><span data-stu-id="94f8c-133">These arguments are passed to the service entry point.</span></span>

<span data-ttu-id="94f8c-134">Mer information finns i **lpBinaryPathName** -parametern för [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) -API: et.</span><span class="sxs-lookup"><span data-stu-id="94f8c-134">For more information, see the **lpBinaryPathName** parameter of [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) API.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="94f8c-135">-Credential</span><span class="sxs-lookup"><span data-stu-id="94f8c-135">-Credential</span></span>

<span data-ttu-id="94f8c-136">Anger kontot som används av tjänsten som [tjänst inloggnings konto](/windows/desktop/ad/about-service-logon-accounts).</span><span class="sxs-lookup"><span data-stu-id="94f8c-136">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="94f8c-137">Ange ett användar namn, till exempel **user01** eller **Domain01\User01**, eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="94f8c-137">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="94f8c-138">Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="94f8c-138">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="94f8c-139">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="94f8c-139">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="94f8c-140">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="94f8c-140">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="94f8c-141">– DependsOn</span><span class="sxs-lookup"><span data-stu-id="94f8c-141">-DependsOn</span></span>

<span data-ttu-id="94f8c-142">Anger namnen på andra tjänster som den nya tjänsten är beroende av.</span><span class="sxs-lookup"><span data-stu-id="94f8c-142">Specifies the names of other services upon which the new service depends.</span></span> <span data-ttu-id="94f8c-143">Om du vill ange flera tjänst namn använder du ett kommatecken för att avgränsa namnen.</span><span class="sxs-lookup"><span data-stu-id="94f8c-143">To enter multiple service names, use a comma to separate the names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="94f8c-144">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="94f8c-144">-Description</span></span>

<span data-ttu-id="94f8c-145">Anger en beskrivning av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="94f8c-145">Specifies a description of the service.</span></span>

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

### <span data-ttu-id="94f8c-146">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="94f8c-146">-DisplayName</span></span>

<span data-ttu-id="94f8c-147">Anger ett visnings namn för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="94f8c-147">Specifies a display name for the service.</span></span>

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

### <span data-ttu-id="94f8c-148">-Name</span><span class="sxs-lookup"><span data-stu-id="94f8c-148">-Name</span></span>

<span data-ttu-id="94f8c-149">Anger namnet på tjänsten.</span><span class="sxs-lookup"><span data-stu-id="94f8c-149">Specifies the name of the service.</span></span> <span data-ttu-id="94f8c-150">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="94f8c-150">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="94f8c-151">– Startuptype tjänst</span><span class="sxs-lookup"><span data-stu-id="94f8c-151">-StartupType</span></span>

<span data-ttu-id="94f8c-152">Anger tjänstens starttyp.</span><span class="sxs-lookup"><span data-stu-id="94f8c-152">Sets the startup type of the service.</span></span> <span data-ttu-id="94f8c-153">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="94f8c-153">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="94f8c-154">**Automatiskt** – tjänsten startas eller startades av operativ systemet vid system start.</span><span class="sxs-lookup"><span data-stu-id="94f8c-154">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="94f8c-155">Om en automatiskt startad tjänst är beroende av en manuellt startad tjänst startas automatiskt den manuellt startade tjänsten automatiskt vid system start.</span><span class="sxs-lookup"><span data-stu-id="94f8c-155">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="94f8c-156">**AutomaticDelayedStart** – startar strax efter att systemet har startat.</span><span class="sxs-lookup"><span data-stu-id="94f8c-156">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="94f8c-157">**Disabled** – tjänsten är inaktive rad och kan inte startas av en användare eller ett program.</span><span class="sxs-lookup"><span data-stu-id="94f8c-157">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="94f8c-158">**InvalidValue** – det här värdet stöds inte.</span><span class="sxs-lookup"><span data-stu-id="94f8c-158">**InvalidValue** - This value is not supported.</span></span> <span data-ttu-id="94f8c-159">Om det här värdet används uppstår ett fel.</span><span class="sxs-lookup"><span data-stu-id="94f8c-159">Using this value results in an error.</span></span>
- <span data-ttu-id="94f8c-160">**Manuell** – tjänsten startas endast manuellt, av en användare, med hjälp av tjänst hanteraren eller av ett program.</span><span class="sxs-lookup"><span data-stu-id="94f8c-160">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

 <span data-ttu-id="94f8c-161">Standardvärdet är **Automatisk**.</span><span class="sxs-lookup"><span data-stu-id="94f8c-161">The default value is **Automatic**.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases:
Accepted values: Automatic, Manual, Disabled, AutomaticDelayedStart, InvalidValue

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="94f8c-162">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="94f8c-162">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="94f8c-163">Anger **adtagent** för tjänsten i **SDDL** -format.</span><span class="sxs-lookup"><span data-stu-id="94f8c-163">Specifies the **SecurityDescriptor** for the service in **Sddl** format.</span></span>

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

### <span data-ttu-id="94f8c-164">-Confirm</span><span class="sxs-lookup"><span data-stu-id="94f8c-164">-Confirm</span></span>

<span data-ttu-id="94f8c-165">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="94f8c-165">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="94f8c-166">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="94f8c-166">-WhatIf</span></span>

<span data-ttu-id="94f8c-167">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="94f8c-167">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="94f8c-168">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="94f8c-168">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="94f8c-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="94f8c-169">CommonParameters</span></span>

<span data-ttu-id="94f8c-170">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="94f8c-170">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="94f8c-171">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="94f8c-171">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="94f8c-172">INDATA</span><span class="sxs-lookup"><span data-stu-id="94f8c-172">INPUTS</span></span>

### <span data-ttu-id="94f8c-173">Inga</span><span class="sxs-lookup"><span data-stu-id="94f8c-173">None</span></span>

<span data-ttu-id="94f8c-174">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94f8c-174">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="94f8c-175">UTDATA</span><span class="sxs-lookup"><span data-stu-id="94f8c-175">OUTPUTS</span></span>

### <span data-ttu-id="94f8c-176">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="94f8c-176">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="94f8c-177">Denna cmdlet returnerar ett objekt som representerar den nya tjänsten.</span><span class="sxs-lookup"><span data-stu-id="94f8c-177">This cmdlet returns an object that represents the new service.</span></span>

## <span data-ttu-id="94f8c-178">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="94f8c-178">NOTES</span></span>

<span data-ttu-id="94f8c-179">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="94f8c-179">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="94f8c-180">Starta PowerShell med alternativet **Kör som administratör** för att köra denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94f8c-180">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="94f8c-181">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="94f8c-181">RELATED LINKS</span></span>

[<span data-ttu-id="94f8c-182">Get-Service</span><span class="sxs-lookup"><span data-stu-id="94f8c-182">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="94f8c-183">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="94f8c-183">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="94f8c-184">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="94f8c-184">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="94f8c-185">Set-Service</span><span class="sxs-lookup"><span data-stu-id="94f8c-185">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="94f8c-186">Start-Service</span><span class="sxs-lookup"><span data-stu-id="94f8c-186">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="94f8c-187">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="94f8c-187">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="94f8c-188">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="94f8c-188">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="94f8c-189">Remove-service</span><span class="sxs-lookup"><span data-stu-id="94f8c-189">Remove-Service</span></span>](Remove-Service.md)
