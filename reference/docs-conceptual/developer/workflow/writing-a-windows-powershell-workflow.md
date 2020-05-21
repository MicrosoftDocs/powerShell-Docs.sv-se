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
ms.openlocfilehash: 0f8a9938a1685e9abc2f1dbfb18c3b2b9008d9be
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564934"
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

- [Lägga till Windows PowerShell-aktiviteter till Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [Skapa ett arbetsflöde med Windows PowerShell-aktiviteter](./creating-a-workflow-with-windows-powershell-activities.md)

- [Skapa ett arbetsflöde med hjälp av ett Windows PowerShell-skript](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [Importera och anropa ett Windows PowerShell-arbetsflöde](./importing-and-invoking-a-windows-powershell-workflow.md)

- [Skapa en arbetsflödesaktivitet från en Windows PowerShell-cmdlet](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)
