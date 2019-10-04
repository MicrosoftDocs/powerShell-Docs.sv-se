---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Paketera och ladda upp resurser till en hämtnings Server
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942246"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="344dd-103">Paketera och ladda upp resurser till en hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="344dd-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="344dd-104">I avsnitten nedan förutsätts att du redan har konfigurerat en hämtnings Server.</span><span class="sxs-lookup"><span data-stu-id="344dd-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="344dd-105">Om du inte har konfigurerat din pull-server kan du använda följande guider:</span><span class="sxs-lookup"><span data-stu-id="344dd-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="344dd-106">Konfigurera en DSC SMB-pull-server</span><span class="sxs-lookup"><span data-stu-id="344dd-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="344dd-107">Konfigurera en DSC HTTP-pull-server</span><span class="sxs-lookup"><span data-stu-id="344dd-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="344dd-108">Varje målnod kan konfigureras för att ladda ned konfigurationer, resurser och till och med rapportera dess status.</span><span class="sxs-lookup"><span data-stu-id="344dd-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="344dd-109">Den här artikeln visar hur du laddar upp resurser så att de kan laddas ned och konfigurera klienterna att ladda ned resurser automatiskt.</span><span class="sxs-lookup"><span data-stu-id="344dd-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="344dd-110">När noden tar emot en tilldelad konfiguration via **pull** eller **push** (V5) laddar den automatiskt ned eventuella resurser som krävs av konfigurationen från den plats som anges i LCM.</span><span class="sxs-lookup"><span data-stu-id="344dd-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="344dd-111">Paketera resurs moduler</span><span class="sxs-lookup"><span data-stu-id="344dd-111">Package Resource Modules</span></span>

<span data-ttu-id="344dd-112">Varje resurs som är tillgänglig för en klient som ska laddas ned måste lagras i en zip-fil.</span><span class="sxs-lookup"><span data-stu-id="344dd-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="344dd-113">I exemplet nedan visas de steg som krävs med hjälp av [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) -resursen.</span><span class="sxs-lookup"><span data-stu-id="344dd-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="344dd-114">Om du har några klienter som använder PowerShell 4,0 måste du göra en plan för resurs mappstrukturen och ta bort alla versioner av mappar.</span><span class="sxs-lookup"><span data-stu-id="344dd-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="344dd-115">Mer information finns i [flera resurs versioner](../configurations/import-dscresource.md#multiple-resource-versions).</span><span class="sxs-lookup"><span data-stu-id="344dd-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="344dd-116">Du kan komprimera resurs katalogen med valfritt verktyg, skript eller metod som du föredrar.</span><span class="sxs-lookup"><span data-stu-id="344dd-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="344dd-117">I Windows kan du *högerklicka* på katalogen "xPSDesiredStateConfiguration" och välja "Skicka till" och sedan "komprimerad mapp".</span><span class="sxs-lookup"><span data-stu-id="344dd-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![Högerklicka](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="344dd-119">Namnge resurs arkivet</span><span class="sxs-lookup"><span data-stu-id="344dd-119">Naming the Resource Archive</span></span>

<span data-ttu-id="344dd-120">Resurs arkivet måste ha namnet med följande format:</span><span class="sxs-lookup"><span data-stu-id="344dd-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="344dd-121">I exemplet ovan ska "xPSDesiredStateConfiguration. zip" byta namn till "xPSDesiredStateConfiguration_ 8.4.4.0. zip".</span><span class="sxs-lookup"><span data-stu-id="344dd-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="344dd-122">Skapa kontroll summor</span><span class="sxs-lookup"><span data-stu-id="344dd-122">Create CheckSums</span></span>

<span data-ttu-id="344dd-123">När modulen har komprimerats och bytt namn måste du skapa en **kontroll Summa**.</span><span class="sxs-lookup"><span data-stu-id="344dd-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="344dd-124">**Kontroll summan** används av LCM på klienten för att avgöra om resursen har ändrats och måste laddas ned igen.</span><span class="sxs-lookup"><span data-stu-id="344dd-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="344dd-125">Du kan skapa en **kontroll Summa** med cmdleten [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) , som visas i exemplet nedan.</span><span class="sxs-lookup"><span data-stu-id="344dd-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="344dd-126">Inga utdata visas, men nu bör du se en "xPSDesiredStateConfiguration_-8.4.4.0. zip. kontroll Summa".</span><span class="sxs-lookup"><span data-stu-id="344dd-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="344dd-127">Du kan också köra `New-DSCCheckSum` mot en katalog med filer med hjälp av parametern `-Path`.</span><span class="sxs-lookup"><span data-stu-id="344dd-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="344dd-128">Om det redan finns en kontroll summa kan du tvinga den att skapas igen med parametern `-Force`.</span><span class="sxs-lookup"><span data-stu-id="344dd-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="344dd-129">Var resurs Arkiv ska lagras</span><span class="sxs-lookup"><span data-stu-id="344dd-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="344dd-130">På en DSC HTTP-pull-server</span><span class="sxs-lookup"><span data-stu-id="344dd-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="344dd-131">När du konfigurerar din HTTP-pull-server, enligt beskrivningen i [Konfigurera en DSC HTTP-pull-server](pullServer.md), anger du kataloger för nycklarna **ModulePath** och **ConfigurationPath** .</span><span class="sxs-lookup"><span data-stu-id="344dd-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="344dd-132">**ConfigurationPath** -nyckeln anger var alla ". MOF"-filer ska lagras.</span><span class="sxs-lookup"><span data-stu-id="344dd-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="344dd-133">**ModulePath** anger var DSC-resurspooler ska lagras.</span><span class="sxs-lookup"><span data-stu-id="344dd-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="344dd-134">På en SMB-resurs</span><span class="sxs-lookup"><span data-stu-id="344dd-134">On an SMB Share</span></span>

<span data-ttu-id="344dd-135">Om du har angett en **ResourceRepositoryShare**när du konfigurerar din pull-klient, lagrar Arkiv och kontroll summor i katalogen **SourcePath** från **ResourceRepositoryShare** -blocket.</span><span class="sxs-lookup"><span data-stu-id="344dd-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

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

<span data-ttu-id="344dd-136">Om du bara har angett en **ConfigurationRepositoryShare**, när du konfigurerar din pull-klient, lagrar Arkiv och kontroll summor i **SourcePath** -katalogen från **ConfigurationRepositoryShare** -blocket.</span><span class="sxs-lookup"><span data-stu-id="344dd-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="344dd-137">Uppdaterar resurser</span><span class="sxs-lookup"><span data-stu-id="344dd-137">Updating resources</span></span>

<span data-ttu-id="344dd-138">Du kan tvinga en nod att uppdatera sina resurser genom att ändra versions numret i arkivets namn, eller genom att skapa en ny kontroll summa.</span><span class="sxs-lookup"><span data-stu-id="344dd-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="344dd-139">Hämtnings klienten söker efter nyare versioner av nödvändiga resurser, samt uppdaterade kontroll summor, när dess LCM uppdateras.</span><span class="sxs-lookup"><span data-stu-id="344dd-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="344dd-140">Se även</span><span class="sxs-lookup"><span data-stu-id="344dd-140">See also</span></span>

- [<span data-ttu-id="344dd-141">Konfigurera en DSC SMB-pull-server</span><span class="sxs-lookup"><span data-stu-id="344dd-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="344dd-142">Konfigurera en DSC HTTP-pull-server</span><span class="sxs-lookup"><span data-stu-id="344dd-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
