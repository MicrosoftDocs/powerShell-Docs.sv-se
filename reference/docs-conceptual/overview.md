---
ms.date: 08/27/2018
keywords: PowerShell, cmdlet
title: PowerShell-skript
ms.openlocfilehash: 281f2e798b3d3fa1c150b079d633cb7e8490dcec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "62058496"
---
# <a name="powershell"></a>PowerShell

PowerShell är ett uppgifts baserat kommando rads gränssnitt och skript språk som bygger på .NET.
Med PowerShell kan system administratörer och avancerade användare snabbt automatisera uppgifter som hanterar operativ system (Linux, macOS och Windows) och processer.

Med PowerShell-kommandon kan du hantera datorer från kommando raden. Med PowerShell-providers kan du komma åt data lager, till exempel registret och certifikat arkivet, så enkelt som du har åtkomst till fil systemet. PowerShell innehåller en omfattande uttrycks parser och ett fullständigt utvecklat skript språk.

## <a name="powershell-is-open-source"></a>PowerShell är öppen källkod

PowerShell-källkoden är nu tillgänglig i GitHub och är öppen för community-bidrag.
Se [PowerShell-källan på GitHub](https://github.com/powershell/powershell).

Du kan börja med de bitar du behöver med [hjälp av PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
Eller så kanske du får en snabb genom gång på [komma igång](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).

## <a name="powershell-design-goals"></a>Design mål för PowerShell

PowerShell är utformat för att förbättra kommando rads-och skript miljön genom att eliminera problem med lång sikt och lägga till nya funktioner.

### <a name="discoverability"></a>Identifierings möjligheten

Med PowerShell är det enkelt att upptäcka dess funktioner. Om du till exempel vill hitta en lista över cmdletar som visar och ändrar Windows-tjänster skriver du:

```powershell
Get-Command *-Service
```

När du har identifierat vilken cmdlet som utför en aktivitet kan du läsa mer om cmdleten med hjälp av `Get-Help` cmdlet. Om du till exempel vill visa hjälp om cmdleten `Get-Service` skriver du:

```powershell
Get-Help Get-Service
```

De flesta cmdletar returnerar objekt som kan manipuleras och sedan återges som text för visning. För att fullständigt förstå utdata från en cmdlet skickar du utdata till `Get-Member`-cmdlet. Följande kommando visar till exempel information om medlemmar i objektets utdata från `Get-Service`-cmdlet.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Konsekvens

Hantering av system kan vara en komplicerad uppgift. Verktyg som har ett konsekvent gränssnitt hjälper dig att styra den komplicerade komplexiteten. Kommando rads verktyg och COM-objekt (Scriptable Component Object Model) är inte kända för deras konsekvens.

Konsekvensen av PowerShell är en av dess primära till gångar. Om du till exempel lär dig hur du använder `Sort-Object`-cmdleten kan du använda den informationen för att sortera utdata från alla cmdletar. Du behöver inte lära dig de olika sorterings rutinerna för varje cmdlet.

Dessutom behöver inte cmdlet-utvecklare utforma sorterings funktioner för sina cmdlets. PowerShell ger ett ramverk med de grundläggande funktioner som tvingar konsekvens. Ramverket eliminerar några val som finns kvar i utvecklaren. Men i retur gör det mycket enklare att utveckla cmdletar.

### <a name="interactive-and-scripting-environments"></a>Interaktiva miljöer och skript miljöer

Kommando tolken i Windows innehåller ett interaktivt gränssnitt med åtkomst till kommando rads verktyg och grundläggande skript. Windows Script Host (WSH) har skript bara kommando rads verktyg och COM Automation-objekt, men ger inte ett interaktivt gränssnitt.

PowerShell kombinerar ett interaktivt gränssnitt och en skript miljö. PowerShell kan komma åt kommando rads verktyg, COM-objekt och .NET-klass bibliotek. Den här kombinationen av funktioner utökar funktionerna i den interaktiva användaren, skript skrivaren och system administratören.

### <a name="object-orientation"></a>Objekt orientering

PowerShell baseras på objekt som inte är text. Utdata från ett kommando är ett objekt. Du kan skicka objektet utdata via pipelinen till ett annat kommando som indata.

Den här pipelinen ger ett välbekant gränssnitt för personer som har erfarenhet av andra gränssnitt. PowerShell utökar det här konceptet genom att skicka objekt i stället för text.

### <a name="easy-transition-to-scripting"></a>Enkel över gång till skript

PowerShell-kommandots identifiering gör det enkelt att gå över från att skriva kommandon interaktivt för att skapa och köra skript. Med PowerShell-avskrifter och historik kan du enkelt kopiera kommandon till en fil för användning som ett skript.
