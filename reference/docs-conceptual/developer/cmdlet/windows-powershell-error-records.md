---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell-felposter
description: Windows PowerShell-felposter
ms.openlocfilehash: 899acf08508b1469b7ec3985d5665367fc2c1531
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355603"
---
# <a name="windows-powershell-error-records"></a>Windows PowerShell-felposter

-Cmdletar måste klara ett [system. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -objekt som identifierar fel tillståndet för avslutande och icke-avslutande fel.

Objektet [system. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) innehåller följande information:

- Det undantag som beskriver felet. Detta är ofta ett undantag som cmdleten fångas in och konverteras till en felpost. Varje fel post måste innehålla ett undantag.

Om cmdleten inte fångade ett undantag måste den skapa ett nytt undantag och välja den undantags klass som bäst beskriver fel tillståndet. Du behöver dock inte utlösa undantaget eftersom det kan nås via egenskapen [system. Management. Automation. ErrorRecord. Exception](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) i objektet [system. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) .

- En fel-ID som ger en riktad beteckning som kan användas för diagnos syfte och Windows PowerShell-skript för att hantera specifika fel villkor med specifika fel hanterare. Varje fel post måste innehålla en fel identifierare (se fel identifierare).

- En fel kategori som tillhandahåller en allmän beteckning som kan användas i diagnostiska syfte.
  Varje fel post måste ange en fel kategori (se fel kategori).

- Ett valfritt ersättnings fel meddelande och en Rekommenderad åtgärd (se ersättnings fel meddelande).

- Valfri anrops information om den cmdlet som utlöste felet. Den här informationen anges av Windows PowerShell (se anrops meddelandet).

- Det mål objekt som bearbetades när felet inträffade. Detta kan vara ett annat objekt, eller så kan det vara ett annat objekt som din cmdlet bearbetar. Till exempel `remove-item -recurse c:\somedirectory` kan felet vara en instans av ett fileinfo-objekt för "c:\somedirectory\lockedfile" för kommandot. Informationen om mål objekt är valfri.

## <a name="error-identifier"></a>Fel-ID

När du skapar en fel post anger du en identifierare som anger fel villkoret i din cmdlet. Windows PowerShell kombinerar mål identifieraren med namnet på din cmdlet för att skapa en fullständigt kvalificerad fel identifierare. Den fullständigt kvalificerade fel identifieraren kan nås via egenskapen [system. Management. Automation. ErrorRecord. FullyQualifiedErrorId](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) för objektet [system. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . Fel identifieraren är inte tillgänglig för sig själv. Den är endast tillgänglig som en del av den fullständigt kvalificerade fel identifieraren.

Använd följande rikt linjer för att generera fel identifierare när du skapar fel poster:

- Gör fel identifierare som är speciella för ett fel tillstånd. Rikta in sig på fel-ID: n för diagnos syfte och för skript som hanterar specifika fel villkor med specifika fel hanterare. En användare ska kunna använda fel identifieraren för att identifiera felet och dess källa. Fel identifierare möjliggör även rapportering av vissa fel villkor från befintliga undantag så att nya undantags underklasser inte krävs.

- I allmänhet tilldelar du olika fel identifierare till olika kod Sök vägar. Slutanvändarens förmåner från särskilda identifierare. Ofta har varje kod Sök väg som anropar [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) eller [system. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) en egen identifierare. Som regel definierar du en ny identifierare när du definierar en ny mall sträng för fel meddelandet och vice versa. Använd inte fel meddelandet som en identifierare.

- När du publicerar kod med en viss fel identifierare upprättar du semantiken för fel med den identifieraren för din fullständiga produkt support livs cykel. Återanvänd den inte i en kontext som är semantiskt annorlunda från den ursprungliga kontexten. Om semantiken för det här felet ändras skapar du och använder sedan en ny identifierare.

- Du bör vanligt vis bara använda en viss fel identifierare för undantag för en viss CLR-typ. Om typen av undantag eller typen av mål objekt ändras, skapar du och använder sedan en ny identifierare.

- Välj text för din fel identifierare som är kortfattad för det fel som du rapporterar. Använd standard-.NET Framework namngivnings-och Skift läges konventioner. Använd inte blank steg eller skiljetecken. Lokalisera inte fel identifierare.

- Generera inte fel identifierare dynamiskt på ett icke-reproducerbart sätt. Inkludera till exempel inte fel information, till exempel ett process-ID. Fel identifierare är bara användbara om de motsvarar de fel identifierare som visas av andra användare som har samma fel tillstånd.

## <a name="error-category"></a>Fel kategori

När du skapar en felpost anger du kategori för felet med hjälp av en av konstanterna som definieras av uppräkningen [system. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) . I Windows PowerShell används fel kategorin för att visa fel information när användarna anger `$ErrorView` variabeln `"CategoryView"` .

Undvik att använda konstanten [system. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) 
 **NotSpecified** . Om du har information om felet eller om åtgärden som orsakade felet, väljer du den kategori som bäst beskriver felet eller åtgärden, även om kategorin inte är en perfekt matchning.

Den information som visas i Windows PowerShell kallas för kategori-och-visnings sträng och bygger på egenskaperna för klassen [system. Management. Automation. Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) . (Den här klassen nås via egenskapen Error [system. Management. Automation. ErrorRecord. CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) .)

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

I följande lista beskrivs den information som visas:

- Kategori: en Windows PowerShell-definierad [system. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) -konstant.

- Målnamn: som standard är namnet på objektet som cmdleten bearbetades när felet inträffade.
  Eller en annan cmdlet-definierad sträng.

- TargetType: som standard är typen av mål objekt. Eller en annan cmdlet-definierad sträng.

- Aktivitet: som standard är namnet på den cmdlet som skapade fel posten. Eller en annan cmdlet-definierad sträng.

- Orsak: som standard är undantags typen. Eller en annan cmdlet-definierad sträng.

## <a name="replacement-error-message"></a>Ersättnings fel meddelande

När du utvecklar en felpost för en cmdlet kommer standard fel meddelandet för felet att hämtas från standard meddelande texten i egenskapen [system. Exception. Message](/dotnet/api/System.Exception.Message) . Detta är en skrivskyddad egenskap vars meddelande text endast är avsedd för fel söknings ändamål (enligt rikt linjerna för .NET Framework). Vi rekommenderar att du skapar ett fel meddelande som ersätter eller förstärker standard meddelande texten. Gör meddelandet mer användarvänligt och mer unikt för cmdleten.

Ersättnings meddelandet tillhandahålls av ett [system. Management. Automation. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) -objekt. Använd någon av följande konstruktorer för det här objektet eftersom de ger ytterligare lokaliserings information som kan användas av Windows PowerShell.

- [ErrorDetails (cmdlet, sträng, sträng, objekt [])](/dotnet/api/system.management.automation.errordetails.-ctor#System_Management_Automation_ErrorDetails__ctor_System_Management_Automation_Cmdlet_System_String_System_String_System_Object___): Använd den här konstruktorn om din mall sträng är en resurs sträng i samma sammansättning som cmdleten implementeras i, eller om du vill läsa in mallstrukturlistan genom en åsidosättning av metoden [system. Management. Automation. cmdlet. GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) .

- [ErrorDetails (sammansättning, sträng, sträng, objekt [])](/dotnet/api/system.management.automation.errordetails.-ctor#System_Management_Automation_ErrorDetails__ctor_System_Reflection_Assembly_System_String_System_String_System_Object___): Använd den här konstruktorn om frågesträngen finns i en annan sammansättning och du inte läser in den via en åsidosättning av [system. Management. Automation. cmdlet. GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString).

Ersättnings meddelandet bör följa rikt linjerna för .NET Framework design för att skriva undantags meddelanden med liten skillnad. Rikt linjerna är ett tillstånd för att undantags meddelanden ska skrivas för utvecklare. De här ersättnings meddelandena ska vara skrivna för cmdlet-användaren.

Ersättnings fel meddelandet måste läggas till innan [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) eller [system. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metoder anropas. Om du vill lägga till ett ersättnings meddelande ställer du in egenskapen [system. Management. Automation. ErrorRecord. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) i fel posten. När den här egenskapen har angetts visas egenskapen [system. Management. Automation. ErrorDetails. Message *](/dotnet/api/System.Management.Automation.ErrorDetails.Message) i Windows PowerShell i stället för standard meddelande texten.

## <a name="recommended-action-information"></a>Rekommenderad åtgärds information

Objektet [system. Management. Automation. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) kan också ge information om vilka åtgärder som rekommenderas när felet uppstår.

## <a name="invocation-information"></a>Information om anrop

När en cmdlet använder [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) eller [system. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) för att rapportera en felpost, lägger Windows PowerShell automatiskt till information som beskriver kommandot som anropades när felet uppstod. Den här informationen tillhandahålls av ett [system. Management. Automation. Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo) -objekt som innehåller namnet på den cmdlet som anropades av kommandot, själva kommandot och information om pipelinen eller skriptet. Den här egenskapen är skrivskyddad.

## <a name="see-also"></a>Se även

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System. Management. Automation. Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System. Management. Automation. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System. Management. Automation. Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Windows PowerShell-felrapportering](./error-reporting-concepts.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
