# Laravel 的集合 Collection

## 简介

`Illuminate\Support\Collection` 类提供了一个更具可读性的、更便于处理数组数据的封装，具体例子看下面的代码。

我们使用了 `collect` 函数从数组中创建新的集合实例，对其中的每个元素运行 `strtoupper` 函数之后再移除所有的空元素：

```
$collection = collect(['taylor', 'abigail', null])->map(function ($name) {
    return strtoupper($name);
})
->reject(function ($name) {
    return empty($name);
});
```

正如你看到的，`Collection` 类允许你链式调用其方法，以达到在底层数组上优雅地执行 map 和 reject 操作。一般来说，集合是不可改变的，这意味着每个 `Collection` 方法都会返回一个全新的 `Collection` 实例。

## 创建集合

如上所述，辅助函数 `collect` 会为给定的数组返回一个新的 `Illuminate\Support\Collection` 实例。也就是说，创建一个集合就这么简单：

```
$collection = collect([1, 2, 3]);
```

> 默认情况下， [Eloquent](https://laravel.com/docs/5.5/eloquent) 查询的结果返回的内容都是 `Collection` 实例。

## 可用的方法

接下来的内容，我们会探讨 `Collection` 类每个可用的方法。**记住，所有方法都可以以方法链的形式优雅地操纵数组。**而且，几乎所有的方法都会返回新的 `Collection` 实例，允许你在必要时保存集合的原始副本。

| 方法名 | 释义 |
| :--- | :--- |
| all [详细](/collections/all.md) | 返回该集合表示的底层**数组** |
| average [详细](/collections/avg.md) | 方法`avg()`的别名 |
| avg [详细](/collections/avg.md) | 返回给定键的**平均值** |
| chunk [详细](/collections/chuck.md) | 将集合拆成多个指定大小的小集合 |
| collapse [详细](/collections/collapse.md) | 将多个数组合并成一个 |
| combine [详细](/collections/combine.md) | 将一个集合的值作为「键」，再将另一个数组或者集合的值作为「值」合并成一个集合 |
| contains [详细](/collections/contains.md) | 判断集合是否包含给定的项目 |
| containsStrict [详细](/collections/containsStrict.md) | 使用「严格模式」来比较所有值 |
| count [详细](/collections/count.md) | 返回该集合内的项目总数 |
| diff [详细](/collections/diff.md) | 基于值求差集 |
| diffAssoc [详细](/collections/diffAssoc.md) | 基于键值对求差集 |
| diffKeys [详细](/collections/diffKeys.md) | 基于键求差集 |
| each [详细](/collections/each.md) | 迭代集合中的内容并将其传递到回调函数中 |
| every [详细](/every) | 可用于验证集合中每一个元素都通过给定的真实测试 |
| except [详细](/collections/except.md) | 返回集合中除了指定键以外的所有项目 |
| filter [详细](/collections/filter.md) | 使用给定的回调函数过滤集合的内容，只留下那些通过给定真实测试的内容 |
| first [详细](/collections/first.md) | 返回集合中通过给定真实测试的第一个元素 |
| flatMap [详细](/collections/flatMap.md) | 遍历集合并将其中的每个值传递到给定的回调 |
| flatten [详细](/collections/flatten.md)| 将多维集合转为一维 |
| flip [详细](/collections/flip.md) | 将集合中的键和对应的数值进行互换 |
| forget [详细](/collections/forget.md) | 通过给定的键来移除掉集合中对应的内容 |
| forPage [详细](/collections/forPage.md) | 返回给定页码上显示的项目的新集合 |
| get [详细](/collections/get.md) | 返回给定键的项目 |
| groupBy [详细](/collections/groupBy.md) | 根据给定的键对集合内的项目进行分组 |
| has [详细](/collections/has.md) | 判断集合中是否存在给定的键 |
| implode [详细](/collections/implode.md) | 合并集合中的项目 |
| intersect [详细](/collections/intersect.md) | 从原集合中删除不在给定数组或集合中的任何值 |
| intersectKey [详细](/collections/intersectKey.md) | 删除原集合中不存在于给定数组或集合中的任何键 |
| isEmpty [详细](/collections/isEmpty.md) | 判断集合是否为空 |
| isNotEmpty [详细](/collections/isNotEmpty.md) | 判断集合是否不为空 |
| keyBy [详细](/collections/keyBy.md) | 以给定的键作为集合的键 |
| keys [详细](/collections/keys.md) | 返回集合的所有键 |
| last [详细](/collections/last.md) | 返回集合中通过给定真实测试的最后一个元素 |
| map [详细](/collections/map.md) | 遍历集合并将每一个值传入给定的回调 |
| mapWithKeys [详细](/collections/mapWithKeys.md) | 遍历集合并将每个值传入给定的回调 |
| max [详细](/collections/max.md) | 返回给定**键**的最大值 |
| median [详细](/collections/median.md) | 方法返回给定**键**的中间值 |
| merge [详细](/collections/merge.md) | 将给定数组或集合合并到原集合 |
| min [详细](/collections/min.md) | 返回给定键的最小值 |
| mode [详细](/collections/mode.md) | 返回给定**键**的[众数值](https://baike.baidu.com/item/%E4%BC%97%E6%95%B0/44796 "百度百科-众数值") |
| nth [详细](/collections/nth.md) | 创建由每隔`n`个元素组成一个新的集合 |
| only [详细](/collections/only.md) | 返回集合中给定键的所有项目 |
| partition [详细](/collections/partition.md) | 配合`list()`方法区分回调函数满足和不满足的数据 |
| pipe [详细](/collections/pipe.md) | 将集合传给给定的回调并返回结果 |
| pluck [详细](/collections/pluck.md) | 获取集合中给定键对应的所有值 |
| pop [详细](/collections/pop.md) | 移除并返回集合中的最后一个项目 |
| prepend [详细](/collections/prepend.md) | 将给定的值添加到集合的开头 |
| pull [详细](/collections/pull.md) | 把给定键对应的值从集合中移除并返回 |
| push [详细](/collections/push.md) | 把给定值添加到集合的末尾 |
| put [详细](/collections/put.md) | 在集合内设置给定的键值对 |
| random [详细](/collections/random.md) | 从集合中返回一个随机项 |
| reduce [详细](/collections/reduce.md) | 将每次迭代的结果传递给下一次迭代直到集合减少为单个值 |
| reject [详细](/collections/reject.md) | 使用指定的回调过滤集合 |
| reverse [详细](/collections/reverse.md) | 倒转集合中项目的顺序 |
| search [详细](/collections/search.md) | 搜索给定的值并返回它的键 |
| shift [详细](/collections/shift.md) | 移除并返回集合的第一个项目 |
| shuffle [详细](/collections/shuffle.md) | 随机排序集合中的项目 |
| slice [详细](/collections/slice.md) | 返回集合中给定值后面的部分 |
| sort [详细](/collections/sort.md) | 保留原数组的键，对集合进行排序 |
| sortBy [详细](/collections/sortBy.md) | 以给定的键对集合进行排序 |
| sortByDesc [详细](/collections/sortByDesc.md) | 与[sortBy](/collections/sortBy.md)一样，以相反的顺序来对集合进行排序 |
| splice [详细](/collections/splice.md) | 删除并返回从给定值后的内容，原集合也会受到影响 |
| split [详细](/collections/split.md) | 将集合按给定的值拆分 |
| sum [详细](/collections/sum.md) | 返回集合内所有项目的总和 |
| take [详细](/collections/take.md) | 返回给定数量项目的新集合 |
| tap [详细](/collections/tap.md) | 将集合传递给回调，在特定点「tap」集合 |
| times [详细](/collections/times.md) | 通过回调在给定次数内创建一个新的集合 |
| toArray [详细](/collections/toArray.md) | 将集合转换成 PHP 数组 |
| toJson [详细](/collections/toJson.md) | 将集合转换成 JSON 字符串 |
| transform [详细](/collections/transform.md) | 迭代集合并对集合内的每个项目调用给定的回调 |
| union [详细](/collections/union.md) | 将给定的数组添加到集合中 |
| unique [详细](/collections/unique.md) | 返回集合中所有唯一的项目 |
| uniqueStrict [详细](/collections/uniqueStrict.md) | 使用严格模式返回集合中所有唯一的项目 |
| values [详细](/collections/values.md) | 返回键被重置为连续编号的新集合 |
| when [详细](/collections/when.md) | 当传入的第一个参数为 true 的时，将执行给定的回调 |
| where [详细](/collections/where.md) | 通过给定的键值过滤集合 |
| whereStrict [详细](/collections/whereStrict.md) | 使用严格模式通过给定的键值过滤集合 |
| whereIn [详细](/collections/whereIn.md) | 通过给定的键值数组来过滤集合 |
| whereInStrict [详细](/collections/whereStrict.md) | 使用严格模式通过给定的键值数组来过滤集合 |
| whereNotIn [详细](/collections/whereNotIn.md) | 集合中不包含的给定键值对进行匹配 |
| whereNotInStrict [详细](/collections/whereNotInStrict.md) | 使用严格模式通过集合中不包含的给定键值对进行匹配 |
| zip [详细](/collections/zip.md) | 将给定数组的值与相应索引处的原集合的值合并在一起 |

## 在项目中单独使用

### 安装

Laravel中的Collection使用Composer管理，所以我们可以在项目中使用composer安装到非Laravel项目中，比如我们新建一个collections目录，通过下面使用命令安装

```
mkdir collections && cd collections
composer require illuminate/support
```

执行完上面的命令将得到所需要的package。

### 使用

```
<?php
// 引入package
require __DIR__ . '/vendor/autoload.php';
```

## 其他

如果在js中也需要使用类似的数组操作，可以参考 [ecrmnn/collect.js](https://github.com/ecrmnn/collect.js) 的相关操作。
