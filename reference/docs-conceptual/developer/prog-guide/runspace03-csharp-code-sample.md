---
title: Kod exempelC#för RunSpace03 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 49911f2779110c04c0e89f09fdf76ee9cd930edb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352565"
---
# <a name="runspace03-c-code-sample"></a>RunSpace03 (C#) – kodexempel

Här är C# käll koden för konsol programmet som beskrivs i avsnittet "skapa ett konsol program som kör ett angivet skript". I det här exemplet används klassen [system. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) för att köra ett skript som hämtar process information med hjälp av listan över process namn som skickas till skriptet. Den visar hur du skickar indata-objekt till ett skript och hur du hämtar fel objekt samt utgående objekt.

> [!NOTE]
> Du kan ladda ned C# käll filen (runspace03.CS) för det här exemplet med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime Components. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk).
> De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .

## <a name="code-sample"></a>Kod exempel

[!code-csharp[Runspace03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a>Se även

[Windows PowerShell Programmer ' s guide](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)