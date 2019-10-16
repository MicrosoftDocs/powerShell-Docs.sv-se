---
title: Snabb start för Windows PowerShell-Provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: 949c0d63b1e5bca1bfe670362df4297c29e98fcc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352362"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="7a4bb-102">Snabbstart för Windows PowerShell-providers</span><span class="sxs-lookup"><span data-stu-id="7a4bb-102">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="7a4bb-103">I det här avsnittet beskrivs hur du skapar en Windows PowerShell-provider som har grundläggande funktioner för att skapa en ny enhet.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-103">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="7a4bb-104">Allmän information om leverantörer finns i [Översikt över Windows PowerShell-Provider](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7a4bb-104">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="7a4bb-105">Exempel på leverantörer med mer kompletta funktioner finns i [Provider-exempel](./provider-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7a4bb-105">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="7a4bb-106">Skriva en grundläggande Provider</span><span class="sxs-lookup"><span data-stu-id="7a4bb-106">Writing a basic provider</span></span>

<span data-ttu-id="7a4bb-107">De mest grundläggande funktionerna i en Windows PowerShell-Provider är att skapa och ta bort enheter.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-107">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="7a4bb-108">I det här exemplet implementerar vi [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) och [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metoderna i [ Klassen system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="7a4bb-108">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="7a4bb-109">Du kommer också att se hur du deklarerar en provider-klass.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-109">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="7a4bb-110">När du skriver en provider kan du ange standard enheter – enheter som skapas automatiskt när leverantören är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-110">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="7a4bb-111">Du definierar också en metod för att skapa nya enheter som använder providern.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-111">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="7a4bb-112">Exemplen som anges i det här avsnittet baseras på [AccessDBProviderSample02](./accessdbprovidersample02.md) -exemplet, som är en del av ett större exempel som representerar en Access-databas som en Windows PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-112">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="7a4bb-113">Konfigurerar projektet</span><span class="sxs-lookup"><span data-stu-id="7a4bb-113">Setting up the project</span></span>

<span data-ttu-id="7a4bb-114">Skapa ett klass biblioteks projekt med namnet AccessDBProviderSample i Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-114">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="7a4bb-115">Slutför följande steg för att konfigurera ditt projekt så att Windows PowerShell startar och providern kommer att läsas in i sessionen när du skapar och startar projektet.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-115">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="7a4bb-116">Konfigurera providerns projekt</span><span class="sxs-lookup"><span data-stu-id="7a4bb-116">Configure the provider project</span></span>

1. <span data-ttu-id="7a4bb-117">Lägg till sammansättningen system. Management. Automation som en referens till ditt projekt.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-117">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="7a4bb-118">Klicka på **Project > AccessDBProviderSample-egenskaper > Felsök**.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-118">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="7a4bb-119">I **Start Project**klickar du på **Starta externt program**och navigerar till Windows PowerShell-filen (vanligt vis c:\windows\system32\windowspowershell\ v1.0\\.powershell.exe).</span><span class="sxs-lookup"><span data-stu-id="7a4bb-119">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="7a4bb-120">Under **Start alternativ**anger du följande i rutan **kommando rads argument** : `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="7a4bb-120">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="7a4bb-121">Deklarera Provider-klassen</span><span class="sxs-lookup"><span data-stu-id="7a4bb-121">Declaring the provider class</span></span>

<span data-ttu-id="7a4bb-122">Leverantören härleds från klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="7a4bb-122">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="7a4bb-123">De flesta leverantörer som tillhandahåller verkliga funktioner (åtkomst till och manipulering av objekt, navigering i data lagringen och hämtning och inställning av innehåll för objekt) härleds från klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="7a4bb-123">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="7a4bb-124">Förutom att ange att klassen är härledd från [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), måste du dekorera den med [system. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) som visas i exemplet .</span><span class="sxs-lookup"><span data-stu-id="7a4bb-124">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

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

### <a name="implementing-newdrive"></a><span data-ttu-id="7a4bb-125">Implementera NewDrive</span><span class="sxs-lookup"><span data-stu-id="7a4bb-125">Implementing NewDrive</span></span>

<span data-ttu-id="7a4bb-126">Metoden [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) anropas av Windows PowerShell-motorn när en användare anropar cmdleten [Microsoft. PowerShell. commands. NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) som anger namnet på din CSP.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-126">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="7a4bb-127">PSDriveInfo-parametern skickas av Windows PowerShell-motorn och metoden returnerar den nya enheten till Windows PowerShell-motorn.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-127">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="7a4bb-128">Den här metoden måste deklareras inom klassen som skapats ovan.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-128">This method must be declared within the class created above.</span></span>

<span data-ttu-id="7a4bb-129">Metoden kontrollerar först att både enhetsobjektet och enhets roten som skickades finns, returnerar `null` om någon av dem inte gör det.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-129">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="7a4bb-130">Den använder sedan en konstruktor för den interna klassen AccessDBPSDriveInfo för att skapa en ny enhet och en anslutning till den åtkomst databas enheten representerar.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-130">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

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

<span data-ttu-id="7a4bb-131">Följande är den interna AccessDBPSDriveInfo-klassen som innehåller konstruktorn som används för att skapa en ny enhet och innehåller Tillståndsinformation för enheten.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-131">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

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

### <a name="implementing-removedrive"></a><span data-ttu-id="7a4bb-132">Implementera RemoveDrive</span><span class="sxs-lookup"><span data-stu-id="7a4bb-132">Implementing RemoveDrive</span></span>

<span data-ttu-id="7a4bb-133">Metoden [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) anropas av Windows PowerShell-motorn när en användare anropar cmdleten [Microsoft. PowerShell. commands. RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) .</span><span class="sxs-lookup"><span data-stu-id="7a4bb-133">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) cmdlet.</span></span> <span data-ttu-id="7a4bb-134">Metoden i den här providern stänger anslutningen till Access-databasen.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-134">The method in this provider closes the connection to the Access database.</span></span>

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