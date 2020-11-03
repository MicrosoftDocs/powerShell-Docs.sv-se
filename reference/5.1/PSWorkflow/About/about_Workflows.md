---
description: Innehåller en kort introduktion till PowerShell Workflow-funktionen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_workflows?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Workflows
ms.openlocfilehash: fbd8ee62b1e9c6969d489c5024c33f5cca883dc6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270909"
---
# <a name="about-workflows"></a>Om arbets flöden

## <a name="short-description"></a>Kort beskrivning

Innehåller en kort introduktion till PowerShell Workflow-funktionen.

## <a name="long-description"></a>Lång beskrivning

PowerShell-arbetsflöde ger fördelarna med [Windows Workflow Foundation](/dotnet/framework/windows-workflow-foundation) till PowerShell och gör det möjligt att skriva och köra arbets flöden.

PowerShell-arbetsflöde introducerades i PowerShell 3,0 och modulen är tillgänglig upp till PowerShell 5,1. Mer information om PowerShell-arbetsflöde finns i arbets flödes [guiden](/previous-versions/powershell/scripting/components/workflows-guide) och [skriva ett Windows PowerShell-arbetsflöde](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow).

## <a name="about-workflows"></a>Om arbets flöden

Arbets flöden är kommandon som består av en ordnad sekvens av relaterade aktiviteter. De körs vanligt vis under en längre tid och samlar in data från och gör ändringar i hundratals datorer, ofta i heterogena miljöer.

Arbets flöden kan skrivas i XAML, språket som används i Windows Workflow Foundation eller på PowerShell-språket. Arbets flöden paketeras vanligt vis i moduler och innehåller hjälp ämnen. Mer information finns i [Översikt över XAML (WPF)](/dotnet/framework/wpf/advanced/xaml-overview-wpf).

Arbets flöden är viktiga i en IT-miljö eftersom de kan överleva omstarter och automatiskt återställas från vanliga fel. Du kan koppla från och återansluta från sessioner och datorer som kör arbets flöden utan att avbryta arbets flödes bearbetningen och pausa och återuppta arbets flöden transparent utan data förlust. Varje aktivitet i ett arbets flöde kan loggas och granskas för referens.
Arbets flöden kan köras som jobb och kan schemaläggas med hjälp av funktionen schemalagda uppgifter i PowerShell.

Tillstånd och data i ett arbets flöde sparas eller sparas i början och i slutet av arbets flödet och vid de punkter som du anger. Beständighets punkter i arbets flödet fungerar som databas ögonblicks bilder eller program kontroll punkter för att skydda arbets flödet från effekterna av avbrott och haverier. Om arbets flödet inte kan återställas efter ett fel kan du använda de sparade data och återuppta från den senaste beständiga punkten, i stället för att köra om ett omfattande arbets flöde från början.

## <a name="workflow-requirements-and-configuration"></a>Arbets flödes krav och konfiguration

En PowerShell Workflow-konfiguration består av följande element:

- En klient dator som kör arbets flödet.
- En arbets flödes session, **PSSession** , på klient datorn eller en fjärrdator.
- Hanterade noder, de mål datorer som påverkas av arbets flödes aktiviteterna.

Arbets flödes sessionen krävs inte, men rekommenderas. **PSSessions** kan dra nytta av funktionerna för robust återställning och frånkopplade sessioner i PowerShell för att återställa frånkopplade arbets flödes sessioner. Mer information finns i [about_Remote_Disconnected_Sessions](../../Microsoft.PowerShell.Core/About/about_Remote_Disconnected_Sessions.md)

Eftersom klient datorn och datorn där arbets flödes sessionen körs kan hanterade noder, kan du köra ett arbets flöde på en dator som uppfyller alla roller.

Klient datorn och datorn där arbets flödes sessionen körs måste köra PowerShell 3,0. Alla berättigade system stöds, inklusive alternativ för Server Core-installation av Windows Server-operativsystem.

För att köra arbets flöden som innehåller cmdlets måste de hanterade noderna ha Windows PowerShell 2,0 eller senare. Hanterade noder kräver inte PowerShell om inte arbets flödet innehåller cmdletar. Du kan köra arbets flöden som inkluderar Windows Management Instrumentation (WMI) och Common Information Model (CIM) kommandon på datorer som inte har PowerShell.

## <a name="how-to-get-workflows"></a>Så här hämtar du arbets flöden

Arbets flöden paketeras vanligt vis i moduler. Om du vill importera modulen som innehåller ett arbets flöde, använder du valfritt kommando i modulen eller använder `Import-Module` cmdleten.
Moduler importeras automatiskt vid första användningen av ett kommando i modulen.

Om du vill hitta arbets flöden i moduler som är installerade på datorn använder du `Get-Command` cmdlet: en **CommandType** -parameter.

```powershell
Get-Command -CommandType Workflow
```

## <a name="how-to-run-workflows"></a>Så här kör du arbets flöden

Använd följande procedur om du vill köra ett arbets flöde.

1. Det här steget krävs inte när den hanterade noden är den lokala datorn.
   Annars startar du PowerShell med alternativet **Kör som administratör** på klient datorn.

   ```powershell
   Start-Process PowerShell -Verb RunAs
   ```

1. Aktivera PowerShell-fjärrkommunikation på datorn som kör arbets flödes sessionen och på hanterade noder som påverkas av arbets flöden som innehåller cmdletar.

   Du behöver bara göra det här steget en gång på varje deltagande dator.

   Det här steget krävs bara när du kör arbets flöden som innehåller cmdletar. Du behöver inte aktivera fjärr kommunikation på klient datorn, om inte arbets flödes sessionen körs på klient datorn eller på några hanterade noder som kör PowerShell 3,0.

   Använd cmdleten om du vill aktivera fjärr kommunikation `Enable-PSRemoting` .

   ```powershell
   Enable-PSRemoting -Force
   ```

   Du kan aktivera fjärr kommunikation med hjälp av inställningen **Aktivera körning av skript** Grupprincip. Mer information finns i [about_Group_Policy_Settings](../../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md) och [about_Execution_Policies](../../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).

1. Använd `New-PSWorkflowSession` `New-PSSession` cmdletarna eller för att skapa arbets flödes sessionen.

   `New-PSWorkflowSession`Cmdleten startar en session som använder den inbyggda konfigurationen av **Microsoft. PowerShell. Workflow** -sessionen på mål datorn. I den här konfigurationen ingår skript, typ och formatering av filer samt alternativ som är utformade för arbets flöden.

   Du kan också använda `New-PSSession` cmdleten. Använd parametern **ConfigurationName** för att ange konfigurationen för **Microsoft. PowerShell. Workflow** -sessionen. Det här kommandot är detsamma som att använda- `New-PSWorkflowSession` cmdleten.

   Ett alternativ är att använda `New-PSSession` cmdleten. Använd parametern **ConfigurationName** för att ange konfigurationen för **Microsoft. PowerShell. Workflow** -sessionen.

   På den lokala datorn:

   ```powershell
   $ws = New-PSWorkflowSession
   ```

   På en fjärrdator:

   ```powershell
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

   Om du är administratör på arbets flödes sessionen kan du använda `New-PSWorkflowExecutionOption` cmdleten för att skapa anpassade alternativ inställningar för konfigurationen av arbets flödets session. Och Använd `Set-PSSessionConfiguration` cmdleten för att ändra konfigurationen för sessionen.

   ```powershell
   $sto = New-PSWorkflowExecutionOption -MaxConnectedSessions 150
   Invoke-Command -ComputerName Server01 `
   {Set-PSSessionConfiguration Microsoft.PowerShell.Workflow `
   -SessionTypeOption $Using:sto}
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

1. Kör arbets flödet i arbets flödes sessionen. Om du vill ange namnen på de hanterade noderna, mål datorerna använder du **PSComputerName** arbets flödets gemensamma parameter.

   Följande exempel kör arbets flödet med namnet **test-Workflow**.

   Där den hanterade noden är den dator som är värd för arbets flödes sessionen:

   ```powershell
   Invoke-Command -Session $ws {Test-Workflow}
   ```

   Var de hanterade noderna är fjärrdatorer.

   ```powershell
   Invoke-Command -Session $ws{
   Test-Workflow -PSComputerName Server01, Server02 }
   ```

   I följande exempel körs **test-Workflow** på hundratals datorer. `Get-Content`Cmdlet: en hämtar dator namnen från en textfil och sparar dem i `$Servers` variabeln på den lokala datorn.

   `Invoke-Command` använder `$Using` omfångs modifieraren för att definiera `$Servers` variabeln i den lokala sessionen. Mer information om `$Using` omfångs modifieraren finns i [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).

   ```powershell
   $Servers = Get-Content Servers.txt
   Invoke-Command -Session $ws {Test-Workflow -PSComputerName $Using:Servers }
   ```

## <a name="using-workflow-common-parameters"></a>Använda gemensamma parametrar för arbets flöde

De gemensamma parametrarna för arbets flödet är en uppsättning parametrar som PowerShell automatiskt lägger till i alla arbets flöden. PowerShell lägger till cmdlets vanliga parametrar i alla arbets flöden, även om arbets flödet inte använder attributet **CmdletBinding** .

Följande arbets flöde definierar till exempel inga parametrar. Men när du kör arbets flödet har det både **CommonParameters** och **WorkflowCommonParameters**.

```powershell
workflow Test-Workflow {Get-Process}
Get-Command Test-Workflow -Syntax
```

```powershell
Test-Workflow [<WorkflowCommonParameters>] [<CommonParameters>]
```

Arbets flödets gemensamma parametrar innehåller flera parametrar som är nödvändiga för att köra arbets flöden. Den gemensamma parametern **PSComputerName** anger till exempel de hanterade noder som arbets flödet påverkar.

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02
}
```

Den gemensamma **PSPersist** -parametern för arbets flödet avgör när arbets flödes data sparas. Du kan lägga till persistence mellan aktiviteter i arbets flöden som inte definierar beständiga punkter.

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPersist:$True
}
```

I andra gemensamma parametrar för arbets flöde kan du ange egenskaperna för fjärr anslutningen till de hanterade noderna. Deras namn och funktionalitet liknar parametrarna för fjärr-cmdletar, inklusive `Invoke-Command` .

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPort 443
}
```

Se till att skilja på de parametrar för fjärr anslutning som definierar anslutningen till arbets flödes sessionen från de gemensamma parametrarna **PS-prefixed** Workflow som definierar anslutningen till de hanterade noderna.

```powershell
$ws = New-PSSession -ComputerName Server01 -ConfigurationName Microsoft.PowerShell.Workflow

Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSConfigurationName Microsoft.PowerShell.Workflow
}
```

Vissa gemensamma parametrar för arbets flödet är unika för arbets flöden, till exempel parametern **PSParameterCollection** som gör att du kan ange olika parameter värden för olika arbets flöden för olika fjärrnoder. En lista och beskrivning av de gemensamma parametrarna för arbets flödet finns i [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md).

## <a name="see-also"></a>Se även

[Invoke-arbetsflöde](xref:PSWorkflowUtility.Invoke-AsWorkflow)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[PSWorkflow](xref:PSWorkflow) -cmdletar

[Arbetsflödesguiden](/previous-versions/powershell/scripting/components/workflows-guide)

[Skriva ett Windows PowerShell-arbetsflöde](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
