---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Bilaga 2 Skapa en anpassad PowerShell-genväg
ms.openlocfilehash: 6f1a6a8187b1797103e3620b2cf9155978807ea5
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030300"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a>Bilaga 2 – Skapa en anpassad PowerShell-genväg

Följande procedur beskriver hur du skapar en genväg till Windows PowerShell som har flera praktiska alternativ för anpassade.

1. Skapa en genväg som pekar på Powershell.exe.

2. Högerklicka på genvägen och klicka sedan på **egenskaper**.

3. Klicka på den **alternativ** fliken.

4. I den **redigeringsalternativ** väljer den **Snabbredigering** markerar du kryssrutan.

    Den här inställningen kan du välja text i Windows PowerShell-konsolfönster genom att dra vänster musknapp och den kan du kopiera text till Urklipp genom att trycka på RETUR eller genom att högerklicka på musen.

5. I den **redigeringsalternativ** väljer den **infogningsläge** markerar du kryssrutan. Den här inställningen kan du högerklicka i konsolfönstret för att automatiskt klistra in text från Urklipp.

6. I den **Kommandohistorik** avsnittet anger eller väljer ett tal mellan 1 och 999 i den **buffertstorleken** box. Detta anger antalet skrivna kommandon som sparas i konsolen buffert.

7. I den **Kommandohistorik** väljer den **ta bort dubbletter** kryssrutan för att undvika upprepade kommandon från konsolen bufferten.

8. Klicka på den **Layout** fliken.

9. I den **skärmbufferten** Skriv ett tal mellan 1 och 9999 i den **höjd** box. Höjd representerar antalet rader med utdata som är buffrade. Det här är det maximala antalet rader som kvarhålls för att visa när du bläddrar igenom konsolfönstret. Om det här värdet är lägre än höjden visas i den **fönsterstorlek** avsnittet fönstret storlek höjden minskas automatiskt till samma värde.

10. I den **fönsterstorlek** Skriv ett tal mellan 1 och 9999 för bredd. Detta representerar antalet tecken som visas i konsolfönstret. Standardbredden är 80 och Windows PowerShell-utdata formatering är avsedd för den här bredden.

11. Om du vill placera konsolen vid en viss på skrivbordet när den öppnas, avmarkera de **låta systemet placera fönstret** kryssrutan i den **fönstret position** , och sedan ändra värdena i  **Vänster** och **upp** rutorna i den **fönstret position** avsnittet.

12. Klicka på **OK**.
