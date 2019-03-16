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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058205"
---
# <a name="writing-an-item-provider"></a><span data-ttu-id="06544-102">Skriva en objektprovider</span><span class="sxs-lookup"><span data-stu-id="06544-102">Writing an item provider</span></span>

<span data-ttu-id="06544-103">Det här avsnittet beskriver hur du implementerar-metoderna i en Windows PowerShell-providern som kommer åt och ändra objekt i datalagret.</span><span class="sxs-lookup"><span data-stu-id="06544-103">This topic describes how to implement the methods of a Windows PowerShell provider that access and manipulate items in the data store.</span></span> <span data-ttu-id="06544-104">Om du vill kunna komma åt objekt, en leverantör måste komma från den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klass.</span><span class="sxs-lookup"><span data-stu-id="06544-104">To be able to access items, a provider must derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

<span data-ttu-id="06544-105">Providern i exemplen i det här avsnittet använder en Access-databas som dess datalager.</span><span class="sxs-lookup"><span data-stu-id="06544-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="06544-106">Det finns flera hjälpmetoder och klasser som används för att interagera med databasen.</span><span class="sxs-lookup"><span data-stu-id="06544-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="06544-107">Hela exemplet som innehåller helper-metoder, se [AccessDBProviderSample03](./accessdbprovidersample03.md)</span><span class="sxs-lookup"><span data-stu-id="06544-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample03](./accessdbprovidersample03.md)</span></span>

<span data-ttu-id="06544-108">Mer information om Windows PowerShell-providrar finns i [Windows PowerShell-providern översikt](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="06544-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-item-methods"></a><span data-ttu-id="06544-109">Implementera objektet metoder</span><span class="sxs-lookup"><span data-stu-id="06544-109">Implementing item methods</span></span>

<span data-ttu-id="06544-110">Den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klassen visar flera metoder som kan användas för att komma åt och ändra objekt i ett datalager.</span><span class="sxs-lookup"><span data-stu-id="06544-110">The [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class exposes several methods that can be used to access and manipulate the items in a data store.</span></span> <span data-ttu-id="06544-111">En fullständig lista över dessa metoder, se [ItemCmdletProvider metoder](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx).</span><span class="sxs-lookup"><span data-stu-id="06544-111">For a complete list of these methods, see [ItemCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx).</span></span> <span data-ttu-id="06544-112">I det här exemplet implementerar vi fyra av dessa metoder.</span><span class="sxs-lookup"><span data-stu-id="06544-112">In this example, we will implement four of these methods.</span></span> <span data-ttu-id="06544-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) hämtar ett objekt på en angiven sökväg.</span><span class="sxs-lookup"><span data-stu-id="06544-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) gets an item at a specified path.</span></span> <span data-ttu-id="06544-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) anger värdet för det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="06544-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sets the value of the specified item.</span></span> <span data-ttu-id="06544-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) kontrollerar om det finns ett objekt i den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="06544-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) checks whether an item exists at the specified path.</span></span> <span data-ttu-id="06544-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) kontrollerar en sökväg för att se om det mappas till en plats i datalagret.</span><span class="sxs-lookup"><span data-stu-id="06544-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) checks a path to see if it maps to a location in the data store.</span></span>

> [!NOTE]
> <span data-ttu-id="06544-117">Det här avsnittet bygger på informationen i [Windows PowerShell-providern Snabbstart](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="06544-117">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="06544-118">Det här avsnittet beskriver inte grunderna för hur du ställer in ett provider-projekt eller hur du implementerar metoderna som ärvts från den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klass som skapar och tar bort enheter.</span><span class="sxs-lookup"><span data-stu-id="06544-118">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="06544-119">Fastställa providerklassen</span><span class="sxs-lookup"><span data-stu-id="06544-119">Declaring the provider class</span></span>

<span data-ttu-id="06544-120">Deklarera providern kan härledas från den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klassen och anpassa den med den [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="06544-120">Declare the provider to derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a><span data-ttu-id="06544-121">Implementera GetItem</span><span class="sxs-lookup"><span data-stu-id="06544-121">Implementing GetItem</span></span>

<span data-ttu-id="06544-122">Den [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) anropas av PowerShell-motorn när en användare anropar den [Microsoft.PowerShell.Commands.Get-Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdleten på din providern.</span><span class="sxs-lookup"><span data-stu-id="06544-122">The [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Get-Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet on your provider.</span></span> <span data-ttu-id="06544-123">Metoden returnerar objektet på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="06544-123">The method returns the item at the specified path.</span></span> <span data-ttu-id="06544-124">I exemplet Access database kontrollerar metoden om objektet är själva enheten, en tabell i databasen, eller en rad i databasen.</span><span class="sxs-lookup"><span data-stu-id="06544-124">In the Access database example, the method checks whether the item is the drive itself, a table in the database, or a row in the database.</span></span> <span data-ttu-id="06544-125">Metoden skickar objektet till PowerShell-motorn genom att anropa den [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) metod.</span><span class="sxs-lookup"><span data-stu-id="06544-125">The method sends the item to the PowerShell engine by calling the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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

### <a name="implementing-setitem"></a><span data-ttu-id="06544-126">Implementera SetItem</span><span class="sxs-lookup"><span data-stu-id="06544-126">Implementing SetItem</span></span>

<span data-ttu-id="06544-127">Den [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metoden anropas av PowerShell-motorn anrop när en användare anropar den [Microsoft.PowerShell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet .</span><span class="sxs-lookup"><span data-stu-id="06544-127">The [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method is called by the PowerShell engine calls when a user calls the [Microsoft.PowerShell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet.</span></span> <span data-ttu-id="06544-128">Anger värdet för objektet på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="06544-128">It sets the value of the item at the specified path.</span></span>

<span data-ttu-id="06544-129">I exemplet Access-databasen är det praktiskt att ange värdet för ett objekt bara om objektet är en rad, så att metoden utlöser [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) när objektet är inte en rad.</span><span class="sxs-lookup"><span data-stu-id="06544-129">In the Access database example, it makes sense to set the value of an item only if that item is a row, so the method throws [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) when the item is not a row.</span></span>

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

### <a name="implementing-itemexists"></a><span data-ttu-id="06544-130">Implementera ItemExists</span><span class="sxs-lookup"><span data-stu-id="06544-130">Implementing ItemExists</span></span>

<span data-ttu-id="06544-131">Den [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metoden anropas av PowerShell-motorn när en användare anropar den [Microsoft.PowerShell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="06544-131">The [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet.</span></span> <span data-ttu-id="06544-132">Metoden anger om det finns ett objekt på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="06544-132">The method determines whether there is an item at the specified path.</span></span> <span data-ttu-id="06544-133">Om objektet finns metoden skickar det tillbaka till PowerShell-motorn genom att anropa [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span><span class="sxs-lookup"><span data-stu-id="06544-133">If the item does exist, the method passes it back to the PowerShell engine by calling [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span></span>

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

### <a name="implementing-isvalidpath"></a><span data-ttu-id="06544-134">Implementera IsValidPath</span><span class="sxs-lookup"><span data-stu-id="06544-134">Implementing IsValidPath</span></span>

<span data-ttu-id="06544-135">Den [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metod för att kontrollera om den angivna sökvägen är syntaktiskt giltig för den aktuella providern.</span><span class="sxs-lookup"><span data-stu-id="06544-135">The [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method checks whether the specified path is syntactically valid for the current provider.</span></span> <span data-ttu-id="06544-136">Intune kontrollerar inte om det finns ett objekt i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="06544-136">It does not check whether an item exists at the path.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="06544-137">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="06544-137">Next steps</span></span>

<span data-ttu-id="06544-138">En typisk verkliga-provider kan ge stöd för objekt som innehåller andra objekt och för att flytta objekt från en sökväg till en annan i enheten.</span><span class="sxs-lookup"><span data-stu-id="06544-138">A typical real-world provider is capable of supporting items that contain other items, and of moving items from one path to another within the drive.</span></span> <span data-ttu-id="06544-139">Ett exempel på en provider som stöder behållare finns i [skriva en behållare provider](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="06544-139">For an example of a provider that supports containers, see [Writing a container provider](./writing-a-container-provider.md).</span></span> <span data-ttu-id="06544-140">Ett exempel på en provider som stöder flytta objekt, se [skriva en leverantör av navigering](./writing-a-navigation-provider.md).</span><span class="sxs-lookup"><span data-stu-id="06544-140">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="06544-141">Se även</span><span class="sxs-lookup"><span data-stu-id="06544-141">See Also</span></span>

[<span data-ttu-id="06544-142">Skriva en container-provider</span><span class="sxs-lookup"><span data-stu-id="06544-142">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="06544-143">Skriva en provider för navigering</span><span class="sxs-lookup"><span data-stu-id="06544-143">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="06544-144">Översikt för Windows PowerShell-providern</span><span class="sxs-lookup"><span data-stu-id="06544-144">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)