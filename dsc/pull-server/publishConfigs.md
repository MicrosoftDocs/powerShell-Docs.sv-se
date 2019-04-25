---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Publicera till en Pull-servern med hjälp av konfigurations-ID (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079514"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="92ab7-103">Publicera till en Pull-servern med hjälp av konfigurations-ID (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="92ab7-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="92ab7-104">I avsnitten nedan förutsätter att du har ställt in en Pull-servern.</span><span class="sxs-lookup"><span data-stu-id="92ab7-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="92ab7-105">Om du inte har konfigurerat din Pull-servern kan du använda följande guider:</span><span class="sxs-lookup"><span data-stu-id="92ab7-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="92ab7-106">Konfigurera en DSC SMB-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="92ab7-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="92ab7-107">Konfigurera en DSC HTTP-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="92ab7-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="92ab7-108">Varje målnoden kan konfigureras för att hämta konfigurationer, resurser, och även rapportera statusen.</span><span class="sxs-lookup"><span data-stu-id="92ab7-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="92ab7-109">Den här artikeln visar hur du laddar upp resurser så att de blir tillgängliga för att hämta och konfigurera klienter för att hämta resurser automatiskt.</span><span class="sxs-lookup"><span data-stu-id="92ab7-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="92ab7-110">När nod som tar emot en tilldelade konfiguration via **hämta** eller **Push** (v5) hämtas automatiskt alla resurser som krävs av konfigurationen från den plats som anges i LCM.</span><span class="sxs-lookup"><span data-stu-id="92ab7-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="92ab7-111">Kompilera konfigurationer</span><span class="sxs-lookup"><span data-stu-id="92ab7-111">Compile Configurations</span></span>

<span data-ttu-id="92ab7-112">Det första steget för att lagra [konfigurationer](../configurations/configurations.md) på en Pull-servern är att sammanställa dem i MOF-filerna.</span><span class="sxs-lookup"><span data-stu-id="92ab7-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into ".mof" files.</span></span> <span data-ttu-id="92ab7-113">Om du vill göra en konfiguration för allmän och gäller för flera klienter, använda `localhost` i noden-block.</span><span class="sxs-lookup"><span data-stu-id="92ab7-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="92ab7-114">Exemplet nedan visar ett Configuration-gränssnitt som använder `localhost` i stället för en viss klient-namn.</span><span class="sxs-lookup"><span data-stu-id="92ab7-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="92ab7-115">När du har skapat din Allmän konfiguration, bör du ha en ”localhost.mof”-fil.</span><span class="sxs-lookup"><span data-stu-id="92ab7-115">Once you have compiled your generic configuration, you should have a "localhost.mof" file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="92ab7-116">Byta namn på MOF-filen</span><span class="sxs-lookup"><span data-stu-id="92ab7-116">Renaming the MOF file</span></span>

<span data-ttu-id="92ab7-117">Du kan lagra konfiguration MOF-filerna på en Hämtningsserver av **ConfigurationName** eller **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="92ab7-117">You can store Configuration ".mof" files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="92ab7-118">Du kan välja ett avsnitt nedan för att korrekt Byt namn på din kompilerade MOF-filerna beroende på hur du planerar att konfigurera din pull-klienter.</span><span class="sxs-lookup"><span data-stu-id="92ab7-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled ".mof" files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="92ab7-119">Konfigurations-ID (GUID)</span><span class="sxs-lookup"><span data-stu-id="92ab7-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="92ab7-120">Du måste byta namn på filen ”localhost.mof” till ”<GUID>.mof” fil.</span><span class="sxs-lookup"><span data-stu-id="92ab7-120">You will need to rename your "localhost.mof" file to "<GUID>.mof" file.</span></span> <span data-ttu-id="92ab7-121">Du kan skapa ett slumpmässigt **Guid** i exemplet nedan eller genom att använda den [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="92ab7-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="92ab7-122">Exempel på utdata</span><span class="sxs-lookup"><span data-stu-id="92ab7-122">Sample Output</span></span>

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="92ab7-123">Du kan sedan byta namn på filen ”.mof” med någon godkänd av metoderna.</span><span class="sxs-lookup"><span data-stu-id="92ab7-123">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="92ab7-124">I exemplet nedan, används den [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="92ab7-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="92ab7-125">Mer information om hur du använder **GUID** i din miljö, se [planera för GUID](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="92ab7-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="92ab7-126">Konfigurationsnamn</span><span class="sxs-lookup"><span data-stu-id="92ab7-126">Configuration Names</span></span>

<span data-ttu-id="92ab7-127">Du måste byta namn på filen ”localhost.mof” till ”<Configuration Name>.mof” fil.</span><span class="sxs-lookup"><span data-stu-id="92ab7-127">You will need to rename your "localhost.mof" file to "<Configuration Name>.mof" file.</span></span> <span data-ttu-id="92ab7-128">I följande exempel används konfigurationsnamnet i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="92ab7-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="92ab7-129">Du kan sedan byta namn på filen ”.mof” med någon godkänd av metoderna.</span><span class="sxs-lookup"><span data-stu-id="92ab7-129">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="92ab7-130">I exemplet nedan, används den [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="92ab7-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="92ab7-131">Skapa kontrollsumman</span><span class="sxs-lookup"><span data-stu-id="92ab7-131">Create the CheckSum</span></span>

<span data-ttu-id="92ab7-132">Varje ”.mof”-fil som lagras på en Pull-servern eller SMB-resursen måste ha en associerad ”.checksum”-fil.</span><span class="sxs-lookup"><span data-stu-id="92ab7-132">Each ".mof" file stored on a Pull Server, or SMB share needs to have an associated ".checksum" file.</span></span> <span data-ttu-id="92ab7-133">Den här filen tillåter klienter att veta när filen associerade ”.mof” har ändrats och ska laddas ned igen.</span><span class="sxs-lookup"><span data-stu-id="92ab7-133">This file lets clients know when the associated ".mof" file has changed and should be downloaded again.</span></span>

<span data-ttu-id="92ab7-134">Du kan skapa en **kontrollsumma** med den [New DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="92ab7-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="92ab7-135">Du kan också köra `New-DSCCheckSum` mot en katalog med filer med hjälp av den `-Path` parametern.</span><span class="sxs-lookup"><span data-stu-id="92ab7-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="92ab7-136">Om det finns redan en kontrollsumma, kan du tvinga den återskapas med den `-Force` parametern.</span><span class="sxs-lookup"><span data-stu-id="92ab7-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="92ab7-137">I följande exempel anges en katalog som innehåller filen ”.mof” i föregående avsnitt och använder den `-Force` parametern.</span><span class="sxs-lookup"><span data-stu-id="92ab7-137">The following example specified a directory containing the ".mof" file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="92ab7-138">Inga utdata visas, men du bör nu se en ”<GUID or Configuration Name>. mof.checksum” fil.</span><span class="sxs-lookup"><span data-stu-id="92ab7-138">No output will be shown, but you should now see a "<GUID or Configuration Name>.mof.checksum" file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="92ab7-139">Var du vill lagra MOF-filer och kontrollsummor</span><span class="sxs-lookup"><span data-stu-id="92ab7-139">Where to store MOF files and CheckSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="92ab7-140">På en DSC HTTP-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="92ab7-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="92ab7-141">När du konfigurerar http-Pull-servern, enligt beskrivningen i [konfigurera en DSC HTTP-Hämtningsserver](pullServer.md), anger du kataloger för den **ModulePath** och **ConfigurationPath** nycklar.</span><span class="sxs-lookup"><span data-stu-id="92ab7-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="92ab7-142">Den **ConfigurationPath** nyckel anger där alla MOF-filerna ska sparas.</span><span class="sxs-lookup"><span data-stu-id="92ab7-142">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="92ab7-143">Den **ConfigurationPath** anger där alla ”.mof” och ”.checksum”-filer ska sparas.</span><span class="sxs-lookup"><span data-stu-id="92ab7-143">The **ConfigurationPath** indicates where any ".mof" files and ".checksum" files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="92ab7-144">På en SMB-resurs</span><span class="sxs-lookup"><span data-stu-id="92ab7-144">On an SMB Share</span></span>

<span data-ttu-id="92ab7-145">När du har konfigurerat en Pull-klient du använder en SMB-resurs kan du ange en **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="92ab7-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="92ab7-146">Alla ”.mof” och ”.checksum”-filer ska sedan lagras i den **SourcePath** katalogen från den **ConfigurationRepositoryShare** block.</span><span class="sxs-lookup"><span data-stu-id="92ab7-146">All ".mof" files and ".checksum" files should then be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="92ab7-147">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="92ab7-147">Next Steps</span></span>

<span data-ttu-id="92ab7-148">Därefter ska du konfigurera Pull-klienter för att hämta den angivna konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="92ab7-148">Next, you will want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="92ab7-149">Mer information finns i någon av följande guider:</span><span class="sxs-lookup"><span data-stu-id="92ab7-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="92ab7-150">Konfigurera en Pull-klient som använder konfigurations-ID (v4)</span><span class="sxs-lookup"><span data-stu-id="92ab7-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="92ab7-151">Konfigurera en Pull-klient som använder konfigurations-ID (v5)</span><span class="sxs-lookup"><span data-stu-id="92ab7-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="92ab7-152">Ställa in en Pull-klient med konfigurationsnamn (v5)</span><span class="sxs-lookup"><span data-stu-id="92ab7-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="92ab7-153">Se även</span><span class="sxs-lookup"><span data-stu-id="92ab7-153">See also</span></span>

- [<span data-ttu-id="92ab7-154">Konfigurera en DSC SMB-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="92ab7-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="92ab7-155">Konfigurera en DSC HTTP-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="92ab7-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="92ab7-156">Paket- och ladda upp resurser till en Pull-Server</span><span class="sxs-lookup"><span data-stu-id="92ab7-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
