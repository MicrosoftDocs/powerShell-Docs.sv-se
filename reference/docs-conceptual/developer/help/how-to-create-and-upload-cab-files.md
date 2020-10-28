---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa och ladda upp CAB-filer
description: Skapa och ladda upp CAB-filer
ms.openlocfilehash: bdcf534f48cff27b403d82440ad4ec6a3212b67d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653890"
---
# <a name="how-to-create-and-upload-cab-files"></a>Skapa och ladda upp CAB-filer

Det här avsnittet beskriver hur du skapar uppdaterings bara CAB-filer för hjälpfiler och laddar upp dem till den plats där de uppdaterings bara hjälp-cmdletar kan hitta dem.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>Skapa och överföra uppdaterings bara CAB-filer för hjälpfiler

Du kan använda funktionen uppdaterbar hjälp för att leverera nya eller uppdaterade hjälpfiler för en modul på flera språk och kulturer. Ett uppdaterings Bart hjälp paket för en modul består av en HelpInfo XML-fil och en eller flera CAB- `.CAB` filer. Varje CAB-fil innehåller hjälpfiler för modulen i en kultur i användar gränssnittet. Använd följande procedur för att skapa CAB-filer för uppdaterings bara hjälp.

1. Organisera hjälpfilerna för modulen efter UI-kultur. Varje uppdaterings bar hjälp-CAB-fil innehåller hjälpfilerna för en modul i en kultur för användar gränssnitt. Du kan leverera flera CAB-filer för modulen, var och en för en annan användar gränssnitts kultur.

1. Kontrol lera att hjälpfilerna bara innehåller de filtyper som tillåts för uppdaterbar hjälp och validera dem mot ett hjälp fils schema. Om `Update-Help` cmdleten påträffar en fil som är ogiltig eller inte är en tillåten typ, installerar den inte den ogiltiga filen och slutar att installera filer från CAB-filen. En lista över tillåtna filtyper finns i [filtyper som tillåts i en uppdaterings bar CAB-fil](./file-types-permitted-in-an-updatable-help-cab-file.md).

1. Signera hjälpfilerna digitalt. Digitala signaturer krävs inte, men de är ett bra tips.

1. Ta med alla hjälpfiler för modulen i användar gränssnitts kulturen, inte bara filer som är nya eller som har ändrats. Om CAB-filen är ofullständig kommer användare som laddar ned hjälpfiler för första gången eller inte hämta alla uppdateringar att ha alla hjälpfiler för modulen.

1. Använd ett verktyg som skapar CAB-filer, till exempel `MakeCab.exe` . PowerShell inkluderar inte cmdletar som skapar CAB-filer.

1. Namnge CAB-filerna. Mer information finns i [så här namnger du en uppdaterings bar CAB-fil](./how-to-name-an-updatable-help-cab-file.md).

1. Ladda upp CAB-filerna för modulen till den plats som anges av **HelpContentUri** -elementet i HelpInfo XML-filen för modulen. Ladda sedan upp XML-filen HelpInfo till den plats som anges av **HelpInfoUri** -nyckeln för modul manifestet. **HelpContentUri** och **HelpInfoUri** kan peka på samma plats.

> [!CAUTION]
> Värdet för **HelpInfoUri** -nyckeln och **HelpContentUri** -elementet måste börja med `http` eller `https` . Värdet måste vara en Internet plats och får inte innehålla ett fil namn.
