---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: 3249ce91a63417f2790997d37e2420c6fcb374d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265520"
---
# <span data-ttu-id="894b1-103">New-Service</span><span class="sxs-lookup"><span data-stu-id="894b1-103">New-Service</span></span>

## <span data-ttu-id="894b1-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="894b1-104">SYNOPSIS</span></span>
<span data-ttu-id="894b1-105">Skapar en ny Windows-tjänst.</span><span class="sxs-lookup"><span data-stu-id="894b1-105">Creates a new Windows service.</span></span>

## <span data-ttu-id="894b1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="894b1-106">SYNTAX</span></span>

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Credential <PSCredential>] [-DependsOn <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="894b1-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="894b1-107">DESCRIPTION</span></span>

<span data-ttu-id="894b1-108">`New-Service`Cmdleten skapar en ny post för en Windows-tjänst i registret och i tjänst databasen.</span><span class="sxs-lookup"><span data-stu-id="894b1-108">The `New-Service` cmdlet creates a new entry for a Windows service in the registry and in the service database.</span></span> <span data-ttu-id="894b1-109">En ny tjänst kräver en körbar fil som körs under tjänsten.</span><span class="sxs-lookup"><span data-stu-id="894b1-109">A new service requires an executable file that runs during the service.</span></span>

<span data-ttu-id="894b1-110">Med parametrarna för denna cmdlet kan du ange visnings namn, beskrivning, start typ och beroenden för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="894b1-110">The parameters of this cmdlet let you set the display name, description, startup type, and dependencies of the service.</span></span>

## <span data-ttu-id="894b1-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="894b1-111">EXAMPLES</span></span>

### <span data-ttu-id="894b1-112">Exempel 1: skapa en tjänst</span><span class="sxs-lookup"><span data-stu-id="894b1-112">Example 1: Create a service</span></span>

```powershell
New-Service -Name "TestService" -BinaryPathName "C:\WINDOWS\System32\svchost.exe -k netsvcs"
```

<span data-ttu-id="894b1-113">Det här kommandot skapar en tjänst med namnet TestService.</span><span class="sxs-lookup"><span data-stu-id="894b1-113">This command creates a service named TestService.</span></span>

### <span data-ttu-id="894b1-114">Exempel 2: skapa en tjänst som innehåller beskrivning, start typ och visnings namn</span><span class="sxs-lookup"><span data-stu-id="894b1-114">Example 2: Create a service that includes description, startup type, and display name</span></span>

```powershell
$params = @{
  Name = "TestService"
  BinaryPathName = "C:\WINDOWS\System32\svchost.exe -k netsvcs"
  DependsOn = "NetLogon"
  DisplayName = "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
}
New-Service @params
```

<span data-ttu-id="894b1-115">Det här kommandot skapar en tjänst med namnet TestService.</span><span class="sxs-lookup"><span data-stu-id="894b1-115">This command creates a service named TestService.</span></span> <span data-ttu-id="894b1-116">Den använder parametrarna för `New-Service` för att ange en beskrivning, starttyp och visnings namn för den nya tjänsten.</span><span class="sxs-lookup"><span data-stu-id="894b1-116">It uses the parameters of `New-Service` to specify a description, startup type, and display name for the new service.</span></span>

### <span data-ttu-id="894b1-117">Exempel 3: Visa den nya tjänsten</span><span class="sxs-lookup"><span data-stu-id="894b1-117">Example 3: View the new service</span></span>

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

<span data-ttu-id="894b1-118">Det här kommandot används `Get-CimInstance` för att hämta **Win32_Service** -objektet för den nya tjänsten.</span><span class="sxs-lookup"><span data-stu-id="894b1-118">This command uses `Get-CimInstance` to get the **Win32_Service** object for the new service.</span></span> <span data-ttu-id="894b1-119">Det här objektet innehåller start-och tjänst beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="894b1-119">This object includes the start mode and the service description.</span></span>

### <span data-ttu-id="894b1-120">Exempel 4: ta bort en tjänst</span><span class="sxs-lookup"><span data-stu-id="894b1-120">Example 4: Delete a service</span></span>

```powershell
sc.exe delete TestService
# - or -
(Get-CimInstance -Class Win32_Service -Filter "name='TestService'").delete()
```

<span data-ttu-id="894b1-121">I det här exemplet visas två sätt att ta bort TestService-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="894b1-121">This example shows two ways to delete the TestService service.</span></span> <span data-ttu-id="894b1-122">Det första kommandot använder alternativet ta bort `Sc.exe` .</span><span class="sxs-lookup"><span data-stu-id="894b1-122">The first command uses the delete option of `Sc.exe`.</span></span> <span data-ttu-id="894b1-123">Det andra kommandot använder **Delete** -metoden för **Win32_Service** objekt som `Get-CimInstance` returneras.</span><span class="sxs-lookup"><span data-stu-id="894b1-123">The second command uses the **Delete** method of the **Win32_Service** objects that `Get-CimInstance` returns.</span></span>

## <span data-ttu-id="894b1-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="894b1-124">PARAMETERS</span></span>

### <span data-ttu-id="894b1-125">-BinaryPathName</span><span class="sxs-lookup"><span data-stu-id="894b1-125">-BinaryPathName</span></span>

<span data-ttu-id="894b1-126">Anger sökvägen till tjänstens körbara fil.</span><span class="sxs-lookup"><span data-stu-id="894b1-126">Specifies the path of the executable file for the service.</span></span> <span data-ttu-id="894b1-127">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="894b1-127">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="894b1-128">-Credential</span><span class="sxs-lookup"><span data-stu-id="894b1-128">-Credential</span></span>

<span data-ttu-id="894b1-129">Anger kontot som används av tjänsten som [tjänst inloggnings konto](/windows/desktop/ad/about-service-logon-accounts).</span><span class="sxs-lookup"><span data-stu-id="894b1-129">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="894b1-130">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="894b1-130">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="894b1-131">Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="894b1-131">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="894b1-132">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="894b1-132">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="894b1-133">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="894b1-133">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="894b1-134">– DependsOn</span><span class="sxs-lookup"><span data-stu-id="894b1-134">-DependsOn</span></span>

<span data-ttu-id="894b1-135">Anger namnen på andra tjänster som den nya tjänsten är beroende av.</span><span class="sxs-lookup"><span data-stu-id="894b1-135">Specifies the names of other services upon which the new service depends.</span></span> <span data-ttu-id="894b1-136">Om du vill ange flera tjänst namn använder du ett kommatecken för att avgränsa namnen.</span><span class="sxs-lookup"><span data-stu-id="894b1-136">To enter multiple service names, use a comma to separate the names.</span></span>

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

### <span data-ttu-id="894b1-137">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="894b1-137">-Description</span></span>

<span data-ttu-id="894b1-138">Anger en beskrivning av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="894b1-138">Specifies a description of the service.</span></span>

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

### <span data-ttu-id="894b1-139">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="894b1-139">-DisplayName</span></span>

<span data-ttu-id="894b1-140">Anger ett visnings namn för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="894b1-140">Specifies a display name for the service.</span></span>

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

### <span data-ttu-id="894b1-141">-Name</span><span class="sxs-lookup"><span data-stu-id="894b1-141">-Name</span></span>

<span data-ttu-id="894b1-142">Anger namnet på tjänsten.</span><span class="sxs-lookup"><span data-stu-id="894b1-142">Specifies the name of the service.</span></span>
<span data-ttu-id="894b1-143">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="894b1-143">This parameter is required.</span></span>

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

### <span data-ttu-id="894b1-144">– Startuptype tjänst</span><span class="sxs-lookup"><span data-stu-id="894b1-144">-StartupType</span></span>

<span data-ttu-id="894b1-145">Anger tjänstens starttyp.</span><span class="sxs-lookup"><span data-stu-id="894b1-145">Sets the startup type of the service.</span></span> <span data-ttu-id="894b1-146">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="894b1-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="894b1-147">**Automatiskt** – tjänsten startas eller startades av operativ systemet vid system start.</span><span class="sxs-lookup"><span data-stu-id="894b1-147">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="894b1-148">Om en automatiskt startad tjänst är beroende av en manuellt startad tjänst startas automatiskt den manuellt startade tjänsten automatiskt vid system start.</span><span class="sxs-lookup"><span data-stu-id="894b1-148">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="894b1-149">**Disabled** – tjänsten är inaktive rad och kan inte startas av en användare eller ett program.</span><span class="sxs-lookup"><span data-stu-id="894b1-149">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="894b1-150">**Manuell** – tjänsten startas endast manuellt, av en användare, med hjälp av tjänst hanteraren eller av ett program.</span><span class="sxs-lookup"><span data-stu-id="894b1-150">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>
- <span data-ttu-id="894b1-151">**Boot** -anger att tjänsten är en enhets driv rutin som startas av system inläsaren.</span><span class="sxs-lookup"><span data-stu-id="894b1-151">**Boot** - Indicates that the service is a device driver started by the system loader.</span></span> <span data-ttu-id="894b1-152">Det här värdet är endast giltigt för enhets driv rutiner.</span><span class="sxs-lookup"><span data-stu-id="894b1-152">This value is valid only for device drivers.</span></span>
- <span data-ttu-id="894b1-153">**System** -anger att tjänsten är en enhets driv rutin som startas av funktionen ' IOInitSystem () '.</span><span class="sxs-lookup"><span data-stu-id="894b1-153">**System** - Indicates that the service is a device driver started by the 'IOInitSystem()' function.</span></span> <span data-ttu-id="894b1-154">Det här värdet är endast giltigt för enhets driv rutiner.</span><span class="sxs-lookup"><span data-stu-id="894b1-154">This value is valid only for device drivers.</span></span>

 <span data-ttu-id="894b1-155">Standardvärdet är **Automatisk**.</span><span class="sxs-lookup"><span data-stu-id="894b1-155">The default value is **Automatic**.</span></span>

```yaml
Type: System.ServiceProcess.ServiceStartMode
Parameter Sets: (All)
Aliases:
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="894b1-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="894b1-156">-Confirm</span></span>

<span data-ttu-id="894b1-157">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="894b1-157">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="894b1-158">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="894b1-158">-WhatIf</span></span>

<span data-ttu-id="894b1-159">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="894b1-159">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="894b1-160">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="894b1-160">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="894b1-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="894b1-161">CommonParameters</span></span>

<span data-ttu-id="894b1-162">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="894b1-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="894b1-163">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="894b1-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="894b1-164">INDATA</span><span class="sxs-lookup"><span data-stu-id="894b1-164">INPUTS</span></span>

### <span data-ttu-id="894b1-165">Inget</span><span class="sxs-lookup"><span data-stu-id="894b1-165">None</span></span>

<span data-ttu-id="894b1-166">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="894b1-166">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="894b1-167">UTDATA</span><span class="sxs-lookup"><span data-stu-id="894b1-167">OUTPUTS</span></span>

### <span data-ttu-id="894b1-168">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="894b1-168">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="894b1-169">Denna cmdlet returnerar ett objekt som representerar den nya tjänsten.</span><span class="sxs-lookup"><span data-stu-id="894b1-169">This cmdlet returns an object that represents the new service.</span></span>

## <span data-ttu-id="894b1-170">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="894b1-170">NOTES</span></span>

<span data-ttu-id="894b1-171">Om du vill köra den här cmdleten på Windows Vista och senare versioner av Windows-operativsystemet startar du PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="894b1-171">To run this cmdlet on Windows Vista and later versions of the Windows operating system, start PowerShell by using the Run as administrator option.</span></span>

<span data-ttu-id="894b1-172">Om du vill ta bort en tjänst använder du Sc.exe eller använder `Get-CimInstance` cmdleten för att hämta **Win32_Service** -objektet som representerar tjänsten och använder sedan **Delete** -metoden för att ta bort tjänsten.</span><span class="sxs-lookup"><span data-stu-id="894b1-172">To delete a service, use Sc.exe, or use the `Get-CimInstance` cmdlet to get the **Win32_Service** object that represents the service and then use the **Delete** method to delete the service.</span></span> <span data-ttu-id="894b1-173">Objektet som `Get-Service` returnerar har ingen Delete-metod.</span><span class="sxs-lookup"><span data-stu-id="894b1-173">The object that `Get-Service` returns does not have a delete method.</span></span>

## <span data-ttu-id="894b1-174">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="894b1-174">RELATED LINKS</span></span>

[<span data-ttu-id="894b1-175">Get-Service</span><span class="sxs-lookup"><span data-stu-id="894b1-175">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="894b1-176">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="894b1-176">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="894b1-177">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="894b1-177">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="894b1-178">Set-Service</span><span class="sxs-lookup"><span data-stu-id="894b1-178">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="894b1-179">Start-Service</span><span class="sxs-lookup"><span data-stu-id="894b1-179">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="894b1-180">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="894b1-180">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="894b1-181">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="894b1-181">Suspend-Service</span></span>](Suspend-Service.md)
