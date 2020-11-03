---
external help file: Microsoft.PowerShell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflowUtility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflowutility/invoke-asworkflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-AsWorkflow
ms.openlocfilehash: b96bce9fe4d574fe2b7e9c7c0f1e05ee0508adce
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264596"
---
# Invoke-AsWorkflow

## SAMMANFATTNING
Kör ett kommando eller uttryck som ett Windows PowerShell-arbetsflöde.

## SYNTAX

### Kommando (standard)

```
Invoke-AsWorkflow [-CommandName <String>] [-Parameter <Hashtable>] [-InputObject <Object>] [<CommonParameters>]
```

### Uttryck

```
Invoke-AsWorkflow [-Expression <String>] [-InputObject <Object>] [<CommonParameters>]
```

## BESKRIVNING

`Invoke-AsWorkflow`Arbets flödet kör ett kommando eller uttryck som ett infogat skript i ett arbets flöde.
Dessa arbets flöden använder standard-semantiken för arbets flöde, har alla gemensamma parametrar för arbets flödet och har alla fördelar med arbets flöden, inklusive möjligheten att stoppa, återuppta och återställa.

Arbets flöden är utformade för långvariga kommandon som samlar in viktiga data, men som kan användas för att köra kommandon.
Mer information finns i [about_Workflows](../PSWorkflow/About/about_Workflows.md).

Du kan också lägga till gemensamma parametrar för arbets flöden i det här kommandot.
Mer information om gemensamma parametrar för arbets flöden finns i [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)

Det här arbets flödet introduceras i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: kör en cmdlet som ett arbets flöde

```powershell
Invoke-AsWorkflow -PSComputerName (Get-Content Servers.txt) -CommandName Get-ExecutionPolicy
```

```output
PSComputerName                     PSSourceJobInstanceId                   Value
--------------                     ---------------------                   -----
Server01                           77b1cdf8-8226-4662-9067-cd2fa5c3b711    AllSigned
Server02                           a33542d7-3cdd-4339-ab99-0e7cd8e59462    Unrestricted
Server03                           279bac28-066a-4646-9497-8fcdcfe9757e    AllSigned
localhost                          0d858009-2cc4-47a4-a2e0-da17dc2883d0    RemoteSigned
```

Det här kommandot kör `Get-ExecutionPolicy` cmdleten som ett arbets flöde på hundratals datorer.

Kommandot använder parametern **commandname** för att ange den cmdlet som körs i arbets flödet.
Den gemensamma parametern för **PSComputerName** -arbetsflöde används för att ange de datorer där kommandot körs.
Värdet för parametern **PSComputerName** är ett `Get-Content` kommando som hämtar en lista med dator namn från Servers.txt-filen.
Parametervärdet omges av parenteser för att direkt köra Windows PowerShell för att köra `Get-Command` kommandot innan värdet används.

Som med alla fjärrkommandon, om kommandot körs på den lokala datorn (om värdet för parametern PSComputerName inkluderar den lokala datorn) måste du starta Windows PowerShell med alternativet "kör som administratör".

### Exempel 2: köra en cmdlet med parametrar

```powershell
$s = Import-Csv .\Servers.csv -Header ServerName, ServerID
Invoke-AsWorkflow -CommandName Get-ExecutionPolicy -Parameter @{Scope="Process"} -PSComputerName {$s.ServerName} -PSConnectionRetryCount 5
```

Det första kommandot använder `Import-Csv` cmdleten för att skapa ett objekt från innehållet i Servers.csvs filen. Kommandot använder `Header` parametern för att skapa en `ServerName` egenskap för den kolumn som innehåller namnen på mål datorerna, även kallade "fjärrnoder". Kommandot sparar resultatet i `$s` variabeln.

Det andra kommandot använder `Invoke-AsWorkflow` arbets flödet för att köra ett `Get-ExecutionPolicy` kommando på datorerna i Servers.csv-filen. Kommandot använder parametern **commandname** för `Invoke-AsWorkflow`  för att ange det kommando som ska köras i arbets flödet. `Parameter`Parametern i används `Invoke-AsWorkflow` för att ange `Scope` parametern för `Get-ExecutionPolicy` cmdleten med värdet **process**. Kommandot använder även `PSConnectionRetryCount` arbets flödets gemensamma parameter för att begränsa kommandot till fem försök på varje dator och den `PSComputerName` gemensamma parametern för arbets flödet för att ange namnen på fjärrnoderna (mål datorer). `PSComputerName`Parameterns värde är ett uttryck som hämtar `ServerName` egenskapen för varje objekt i `$s` variabeln.

Kommandona kör ett `Get-ExecutionPolicy` kommando som ett arbets flöde på hundratals datorer.
Kommandot använder `Scope` parametern för `Get-ExecutionPolicy` cmdleten med värdet **process** för att hämta körnings principen i den aktuella sessionen.

### Exempel 3: kör ett uttryck som ett arbets flöde

```powershell
Invoke-AsWorkflow -Expression "ipconfig /all" -PSComputerName (Get-Content DomainControllers.txt) -AsJob -JobName IPConfig
```

```output
Id     Name          PSJobTypeName   State         HasMoreData   Location                Command
--     ----          -------------   -----         -----------   --------                -------
2      IpConfig      PSWorkflowJob   Completed     True          Server01, Server01...   Invoke-AsWorkflow
```

Det här kommandot använder `Invoke-AsWorkflow` arbets flödet för att köra ett ipconfig-kommando som ett arbets flödes jobb på de datorer som anges i DomainControllers.txt-filen.

Kommandot använder `Expression` parametern för att ange det uttryck som ska köras.
Den `PSComputerName` gemensamma parametern för arbets flödet används för att ange namnen på fjärrnoderna (mål datorer).

Kommandot använder också de `AsJob` `JobName` gemensamma parametrarna och för att köra arbets flödet som ett bakgrunds jobb på varje dator med jobbnamn "ipconfig".

Kommandot returnerar ett `ContainerParentJob` objekt ( `System.Management.Automation.ContainerParentJob` ) som innehåller arbets flödes jobben på varje dator.

## PARAMETRAR

### – CommandName

Kör angiven cmdlet eller avancerad funktion som ett arbets flöde.
Ange cmdleten eller funktions namnet, till exempel `Update-Help` , `Set-ExecutionPolicy` eller `Set-NetFirewallRule` .

```yaml
Type: System.String
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Uttryck

Anger det uttryck som den här cmdleten kör som ett arbets flöde.
Ange uttrycket som en sträng, till exempel `"ipconfig /all"` .
Om uttrycket innehåller blank steg eller specialtecken omger du uttrycket med citat tecken.

```yaml
Type: System.String
Parameter Sets: Expression
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Parameter

Anger parametrar och parameter värden för kommandot som anges i `CommandName` parametern.
Ange en hash-tabell där varje nyckel är ett parameter namn och dess värde är parametervärdet, till exempel `@{ExecutionPolicy="AllSigned"}` .

Information om hash-tabeller finns i [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Används för att tillåta pipeline-inflöden.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

### WorkflowCommonParameters

Den här cmdleten stöder också arbets flödes parametrar för gemensamma parametrar.
Mer information finns i [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md).

## INDATA

### System. Object

Du kan skicka ett objekt till- `InputObject` parametern.

## UTDATA

### Inget

Det här kommandot genererar inga utdata.
Men den kör arbets flödet, vilket kan generera utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[New-PSWorkflowExecutionOption](../PSWorkflow/New-PSWorkflowExecutionOption.md)

[New-PSWorkflowSession](../PSWorkflow/New-PSWorkflowSession.md)

[about_Workflows](../PSWorkflow/About/about_Workflows.md)

[about_Workflow_Common_Parameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)
