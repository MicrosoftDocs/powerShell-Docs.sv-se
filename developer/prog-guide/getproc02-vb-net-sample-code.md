---
title: GetProc02 (VB.NET) exempelkoden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3497546-5b3a-4e29-84ba-cd9747be64b3
caps.latest.revision: 6
ms.openlocfilehash: 821d0dd327529614322e446bfb30d128d1b6a7f3
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056285"
---
# <a name="getproc02-vbnet-sample-code"></a>GetProc02 (VB.NET) – kodexempel

Följande kod visar implementeringen av en `Get-Process` cmdlet som accepterar kommandoradsverktyget indata. Observera att den här implementeringen definierar en `Name` parametern så att kommandoraden indata och använder den [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) metod som utdata mekanism för att skicka utdata objekt till pipelinen.

## <a name="code-sample"></a>Kodexempel

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)