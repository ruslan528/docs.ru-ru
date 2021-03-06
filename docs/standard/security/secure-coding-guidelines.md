---
title: Рекомендации по обеспечению безопасного написания кода для .NET
ms.date: 06/28/2018
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET], security
- code security, options
- security-neutral code
- security [.NET], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
ms.openlocfilehash: 51f835803cc545e2a9982c1c8a90d0c998c2bcb8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705916"
---
# <a name="secure-coding-guidelines"></a>Рекомендации по безопасному написанию кода

Защита на основе фактических данных и управление доступом для кода предоставляют очень мощные, четкие механизмы для обеспечения безопасности. Большая часть кода приложения может просто использовать инфраструктуру, реализованную в .NET. В некоторых случаях требуется дополнительная защита на уровне приложения, построенная либо путем расширения системы, либо с помощью новых специальных методов.

Используя принудительные разрешения .NET и другие средства обеспечения безопасности в коде, следует возводить барьеры, чтобы предотвратить доступ вредоносного кода к информации, которую не нужно использовать, или выполнить другие нежелательные действия. Кроме того, необходимо соблюсти баланс между безопасностью и удобством использования во всех планируемых сценариях с использованием доверенного кода.

В этом обзоре описываются различные способы разработки кода, взаимодействующего с системой безопасности.

## <a name="securing-resource-access"></a>Защита доступа к ресурсам

При разработке и написания кода необходимо защитить и ограничить доступ данного кода к ресурсам, особенно при использовании или вызове кода неизвестного происхождения. Убедиться, что ваш код является безопасным, можно с помощью следующих методов.

- Не используйте управление доступом для кода (CAS).

- Не используйте частично доверенный код.

- Не используйте атрибут [алловпартиаллитрустедкаллер](xref:System.Security.AllowPartiallyTrustedCallersAttribute) (APTCA).

- Не используйте удаленное взаимодействие .NET.

- Не используйте модель DCOM.

- Не используйте двоичные модули форматирования.

Безопасность доступа к коду и прозрачный для системы безопасности код не поддерживаются в качестве границы безопасности с частично доверенным кодом. Мы не рекомендуем загружать и выполнять код из неизвестных источников, не предприняв дополнительные меры безопасности. Ниже приведены дополнительные меры безопасности.

- Виртуализация

- Контейнеры AppContainer

- Пользователи операционной системы (ОС) и разрешения

- Контейнеры Hyper-V

## <a name="security-neutral-code"></a>Код, нейтральный к безопасности

Нейтральный код не взаимодействует явным образом с системой безопасности. Он работает с любыми полученными разрешениями. Хотя приложения, которые не перехватывают исключения безопасности, связанные с защищенными операциями (например, использование файлов, сети и т. д.), могут привести к необработанному исключению, код, нейтральный к безопасности, по-прежнему использует преимущества технологий безопасности в .NET. .

Библиотека нейтрального кода имеет особенности, которые следует понимать. Предположим, что библиотека предоставляет элементы API, которые используют файлы или вызывают неуправляемый код. Если код не имеет соответствующего разрешения, он не будет выполняться, как описано. Однако даже если код имеет разрешения, вызывающий его код приложения должен иметь те же разрешения, чтобы он мог работать. Если вызывающий код не имеет нужных разрешений, <xref:System.Security.SecurityException> появляется в результате анализа стека управления доступом для кода.

## <a name="application-code-that-isnt-a-reusable-component"></a>Код приложения, который не является повторно используемым компонентом

Если код является частью приложения, которое не будет вызываться другим кодом, обеспечение безопасности является простым, а специальное кодирование может не требоваться. Однако помните, что вредоносный код может вызвать ваш код. Хотя управление доступом для кода может предотвратить доступ вредоносного кода к ресурсам, такой код все еще может считывать значения полей или свойств, которые могут содержать конфиденциальные сведения.

Кроме того, если код принимает ввод пользователя из Интернета или других ненадежных источников, будьте осторожны, чтобы не были введены вредоносные данные.

## <a name="managed-wrapper-to-native-code-implementation"></a>Реализация управляемой оболочки в машинный код

Обычно в этом сценарии некоторые полезные функции реализуются в машинном коде, который требуется сделать доступным для управляемого кода. Управляемые оболочки легко создаются с помощью вызова неуправляемого кода или COM-взаимодействия. Однако если это сделать, для успешного выполнения вызывающим ваши оболочки объектам необходимо предоставить права на неуправляемый код. В разделе Политика по умолчанию это означает, что код, скачанный из интрасети или Интернета, не будет работать с оболочками.

Вместо предоставления прав на неуправляемый код для всех приложений, использующих эти оболочки, лучше предоставить эти права только коду оболочки. Если эта базовая функциональность не предоставляет никакие ресурсы и реализация также безопасна, оболочке достаточно просто объявить свои права, что позволяет любому коду вызывать ее. При использовании ресурсов написание безопасного кода должно быть таким же, как в случае кода библиотеки, описанного в следующем разделе. Поскольку оболочка потенциально предоставляет вызывающим объектам доступ к этим ресурсам, необходима тщательная проверка безопасности машинного кода, за которую отвечает оболочка.

## <a name="library-code-that-exposes-protected-resources"></a>Код библиотеки, предоставляющий защищенные ресурсы

Следующий подход является наиболее мощным и, следовательно, потенциально опасным (при неправильном завершении) для написания кода безопасности. Библиотека выступает в качестве интерфейса для другого кода, чтобы получить доступ к определенным ресурсам, которые не доступны иным образом, точно так же, как классы .NET применяются разрешения для используемых ресурсов. При предоставлении доступа к ресурсу код должен сначала запросить соответствующее разрешение на ресурс (т. е. он должен выполнить проверку безопасности), а затем объявить свои права на выполнение текущей операции.

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Обеспечение безопасности данных](securing-state-data.md)|Описание порядка защиты закрытых членов.|
|[Безопасность и ввод данных пользователем](security-and-user-input.md)|Вопросы безопасности для приложений, которые принимают пользовательский ввод.|
|[Безопасность и конфликты](security-and-race-conditions.md)|Описывается, как избежать состояний соперничества в коде.|
|[Безопасность и создание кода "на лету"](security-and-on-the-fly-code-generation.md)|Вопросы безопасности для приложений, создающих динамический код.|
|[Безопасность на основе ролей](role-based-security.md)|Подробное описание безопасности на основе ролей в .NET и инструкции по его использованию в коде.|
