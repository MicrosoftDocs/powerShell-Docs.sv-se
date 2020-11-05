---
ms.date: 09/13/2016
ms.topic: reference
title: Skriva en navigeringsprovider
description: Skriva en navigeringsprovider
ms.openlocfilehash: 3123672d3365c97714557bd0e72a6e444ac228a0
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355229"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="3befb-103">Skriva en navigeringsprovider</span><span class="sxs-lookup"><span data-stu-id="3befb-103">Writing a navigation provider</span></span>

<span data-ttu-id="3befb-104">I det här avsnittet beskrivs hur du implementerar metoder för en Windows PowerShell-provider som stöder kapslade behållare (data lager på flera nivåer), flyttar objekt och relativa sökvägar.</span><span class="sxs-lookup"><span data-stu-id="3befb-104">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="3befb-105">En navigerings leverantör måste vara härledd från klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="3befb-105">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="3befb-106">Providern i exemplen i det här avsnittet använder en Access-databas som data lager.</span><span class="sxs-lookup"><span data-stu-id="3befb-106">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="3befb-107">Det finns flera hjälp metoder och klasser som används för att interagera med databasen.</span><span class="sxs-lookup"><span data-stu-id="3befb-107">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="3befb-108">Det fullständiga exemplet som innehåller hjälp metoder finns i [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="3befb-108">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="3befb-109">Mer information om Windows PowerShell-leverantörer finns i [Översikt över Windows PowerShell-Provider](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3befb-109">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="3befb-110">Implementera navigerings metoder</span><span class="sxs-lookup"><span data-stu-id="3befb-110">Implementing navigation methods</span></span>

<span data-ttu-id="3befb-111">Klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) implementerar metoder som stöder kapslade behållare, relativa sökvägar och flyttar objekt.</span><span class="sxs-lookup"><span data-stu-id="3befb-111">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="3befb-112">En fullständig lista över dessa metoder finns i [NavigationCmdletProvider-metoder](/dotnet/api/system.management.automation.provider.navigationcmdletprovider#methods).</span><span class="sxs-lookup"><span data-stu-id="3befb-112">For a complete list of these methods, see [NavigationCmdletProvider Methods](/dotnet/api/system.management.automation.provider.navigationcmdletprovider#methods).</span></span>

> [!NOTE]
> <span data-ttu-id="3befb-113">Det här avsnittet bygger på informationen i [snabb starten för Windows PowerShell-providern](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="3befb-113">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="3befb-114">Det här avsnittet beskriver inte grunderna för hur du konfigurerar ett Provider-projekt eller hur du implementerar de metoder som ärvts från klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) som skapar och tar bort enheter.</span><span class="sxs-lookup"><span data-stu-id="3befb-114">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="3befb-115">Det här avsnittet beskriver inte heller hur du implementerar metoder som exponeras av [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) eller [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -klasser.</span><span class="sxs-lookup"><span data-stu-id="3befb-115">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="3befb-116">Ett exempel som visar hur du implementerar objekt-cmdlets finns i [skriva en objekt leverantör](./writing-an-item-provider.md).</span><span class="sxs-lookup"><span data-stu-id="3befb-116">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="3befb-117">Ett exempel som visar hur du implementerar behållar-cmdlets finns i [skriva en container-Provider](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="3befb-117">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="3befb-118">Deklarera Provider-klassen</span><span class="sxs-lookup"><span data-stu-id="3befb-118">Declaring the provider class</span></span>

<span data-ttu-id="3befb-119">Deklarera providern som ska härledas från klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) och dekorera den med [system. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="3befb-119">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="3befb-120">Implementera IsItemContainer</span><span class="sxs-lookup"><span data-stu-id="3befb-120">Implementing IsItemContainer</span></span>

<span data-ttu-id="3befb-121">Metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) kontrollerar om objektet på den angivna sökvägen är en behållare.</span><span class="sxs-lookup"><span data-stu-id="3befb-121">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

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

### <a name="implementing-getchildname"></a><span data-ttu-id="3befb-122">Implementera GetChildName</span><span class="sxs-lookup"><span data-stu-id="3befb-122">Implementing GetChildName</span></span>

<span data-ttu-id="3befb-123">Metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) hämtar egenskapen Name för det underordnade objektet på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="3befb-123">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="3befb-124">Om objektet på den angivna sökvägen inte är underordnat en behållare ska den här metoden returnera sökvägen.</span><span class="sxs-lookup"><span data-stu-id="3befb-124">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

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

### <a name="implementing-getparentpath"></a><span data-ttu-id="3befb-125">Implementera GetParentPath</span><span class="sxs-lookup"><span data-stu-id="3befb-125">Implementing GetParentPath</span></span>

<span data-ttu-id="3befb-126">Metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) hämtar sökvägen till det överordnade objektet på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="3befb-126">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="3befb-127">Om objektet på den angivna sökvägen är roten för data lagret (så att den inte har någon överordnad) ska den här metoden returnera rot Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="3befb-127">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

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

### <a name="implementing-makepath"></a><span data-ttu-id="3befb-128">Implementera MakePath</span><span class="sxs-lookup"><span data-stu-id="3befb-128">Implementing MakePath</span></span>

<span data-ttu-id="3befb-129">Metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) ansluter till en angiven överordnad sökväg och en angiven underordnad sökväg för att skapa en provider-intern sökväg (mer information om Sök vägs typer som providers har stöd för finns i [Översikt över Windows PowerShell-providern](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3befb-129">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="3befb-130">PowerShell-motorn anropar den här metoden när en användare anropar cmdleten [Microsoft. PowerShell. commands. JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) .</span><span class="sxs-lookup"><span data-stu-id="3befb-130">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet.</span></span>

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

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="3befb-131">Implementera NormalizeRelativePath</span><span class="sxs-lookup"><span data-stu-id="3befb-131">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="3befb-132">Metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) tar `path` och `basepath` parametrar, och returnerar en normaliserad sökväg som motsvarar `path` parametern och i förhållande till `basepath` parametern.</span><span class="sxs-lookup"><span data-stu-id="3befb-132">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

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

### <a name="implementing-moveitem"></a><span data-ttu-id="3befb-133">Implementera MoveItem</span><span class="sxs-lookup"><span data-stu-id="3befb-133">Implementing MoveItem</span></span>

<span data-ttu-id="3befb-134">Metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) flyttar ett objekt från den angivna sökvägen till den angivna mål Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="3befb-134">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="3befb-135">PowerShell-motorn anropar den här metoden när en användare anropar cmdleten [Microsoft. PowerShell. commands. MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) .</span><span class="sxs-lookup"><span data-stu-id="3befb-135">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3befb-136">Se även</span><span class="sxs-lookup"><span data-stu-id="3befb-136">See Also</span></span>

[<span data-ttu-id="3befb-137">Skriva en containerprovider</span><span class="sxs-lookup"><span data-stu-id="3befb-137">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="3befb-138">Översikt över Windows PowerShell-providers</span><span class="sxs-lookup"><span data-stu-id="3befb-138">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
