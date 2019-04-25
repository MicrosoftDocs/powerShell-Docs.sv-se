---
title: Skriva en provider med objektet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: 9285a2f0e673de8b86084157423512bdeeda109d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080823"
---
# <a name="writing-an-item-provider"></a>Skriva en objektprovider

Det här avsnittet beskriver hur du implementerar-metoderna i en Windows PowerShell-providern som kommer åt och ändra objekt i datalagret. Om du vill kunna komma åt objekt, en leverantör måste komma från den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klass.

Providern i exemplen i det här avsnittet använder en Access-databas som dess datalager. Det finns flera hjälpmetoder och klasser som används för att interagera med databasen. Hela exemplet som innehåller helper-metoder, se [AccessDBProviderSample03](./accessdbprovidersample03.md)

Mer information om Windows PowerShell-providrar finns i [Windows PowerShell-providern översikt](./windows-powershell-provider-overview.md).

## <a name="implementing-item-methods"></a>Implementera objektet metoder

Den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klassen visar flera metoder som kan användas för att komma åt och ändra objekt i ett datalager. En fullständig lista över dessa metoder, se [ItemCmdletProvider metoder](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx). I det här exemplet implementerar vi fyra av dessa metoder. [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) hämtar ett objekt på en angiven sökväg. [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) anger värdet för det angivna objektet. [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) kontrollerar om det finns ett objekt i den angivna sökvägen. [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) kontrollerar en sökväg för att se om det mappas till en plats i datalagret.

> [!NOTE]
> Det här avsnittet bygger på informationen i [Windows PowerShell-providern Snabbstart](./windows-powershell-provider-quickstart.md). Det här avsnittet beskriver inte grunderna för hur du ställer in ett provider-projekt eller hur du implementerar metoderna som ärvts från den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klass som skapar och tar bort enheter.

### <a name="declaring-the-provider-class"></a>Fastställa providerklassen

Deklarera providern kan härledas från den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klassen och anpassa den med den [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>Implementera GetItem

Den [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) anropas av PowerShell-motorn när en användare anropar den [Microsoft.PowerShell.Commands.Get-Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdleten på din providern. Metoden returnerar objektet på den angivna sökvägen. I exemplet Access database kontrollerar metoden om objektet är själva enheten, en tabell i databasen, eller en rad i databasen. Metoden skickar objektet till PowerShell-motorn genom att anropa den [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) metod.

```csharp
protected override void GetItem(string path)
      {
          // check if the path represented is a drive
          if (PathIsDrive(path))
          {
              WriteItemObject(this.PSDriveInfo, path, true);
              return;
          }// if (PathIsDrive...

           // Get table name and row information from the path and do
           // necessary actions
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               DatabaseTableInfo table = GetTable(tableName);
               WriteItemObject(table, path, true);
           }
           else if (type == PathType.Row)
           {
               DatabaseRowInfo row = GetRow(tableName, rowNumber);
               WriteItemObject(row, path, false);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

### <a name="implementing-setitem"></a>Implementera SetItem

Den [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metoden anropas av PowerShell-motorn anrop när en användare anropar den [Microsoft.PowerShell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet . Anger värdet för objektet på den angivna sökvägen.

I exemplet Access-databasen är det praktiskt att ange värdet för ett objekt bara om objektet är en rad, så att metoden utlöser [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) när objektet är inte en rad.

```csharp
protected override void SetItem(string path, object values)
       {
           // Get type, table name and row number from the path specified
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type != PathType.Row)
           {
               WriteError(new ErrorRecord(new NotSupportedException(
                     "SetNotSupported"), "",
                  ErrorCategory.InvalidOperation, path));

               return;
           }

           // Get in-memory representation of table
           OdbcDataAdapter da = GetAdapterForTable(tableName);

           if (da == null)
           {
               return;
           }
           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           if (rowNumber >= table.Rows.Count)
           {
               // The specified row number has to be available. If not
               // NewItem has to be used to add a new row
               throw new ArgumentException("Row specified is not available");
           } // if (rowNum...

           string[] colValues = (values as string).Split(',');

           // set the specified row
           DataRow row = table.Rows[rowNumber];

           for (int i = 0; i < colValues.Length; i++)
           {
               row[i] = colValues[i];
           }

           // Update the table
           if (ShouldProcess(path, "SetItem"))
           {
               da.Update(ds, tableName);
           }

       }
```

### <a name="implementing-itemexists"></a>Implementera ItemExists

Den [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metoden anropas av PowerShell-motorn när en användare anropar den [Microsoft.PowerShell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet. Metoden anger om det finns ett objekt på den angivna sökvägen. Om objektet finns metoden skickar det tillbaka till PowerShell-motorn genom att anropa [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).

```csharp
protected override bool ItemExists(string path)
       {
           // check if the path represented is a drive
           if (PathIsDrive(path))
           {
               return true;
           }

           // Obtain type, table name and row number from path
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           DatabaseTableInfo table = GetTable(tableName);

           if (type == PathType.Table)
           {
               // if specified path represents a table then DatabaseTableInfo
               // object for the same should exist
               if (table != null)
               {
                   return true;
               }
           }
           else if (type == PathType.Row)
           {
               // if specified path represents a row then DatabaseTableInfo should
               // exist for the table and then specified row number must be within
               // the maximum row count in the table
               if (table != null && rowNumber < table.RowCount)
               {
                   return true;
               }
           }

           return false;

       }
```

### <a name="implementing-isvalidpath"></a>Implementera IsValidPath

Den [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metod för att kontrollera om den angivna sökvägen är syntaktiskt giltig för den aktuella providern. Intune kontrollerar inte om det finns ett objekt i sökvägen.

```csharp
protected override bool IsValidPath(string path)
       {
           bool result = true;

           // check if the path is null or empty
           if (String.IsNullOrEmpty(path))
           {
               result = false;
           }

           // convert all separators in the path to a uniform one
           path = NormalizePath(path);

           // split the path into individual chunks
           string[] pathChunks = path.Split(pathSeparator.ToCharArray());

           foreach (string pathChunk in pathChunks)
           {
               if (pathChunk.Length == 0)
               {
                   result = false;
               }
           }
           return result;
       }
```

## <a name="next-steps"></a>Nästa steg

En typisk verkliga-provider kan ge stöd för objekt som innehåller andra objekt och för att flytta objekt från en sökväg till en annan i enheten. Ett exempel på en provider som stöder behållare finns i [skriva en behållare provider](./writing-a-container-provider.md). Ett exempel på en provider som stöder flytta objekt, se [skriva en leverantör av navigering](./writing-a-navigation-provider.md).

## <a name="see-also"></a>Se även

[Skriva en container-provider](./writing-a-container-provider.md)

[Skriva en provider för navigering](./writing-a-navigation-provider.md)

[Översikt för Windows PowerShell-providern](./windows-powershell-provider-overview.md)