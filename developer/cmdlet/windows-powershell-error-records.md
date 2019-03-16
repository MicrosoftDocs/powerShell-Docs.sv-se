---
title: Windows PowerShell-fel registrerar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error category [PowerShell SDK]
- error identifier [PowerShell SDK]
- error records [PowerShell SDK]
- error category string [PowerShell SDK]
ms.assetid: bdd66fea-eb63-4bb6-9cbe-9a799e5e0db5
caps.latest.revision: 9
ms.openlocfilehash: f6f5e50c55b477cbbeeaaf4f3ea665d5dc07758c
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059770"
---
# <a name="windows-powershell-error-records"></a>Windows PowerShell-felposter

Cmdlet: ar måste klara ett [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objekt som identifierar feltillstånd för avslutande och icke-avslutande fel.

Den [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objektet innehåller följande information:

- Undantag som beskriver felet. Det här är ofta ett undantag som cmdleten fångas och konverteras till en Felpost. Varje Felpost måste innehålla ett undantag.

Om cmdlet: en inte fånga undantag, måste den skapa ett nytt undantag och välj undantagsklass som bäst beskriver felet. Men du behöver inte Utlös undantaget eftersom den kan nås via den [System.Management.Automation.ErrorRecord.Exception](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) egenskapen för den [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)objekt.

- En identifierare för fel som tillhandahåller en riktad enhetsbeteckning som kan användas i diagnostiskt syfte och av Windows PowerShell-skript för att hantera specifika felvillkor med specifika felhanterare. Varje Felpost måste innehålla ett fel-ID (se fel-ID).

- En felkategori som ger en allmän enhetsbeteckning som kan användas i diagnostiskt syfte. Varje Felpost måste ange en felkategori (se felkategori).

- Ett valfritt ersättning felmeddelande och en rekommenderad åtgärd (se felmeddelandet för ersättning).

- Valfritt anrop information om cmdlet: en som returnerade fel. Den här informationen anges av Windows PowerShell (se anrop meddelande).

- Målobjektet som behandlades när felet inträffade. Detta kan vara indataobjektet eller det kan vara ett annat objekt som din cmdlet bearbetar. Till exempel för kommandot `remove-item -recurse c:\somedirectory`, felet kan vara en instans av en FileInfo-objektet för ”c:\somedirectory\lockedfile”. Objektinformation mål är valfritt.

## <a name="error-identifier"></a>Fel-ID

Ange en identifierare som betecknar feltillstånd i din cmdlet när du skapar en Felpost. Windows PowerShell kombinerar det aktuella ID: t med namnet på din cmdlet för att skapa ett fullständigt fel-ID. Det fullständigt kvalificerade fel-ID: t kan nås via den [System.Management.Automation.ErrorRecord.FullyQualifiedErrorId](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) egenskapen för den [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)objekt. Fel-ID är inte tillgänglig ensamt. Det finns endast som en del av det fullständigt kvalificerade fel-ID: t.

Använd följande riktlinjer för att generera fel-ID när du skapar felposter:

- Göra fel-ID specifika i ett feltillstånd. Rikta fel-ID i diagnostiskt syfte och för skript som hanterar specifika felvillkor med specifika felhanterare. En användare ska kunna använda fel identifierare för att identifiera felet och dess källa. Fel-ID också aktivera rapportering för specifika felvillkor från befintliga undantag så att den nya undantag underklasser inte krävs.

- I allmänhet tilldela olika fel-ID till olika kodsökvägar. Slutanvändaren dra nytta av specifika identifierare. Ofta varje kodsökvägar som anropar [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) eller [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) har sin egen identifierare. Definiera en ny identifierare som en regel när du definierar en ny mallsträng för felmeddelande och vice versa. Använd inte ett felmeddelande som en identifierare.

- När du publicerar kod med hjälp av ett visst fel-ID kan upprätta du semantiken för fel med en identifierare för fullständig produkten supportlivscykeln. Återanvänd inte det i en kontext som skiljer sig från från den ursprungliga kontexten. Ändrar semantiken för det här felet, skapa och Använd sedan en ny identifierare.

- Allmänt bör du använda ett visst fel-ID endast för undantag av en viss CLR-typen. Om typ av undantag eller typ av målobjektet ändras, skapa och Använd sedan en ny identifierare.

- Välj text för din fel-ID som motsvarar koncist felet som du rapporterar. Använd standard .NET Framework-namngivning och skiftläge konventioner. Använd inte blanksteg eller skiljetecken. Lokalisera inte fel-ID.

- Dynamiskt generera inte fel-ID på ett icke-reproducerbar sätt. Exempelvis inte inkludera information om fel, till exempel en process-ID. Fel-ID är användbara endast om de motsvarar fel-ID som ses av andra användare som har samma fel.

## <a name="error-category"></a>Felkategori

När du skapar en Felpost kan ange vilken typ av fel med någon av konstanterna som definieras av den [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) uppräkning. Windows PowerShell använder kategorin fel för att visa information om fel när användare anger den `$ErrorView` variabeln `"CategoryView"`.

Undvik att använda den [System.Management.Automation.Errorcategory.Notspecified](/dotnet/api/System.Management.Automation.ErrorCategory.NotSpecified) konstant. Om du har all information om felet eller den åtgärd som orsakade felet, Välj den kategori som bäst beskriver felet eller åtgärden, även om kategorin inte är perfekt.

Informationen som visas av Windows PowerShell kallas kategorivyn strängen och är byggd från egenskaperna för den [System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) klass. (Den här klassen är tillgängligt via felet [System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) egenskap.)

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

I följande lista beskrivs den information som visas:

- Kategori: En Windows PowerShell-definierade [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) konstant.

- Målnamn: Som standard objektets namn cmdleten bearbetade när felet uppstod. Eller en annan cmdlet-definierade sträng.

- TargetType: Standardvärdet är typ av målobjektet. Eller en annan cmdlet-definierade sträng.

- Aktivitet: Standardvärdet är namnet på den cmdlet som skapade en Felpost. Eller andra cmdlet-definierade sträng.

- Orsak: Standardvärdet är typ av undantag. Eller en annan cmdlet-definierade sträng.

## <a name="replacement-error-message"></a>Felmeddelande för ersättning

När du utvecklar en Felpost för en cmdlet standardfelmeddelande för felet kommer från standardmeddelandet i den [System.Exception.Message](/dotnet/api/System.Exception.Message) egenskapen. Det här är en skrivskyddad egenskap vars meddelandetext är endast avsett för felsökning (enligt riktlinjerna för .NET Framework). Vi rekommenderar att du skapar ett felmeddelande som ersätter eller förstärker standardmeddelandet. Gör budskapet mer användarvänligt och mer specifikt till cmdleten.

Ersättning meddelandet kommer från en [System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) objekt. Använd någon av följande konstruktorer i det här objektet eftersom de ger ytterligare lokaliseringsinformation som kan användas av Windows PowerShell.

- [ErrorDetails.ErrorDetails (objekt-Cmdlet, String, String,\[System.Management.Automation.ErrorDetails.%23Ctor%28System.Management.Automation.Cmdlet%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Management.Automation.Cmdlet%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Använd den här konstruktorn om din mall-strängen är en resurssträng i samma sammansättning där cmdleten har implementerats eller om du vill läsa in mallen strängen via en åsidosättning av den [System.Management.Automation.Cmdlet.GetResourceString ](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) metod.

- [ErrorDetails.ErrorDetails (objekt-sammansättningen, String, String,\[System.Management.Automation.ErrorDetails.%23Ctor%28System.Reflection.Assembly%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Reflection.Assembly%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Använd den här konstruktorn om mall-strängen är i en annan sammansättning och du inte läser in den via en åsidosättning av [System.Management.Automation.Cmdlet.GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString).

Ersättning meddelandet ska följa designriktlinjer för .NET Framework för att skriva undantag meddelanden med en viss skillnad. Tillståndet för riktlinjer som undantag meddelanden ska vara skrivna för utvecklare. De här meddelandena ska vara skrivna för cmdlet-användaren.

Felmeddelandet ersättning måste läggas till innan den [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) eller [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metoderna anropas. Om du vill lägga till ett meddelande som ersättning, ange den [System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) egenskapen för en Felpost. När den här egenskapen anges Windows PowerShell visar den [System.Management.Automation.ErrorDetails.Message*](/dotnet/api/System.Management.Automation.ErrorDetails.Message) egenskap i stället för standardmeddelandet.

## <a name="recommended-action-information"></a>Rekommenderad åtgärdsinformation

Den [System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) objekt kan också ge information om vilka åtgärder som rekommenderas när felet inträffar.

## <a name="invocation-information"></a>Anrops-information

När en cmdlet använder [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) eller [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) att rapportera en Felpost, Windows PowerShell lägger automatiskt till information som beskriver det kommando som anropas när felet uppstod. Den här informationen tillhandahålls av en [System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo) objekt som innehåller namnet på den cmdlet som anropas av kommandot, kommandot, och information om pipeline eller skript. Den här egenskapen är skrivskyddad.

## <a name="see-also"></a>Se även

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Felrapportering för Windows PowerShell](./error-reporting-concepts.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
