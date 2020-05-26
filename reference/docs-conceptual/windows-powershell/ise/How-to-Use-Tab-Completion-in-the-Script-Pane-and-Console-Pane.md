---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Använd tabbifyllning i skriptfönstret och konsolfönstret
ms.openlocfilehash: 07cf9ff75db8d33ed018542153bfcd7503035e40
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810297"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>Använd tabbifyllning i skriptfönstret och konsolfönstret

Ifyllning av flikar ger automatisk hjälp när du skriver i skript fönstret eller i kommando fönstret. Använd följande steg för att dra nytta av den här funktionen:

## <a name="to-automatically-complete-a-command-entry"></a>Så här slutför du en kommando post automatiskt

Skriv några tecken i ett kommando i kommando fönstret eller skript rutan och tryck sedan på <kbd>TABB</kbd> för att välja önskad slut för ande text. Om flera objekt börjar med texten som du ursprungligen skrev in, fortsätter du att trycka på <kbd>TABB</kbd> tills det önskade objektet visas. TABB-slutförande kan hjälpa dig att skriva ett cmdlet-namn, parameter namn, variabel namn, objekt egenskaps namn eller en fil Sök väg.

> [!NOTE]
> När du trycker på <kbd>fliken</kbd> i skript fönstret utförs automatiskt ett kommando när du redigerar `.ps1` , `.psd1` eller `.psm1` filer. TABB-slutförande fungerar när som helst när du skriver i kommando fönstret.

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>Så här slutför du en cmdlet-parameter post automatiskt

I kommando fönstret eller skript rutan skriver du en cmdlet följt av ett streck och trycker sedan på <kbd>TABB</kbd>.

Skriv till exempel `Get-Process -` och tryck på <kbd>TABB</kbd> flera gånger för att visa var och en av parametrarna för cmdleten i tur och retur.

## <a name="see-also"></a>Se även

- [Vi presenterar Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Så här skapar du en PowerShell-flik](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
