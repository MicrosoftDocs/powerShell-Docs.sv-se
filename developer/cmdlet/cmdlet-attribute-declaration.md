---
title: Cmdlet-attributet deklarationen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.assetid: 1d323332-f773-4c0e-8a69-2aada765afb2
caps.latest.revision: 12
ms.openlocfilehash: 6887467ad5ccafe6edf8f03f531b4750133aa9e9
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058036"
---
# <a name="cmdlet-attribute-declaration"></a>Deklaration av attributet Cmdlet

Attributet cmdleten identifierar en Microsoft .NET Framework-klass som en cmdlet och anger verb och substantiv som används för att anropa cmdleten.

## <a name="syntax"></a>Syntax

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>Parametrar

`VerbName` ([System.String](/dotnet/api/System.String)) krävs. Anger cmdlet verb. Den här verb anger de åtgärder som vidtagits av cmdlet: en. Läs mer om godkända cmdlet verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md) och [krävs utveckling riktlinjer](./required-development-guidelines.md).

`NounName` ([System.String](/dotnet/api/System.String)) krävs. Anger cmdlet-substantiv. Den här substantiv anger den resurs som cmdleten agerar på. Läs mer om cmdlet-substantiv [Cmdlet deklarationen](./cmdlet-class-declaration.md) och [starkt uppmuntras riktlinjer för utveckling](./strongly-encouraged-development-guidelines.md).

`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) valfritt med namnet parametern. `True` Anger att cmdleten stöder anrop till den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metoden, vilket ger ett sätt att fråga användaren innan en åtgärd som ändrar systemet utförs cmdlet: en. `False`, standardvärdet anger att cmdleten inte stöder anrop till den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metod. Läs mer om begäranden om händelsebekräftelse [begär bekräftelse](./requesting-confirmation-from-cmdlets.md).

`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) valfritt med namnet parametern. Anger när åtgärden för cmdlet: en ska bekräftas av ett anrop till den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metod. [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ska endast anropas när ConfirmImpact värdet för cmdlet: en (som standard, medel) är lika med eller större än värdet för den `$ConfirmPreference` variabeln. Den här parametern anges endast när den `SupportsShouldProcess` parameter har angetts.

`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) valfritt med namnet parametern. Anger den standardparametern anger att Windows PowerShell-runtime försöker använda när den inte kan avgöra vilken parametern inställd på att använda. Observera att den här situationen kan tas bort genom att göra unika parametern för varje parameter som anger en obligatorisk parameter.

Det är ett fall där Windows PowerShell inte kan använda standardparameter ange även om ett set parameternamn har angetts. Windows PowerShell-körning kan inte skilja mellan parameteruppsättningar som endast baseras på objekttyp. Till exempel om du har en parameteruppsättning som tar en sträng som filens sökväg och en annan uppsättning som tar en **FileInfo** objekt direkt, Windows PowerShell det går inte att fastställa vilka parametern inställd på att använda baserat på de värden som skickas till den cmdlet: en, och den standard-parameteruppsättningen. Även om du anger en standardparameter ange namn, i det här fallet utlöser felmeddelandet tvetydig parametern uppsättning Windows PowerShell.

`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) valfritt med namnet parametern. `True` Anger att cmdleten kan användas i en transaktion. När `True` anges, Windows PowerShell-runtime lägger till den `UseTransaction` parameter i parameterlistan för cmdlet: ar. `False`, standardvärdet anger att cmdleten inte kan användas i en transaktion.

## <a name="remarks"></a>Anmärkningar

- Verb och substantiv är tillsammans för att identifiera registrerade cmdlet: och att anropa cmdlet: ett skript.

- När cmdleten anropas från Windows PowerShell-konsolen, liknar kommandot följande kommando:

**VerbName NounName**

- Alla cmdletar som ändrar resurser utanför Windows PowerShell ska innehålla den `SupportsShouldProcess` nyckelord när Cmdlet-attributet har deklarerats, vilket gör att cmdleten för att anropa den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metoden innan cmdlet utför åtgärden. Om den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -anrop returnerar `false`, åtgärden bör inte vidtas. Mer information om bekräftelse begäranden genererade av den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anropa, se [begär bekräftelse](./requesting-confirmation-from-cmdlets.md).

Den `Confirm` och `WhatIf` cmdlet-parametrarna är endast tillgängliga för cmdletar som stöder [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anrop.

## <a name="example"></a>Exempel

Följande klassdefinition använder Cmdlet-attribut för att identifiera den .NET Framework-klassen för en **Get-Proc** cmdlet som hämtar information om de processer som körs på den lokala datorn.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Mer information om den **Get-Proc** cmdlet, se [GetProc självstudien](./getproc-tutorial.md).

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
