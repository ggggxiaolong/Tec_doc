一次业务处理的流程[从数据请求，线程切换，到数据展示]

```kotlin
internal fun load(year: Int, month: Int, day: Int) {
    mRepository.getOilRecordByDay(getDateTime(year, month, day))//从数据仓库请求数据
        .async()//线程切换
        .doOnDispose{ mView!!.showLoading() }
        .doOnComplete{ mView!!.hideLoading() }
        .subscribe({ dateRecordResponse ->
          if (dateRecordResponse.isSuccess()) {
            mView!!.onDataSuccess(dateRecordResponse.data()!!, year, month, day)//数据展示
          } else {
            mView!!.onDataError()//错误处理
          }
        }, { e ->
          mView!!.hideLoading()
          mView!!.onDataError()//错误处理
        }).addThis (this::addSubscription)//生命周期控制
  }
```

