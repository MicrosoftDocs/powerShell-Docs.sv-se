---
ms.date: 06/12/2017
keywords: jea, powershell, säkerhet
title: Översikt över precis tillräcklig Administration
ms.openlocfilehash: c097838fb25a63d42502eebf751c64c537bdd077
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084920"
---
# <a name="just-enough-administration"></a>JEA (Just Enough Administration)

Tillräckligt Administration JEA () är en säkerhetsteknik som möjliggör delegerad administration för allt som kan hanteras med PowerShell.
JEA kan du:

- **Minska antalet administratörer på dina datorer** genom att använda virtuella konton eller gruppen hanterade tjänstkonton som utföra Privilegierade åtgärder för vanliga användare.
- **Begränsa vad användarna kan göra** genom att ange vilka cmdlet: ar, funktioner och externa kommandon de kan köra.
- **Bättre förstå vad användarna gör** med avskrifter och loggar som visar exakt vilka kommandon som en användare som körs under sin session.

**Varför är detta viktigt?**

Hög behöriga konton som används för att administrera dina servrar utgöra en säkerhetsrisk.
Bör en angripare kompromettera något av dessa konton, kan de starta [lateral attacker](http://aka.ms/pth) i hela organisationen.
Varje konto de äventyra kan ge dem åtkomst till och med flera konton och resurser, placera dem ett steg närmare att stjäla företagets hemligheter, starta en denial of service-attack med mera.

Det är inte alltid lätt att ta bort administrativa privilegier, antingen.
Föreställ dig ett vanligt scenario där DNS-rollen är installerad på samma dator som din Active Directory-domänkontrollant.
DNS-administratörer kräver behörighet som lokal administratör att åtgärda problem med DNS-servern, men för att kunna göra så att du behöver göra dem till medlemmar i gruppen med hög behörighetsnivå ”Domänadministratörer”.
Den här metoden ger ett effektivt sätt DNS-administratörer kontroll över hela domänen och åtkomst till alla resurser på den datorn.

JEA hjälper dig att lösa problemet genom att hjälpa dig att anta principen om *lägsta behörighet*.
Du kan konfigurera en hanteringsslutpunkt för DNS-administratörer som ger dem åtkomst till alla PowerShell-kommandon som de behöver för att utföra sitt jobb, men inget mer med JEA.
Det innebär att du kan ange lämplig åtkomst att reparera en förgiftat DNS-cache eller starta om DNS-servern utan att ge dem oavsiktligt åtkomstbehörighet till Active Directory, eller att bläddra i filsystemet eller köra potentiellt skadliga skript.
Dessutom finns när JEA-sessionen är konfigurerad för att använda tillfälliga Privilegierade virtuella konton, DNS-administratörer kan ansluta till servern med *icke-administratörer* autentiseringsuppgifter och fortfarande att kunna köra kommandon som kräver vanligtvis Admin-behörighet.
Den här funktionen kan du ta bort användare från mycket Privilegierade lokal/domän-administratörsroller och istället noggrant kontrollera vad de kan utföra på varje dator.

## <a name="get-started-with-jea"></a>Kom igång med JEA

Du kan börja använda JEA idag på valfri dator som kör Windows Server 2016 eller Windows 10.
Du kan också köra JEA på äldre operativsystem med en uppdatering för Windows Management Framework.
Om du vill veta mer om krav för att använda JEA och lär dig hur du skapar, använder, och granska en JEA-slutpunkt, ta en titt i följande avsnitt:

- [Förutsättningar](prerequisites.md) -förklarar hur du ställer in din miljö för att använda JEA.
- [Rollfunktioner](role-capabilities.md) – beskriver hur du skapar roller som avgör vad en användare tillåts att göra i en JEA-session.
- [Sessionskonfigurationer](session-configurations.md) -förklarar hur du konfigurerar JEA-slutpunkter som mappa användare till roller och JEA-identitet
- [Registrera JEA](register-jea.md) – skapa en JEA-slutpunkt och göra den tillgänglig för användarna att ansluta till.
- [Använda JEA](using-jea.md) – Lär dig de olika sätt som du kan använda JEA.
- [Säkerhetsöverväganden](security-considerations.md) -granska säkerhetsmetoder och konsekvenserna av JEA konfigurationsalternativ.
- [Granska och rapportera i JEA](audit-and-report.md) – Lär dig att granska och rapportera i JEA-slutpunkter.

## <a name="samples-and-dsc-resource"></a>Exempel och DSC-resurs

Exemplet JEA konfigurationer och JEA DSC-resurs kan hittas i den [JEA GitHub-lagringsplatsen](https://github.com/PowerShell/JEA).