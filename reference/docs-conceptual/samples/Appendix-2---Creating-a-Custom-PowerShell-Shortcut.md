---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Bilaga 2 Skapa en anpassad PowerShell-genväg
description: Följande procedur beskriver hur du skapar en genväg till Windows PowerShell som har flera praktiska alternativ anpassade.
ms.openlocfilehash: abdab517dec1357050bf431b6f2e35311ad49976
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500733"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a>Bilaga 2 – Skapa en anpassad PowerShell-genväg

Följande procedur beskriver hur du skapar en genväg till Windows PowerShell som har flera praktiska alternativ anpassade.

1. Skapa en genväg som pekar på Powershell.exe.

1. Högerklicka på genvägen och klicka sedan på **Egenskaper**.

1. Klicka på fliken **Alternativ**.

1. I avsnittet **Redigera alternativ** markerar du kryss rutan **Snabb redigering** .

    Med den här inställningen kan du välja text i fönstret Windows PowerShell-konsol genom att dra den vänstra mus knappen, så att du kan kopiera text till Urklipp genom att trycka på RETUR eller genom att högerklicka på musen.

1. I avsnittet **Redigera alternativ** markerar du kryss rutan **infognings läge** . Med den här inställningen kan du högerklicka i konsol fönstret för att automatiskt klistra in text från Urklipp.

1. I avsnittet **kommando historik** skriver eller väljer du ett tal mellan 1 och 999 i rutan **Buffertstorlek** . Detta anger antalet skrivna kommandon som ska behållas i-konsolens buffert.

1. I avsnittet **kommando historik** markerar du kryss rutan **ta bort gamla dubbletter** för att ta bort upprepade kommandon från-konsolens buffert.

1. Klicka på fliken **layout** .

1. I avsnittet **skärmlayout** anger du ett tal mellan 1 och 9999 i rutan **höjd** . Höjden representerar antalet rader utdata som buffras. Detta är det maximala antalet rader som behålls för visning när du bläddrar i konsol fönstret. Om det här talet är lägre än den höjd som visas i avsnittet **fönster storlek** , minskas fönstrets storleks höjd automatiskt till samma värde.

1. I avsnittet **fönster storlek** anger du en siffra mellan 1 och 9999 för bredden. Detta representerar antalet tecken som visas i konsol fönstret. Standard bredden är 80 och Windows PowerShell: s utdataformat är utformad för den här bredden.

1. Om du vill placera konsolen vid en viss punkt på Skriv bordet när den öppnas, avmarkerar du kryss rutan **Låt system positions fönstret** i avsnittet **fönster placering** och ändrar sedan värdena i rutorna till **vänster** och **överkant** i avsnittet **fönster placering** .

1. Klicka på **OK**.
