---
title: Så här skriver du en PowerShell-modul för binär | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357409"
---
# <a name="how-to-write-a-powershell-binary-module"></a>Skriva en binär PowerShell-modul

En binär modul kan vara vilken sammansättning som helst (. dll) som innehåller cmdlet-klasser. Som standard importeras alla cmdletar i sammansättningen när den binära modulen importeras. Du kan dock begränsa de cmdlet: ar som importeras genom att skapa ett modulens manifest vars rotnod är sammansättningen. (Till exempel kan Manifestets CmdletsToExport-nyckel endast användas för att exportera de cmdlets som behövs.) Dessutom kan en binär modul innehålla ytterligare filer, en katalog struktur och andra delar av användbar hanterings information som en enskild cmdlet inte kan.

Följande procedur beskriver hur du skapar och installerar en PowerShell-modul för binär.

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>Skapa och installera en PowerShell-modul för binär

1. Skapa en binär PowerShell-lösning (till exempel en cmdlet skriven C#i), med de funktioner du behöver och kontrol lera att den fungerar korrekt.

   I ett kod perspektiv är kärnan i en binär modul bara en cmdlet-sammansättning. I själva verket behandlar PowerShell en enda cmdlet-sammansättning som en modul, vad gäller inläsning och avlastning, utan extra ansträngning på den delen av utvecklaren. Mer information om hur du skriver en cmdlet finns i [skriva en Windows PowerShell-cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).

2. Om det behövs kan du skapa resten av lösningen: (ytterligare cmdlets, XML-filer och så vidare) och beskriv dem med ett modul manifest.

   Förutom att beskriva cmdlet-sammansättningarna i lösningen kan ett modul manifest beskriva hur du vill att modulen ska exporteras och importeras, vilka cmdlets som ska exponeras och vilka ytterligare filer som ska ingå i modulen.
   Som tidigare nämnts kan PowerShell behandla en binär cmdlet som en modul utan ytterligare arbete.
   Därför är ett modul manifest användbart för att kombinera flera filer till ett enda paket, eller för att explicit kontrol lera publikationen för en viss sammansättning.
   Mer information finns i [så här skriver du ett manifest för PowerShell-modul](how-to-write-a-powershell-module-manifest.md).

   Följande kod är ett mycket enkelt C# kodblock som innehåller tre cmdletar i samma fil som kan användas som en modul.

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. Paketera din lösning och spara paketet till någonstans i sökvägen till PowerShell-modulen.

   Den globala miljövariabeln `PSModulePath` beskriver standard Sök vägarna som PowerShell använder för att hitta modulen. Till exempel är en gemensam sökväg för att spara en modul på ett system `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`. Om du inte använder standard Sök vägarna måste du uttryckligen ange platsen för modulen under installationen. Se till att skapa en mapp för att spara modulen i, eftersom du kanske behöver mappen för att lagra flera sammansättningar och filer för din lösning.

   Observera att tekniskt sett du inte behöver installera modulen var som helst på `PSModulePath` – de är bara de standard platser som PowerShell söker efter din modul. Men det anses vara bästa praxis, om du inte har en bra anledning att lagra modulen någon annan stans. Mer information finns i [installera en PowerShell-modul](./installing-a-powershell-module.md) och [ändra installations Sök vägen för PowerShell-modulen](./modifying-the-psmodulepath-installation-path.md).

4. Importera modulen till PowerShell med ett anrop till [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).

   Genom att anropa [import-modulen](/powershell/module/Microsoft.PowerShell.Core/Import-Module) läses modulen in i aktivt minne. Om du använder PowerShell 3,0 och senare, behöver du bara anropa namnet på din modul i koden för att importera den. Mer information finns i [Importera en PowerShell-modul](./importing-a-powershell-module.md).

## <a name="importing-snap-in-assemblies-as-modules"></a>Importera snapin-sammansättningar som moduler

Cmdlets och providrar som finns i snapin-sammansättningar kan läsas in som binära moduler. När sammansättningarna för snapin-modulen läses in som binära moduler, är cmdletarna och providers i snapin-modulen tillgängliga för användaren, men snapin-klassen i sammansättningen ignoreras och snapin-modulen är inte registrerad. Därför kan snapin-cmdlet: arna som tillhandahålls av Windows PowerShell inte identifiera snapin-modulen även om de cmdlets och providers är tillgängliga för sessionen.

Dessutom går det inte att importera formaterings-och filfiler som snapin-modulen refererar till som en del av en binär modul.
För att importera format och typer av filer måste du skapa ett modul manifest.
Se [hur du skriver ett manifest för PowerShell-modul](how-to-write-a-powershell-module-manifest.md).

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-modul](./writing-a-windows-powershell-module.md)
