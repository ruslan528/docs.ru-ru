---
title: Безопасность свойства зависимости
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers [WPF], access
- wrappers [WPF], security
- dependency properties [WPF], security
- security [WPF], wrappers
- validation [WPF], dependency properties
- dependency properties [WPF], access
- security [WPF], dependency properties
ms.assetid: d10150ec-90c5-4571-8d35-84bafa2429a4
ms.openlocfilehash: d9dd9306980b80f7845c10e8c0ccb59f29821245
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940842"
---
# <a name="dependency-property-security"></a>Безопасность свойства зависимости
Свойства зависимости, как правило, считаются открытыми. Суть системы свойств [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] такова, что дать гарантии безопасности о значении свойства зависимости невозможно.  

<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Доступ к программам-оболочкам и свойствам зависимости и их безопасность  
 Как правило, свойства зависимостей реализуются вместе со свойствами "оболочки" среды CLR, которые упрощают получение или установку свойства из экземпляра. Однако оболочки — это просто удобные методы, реализующие базовые <xref:System.Windows.DependencyObject.GetValue%2A> и <xref:System.Windows.DependencyObject.SetValue%2A> статические вызовы, которые используются при взаимодействии со свойствами зависимостей. С другой стороны, свойства предоставляются в виде свойств среды CLR, которые могут поддерживаться свойством зависимостей, а не закрытым полем. Механизмы безопасности, применяемые к программам-оболочкам, не поддерживают параллели между поведением системы свойств и доступом базового свойства зависимости. Помещение требования безопасности в оболочку будет препятствовать использованию удобного метода, но не предотвратит вызовы <xref:System.Windows.DependencyObject.GetValue%2A> или. <xref:System.Windows.DependencyObject.SetValue%2A> Аналогично: размещение защищенного или закрытого уровня доступа в программе-разработчике не обеспечивает эффективную защиту.  
  
 При написании собственных свойств зависимостей следует объявить оболочки и <xref:System.Windows.DependencyProperty> поле идентификатора как открытые члены, чтобы вызывающие объекты не могли ошибочно получить информацию о истинном уровне доступа этого свойства (из-за того, что хранилище реализуется как свойство зависимостей.  
  
 Для настраиваемого свойства зависимости можно зарегистрировать свойство как свойство зависимостей только для чтения, и это обеспечивает эффективное средство предотвращения установки свойства любым пользователем, который не хранит ссылку <xref:System.Windows.DependencyPropertyKey> на свойство для этого свойства. Дополнительные сведения см. в разделе [Свойства зависимостей "только для чтения"](read-only-dependency-properties.md).  
  
> [!NOTE]
> Объявление поля идентификатора Private не запрещено, и его можно использовать для уменьшения немедленно предоставляемого пространства имен пользовательского класса, но такое свойство не должно рассматриваться как "Private" в том же смысле, что и общий язык. <xref:System.Windows.DependencyProperty> определения языка среды выполнения (среда CLR) определяют этот уровень доступа, по причинам, описанным в следующем разделе.  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>Предоставление системы свойств свойствам зависимости  
 Как правило, он не полезен и является недостоверным, чтобы объявить <xref:System.Windows.DependencyProperty> как любой уровень доступа, отличный от Public. Такая настройка уровня доступа просто лишит возможности получить ссылку на экземпляр из объявляющего класса. Но существует несколько аспектов системы свойств, которые будут возвращать в <xref:System.Windows.DependencyProperty> качестве средства идентификации конкретного свойства в том виде, в каком оно существует в экземпляре класса или экземпляра производного класса, и этот идентификатор по-прежнему можно использовать <xref:System.Windows.DependencyObject.SetValue%2A> в вызове, даже значение, если исходный статический идентификатор объявлен как неоткрытый. Кроме того <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> , виртуальные методы получают сведения о любом существующем свойстве зависимости, которое изменило значение. Кроме того <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> , метод возвращает идентификаторы для любого свойства в экземплярах с локально заданным значением.  
  
### <a name="validation-and-security"></a>Проверка и безопасность  
 Применение спроса к <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> и ожидаемого сбоя проверки при сбое требования, чтобы предотвратить установку свойства, не является адекватным механизмом безопасности. Если вызывающие объекты работают в домене приложения, <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> они также могут подавляться с помощью недействительности Set-value.  
  
## <a name="see-also"></a>См. также

- [Пользовательские свойства зависимостей](custom-dependency-properties.md)
