---
title: Skriva ett Windows PowerShell-arbetsflöde | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356632"
---
# <a name="writing-a-windows-powershell-workflow"></a>Skriva ett Windows PowerShell-arbetsflöde

Du kan skapa ett XAML-arbetsflöde genom att lägga till aktiviteter som exponeras av Windows PowerShell-sammansättningar i arbetsflödesdesignern i Visual Studio. Följande Windows PowerShell-sammansättningar exponerar arbets flöde – aktiverade aktiviteter.

> [!IMPORTANT]
> Ett XAML-arbetsflöde måste paketeras som en modul om du vill ge hjälp för arbets flödet. Information om moduler finns i [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).

- [Microsoft. PowerShell.-aktiviteter](/dotnet/api/Microsoft.PowerShell.Activities)

- [Microsoft. PowerShell. Core. Activities](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [Microsoft. PowerShell. Diagnostics.-aktiviteter](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [Microsoft. PowerShell. Management. Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [Microsoft. PowerShell. Security. Activities](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [Microsoft. PowerShell. Utility.-aktiviteter](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  I följande avsnitt beskrivs hur du skapar ett arbets flöde med hjälp av Windows PowerShell-aktiviteter.

- [Lägga till Windows PowerShell-aktiviteter i Visual Studio-verktygslådan](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [Skapa ett arbets flöde med Windows PowerShell-aktiviteter](./creating-a-workflow-with-windows-powershell-activities.md)

- [Skapa ett arbets flöde med hjälp av ett Windows PowerShell-skript](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [Importera och anropa ett Windows PowerShell-arbetsflöde](./importing-and-invoking-a-windows-powershell-workflow.md)

- [Skapa en arbets flödes aktivitet från en Windows PowerShell-cmdlet](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)