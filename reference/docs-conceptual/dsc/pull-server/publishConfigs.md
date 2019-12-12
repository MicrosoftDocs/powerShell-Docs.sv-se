---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: 'Publicera till en pull-server med konfigurations-ID: n (v4/V5)'
ms.openlocfilehash: 3b094308338e62c783b19f4d3bb41634feee63f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417252"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="8f1de-103">Publicera till en pull-server med konfigurations-ID: n (v4/V5)</span><span class="sxs-lookup"><span data-stu-id="8f1de-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="8f1de-104">I avsnitten nedan förutsätts att du redan har konfigurerat en hämtnings Server.</span><span class="sxs-lookup"><span data-stu-id="8f1de-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="8f1de-105">Om du inte har konfigurerat din pull-server kan du använda följande guider:</span><span class="sxs-lookup"><span data-stu-id="8f1de-105">If you haven't set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="8f1de-106">Konfigurera en DSC SMB-pull-server</span><span class="sxs-lookup"><span data-stu-id="8f1de-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="8f1de-107">Konfigurera en DSC HTTP-pull-server</span><span class="sxs-lookup"><span data-stu-id="8f1de-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="8f1de-108">Varje målnod kan konfigureras för att ladda ned konfigurationer, resurser och till och med rapportera dess status.</span><span class="sxs-lookup"><span data-stu-id="8f1de-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="8f1de-109">Den här artikeln visar hur du laddar upp resurser så att de kan laddas ned och konfigurera klienterna så att de automatiskt laddar ned resurser.</span><span class="sxs-lookup"><span data-stu-id="8f1de-109">This article shows you how to upload resources so they're available to be downloaded, and configure clients to automatically download resources.</span></span> <span data-ttu-id="8f1de-110">När noden får en tilldelad konfiguration via **pull** eller **push** (V5) laddar den automatiskt ned eventuella resurser som krävs av konfigurationen från den plats som anges i den lokala Configuration Manager (LCM).</span><span class="sxs-lookup"><span data-stu-id="8f1de-110">When the node receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the Local Configuration Manager (LCM).</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="8f1de-111">Kompilera konfigurationer</span><span class="sxs-lookup"><span data-stu-id="8f1de-111">Compile configurations</span></span>

<span data-ttu-id="8f1de-112">Det första steget för att lagra [konfigurationer](../configurations/configurations.md) på en pull-server är att kompilera dem till `.mof` filer.</span><span class="sxs-lookup"><span data-stu-id="8f1de-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into `.mof` files.</span></span> <span data-ttu-id="8f1de-113">Om du vill göra en konfiguration generisk och tillämplig på fler klienter använder du `localhost` i Node-blocket.</span><span class="sxs-lookup"><span data-stu-id="8f1de-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="8f1de-114">Exemplet nedan visar ett konfigurations gränssnitt som använder `localhost` i stället för ett angivet klient namn.</span><span class="sxs-lookup"><span data-stu-id="8f1de-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="8f1de-115">När du har kompilerat den allmänna konfigurationen bör du ha en `localhost.mof`-fil.</span><span class="sxs-lookup"><span data-stu-id="8f1de-115">Once you've compiled your generic configuration, you should have a `localhost.mof` file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="8f1de-116">Byta namn på MOF-filen</span><span class="sxs-lookup"><span data-stu-id="8f1de-116">Renaming the MOF file</span></span>

<span data-ttu-id="8f1de-117">Du kan lagra konfigurations `.mof` filer på en pull-server av **ConfigurationName** eller **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="8f1de-117">You can store Configuration `.mof` files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="8f1de-118">Beroende på hur du planerar att konfigurera dina pull-klienter kan du välja ett avsnitt nedan för att byta namn på dina kompilerade `.mof`-filer på ett korrekt sätt.</span><span class="sxs-lookup"><span data-stu-id="8f1de-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled `.mof` files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="8f1de-119">Konfigurations-ID (GUID)</span><span class="sxs-lookup"><span data-stu-id="8f1de-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="8f1de-120">Du måste byta namn på `localhost.mof`-filen till `<GUID>.mof`-fil.</span><span class="sxs-lookup"><span data-stu-id="8f1de-120">You'll need to rename your `localhost.mof` file to `<GUID>.mof` file.</span></span> <span data-ttu-id="8f1de-121">Du kan skapa ett slumpmässigt **GUID** med hjälp av exemplet nedan eller med hjälp av cmdleten [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) .</span><span class="sxs-lookup"><span data-stu-id="8f1de-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="8f1de-122">Exempel på utdata</span><span class="sxs-lookup"><span data-stu-id="8f1de-122">Sample Output</span></span>

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="8f1de-123">Du kan sedan byta namn på `.mof`-filen med en acceptabel metod.</span><span class="sxs-lookup"><span data-stu-id="8f1de-123">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="8f1de-124">Exemplet nedan använder cmdleten [rename-item](/powershell/module/microsoft.powershell.management/rename-item) .</span><span class="sxs-lookup"><span data-stu-id="8f1de-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="8f1de-125">Mer information om hur du använder **GUID** i din miljö finns i [Planera för GUID](/powershell/scripting/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="8f1de-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/scripting/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="8f1de-126">Konfigurations namn</span><span class="sxs-lookup"><span data-stu-id="8f1de-126">Configuration names</span></span>

<span data-ttu-id="8f1de-127">Du måste byta namn på `localhost.mof`-filen till `<Configuration Name>.mof`-fil.</span><span class="sxs-lookup"><span data-stu-id="8f1de-127">You'll need to rename your `localhost.mof` file to `<Configuration Name>.mof` file.</span></span> <span data-ttu-id="8f1de-128">I följande exempel används konfigurations namnet från föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="8f1de-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="8f1de-129">Du kan sedan byta namn på `.mof`-filen med en acceptabel metod.</span><span class="sxs-lookup"><span data-stu-id="8f1de-129">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="8f1de-130">Exemplet nedan använder cmdleten [rename-item](/powershell/module/microsoft.powershell.management/rename-item) .</span><span class="sxs-lookup"><span data-stu-id="8f1de-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="8f1de-131">Skapa kontroll summan</span><span class="sxs-lookup"><span data-stu-id="8f1de-131">Create the checkSum</span></span>

<span data-ttu-id="8f1de-132">Varje `.mof`-fil som lagras på en pull-server eller SMB-resurs måste ha en tillhör ande `.checksum`-fil.</span><span class="sxs-lookup"><span data-stu-id="8f1de-132">Each `.mof` file stored on a Pull Server, or SMB share needs to have an associated `.checksum` file.</span></span>
<span data-ttu-id="8f1de-133">Den här filen låter klienter veta när den associerade `.mof`-filen har ändrats och ska laddas ned igen.</span><span class="sxs-lookup"><span data-stu-id="8f1de-133">This file lets clients know when the associated `.mof` file has changed and should be downloaded again.</span></span>

<span data-ttu-id="8f1de-134">Du kan skapa en **kontroll Summa** med cmdleten [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) .</span><span class="sxs-lookup"><span data-stu-id="8f1de-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="8f1de-135">Du kan också köra `New-DSCCheckSum` mot en katalog med filer med hjälp av `-Path`-parametern.</span><span class="sxs-lookup"><span data-stu-id="8f1de-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span>
<span data-ttu-id="8f1de-136">Om det redan finns en kontroll summa kan du tvinga den att skapas igen med `-Force`-parametern.</span><span class="sxs-lookup"><span data-stu-id="8f1de-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="8f1de-137">I följande exempel angavs en katalog som innehåller `.mof`-filen från föregående avsnitt och använder parametern `-Force`.</span><span class="sxs-lookup"><span data-stu-id="8f1de-137">The following example specified a directory containing the `.mof` file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="8f1de-138">Inga utdata visas, men nu bör du se en `<GUID or Configuration Name>.mof.checksum`-fil.</span><span class="sxs-lookup"><span data-stu-id="8f1de-138">No output will be shown, but you should now see a `<GUID or Configuration Name>.mof.checksum` file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="8f1de-139">Var du ska lagra MOF-filer och kontroll summor</span><span class="sxs-lookup"><span data-stu-id="8f1de-139">Where to store MOF files and checkSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="8f1de-140">På en DSC HTTP-pull-server</span><span class="sxs-lookup"><span data-stu-id="8f1de-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="8f1de-141">När du konfigurerar din HTTP-pull-server, enligt beskrivningen i [Konfigurera en DSC HTTP-pull-server](pullServer.md), anger du kataloger för nycklarna **ModulePath** och **ConfigurationPath** .</span><span class="sxs-lookup"><span data-stu-id="8f1de-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="8f1de-142">Nyckeln **ModulePath** anger var en moduls paketerade `.zip` filer ska lagras.</span><span class="sxs-lookup"><span data-stu-id="8f1de-142">The **ModulePath** key indicates where a module's packaged `.zip` files should be stored.</span></span> <span data-ttu-id="8f1de-143">**ConfigurationPath** anger var `.mof` filer och `.checksum` filer ska lagras.</span><span class="sxs-lookup"><span data-stu-id="8f1de-143">The **ConfigurationPath** indicates where any `.mof` files and `.checksum` files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="8f1de-144">På en SMB-resurs</span><span class="sxs-lookup"><span data-stu-id="8f1de-144">On an SMB share</span></span>

<span data-ttu-id="8f1de-145">När du konfigurerar en pull-klient för att använda en SMB-resurs anger du en **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="8f1de-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span>
<span data-ttu-id="8f1de-146">Alla `.mof`-filer och `.checksum` filer ska lagras i **SourcePath** -katalogen från **ConfigurationRepositoryShare** -blocket.</span><span class="sxs-lookup"><span data-stu-id="8f1de-146">All `.mof` files and `.checksum` files should be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="8f1de-147">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="8f1de-147">Next steps</span></span>

<span data-ttu-id="8f1de-148">Härnäst ska du konfigurera pull-klienter för att hämta den angivna konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="8f1de-148">Next, you'll want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="8f1de-149">Mer information finns i någon av följande guider:</span><span class="sxs-lookup"><span data-stu-id="8f1de-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="8f1de-150">Konfigurera en pull-klient med hjälp av konfigurations-ID: n (v4)</span><span class="sxs-lookup"><span data-stu-id="8f1de-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="8f1de-151">Konfigurera en pull-klient med konfigurations-ID: n (V5)</span><span class="sxs-lookup"><span data-stu-id="8f1de-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="8f1de-152">Konfigurera en pull-klient med konfigurations namn (V5)</span><span class="sxs-lookup"><span data-stu-id="8f1de-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="8f1de-153">Se även</span><span class="sxs-lookup"><span data-stu-id="8f1de-153">See also</span></span>

- [<span data-ttu-id="8f1de-154">Konfigurera en DSC SMB-pull-server</span><span class="sxs-lookup"><span data-stu-id="8f1de-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="8f1de-155">Konfigurera en DSC HTTP-pull-server</span><span class="sxs-lookup"><span data-stu-id="8f1de-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="8f1de-156">Paketera och ladda upp resurser till en hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="8f1de-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
