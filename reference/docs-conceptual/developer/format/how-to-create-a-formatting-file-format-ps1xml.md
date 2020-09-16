---
title: Så här skapar du en fil för formatering (.format.ps1XML) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: abdbd4e15b0c4cb1dafcde087d24ed5792c86c3d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781264"
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
