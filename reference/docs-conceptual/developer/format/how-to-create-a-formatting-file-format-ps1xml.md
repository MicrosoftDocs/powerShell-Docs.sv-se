---
title: Så här skapar du en format fil (. format. ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354959"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>Skapa en formateringsfil (.format.ps1xml)

I det här avsnittet beskrivs hur du skapar en format fil (. format. ps1xml).

> [!NOTE]
> Du kan också skapa en fil för formatering genom att göra en kopia av en av filerna som tillhandahålls av Windows PowerShell. Om du gör en kopia av en befintlig fil tar du bort den befintliga digitala signaturen och lägger till din egen signatur i den nya filen.

### <a name="to-create-a-formatps1xml-file"></a>För att skapa en. format. ps1xml-fil.

1. Skapa en textfil (. txt) med en text redigerare, till exempel Anteckningar.

2. Kopiera följande rader till format filen.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - > Taggarna \<Configuration > \</Configuration definierar rot `Configuration`-noden. Alla ytterligare XML-taggar kommer att stå inom den här noden.

   - <ViewDefinitions></ViewDefinitions> Taggarna definierar `ViewDefinitions`-noden. Alla vyer definieras i den här noden.

3. Spara filen i installationsmappen för Windows PowerShell, till mappen modul eller till en undermapp i mappen modul. Använd följande namn format när du sparar filen: `MyFile.format.ps1xml`. Filer måste använda tillägget `.format.ps1xml`.

   Nu kan du lägga till vyer i format filen. Det finns ingen gräns för hur många vyer som kan definieras i en textfil. Du kan lägga till en enskild vy för varje objekt, flera vyer för samma objekt eller en enskild vy som används av flera objekt.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-formatering och en typ fil](./writing-a-powershell-formatting-file.md)
