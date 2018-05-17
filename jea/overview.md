---
ms.date: 06/12/2017
keywords: jea powershell säkerhet
title: Översikt över Just Enough Administration
ms.openlocfilehash: 3dae8b31d4d13ff9033803035c870c02fc7c38ca
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="just-enough-administration"></a>JEA (Just Enough Administration)

Bara tillräckligt Administration JEA () är en säkerhetsteknik som möjliggör delegerad administration för sådant som kan hanteras med PowerShell.
Med JEA kan du:

- **Minska antalet administratörer på dina datorer** hanterade tjänstkonton som utföra Privilegierade åtgärder för vanliga användare genom att utnyttja virtuella konton eller grupp.
- **Begränsa vad användarna kan göra** genom att ange vilka cmdlets, funktioner och externa kommandon kan de köra.
- **Bättre förstå vad användarna gör** med betyg och -loggarna som visar exakt vilka kommandon som en användare som körs under sin session.

**Varför är detta viktigt?**

Mycket Privilegierade konton som används för att administrera dina servrar utgöra en säkerhetsrisk.
Bör en angripare kompromettera något av dessa konton, kan de starta [lateral attacker](http://aka.ms/pth) inom organisationen.
Varje konto de angripa kan ge dem åtkomst till flera konton och resurser, placerar dem även ett steg närmare stjäla företagets hemligheter, starta en denial of service-attack med mera.

Det är inte alltid enkelt ta antingen bort administrativa privilegier.
Överväg att ett vanligt scenario där DNS-serverrollen installeras på samma dator som din Active Directory-domänkontrollant.
DNS-administratörer kräver lokal administratörsbehörighet för att åtgärda problem med DNS-servern, men för att göra så att du behöver göra dem till medlemmar i säkerhetsgruppen för mycket Privilegierade ”Domänadministratörer”.
Den här metoden ger effektivt DNS-administratörer kontroll över hela domänen och åtkomst till alla resurser på den datorn.

JEA kan du lösa det här problemet genom att hjälpa dig fatta principen om *minsta privilegium*.
Du kan konfigurera en slutpunkt för hantering med JEA för DNS-administratörer som ger dem åtkomst till alla PowerShell-kommandon som de behöver för att utföra sitt jobb, men inget mer.
Det innebär att du kan ange lämplig åtkomst att reparera en förgiftade DNS-cache eller starta om DNS-servern utan att oavsiktligt ge dem behörighet till Active Directory eller för att bläddra i filsystemet eller potentiellt skadliga skript körs.
Ännu bättre är när JEA sessionen är konfigurerad för att använda tillfälliga Privilegierade virtuella konton, DNS-administratörer kan ansluta till en server med hjälp av *icke-administratörer* autentiseringsuppgifter och fortfarande att kunna köra kommandon som kräver vanligen Admin-privilegier.
Den här funktionen kan du ta bort användare från mycket Privilegierade lokala/domän-administratörsroller och istället noggrant styra vad de kan göra på varje dator.

## <a name="get-started-with-jea"></a>Kom igång med JEA

Du kan börja använda JEA idag på en dator som kör Windows Server 2016 eller Windows 10.
Du kan också köra JEA på äldre operativsystem med en uppdatering för Windows Management Framework.
Om du vill lära dig mer om krav för att använda JEA och lär dig hur du skapar, använder, och granska en JEA slutpunkt, ta en titt i följande avsnitt:

- [Krav för](prerequisites.md) -förklarar hur du konfigurerar miljön att använda JEA.
- [Funktioner för rollen](role-capabilities.md) -förklarar hur du skapar roller som avgör vad en användare som tillåts i en JEA-session.
- [Sessionskonfigurationer](session-configurations.md) -förklarar hur du konfigurerar JEA slutpunkter som mappar användare till roller och definiera JEA identiteten
- [Registrera JEA](register-jea.md) – skapa en JEA slutpunkt och göra den tillgänglig för användare att ansluta till.
- [Med hjälp av JEA](using-jea.md) -Läs de olika sätt som du kan använda JEA.
- [Säkerhetsaspekter](security-considerations.md) -granska Metodtips om säkerhet och konsekvenser angående JEA konfigurationsalternativ.
- [Granska och rapportera om JEA](audit-and-report.md) – Lär dig hur du granskar och rapportera om JEA slutpunkter.

## <a name="samples-and-dsc-resource"></a>Exemplen och DSC-resurs

Exempel JEA konfigurationer och JEA DSC-resursen finns i den [JEA GitHub-lagringsplatsen](https://github.com/PowerShell/JEA).