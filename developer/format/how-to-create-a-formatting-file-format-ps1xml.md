---
title: Så här skapar du en formatering fil (. format.ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851690"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>Skapa en formateringsfil (.format.ps1xml)

Det här avsnittet beskriver hur du skapar en formatering fil (. format.ps1xml).

> [!NOTE]
> Du kan också skapa en formatering fil genom att göra en kopia av en av filerna som tillhandahålls av Windows PowerShell. Om du gör en kopia av en befintlig fil, ta bort den befintliga digitala signaturen och lägga till en egen signatur i den nya filen.

### <a name="to-create-a-formatps1xml-file"></a>Skapa en. format.ps1xml fil.

1. Skapa en textfil (.txt) med hjälp av en text-redigerare till exempel Anteckningar.

2. Kopiera följande rader till filen formatering.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - Den \<Configuration >\</Configuration > taggar definierar roten `Configuration` noden. Alla ytterligare XML-taggar ska stå inom den här noden.

   - Den <ViewDefinitions> </ViewDefinitions> taggar definiera den `ViewDefinitions` noden. Alla vyer har definierats i den här noden.

3. Spara filen till Windows PowerShell-installationsmappen, till modulmappen eller i en undermapp till modulmappen. Använd följande format för namn när du sparar filen: `MyFile.format.ps1xml`. Formatering filer måste använda den `.format.ps1xml` tillägget.

   Du är nu redo att lägga till vyer i filen formatering. Det finns ingen gräns för antal vyer som kan definieras i en fil med formatering. Du kan lägga till en enda vy för varje objekt, flera vyer för samma objekt eller en vy som används av flera objekt.

## <a name="see-also"></a>Se även

[Skriva ett Windows PowerShell formatering och skriver fil](./writing-a-powershell-formatting-file.md)
