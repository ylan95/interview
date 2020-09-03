Vue 面试题
## 1. 生命周期
* `beforeCreate` （初始化事件和生命周期）
* `created` （完成数据观测、属性和方法的计算，watcher、event事件回调完成）
* `beforeMount` （执行render函数，模板编译完成，）
* `mounted` （生成真实DOM，可访问$el）
* `beforeUpdate` （在这里更新data不会重新渲染）
* `updated` （更新完成，可以拿到更新后的dom）
* `beforeDestroy`
* `destroyed` (实例及子组件一起被销毁)

## 2. `computed`中的`getter`和`setter`
`computed`可以手动设置`set`和`get`函数，
``` javascript
computed:{
    get: function(){
        return this.firstName+' ' +this.lastName
    },
    set:function(newValue){
        const arr = newValue.split(' ')
        this.firstName = arr[0]
        this.lastName = arr[1]
    }
}
```
## 3. watch监听
``` javascript
watch:{
    key : function|functionName|obj|array
}
```
key可以是object.key，用于监听对象中某一个值的变化
``` javascript
watch:{
    obj:{
        handler:function(value,oldValue){},
        deep:true,//深层监听obj,无论多深，都能监听到变化然后执行回调函数
        immediate:true,//值第一次绑定到watch时默认并不会触发一次回调，设置为true后，绑定初始时就立即执行一次回调函数
    }
}
```