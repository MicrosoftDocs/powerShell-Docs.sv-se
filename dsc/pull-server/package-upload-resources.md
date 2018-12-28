---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Paket- och ladda upp resurser till en Pull-Server
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404757"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="6f041-103">Paket- och ladda upp resurser till en Pull-Server</span><span class="sxs-lookup"><span data-stu-id="6f041-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="6f041-104">I avsnitten nedan förutsätter att du har ställt in en Pull-servern.</span><span class="sxs-lookup"><span data-stu-id="6f041-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="6f041-105">Om du inte har konfigurerat din Pull-servern kan du använda följande guider:</span><span class="sxs-lookup"><span data-stu-id="6f041-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="6f041-106">Konfigurera en DSC SMB-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="6f041-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="6f041-107">Konfigurera en DSC HTTP-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="6f041-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="6f041-108">Varje målnoden kan konfigureras för att hämta konfigurationer, resurser, och även rapportera statusen.</span><span class="sxs-lookup"><span data-stu-id="6f041-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="6f041-109">Den här artikeln visar hur du laddar upp resurser så att de blir tillgängliga för att hämta och konfigurera klienter för att hämta resurser automatiskt.</span><span class="sxs-lookup"><span data-stu-id="6f041-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="6f041-110">När nod som tar emot en tilldelade konfiguration via **hämta** eller **Push** (v5) hämtas automatiskt alla resurser som krävs av konfigurationen från den plats som anges i LCM.</span><span class="sxs-lookup"><span data-stu-id="6f041-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="6f041-111">Paketet Resource moduler</span><span class="sxs-lookup"><span data-stu-id="6f041-111">Package Resource Modules</span></span>

<span data-ttu-id="6f041-112">Varje resurs som är tillgängliga för en klient för att ladda ned måste lagras i en ”ZIP”-fil.</span><span class="sxs-lookup"><span data-stu-id="6f041-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="6f041-113">Exemplet nedan visar de steg som krävs med hjälp av den [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resurs.</span><span class="sxs-lookup"><span data-stu-id="6f041-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="6f041-114">Om du har alla klienter som använder PowerShell 4.0, du behöver flaten mappstrukturen för resursen och ta bort alla version mappar.</span><span class="sxs-lookup"><span data-stu-id="6f041-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="6f041-115">Mer information finns i [flera versioner av resursen](../configurations/import-dscresource.md#multiple-resource-versions).</span><span class="sxs-lookup"><span data-stu-id="6f041-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="6f041-116">Du kan komprimera resursbiblioteket med hjälp av verktyg, skript eller metod som du föredrar.</span><span class="sxs-lookup"><span data-stu-id="6f041-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="6f041-117">I Windows, kan du *högerklickar du på* på ”xPSDesiredStateConfiguration” katalog- och välj ”Skicka till” och sedan ”komprimerade mappen”.</span><span class="sxs-lookup"><span data-stu-id="6f041-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![Högerklicka på](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="6f041-119">Namnge resursen arkivet</span><span class="sxs-lookup"><span data-stu-id="6f041-119">Naming the Resource Archive</span></span>

<span data-ttu-id="6f041-120">Resurs-arkivet måste ha namnet med följande format:</span><span class="sxs-lookup"><span data-stu-id="6f041-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="6f041-121">I exemplet ovan ska ”xPSDesiredStateConfiguration.zip” omdöpt ”xPSDesiredStateConfiguration_8.4.4.0.zip”.</span><span class="sxs-lookup"><span data-stu-id="6f041-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="6f041-122">Skapa kontrollsummor</span><span class="sxs-lookup"><span data-stu-id="6f041-122">Create CheckSums</span></span>

<span data-ttu-id="6f041-123">När modulen resurs har komprimeras och byta namn på, måste du skapa en **kontrollsumma**.</span><span class="sxs-lookup"><span data-stu-id="6f041-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="6f041-124">Den **kontrollsumma** används av LCM på klienten för att avgöra om resursen har ändrats och måste hämtas igen.</span><span class="sxs-lookup"><span data-stu-id="6f041-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="6f041-125">Du kan skapa en **kontrollsumma** med den [New DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, enligt exemplet nedan.</span><span class="sxs-lookup"><span data-stu-id="6f041-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="6f041-126">Inga utdata visas, men du bör nu se en ”xPSDesiredStateConfiguration_8.4.4.0.zip.checksum”.</span><span class="sxs-lookup"><span data-stu-id="6f041-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="6f041-127">Du kan också köra `New-DSCCheckSum` mot en katalog med filer med hjälp av den `-Path` parametern.</span><span class="sxs-lookup"><span data-stu-id="6f041-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="6f041-128">Om det finns redan en kontrollsumma, kan du tvinga den återskapas med den `-Force` parametern.</span><span class="sxs-lookup"><span data-stu-id="6f041-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="6f041-129">Var du vill lagra Resource Arkiv</span><span class="sxs-lookup"><span data-stu-id="6f041-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="6f041-130">På en DSC HTTP-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="6f041-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="6f041-131">När du konfigurerar http-Pull-servern, enligt beskrivningen i [konfigurera en DSC HTTP-Hämtningsserver](pullServer.md), anger du kataloger för den **ModulePath** och **ConfigurationPath** nycklar.</span><span class="sxs-lookup"><span data-stu-id="6f041-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="6f041-132">Den **ConfigurationPath** nyckel anger där alla MOF-filerna ska sparas.</span><span class="sxs-lookup"><span data-stu-id="6f041-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="6f041-133">Den **ModulePath** anger där alla moduler för DSC-resurs ska sparas.</span><span class="sxs-lookup"><span data-stu-id="6f041-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="6f041-134">På en SMB-resurs</span><span class="sxs-lookup"><span data-stu-id="6f041-134">On an SMB Share</span></span>

<span data-ttu-id="6f041-135">Om du har angett en **ResourceRepositoryShare**, när konfigurationen av din Pull-klienten lagrar Arkiv och kontrollsummor i den **SourcePath** katalogen från den **ResourceRepositoryShare** block.</span><span class="sxs-lookup"><span data-stu-id="6f041-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

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

<span data-ttu-id="6f041-136">Om du bara anges en **ConfigurationRepositoryShare**, när konfigurationen av din Pull-klienten lagrar Arkiv och kontrollsummor i den **SourcePath** katalogen från den  **ConfigurationRepositoryShare** block.</span><span class="sxs-lookup"><span data-stu-id="6f041-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="6f041-137">Uppdatera resurser</span><span class="sxs-lookup"><span data-stu-id="6f041-137">Updating resources</span></span>

<span data-ttu-id="6f041-138">Du kan tvinga en nod för att uppdatera dess resurser genom att ändra versionsnumret i den arkivnamn eller genom att skapa en ny kontrollsumma.</span><span class="sxs-lookup"><span data-stu-id="6f041-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="6f041-139">Hämta klienten ska söka efter nyare versioner av resurser som krävs samt uppdateras kontrollsummor, när dess LCM uppdateras.</span><span class="sxs-lookup"><span data-stu-id="6f041-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f041-140">Se även</span><span class="sxs-lookup"><span data-stu-id="6f041-140">See also</span></span>

- [<span data-ttu-id="6f041-141">Konfigurera en DSC SMB-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="6f041-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="6f041-142">Konfigurera en DSC HTTP-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="6f041-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
