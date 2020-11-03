---
description: WSMan
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_wsman_provider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: WSMan-Provider
ms.openlocfilehash: 962684fceaa8fdf16985df56fb4fcdb830bb828b
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273170"
---
# <a name="wsman-provider"></a><span data-ttu-id="16566-104">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="16566-104">WSMan Provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="16566-105">Providernamn</span><span class="sxs-lookup"><span data-stu-id="16566-105">Provider name</span></span>

<span data-ttu-id="16566-106">WSMan</span><span class="sxs-lookup"><span data-stu-id="16566-106">WSMan</span></span>

## <a name="drives"></a><span data-ttu-id="16566-107">Enheter</span><span class="sxs-lookup"><span data-stu-id="16566-107">Drives</span></span>

`WSMan:`

## <a name="short-description"></a><span data-ttu-id="16566-108">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="16566-108">Short description</span></span>

<span data-ttu-id="16566-109">Ger åtkomst till konfigurations information för hantering av webb tjänster (WS-Management).</span><span class="sxs-lookup"><span data-stu-id="16566-109">Provides access to Web Services for Management (WS-Management) configuration information.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="16566-110">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="16566-110">Detailed description</span></span>

<span data-ttu-id="16566-111">Med **WSMan** -providern för PowerShell kan du lägga till, ändra, rensa och ta bort WS-Management konfigurations data på lokala eller fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="16566-111">The **WSMan** provider for PowerShell lets you add, change, clear, and delete WS-Management configuration data on local or remote computers.</span></span>

<span data-ttu-id="16566-112">**WSMan** -providern exponerar en PowerShell-enhet med en katalog struktur som motsvarar en logisk gruppering av WS-Management konfigurations inställningar.</span><span class="sxs-lookup"><span data-stu-id="16566-112">The **WSMan** provider exposes a PowerShell drive with a directory structure that corresponds to a logical grouping of WS-Management configuration settings.</span></span> <span data-ttu-id="16566-113">Dessa grupperingar kallas behållare.</span><span class="sxs-lookup"><span data-stu-id="16566-113">These groupings are known as containers.</span></span>

<span data-ttu-id="16566-114">Från och med Windows PowerShell 3,0 har **WSMan** -providern uppdaterats för att stödja nya egenskaper för sessionsinställningar, till exempel **OutputBufferingMode**.</span><span class="sxs-lookup"><span data-stu-id="16566-114">Beginning in Windows PowerShell 3.0, the **WSMan** provider has been updated to support new properties for session configurations, such as **OutputBufferingMode**.</span></span> <span data-ttu-id="16566-115">Sessionens konfigurationer visas som objekt i katalogen plugin-program för `WSMan:` enheten och egenskaperna visas som objekt i varje konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="16566-115">The session configurations appear as items in the Plugin directory of the `WSMan:` drive and the properties appear as items in each session configuration.</span></span>

<span data-ttu-id="16566-116">**WSMan** -providern stöder följande cmdletar, som beskrivs i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="16566-116">The **WSMan** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="16566-117">Get-location</span><span class="sxs-lookup"><span data-stu-id="16566-117">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="16566-118">Ange plats</span><span class="sxs-lookup"><span data-stu-id="16566-118">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="16566-119">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="16566-119">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="16566-120">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="16566-120">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="16566-121">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-121">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="16566-122">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="16566-122">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)

> [!NOTE]
> <span data-ttu-id="16566-123">Du kan använda kommandon i `WSMan:` enheten för att ändra värdena för de nya egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="16566-123">You can use commands in the `WSMan:` drive to change the values of the new properties.</span></span> <span data-ttu-id="16566-124">Du kan dock inte använda `WSMan:` enheten i PowerShell 2,0 för att ändra egenskaper som introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="16566-124">However, you cannot use the `WSMan:` drive in PowerShell 2.0 to change properties that are introduced in Windows PowerShell 3.0.</span></span>
> <span data-ttu-id="16566-125">Även om inget fel genereras är kommandona inte effektiva att ändra inställningarna, använda **WSMan** -enheten i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="16566-125">Although no error is generated, the commands are not effective To change these settings, use the **WSMan** drive in Windows PowerShell 3.0.</span></span>

### <a name="organization-of-the-wsman-drive"></a><span data-ttu-id="16566-126">Organisation för WSMan: Drive</span><span class="sxs-lookup"><span data-stu-id="16566-126">Organization of the WSMan: Drive</span></span>

- <span data-ttu-id="16566-127">**Klient** : du kan konfigurera olika aspekter av WS-Management-klienten.</span><span class="sxs-lookup"><span data-stu-id="16566-127">**Client** : You can configure various aspects of the WS-Management client.</span></span> <span data-ttu-id="16566-128">Konfigurations informationen lagras i registret.</span><span class="sxs-lookup"><span data-stu-id="16566-128">The configuration information is stored in the registry.</span></span>

- <span data-ttu-id="16566-129">**Tjänst** : du kan konfigurera olika aspekter av tjänsten WS-Management.</span><span class="sxs-lookup"><span data-stu-id="16566-129">**Service** : You can configure various aspects of the WS-Management service.</span></span>
  <span data-ttu-id="16566-130">Konfigurations informationen lagras i registret.</span><span class="sxs-lookup"><span data-stu-id="16566-130">The configuration information is stored in the registry.</span></span>
  > [!NOTE]
  > <span data-ttu-id="16566-131">Tjänst konfigurationen kallas ibland för Server konfiguration.</span><span class="sxs-lookup"><span data-stu-id="16566-131">Service configuration is sometimes referred to as Server configuration.</span></span>

- <span data-ttu-id="16566-132">**Shell** : du kan konfigurera olika aspekter av WS-Management Shell, till exempel inställningen att tillåta fjärråtkomst ( **AllowRemoteShellAccess** ) och det maximala antalet samtidiga användare som tillåts ( **MaxConcurrentUsers** ).</span><span class="sxs-lookup"><span data-stu-id="16566-132">**Shell** : You can configure various aspects of the WS-Management shell, such as the setting to allow remote shell access ( **AllowRemoteShellAccess** ) and the maximum number of concurrent users allowed ( **MaxConcurrentUsers** ).</span></span>

- <span data-ttu-id="16566-133">**Lyssnare** : du kan skapa och konfigurera en lyssnare.</span><span class="sxs-lookup"><span data-stu-id="16566-133">**Listener** : You can create and configure a listener.</span></span> <span data-ttu-id="16566-134">En lyssnare är en hanterings tjänst som implementerar WS-Management protokoll för att skicka och ta emot meddelanden.</span><span class="sxs-lookup"><span data-stu-id="16566-134">A listener is a management service that implements the WS-Management protocol to send and to receive messages.</span></span>

- <span data-ttu-id="16566-135">**Plugin** : plugin-program läses in och används av WS-Managements tjänsten för att tillhandahålla olika funktioner.</span><span class="sxs-lookup"><span data-stu-id="16566-135">**Plugin** : Plug-ins are loaded and used by the WS-Management service to provide various functions.</span></span> <span data-ttu-id="16566-136">Som standard tillhandahåller PowerShell tre plugin-program:</span><span class="sxs-lookup"><span data-stu-id="16566-136">By default, PowerShell provides three plug-ins:</span></span>
  - <span data-ttu-id="16566-137">Plugin-programmet för Event Forwarding.</span><span class="sxs-lookup"><span data-stu-id="16566-137">The Event Forwarding plug-in.</span></span>
  - <span data-ttu-id="16566-138">Microsoft. PowerShell-plugin-programmet.</span><span class="sxs-lookup"><span data-stu-id="16566-138">The Microsoft.PowerShell plug-in.</span></span>
  - <span data-ttu-id="16566-139">Plugin-programmet för Windows Management Instrumentation (WMI) providern.</span><span class="sxs-lookup"><span data-stu-id="16566-139">The Windows Management Instrumentation (WMI) Provider plug-in.</span></span>
  <span data-ttu-id="16566-140">Dessa tre plugin-program stöder vidarebefordran av händelser, konfiguration och WMI-åtkomst.</span><span class="sxs-lookup"><span data-stu-id="16566-140">These three plug-ins support event forwarding, configuration, and WMI access.</span></span>

- <span data-ttu-id="16566-141">**ClientCertificate** : du kan skapa och konfigurera ett klient certifikat.</span><span class="sxs-lookup"><span data-stu-id="16566-141">**ClientCertificate** : You can create and configure a client certificate.</span></span>
  <span data-ttu-id="16566-142">Ett klient certifikat används när den WS-Management klienten är konfigurerad för att använda certifikatautentisering.</span><span class="sxs-lookup"><span data-stu-id="16566-142">A client certificate is used when the WS-Management client is configured to use certificate authentication.</span></span>

### <a name="directory-hierarchy-of-the-wsman-provider"></a><span data-ttu-id="16566-143">Katalog-hierarki för WSMan-providern</span><span class="sxs-lookup"><span data-stu-id="16566-143">Directory Hierarchy of the WSMan Provider</span></span>

<span data-ttu-id="16566-144">Katalog-hierarkin för WSMan-providern för den lokala datorn är följande.</span><span class="sxs-lookup"><span data-stu-id="16566-144">The directory hierarchy of the WSMan provider for the local computer is as follows.</span></span>

```
WSMan:\localhost
--- Client
--- Service
--- Shell
--- Listener
------ <Specific_Listener>
--- Plugin
------ Event Forwarding Plugin
--------- InitializationParameters
--------- Resources
------------ Security
------ Microsoft.Powershell
--------- InitializationParameters
--------- Resources
------------ Security
------ WMI Provider
--------- InitializationParameters
--------- Resources
------------ Security
--- ClientCertificate
```

<span data-ttu-id="16566-145">Hierarkin för WSMan-providern för en fjärrdator är samma som en lokal dator.</span><span class="sxs-lookup"><span data-stu-id="16566-145">The directory hierarchy of the WSMan provider for a remote computer is the same as a local computer.</span></span> <span data-ttu-id="16566-146">Men för att få åtkomst till konfigurations inställningarna för en fjärrdator måste du upprätta en anslutning till fjärrdatorn med hjälp av [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan).</span><span class="sxs-lookup"><span data-stu-id="16566-146">However, in order to access the configuration settings of a remote computer, you need to make a connection to the remote computer using [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan).</span></span> <span data-ttu-id="16566-147">När en anslutning har gjorts till en fjärrdator visas namnet på fjärrdatorn i providern.</span><span class="sxs-lookup"><span data-stu-id="16566-147">Once a connection is made to a remote computer, the name of the remote computer shows up in the provider.</span></span>

```
WSMan:\<Remote_Computer_Name>
```

## <a name="navigating-the-wsman-drive"></a><span data-ttu-id="16566-148">Navigera i filen WSMan: Drive</span><span class="sxs-lookup"><span data-stu-id="16566-148">Navigating the WSMan: Drive</span></span>

<span data-ttu-id="16566-149">Detta kommando använder `Set-Location` cmdleten för att ändra den aktuella platsen till `WSMan:` enheten.</span><span class="sxs-lookup"><span data-stu-id="16566-149">This command uses the `Set-Location` cmdlet to change the current location to the `WSMan:` drive.</span></span>

```powershell
Set-Location WSMan:
```

<span data-ttu-id="16566-150">Om du vill återgå till en fil systemen het skriver du enhetens namn.</span><span class="sxs-lookup"><span data-stu-id="16566-150">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="16566-151">Skriv till exempel.</span><span class="sxs-lookup"><span data-stu-id="16566-151">For example, type.</span></span>

```powershell
Set-Location C:
```

### <a name="navigating-to-a-remote-system-store-location"></a><span data-ttu-id="16566-152">Navigera till en lagrings plats för fjärrsystem</span><span class="sxs-lookup"><span data-stu-id="16566-152">Navigating to a remote system store location</span></span>

<span data-ttu-id="16566-153">Det här kommandot använder `Set-Location` kommandot för att ändra den aktuella platsen till rot platsen på den fjärranslutna system lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="16566-153">This command uses the `Set-Location` command to change the current location to the root location in the remote system store location.</span></span> <span data-ttu-id="16566-154">Använd ett omvänt snedstreck eller ett snedstreck `\` `/` för att ange `WSMan:` enhetens nivå.</span><span class="sxs-lookup"><span data-stu-id="16566-154">Use a backslash `\` or forward slash `/` to indicate a level of the `WSMan:` drive.</span></span>

```powershell
Set-Location -Path  WSMan:\SERVER01
```

> [!NOTE]
> <span data-ttu-id="16566-155">Kommandot ovan förutsätter att det redan finns en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="16566-155">The above command assume that a connection to the remote system already exists.</span></span>

## <a name="displaying-the-contents-of-the-wsman-drive"></a><span data-ttu-id="16566-156">Visar innehållet i filen WSMan: Drive</span><span class="sxs-lookup"><span data-stu-id="16566-156">Displaying the Contents of the WSMan: Drive</span></span>

<span data-ttu-id="16566-157">Det här kommandot använder `Get-Childitem` cmdlet: en för att visa WS-Management butikerna på localhost-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="16566-157">This command uses the `Get-Childitem` cmdlet to display the WS-Management stores in the Localhost store location.</span></span>

```powershell
Get-ChildItem -path WSMan:\Localhost
```

<span data-ttu-id="16566-158">Om du är i `WSMan:` enheten kan du utelämna enhets namnet.</span><span class="sxs-lookup"><span data-stu-id="16566-158">If you are in the `WSMan:` drive, you can omit the drive name.</span></span>

<span data-ttu-id="16566-159">Det här kommandot använder `Get-Childitem` cmdleten för att visa WS-Management butiker på fjärrdatorn "SERVER01".</span><span class="sxs-lookup"><span data-stu-id="16566-159">This command uses the `Get-Childitem` cmdlet to display the WS-Management stores in the remote computer "SERVER01" store location.</span></span>

```powershell
Get-ChildItem -path WSMan:\SERVER01
```

> [!NOTE]
> <span data-ttu-id="16566-160">Kommandot ovan förutsätter att det redan finns en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="16566-160">The above command assume that a connection to the remote system already exists.</span></span>

## <a name="setting-the-value-of-items-in-the--wsman-drive"></a><span data-ttu-id="16566-161">Ange värdet för objekt i WSMAN: Drive</span><span class="sxs-lookup"><span data-stu-id="16566-161">Setting the value of items in the  WSMAN: drive</span></span>

<span data-ttu-id="16566-162">Du kan använda `Set-Item` cmdleten för att ändra konfigurations inställningarna i `WSMAN` enheten.</span><span class="sxs-lookup"><span data-stu-id="16566-162">You can use the `Set-Item` cmdlet to change configuration settings in the `WSMAN` drive.</span></span> <span data-ttu-id="16566-163">I följande exempel anges värdet **TrustedHosts** för att acceptera alla värdar med suffixet "contoso.com".</span><span class="sxs-lookup"><span data-stu-id="16566-163">The following example sets the **TrustedHosts** value to accept all hosts with the suffix "contoso.com".</span></span>

```powershell
# You do not need to specify the -Path parameter name when using Set-Item.
PS WSMAN:\localhost\Client> Set-Item .\TrustedHosts -Value "*.contoso.com"
```

<span data-ttu-id="16566-164">`Set-Item`Cmdleten stöder ytterligare en parameter `-Concatenate` som lägger till ett värde i stället för att ändra det.</span><span class="sxs-lookup"><span data-stu-id="16566-164">The `Set-Item` cmdlet supports an additional parameter `-Concatenate` that appends a value instead of changing it.</span></span> <span data-ttu-id="16566-165">I följande exempel läggs ett nytt värde "\*. domain2.com" till i det gamla värdet som är lagrat i `TrustedHost:`</span><span class="sxs-lookup"><span data-stu-id="16566-165">The following example will append a new value "\*.domain2.com" to the old value stored in `TrustedHost:`</span></span>

```powershell
Set-Item WSMAN:\localhost\Client\TrustedHosts *.domain2.com -Concatenate
```

## <a name="creating-items-in-the-wsman-drive"></a><span data-ttu-id="16566-166">Skapa objekt i WSMAN: Drive</span><span class="sxs-lookup"><span data-stu-id="16566-166">Creating items in the WSMAN: drive</span></span>

### <a name="creating-a-new-listener"></a><span data-ttu-id="16566-167">Skapa en ny lyssnare</span><span class="sxs-lookup"><span data-stu-id="16566-167">Creating a new listener</span></span>

<span data-ttu-id="16566-168">`New-Item`Cmdleten skapar objekt i en provider.</span><span class="sxs-lookup"><span data-stu-id="16566-168">The `New-Item` cmdlet creates items within a provider drive.</span></span> <span data-ttu-id="16566-169">Varje provider har olika objekt typer som du kan skapa.</span><span class="sxs-lookup"><span data-stu-id="16566-169">Each provider has different item types that you can create.</span></span> <span data-ttu-id="16566-170">I `WSMAN:` enheten kan du skapa *lyssnare* som du konfigurerar för att ta emot och svara på fjärrbegäranden.</span><span class="sxs-lookup"><span data-stu-id="16566-170">In the `WSMAN:` drive, you can create *Listeners* which you configure to receive and respond to remote requests.</span></span> <span data-ttu-id="16566-171">Följande kommando skapar en ny HTTP-lyssnare med hjälp av `New-Item` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="16566-171">The following command creates a new HTTP listener using the `New-Item` cmdlet.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Listener -Address * -Transport HTTP -force
```

### <a name="creating-a-new-plug-in"></a><span data-ttu-id="16566-172">Skapa ett nytt plugin-program</span><span class="sxs-lookup"><span data-stu-id="16566-172">Creating a new plug-in</span></span>

<span data-ttu-id="16566-173">Det här kommandot skapar (registrerar) ett plugin-program för tjänsten WS-Management.</span><span class="sxs-lookup"><span data-stu-id="16566-173">This command creates (registers) a plug-in for the WS-Management service.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin `
         -Plugin TestPlugin `
         -FileName %systemroot%\system32\WsmWmiPl.dll `
         -Resource http://schemas.dmtf.org/wbem/wscim/2/cim-schema `
         -SDKVersion 1 `
         -Capability "Get","Put","Invoke","Enumerate" `
         -XMLRenderingType text
```

### <a name="creating-a-new-resource-entry"></a><span data-ttu-id="16566-174">Skapa en ny resurs post</span><span class="sxs-lookup"><span data-stu-id="16566-174">Creating a new resource entry</span></span>

<span data-ttu-id="16566-175">Det här kommandot skapar en resurs post i resurs katalogen i en TestPlugin.</span><span class="sxs-lookup"><span data-stu-id="16566-175">This command creates a resource entry in the Resources directory of a TestPlugin.</span></span> <span data-ttu-id="16566-176">Det här kommandot förutsätter att en TestPlugin har skapats med ett separat kommando.</span><span class="sxs-lookup"><span data-stu-id="16566-176">This command assumes that a TestPlugin has been created using a separate command.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\Resources `
         -ResourceUri http://schemas.dmtf.org/wbem/wscim/3/cim-schema `
         -Capability "Enumerate"

```

### <a name="creating-a-new-security-entry-for-a-resource"></a><span data-ttu-id="16566-177">Skapa en ny säkerhets post för en resurs</span><span class="sxs-lookup"><span data-stu-id="16566-177">Creating a new security entry for a resource</span></span>

<span data-ttu-id="16566-178">Det här kommandot skapar en säkerhets post i säkerhets katalogen för Resource_5967683 (en angiven resurs).</span><span class="sxs-lookup"><span data-stu-id="16566-178">This command creates a security entry in the Security directory of Resource_5967683 (a specific resource).</span></span> <span data-ttu-id="16566-179">Det här kommandot förutsätter att resurs posten har skapats med ett separat kommando.</span><span class="sxs-lookup"><span data-stu-id="16566-179">This command assumes that the resource entry has been created using a separate command.</span></span>

```powershell
$path = "WSMan:\localhost\Plugin\TestPlugin\Resources\Resource_5967683"
New-Item -Path $path\Security `
         -Sddl "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GWGX;;;WD)"
```

### <a name="creating-a-new-client-certificate"></a><span data-ttu-id="16566-180">Skapa ett nytt klient certifikat</span><span class="sxs-lookup"><span data-stu-id="16566-180">Creating a new Client Certificate</span></span>

<span data-ttu-id="16566-181">Det här kommandot skapar **ClientCertificate** -poster som kan användas av den WS-Management klienten.</span><span class="sxs-lookup"><span data-stu-id="16566-181">This command creates **ClientCertificate** entry that can be used by the WS-Management client.</span></span> <span data-ttu-id="16566-182">Den nya **ClientCertificate** visas under katalogen **ClientCertificate** som "ClientCertificate_1234567890".</span><span class="sxs-lookup"><span data-stu-id="16566-182">The new **ClientCertificate** will show up under the **ClientCertificate** directory as "ClientCertificate_1234567890".</span></span> <span data-ttu-id="16566-183">Alla parametrar är obligatoriska.</span><span class="sxs-lookup"><span data-stu-id="16566-183">All of the parameters are mandatory.</span></span> <span data-ttu-id="16566-184">**Utfärdaren** måste vara tumavtryck för utfärdarcertifikatet.</span><span class="sxs-lookup"><span data-stu-id="16566-184">The **Issuer** needs to be thumbprint of the issuers certificate.</span></span>

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* `
         -Credential $cred;
```

### <a name="creating-a-new-initialization-parameter"></a><span data-ttu-id="16566-185">Skapa en ny initierings parameter</span><span class="sxs-lookup"><span data-stu-id="16566-185">Creating a new Initialization Parameter</span></span>

<span data-ttu-id="16566-186">Det här kommandot skapar en initierings parameter med namnet "testparametername" i katalogen "InitializationParameters".</span><span class="sxs-lookup"><span data-stu-id="16566-186">This command creates an Initialization parameter named "testparametername" in the "InitializationParameters" directory.</span></span> <span data-ttu-id="16566-187">Det här kommandot förutsätter att "TestPlugin" har skapats med ett separat kommando.</span><span class="sxs-lookup"><span data-stu-id="16566-187">This command assumes that the "TestPlugin" has been created using a separate command.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\InitializationParameters `
         -ParamName testparametername `
         -ParamValue testparametervalue
```

## <a name="dynamic-parameters"></a><span data-ttu-id="16566-188">Dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="16566-188">Dynamic parameters</span></span>

<span data-ttu-id="16566-189">Dynamiska parametrar är cmdlet-parametrar som läggs till av en PowerShell-Provider och är bara tillgängliga när cmdleten används i den provider-aktiverade enheten.</span><span class="sxs-lookup"><span data-stu-id="16566-189">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="address-string"></a><span data-ttu-id="16566-190">Adresspool \<String\></span><span class="sxs-lookup"><span data-stu-id="16566-190">Address \<String\></span></span>

<span data-ttu-id="16566-191">Anger adressen som den här lyssnaren skapades för.</span><span class="sxs-lookup"><span data-stu-id="16566-191">Specifies the address for which this listener was created.</span></span> <span data-ttu-id="16566-192">Värdet kan vara något av följande:</span><span class="sxs-lookup"><span data-stu-id="16566-192">The value can be one of the following:</span></span>

- <span data-ttu-id="16566-193">Den litterala strängen "\*".</span><span class="sxs-lookup"><span data-stu-id="16566-193">The literal string "\*".</span></span> <span data-ttu-id="16566-194">(Jokertecknet ( `*` ) gör att kommandot binder alla IP-adresser på alla nätverkskort.)</span><span class="sxs-lookup"><span data-stu-id="16566-194">(The wildcard character (`*`) makes the command bind all the IP addresses on all the network adapters.)</span></span>
- <span data-ttu-id="16566-195">Den litterala strängen "IP:" följt av en giltig IP-adress i antingen IPv4 punktavgränsat decimal format eller i IPv6-klonat-hexadecimalt format.</span><span class="sxs-lookup"><span data-stu-id="16566-195">The literal string "IP:" followed by a valid IP address in either IPv4 dotted-decimal format or in IPv6 cloned-hexadecimal format.</span></span>
- <span data-ttu-id="16566-196">Den litterala strängen "MAC:" följt av MAC-adressen för ett kort.</span><span class="sxs-lookup"><span data-stu-id="16566-196">The literal string "MAC:" followed by the MAC address of an adapter.</span></span>
  <span data-ttu-id="16566-197">Till exempel: MAC: 32-a3-58 -90-CC.</span><span class="sxs-lookup"><span data-stu-id="16566-197">For example: MAC:32-a3-58-90-be-cc.</span></span>

> [!NOTE]
> <span data-ttu-id="16566-198">Värdet Address anges när du skapar en lyssnare.</span><span class="sxs-lookup"><span data-stu-id="16566-198">The Address value is set when creating a Listener.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-199">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-199">Cmdlets supported</span></span>

- [<span data-ttu-id="16566-200">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-200">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="capability-enumeration"></a><span data-ttu-id="16566-201">Funktionen \<Enumeration\></span><span class="sxs-lookup"><span data-stu-id="16566-201">Capability \<Enumeration\></span></span>

<span data-ttu-id="16566-202">När du arbetar med *plugin-program,* anger den här parametern en åtgärd som stöds på den här Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="16566-202">When working with *Plug-ins* this parameter specifies an operation that is supported on this Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="16566-203">Du måste skapa en post för varje typ av åtgärd som URI: n stöder.</span><span class="sxs-lookup"><span data-stu-id="16566-203">You have to create one entry for each type of operation that the URI supports.</span></span> <span data-ttu-id="16566-204">Du kan ange giltiga attribut för en specifik åtgärd, om åtgärden stöder det.</span><span class="sxs-lookup"><span data-stu-id="16566-204">You can specify any valid attributes for a given operation, if the operation supports it.</span></span>

<span data-ttu-id="16566-205">Dessa attribut är **SupportsFiltering** och **SupportsFragment**.</span><span class="sxs-lookup"><span data-stu-id="16566-205">These attributes include **SupportsFiltering** and **SupportsFragment**.</span></span>

- <span data-ttu-id="16566-206">**Skapa** : skapa-åtgärder stöds på URI: n.</span><span class="sxs-lookup"><span data-stu-id="16566-206">**Create** : Create operations are supported on the URI.</span></span>
  - <span data-ttu-id="16566-207">Attributet **SupportFragment**  används om Create-åtgärden stöder konceptet.</span><span class="sxs-lookup"><span data-stu-id="16566-207">The **SupportFragment**  attribute is used if the Create operation supports the concept.</span></span>
  - <span data-ttu-id="16566-208">Attributet **SupportFiltering** är inte giltigt för Create-åtgärder och ska vara inställt på "false".</span><span class="sxs-lookup"><span data-stu-id="16566-208">The **SupportFiltering** attribute is NOT valid for Create operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="16566-209">Den här åtgärden är inte giltig för en URI om Shell-åtgärder också stöds.</span><span class="sxs-lookup"><span data-stu-id="16566-209">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="16566-210">**Ta bort** : borttagnings åtgärder stöds på URI: n.</span><span class="sxs-lookup"><span data-stu-id="16566-210">**Delete** : Delete operations are supported on the URI.</span></span>
  - <span data-ttu-id="16566-211">Attributet **SupportFragment** används om borttagnings åtgärden stöder konceptet.</span><span class="sxs-lookup"><span data-stu-id="16566-211">The **SupportFragment** attribute is used if the Delete operation supports the concept.</span></span>
  - <span data-ttu-id="16566-212">Attributet **SupportFiltering** är inte giltigt för Delete-åtgärder och ska vara inställt på "false".</span><span class="sxs-lookup"><span data-stu-id="16566-212">The **SupportFiltering** attribute is NOT valid for Delete operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="16566-213">Den här åtgärden är inte giltig för en URI om Shell-åtgärder också stöds.</span><span class="sxs-lookup"><span data-stu-id="16566-213">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="16566-214">**Uppräkning** : uppräknings åtgärder stöds på URI: n.</span><span class="sxs-lookup"><span data-stu-id="16566-214">**Enumerate** : Enumerate operations are supported on the URI.</span></span>
  - <span data-ttu-id="16566-215">Attributet **SupportFragment** stöds inte för uppräknings åtgärder och ska vara inställt på false.</span><span class="sxs-lookup"><span data-stu-id="16566-215">The **SupportFragment** attribute is NOT supported for Enumerate operations and should be set to False.</span></span>
  - <span data-ttu-id="16566-216">Attributet **SupportFiltering** är giltigt och om plugin-programmet stöder filtrering ska det här attributet anges till "true".</span><span class="sxs-lookup"><span data-stu-id="16566-216">The **SupportFiltering** attribute is valid, and if the plug-in supports filtering, this attribute should be set to "True".</span></span>
  > [!NOTE]
  > <span data-ttu-id="16566-217">Den här åtgärden är inte giltig för en URI om Shell-åtgärder också stöds.</span><span class="sxs-lookup"><span data-stu-id="16566-217">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="16566-218">**Get** : get-åtgärder stöds på URI: n.</span><span class="sxs-lookup"><span data-stu-id="16566-218">**Get** : Get operations are supported on the URI.</span></span>
  - <span data-ttu-id="16566-219">Attributet **SupportFragment** används om Get-åtgärden stöder konceptet.</span><span class="sxs-lookup"><span data-stu-id="16566-219">The **SupportFragment** attribute is used if the Get operation supports the concept.</span></span>
  - <span data-ttu-id="16566-220">Attributet **SupportFiltering** är inte giltigt för Get-åtgärder och ska vara inställt på "false".</span><span class="sxs-lookup"><span data-stu-id="16566-220">The **SupportFiltering** attribute is NOT valid for Get operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="16566-221">Den här åtgärden är inte giltig för en URI om Shell-åtgärder också stöds.</span><span class="sxs-lookup"><span data-stu-id="16566-221">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="16566-222">**Invoke** : Invoke-åtgärder stöds på URI: n.</span><span class="sxs-lookup"><span data-stu-id="16566-222">**Invoke** : Invoke operations are supported on the URI.</span></span>
  - <span data-ttu-id="16566-223">Attributet **SupportFragment** stöds inte för Invoke-åtgärder och ska vara inställt på false.</span><span class="sxs-lookup"><span data-stu-id="16566-223">The **SupportFragment** attribute is not supported for Invoke operations and should be set to False.</span></span>
  - <span data-ttu-id="16566-224">Attributet **SupportFiltering** är inte giltigt och ska vara inställt på "false".</span><span class="sxs-lookup"><span data-stu-id="16566-224">The **SupportFiltering** attribute is not valid and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="16566-225">Den här åtgärden är inte giltig för en URI om Shell-åtgärder också stöds.</span><span class="sxs-lookup"><span data-stu-id="16566-225">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="16566-226">**Lägg** till: placerings åtgärder stöds på URI: n.</span><span class="sxs-lookup"><span data-stu-id="16566-226">**Put** : Put operations are supported on the URI.</span></span>
  - <span data-ttu-id="16566-227">Attributet **SupportFragment** används om åtgärden Lägg till stöder konceptet.</span><span class="sxs-lookup"><span data-stu-id="16566-227">The **SupportFragment** attribute is used if the Put operation supports the concept.</span></span>
  - <span data-ttu-id="16566-228">Attributet **SupportFiltering** är inte giltigt för att införa åtgärder och ska vara inställt på "false".</span><span class="sxs-lookup"><span data-stu-id="16566-228">The **SupportFiltering** attribute is not valid for Put operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="16566-229">Den här åtgärden är inte giltig för en URI om Shell-åtgärder också stöds.</span><span class="sxs-lookup"><span data-stu-id="16566-229">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="16566-230">**Prenumerera** : prenumerations åtgärder stöds på URI: n.</span><span class="sxs-lookup"><span data-stu-id="16566-230">**Subscribe** : Subscribe operations are supported on the URI.</span></span>
  - <span data-ttu-id="16566-231">Attributet **SupportFragment** stöds inte för prenumerations åtgärder och ska vara inställt på false.</span><span class="sxs-lookup"><span data-stu-id="16566-231">The **SupportFragment** attribute is not supported for Subscribe operations and should be set to False.</span></span>
  - <span data-ttu-id="16566-232">Attributet **SupportFiltering** är inte giltigt för prenumerations åtgärder och ska vara inställt på "false".</span><span class="sxs-lookup"><span data-stu-id="16566-232">The **SupportFiltering** attribute is not valid for Subscribe operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="16566-233">Den här åtgärden är inte giltig för en URI om Shell-åtgärder också stöds.</span><span class="sxs-lookup"><span data-stu-id="16566-233">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="16566-234">**Shell** : Shell-åtgärder stöds på URI: n.</span><span class="sxs-lookup"><span data-stu-id="16566-234">**Shell** : Shell operations are supported on the URI.</span></span>
  - <span data-ttu-id="16566-235">Attributet **SupportFragment** stöds inte för Shell-åtgärder och ska vara inställt på "false".</span><span class="sxs-lookup"><span data-stu-id="16566-235">The **SupportFragment** attribute is not supported for Shell operations and should be set to "False".</span></span>
  - <span data-ttu-id="16566-236">Attributet **SupportFiltering** är inte giltigt för Shell-åtgärder och ska vara inställt på "false".</span><span class="sxs-lookup"><span data-stu-id="16566-236">The **SupportFiltering** attribute is not valid for Shell operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="16566-237">Den här åtgärden är inte giltig för en URI om en annan åtgärd också stöds.</span><span class="sxs-lookup"><span data-stu-id="16566-237">This operation is not valid for a URI if ANY other operation is also supported.</span></span>
  > [!NOTE]
  > <span data-ttu-id="16566-238">Om en gränssnitts åtgärd har kon figurer ATS för en URI, get-, get-, Create-, DELETE-, Invoke-och Enumeration-åtgärder bearbetas internt i WS-Management (WinRM)-tjänsten för att hantera gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="16566-238">If a Shell operation is configured for a URI, Get, Put, Create, Delete, Invoke, and Enumerate operations are processed internally within the WS-Management (WinRM) service to manage shells.</span></span> <span data-ttu-id="16566-239">Därför kan plugin-programmet inte hantera åtgärderna.</span><span class="sxs-lookup"><span data-stu-id="16566-239">As a result, the plug-in cannot handle the operations.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-240">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-240">Cmdlets supported</span></span>

- [<span data-ttu-id="16566-241">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-241">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="certificatethumbprint-string"></a><span data-ttu-id="16566-242">CertificateThumbprint \<String\></span><span class="sxs-lookup"><span data-stu-id="16566-242">CertificateThumbprint \<String\></span></span>

<span data-ttu-id="16566-243">Anger tumavtrycket för tjänst certifikatet.</span><span class="sxs-lookup"><span data-stu-id="16566-243">Specifies the thumbprint of the service certificate.</span></span>

<span data-ttu-id="16566-244">Det här värdet representerar strängen med tvåsiffriga hexadecimala värden i certifikatets tumavtryck-fält.</span><span class="sxs-lookup"><span data-stu-id="16566-244">This value represents the string of two-digit hexadecimal values in the Thumbprint field of the certificate.</span></span> <span data-ttu-id="16566-245">Den anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="16566-245">It specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="16566-246">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="16566-246">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="16566-247">De kan endast mappas till lokala användar konton och de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="16566-247">They can be mapped only to local user accounts, and they do not work with domain accounts.</span></span> <span data-ttu-id="16566-248">Använd `Get-Item` `Get-ChildItem` cmdletarna eller i PowerShell-enheten för att hämta ett tumavtryck för certifikatet `Cert:` .</span><span class="sxs-lookup"><span data-stu-id="16566-248">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` cmdlets in the PowerShell `Cert:` drive.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-249">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-249">Cmdlets supported</span></span>

- [<span data-ttu-id="16566-250">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-250">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="enabled-boolean"></a><span data-ttu-id="16566-251">Aktiva \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="16566-251">Enabled \<Boolean\></span></span>

<span data-ttu-id="16566-252">Anger om lyssnaren är aktive rad eller inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="16566-252">Specifies whether the listener is enabled or disabled.</span></span> <span data-ttu-id="16566-253">Standardvärdet är true.</span><span class="sxs-lookup"><span data-stu-id="16566-253">The default is True.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-254">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-254">Cmdlets Supported</span></span>

- [<span data-ttu-id="16566-255">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-255">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="filename-plugin-string"></a><span data-ttu-id="16566-256">Fil namn (plugin-program) \<String\></span><span class="sxs-lookup"><span data-stu-id="16566-256">FileName (Plugin) \<String\></span></span>

<span data-ttu-id="16566-257">Anger fil namnet för åtgärds-plugin-programmet.</span><span class="sxs-lookup"><span data-stu-id="16566-257">Specifies the file name of the operations plug-in.</span></span> <span data-ttu-id="16566-258">Alla miljövariabler som placeras i den här posten kommer att expanderas i användarnas kontext när en begäran tas emot.</span><span class="sxs-lookup"><span data-stu-id="16566-258">Any environment variables that are put in this entry will be expanded in the users' context when a request is received.</span></span> <span data-ttu-id="16566-259">Eftersom varje användare kan ha en annan version av samma miljö variabel kan varje användare ha olika plugin-program.</span><span class="sxs-lookup"><span data-stu-id="16566-259">Because each user could have a different version of the same environment variable, each user could have a different plug-in.</span></span> <span data-ttu-id="16566-260">Den här posten får inte vara tom och måste peka på ett giltigt plugin-program.</span><span class="sxs-lookup"><span data-stu-id="16566-260">This entry cannot be blank and must point to a valid plug-in.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-261">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-261">Cmdlets Supported</span></span>

- [<span data-ttu-id="16566-262">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-262">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="hostname-string"></a><span data-ttu-id="16566-263">Värdnamn \<String\></span><span class="sxs-lookup"><span data-stu-id="16566-263">HostName \<String\></span></span>

<span data-ttu-id="16566-264">Anger värd namnet för den dator där tjänsten WS-Management (WinRM) körs.</span><span class="sxs-lookup"><span data-stu-id="16566-264">Specifies the host name of the computer on which the WS-Management (WinRM) service is running.</span></span>

<span data-ttu-id="16566-265">Värdet måste vara ett fullständigt kvalificerat domän namn, en IPv4-eller IPv6 literal sträng eller ett jokertecken.</span><span class="sxs-lookup"><span data-stu-id="16566-265">The value must be a fully qualified domain name, an IPv4 or IPv6 literal string, or a wildcard character.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-266">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-266">Cmdlets Supported</span></span>

- [<span data-ttu-id="16566-267">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-267">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="issuer-string"></a><span data-ttu-id="16566-268">Utfärdare \<String\></span><span class="sxs-lookup"><span data-stu-id="16566-268">Issuer \<String\></span></span>

<span data-ttu-id="16566-269">Anger namnet på den certifikat utfärdare som utfärdade certifikatet.</span><span class="sxs-lookup"><span data-stu-id="16566-269">Specifies the name of the certification authority that issued the certificate.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-270">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-270">Cmdlets Supported</span></span>

- [<span data-ttu-id="16566-271">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-271">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="plugin--ws-management-plug-ins-are-native-dynamic-link-libraries-dlls"></a><span data-ttu-id="16566-272">Plugin \<\> -program för WS-Management plugin-program är interna DLL-bibliotek (Dynamic Link Libraries)</span><span class="sxs-lookup"><span data-stu-id="16566-272">Plugin \<\> WS-Management plug-ins are native dynamic link libraries (DLLs)</span></span>

<span data-ttu-id="16566-273">den ansluter till och utökar funktionerna i WS-Management.</span><span class="sxs-lookup"><span data-stu-id="16566-273">that plug in to and extend the functionality of WS-Management .</span></span> <span data-ttu-id="16566-274">API: et för WSW-Management-plugin innehåller funktioner som gör att en användare kan skriva plugin-program genom att implementera vissa API: er för resurs-URI: er och åtgärder som stöds.</span><span class="sxs-lookup"><span data-stu-id="16566-274">The WSW-Management Plug-in API provides functionality that enables a user to write plug-ins by implementing certain APIs for supported resource URIs and operations.</span></span> <span data-ttu-id="16566-275">När plugin-programmen har kon figurer ATS för antingen tjänsten WS-Management (WinRM) eller för Internet Information Services (IIS), läses plugin-programmen in i WS-Management-värden eller IIS-värden.</span><span class="sxs-lookup"><span data-stu-id="16566-275">After the plug-ins are configured for either the WS-Management (WinRM) service or for Internet Information Services (IIS), the plug-ins are loaded in the WS-Management host or in the IIS host, respectively.</span></span> <span data-ttu-id="16566-276">Fjärrbegäranden dirigeras till dessa plugin-ingångs punkter för att utföra åtgärder.</span><span class="sxs-lookup"><span data-stu-id="16566-276">Remote requests are routed to these plug-in entry points to perform operations.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-277">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-277">Cmdlets Supported</span></span>

- [<span data-ttu-id="16566-278">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-278">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="port-unsigned-short-integer"></a><span data-ttu-id="16566-279">Lastning \<Unsigned Short Integer\></span><span class="sxs-lookup"><span data-stu-id="16566-279">Port \<Unsigned Short Integer\></span></span>

<span data-ttu-id="16566-280">Anger den TCP-port som den här lyssnaren har skapats för.</span><span class="sxs-lookup"><span data-stu-id="16566-280">Specifies the TCP port for which this listener is created.</span></span> <span data-ttu-id="16566-281">Du kan ange ett värde mellan 1 och 65535.</span><span class="sxs-lookup"><span data-stu-id="16566-281">You can specify any value from 1 through 65535.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-282">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-282">Cmdlets Supported</span></span>

- [<span data-ttu-id="16566-283">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-283">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a><span data-ttu-id="16566-284">Klusterresursen \<String\></span><span class="sxs-lookup"><span data-stu-id="16566-284">Resource \<String\></span></span>

<span data-ttu-id="16566-285">Anger en slut punkt som representerar en distinkt typ av hanterings åtgärd eller värde.</span><span class="sxs-lookup"><span data-stu-id="16566-285">Specifies an endpoint that represents a distinct type of management operation or value.</span></span> <span data-ttu-id="16566-286">En tjänst exponerar en eller flera resurser och vissa resurser kan ha mer än en instans.</span><span class="sxs-lookup"><span data-stu-id="16566-286">A service exposes one or more resources, and some resources can have more than one instance.</span></span> <span data-ttu-id="16566-287">En hanterings resurs liknar en WMI-klass eller en databas tabell, och en instans liknar en instans av klassen eller en rad i tabellen.</span><span class="sxs-lookup"><span data-stu-id="16566-287">A management resource is similar to a WMI class or to a database table, and an instance is similar to an instance of the class or to a row in the table.</span></span> <span data-ttu-id="16566-288">**Win32_LogicalDisk** -klassen representerar till exempel en resurs.</span><span class="sxs-lookup"><span data-stu-id="16566-288">For example, the **Win32_LogicalDisk** class represents a resource.</span></span> <span data-ttu-id="16566-289">`Win32_LogicalDisk="C:\\"` är en angiven instans av resursen.</span><span class="sxs-lookup"><span data-stu-id="16566-289">`Win32_LogicalDisk="C:\\"` is a specific instance of the resource.</span></span>

<span data-ttu-id="16566-290">En Uniform Resource Identifier (URI) innehåller ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="16566-290">A Uniform Resource Identifier (URI) contains a prefix and a path to a resource.</span></span>
<span data-ttu-id="16566-291">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="16566-291">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-292">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-292">Cmdlets Supported</span></span>

- [<span data-ttu-id="16566-293">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-293">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a><span data-ttu-id="16566-294">Klusterresursen \<String\></span><span class="sxs-lookup"><span data-stu-id="16566-294">Resource \<String\></span></span>

<span data-ttu-id="16566-295">Anger Uniform Resource Identifier (URI) som identifierar en speciell typ av resurs, till exempel en disk eller en process, på en dator.</span><span class="sxs-lookup"><span data-stu-id="16566-295">Specifies the Uniform Resource Identifier (URI) that identifies a specific type of resource, such as a disk or a process, on a computer.</span></span>

<span data-ttu-id="16566-296">En URI består av ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="16566-296">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="16566-297">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="16566-297">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-298">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-298">Cmdlets Supported</span></span>

- [<span data-ttu-id="16566-299">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-299">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sdkversion-string"></a><span data-ttu-id="16566-300">SDKVersion \<String\></span><span class="sxs-lookup"><span data-stu-id="16566-300">SDKVersion \<String\></span></span>

<span data-ttu-id="16566-301">Anger versionen för WS-Management plugin-programmet SDK.</span><span class="sxs-lookup"><span data-stu-id="16566-301">Specifies the version of the WS-Management plug-in SDK.</span></span> <span data-ttu-id="16566-302">Det enda giltiga värdet är</span><span class="sxs-lookup"><span data-stu-id="16566-302">The only valid value is</span></span>
1.

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-303">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-303">Cmdlets Supported</span></span>

- [<span data-ttu-id="16566-304">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-304">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="subject-string"></a><span data-ttu-id="16566-305">Motiv \<String\></span><span class="sxs-lookup"><span data-stu-id="16566-305">Subject \<String\></span></span>

<span data-ttu-id="16566-306">Anger den entitet som identifieras av certifikatet.</span><span class="sxs-lookup"><span data-stu-id="16566-306">Specifies the entity that is identified by the certificate.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-307">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-307">Cmdlets Supported</span></span>

- [<span data-ttu-id="16566-308">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-308">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="transport-string"></a><span data-ttu-id="16566-309">Källtransportadr \<String\></span><span class="sxs-lookup"><span data-stu-id="16566-309">Transport \<String\></span></span>

<span data-ttu-id="16566-310">Anger vilken transport som ska användas för att skicka och ta emot WS-Management protokoll förfrågningar och svar.</span><span class="sxs-lookup"><span data-stu-id="16566-310">Specifies the transport to use to send and receive WS-Management protocol requests and responses.</span></span> <span data-ttu-id="16566-311">Värdet måste vara antingen HTTP eller HTTPS.</span><span class="sxs-lookup"><span data-stu-id="16566-311">The value must be either HTTP or HTTPS.</span></span>

<span data-ttu-id="16566-312">Obs: transport svärdet anges när du skapar en lyssnare.</span><span class="sxs-lookup"><span data-stu-id="16566-312">Note: The Transport value is set when creating a Listener.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-313">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-313">Cmdlets Supported</span></span>

- [<span data-ttu-id="16566-314">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-314">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="uri-string"></a><span data-ttu-id="16566-315">URI \<String\></span><span class="sxs-lookup"><span data-stu-id="16566-315">URI \<String\></span></span>

<span data-ttu-id="16566-316">Identifierar den URI för vilken åtkomst är tillåten baserat på värdet för SDDL-parametern.</span><span class="sxs-lookup"><span data-stu-id="16566-316">Identifies the URI for which access is authorized based on the value of the Sddl parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-317">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-317">Cmdlets Supported</span></span>

- [<span data-ttu-id="16566-318">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-318">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="urlprefix-string"></a><span data-ttu-id="16566-319">URLPrefix \<String\></span><span class="sxs-lookup"><span data-stu-id="16566-319">URLPrefix \<String\></span></span>

<span data-ttu-id="16566-320">Ett URL-prefix som accepterar HTTP-eller HTTPS-begäranden.</span><span class="sxs-lookup"><span data-stu-id="16566-320">A URL prefix on which to accept HTTP or HTTPS requests.</span></span> <span data-ttu-id="16566-321">Detta är en sträng som endast innehåller tecknen `[a-z]` , `[A-Z]` , `[9-0]` , under streck ( `_` ) och omvänt snedstreck ( `/` ).</span><span class="sxs-lookup"><span data-stu-id="16566-321">This is a string containing only the characters `[a-z]`, `[A-Z]`, `[9-0]`, underscore (`_`) and backslash (`/`).</span></span> <span data-ttu-id="16566-322">Strängen får inte börja med eller sluta med ett omvänt snedstreck ( `/` ).</span><span class="sxs-lookup"><span data-stu-id="16566-322">The string must not start with or end with a backslash (`/`).</span></span> <span data-ttu-id="16566-323">Om dator namnet till exempel är "SampleComputer" anger WS-Management klienten `http://SampleMachine/URLPrefix` i mål adressen.</span><span class="sxs-lookup"><span data-stu-id="16566-323">For example, if the computer name is "SampleComputer", the WS-Management client would specify `http://SampleMachine/URLPrefix` in the destination address.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-324">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-324">Cmdlets Supported</span></span>

- [<span data-ttu-id="16566-325">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-325">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="value-string"></a><span data-ttu-id="16566-326">Värde \<String\></span><span class="sxs-lookup"><span data-stu-id="16566-326">Value \<String\></span></span>

<span data-ttu-id="16566-327">Anger värdet för en initierings parameter, vilket är ett plugin-/regionsspecifika värde som används för att ange konfigurations alternativ.</span><span class="sxs-lookup"><span data-stu-id="16566-327">Specifies the value of an initialization parameter, which is a plug-in-specific value that is used to specify configuration options.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-328">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-328">Cmdlets Supported</span></span>

- [<span data-ttu-id="16566-329">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-329">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="xmlrenderingtype-string"></a><span data-ttu-id="16566-330">XMLRenderingType \<String\></span><span class="sxs-lookup"><span data-stu-id="16566-330">XMLRenderingType \<String\></span></span>

<span data-ttu-id="16566-331">Anger det format i vilket XML skickas till plugin-program via **WSMAN_DATA** -objektet.</span><span class="sxs-lookup"><span data-stu-id="16566-331">Specifies the format in which XML is passed to plug-ins through the **WSMAN_DATA** object.</span></span> <span data-ttu-id="16566-332">Följande är giltiga värden:</span><span class="sxs-lookup"><span data-stu-id="16566-332">The following are valid values:</span></span>

- <span data-ttu-id="16566-333">Text: inkommande XML-data finns i en **WSMAN_DATA_TYPE_TEXT** -struktur som representerar XML-filen som **PCWSTR** -minnesbuffert.</span><span class="sxs-lookup"><span data-stu-id="16566-333">Text: Incoming XML data is contained in a **WSMAN_DATA_TYPE_TEXT** structure, which represents the XML as a **PCWSTR** memory buffer.</span></span>
- <span data-ttu-id="16566-334">XMLReader: inkommande XML-data finns i en **WSMAN_DATA_TYPE_WS_XML_READER** -struktur som representerar XML som ett **XmlReader** -objekt, som definieras i huvud filen "WebServices. h".</span><span class="sxs-lookup"><span data-stu-id="16566-334">XMLReader: Incoming XML data is contained in a **WSMAN_DATA_TYPE_WS_XML_READER** structure, which represents the XML as an **XmlReader** object, which is defined in the "WebServices.h" header file.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="16566-335">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="16566-335">Cmdlets Supported</span></span>

- [<span data-ttu-id="16566-336">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="16566-336">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="16566-337">Använda pipelinen</span><span class="sxs-lookup"><span data-stu-id="16566-337">Using the pipeline</span></span>

<span data-ttu-id="16566-338">Provider-cmdletar accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="16566-338">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="16566-339">Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="16566-339">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="16566-340">Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="16566-340">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="16566-341">Få hjälp</span><span class="sxs-lookup"><span data-stu-id="16566-341">Getting help</span></span>

<span data-ttu-id="16566-342">Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="16566-342">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="16566-343">Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett [Get-Help-](xref:Microsoft.PowerShell.Core.Get-Help) kommando i en fil system enhet eller använder `-Path` parametern för [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) för att ange en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="16566-343">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path wsman:
```

## <a name="see-also"></a><span data-ttu-id="16566-344">Se även</span><span class="sxs-lookup"><span data-stu-id="16566-344">See also</span></span>

[<span data-ttu-id="16566-345">about_Providers</span><span class="sxs-lookup"><span data-stu-id="16566-345">about_Providers</span></span>](../../Microsoft.PowerShell.Core/About/about_Providers.md)
