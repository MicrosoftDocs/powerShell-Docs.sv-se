---
title: Vanliga parameternamn | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: c65deeda6b2ef1b52de55035dc606259a7f2d232
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068447"
---
# <a name="common-parameter-names"></a>Vanliga parameternamn

De parametrar som beskrivs i det här avsnittet kallas *gemensamma parametrar*. De har lagts till i cmdletar med Windows PowerShell-runtime och går inte att deklarera av cmdlet: en.

> [!NOTE]
> Dessa parametrar läggs också till provider-cmdletar och funktioner som dekorerad med den `CmdletBinding` attribut.

## <a name="general-common-parameters"></a>Allmänna gemensamma parametrar

Följande parametrar läggs till i alla cmdletar och kan nås när cmdleten körs. Dessa parametrar definieras av den [System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters) klass.

### <a name="debug-alias-db"></a>Debug (alias: db)

Datatyp: SwitchParameter

Den här parametern anger om felsökning av programmerare på servernivå meddelanden som kan visas på kommandoraden. Dessa meddelanden är avsedda för att felsöka driften av cmdlet: en och genereras av anrop till den [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metod. Felsökningsmeddelanden behöver inte lokaliseras.

### <a name="erroraction-alias-ea"></a>ErrorAction (alias: ea)

Datatyp: Uppräkning

Den här parametern anger vilka åtgärder ska äga rum när ett fel uppstår. De möjliga värdena för den här parametern definieras av den [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) uppräkning.

### <a name="errorvariable-alias-ev"></a>ErrorVariable (alias: ev)

Datatyp: Sträng

Den här parametern anger variabeln att placera objekt när ett fel uppstår. Om du vill lägga till den här variabeln, Använd +*varname* i stället för att rensa och ange variabeln.

### <a name="outvariable-alias-ov"></a>OutVariable (alias: ov)

Datatyp: Sträng

Den här parametern anger variabeln som du vill placera alla utdata genereras av cmdlet: en. Om du vill lägga till den här variabeln, Använd +*varname* i stället för att rensa och ange variabeln.

### <a name="outbuffer-alias-ob"></a>OutBuffer (alias: ob)

Datatyp: Int32

Den här parametern anger antalet objekt som ska lagra i utdatabufferten innan alla objekt som skickas av pipelinen. Som standard skickas objekt direkt av pipelinen.

### <a name="verbose-alias-vb"></a>Verbose (alias: vb)

Datatyp: SwitchParameter

Den här parametern anger om cmdleten skriver förklarande meddelanden som kan visas på kommandoraden. Dessa meddelanden är avsedda att ge mer hjälp för användaren och genereras av anrop till den [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metod.

### <a name="warningaction-alias-wa"></a>WarningAction (alias: wa)

Datatyp: Uppräkning

Den här parametern anger vilka åtgärder ska äga rum när cmdleten skriver ett varningsmeddelande. De möjliga värdena för den här parametern definieras av den [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) uppräkning.

### <a name="warningvariable-alias-wv"></a>WarningVariable (alias: wv)

Datatyp: Sträng

Den här parametern anger variabeln där varningsmeddelanden kan sparas. Om du vill lägga till den här variabeln, Använd +*varname* i stället för att rensa och ange variabeln.

## <a name="risk-mitigation-parameters"></a>Riskreducering parametrar

Följande parametrar läggs till i cmdletar som begär bekräftelse innan de utför åtgärden. Läs mer om begäranden om händelsebekräftelse [begär bekräftelse](./requesting-confirmation-from-cmdlets.md). Dessa parametrar definieras av den [System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) klass.

### <a name="confirm-alias-cf"></a>Bekräfta (alias: cf)

Datatyp: SwitchParameter

Den här parametern anger om cmdleten visar uppmanas att ange om användaren är säker på att de vill fortsätta.

### <a name="whatif-alias-wi"></a>WhatIf (alias: wi)

Datatyp: SwitchParameter

Den här parametern anger om cmdleten skriver ett meddelande om att effekterna av att köra cmdlet utan att faktiskt utföra några åtgärder.

## <a name="transaction-parameters"></a>Parametrar för transaktion

Följande parameter har lagts till cmdlets som stöder transaktioner. Dessa parametrar definieras av den [System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) klass.

### <a name="usetransaction-alias-usetx"></a>Egenskaperna UseTransaction (alias: usetx)

Datatyp: SwitchParameter

Den här parametern anger om cmdlet: en kommer att använda den aktuella transaktionen för att utföra åtgärden.

## <a name="see-also"></a>Se även

[System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
