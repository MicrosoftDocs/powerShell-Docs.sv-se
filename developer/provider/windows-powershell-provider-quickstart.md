---
title: Windows PowerShell-providern Snabbstart | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: 151b7125afe1b0d386467a0e5f89225716857ac2
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054925"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="56cde-102">Snabbstart för Windows PowerShell-providers</span><span class="sxs-lookup"><span data-stu-id="56cde-102">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="56cde-103">Det här avsnittet beskriver hur du skapar en Windows PowerShell-providern som har grundläggande funktioner för att skapa en ny enhet.</span><span class="sxs-lookup"><span data-stu-id="56cde-103">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="56cde-104">Allmän information om leverantörer finns i [Windows PowerShell-providern översikt](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="56cde-104">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="56cde-105">Exempel på leverantörer med fullständig funktionalitet finns [providern exempel](./provider-samples.md).</span><span class="sxs-lookup"><span data-stu-id="56cde-105">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="56cde-106">Skriva en grundläggande provider</span><span class="sxs-lookup"><span data-stu-id="56cde-106">Writing a basic provider</span></span>

<span data-ttu-id="56cde-107">De mest grundläggande funktionerna i en Windows PowerShell-providern är att skapa och ta bort enheter.</span><span class="sxs-lookup"><span data-stu-id="56cde-107">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="56cde-108">I det här exemplet vi implementera den [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) och [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metoder för att den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klass.</span><span class="sxs-lookup"><span data-stu-id="56cde-108">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="56cde-109">Du kan även se hur du deklarerar en providerklass.</span><span class="sxs-lookup"><span data-stu-id="56cde-109">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="56cde-110">Du kan ange standard-enheter – enheter som skapas automatiskt när providern är tillgänglig när du skriver en provider.</span><span class="sxs-lookup"><span data-stu-id="56cde-110">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="56cde-111">Du kan också definiera en metod för att skapa nya enheter som använder providern.</span><span class="sxs-lookup"><span data-stu-id="56cde-111">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="56cde-112">Exemplen i det här avsnittet baseras på den [AccessDBProviderSample02](./accessdbprovidersample02.md) samplet, som är en del av en större kodexemplet som representerar en Access-databas som en Windows PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="56cde-112">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="56cde-113">Konfigurera projektet</span><span class="sxs-lookup"><span data-stu-id="56cde-113">Setting up the project</span></span>

<span data-ttu-id="56cde-114">Skapa ett Class Library-projekt med namnet AccessDBProviderSample i Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="56cde-114">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="56cde-115">Utför följande steg för att konfigurera ditt projekt så att Windows PowerShell startas och providern kommer att läsas in i sessionen, när du skapar och startar ditt projekt.</span><span class="sxs-lookup"><span data-stu-id="56cde-115">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="56cde-116">Konfigurera provider-projektet</span><span class="sxs-lookup"><span data-stu-id="56cde-116">Configure the provider project</span></span>

1. <span data-ttu-id="56cde-117">Lägg till sammansättningen System.Management.Automation som en referens till ditt projekt.</span><span class="sxs-lookup"><span data-stu-id="56cde-117">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="56cde-118">Klicka på **projekt > AccessDBProviderSample Egenskaper > Felsöka**.</span><span class="sxs-lookup"><span data-stu-id="56cde-118">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="56cde-119">I **Spustit projekt**, klickar du på **Start externa program**, och gå till Windows PowerShell körbar fil (vanligtvis c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).</span><span class="sxs-lookup"><span data-stu-id="56cde-119">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="56cde-120">Under **starta alternativ**, anger du följande i den **kommandoradsargument** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="56cde-120">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="56cde-121">Fastställa providerklassen</span><span class="sxs-lookup"><span data-stu-id="56cde-121">Declaring the provider class</span></span>

<span data-ttu-id="56cde-122">Vår leverantör som härleds från den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klass.</span><span class="sxs-lookup"><span data-stu-id="56cde-122">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="56cde-123">De flesta leverantörer som ger verkliga funktioner (åtkomst till och manipulera objekt, navigering datalager, och hämta och ange innehållet i objekt) som härleds från den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klass.</span><span class="sxs-lookup"><span data-stu-id="56cde-123">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="56cde-124">Förutom att ange att klassen härleds från [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), måste du anpassa den med den [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) som visas i exemplet.</span><span class="sxs-lookup"><span data-stu-id="56cde-124">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System;
  using System.Data;
  using System.Data.Odbc;
  using System.IO;
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  #region AccessDBProvider

  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : DriveCmdletProvider
  {

}
}
```

### <a name="implementing-newdrive"></a><span data-ttu-id="56cde-125">Implementera NewDrive</span><span class="sxs-lookup"><span data-stu-id="56cde-125">Implementing NewDrive</span></span>

<span data-ttu-id="56cde-126">Den [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metoden anropas av Windows PowerShell-motorn när en användare anropar den [Microsoft.PowerShell.Commands.New PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)cmdlet som anger namnet på leverantören.</span><span class="sxs-lookup"><span data-stu-id="56cde-126">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="56cde-127">Parametern PSDriveInfo skickas av Windows PowerShell-motorn och den nya enheten returneras till Windows PowerShell-motorn.</span><span class="sxs-lookup"><span data-stu-id="56cde-127">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="56cde-128">Den här metoden måste deklareras i klassen som skapade ovan.</span><span class="sxs-lookup"><span data-stu-id="56cde-128">This method must be declared within the class created above.</span></span>

<span data-ttu-id="56cde-129">Metoden kontrollerar först kontrollera att både enhetsobjektet och enheten roten som skickades i finns, returnerar `null` om någon av dem inte.</span><span class="sxs-lookup"><span data-stu-id="56cde-129">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="56cde-130">Det använder sedan en konstruktor i klassen interna AccessDBPSDriveInfo för att skapa en ny enhet och en anslutning till Access-databas enheten representerar.</span><span class="sxs-lookup"><span data-stu-id="56cde-130">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

```csharp
protected override PSDriveInfo NewDrive(PSDriveInfo drive)
    {
      // Check if the drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   null));

        return null;
      }

      // Check if the drive root is not null or empty
      // and if it is an existing file.
      if (String.IsNullOrEmpty(drive.Root) || (File.Exists(drive.Root) == false))
      {
        WriteError(new ErrorRecord(
                   new ArgumentException("drive.Root"),
                   "NoRoot",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Create a new drive and create an ODBC connection to the new drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = new AccessDBPSDriveInfo(drive);
      OdbcConnectionStringBuilder builder = new OdbcConnectionStringBuilder();

      builder.Driver = "Microsoft Access Driver (*.mdb)";
      builder.Add("DBQ", drive.Root);

      OdbcConnection conn = new OdbcConnection(builder.ConnectionString);
      conn.Open();
      accessDBPSDriveInfo.Connection = conn;

      return accessDBPSDriveInfo;
    }
```

<span data-ttu-id="56cde-131">Följande är AccessDBPSDriveInfo interna klassen som innehåller konstruktorn som används för att skapa en ny enhet och innehåller tillståndsinformation om för enheten.</span><span class="sxs-lookup"><span data-stu-id="56cde-131">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

```csharp
internal class AccessDBPSDriveInfo : PSDriveInfo
  {
    /// <summary>
    /// A reference to the connection to the database.
    /// </summary>
    private OdbcConnection connection;

    /// <summary>
    /// Initializes a new instance of the AccessDBPSDriveInfo class.
    /// The constructor takes a single argument.
    /// </summary>
    /// <param name="driveInfo">Drive defined by this provider</param>
    public AccessDBPSDriveInfo(PSDriveInfo driveInfo)
           : base(driveInfo)
    {
    }

    /// <summary>
    /// Gets or sets the ODBC connection information.
    /// </summary>
    public OdbcConnection Connection
    {
        get { return this.connection; }
        set { this.connection = value; }
    }
  }
```

### <a name="implementing-removedrive"></a><span data-ttu-id="56cde-132">Implementera RemoveDrive</span><span class="sxs-lookup"><span data-stu-id="56cde-132">Implementing RemoveDrive</span></span>

<span data-ttu-id="56cde-133">Den [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metoden anropas av Windows PowerShell-motorn när en användare anropar den [Microsoft.PowerShell.Commands.Remove PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="56cde-133">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet.</span></span> <span data-ttu-id="56cde-134">-Metoden i den här providern stängs anslutningen till Access-databas.</span><span class="sxs-lookup"><span data-stu-id="56cde-134">The method in this provider closes the connection to the Access database.</span></span>

```csharp
protected override PSDriveInfo RemoveDrive(PSDriveInfo drive)
    {
      // Check if drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Close the ODBC connection to the drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = drive as AccessDBPSDriveInfo;

      if (accessDBPSDriveInfo == null)
      {
         return null;
      }

      accessDBPSDriveInfo.Connection.Close();

      return accessDBPSDriveInfo;
    }
```