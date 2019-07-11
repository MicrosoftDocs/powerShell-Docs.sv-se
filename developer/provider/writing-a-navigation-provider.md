---
title: Skriva en navigering-provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98bcfda0-6ee2-46f5-bbc7-5fab8b780d6a
caps.latest.revision: 5
ms.openlocfilehash: edb4d9944a527391983e068ddf07f4fac415c3f9
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734728"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="ecd2f-102">Skriva en navigeringsprovider</span><span class="sxs-lookup"><span data-stu-id="ecd2f-102">Writing a navigation provider</span></span>

<span data-ttu-id="ecd2f-103">Det här avsnittet beskriver hur du implementerar metoderna i en Windows PowerShell-providern som har stöd för kapslade behållare (med flera nivåer datalager), flytta objekt och relativa sökvägar.</span><span class="sxs-lookup"><span data-stu-id="ecd2f-103">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="ecd2f-104">En provider för navigering måste komma från den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klass.</span><span class="sxs-lookup"><span data-stu-id="ecd2f-104">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="ecd2f-105">Providern i exemplen i det här avsnittet använder en Access-databas som dess datalager.</span><span class="sxs-lookup"><span data-stu-id="ecd2f-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="ecd2f-106">Det finns flera hjälpmetoder och klasser som används för att interagera med databasen.</span><span class="sxs-lookup"><span data-stu-id="ecd2f-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="ecd2f-107">Hela exemplet som innehåller helper-metoder, se [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="ecd2f-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="ecd2f-108">Mer information om Windows PowerShell-providrar finns i [Windows PowerShell-providern översikt](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ecd2f-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="ecd2f-109">Implementera navigeringsmetoderna</span><span class="sxs-lookup"><span data-stu-id="ecd2f-109">Implementing navigation methods</span></span>

<span data-ttu-id="ecd2f-110">Den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klassen implementerar metoderna som stöder kapslade behållare, relativa sökvägar och flytta objekt.</span><span class="sxs-lookup"><span data-stu-id="ecd2f-110">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="ecd2f-111">En fullständig lista över dessa metoder, se [NavigationCmdletProvider metoder](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).</span><span class="sxs-lookup"><span data-stu-id="ecd2f-111">For a complete list of these methods, see [NavigationCmdletProvider Methods](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).</span></span>

> [!NOTE]
> <span data-ttu-id="ecd2f-112">Det här avsnittet bygger på informationen i [Windows PowerShell-providern Snabbstart](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="ecd2f-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="ecd2f-113">Det här avsnittet beskriver inte grunderna för hur du ställer in ett provider-projekt eller hur du implementerar metoderna som ärvts från den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klass som skapar och tar bort enheter.</span><span class="sxs-lookup"><span data-stu-id="ecd2f-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="ecd2f-114">Det här avsnittet beskriver också inte hur du implementerar metoderna som exponeras av den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) eller [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasser.</span><span class="sxs-lookup"><span data-stu-id="ecd2f-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="ecd2f-115">Ett exempel som visar hur du implementerar artikel-cmdletar finns i [skriva en provider med objektet](./writing-an-item-provider.md).</span><span class="sxs-lookup"><span data-stu-id="ecd2f-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="ecd2f-116">Ett exempel som visar hur du implementerar container-cmdletar finns i [skriva en behållare provider](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="ecd2f-116">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="ecd2f-117">Fastställa providerklassen</span><span class="sxs-lookup"><span data-stu-id="ecd2f-117">Declaring the provider class</span></span>

<span data-ttu-id="ecd2f-118">Deklarera providern kan härledas från den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klassen och anpassa den med den [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="ecd2f-118">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="ecd2f-119">Implementera IsItemContainer</span><span class="sxs-lookup"><span data-stu-id="ecd2f-119">Implementing IsItemContainer</span></span>

<span data-ttu-id="ecd2f-120">Den [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) metod för att kontrollera om objektet på den angivna sökvägen är en behållare.</span><span class="sxs-lookup"><span data-stu-id="ecd2f-120">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

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

### <a name="implementing-getchildname"></a><span data-ttu-id="ecd2f-121">Implementera GetChildName</span><span class="sxs-lookup"><span data-stu-id="ecd2f-121">Implementing GetChildName</span></span>

<span data-ttu-id="ecd2f-122">Den [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) metoden hämtar namnegenskapen för det underordnade objektet på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="ecd2f-122">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="ecd2f-123">Om objektet på den angivna sökvägen inte är en underordnad till en behållare, bör den här metoden returnerar sökvägen.</span><span class="sxs-lookup"><span data-stu-id="ecd2f-123">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

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

### <a name="implementing-getparentpath"></a><span data-ttu-id="ecd2f-124">Implementera GetParentPath</span><span class="sxs-lookup"><span data-stu-id="ecd2f-124">Implementing GetParentPath</span></span>

<span data-ttu-id="ecd2f-125">Den [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) metoden hämtar sökvägen till överordnat objektet på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="ecd2f-125">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="ecd2f-126">Om objektet på den angivna sökvägen är roten till datalagret (så att den har ingen överordnad), bör den här metoden returnerar rotsökvägen.</span><span class="sxs-lookup"><span data-stu-id="ecd2f-126">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

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

### <a name="implementing-makepath"></a><span data-ttu-id="ecd2f-127">Implementing MakePath</span><span class="sxs-lookup"><span data-stu-id="ecd2f-127">Implementing MakePath</span></span>

<span data-ttu-id="ecd2f-128">Den [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metoden kopplar en angivna överordnade och sökvägen till en angivna underordnade att skapa en provider-internt sökväg (för information om sökvägen typer som leverantörer kan stödja, se [Windows PowerShell-providern översikt](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ecd2f-128">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="ecd2f-129">PowerShell-motorn anropar den här metoden när en användare anropar den [Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ecd2f-129">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet.</span></span>

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

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="ecd2f-130">Implementera NormalizeRelativePath</span><span class="sxs-lookup"><span data-stu-id="ecd2f-130">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="ecd2f-131">Den [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) metoden tar `path` och `basepath` parametrar, och returnerar en normaliserad sökväg som motsvarar `path`parametern och i förhållande till den `basepath` parametern.</span><span class="sxs-lookup"><span data-stu-id="ecd2f-131">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

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

### <a name="implementing-moveitem"></a><span data-ttu-id="ecd2f-132">Implementera MoveItem</span><span class="sxs-lookup"><span data-stu-id="ecd2f-132">Implementing MoveItem</span></span>

<span data-ttu-id="ecd2f-133">Den [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) metoden flyttar ett objekt från den angivna sökvägen till den angivna målsökvägen.</span><span class="sxs-lookup"><span data-stu-id="ecd2f-133">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="ecd2f-134">PowerShell-motorn anropar den här metoden när en användare anropar den [Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ecd2f-134">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ecd2f-135">Se även</span><span class="sxs-lookup"><span data-stu-id="ecd2f-135">See Also</span></span>

[<span data-ttu-id="ecd2f-136">Skriva en container-provider</span><span class="sxs-lookup"><span data-stu-id="ecd2f-136">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="ecd2f-137">Översikt för Windows PowerShell-providern</span><span class="sxs-lookup"><span data-stu-id="ecd2f-137">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)