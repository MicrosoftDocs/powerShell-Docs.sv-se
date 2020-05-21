---
title: Skapa en arbets flödes aktivitet från en Windows PowerShell-cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4174e84f-d516-4aca-b418-273047dcfb07
caps.latest.revision: 7
ms.openlocfilehash: f45b5e985fa38ca4ff41707f1842ddb8b930e2b1
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557507"
---
# <a name="creating-a-workflow-activity-from-a-windows-powershell-cmdlet"></a>Skapa en arbetsflödesaktivitet från en Windows PowerShell-cmdlet

En Windows PowerShell-modul eller-cmdlet kan paketeras som en arbets flödes aktivitet med hjälp av metoderna i klassen [Microsoft. PowerShell. Activities. Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) . Använd [Microsoft. PowerShell. Activities. Activitygenerator. Generatefrommoduleinfo *](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromModuleInfo), [Microsoft. PowerShell. Activities. Activitygenerator. Generatefromcommandinfo *](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromCommandInfo)och [Microsoft. PowerShell. Activities. Activitygenerator. Generatefromname *](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromName) metoder i klassen [Microsoft. PowerShell. Activities. Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) för att generera C#-kod som representerar en aktivitet. Du kan sedan kompilera den resulterande C#-koden i en sammansättning som kan läggas till i ett projekt som en aktivitet.

Du kan sedan kompilera den resulterande C#-koden i en sammansättning som kan läggas till i ett projekt som en aktivitet genom att använda en kommando rad med följande formulär.

**CSC/nologo/out: AssemblyName/Target: Library/reference: system. Activities. Activity/reference: Microsoft. PowerShell. Activities codefile.cs**

## <a name="example"></a>Exempel

Följande exempel visar hur du genererar C#-kod för en aktivitet från en Windows PowerShell-modul.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using System.Management.Automation;
using System.Collections.ObjectModel;
using Microsoft.PowerShell.Activities;

namespace MakeActivity
{
    class Program
    {
        static void Main(string[] args)

        {
            StreamWriter CodeFile = new StreamWriter("c:\\\\testmodule\\codefile.cs");
            Collection<PSModuleInfo> ModuleInfos = new Collection<PSModuleInfo> { };
            PSModuleInfo ModuleInfo;
            string ActivityCode = "";
            string ModulePath = "";
            Console.Write("Type the full path and filename of the module to process:");
            ModulePath = Console.ReadLine();

            PowerShell ps = PowerShell.Create();

            ps.AddCommand("Import-Module").AddArgument(ModulePath);
            ps.AddParameter("PassThru");
            ModuleInfos = ps.Invoke<PSModuleInfo>();

            ModuleInfo = (PSModuleInfo)ModuleInfos[0];

            ActivityCode = ActivityGenerator.GenerateFromModuleInfo(ModuleInfo, "MyNamespace").First<String>();

           CodeFile.Write(ActivityCode);
            Console.ReadLine();

        }
    }
}

```

## <a name="example"></a>Exempel

Följande exempel visar hur du genererar C#-kod för en aktivitet från en Windows PowerShell-cmdlet.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using System.Management.Automation;
using System.Collections.ObjectModel;
using Microsoft.PowerShell.Activities;

namespace MakeActivity
{
    class Program
    {
        static void Main(string[] args)

        {
            StreamWriter CodeFile = new StreamWriter("c:\\\\testmodule\\codefile.cs");
            Collection<PSModuleInfo> ModuleInfos = new Collection<PSModuleInfo> { };
            PSModuleInfo ModuleInfo;
            Collection<CommandInfo> CommandInfos = new Collection<CommandInfo> { };
            CommandInfo MyCommand;
            string ActivityCode = "";
            string ModulePath = "";
            Console.Write("Type the full path and filename of the module to process:");
            ModulePath = Console.ReadLine();

            PowerShell ps = PowerShell.Create();

            ps.AddCommand("Import-Module").AddArgument(ModulePath);
            ps.AddParameter("PassThru");
            ModuleInfos = ps.Invoke<PSModuleInfo>();

            ModuleInfo = (PSModuleInfo)ModuleInfos[0];

            ps.AddCommand("Get-Command").AddArgument(ModuleInfo);
            CommandInfos = ps.Invoke<CommandInfo>();

            MyCommand = CommandInfos[0];

            ActivityCode = ActivityGenerator.GenerateFromCommandInfo(MyCommand, "MyNamespace");

           CodeFile.Write(ActivityCode);
            Console.ReadLine();

        }
    }
}

```
