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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080891"
---
# <a name="windows-powershell-provider-quickstart"></a>Snabbstart för Windows PowerShell-providers

Det här avsnittet beskriver hur du skapar en Windows PowerShell-providern som har grundläggande funktioner för att skapa en ny enhet. Allmän information om leverantörer finns i [Windows PowerShell-providern översikt](./windows-powershell-provider-overview.md). Exempel på leverantörer med fullständig funktionalitet finns [providern exempel](./provider-samples.md).

## <a name="writing-a-basic-provider"></a>Skriva en grundläggande provider

De mest grundläggande funktionerna i en Windows PowerShell-providern är att skapa och ta bort enheter. I det här exemplet vi implementera den [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) och [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metoder för att den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klass. Du kan även se hur du deklarerar en providerklass.

Du kan ange standard-enheter – enheter som skapas automatiskt när providern är tillgänglig när du skriver en provider. Du kan också definiera en metod för att skapa nya enheter som använder providern.

Exemplen i det här avsnittet baseras på den [AccessDBProviderSample02](./accessdbprovidersample02.md) samplet, som är en del av en större kodexemplet som representerar en Access-databas som en Windows PowerShell-enhet.

### <a name="setting-up-the-project"></a>Konfigurera projektet

Skapa ett Class Library-projekt med namnet AccessDBProviderSample i Visual Studio. Utför följande steg för att konfigurera ditt projekt så att Windows PowerShell startas och providern kommer att läsas in i sessionen, när du skapar och startar ditt projekt.

##### <a name="configure-the-provider-project"></a>Konfigurera provider-projektet

1. Lägg till sammansättningen System.Management.Automation som en referens till ditt projekt.

2. Klicka på **projekt > AccessDBProviderSample Egenskaper > Felsöka**. I **Spustit projekt**, klickar du på **Start externa program**, och gå till Windows PowerShell körbar fil (vanligtvis c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).

3. Under **starta alternativ**, anger du följande i den **kommandoradsargument** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>Fastställa providerklassen

Vår leverantör som härleds från den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klass. De flesta leverantörer som ger verkliga funktioner (åtkomst till och manipulera objekt, navigering datalager, och hämta och ange innehållet i objekt) som härleds från den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klass.

Förutom att ange att klassen härleds från [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), måste du anpassa den med den [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) som visas i exemplet.

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

### <a name="implementing-newdrive"></a>Implementera NewDrive

Den [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metoden anropas av Windows PowerShell-motorn när en användare anropar den [Microsoft.PowerShell.Commands.New PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)cmdlet som anger namnet på leverantören. Parametern PSDriveInfo skickas av Windows PowerShell-motorn och den nya enheten returneras till Windows PowerShell-motorn. Den här metoden måste deklareras i klassen som skapade ovan.

Metoden kontrollerar först kontrollera att både enhetsobjektet och enheten roten som skickades i finns, returnerar `null` om någon av dem inte. Det använder sedan en konstruktor i klassen interna AccessDBPSDriveInfo för att skapa en ny enhet och en anslutning till Access-databas enheten representerar.

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

Följande är AccessDBPSDriveInfo interna klassen som innehåller konstruktorn som används för att skapa en ny enhet och innehåller tillståndsinformation om för enheten.

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

### <a name="implementing-removedrive"></a>Implementera RemoveDrive

Den [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metoden anropas av Windows PowerShell-motorn när en användare anropar den [Microsoft.PowerShell.Commands.Remove PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet. -Metoden i den här providern stängs anslutningen till Access-databas.

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