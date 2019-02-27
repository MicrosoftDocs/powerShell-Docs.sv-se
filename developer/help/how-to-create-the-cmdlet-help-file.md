---
title: Så här skapar du filen Cmdlet-hjälpavsnitten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848897"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Skapa cmdlet-hjälpfilen

Det här avsnittet beskriver hur du skapar en giltig XML-fil som innehåller innehållet för hjälpavsnitt för Windows PowerShell-cmdlet. Det här avsnittet beskrivs hur du namnger hjälpfilen, hur du lägger till rätt XML-huvuden och hur du lägger till noder som innehåller de olika avsnitten hjälpinnehållet-cmdlet: ens.

> [!NOTE]
> För en fullständig överblick över en hjälpfilen, öppna en av dll-Help.xml-filerna finns i installationskatalogen för Windows PowerShell. Till exempel innehåller filen Microsoft.PowerShell.Commands.Management.dll Help.xml innehåll för flera av Windows PowerShell-cmdlets.

### <a name="how-to-create-a-cmdlet-help-file"></a>Så här skapar du en Cmdlet-hjälpavsnitten-fil

1. Skapa en textfil och spara den UTF8-kodning används. Filnamnet måste ha följande format så att Windows PowerShell kan identifiera den som en cmdlet-hjälpfilen.

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. Lägg till följande XML-huvuden i textfilen. Tänk på att filen kommer att valideras mot flera agenten modellering språk (MAML)-schemat. Windows PowerShell ger för närvarande inte några verktyg för att verifiera filen.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. Lägga till en kommando-nod i hjälpfilen för cmdlet: en för varje cmdlet i sammansättningen. Varje nod under noden kommandot relaterar till de olika avsnitten i cmdlet-hjälpavsnittet.

   I följande tabell visas de XML-elementet för varje nod, följt av en beskrivningar för varje nod.

   |Nod|Beskrivning|
   |----------|-----------------|
   |`<details>`|Lägger till innehåll för avsnitten namn och en sammanfattning av cmdlet-hjälpavsnittet. Mer information finns i [hur du lägger till Cmdlet-namn och sammanfattning](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).|
   |`<maml:description>`|Lägger till innehåll för avsnittet beskrivning i cmdlet-hjälpavsnittet. Mer information finns i [hur du lägger till den detaljerade beskrivningen för en Cmdlet-hjälpavsnittet](./how-to-add-a-cmdlet-description.md).|
   |`<command:syntax>`|Lägger till innehåll för avsnittet SYNTAX i cmdlet-hjälpavsnittet. Mer information finns i [hur du lägger till Syntax för en Cmdlet-hjälpavsnittet](./how-to-add-syntax-to-a-cmdlet-help-topic.md).|
   |`<command:parameters>`|Lägger till innehåll för avsnittet parametrar i cmdlet-hjälpavsnittet. Mer information finns i [hur du lägger till parametrar till en Cmdlet-hjälpavsnittet](./how-to-add-parameter-information.md).|
   |`<command:inputTypes>`|Lägger till innehåll för avsnittet indata i cmdlet-hjälpavsnittet. Mer information finns i [hur du lägger till indata-typer till en Cmdlet-hjälpavsnittet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).|
   |`<command:returnValues>`|Lägger till innehåll för OUTPUTS-avsnittet i cmdlet-hjälpavsnittet. Mer information finns i [hur du lägger till returnera värden till en Cmdlet-hjälpavsnittet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).|
   |`<maml:alertset>`|Lägger till innehåll i avsnittet ANTECKNINGAR i cmdlet-hjälpavsnittet. Mer information finns i [hur du lägger till information till en Cmdlet-hjälpavsnittet](./how-to-add-notes-to-a-cmdlet-help-topic.md).|
   |`<command:examples>`|Lägger till innehåll för avsnittet exempel i cmdlet-hjälpavsnittet. Mer information finns i [så här lägger du till exempel att en Cmdlet-hjälpavsnittet](./how-to-add-examples-to-a-cmdlet-help-topic.md).|
   |`<maml:relatedLinks>`|Lägger till innehåll för avsnittet med länkar i cmdlet-hjälpavsnittet. Mer information finns i [så här lägger du till relaterade länkar till en Cmdlet-hjälpavsnittet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).|

## <a name="example"></a>Exempel

 Här är ett exempel på en kommando-nod som innehåller noder för de olika delarna av cmdlet-hjälpavsnittet.

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a>Se även

 [Hur du lägger till Cmdlet-namn och sammanfattning](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Hur du lägger till den detaljerade beskrivningen för en Cmdlet-hjälpavsnittet](./how-to-add-a-cmdlet-description.md)

 [Lägga till Syntax i en Cmdlet-hjälpavsnittet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Lägga till parametrar i en Cmdlet-hjälpavsnittet](./how-to-add-parameter-information.md)

 [Hur du lägger till Indatatyper en Cmdlet-hjälpavsnittet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Hur du lägger till returvärden för en Cmdlet-hjälpavsnittet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Hur du lägger till information till en Cmdlet-hjälpavsnittet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Hur du lägger till exempel att en Cmdlet-hjälpavsnittet](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Lägga till länkarna till Cmdlet-hjälpavsnittet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)