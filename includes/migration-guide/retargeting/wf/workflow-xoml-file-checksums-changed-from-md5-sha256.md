---
ms.openlocfilehash: 19e0524f4d40517f3e305b2397e628e0478da8f9
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803488"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a>Контрольные суммы файла XOML рабочего процесса переведены с MD5 на SHA256

|   |   |
|---|---|
|Подробные сведения|Для поддержки отладки рабочих процессов на основе XOML с помощью Visual Studio при сборке проектов рабочих процессов, содержащих файлы XOML, контрольная сумма содержимого файла XOML включается в сгенерированный код как значение <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType>. В .NET Framework 4.7.2 и более ранних версий для хэширования этой контрольной суммы использовался алгоритм MD5, что приводило к проблемам в системах с поддержкой стандарта FIPS. Начиная с .NET Framework 4.8 используется алгоритм SHA256. Для совместимости с WorkflowMarkupSourceAttribute.MD5Digest используются только первые 16 байт сгенерированной контрольной суммы. Это может приводить к проблемам при отладке. Может потребоваться повторная сборка проекта.|
|Предложение|Если повторная сборка проекта не помогла решить проблему, попробуйте задать для параметра <code>AppContext</code> &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; значение true. В коде:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>Или в файле конфигурации (это должен быть файл MSBuild.exe.config для используемой программы MSBuild.exe):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Область|Дополнительный номер|
|Версия|4.8|
|Тип|Изменение целевой платформы|

