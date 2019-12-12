---
title: GetProcessSample01-exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 00190c7350cb0f1cfc5c389b56e48e9397480446
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359315"
---
# <a name="getprocesssample01-sample"></a><span data-ttu-id="1521a-102">GetProcessSample01 – exempel</span><span class="sxs-lookup"><span data-stu-id="1521a-102">GetProcessSample01 Sample</span></span>

<span data-ttu-id="1521a-103">Det här exemplet visar hur du implementerar en cmdlet som hämtar processerna på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="1521a-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="1521a-104">Denna cmdlet är en förenklad version av `Get-Process`-cmdleten som tillhandahålls av Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="1521a-104">This cmdlet is a simplified version of the `Get-Process` cmdlet that is provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="1521a-105">Så här skapar du exemplet med hjälp av Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1521a-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="1521a-106">Med Windows PowerShell 2,0 SDK installerat navigerar du till mappen GetProcessSample01</span><span class="sxs-lookup"><span data-stu-id="1521a-106">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample01 folder.</span></span> <span data-ttu-id="1521a-107">Standard platsen är C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="1521a-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span></span>

2. <span data-ttu-id="1521a-108">Dubbelklicka på ikonen för lösnings filen (. SLN).</span><span class="sxs-lookup"><span data-stu-id="1521a-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="1521a-109">Detta öppnar exempelprojektet i Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1521a-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="1521a-110">I menyn **build** väljer du **build-lösning**.</span><span class="sxs-lookup"><span data-stu-id="1521a-110">In the **Build** menu, select **Build Solution**.</span></span>

  <span data-ttu-id="1521a-111">Biblioteket för exemplet skapas i standardmappen \Bin eller \Bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="1521a-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="1521a-112">Köra exemplet</span><span class="sxs-lookup"><span data-stu-id="1521a-112">How to run the sample</span></span>

1. <span data-ttu-id="1521a-113">Öppna Kommandotolken.</span><span class="sxs-lookup"><span data-stu-id="1521a-113">Open a Command Prompt window.</span></span>

2. <span data-ttu-id="1521a-114">Navigera till den katalog som innehåller Sample. dll-filen.</span><span class="sxs-lookup"><span data-stu-id="1521a-114">Navigate to the directory containing the sample .dll file.</span></span>

3. <span data-ttu-id="1521a-115">Kör InstallUtil "GetProcessSample01. dll".</span><span class="sxs-lookup"><span data-stu-id="1521a-115">Run installutil "GetProcessSample01.dll".</span></span>

4. <span data-ttu-id="1521a-116">Starta Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1521a-116">Start Windows PowerShell.</span></span>

5. <span data-ttu-id="1521a-117">Kör följande kommando för att lägga till snapin-modulen i gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="1521a-117">Run the following command to add the snap-in to the shell.</span></span>

   `Add-PSSnapin GetProcPSSnapIn01`

6. <span data-ttu-id="1521a-118">Ange följande kommando för att köra cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1521a-118">Enter the following command to run the cmdlet.</span></span> `get-proc`

   `get-proc`

   <span data-ttu-id="1521a-119">Detta är ett exempel på utdata som resulterar i följande steg.</span><span class="sxs-lookup"><span data-stu-id="1521a-119">This is a sample output that results from following these steps.</span></span>

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a><span data-ttu-id="1521a-120">Krav</span><span class="sxs-lookup"><span data-stu-id="1521a-120">Requirements</span></span>

<span data-ttu-id="1521a-121">Det här exemplet kräver Windows PowerShell 1,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="1521a-121">This sample requires Windows PowerShell 1.0 or later.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="1521a-122">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="1521a-122">Demonstrates</span></span>

<span data-ttu-id="1521a-123">Det här exemplet demonstrerar följande.</span><span class="sxs-lookup"><span data-stu-id="1521a-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="1521a-124">Skapar en grundläggande exempel-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1521a-124">Creating a basic sample cmdlet.</span></span>

- <span data-ttu-id="1521a-125">Definiera en cmdlet-klass med hjälp av cmdlet-attributet.</span><span class="sxs-lookup"><span data-stu-id="1521a-125">Defining a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="1521a-126">Skapa en snapin-modul som fungerar med både Windows PowerShell 1,0 och Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="1521a-126">Creating a snap-in that works with both Windows PowerShell 1.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="1521a-127">Efterföljande exempel använder moduler i stället för snapin-moduler så att de kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="1521a-127">Subsequent samples use modules instead of snap-ins so they require Windows PowerShell 2.0.</span></span>

## <a name="example"></a><span data-ttu-id="1521a-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="1521a-128">Example</span></span>

<span data-ttu-id="1521a-129">Det här exemplet visar hur du skapar en enkel cmdlet och dess snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="1521a-129">This sample shows how to create a simple cmdlet and its snap-in.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a><span data-ttu-id="1521a-130">Se även</span><span class="sxs-lookup"><span data-stu-id="1521a-130">See Also</span></span>

[<span data-ttu-id="1521a-131">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="1521a-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)