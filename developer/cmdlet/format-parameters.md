---
title: Formatera parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 4f24af9b32f785695d156bfb4784aa03c97e8987
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849422"
---
# <a name="format-parameters"></a><span data-ttu-id="5f0a5-102">Formatparametrar</span><span class="sxs-lookup"><span data-stu-id="5f0a5-102">Format Parameters</span></span>

<span data-ttu-id="5f0a5-103">I följande tabell visas rekommenderade namn och funktioner för parametrar som används för att formatera eller för att generera data.</span><span class="sxs-lookup"><span data-stu-id="5f0a5-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

<span data-ttu-id="5f0a5-104">Som datatyp: Nyckelord</span><span class="sxs-lookup"><span data-stu-id="5f0a5-104">As Data type: Keyword</span></span>

<span data-ttu-id="5f0a5-105">Implementera den här parametern om du vill ange formatet för cmdlet-utdata.</span><span class="sxs-lookup"><span data-stu-id="5f0a5-105">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="5f0a5-106">Möjliga värden kan exempelvis vara Text eller skript.</span><span class="sxs-lookup"><span data-stu-id="5f0a5-106">For example, possible values could be Text or Script.</span></span>

<span data-ttu-id="5f0a5-107">Datatypen Binary: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="5f0a5-107">Binary Data type: SwitchParameter</span></span>

<span data-ttu-id="5f0a5-108">Implementera den här parametern om du vill ange att cmdleten hanterar binära värden.</span><span class="sxs-lookup"><span data-stu-id="5f0a5-108">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>

<span data-ttu-id="5f0a5-109">Kodning datatyp: Nyckelord</span><span class="sxs-lookup"><span data-stu-id="5f0a5-109">Encoding Data type: Keyword</span></span>

<span data-ttu-id="5f0a5-110">Implementera den här parametern om du vill ange vilken typ av kodning som stöds.</span><span class="sxs-lookup"><span data-stu-id="5f0a5-110">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="5f0a5-111">Möjliga värden kan exempelvis vara ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte och sträng.</span><span class="sxs-lookup"><span data-stu-id="5f0a5-111">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>

<span data-ttu-id="5f0a5-112">Ny rad datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="5f0a5-112">NewLine Data type: SwitchParameter</span></span>

<span data-ttu-id="5f0a5-113">Implementera den här parametern så att radmatningstecken stöds när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="5f0a5-113">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>

<span data-ttu-id="5f0a5-114">Kortnamn datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="5f0a5-114">ShortName Data type: SwitchParameter</span></span>

<span data-ttu-id="5f0a5-115">Implementera den här parametern så att kortnamn stöds när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="5f0a5-115">Implement this parameter so that short names are supported when the parameter is specified.</span></span>

<span data-ttu-id="5f0a5-116">Bredd datatyp: Int32</span><span class="sxs-lookup"><span data-stu-id="5f0a5-116">Width Data type: Int32</span></span>

<span data-ttu-id="5f0a5-117">Implementera den här parametern så att användaren kan ange bredden på enheten.</span><span class="sxs-lookup"><span data-stu-id="5f0a5-117">Implement this parameter so that the user can specify the width of the output device.</span></span>

<span data-ttu-id="5f0a5-118">Omsluta datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="5f0a5-118">Wrap Data type: SwitchParameter</span></span>

<span data-ttu-id="5f0a5-119">Implementera den här parametern så att radbrytning stöds när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="5f0a5-119">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f0a5-120">Se även</span><span class="sxs-lookup"><span data-stu-id="5f0a5-120">See Also</span></span>

[<span data-ttu-id="5f0a5-121">Cmdlet-parametrarna</span><span class="sxs-lookup"><span data-stu-id="5f0a5-121">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="5f0a5-122">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5f0a5-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="5f0a5-123">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5f0a5-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
