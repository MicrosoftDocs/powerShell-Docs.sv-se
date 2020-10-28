---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa en formateringsfil (.format.ps1xml)
description: Skapa en formateringsfil (.format.ps1xml)
ms.openlocfilehash: 5bbc1ba40bfccf13636abc0f0751938aa724b761
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652008"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>Skapa en formateringsfil (.format.ps1xml)

I det här avsnittet beskrivs hur du skapar en format fil (.format.ps1XML).

> [!NOTE]
> Du kan också skapa en fil för formatering genom att göra en kopia av en av filerna som tillhandahålls av Windows PowerShell. Om du gör en kopia av en befintlig fil tar du bort den befintliga digitala signaturen och lägger till din egen signatur i den nya filen.

### <a name="to-create-a-formatps1xml-file"></a>För att skapa en .format.ps1XML-fil.

1. Skapa en textfil (. txt) med en text redigerare, till exempel Anteckningar.

2. Kopiera följande rader till format filen.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - `<Configuration></Configuration>`Taggarna definierar rotnoden `Configuration` . Alla ytterligare XML-taggar kommer att stå inom den här noden.

   - `<ViewDefinitions></ViewDefinitions>`Taggarna definierar `ViewDefinitions` noden. Alla vyer definieras i den här noden.

3. Spara filen i installationsmappen för Windows PowerShell, till mappen modul eller till en undermapp i mappen modul. Använd följande namn format när du sparar filen:  `MyFile.format.ps1xml` . Filer måste använda `.format.ps1xml` tillägget.

   Nu kan du lägga till vyer i format filen. Det finns ingen gräns för hur många vyer som kan definieras i en textfil. Du kan lägga till en enskild vy för varje objekt, flera vyer för samma objekt eller en enskild vy som används av flera objekt.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-formatering och en typ fil](./writing-a-powershell-formatting-file.md)
