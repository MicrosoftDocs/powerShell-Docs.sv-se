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
# <a name="error-reporting-concepts"></a><span data-ttu-id="de3d0-102">Begrepp relaterade till felrapportering</span><span class="sxs-lookup"><span data-stu-id="de3d0-102">Error Reporting Concepts</span></span>

<span data-ttu-id="de3d0-103">Windows PowerShell innehåller två metoder för rapportering av fel: en mekanism för att *Avsluta fel* och en annan mekanism för *icke-avslutande fel*.</span><span class="sxs-lookup"><span data-stu-id="de3d0-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="de3d0-104">Det är viktigt att din cmdlet rapporterar fel korrekt så att värd programmet som kör dina cmdletar kan reagera på lämpligt sätt.</span><span class="sxs-lookup"><span data-stu-id="de3d0-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="de3d0-105">Cmdleten ska anropa metoden [system. Management. Automation. cmdlet. Throwterminatingerror \*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) när ett fel inträffar som inte tillåter att cmdleten fortsätter att bearbeta sina inobjekt.</span><span class="sxs-lookup"><span data-stu-id="de3d0-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="de3d0-106">Cmdleten ska anropa metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) för att rapportera icke-avslutande fel när cmdleten kan fortsätta att bearbeta indata-objekten.</span><span class="sxs-lookup"><span data-stu-id="de3d0-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="de3d0-107">Båda metoderna ger en fel post som värd programmet kan använda för att undersöka orsaken till felet.</span><span class="sxs-lookup"><span data-stu-id="de3d0-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="de3d0-108">Använd följande rikt linjer för att avgöra om ett fel är ett avslutande eller icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="de3d0-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="de3d0-109">Ett fel är ett avbrotts fel om cmdleten förhindrar att din cmdlet fortsätter bearbeta det aktuella objektet eller bearbetar ytterligare indata-objekt, oavsett innehåll.</span><span class="sxs-lookup"><span data-stu-id="de3d0-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="de3d0-110">Ett fel är ett avbrotts fel om du inte vill att din cmdlet ska fortsätta att bearbeta det aktuella objektet eller några ytterligare indata-objekt, oavsett deras innehåll.</span><span class="sxs-lookup"><span data-stu-id="de3d0-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="de3d0-111">Ett fel är ett avbrotts fel om det inträffar i en cmdlet som inte accepterar eller returnerar ett objekt eller om det förekommer i en cmdlet som accepterar eller returnerar ett objekt.</span><span class="sxs-lookup"><span data-stu-id="de3d0-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="de3d0-112">Ett fel är ett icke-avslutande fel om du vill att din cmdlet ska fortsätta att bearbeta det aktuella objektet och eventuella ytterligare indata-objekt.</span><span class="sxs-lookup"><span data-stu-id="de3d0-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="de3d0-113">Ett fel är ett icke-avslutande fel meddelande om det är relaterat till ett angivet indatamängds objekt eller en delmängd av inobjekten.</span><span class="sxs-lookup"><span data-stu-id="de3d0-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="de3d0-114">Se även</span><span class="sxs-lookup"><span data-stu-id="de3d0-114">See Also</span></span>

[<span data-ttu-id="de3d0-115">System. Management. Automation. cmdlet. Throwterminatingerror \*</span><span class="sxs-lookup"><span data-stu-id="de3d0-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="de3d0-116">System. Management. Automation. cmdlet. WriteError</span><span class="sxs-lookup"><span data-stu-id="de3d0-116">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="de3d0-117">Windows PowerShell-felposter</span><span class="sxs-lookup"><span data-stu-id="de3d0-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="de3d0-118">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="de3d0-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
