---
title: Så här skapar du cmdlet-hjälp filen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353265"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Skapa cmdlet-hjälpfilen

I det här avsnittet beskrivs hur du skapar en giltig XML-fil som innehåller innehåll för Windows PowerShell-cmdlet hjälp avsnitt. I det här avsnittet beskrivs hur du namnger hjälp filen, hur du lägger till lämpliga XML-huvuden och hur du lägger till noder som innehåller de olika avsnitten i hjälp innehållet för cmdleten.

> [!NOTE]
> Om du vill se en fullständig vy över en hjälpfil öppnar du en av dll-Help. XML-filerna som finns i installations katalogen för Windows PowerShell. Till exempel innehåller filen Microsoft. PowerShell. commands. Management. dll-Help. XML innehåll för flera av Windows PowerShell-cmdlets.

### <a name="how-to-create-a-cmdlet-help-file"></a>Så här skapar du en cmdlet-hjälpfil

1. Skapa en textfil och spara den med hjälp av UTF8-kodning. Fil namnet måste ha följande format så att Windows PowerShell kan identifiera det som en hjälp fil för cmdlet.

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. Lägg till följande XML-rubriker i text filen. Tänk på att filen kommer att verifieras mot MAML-schemat (Multi-agent Modeling Language). För närvarande tillhandahåller Windows PowerShell inga verktyg för att validera filen.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. Lägg till en kommando nod i cmdlet-hjälpen för varje cmdlet i sammansättningen. Varje nod i kommando-noden relaterar till de olika avsnitten i hjälp avsnittet för cmdleten.

   I följande tabell visas XML-elementet för varje nod, följt av en beskrivning av varje nod.

   |Nodfel|Beskrivning|
   |----------|-----------------|
   |`<details>`|Lägger till innehåll för avsnittet namn och sammanfattning i hjälpen för cmdlet. Mer information finns i [så här lägger du till cmdlet-namn och-sammanfattning](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).|
   |`<maml:description>`|Lägger till innehåll i BESKRIVNINGs avsnittet i hjälp avsnittet för cmdleten. Mer information finns i [avsnittet så här lägger du till den detaljerade beskrivningen i en cmdlet-hjälpfil](./how-to-add-a-cmdlet-description.md).|
   |`<command:syntax>`|Lägger till innehåll i avsnittet SYNTAX i hjälp avsnittet för cmdlet. Mer information finns i [avsnittet så här lägger du till syntax i en cmdlet-hjälpfil](./how-to-add-syntax-to-a-cmdlet-help-topic.md).|
   |`<command:parameters>`|Lägger till innehåll för avsnittet parametrar i hjälp avsnittet för cmdlet. Mer information finns i [avsnittet How to Add Parameters to a cmdlet Help](./how-to-add-parameter-information.md).|
   |`<command:inputTypes>`|Lägger till innehåll för indata-avsnittet i hjälp avsnittet för cmdlet. Mer information finns i [så här lägger du till indatatyper i ett hjälp avsnitt om cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).|
   |`<command:returnValues>`|Lägger till innehåll för avsnittet utdata i hjälp avsnittet för cmdlet. Mer information finns i [Hjälp avsnittet så här lägger du till retur värden i en cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).|
   |`<maml:alertset>`|Lägger till innehåll i avsnittet anteckningar i hjälp avsnittet för cmdlet. Mer information finns i [så här lägger du till anteckningar i ett hjälp avsnitt för cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md).|
   |`<command:examples>`|Lägger till innehåll i avsnittet exempel i hjälp avsnittet för cmdlet. Mer information finns i [så här lägger du till exempel i ett hjälp avsnitt om cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md).|
   |`<maml:relatedLinks>`|Lägger till innehåll i avsnittet relaterade länkar i hjälp avsnittet för cmdleten. Mer information finns i [så här lägger du till relaterade länkar i ett hjälp avsnitt för cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).|

## <a name="example"></a>Exempel

 Här är ett exempel på en kommando nod som innehåller noderna för de olika avsnitten i hjälp avsnittet för cmdleten.

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

 [Så här lägger du till cmdlet-namn och-sammanfattning](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Så här lägger du till den detaljerade beskrivningen i ett hjälp avsnitt för cmdlet](./how-to-add-a-cmdlet-description.md)

 [Så här lägger du till syntax i ett cmdlet-hjälp ämne](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Så här lägger du till parametrar i ett hjälp avsnitt för cmdlet](./how-to-add-parameter-information.md)

 [Så här lägger du till indatatyper i ett hjälp avsnitt för cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Så här lägger du till retur värden i ett cmdlet-hjälp avsnitt](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Så här lägger du till anteckningar i hjälp avsnittet om cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Så här lägger du till exempel i ett hjälp avsnitt för cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Så här lägger du till relaterade länkar i ett hjälp avsnitt för cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)