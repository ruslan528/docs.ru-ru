---
title: Общие сведения о контейнерах и Docker
description: Общий обзор основных преимуществ использования Docker.
ms.date: 02/15/2019
ms.openlocfilehash: a03c67ed4fbc55c84e69fba5b7978863c8305e00
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295051"
---
# <a name="introduction-to-containers-and-docker"></a>Общие сведения о контейнерах и Docker

*Контейнеризация — это подход к разработке программного обеспечения, при котором приложение или служба, их зависимости и конфигурация (абстрактные файлы манифеста развертывания) упаковываются вместе в образ контейнера. Контейнерное приложение можно тестировать как единое целое и развертывать как экземпляр образа контейнера в операционной системе (ОС) узла.*

Так же как обычные контейнеры позволяют перевозить любые грузы на корабле, поезде или грузовике, программные контейнеры выступают в качестве стандартных модулей для развертывания программного обеспечения, которые могут содержать различный код и зависимости. Контейнеризация программного обеспечения позволяет разработчикам и ИТ-специалистам развертывать его в разных средах без каких-либо изменений или с минимальными изменениями.

Контейнеры также изолируют приложения друг от друга в общей операционной системе. Контейнерные приложения выполняются на основе узла контейнеров, который в свою очередь работает в операционной системе (Linux или Windows). Поэтому контейнеры требуют гораздо меньше ресурсов, чем образы виртуальных машин.

Каждый контейнер может вмещать целое веб-приложение или службу, как показано на рис. 1-1. В этом примере узел Docker — это узел контейнеров, а App1, App2, Svc1 и Svc2 — контейнерные приложения или службы.

![Два приложения и две службы, работающие в операционной системе на виртуальной машине или физическом сервере](./media/image1.png)

**Рис. 1-1**. Несколько контейнеров на одном узле

Еще одним преимуществом контейнеризации является масштабируемость. Вы можете быстро осуществлять горизонтальное масштабирование, создавая контейнеры для краткосрочных задач. С точки зрения приложения, создание экземпляра образа (контейнера) аналогично созданию экземпляра процесса, например для службы или веб-приложения. Но для обеспечения надежности при запуске нескольких экземпляров одного образа на нескольких серверах обычно желательно, чтобы контейнеры (экземпляры образа) выполнялись на разных серверах или виртуальных машинах в разных доменах сбоя.

Иными словами, контейнеры предоставляют такие преимущества, как изоляция, переносимость, гибкость, масштабируемость и контроль, на протяжении всего жизненного цикла приложения. Самым важным преимуществом является изоляция среды разработки от рабочей среды.

>[!div class="step-by-step"]
>[Вперед](what-is-docker.md)