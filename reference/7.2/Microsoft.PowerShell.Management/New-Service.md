---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: d3c6d77db88683c134335cf05d0165b542644b7b
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891040"
---
# <span data-ttu-id="19352-102">New-Service</span><span class="sxs-lookup"><span data-stu-id="19352-102">New-Service</span></span>

## <span data-ttu-id="19352-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="19352-103">SYNOPSIS</span></span>
<span data-ttu-id="19352-104">Skapar en ny Windows-tjänst.</span><span class="sxs-lookup"><span data-stu-id="19352-104">Creates a new Windows service.</span></span>

## <span data-ttu-id="19352-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="19352-105">SYNTAX</span></span>

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-SecurityDescriptorSddl <String>] [-StartupType <ServiceStartupType>] [-Credential <PSCredential>]
 [-DependsOn <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="19352-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="19352-106">DESCRIPTION</span></span>

<span data-ttu-id="19352-107">`New-Service`Cmdleten skapar en ny post för en Windows-tjänst i registret och i tjänst databasen.</span><span class="sxs-lookup"><span data-stu-id="19352-107">The `New-Service` cmdlet creates a new entry for a Windows service in the registry and in the service database.</span></span> <span data-ttu-id="19352-108">En ny tjänst kräver en körbar fil som körs under tjänsten.</span><span class="sxs-lookup"><span data-stu-id="19352-108">A new service requires an executable file that runs during the service.</span></span>

<span data-ttu-id="19352-109">Med parametrarna för denna cmdlet kan du ange visnings namn, beskrivning, start typ och beroenden för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="19352-109">The parameters of this cmdlet let you set the display name, description, startup type, and dependencies of the service.</span></span>

## <span data-ttu-id="19352-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="19352-110">EXAMPLES</span></span>

### <span data-ttu-id="19352-111">Exempel 1: skapa en tjänst</span><span class="sxs-lookup"><span data-stu-id="19352-111">Example 1: Create a service</span></span>

```powershell
New-Service -Name "TestService" -BinaryPathName '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
```

<span data-ttu-id="19352-112">Det här kommandot skapar en tjänst med namnet TestService.</span><span class="sxs-lookup"><span data-stu-id="19352-112">This command creates a service named TestService.</span></span>

### <span data-ttu-id="19352-113">Exempel 2: skapa en tjänst som innehåller beskrivning, start typ och visnings namn</span><span class="sxs-lookup"><span data-stu-id="19352-113">Example 2: Create a service that includes description, startup type, and display name</span></span>

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

<span data-ttu-id="19352-114">Det här kommandot skapar en tjänst med namnet TestService.</span><span class="sxs-lookup"><span data-stu-id="19352-114">This command creates a service named TestService.</span></span> <span data-ttu-id="19352-115">Den använder parametrarna för `New-Service` för att ange en beskrivning, starttyp och visnings namn för den nya tjänsten.</span><span class="sxs-lookup"><span data-stu-id="19352-115">It uses the parameters of `New-Service` to specify a description, startup type, and display name for the new service.</span></span>

### <span data-ttu-id="19352-116">Exempel 3: Visa den nya tjänsten</span><span class="sxs-lookup"><span data-stu-id="19352-116">Example 3: View the new service</span></span>

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

<span data-ttu-id="19352-117">Det här kommandot används `Get-CimInstance` för att hämta **Win32_Service** -objektet för den nya tjänsten.</span><span class="sxs-lookup"><span data-stu-id="19352-117">This command uses `Get-CimInstance` to get the **Win32_Service** object for the new service.</span></span> <span data-ttu-id="19352-118">Det här objektet innehåller start-och tjänst beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="19352-118">This object includes the start mode and the service description.</span></span>

### <span data-ttu-id="19352-119">Exempel 4: Ange adtagent för en tjänst när du skapar.</span><span class="sxs-lookup"><span data-stu-id="19352-119">Example 4: Set the SecurityDescriptor of a service when creating.</span></span>

<span data-ttu-id="19352-120">Det här exemplet lägger till **adtagent** för den tjänst som skapas.</span><span class="sxs-lookup"><span data-stu-id="19352-120">This example adds the **SecurityDescriptor** of the service being created.</span></span>

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

<span data-ttu-id="19352-121">**Adtagent** lagras i `$SDDLToSet` variabeln.</span><span class="sxs-lookup"><span data-stu-id="19352-121">The **SecurityDescriptor** is stored in the `$SDDLToSet` variable.</span></span> <span data-ttu-id="19352-122">**SecurityDescriptorSddl** -parametern använder `$SDDL` för att ange **adtagent** för den nya tjänsten.</span><span class="sxs-lookup"><span data-stu-id="19352-122">The **SecurityDescriptorSddl** parameter uses `$SDDL` to set the **SecurityDescriptor** of the new service.</span></span>

## <span data-ttu-id="19352-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="19352-123">PARAMETERS</span></span>

### <span data-ttu-id="19352-124">-BinaryPathName</span><span class="sxs-lookup"><span data-stu-id="19352-124">-BinaryPathName</span></span>

<span data-ttu-id="19352-125">Anger sökvägen till tjänstens körbara fil.</span><span class="sxs-lookup"><span data-stu-id="19352-125">Specifies the path of the executable file for the service.</span></span> <span data-ttu-id="19352-126">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="19352-126">This parameter is required.</span></span>

<span data-ttu-id="19352-127">Den fullständigt kvalificerade sökvägen till den binära filen för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="19352-127">The fully qualified path to the service binary file.</span></span> <span data-ttu-id="19352-128">Om sökvägen innehåller ett blank steg måste den vara citerad så att den tolkas korrekt.</span><span class="sxs-lookup"><span data-stu-id="19352-128">If the path contains a space, it must be quoted so that it is correctly interpreted.</span></span> <span data-ttu-id="19352-129">Ska till exempel `d:\my share\myservice.exe` anges som `'"d:\my share\myservice.exe"'` .</span><span class="sxs-lookup"><span data-stu-id="19352-129">For example, `d:\my share\myservice.exe` should be specified as `'"d:\my share\myservice.exe"'`.</span></span>

<span data-ttu-id="19352-130">Sökvägen kan även innehålla argument för en tjänst för automatisk start.</span><span class="sxs-lookup"><span data-stu-id="19352-130">The path can also include arguments for an auto-start service.</span></span> <span data-ttu-id="19352-131">Ett exempel är `'"d:\myshare\myservice.exe arg1 arg2"'`.</span><span class="sxs-lookup"><span data-stu-id="19352-131">For example, `'"d:\myshare\myservice.exe arg1 arg2"'`.</span></span> <span data-ttu-id="19352-132">Dessa argument skickas till tjänst start punkten.</span><span class="sxs-lookup"><span data-stu-id="19352-132">These arguments are passed to the service entry point.</span></span>

<span data-ttu-id="19352-133">Mer information finns i **lpBinaryPathName** -parametern för [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) -API: et.</span><span class="sxs-lookup"><span data-stu-id="19352-133">For more information, see the **lpBinaryPathName** parameter of [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) API.</span></span>

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

### <span data-ttu-id="19352-134">-Credential</span><span class="sxs-lookup"><span data-stu-id="19352-134">-Credential</span></span>

<span data-ttu-id="19352-135">Anger kontot som används av tjänsten som [tjänst inloggnings konto](/windows/desktop/ad/about-service-logon-accounts).</span><span class="sxs-lookup"><span data-stu-id="19352-135">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="19352-136">Ange ett användar namn, till exempel **user01** eller **Domain01\User01**, eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="19352-136">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="19352-137">Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="19352-137">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="19352-138">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="19352-138">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="19352-139">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="19352-139">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="19352-140">– DependsOn</span><span class="sxs-lookup"><span data-stu-id="19352-140">-DependsOn</span></span>

<span data-ttu-id="19352-141">Anger namnen på andra tjänster som den nya tjänsten är beroende av.</span><span class="sxs-lookup"><span data-stu-id="19352-141">Specifies the names of other services upon which the new service depends.</span></span> <span data-ttu-id="19352-142">Om du vill ange flera tjänst namn använder du ett kommatecken för att avgränsa namnen.</span><span class="sxs-lookup"><span data-stu-id="19352-142">To enter multiple service names, use a comma to separate the names.</span></span>

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

### <span data-ttu-id="19352-143">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="19352-143">-Description</span></span>

<span data-ttu-id="19352-144">Anger en beskrivning av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="19352-144">Specifies a description of the service.</span></span>

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

### <span data-ttu-id="19352-145">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="19352-145">-DisplayName</span></span>

<span data-ttu-id="19352-146">Anger ett visnings namn för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="19352-146">Specifies a display name for the service.</span></span>

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

### <span data-ttu-id="19352-147">-Name</span><span class="sxs-lookup"><span data-stu-id="19352-147">-Name</span></span>

<span data-ttu-id="19352-148">Anger namnet på tjänsten.</span><span class="sxs-lookup"><span data-stu-id="19352-148">Specifies the name of the service.</span></span> <span data-ttu-id="19352-149">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="19352-149">This parameter is required.</span></span>

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

### <span data-ttu-id="19352-150">– Startuptype tjänst</span><span class="sxs-lookup"><span data-stu-id="19352-150">-StartupType</span></span>

<span data-ttu-id="19352-151">Anger tjänstens starttyp.</span><span class="sxs-lookup"><span data-stu-id="19352-151">Sets the startup type of the service.</span></span> <span data-ttu-id="19352-152">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="19352-152">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="19352-153">**Automatiskt** – tjänsten startas eller startades av operativ systemet vid system start.</span><span class="sxs-lookup"><span data-stu-id="19352-153">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="19352-154">Om en automatiskt startad tjänst är beroende av en manuellt startad tjänst startas automatiskt den manuellt startade tjänsten automatiskt vid system start.</span><span class="sxs-lookup"><span data-stu-id="19352-154">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="19352-155">**AutomaticDelayedStart** – startar strax efter att systemet har startat.</span><span class="sxs-lookup"><span data-stu-id="19352-155">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="19352-156">**Disabled** – tjänsten är inaktive rad och kan inte startas av en användare eller ett program.</span><span class="sxs-lookup"><span data-stu-id="19352-156">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="19352-157">**InvalidValue** – det här värdet stöds inte.</span><span class="sxs-lookup"><span data-stu-id="19352-157">**InvalidValue** - This value is not supported.</span></span> <span data-ttu-id="19352-158">Om det här värdet används uppstår ett fel.</span><span class="sxs-lookup"><span data-stu-id="19352-158">Using this value results in an error.</span></span>
- <span data-ttu-id="19352-159">**Manuell** – tjänsten startas endast manuellt, av en användare, med hjälp av tjänst hanteraren eller av ett program.</span><span class="sxs-lookup"><span data-stu-id="19352-159">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

 <span data-ttu-id="19352-160">Standardvärdet är **Automatisk**.</span><span class="sxs-lookup"><span data-stu-id="19352-160">The default value is **Automatic**.</span></span>

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

### <span data-ttu-id="19352-161">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="19352-161">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="19352-162">Anger **adtagent** för tjänsten i **SDDL** -format.</span><span class="sxs-lookup"><span data-stu-id="19352-162">Specifies the **SecurityDescriptor** for the service in **Sddl** format.</span></span>

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

### <span data-ttu-id="19352-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="19352-163">-Confirm</span></span>

<span data-ttu-id="19352-164">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="19352-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="19352-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="19352-165">-WhatIf</span></span>

<span data-ttu-id="19352-166">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="19352-166">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="19352-167">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="19352-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="19352-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="19352-168">CommonParameters</span></span>

<span data-ttu-id="19352-169">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="19352-169">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="19352-170">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="19352-170">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="19352-171">INDATA</span><span class="sxs-lookup"><span data-stu-id="19352-171">INPUTS</span></span>

### <span data-ttu-id="19352-172">Inga</span><span class="sxs-lookup"><span data-stu-id="19352-172">None</span></span>

<span data-ttu-id="19352-173">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="19352-173">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="19352-174">UTDATA</span><span class="sxs-lookup"><span data-stu-id="19352-174">OUTPUTS</span></span>

### <span data-ttu-id="19352-175">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="19352-175">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="19352-176">Denna cmdlet returnerar ett objekt som representerar den nya tjänsten.</span><span class="sxs-lookup"><span data-stu-id="19352-176">This cmdlet returns an object that represents the new service.</span></span>

## <span data-ttu-id="19352-177">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="19352-177">NOTES</span></span>

<span data-ttu-id="19352-178">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="19352-178">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="19352-179">Starta PowerShell med alternativet **Kör som administratör** för att köra denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="19352-179">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="19352-180">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="19352-180">RELATED LINKS</span></span>

[<span data-ttu-id="19352-181">Get-Service</span><span class="sxs-lookup"><span data-stu-id="19352-181">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="19352-182">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="19352-182">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="19352-183">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="19352-183">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="19352-184">Set-Service</span><span class="sxs-lookup"><span data-stu-id="19352-184">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="19352-185">Start-Service</span><span class="sxs-lookup"><span data-stu-id="19352-185">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="19352-186">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="19352-186">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="19352-187">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="19352-187">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="19352-188">Remove-service</span><span class="sxs-lookup"><span data-stu-id="19352-188">Remove-Service</span></span>](Remove-Service.md)
