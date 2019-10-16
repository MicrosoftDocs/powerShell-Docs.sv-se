---
title: GetProc04 (C#) exempel kod | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: e8d9ae69c0d9da23b3e9a807e30ee76ba83af604
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357171"
---
# <a name="getproc04-c-sample-code"></a>GetProc04 (C#) – kodexempel

Följande kod visar implementeringen av en `Get-Process`-cmdlet som rapporterar att det inte går att avsluta fel. Den här implementeringen anropar metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) för att rapportera att det inte går att avsluta fel.

> [!NOTE]
> Du kan ladda ned C# käll filen (getprov04.CS) för den här get-proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .

## <a name="code-sample"></a>Kod exempel

[!code-csharp[GetProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a>Se även

[Windows PowerShell Programmer ' s guide](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
