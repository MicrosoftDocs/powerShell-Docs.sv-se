---
ms.date: 09/13/2016
ms.topic: reference
title: Vanliga parameternamn
description: Vanliga parameternamn
ms.openlocfilehash: cf39dd3b04660076718336857d79d55c3784ccd1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668226"
---
# <a name="common-parameter-names"></a>Vanliga parameternamn

De parametrar som beskrivs i det här avsnittet kallas *vanliga parametrar*. De läggs till i cmdlets av Windows PowerShell-körningsmiljön och kan inte deklareras av cmdleten.

> [!NOTE]
> Dessa parametrar läggs också till i Provider-cmdletar och till funktioner som är dekorerade till `CmdletBinding` attributet.

## <a name="general-common-parameters"></a>Allmänna vanliga parametrar

Följande parametrar läggs till i alla cmdlets och kan nås varje gång cmdleten körs. De här parametrarna definieras av klassen [system. Management. Automation. Internal. Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters) .

### <a name="debug-alias-db"></a>Felsök (alias: dB)

Datatyp: SwitchParameter

Den här parametern anger om fel sökning av meddelanden på program nivå som kan visas på kommando raden. Dessa meddelanden är avsedda för att felsöka cmdletens funktion och genereras av anrop till metoden [system. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) . Fel söknings meddelanden behöver inte vara lokaliserade.

### <a name="erroraction-alias-ea"></a>ErrorAction (alias: EA)

Datatyp: uppräkning

Den här parametern anger vilken åtgärd som ska utföras när ett fel inträffar. De möjliga värdena för den här parametern definieras av uppräkningen [system. Management. Automation. Åtgärdsinställning](/dotnet/api/System.Management.Automation.ActionPreference) .

### <a name="errorvariable-alias-ev"></a>ErrorVariable (alias: EV)

Datatyp: sträng

Den här parametern anger vilken variabel som objekt ska placeras i när ett fel inträffar. Om du vill lägga till i den här variabeln använder du +*varname* i stället för att rensa och ange variabeln.

### <a name="outvariable-alias-ov"></a>Övervariabel (alias: OV)

Datatyp: sträng

Den här parametern anger den variabel där alla utdata som genereras av cmdleten ska placeras. Om du vill lägga till i den här variabeln använder du +*varname* i stället för att rensa och ange variabeln.

### <a name="outbuffer-alias-ob"></a>Utbuffer (alias: OB)

Datatyp: Int32

Den här parametern definierar antalet objekt som ska lagras i utdatabufferten innan alla objekt överförs nedåt i pipelinen. Som standard skickas objekt omedelbart ned pipelinen.

### <a name="verbose-alias-vb"></a>Verbose (alias: VB)

Datatyp: SwitchParameter

Den här parametern anger om cmdleten skriver för klar ande meddelanden som kan visas på kommando raden. Dessa meddelanden är avsedda att ge ytterligare hjälp till användaren och genereras av anrop till metoden [system. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .

### <a name="warningaction-alias-wa"></a>WarningAction (alias: WA)

Datatyp: uppräkning

Den här parametern anger vilken åtgärd som ska utföras när cmdleten skriver ett varnings meddelande. De möjliga värdena för den här parametern definieras av uppräkningen [system. Management. Automation. Åtgärdsinställning](/dotnet/api/System.Management.Automation.ActionPreference) .

### <a name="warningvariable-alias-wv"></a>WarningVariable (alias: WV)

Datatyp: sträng

Den här parametern anger vilken variabel som varnings meddelanden kan sparas i. Om du vill lägga till i den här variabeln använder du +*varname* i stället för att rensa och ange variabeln.

## <a name="risk-mitigation-parameters"></a>Risk-Mitigation parametrar

Följande parametrar läggs till i-cmdletar som begär bekräftelse innan de utför sin åtgärd. Mer information om bekräftelse begär Anden finns i [begära bekräftelse](./requesting-confirmation-from-cmdlets.md). De här parametrarna definieras av klassen [system. Management. Automation. Internal. Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) .

### <a name="confirm-alias-cf"></a>Bekräfta (alias: CF)

Datatyp: SwitchParameter

Den här parametern anger om cmdleten visar en uppmaning som frågar om användaren är säker på att han eller hon vill fortsätta.

### <a name="whatif-alias-wi"></a>WhatIf (alias: Wi)

Datatyp: SwitchParameter

Den här parametern anger om cmdleten skriver ett meddelande som beskriver effekterna av att köra cmdleten utan att faktiskt utföra någon åtgärd.

## <a name="transaction-parameters"></a>Transaktions parametrar

Följande parameter läggs till i cmdletar som stöder transaktioner. De här parametrarna definieras av klassen [system. Management. Automation. Internal. Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) .

### <a name="usetransaction-alias-usetx"></a>UseTransaction (alias: usetx)

Datatyp: SwitchParameter

Den här parametern anger om cmdleten ska använda den aktuella transaktionen för att utföra åtgärden.

## <a name="see-also"></a>Se även

[System. Management. Automation. Internal. Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System. Management. Automation. Internal. Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System. Management. Automation. Internal. Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
