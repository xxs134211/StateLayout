我们可以通过监听缺省页显示的生命周期来获取其对应的视图对象

```kotlin
fun onEmpty(block: View.(Any?) -> Unit): StateLayout
// showEmpty() 时回调
fun onError(block: View.(Any?) -> Unit): StateLayout
// showError() 时回调
fun onLoading(block: View.(Any?) -> Unit): StateLayout
// showLoading() 时回调
fun onRefresh(block: StateLayout.(loading: View) -> Unit): StateLayout
// showLoading() 时回调
```

监听加载

```kotlin tab="示例"
state.onRefresh {
    // 每次showLoading都会执行该回调
}
state.showLoading()
```

```kotlin tab="链式调用"

state.onRefresh {
    // 每次showLoading都会执行该回调
}.showLoading()
```

监听缺省页显示

```kotlin tab="示例"
state.onEmpty {

}

state.onError {

}

state.onLoading {

}

state.onRefresh {

}
```

```kotlin tab="链式调用"
state.onEmpty {

}.onError {

}.onLoading {

}.onRefresh {

}
```

这里可以看到onRefresh和onLoading触发的条件一样, 但是他们的函数参数接收者不一样, 他们所代表的的作用也不同.

1. onRefresh 回调中处理加载时其异步任务(例如网络请求)
1. onLoading 中则处理的是加载视图UI