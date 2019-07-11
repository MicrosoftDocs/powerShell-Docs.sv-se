---
ms.date: 07/10/2019
keywords: jea, powershell, säkerhet
title: Översikt över precis tillräcklig Administration
ms.openlocfilehash: 4b74e5be9558810748a8844a325c8213e1b3ebc9
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726644"
---
# <a name="just-enough-administration"></a>JEA (Just Enough Administration)

Tillräckligt Administration JEA () är en säkerhetsteknik som möjliggör delegerad administration för allt hanteras av PowerShell. JEA kan du:

- **Minska antalet administratörer på dina datorer** använda virtuella konton eller grupp-hanterade tjänstkonton för att utföra Privilegierade åtgärder för vanliga användare.
- **Begränsa vad användarna kan göra** genom att ange vilka cmdlet: ar, funktioner och externa kommandon de kan köra.
- **Bättre förstå vad användarna gör** med avskrifter och loggar som visar exakt vilka kommandon som en användare som körs under sin session.

**Varför är JEA viktigt?**

Hög behöriga konton som används för att administrera dina servrar utgöra en säkerhetsrisk. Bör en angripare kompromettera något av dessa konton, kan de starta [lateral attacker](https://aka.ms/pth) i hela organisationen. Varje komprometterat konto ger en angripare åtkomst till och med flera konton och resurser, och placerar dem ett steg närmare att stjäla företagets hemligheter, starta en denial of service-attack med mera.

Det är inte alltid lätt att ta bort administrativa privilegier, antingen. Föreställ dig ett vanligt scenario där DNS-rollen är installerad på samma dator som din Active Directory-domänkontrollant. DNS-administratörer kräver lokal administratörsbehörighet för att åtgärda problem med DNS-servern. Om du vill göra det måste du se dem medlemmar i mycket Privilegierade **Domänadministratörer** säkerhetsgrupp. Den här metoden ger ett effektivt sätt DNS-administratörer kontroll över hela domänen och åtkomst till alla resurser på den datorn.

JEA åtgärdar problemet med principen om **lägsta behörighet**. Du kan använda JEA, för att konfigurera en hanteringsslutpunkt för DNS-administratörer som ger dem åtkomst endast till PowerShell-kommandon som de behöver för att utföra sitt jobb. Det innebär att du kan ange lämplig åtkomst att reparera en förgiftat DNS-cache eller starta om DNS-servern utan att ge dem oavsiktligt åtkomstbehörighet till Active Directory, eller att bläddra i filsystemet eller köra potentiellt skadliga skript. Dessutom finns när JEA-sessionen är konfigurerad för att använda tillfälliga Privilegierade virtuella konton, DNS-administratörer kan ansluta till servern med **icke-administratörer** autentiseringsuppgifter och fortfarande kör kommandon som vanligtvis kräver administratör behörigheter för. JEA kan du ta bort användare från mycket Privilegierade lokal/domän-administratörsroller och noggrant kontrollera vad de kan göra på varje dator.

## <a name="next-steps"></a>Nästa steg

Läs mer om kraven för att använda JEA i den [krav](prerequisites.md) artikeln.

## <a name="samples-and-dsc-resource"></a>Exempel och DSC-resurs

Exemplet JEA konfigurationer och JEA DSC-resurs kan hittas i den [JEA GitHub-lagringsplatsen](https://github.com/PowerShell/JEA).
