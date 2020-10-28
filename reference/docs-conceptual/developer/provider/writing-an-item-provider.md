---
ms.date: 09/13/2016
ms.topic: reference
title: Skriva en objektprovider
description: Skriva en objektprovider
ms.openlocfilehash: ca25809178a4b812cff8b46ea456702d142f6fd6
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647209"
---
# <a name="writing-an-item-provider"></a><span data-ttu-id="c09a3-103">Skriva en objektprovider</span><span class="sxs-lookup"><span data-stu-id="c09a3-103">Writing an item provider</span></span>

<span data-ttu-id="c09a3-104">I det här avsnittet beskrivs hur du implementerar metoder för en Windows PowerShell-provider som har åtkomst till och hanterar objekt i data lagret.</span><span class="sxs-lookup"><span data-stu-id="c09a3-104">This topic describes how to implement the methods of a Windows PowerShell provider that access and manipulate items in the data store.</span></span> <span data-ttu-id="c09a3-105">För att kunna komma åt objekt måste en provider härledas från klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="c09a3-105">To be able to access items, a provider must derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

<span data-ttu-id="c09a3-106">Providern i exemplen i det här avsnittet använder en Access-databas som data lager.</span><span class="sxs-lookup"><span data-stu-id="c09a3-106">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="c09a3-107">Det finns flera hjälp metoder och klasser som används för att interagera med databasen.</span><span class="sxs-lookup"><span data-stu-id="c09a3-107">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="c09a3-108">Det fullständiga exemplet som innehåller hjälp metoder finns i [AccessDBProviderSample03](./accessdbprovidersample03.md)</span><span class="sxs-lookup"><span data-stu-id="c09a3-108">For the complete sample that includes the helper methods, see [AccessDBProviderSample03](./accessdbprovidersample03.md)</span></span>

<span data-ttu-id="c09a3-109">Mer information om Windows PowerShell-leverantörer finns i [Översikt över Windows PowerShell-Provider](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c09a3-109">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-item-methods"></a><span data-ttu-id="c09a3-110">Implementera objekt metoder</span><span class="sxs-lookup"><span data-stu-id="c09a3-110">Implementing item methods</span></span>

<span data-ttu-id="c09a3-111">Klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) visar flera metoder som kan användas för att få åtkomst till och manipulera objekt i ett data lager.</span><span class="sxs-lookup"><span data-stu-id="c09a3-111">The [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class exposes several methods that can be used to access and manipulate the items in a data store.</span></span> <span data-ttu-id="c09a3-112">En fullständig lista över dessa metoder finns i [ItemCmdletProvider-metoder](/dotnet/api/system.management.automation.provider.itemcmdletprovider?view=pscore-6.2.0#methods).</span><span class="sxs-lookup"><span data-stu-id="c09a3-112">For a complete list of these methods, see [ItemCmdletProvider Methods](/dotnet/api/system.management.automation.provider.itemcmdletprovider?view=pscore-6.2.0#methods).</span></span> <span data-ttu-id="c09a3-113">I det här exemplet ska vi implementera fyra av dessa metoder.</span><span class="sxs-lookup"><span data-stu-id="c09a3-113">In this example, we will implement four of these methods.</span></span> <span data-ttu-id="c09a3-114">[System. Management. Automation. Provider. Itemcmdletprovider. getItem, \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) hämtar ett objekt vid en angiven sökväg.</span><span class="sxs-lookup"><span data-stu-id="c09a3-114">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) gets an item at a specified path.</span></span> <span data-ttu-id="c09a3-115">[System. Management. Automation. Provider. Itemcmdletprovider. setItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) anger värdet för det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="c09a3-115">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sets the value of the specified item.</span></span> <span data-ttu-id="c09a3-116">[System. Management. Automation. Provider. Itemcmdletprovider. Itemexists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) kontrollerar om ett objekt finns på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="c09a3-116">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) checks whether an item exists at the specified path.</span></span> <span data-ttu-id="c09a3-117">[System. Management. Automation. Provider. Itemcmdletprovider. Isvalidpath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) kontrollerar en sökväg för att se om den mappas till en plats i data lagret.</span><span class="sxs-lookup"><span data-stu-id="c09a3-117">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) checks a path to see if it maps to a location in the data store.</span></span>

> [!NOTE]
> <span data-ttu-id="c09a3-118">Det här avsnittet bygger på informationen i [snabb starten för Windows PowerShell-providern](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="c09a3-118">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="c09a3-119">Det här avsnittet beskriver inte grunderna för hur du konfigurerar ett Provider-projekt eller hur du implementerar de metoder som ärvts från klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) som skapar och tar bort enheter.</span><span class="sxs-lookup"><span data-stu-id="c09a3-119">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="c09a3-120">Deklarera Provider-klassen</span><span class="sxs-lookup"><span data-stu-id="c09a3-120">Declaring the provider class</span></span>

<span data-ttu-id="c09a3-121">Deklarera providern som ska härledas från klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) och dekorera den med [system. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="c09a3-121">Declare the provider to derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a><span data-ttu-id="c09a3-122">Implementera getItem,</span><span class="sxs-lookup"><span data-stu-id="c09a3-122">Implementing GetItem</span></span>

<span data-ttu-id="c09a3-123">[System. Management. Automation. Provider. Itemcmdletprovider. getItem, \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) anropas av PowerShell-motorn när en användare anropar cmdleten [Microsoft. PowerShell. commands. GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) på din Provider.</span><span class="sxs-lookup"><span data-stu-id="c09a3-123">The [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) cmdlet on your provider.</span></span> <span data-ttu-id="c09a3-124">Metoden returnerar objektet på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="c09a3-124">The method returns the item at the specified path.</span></span> <span data-ttu-id="c09a3-125">I Access Database-exemplet kontrollerar metoden om objektet är själva enheten, en tabell i databasen eller en rad i databasen.</span><span class="sxs-lookup"><span data-stu-id="c09a3-125">In the Access database example, the method checks whether the item is the drive itself, a table in the database, or a row in the database.</span></span> <span data-ttu-id="c09a3-126">Metoden skickar objektet till PowerShell-motorn genom att anropa metoden [system. Management. Automation. Provider. Cmdletprovider. Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) .</span><span class="sxs-lookup"><span data-stu-id="c09a3-126">The method sends the item to the PowerShell engine by calling the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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

### <a name="implementing-setitem"></a><span data-ttu-id="c09a3-127">Implementera SetItem</span><span class="sxs-lookup"><span data-stu-id="c09a3-127">Implementing SetItem</span></span>

<span data-ttu-id="c09a3-128">Metoden [system. Management. Automation. Provider. Itemcmdletprovider. setItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) anropas av PowerShell-motorn anrop när en användare anropar cmdleten [Microsoft. PowerShell. commands. SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) .</span><span class="sxs-lookup"><span data-stu-id="c09a3-128">The [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method is called by the PowerShell engine calls when a user calls the [Microsoft.PowerShell.Commands.SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) cmdlet.</span></span> <span data-ttu-id="c09a3-129">Värdet för objektet anges på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="c09a3-129">It sets the value of the item at the specified path.</span></span>

<span data-ttu-id="c09a3-130">I Access Database-exemplet är det klokt att ange värdet för ett objekt endast om objektet är en rad, så att metoden returnerar [NotSupportedException](/dotnet/api/system.notsupportedexception?view=netframework-4.8) när objektet inte är en rad.</span><span class="sxs-lookup"><span data-stu-id="c09a3-130">In the Access database example, it makes sense to set the value of an item only if that item is a row, so the method throws [NotSupportedException](/dotnet/api/system.notsupportedexception?view=netframework-4.8) when the item is not a row.</span></span>

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

### <a name="implementing-itemexists"></a><span data-ttu-id="c09a3-131">Implementera ItemExists</span><span class="sxs-lookup"><span data-stu-id="c09a3-131">Implementing ItemExists</span></span>

<span data-ttu-id="c09a3-132">Metoden [system. Management. Automation. Provider. Itemcmdletprovider. Itemexists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) anropas av PowerShell-motorn när en användare anropar cmdleten [Microsoft. PowerShell. commands. TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) .</span><span class="sxs-lookup"><span data-stu-id="c09a3-132">The [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) cmdlet.</span></span> <span data-ttu-id="c09a3-133">Metoden avgör om det finns ett objekt på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="c09a3-133">The method determines whether there is an item at the specified path.</span></span> <span data-ttu-id="c09a3-134">Om objektet finns skickar metoden tillbaka den till PowerShell-motorn genom att anropa [system. Management. Automation. Provider. Cmdletprovider. Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span><span class="sxs-lookup"><span data-stu-id="c09a3-134">If the item does exist, the method passes it back to the PowerShell engine by calling [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span></span>

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

### <a name="implementing-isvalidpath"></a><span data-ttu-id="c09a3-135">Implementera IsValidPath</span><span class="sxs-lookup"><span data-stu-id="c09a3-135">Implementing IsValidPath</span></span>

<span data-ttu-id="c09a3-136">Metoden [system. Management. Automation. Provider. Itemcmdletprovider. Isvalidpath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) kontrollerar om den angivna sökvägen är syntaktiskt giltig för den aktuella providern.</span><span class="sxs-lookup"><span data-stu-id="c09a3-136">The [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method checks whether the specified path is syntactically valid for the current provider.</span></span> <span data-ttu-id="c09a3-137">Den kontrollerar inte om ett objekt finns på sökvägen.</span><span class="sxs-lookup"><span data-stu-id="c09a3-137">It does not check whether an item exists at the path.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="c09a3-138">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="c09a3-138">Next steps</span></span>

<span data-ttu-id="c09a3-139">En typisk verklig Provider kan stödja objekt som innehåller andra objekt och för att flytta objekt från en sökväg till en annan i enheten.</span><span class="sxs-lookup"><span data-stu-id="c09a3-139">A typical real-world provider is capable of supporting items that contain other items, and of moving items from one path to another within the drive.</span></span> <span data-ttu-id="c09a3-140">Ett exempel på en provider som stöder behållare finns i [skriva en container-Provider](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="c09a3-140">For an example of a provider that supports containers, see [Writing a container provider](./writing-a-container-provider.md).</span></span> <span data-ttu-id="c09a3-141">Ett exempel på en provider som stöder flytta objekt finns i [skriva en navigerings leverantör](./writing-a-navigation-provider.md).</span><span class="sxs-lookup"><span data-stu-id="c09a3-141">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c09a3-142">Se även</span><span class="sxs-lookup"><span data-stu-id="c09a3-142">See Also</span></span>

[<span data-ttu-id="c09a3-143">Skriva en containerprovider</span><span class="sxs-lookup"><span data-stu-id="c09a3-143">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="c09a3-144">Skriva en navigeringsprovider</span><span class="sxs-lookup"><span data-stu-id="c09a3-144">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="c09a3-145">Översikt över Windows PowerShell-providers</span><span class="sxs-lookup"><span data-stu-id="c09a3-145">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
