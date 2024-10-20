# JavaScript

互联网上已经有许多非常成熟、易懂、免费的公共资源，这里放几个他山之石，都是非常优质的资源。

[网道 / WangDoc.com - JavaScript 教程](https://wangdoc.com/javascript/)

[网道 / WangDoc.com - ES6 教程](https://wangdoc.com/es6/)

[网道 / WangDoc.com - Web API 教程](https://wangdoc.com/webapi/)

[JavaScript 教程| 菜鸟教程](https://www.runoob.com/js/js-tutorial.html)

[JavaScript - MDN Web Docs - Mozilla](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript)

## 📌 文章

[JavaScript 发布-订阅模式 - https://juejin.im/post/6844903850105634824#comment](https://juejin.im/post/6844903850105634824#comment)

[JSDoc - https://www.shouce.ren/api/view/a/13232](https://www.shouce.ren/api/view/a/13232)

## 📌 排序

```javascript
/**
 * @name 数组排序算法（保证数组数据唯一）
 * @author SunSeekerX
 * @time 2019-11-23 16:05:37
 * @LastEditors SunSeekerX
 * @LastEditTime 2019-11-23 18:59:32
 */

/**
 * 冒泡排序
 * 1.比较相邻的元素。如果第一个比第二个大，就交换他们两个。
 * 2.对每一对相邻元素做同样的工作，从开始第一对到结尾的最后一对。在这一点，最后的元素应该会是最大的数。
 * 3.针对所有的元素重复以上的步骤，除了最后一个。
 * 4.持续每次对越来越少的元素重复上面的步骤，直到没有任何一对数字需要比较。
 */

console.log('------------------冒泡排序---------------')
console.time()
const arr = [1, 9, 5, 4, 3, 8]
console.log('排序前>>>', arr)
for (let i = 0; i < arr.length - 1; i++) {
  for (let j = 0; j < arr.length - 1 - i; j++) {
    let temp = null
    if (arr[j] > arr[j + 1]) {
      temp = arr[j]
      arr[j] = arr[j + 1]
      arr[j + 1] = temp
    }
  }
}
console.log('排序后>>>', arr)
console.timeEnd()
console.log('\n')

/**
 * 插入排序
 * 1.依次取出数组中的值
 * 2.更新的数组对比插入到新的数组（抓牌原理一样）
 */

console.log('------------------插入排序,从后往前比（斗地主抓牌）---------------')
// 插入排序,从后往前比（斗地主抓牌）
const arr2 = [1, 9, 5, 4, 3, 8]
console.time()
console.log('排序前>>>', arr2)
// 1.取出第一张牌
const newArr = [arr2[0]]
for (let i = 1; i < arr2.length; i++) {
  // 2.从后面往前插
  for (let j = newArr.length - 1; j >= 0; j--) {
    // 如果取出的牌比当前循环的牌大，就放在这个牌后面
    if (arr2[i] > newArr[j]) {
      // 插入到新的数组
      newArr.splice(j + 1, 0, arr2[i])
      break
    }
    // 比较到第一张牌，放到手里的第一张（最小）
    if (j === 0) {
      newArr.unshift(arr2[i])
    }
  }
}
console.log('排序后>>>', newArr)
console.timeEnd()
console.log('\n')

/**
 * 快速排序
 * 1.首先设定一个分界值，通过该分界值将数组分成左右两部分。
 * 2.将大于或等于分界值的数据集中到数组右边，小于分界值的数据集中到数组的左边。此时，左边部分中各元素都小于或等于分界值，而右边部分中各元素都大于或等于分界值。
 * 3.然后，左边和右边的数据可以独立排序。对于左侧的数组数据，又可以取一个分界值，将该部分数据分成左右两部分，同样在左边放置较小值，右边放置较大值。右侧的数组数据也可以做类似处理。
 * 4.重复上述过程，可以看出，这是一个递归定义。通过递归将左侧部分排好序后，再递归排好右侧部分的顺序。当左、右两个部分各数据排序完成后，整个数组的排序也就完成了。
 */

console.log('------------------快速排序---------------')
const arr3 = [1, 9, 5, 4, 3, 8]
console.time()
console.log('排序前>>>', arr3)
function quick(arr) {
  // 4.结束递归（当arr中小于等于一项，则返回）
  if (arr.length <= 1) {
    return arr
  }

  // 1.找到数组的中间项把他删除
  let middleIndex = Math.floor(arr.length / 2)
  let middleValue = arr.splice(middleIndex, 1)[0]

  // 2.准备左右两个数组，循环剩下的数组中的每一项，比中间项小的放左边，反之放右边
  let arrLeft = [],
    arrRight = []
  for (let i = 0; i < arr.length; i++) {
    arr[i] < middleValue ? arrLeft.push(arr[i]) : arrRight.push(arr[i])
  }

  // 3.递归处理左右两边数组，一直到左右两边都排好（左右让左边+中间+右边为最后的结果）
  return quick(arrLeft).concat(middleValue, quick(arrRight))
}
console.log('排序后>>>', quick(arr3))
console.timeEnd()
console.log('\n')

console.log('------------------分割线---------------\n\n')

console.log('------------------（For循环计算1-10累加的和）---------------')
console.time()
let total = 0
for (let i = 1; i <= 10; i++) {
  total = total + i
}
console.log('For循环计算后>>>', total)
console.timeEnd()
console.log('\n')

console.log('------------------（递归计算1-10累加的和）---------------')
console.time()
function sumFun(n) {
  if (n > 10) {
    return 0
  }
  return n + sumFun(n + 1)
}
console.log('递归计算后>>>', sumFun(1))
console.timeEnd()
console.log('\n')

/**
 * 堆栈溢出
 *
 * Uncaught RangeError: Maximum call stack size exceeded
 */

// function fn() {
//   fn();
// }
// fn();

/**
 * 堆栈不溢出
 * 这实际上并不是递归调用，因为fn2的第一次调用实际上在setTimeout()调用下一个调用之前完成。
 * 所以，这不是技术上的递归，并且不会随着时间的推移建立堆栈。它可以在没有任何积聚的情况下永久运行，这是保持反复运行的完美方式。
 * javascript不是多线程的，因此它不会为定时器创建多个线程。
 * 触发的每个定时器事件只是将事件放入事件队列中，并且如果当时没有JS正在运行，则触发该事件（从而调用回调函数）。
 * 如果JS正在运行，那么JS引擎会等待，直到当前正在执行的JS完成，然后为事件队列中的下一个事件提供服务（从而调用回调）。
 *
 * 通俗的说
 *
 * 在执行setTimeout中的函数方法之前，fn()这个方法已经执行完毕了，内存堆栈已经释放了，因此不会内存溢出
 */

// function fn2() {
//   setTimeout(() => fn2(), 0);
// }
// fn2();
```
