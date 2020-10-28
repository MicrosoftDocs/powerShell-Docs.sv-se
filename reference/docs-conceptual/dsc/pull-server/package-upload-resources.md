---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Paketera och ladda upp resurser till en hämtnings Server
description: Den här artikeln visar hur du överför resurser till en pull-server så att de kan hämtas av konfigurationer på noderna som hanteras av DSC.
ms.openlocfilehash: a19d04346a0ae546cfcaf70701fde870d3839f65
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661694"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="28d87-104">Paketera och ladda upp resurser till en hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="28d87-104">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="28d87-105">I avsnitten nedan förutsätts att du redan har konfigurerat en hämtnings Server.</span><span class="sxs-lookup"><span data-stu-id="28d87-105">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="28d87-106">Om du inte har konfigurerat din pull-server kan du använda följande guider:</span><span class="sxs-lookup"><span data-stu-id="28d87-106">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="28d87-107">Konfigurera en DSC SMB-hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="28d87-107">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="28d87-108">Konfigurera en DSC HTTP-hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="28d87-108">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="28d87-109">Varje målnod kan konfigureras för att ladda ned konfigurationer, resurser och till och med rapportera dess status.</span><span class="sxs-lookup"><span data-stu-id="28d87-109">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="28d87-110">Den här artikeln visar hur du laddar upp resurser så att de kan laddas ned och konfigurera klienterna att ladda ned resurser automatiskt.</span><span class="sxs-lookup"><span data-stu-id="28d87-110">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="28d87-111">När noden tar emot en tilldelad konfiguration via **pull** eller **push** (V5) laddar den automatiskt ned eventuella resurser som krävs av konfigurationen från den plats som anges i LCM.</span><span class="sxs-lookup"><span data-stu-id="28d87-111">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="28d87-112">Paketera resurs moduler</span><span class="sxs-lookup"><span data-stu-id="28d87-112">Package Resource Modules</span></span>

<span data-ttu-id="28d87-113">Varje resurs som är tillgänglig för en klient som ska laddas ned måste lagras i en `.zip` fil.</span><span class="sxs-lookup"><span data-stu-id="28d87-113">Each resource available for a client to download must be stored in a `.zip` file.</span></span> <span data-ttu-id="28d87-114">I exemplet nedan visas de steg som krävs med hjälp av [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) -resursen.</span><span class="sxs-lookup"><span data-stu-id="28d87-114">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="28d87-115">Om du har några klienter som använder PowerShell 4,0 måste du förenkla resurs mappstrukturen och ta bort alla versions-mappar.</span><span class="sxs-lookup"><span data-stu-id="28d87-115">If you have any clients using PowerShell 4.0, you will need to flatten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="28d87-116">Mer information finns i [flera resurs versioner](../configurations/import-dscresource.md#multiple-resource-versions).</span><span class="sxs-lookup"><span data-stu-id="28d87-116">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="28d87-117">Du kan komprimera resurs katalogen med valfritt verktyg, skript eller metod som du föredrar.</span><span class="sxs-lookup"><span data-stu-id="28d87-117">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="28d87-118">I Windows kan du _högerklicka_ på `xPSDesiredStateConfiguration` katalogen och välja **Skicka till** och sedan på **komprimerad mapp** .</span><span class="sxs-lookup"><span data-stu-id="28d87-118">In Windows, you can _right-click_ on the `xPSDesiredStateConfiguration` directory, and select **Send To** , then **Compressed Folder** .</span></span>

![Högerklicka – skicka till komprimerad mapp](media/package-upload-resources/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="28d87-120">Namnge resurs arkivet</span><span class="sxs-lookup"><span data-stu-id="28d87-120">Naming the Resource Archive</span></span>

<span data-ttu-id="28d87-121">Resurs arkivet måste ha namnet med följande format:</span><span class="sxs-lookup"><span data-stu-id="28d87-121">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="28d87-122">I exemplet ovan `xPSDesiredStateConfiguration.zip` bör byta namn `xPSDesiredStateConfiguration_8.4.4.0.zip` .</span><span class="sxs-lookup"><span data-stu-id="28d87-122">In the example above, `xPSDesiredStateConfiguration.zip` should be renamed `xPSDesiredStateConfiguration_8.4.4.0.zip`.</span></span>

### <a name="create-checksums"></a><span data-ttu-id="28d87-123">Skapa kontroll summor</span><span class="sxs-lookup"><span data-stu-id="28d87-123">Create CheckSums</span></span>

<span data-ttu-id="28d87-124">När modulen har komprimerats och bytt namn måste du skapa en **kontroll Summa** .</span><span class="sxs-lookup"><span data-stu-id="28d87-124">Once the Resource module has been compressed and renamed, you need to create a **CheckSum** .</span></span> <span data-ttu-id="28d87-125">**Kontroll summan** används av LCM på klienten för att avgöra om resursen har ändrats och måste laddas ned igen.</span><span class="sxs-lookup"><span data-stu-id="28d87-125">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="28d87-126">Du kan skapa en **kontroll Summa** med cmdleten [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) , som visas i exemplet nedan.</span><span class="sxs-lookup"><span data-stu-id="28d87-126">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="28d87-127">Inga utdata visas, men nu bör du se en "xPSDesiredStateConfiguration_8.4.4.0.zip. kontroll Summa".</span><span class="sxs-lookup"><span data-stu-id="28d87-127">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="28d87-128">Du kan också köra `New-DSCCheckSum` mot en katalog med filer med hjälp av `-Path` parametern.</span><span class="sxs-lookup"><span data-stu-id="28d87-128">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="28d87-129">Om det redan finns en kontroll summa kan du tvinga den att skapas igen med `-Force` parametern.</span><span class="sxs-lookup"><span data-stu-id="28d87-129">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="28d87-130">Var resurs Arkiv ska lagras</span><span class="sxs-lookup"><span data-stu-id="28d87-130">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="28d87-131">På en DSC HTTP-pull-server</span><span class="sxs-lookup"><span data-stu-id="28d87-131">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="28d87-132">När du konfigurerar din HTTP-pull-server, enligt beskrivningen i [Konfigurera en DSC HTTP-pull-server](pullServer.md), anger du kataloger för nycklarna **ModulePath** och **ConfigurationPath** .</span><span class="sxs-lookup"><span data-stu-id="28d87-132">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="28d87-133">**ConfigurationPath** -nyckeln anger var alla ". MOF"-filer ska lagras.</span><span class="sxs-lookup"><span data-stu-id="28d87-133">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="28d87-134">**ModulePath** anger var DSC-resurspooler ska lagras.</span><span class="sxs-lookup"><span data-stu-id="28d87-134">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="28d87-135">På en SMB-resurs</span><span class="sxs-lookup"><span data-stu-id="28d87-135">On an SMB Share</span></span>

<span data-ttu-id="28d87-136">Om du har angett en **ResourceRepositoryShare** när du konfigurerar din pull-klient, lagrar Arkiv och kontroll summor i katalogen **SourcePath** från **ResourceRepositoryShare** -blocket.</span><span class="sxs-lookup"><span data-stu-id="28d87-136">If you specified a **ResourceRepositoryShare** , when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

<span data-ttu-id="28d87-137">Om du bara har angett en **ConfigurationRepositoryShare** , när du konfigurerar din pull-klient, lagrar Arkiv och kontroll summor i **SourcePath** -katalogen från **ConfigurationRepositoryShare** -blocket.</span><span class="sxs-lookup"><span data-stu-id="28d87-137">If you specified only a **ConfigurationRepositoryShare** , when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="28d87-138">Uppdaterar resurser</span><span class="sxs-lookup"><span data-stu-id="28d87-138">Updating resources</span></span>

<span data-ttu-id="28d87-139">Du kan tvinga en nod att uppdatera sina resurser genom att ändra versions numret i arkivets namn, eller genom att skapa en ny kontroll summa.</span><span class="sxs-lookup"><span data-stu-id="28d87-139">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="28d87-140">Hämtnings klienten söker efter nyare versioner av nödvändiga resurser, samt uppdaterade kontroll summor, när dess LCM uppdateras.</span><span class="sxs-lookup"><span data-stu-id="28d87-140">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="28d87-141">Se även</span><span class="sxs-lookup"><span data-stu-id="28d87-141">See also</span></span>

- [<span data-ttu-id="28d87-142">Konfigurera en DSC SMB-hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="28d87-142">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="28d87-143">Konfigurera en DSC HTTP-hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="28d87-143">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
