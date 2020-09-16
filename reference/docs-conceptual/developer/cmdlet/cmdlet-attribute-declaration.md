---
title: Deklaration av cmdlet-attribut | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.openlocfilehash: 672609f1f50e4600aebcbb7e6e79bb7353ec867d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774838"
---
# <a name="cmdlet-attribute-declaration"></a>Deklaration av attributet Cmdlet

Cmdlet-attributet identifierar en Microsoft .NET Framework-klass som en cmdlet och anger verbet och substantivet som används för att anropa cmdleten.

## <a name="syntax"></a>Syntax

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>Parametrar

`VerbName` ([System. String](/dotnet/api/System.String)) krävs. Anger cmdlet-verbet. Verbet anger den åtgärd som ska vidtas av cmdleten. Mer information om godkända cmdlet-verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md) och [nödvändiga utvecklings rikt linjer](./required-development-guidelines.md).

`NounName` ([System. String](/dotnet/api/System.String)) krävs. Anger cmdleten substantiv. Detta Substantiv anger den resurs som cmdleten agerar på. Mer information om cmdlet Substantiv finns i cmdlet- [deklaration](./cmdlet-class-declaration.md) och [starkt uppmuntrande utvecklings rikt linjer](./strongly-encouraged-development-guidelines.md).

`SupportsShouldProcess` ([System. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter. `True` anger att cmdleten stöder anrop till metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , som tillhandahåller cmdleten ett sätt att uppmana användaren innan en åtgärd som ändrar systemet utförs. `False`, standardvärdet anger att cmdleten inte stöder anrop till metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Mer information om bekräftelse begär Anden finns i [begära bekräftelse](./requesting-confirmation-from-cmdlets.md).

`ConfirmImpact` ([System. Management. Automation. Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) valfri namngiven parameter. Anger när cmdlet-åtgärden ska bekräftas av ett anrop till metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) kommer endast att anropas när ConfirmImpact-värdet för cmdleten (som standard, medium) är lika med eller större än värdet för `$ConfirmPreference` variabeln. Den här parametern ska endast anges när `SupportsShouldProcess` parametern har angetts.

`DefaultParameterSetName` ([System. String](/dotnet/api/System.String)) valfri namngiven parameter. Anger standard parameter uppsättningen som Windows PowerShell-körningsmiljön försöker använda när den inte kan avgöra vilken parameter som ska användas. Observera att den här situationen kan elimineras genom att göra den unika parametern för varje parameter inställd på en obligatorisk parameter.

Det finns ett fall där Windows PowerShell inte kan använda standard parameter uppsättningen även om en standard parameter uppsättnings namn har angetts. Windows PowerShell-körningsmiljön kan inte särskilja mellan parameter uppsättningar som enbart baseras på objekt typ. Om du till exempel har en parameter uppsättning som tar en sträng som fil Sök väg och en annan uppsättning som tar ett **fileinfo** -objekt direkt, kan Windows PowerShell inte avgöra vilken parameter som ska användas baserat på de värden som skickas till cmdleten, eller använda standard parameter uppsättningen. I det här fallet, även om du anger ett standard parameter uppsättnings namn, genererar Windows PowerShell ett fel meddelande med en tvetydig parameter uppsättning.

`SupportsTransactions` ([System. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter. `True` anger att cmdleten kan användas i en transaktion. När `True` har angetts lägger Windows PowerShell-körningsmiljön till `UseTransaction` parametern till parameter listan för cmdleten. `False`, standardvärdet anger att cmdleten inte kan användas i en transaktion.

## <a name="remarks"></a>Kommentarer

- Tillsammans används verbet och Substantiv för att identifiera din registrerade cmdlet och för att anropa din cmdlet i ett skript.

- När cmdleten anropas från Windows PowerShell-konsolen liknar kommandot följande kommando:

**VerbName-NounName**

- Alla cmdletar som ändrar resurser utanför Windows PowerShell ska innehålla `SupportsShouldProcess` nyckelordet när cmdlet-attributet deklareras, vilket gör att cmdleten anropar metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) innan cmdleten utför åtgärden. Om anropet [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returneras `false` , ska åtgärden inte vidtas. Mer information om bekräftelse förfrågningar som genereras av anropet [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) finns i [begära bekräftelse](./requesting-confirmation-from-cmdlets.md).

`Confirm`Parametrarna-och `WhatIf` cmdlet är bara tillgängliga för cmdletar som stöder [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -anrop.

## <a name="example"></a>Exempel

Följande klass definition använder cmdlet-attributet för att identifiera .NET Framework-klassen för en **Get-proc-** cmdlet som hämtar information om processerna som körs på den lokala datorn.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Mer information om cmdleten **Get-proc** finns i [själv studie kursen om GetProc](./getproc-tutorial.md).

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
