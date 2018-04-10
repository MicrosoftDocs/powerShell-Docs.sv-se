---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Bilaga 2 Skapa en anpassad PowerShell-genväg
ms.assetid: 5d4fd421-5d43-4ec7-86fd-acfe887b066e
ms.openlocfilehash: e8081b7a64d313c8ef4bbccf95f250445dd68ad9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a>Bilaga 2 – Skapa en anpassad PowerShell-genväg

Följande procedur beskriver hur du skapar en genväg till Windows PowerShell som har flera praktiska alternativ för anpassat.

1. Skapa en genväg som pekar på Powershell.exe.

2. Högerklicka på genvägen och klicka sedan på **egenskaper**.

3. Klicka på den **alternativ** fliken.

4. I den **alternativ** väljer den **här** kryssrutan.

    Den här inställningen kan du markera text i fönstret Windows PowerShell-konsolen genom att dra vänster musknapp och gör det möjligt att kopiera text till Urklipp genom att trycka på RETUR eller genom att högerklicka på med musen.

5. I den **alternativ** väljer den **infogningsläge** kryssrutan. Den här inställningen kan du högerklicka i fönstret för att automatiskt klistra in text från Urklipp.

6. I den **Kommandohistoriken** avsnittet, ange eller välj ett värde mellan 1 och 999 i den **buffertstorlek** rutan. Detta anger antalet skrivna kommandon som sparas i konsolen bufferten.

7. I den **Kommandohistoriken** väljer den **ta bort dubbletter** kryssrutan för att undvika upprepade kommandon från konsolen bufferten.

8. Klicka på den **Layout** fliken.

9. I den **skärmbufferten** avsnittet, ange ett tal mellan 1 och 9999 i den **höjd** rutan. Höjden representerar antalet rader av utdata som är buffrade. Detta är det maximala antalet rader som sparas för att visa när du bläddrar till konsolfönstret. Om det här värdet är lägre än höjden visas i den **fönsterstorlek** avsnittet höjd fönstret storlek minskas automatiskt till samma värde.

10. I den **fönsterstorlek** avsnittet, ange ett tal mellan 1 och 9999 för bredd. Detta motsvarar antalet tecken som visas i konsolfönstret. Standardbredden är 80 och Windows PowerShell-utdata formatering är avsedd för den här bredden.

11. Om du vill placera konsolen vid en viss på skrivbordet när det öppnas, avmarkera den **låta systemet placera fönstret** kryssrutan i den **Fönsterplaceringen** avsnittet och ändra värdena i  **Vänster** och **upp** rutor i den **Fönsterplaceringen** avsnitt.

12. Klicka på **OK**.