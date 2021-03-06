---
title: Добавление ссылки на службу в решение рабочего процесса
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 641d401fb85ea156f35134f54e54840f20fa4c9d
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116697"
---
# <a name="add-a-service-reference-in-a-workflow-solution"></a>Добавление ссылки на службу в решение рабочего процесса

Добавление ссылки на службу в приложение рабочего процесса работает несколько иначе, чем обычное приложение WCF. Когда вы наберете **ссылку** **Добавить** > службы и укажите URL-адрес службы, загружаются метаданные и создаются пользовательские действия, которые позволяют вызывать эту службу WCF или службу рабочего процесса WCF. После добавления ссылки на службу заново постройте решение, чтобы построить сформированные действия. После этого они отобразятся в области элементов конструктора рабочих процессов. Это будет работать только при добавлении ссылки на службу в рамках решения рабочего процесса. В следующем веб-трансляции показано, как добавить ссылку на службу в других типах проектов: [вызов службы WCF из рабочего процесса в веб-проекте](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow).

При добавлении двух или более ссылок на службы, которые содержат одинаковое имя операции, возникнет проблема. Созданные действия будут вызывать только первую операцию службы. Чтобы обойти эту ошибку, переименуйте операции службы так, чтобы они отличались, или измените имя конфигурации конечной точки в каждом созданном действии.

## <a name="see-also"></a>См. также:

- [Службы рабочих процессов](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Вызов службы WCF из рабочего процесса в веб-проекте](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
