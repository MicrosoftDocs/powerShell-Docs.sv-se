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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352362"
---
# <a name="windows-powershell-provider-quickstart"></a>Snabbstart för Windows PowerShell-providers

I det här avsnittet beskrivs hur du skapar en Windows PowerShell-provider som har grundläggande funktioner för att skapa en ny enhet. Allmän information om leverantörer finns i [Översikt över Windows PowerShell-Provider](./windows-powershell-provider-overview.md). Exempel på leverantörer med mer kompletta funktioner finns i [Provider-exempel](./provider-samples.md).

## <a name="writing-a-basic-provider"></a>Skriva en grundläggande Provider

De mest grundläggande funktionerna i en Windows PowerShell-Provider är att skapa och ta bort enheter. I det här exemplet implementerar vi [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) och [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metoderna i klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Du kommer också att se hur du deklarerar en provider-klass.

När du skriver en provider kan du ange standard enheter – enheter som skapas automatiskt när leverantören är tillgänglig. Du definierar också en metod för att skapa nya enheter som använder providern.

Exemplen som anges i det här avsnittet baseras på [AccessDBProviderSample02](./accessdbprovidersample02.md) -exemplet, som är en del av ett större exempel som representerar en Access-databas som en Windows PowerShell-enhet.

### <a name="setting-up-the-project"></a>Konfigurerar projektet

Skapa ett klass biblioteks projekt med namnet AccessDBProviderSample i Visual Studio. Slutför följande steg för att konfigurera ditt projekt så att Windows PowerShell startar och providern kommer att läsas in i sessionen när du skapar och startar projektet.

##### <a name="configure-the-provider-project"></a>Konfigurera providerns projekt

1. Lägg till sammansättningen system. Management. Automation som en referens till ditt projekt.

2. Klicka på **Project > AccessDBProviderSample-egenskaper > Felsök**. I **Start Project**klickar du på **Starta externt program**och navigerar till Windows PowerShell-filen (vanligt vis c:\Windows\System32\WindowsPowerShell\v1.0\\. PowerShell. exe).

3. Under **Start alternativ**anger du följande i rutan **kommando rads argument** : `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>Deklarera Provider-klassen

Leverantören härleds från klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . De flesta leverantörer som tillhandahåller verkliga funktioner (åtkomst till och manipulering av objekt, navigering i data lagringen och hämtning och inställning av innehåll för objekt) härleds från klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

Förutom att ange att klassen är härledd från [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), måste du dekorera den med [system. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) som visas i exemplet.

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

Metoden [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) anropas av Windows PowerShell-motorn när en användare anropar cmdleten [Microsoft. PowerShell. commands. NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) som anger namnet på din Provider. PSDriveInfo-parametern skickas av Windows PowerShell-motorn och metoden returnerar den nya enheten till Windows PowerShell-motorn. Den här metoden måste deklareras inom klassen som skapats ovan.

Metoden kontrollerar först att både enhetsobjektet och enhets roten som skickades finns, och returnerar `null` om någon av dem inte gör det. Den använder sedan en konstruktor för den interna klassen AccessDBPSDriveInfo för att skapa en ny enhet och en anslutning till den åtkomst databas enheten representerar.

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

Följande är den interna AccessDBPSDriveInfo-klassen som innehåller konstruktorn som används för att skapa en ny enhet och innehåller Tillståndsinformation för enheten.

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

Metoden [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) anropas av Windows PowerShell-motorn när en användare anropar cmdleten [Microsoft. PowerShell. commands. RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) . Metoden i den här providern stänger anslutningen till Access-databasen.

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