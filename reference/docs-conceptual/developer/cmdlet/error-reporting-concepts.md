---
title: Koncept för fel rapportering | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.openlocfilehash: ff010bbe1a87daa351ec13ed249ffc899781a8c3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774515"
---
# <a name="error-reporting-concepts"></a>Begrepp relaterade till felrapportering

Windows PowerShell innehåller två metoder för rapportering av fel: en mekanism för att *Avsluta fel* och en annan mekanism för *icke-avslutande fel*. Det är viktigt att din cmdlet rapporterar fel korrekt så att värd programmet som kör dina cmdletar kan reagera på lämpligt sätt.

Cmdleten ska anropa metoden [system. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) när ett fel inträffar som inte tillåter att cmdleten fortsätter att bearbeta sina inobjekt. Cmdleten ska anropa metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) för att rapportera icke-avslutande fel när cmdleten kan fortsätta att bearbeta indata-objekten. Båda metoderna ger en fel post som värd programmet kan använda för att undersöka orsaken till felet.

Använd följande rikt linjer för att avgöra om ett fel är ett avslutande eller icke-avslutande fel.

- Ett fel är ett avbrotts fel om cmdleten förhindrar att din cmdlet fortsätter bearbeta det aktuella objektet eller bearbetar ytterligare indata-objekt, oavsett innehåll.

- Ett fel är ett avbrotts fel om du inte vill att din cmdlet ska fortsätta att bearbeta det aktuella objektet eller några ytterligare indata-objekt, oavsett deras innehåll.

- Ett fel är ett avbrotts fel om det inträffar i en cmdlet som inte accepterar eller returnerar ett objekt eller om det förekommer i en cmdlet som accepterar eller returnerar ett objekt.

- Ett fel är ett icke-avslutande fel om du vill att din cmdlet ska fortsätta att bearbeta det aktuella objektet och eventuella ytterligare indata-objekt.

- Ett fel är ett icke-avslutande fel meddelande om det är relaterat till ett angivet indatamängds objekt eller en delmängd av inobjekten.

## <a name="see-also"></a>Se även

[System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell-felposter](./windows-powershell-error-records.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
