---
title: RunSpace03 (C#)-kodexemplet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 0e80f4d850a7c6dc044526a56b92f16eea4040b5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081384"
---
# <a name="runspace03-c-code-sample"></a>RunSpace03 (C#) – kodexempel

Här är den C# källkoden för konsolprogrammet som beskrivs i [och skapa en konsolen program som använder ett skript som angetts](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68). Det här exemplet används den [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) klassen för att köra ett skript som hämtar bearbeta information med hjälp av listan över processnamn som skickades till skriptet. Den visar hur du skickar in objekt till ett skript och hur du hämtar felobjekt samt utdata-objekt.

> [!NOTE]
> Du kan ladda ned den C# källfilen (runspace03.cs) för det här exemplet med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter. Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.

## <a name="code-sample"></a>Kodexempel

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)