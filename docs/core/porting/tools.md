---
title: Инструменты для переноса в .NET Core
description: Дополнительные сведения о некоторых инструментах, которые можно использовать для переноса в .NET Core
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 3b71c31b4f26b278b2bd1088adc8e9f64d28ab7b
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215200"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>Инструменты для переноса в .NET Core

Инструменты в этой статье помогут вам при переносе:

- [Анализатор переносимости .NET](../../standard/analyzers/portability-analyzer.md) — цепочка инструментов, создающих отчеты о переносимости кода между .NET Framework и .NET Core:
  - как [программа командной строки](https://github.com/Microsoft/dotnet-apiport/releases);
  - как [расширение Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).
- [Анализатор API .NET](../../standard/analyzers/api-analyzer.md) — анализатор на основе Roslyn выявляет риски совместимости для API на языке C# на разных платформах, а также отслеживает вызовы устаревших API.

Кроме того, можно попытаться перенести более мелкие решения или отдельные проекты в формат файла проекта .NET Core с помощью средства [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017).

> [!WARNING] 
> CsprojToVs2017 — это стороннее средство. Нет никакой гарантии, что оно будет поддерживать все проекты. Кроме того, оно может вызвать незначительные изменения в ожидаемом поведении. CsprojToVs2017 следует использовать в качестве _начальной точки_, которая автоматизирует соответствующие основные процессы. Это решение не может гарантировать перенос форматов файлов проекта.
