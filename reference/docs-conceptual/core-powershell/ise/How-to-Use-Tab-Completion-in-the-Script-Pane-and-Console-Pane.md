---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Använd tabbifyllning i skriptfönstret och konsolfönstret
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: e1f8146b6113a82fd3d857c98550ec2e459715a4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954933"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>Använd tabbifyllning i skriptfönstret och konsolfönstret

Flikavslutande innehåller automatisk hjälp när du skriver i rutan skript eller kommando-rutan. Använd följande steg för att dra nytta av den här funktionen:

## <a name="to-automatically-complete-a-command-entry"></a>Att automatiskt slutföra en kommando-post

I kommando-fönstret eller Skriptfönster Skriv några tecken på ett kommando och tryck på TAB för att markera den önskade slutförande texten. Om flera objekt som börjar med texten som du ursprungligen angav, fortsätter du att trycka på TABB tills objektet visas. Flikavslutande kan hjälpa dig med att skriva en cmdlet-namn, parameternamn, variabelns namn, egenskapsnamn för objektet eller en sökväg till filen.

> [!NOTE]
> I rutan skript Slutför att trycka på TABB automatiskt kommandot endast när du redigerar .ps1, .psd1 eller .psm1-filer. Flikavslutande fungerar helst när du skriver i rutan kommando.

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>Att automatiskt slutföra en post i cmdlet-parameter

Skriv en cmdlet som följd av ett bindestreck i fönstret rutan kommando eller skript och tryck sedan på FLIKEN.

Skriv till exempel `Get-Process -` och sedan på TABB flera gånger för att visa var och en av parametrarna för cmdleten i sin tur.

## <a name="see-also"></a>Se även

- [Introduktion till Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Så här skapar du en PowerShell-fliken](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)