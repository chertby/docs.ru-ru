---
title: Практическое руководство. Переопределение глобальных прокси-серверов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 2389ea01a980f80c7723f9b481ede2e1fe915b28
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624539"
---
# <a name="how-to-override-a-global-proxy-selection"></a>Практическое руководство. Переопределение глобальных прокси-серверов
В этом примере класс **WebRequest** отправляется на веб-сайт `www.contoso.com`, который переопределяет глобальные прокси-серверы прокси-сервером с именем `alternateproxy` на порту 80.  
  
## <a name="example"></a>Пример  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
- Директива [`using` ](~/docs/csharp/language-reference/keywords/using-directive.md) для пространства имен **System.Net**.  
  
## <a name="see-also"></a>См. также

- [Использование протоколов приложений](../../../docs/framework/network-programming/using-application-protocols.md)
- [Доступ к Интернету через прокси-сервер](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
