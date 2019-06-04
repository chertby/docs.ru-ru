---
title: Синтаксис, используемый свойством DebugView (C#)
description: В этой статье описывается специальный синтаксис, используемый свойством DebugView для получения строкового представления деревьев выражений.
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: de82a738430cdd37c4905a5ae7da5faeb46f00a4
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196370"
---
# <a name="debugview-syntax"></a><span data-ttu-id="8db67-103">Синтаксис `DebugView`</span><span class="sxs-lookup"><span data-stu-id="8db67-103">`DebugView` syntax</span></span>

<span data-ttu-id="8db67-104">Свойство `DebugView` (доступно только при отладке) предоставляет строковое представление деревьев выражений.</span><span class="sxs-lookup"><span data-stu-id="8db67-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="8db67-105">Большая часть синтаксиса достаточно проста для понимания; особые случаи описаны в разделах ниже.</span><span class="sxs-lookup"><span data-stu-id="8db67-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="8db67-106">Каждый пример сопровождается комментарием с `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="8db67-106">Each example is followed by a block comment, containing the `DebugView`.</span></span> 

## <a name="parameterexpression"></a><span data-ttu-id="8db67-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="8db67-107">ParameterExpression</span></span> 

<span data-ttu-id="8db67-108">В начале имен переменных <xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> отображается символ `$`.</span><span class="sxs-lookup"><span data-stu-id="8db67-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a `$` symbol at the beginning.</span></span>
  
<span data-ttu-id="8db67-109">Если параметр не имеет имени, оно назначается автоматически, например `$var1` или `$var2`.</span><span class="sxs-lookup"><span data-stu-id="8db67-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>
  
### <a name="examples"></a><span data-ttu-id="8db67-110">Примеры</span><span class="sxs-lookup"><span data-stu-id="8db67-110">Examples</span></span>

```csharp
ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");
/*
    $num
*/

ParameterExpression numParam =  Expression.Parameter(typeof(int));
/*
    $var1
*/
```

## <a name="constantexpression"></a><span data-ttu-id="8db67-111">ConstantExpression</span><span class="sxs-lookup"><span data-stu-id="8db67-111">ConstantExpression</span></span>  

<span data-ttu-id="8db67-112">Для объектов <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType>, представляющих целочисленные значения, строки и `null`, отображается значение константы.</span><span class="sxs-lookup"><span data-stu-id="8db67-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
<span data-ttu-id="8db67-113">Для числовых типов, имеющих стандартные суффиксы, такие как литералы C#, суффикс добавляется к значению.</span><span class="sxs-lookup"><span data-stu-id="8db67-113">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="8db67-114">В следующей таблице показаны суффиксы для различных числовых типов.</span><span class="sxs-lookup"><span data-stu-id="8db67-114">The following table shows the suffixes associated with various numeric types.</span></span>  

| <span data-ttu-id="8db67-115">Тип</span><span class="sxs-lookup"><span data-stu-id="8db67-115">Type</span></span> | <span data-ttu-id="8db67-116">Ключевое слово</span><span class="sxs-lookup"><span data-stu-id="8db67-116">Keyword</span></span> | <span data-ttu-id="8db67-117">Суффикс</span><span class="sxs-lookup"><span data-stu-id="8db67-117">Suffix</span></span> |  
|--|--|--|  
| <xref:System.UInt32?displayProperty=nameWithType> | [<span data-ttu-id="8db67-118">uint</span><span class="sxs-lookup"><span data-stu-id="8db67-118">uint</span></span>](../../../language-reference/keywords/uint.md) | <span data-ttu-id="8db67-119">U</span><span class="sxs-lookup"><span data-stu-id="8db67-119">U</span></span> |  
| <xref:System.Int64?displayProperty=nameWithType> | [<span data-ttu-id="8db67-120">long</span><span class="sxs-lookup"><span data-stu-id="8db67-120">long</span></span>](../../../language-reference/keywords/long.md) | <span data-ttu-id="8db67-121">L</span><span class="sxs-lookup"><span data-stu-id="8db67-121">L</span></span> |  
| <xref:System.UInt64?displayProperty=nameWithType> | [<span data-ttu-id="8db67-122">ulong</span><span class="sxs-lookup"><span data-stu-id="8db67-122">ulong</span></span>](../../../language-reference/keywords/ulong.md) | <span data-ttu-id="8db67-123">UL</span><span class="sxs-lookup"><span data-stu-id="8db67-123">UL</span></span> |  
| <xref:System.Double?displayProperty=nameWithType> | [<span data-ttu-id="8db67-124">double</span><span class="sxs-lookup"><span data-stu-id="8db67-124">double</span></span>](../../../language-reference/keywords/double.md) | <span data-ttu-id="8db67-125">D</span><span class="sxs-lookup"><span data-stu-id="8db67-125">D</span></span> |  
| <xref:System.Single?displayProperty=nameWithType> | [<span data-ttu-id="8db67-126">float</span><span class="sxs-lookup"><span data-stu-id="8db67-126">float</span></span>](../../../language-reference/keywords/float.md) | <span data-ttu-id="8db67-127">C</span><span class="sxs-lookup"><span data-stu-id="8db67-127">F</span></span> |  
| <xref:System.Decimal?displayProperty=nameWithType> | [<span data-ttu-id="8db67-128">decimal</span><span class="sxs-lookup"><span data-stu-id="8db67-128">decimal</span></span>](../../../language-reference/keywords/decimal.md) | <span data-ttu-id="8db67-129">M</span><span class="sxs-lookup"><span data-stu-id="8db67-129">M</span></span> |  
  
### <a name="examples"></a><span data-ttu-id="8db67-130">Примеры</span><span class="sxs-lookup"><span data-stu-id="8db67-130">Examples</span></span>  

```csharp
int num = 10; 
ConstantExpression expr = Expression.Constant(num);
/*
    10
*/

double num = 10; 
ConstantExpression expr = Expression.Constant(num);
/*
    10D
*/
```

## <a name="blockexpression"></a><span data-ttu-id="8db67-131">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="8db67-131">BlockExpression</span></span>
 
<span data-ttu-id="8db67-132">Если тип объекта <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> отличается от типа последнего выражения в блоке, то тип отображается в угловых скобках (`<` и `>`).</span><span class="sxs-lookup"><span data-stu-id="8db67-132">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="8db67-133">В противном случае тип объекта <xref:System.Linq.Expressions.BlockExpression> не отображается.</span><span class="sxs-lookup"><span data-stu-id="8db67-133">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="8db67-134">Примеры</span><span class="sxs-lookup"><span data-stu-id="8db67-134">Examples</span></span>  

```csharp
BlockExpression block = Expression.Block(Expression.Constant("test"));
/*
    .Block() {
        "test"
    }
*/

BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));
/*
    .Block<System.Object>() {
        "test"
    }
*/
```

## <a name="lambdaexpression"></a><span data-ttu-id="8db67-135">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="8db67-135">LambdaExpression</span></span>

<span data-ttu-id="8db67-136">Объекты <xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> отображаются вместе со своими типами делегатов.</span><span class="sxs-lookup"><span data-stu-id="8db67-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>
  
<span data-ttu-id="8db67-137">Если лямбда-выражение не имеет имени, оно назначается автоматически, например `#Lambda1` или `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="8db67-137">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>
  
### <a name="examples"></a><span data-ttu-id="8db67-138">Примеры</span><span class="sxs-lookup"><span data-stu-id="8db67-138">Examples</span></span>

```csharp
LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));
/*
    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
        1
    }
*/

LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);
/*
    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
        1
    }
*/
```
  
## <a name="labelexpression"></a><span data-ttu-id="8db67-139">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="8db67-139">LabelExpression</span></span>

<span data-ttu-id="8db67-140">Если указать значение по умолчанию для объекта <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType>, оно будет отображаться перед объектом <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8db67-140">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>
  
<span data-ttu-id="8db67-141">Маркер `.Label` указывает начало метки.</span><span class="sxs-lookup"><span data-stu-id="8db67-141">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="8db67-142">Маркер `.LabelTarget` задает конечную цель перехода для целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="8db67-142">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>
  
<span data-ttu-id="8db67-143">Если метка не имеет имени, оно назначается автоматически, например `#Label1` или `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="8db67-143">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>
  
### <a name="examples"></a><span data-ttu-id="8db67-144">Примеры</span><span class="sxs-lookup"><span data-stu-id="8db67-144">Examples</span></span>

```csharp
LabelTarget target = Expression.Label(typeof(int), "SampleLabel");
BlockExpression block = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
);
/*
    .Block() {
        .Goto SampleLabel { 0 };
        .Label
            -1
        .LabelTarget SampleLabel:
    }
*/

LabelTarget target = Expression.Label();
BlockExpression block = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
);
/*
    .Block() {
        .Goto #Label1 { };
        .Label
        .LabelTarget #Label1:
    }
*/
```
  
## <a name="checked-operators"></a><span data-ttu-id="8db67-145">Проверяемые операторы</span><span class="sxs-lookup"><span data-stu-id="8db67-145">Checked Operators</span></span>  

<span data-ttu-id="8db67-146">Проверяемые операторы отображаются с символом `#` перед оператором.</span><span class="sxs-lookup"><span data-stu-id="8db67-146">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="8db67-147">Например, проверяемый оператор сложения отображается как `#+`.</span><span class="sxs-lookup"><span data-stu-id="8db67-147">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="8db67-148">Примеры</span><span class="sxs-lookup"><span data-stu-id="8db67-148">Examples</span></span>  

```csharp
Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));
/*
    1 #+ 2
*/

Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));
/*
    #(System.Int32)10D
*/
```