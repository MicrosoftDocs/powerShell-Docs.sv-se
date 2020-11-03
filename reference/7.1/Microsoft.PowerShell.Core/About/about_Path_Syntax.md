---
description: Beskriver de fullständiga och relativa Sök vägs namn formaten i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_path_syntax?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Path_Syntax
ms.openlocfilehash: 388ebb6a613f02f71ca630e13d20c9e5ade82d02
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271047"
---
# <a name="about-path-syntax"></a>Om syntax för sökväg

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver de fullständiga och relativa Sök vägs namn formaten i PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

Alla objekt i ett data lager som kan nås via en PowerShell-Provider kan identifieras unikt med hjälp av Sök vägs namnen. Ett Sök vägs namn är en kombination av objekt namn, behållare och under behållare där objektet finns och PowerShell-enheten som behållarna har åtkomst till.

I PowerShell är Sök vägs namn indelade i en av två typer: fullständigt kvalificerade och relativa. Ett fullständigt kvalificerat Sök vägs namn består av alla element som utgör en sökväg. Följande syntax visar elementen i ett fullständigt kvalificerat Sök vägs namn:

```powershell
[<provider>::]<drive>:[\<container>[\<subcontainer>...]]\<item>
```

\<provider\>Plats hållaren refererar till PowerShell-providern som du kan använda för att komma åt data lagret. Till exempel kan du använda fil Systems leverantören för att komma åt filer och kataloger på datorn. Det här elementet i syntaxen är valfritt och behövs inte eftersom enhets namnen är unika för alla leverantörer.

\<drive\>Plats hållaren avser den PowerShell-enhet som stöds av en viss PowerShell-Provider. Vid fil Systems leverantören mappar PowerShell-enheterna till de Windows-enheter som är konfigurerade i systemet. Om systemet t. ex. innehåller enhets-och enhets enhets enhet skapar fil tjänst leverantören samma enheter i PowerShell.

När du har angett enheten måste du ange behållare och under behållare som innehåller objektet. Behållarna måste anges i den hierarkiska ordning som de finns i data lagret. Med andra ord måste du börja med den överordnade behållaren, sedan den underordnade behållaren i den överordnade behållaren och så vidare. Dessutom måste varje behållare föregås av ett omvänt snedstreck. (Observera att PowerShell tillåter att du använder snedstreck för att se kompatibilitet med andra PowerShell.)

När behållaren och under behållare har angetts måste du ange namnet på objektet, föregånget av ett omvänt snedstreck. Till exempel är den fullständigt kvalificerade sökvägen till Shell.dll-filen i katalogen C: \\ Windows \\ system32 följande:

```powershell
C:\Windows\System32\Shell.dll
```

I det här fallet är enheten som behållarna har åtkomst till C: Drive, behållaren på den översta nivån Windows, under behållare är system32 (finns i Windows-behållaren) och objektet är Shell.dll.

I vissa fall behöver du inte ange en fullständigt kvalificerad sökväg och kan istället använda ett relativt Sök vägs namn. Ett relativt Sök vägs namn baseras på den aktuella arbets platsen. Med PowerShell kan du identifiera ett objekt baserat på dess plats i förhållande till den aktuella arbets platsen. Du kan ange relativa Sök vägs namn med hjälp av specialtecken. I följande tabell beskrivs vart och ett av dessa tecken och innehåller exempel på relativa Sök vägs namn och fullständiga Sök vägs namn. Exemplen i tabellen baseras på den aktuella arbets katalogen som angetts till C:\Windows.

|Symbol|Beskrivning               |Relativ sökväg    |Fullständig sökväg          |
|------|--------------------------|-----------------|-------------------|
|.     |Aktuell plats          |.\\ Säker        |c: \\ Windows- \\ system|
|..    |Överordnad för aktuell plats|..\\ Programfiler|c: \\ Program Files  |
|\     |Enhets roten för aktuella     |\\Programfiler  |c: \\ Program Files  |
|      |location                  |                 |                   |
|alternativet|Inga specialtecken     |System           |c: \\ Windows- \\ system|

När du använder ett Sök vägs namn i ett kommando, anger du namnet på samma sätt oavsett om du använder ett fullständigt kvalificerat Sök vägs namn eller en relativ sökväg. Anta till exempel att din aktuella arbets katalog är C:\Windows. Följande Get-ChildItem-kommando hämtar alla objekt i C:\Techdocs-katalogen:

```powershell
Get-ChildItem \techdocs
```

Det omvända snedstrecket anger att enhets roten för den aktuella arbets platsen ska användas. Eftersom arbets katalogen är C: \\ Windows, är enhets roten enheten C:. Eftersom techdocs-katalogen finns utanför roten behöver du bara ange det omvända snedstrecket.

Du kan få samma resultat genom att använda följande kommando:

```powershell
Get-ChildItem c:\techdocs
```

Oavsett om du använder ett fullständigt kvalificerat Sök vägs namn eller ett relativt Sök vägs namn är ett Sök vägs namn viktigt inte bara eftersom det hittar ett objekt, men också eftersom det unikt identifierar objektet även om objektet delar samma namn som ett annat objekt i en annan behållare.

Anta till exempel att du har två filer som är namngivna Results.txt.
Den första filen finns i en katalog med namnet C: \\ techdocs \\ Jan och den andra filen finns i en katalog med namnet c: \\ techdocs \\ feb. Sök vägs namnet för den första filen (C: \\ techdocs \\ Jan \\Results.txt) och sökvägen för den andra filen (c: \\ techdocs \\ feb \\Results.txt) gör att du tydligt kan skilja mellan de två filerna.

## <a name="see-also"></a>SE ÄVEN

[about_Locations](about_Locations.md)

