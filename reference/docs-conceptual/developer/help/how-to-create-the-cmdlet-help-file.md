---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa cmdlet-hjälpfilen
description: Skapa cmdlet-hjälpfilen
ms.openlocfilehash: 40259c8f9496b10380805a78f3711aed6f1bf2e5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659099"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Skapa cmdlet-hjälpfilen

I det här avsnittet beskrivs hur du skapar en giltig XML-fil som innehåller innehåll för Windows PowerShell-cmdlet hjälp avsnitt. I det här avsnittet beskrivs hur du namnger hjälp filen, hur du lägger till lämpliga XML-huvuden och hur du lägger till noder som innehåller de olika avsnitten i hjälp innehållet för cmdleten.

> [!NOTE]
> Om du vill se en fullständig vy över en hjälpfil öppnar du en av `dll-Help.xml` filerna som finns i installations katalogen för Windows PowerShell. Filen innehåller till exempel `Microsoft.PowerShell.Commands.Management.dll-Help.xml` innehåll för flera av PowerShell-cmdletarna.

### <a name="how-to-create-a-cmdlet-help-file"></a>Så här skapar du en cmdlet-hjälpfil

1. Skapa en textfil och spara den med hjälp av UTF8-kodning. Fil namnet måste ha följande format så att Windows PowerShell kan identifiera det som en hjälp fil för cmdlet.

   `<PSSnapInAssemblyName>.dll-Help.xml`

1. Lägg till följande XML-rubriker i text filen. Tänk på att filen kommer att verifieras mot MAML-schemat (Microsoft Assistance Markup Language). För närvarande tillhandahåller PowerShell inga verktyg för att validera filen.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

1. Lägg till en **kommando** nod i cmdlet-hjälpen för varje cmdlet i sammansättningen. Varje nod i **kommando** -noden relaterar till de olika avsnitten i hjälp avsnittet för cmdleten.

   I följande tabell visas XML-elementet för varje nod, följt av en beskrivning av varje nod.

   |           Nod           |                                                                                                     Beskrivning                                                                                                     |
   | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | `<details>`              | Lägger till innehåll för avsnittet namn och sammanfattning i hjälpen för cmdlet. Mer information finns i [så här lägger du till cmdlet-namn och-sammanfattning](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md). |
   | `<maml:description>`     | Lägger till innehåll i BESKRIVNINGs avsnittet i hjälp avsnittet för cmdleten. Mer information finns i [avsnittet så här lägger du till den detaljerade beskrivningen i en cmdlet-hjälpfil](./how-to-add-a-cmdlet-description.md).                    |
   | `<command:syntax>`       | Lägger till innehåll i avsnittet SYNTAX i hjälp avsnittet för cmdlet. Mer information finns i [avsnittet så här lägger du till syntax i en cmdlet-hjälpfil](./how-to-add-syntax-to-a-cmdlet-help-topic.md).                                  |
   | `<command:parameters>`   | Lägger till innehåll för avsnittet parametrar i hjälp avsnittet för cmdlet. Mer information finns i [avsnittet How to Add Parameters to a cmdlet Help](./how-to-add-parameter-information.md).                                  |
   | `<command:inputTypes>`   | Lägger till innehåll för indata-avsnittet i hjälp avsnittet för cmdlet. Mer information finns i [så här lägger du till indatatyper i ett hjälp avsnitt om cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).                        |
   | `<command:returnValues>` | Lägger till innehåll för avsnittet utdata i hjälp avsnittet för cmdlet. Mer information finns i [Hjälp avsnittet så här lägger du till retur värden i en cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).                   |
   | `<maml:alertset>`        | Lägger till innehåll i avsnittet anteckningar i hjälp avsnittet för cmdlet. Mer information finns i [så här lägger du till anteckningar i ett hjälp avsnitt för cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md).                                      |
   | `<command:examples>`     | Lägger till innehåll i avsnittet exempel i hjälp avsnittet för cmdlet. Mer information finns i [så här lägger du till exempel i ett hjälp avsnitt om cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md).                            |
   | `<maml:relatedLinks>`    | Lägger till innehåll i avsnittet relaterade länkar i hjälp avsnittet för cmdleten. Mer information finns i [så här lägger du till relaterade länkar i ett hjälp avsnitt för cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).             |

## <a name="example"></a>Exempel

 Här är ett exempel på en **kommando** nod som innehåller noderna för de olika avsnitten i hjälp avsnittet för cmdleten.

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

 [Lägga till syntax till ett cmdlet-hjälpavsnitt](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Så här lägger du till parametrar i ett hjälp avsnitt för cmdlet](./how-to-add-parameter-information.md)

 [Lägga till indatatyper i ett cmdlet-hjälpavsnitt](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Lägga till returvärden i ett cmdlet-hjälpavsnitt](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Så här lägger du till anteckningar i hjälp avsnittet om cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Lägga till exempel i ett cmdlet-hjälpavsnitt](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)
