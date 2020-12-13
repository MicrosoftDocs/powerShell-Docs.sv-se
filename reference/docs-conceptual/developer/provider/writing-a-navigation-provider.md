---
ms.date: 09/13/2016
ms.topic: reference
title: Skriva en navigeringsprovider
description: Skriva en navigeringsprovider
ms.openlocfilehash: 3123672d3365c97714557bd0e72a6e444ac228a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355229"
---
# <a name="writing-a-navigation-provider"></a>Skriva en navigeringsprovider

I det här avsnittet beskrivs hur du implementerar metoder för en Windows PowerShell-provider som stöder kapslade behållare (data lager på flera nivåer), flyttar objekt och relativa sökvägar. En navigerings leverantör måste vara härledd från klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

Providern i exemplen i det här avsnittet använder en Access-databas som data lager. Det finns flera hjälp metoder och klasser som används för att interagera med databasen. Det fullständiga exemplet som innehåller hjälp metoder finns i [AccessDBProviderSample05](./accessdbprovidersample05.md).

Mer information om Windows PowerShell-leverantörer finns i [Översikt över Windows PowerShell-Provider](./windows-powershell-provider-overview.md).

## <a name="implementing-navigation-methods"></a>Implementera navigerings metoder

Klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) implementerar metoder som stöder kapslade behållare, relativa sökvägar och flyttar objekt. En fullständig lista över dessa metoder finns i [NavigationCmdletProvider-metoder](/dotnet/api/system.management.automation.provider.navigationcmdletprovider#methods).

> [!NOTE]
> Det här avsnittet bygger på informationen i [snabb starten för Windows PowerShell-providern](./windows-powershell-provider-quickstart.md). Det här avsnittet beskriver inte grunderna för hur du konfigurerar ett Provider-projekt eller hur du implementerar de metoder som ärvts från klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) som skapar och tar bort enheter. Det här avsnittet beskriver inte heller hur du implementerar metoder som exponeras av [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) eller [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -klasser. Ett exempel som visar hur du implementerar objekt-cmdlets finns i [skriva en objekt leverantör](./writing-an-item-provider.md). Ett exempel som visar hur du implementerar behållar-cmdlets finns i [skriva en container-Provider](./writing-a-container-provider.md).

### <a name="declaring-the-provider-class"></a>Deklarera Provider-klassen

Deklarera providern som ska härledas från klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) och dekorera den med [system. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a>Implementera IsItemContainer

Metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) kontrollerar om objektet på den angivna sökvägen är en behållare.

```csharp
protected override bool IsItemContainer(string path)
      {
         if (PathIsDrive(path))
         {
             return true;
         }

         string[] pathChunks = ChunkPath(path);
         string tableName;
         int rowNumber;

         PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

         if (type == PathType.Table)
         {
            foreach (DatabaseTableInfo ti in GetTables())
            {
                if (string.Equals(ti.Name, tableName, StringComparison.OrdinalIgnoreCase))
                {
                    return true;
                }
            } // foreach (DatabaseTableInfo...
         } // if (pathChunks...

         return false;
      }
```

### <a name="implementing-getchildname"></a>Implementera GetChildName

Metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) hämtar egenskapen Name för det underordnade objektet på den angivna sökvägen. Om objektet på den angivna sökvägen inte är underordnat en behållare ska den här metoden returnera sökvägen.

```csharp
protected override string GetChildName(string path)
       {
           if (PathIsDrive(path))
           {
               return path;
           }

           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               return tableName;
           }
           else if (type == PathType.Row)
           {
               return rowNumber.ToString(CultureInfo.CurrentCulture);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

           return null;
       }
```

### <a name="implementing-getparentpath"></a>Implementera GetParentPath

Metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Getparentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) hämtar sökvägen till det överordnade objektet på den angivna sökvägen. Om objektet på den angivna sökvägen är roten för data lagret (så att den inte har någon överordnad) ska den här metoden returnera rot Sök vägen.

```csharp
protected override string GetParentPath(string path, string root)
       {
           // If root is specified then the path has to contain
           // the root. If not nothing should be returned
           if (!String.IsNullOrEmpty(root))
           {
               if (!path.Contains(root))
               {
                   return null;
               }
           }

           return path.Substring(0, path.LastIndexOf(pathSeparator, StringComparison.OrdinalIgnoreCase));
       }
```

### <a name="implementing-makepath"></a>Implementera MakePath

Metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) ansluter till en angiven överordnad sökväg och en angiven underordnad sökväg för att skapa en provider-intern sökväg (mer information om Sök vägs typer som providers har stöd för finns i [Översikt över Windows PowerShell-providern](./windows-powershell-provider-overview.md). PowerShell-motorn anropar den här metoden när en användare anropar cmdleten [Microsoft. PowerShell. commands. JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) .

```csharp
protected override string MakePath(string parent, string child)
       {
           string result;

           string normalParent = NormalizePath(parent);
           normalParent = RemoveDriveFromPath(normalParent);
           string normalChild = NormalizePath(child);
           normalChild = RemoveDriveFromPath(normalChild);

           if (String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               result = String.Empty;
           }
           else if (String.IsNullOrEmpty(normalParent) && !String.IsNullOrEmpty(normalChild))
           {
               result = normalChild;
           }
           else if (!String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               if (normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent;
               }
               else
               {
                   result = normalParent + pathSeparator;
               }
           } // else if (!String...
           else
           {
               if (!normalParent.Equals(String.Empty) &&
                   !normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent + pathSeparator;
               }
               else
               {
                   result = normalParent;
               }

               if (normalChild.StartsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result += normalChild.Substring(1);
               }
               else
               {
                   result += normalChild;
               }
           } // else

           return result;
       }
```

### <a name="implementing-normalizerelativepath"></a>Implementera NormalizeRelativePath

Metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) tar `path` och `basepath` parametrar, och returnerar en normaliserad sökväg som motsvarar `path` parametern och i förhållande till `basepath` parametern.

```csharp
protected override string NormalizeRelativePath(string path,
                                                            string basepath)
       {
           // Normalize the paths first
           string normalPath = NormalizePath(path);
           normalPath = RemoveDriveFromPath(normalPath);
           string normalBasePath = NormalizePath(basepath);
           normalBasePath = RemoveDriveFromPath(normalBasePath);

           if (String.IsNullOrEmpty(normalBasePath))
           {
               return normalPath;
           }
           else
           {
               if (!normalPath.Contains(normalBasePath))
               {
                   return null;
               }

               return normalPath.Substring(normalBasePath.Length + pathSeparator.Length);
           }
       }
```

### <a name="implementing-moveitem"></a>Implementera MoveItem

Metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) flyttar ett objekt från den angivna sökvägen till den angivna mål Sök vägen. PowerShell-motorn anropar den här metoden när en användare anropar cmdleten [Microsoft. PowerShell. commands. MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) .

```csharp
protected override void MoveItem(string path, string destination)
       {
           // Get type, table name and rowNumber from the path
           string tableName, destTableName;
           int rowNumber, destRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           PathType destType = GetNamesFromPath(destination, out destTableName,
                                    out destRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (destType == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(destination);
           }

           if (type == PathType.Table)
           {
               ArgumentException e = new ArgumentException("Move not supported for tables");

               WriteError(new ErrorRecord(e, "MoveNotSupported",
                   ErrorCategory.InvalidArgument, path));

               throw e;
           }
           else
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               OdbcDataAdapter dda = GetAdapterForTable(destTableName);
               if (dda == null)
               {
                   return;
               }

               DataSet dds = GetDataSetForTable(dda, destTableName);
               DataTable destTable = GetDataTable(dds, destTableName);
               DataRow row = table.Rows[rowNumber];

               if (destType == PathType.Table)
               {
                   DataRow destRow = destTable.NewRow();

                   destRow.ItemArray = row.ItemArray;
               }
               else
               {
                   DataRow destRow = destTable.Rows[destRowNumber];

                   destRow.ItemArray = row.ItemArray;
               }

               // Update the changes
               if (ShouldProcess(path, "MoveItem"))
               {
                   WriteItemObject(row, path, false);
                   dda.Update(dds, destTableName);
               }
           }
       }
```

## <a name="see-also"></a>Se även

[Skriva en containerprovider](./writing-a-container-provider.md)

[Översikt över Windows PowerShell-providers](./windows-powershell-provider-overview.md)
