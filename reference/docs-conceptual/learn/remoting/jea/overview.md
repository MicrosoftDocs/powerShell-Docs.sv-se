---
ms.date: 07/10/2019
keywords: Jea, PowerShell, säkerhet
title: Översikt över bara tillräckligt med administration (JEA)
description: JEA är en säkerhets teknik som möjliggör delegerad administration för allt som hanteras av PowerShell.
ms.openlocfilehash: cc1c49960e274b58635c1ca4e6769a54c3c7ded6
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501719"
---
# <a name="just-enough-administration"></a>Precis tillräcklig administration

Bara tillräckligt med administration (JEA) är en säkerhets teknik som möjliggör delegerad administration för allt som hanteras av PowerShell. Med JEA kan du:

- **Minska antalet administratörer på dina datorer** med hjälp av virtuella konton eller grupphanterade tjänst konton för att utföra privilegierade åtgärder för vanliga användares räkning.
- **Begränsa vad användarna kan göra** genom att ange vilka cmdletar, funktioner och externa kommandon som de kan köra.
- **Bättre förstå vad användarna gör** med avskrifter och loggar som visar exakt vilka kommandon en användare utförde under sin session.

**Varför är JEA viktigt?**

Konton med hög privilegier som används för att administrera dina servrar utgör en allvarlig säkerhets risk. Om en angripare kompromettera ett av dessa konton kan de starta [laterala angrepp](https://aka.ms/pth) i hela organisationen. Varje komprometterat konto ger en angripare åtkomst till ännu fler konton och resurser och ger dem ett steg närmare att stjäla företags hemligheter, starta en denial-of-service-attack och mer.

Det är inte alltid lätt att ta bort administratörs behörighet, vare sig. Överväg det vanliga scenariot där DNS-rollen är installerad på samma dator som din Active Directory-domän-styrenhet. Dina DNS-administratörer måste ha lokal administratörs behörighet för att åtgärda problem med DNS-servern. Men för att göra det måste du göra dem till medlemmar i säkerhets gruppen privilegierade **domän administratörer** . Den här metoden ger dig en effektiv kontroll av DNS-administratörer över hela domänen och åtkomst till alla resurser på den datorn.

JEA löser problemet genom principen om **minsta behörighet**. Med JEA kan du konfigurera en hanterings slut punkt för DNS-administratörer som ger dem åtkomst till de PowerShell-kommandon som de behöver för att utföra jobbet. Det innebär att du kan ge rätt åtkomst för att reparera en GIFTAD DNS-cache eller starta om DNS-servern utan att oavsiktligt ge dem behörighet att Active Directory, eller att söka i fil systemet eller köra potentiellt farliga skript. När JEA-sessionen har kon figurer ATS för att använda temporära privilegierade virtuella konton, kan dina DNS-administratörer dessutom ansluta till servern med autentiseringsuppgifter som **inte är administratör** och fortfarande köra kommandon som vanligt vis kräver administratörs behörighet. Med JEA kan du ta bort användare från privilegierade lokala/domän administratörs roller och kontrol lera noga vad de kan göra på varje dator.

## <a name="next-steps"></a>Nästa steg

Mer information om kraven för att använda JEA finns i artikeln [krav](prerequisites.md) .

## <a name="samples-and-dsc-resource"></a>Exempel och DSC-resurs

Exempel på JEA-konfigurationer och JEA DSC-resursen finns i [Jea GitHub-lagringsplatsen](https://github.com/PowerShell/JEA).
