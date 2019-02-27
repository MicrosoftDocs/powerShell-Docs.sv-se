---
title: Hur du skriver en binär PowerShell-modulen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: 9ddb3bc172c66314603d2be4df5192a76c92e05d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847154"
---
# <a name="how-to-write-a-powershell-binary-module"></a>Skriva en binär PowerShell-modul

En binär modul kan vara valfri sammansättning (.dll) som innehåller cmdlet klasser. Som standard importeras alla cmdletar i sammansättningen när binär modulen har importerats. Du kan dock begränsa de cmdletar som har importerats genom att skapa ett modulmanifest vars rot-modulen är sammansättningen. (Till exempel nyckeln CmdletsToExport i manifestet kan användas för att exportera dessa cmdlets som krävs.) Dessutom kan kan en binär modul innehålla ytterligare filer, en katalogstruktur och andra delar av användbar information om att en enda cmdlet kan inte.

Följande procedur beskriver hur du skapar och installerar en binär PowerShell-modulen.

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>Hur du skapar och installerar en binär PowerShell-modulen

1. Skapa en binär PowerShell-lösning (till exempel en cmdlet som skrivits i C#), med funktionerna du behöver och se till att den körs korrekt.

   Från en kod perspektiv är kärnan i en binär modul helt enkelt en cmdlet-sammansättning. I själva verket behandlar PowerShell en enda cmdlet-sammansättning som en modul, när det gäller och avlastning med inget extra arbete för utvecklaren. Läs mer om hur du skriver en cmdlet, [skriva en Windows PowerShell-Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).

2. Om det behövs skapar du resten av din lösning: (fler cmdlet: ar, XML-filer och så vidare) och beskriver dem med ett modulmanifest.

   Förutom som beskriver cmdlet-sammansättningar i din lösning, beskrivs ett modulmanifest hur du vill att din modul exporteras och importeras, vilka cmdletar visas och vilka ytterligare filer hamnar i modulen. Som nämnts tidigare men kan PowerShell behandla en binär cmdlet som en modul med inget extra arbete. Ett modulmanifest är därför användbart främst för att kombinera flera filer till ett enda paket eller uttryckligen styra publicering för en angiven sammansättning. Mer information finns i [hur du skriver en PowerShell-modulen Manifest](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).

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

3. Paketera din lösning och spara paketet på en plats i PowerShell-modulens sökväg.

   Den `PSModulePath` globala miljövariabeln beskriver standardsökvägarna som PowerShell använder för att leta upp din modul. Till exempel en sökväg till att spara en modul i ett system är `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`. Om du inte använder standardsökvägarna behöver att uttryckligen ange platsen för din modul under installationen. Var noga med att skapa en mapp för att spara din modul, som du kan behöva mappen för att lagra flera sammansättningar och filer för din lösning.

   Observera att tekniskt du inte behöver installera modulens var som helst på den `PSModulePath` – de är helt enkelt standardplatserna som PowerShell söker efter din modul. Dock anses det bäst att göra det, såvida du inte har en bra anledning för att lagra modulens någon annanstans. Mer information finns i [installerar ett PowerShell-modulen](./installing-a-powershell-module.md) och [ändra installationssökvägen för PowerShell-modulen](./modifying-the-psmodulepath-installation-path.md).

4. Importera din modul till PowerShell med ett anrop till [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).

   Anrop till [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) ska läsa in din modul i active minnet. Om du använder PowerShell 3.0 och senare kan bara anropa namnet på din modul i kod också importeras. Mer information finns i [importera en PowerShell-modul](./importing-a-powershell-module.md).

## <a name="importing-snap-in-assemblies-as-modules"></a>Importera snapin-modulen sammansättningar som moduler

Cmdlets och providers som finns i snapin-modulen sammansättningar kan läsas som binära moduler. När snapin-modulen-sammansättningar läses som binära moduler, cmdlets och providers i snapin-modulen är tillgängliga för användare, men snapin-modulen-klassen i sammansättningen ignoreras och snapin-modulen är inte registrerad. Därför kan inte snapin-cmdletar som tillhandahålls av Windows PowerShell identifiera snapin-modulen även om cmdlets och providers är tillgängliga för sessionen.

Dessutom kan inte importeras alla filer för formatering eller typer som refereras av snapin-modulen som en del av en binär modul. Om du vill importera filerna formatering och typer måste du skapa ett modulmanifest. Se, [hur du skriver ett PowerShell-modulen Manifest](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).

## <a name="see-also"></a>Se även

[Skriva ett Windows PowerShell-modul](./writing-a-windows-powershell-module.md)
