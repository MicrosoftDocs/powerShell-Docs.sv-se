---
title: Skriver en objekt leverantör | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: 12d2cb8c40c9fd6278bb964a6259d03167536195
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352334"
---
# <a name="writing-an-item-provider"></a>Skriva en objektprovider

I det här avsnittet beskrivs hur du implementerar metoder för en Windows PowerShell-provider som har åtkomst till och hanterar objekt i data lagret. För att kunna komma åt objekt måste en provider härledas från klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .

Providern i exemplen i det här avsnittet använder en Access-databas som data lager. Det finns flera hjälp metoder och klasser som används för att interagera med databasen. Det fullständiga exemplet som innehåller hjälp metoder finns i [AccessDBProviderSample03](./accessdbprovidersample03.md)

Mer information om Windows PowerShell-leverantörer finns i [Översikt över Windows PowerShell-Provider](./windows-powershell-provider-overview.md).

## <a name="implementing-item-methods"></a>Implementera objekt metoder

Klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) visar flera metoder som kan användas för att få åtkomst till och manipulera objekt i ett data lager. En fullständig lista över dessa metoder finns i [ItemCmdletProvider-metoder](/dotnet/api/system.management.automation.provider.itemcmdletprovider?view=pscore-6.2.0#methods). I det här exemplet ska vi implementera fyra av dessa metoder. [System. Management. Automation. Provider. Itemcmdletprovider. getItem, *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) hämtar ett objekt vid en angiven sökväg. [System. Management. Automation. Provider. Itemcmdletprovider. setItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) anger värdet för det angivna objektet. [System. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) kontrollerar om ett objekt finns på den angivna sökvägen. [System. Management. Automation. Provider. Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) kontrollerar en sökväg för att se om den mappas till en plats i data lagret.

> [!NOTE]
> Det här avsnittet bygger på informationen i [snabb starten för Windows PowerShell-providern](./windows-powershell-provider-quickstart.md). Det här avsnittet beskriver inte grunderna för hur du konfigurerar ett Provider-projekt eller hur du implementerar de metoder som ärvts från klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) som skapar och tar bort enheter.

### <a name="declaring-the-provider-class"></a>Deklarera Provider-klassen

Deklarera providern som ska härledas från klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) och dekorera den med [system. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>Implementera getItem,

[System. Management. Automation. Provider. Itemcmdletprovider. getItem, *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) anropas av PowerShell-motorn när en användare anropar cmdleten [Microsoft. PowerShell. commands. GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) på din Provider. Metoden returnerar objektet på den angivna sökvägen. I Access Database-exemplet kontrollerar metoden om objektet är själva enheten, en tabell i databasen eller en rad i databasen. Metoden skickar objektet till PowerShell-motorn genom att anropa metoden [system. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) .

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

Metoden [system. Management. Automation. Provider. Itemcmdletprovider. setItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) anropas av PowerShell-motorn anrop när en användare anropar cmdleten [Microsoft. PowerShell. commands. SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) . Värdet för objektet anges på den angivna sökvägen.

I Access Database-exemplet är det klokt att ange värdet för ett objekt endast om objektet är en rad, så att metoden returnerar [NotSupportedException](/dotnet/api/system.notsupportedexception?view=netframework-4.8) när objektet inte är en rad.

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

Metoden [system. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) anropas av PowerShell-motorn när en användare anropar cmdleten [Microsoft. PowerShell. commands. TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) . Metoden avgör om det finns ett objekt på den angivna sökvägen. Om objektet finns skickar metoden tillbaka den till PowerShell-motorn genom att anropa [system. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).

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

Metoden [system. Management. Automation. Provider. Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) kontrollerar om den angivna sökvägen är syntaktiskt giltig för den aktuella providern. Den kontrollerar inte om ett objekt finns på sökvägen.

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

En typisk verklig Provider kan stödja objekt som innehåller andra objekt och för att flytta objekt från en sökväg till en annan i enheten. Ett exempel på en provider som stöder behållare finns i [skriva en container-Provider](./writing-a-container-provider.md). Ett exempel på en provider som stöder flytta objekt finns i [skriva en navigerings leverantör](./writing-a-navigation-provider.md).

## <a name="see-also"></a>Se även

[Skriver en container leverantör](./writing-a-container-provider.md)

[Skriver en navigerings leverantör](./writing-a-navigation-provider.md)

[Översikt över Windows PowerShell-Provider](./windows-powershell-provider-overview.md)
