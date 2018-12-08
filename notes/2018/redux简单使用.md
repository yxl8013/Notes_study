# redux在项目的简单使用
一般在全局index.js建立一个store

### 配置store
```js
import { createStore } from 'redux'
const store = createStore((state = {

    data01: "定义你需要的数据01"

}, action) => {
    switch (action.type) {
        case '哈哈哈':
            return {
                ...state,
                data01: action.随意属性名  //connect()(组件)里定义的随意属性名
            }
        case '呀呀呀':
            return {
                ...state,
                data01: action.随意属性名
            }
        default:
            return state
    }
})

```
下面是redux 实现的流程图
        |-----<------------------<------------------------------|
        |                                                                       |                       
         view----->action----->dispatch------>state--|

 state 是存放数据的仓库
 action view里用户发出的一个的动作
 它是状态管理的配置参数，函数第一个参数为state，就是存储组件需要通信和交换的数据
 第二个参数是action，它是触发，他需要其他组件传递一个信号，

###  把上面配置好的store和react进行关联

简单来说 , Provider 的作用就是可以让App的所有子组件默认都可以拿到state

下面代码一般是固定写法
```js
import { Provider } from 'react-redux';
ReactDOM.render(
    <Provider store={store}>
        <Router>
            <App />
        </Router>
    </Provider>
, document.getElementById('root'));

```

###  connect( )(你需要拿state的组件)

```js
import { connect } from 'react-redux';
export default connect((state) => {
    return state

}, (dispatch) => {
    return {
        //定义一个方法给组件使用.  state 和方法都可以在组件的this.props中拿到
      toggleNav(){
            console.log(this) //如果要使用this,注意this是什么

            //触发了这个方法就会dispatch(action)了,里面放的对象就是action了,一般是用户触发了这个方法,发出action,action对象是什么自由发挥,要注意type是必须的,其他随意

			dispatch({
				type:"哈哈哈",
				isShowNav: this.props.isShowNav
			})

        }
    }
})(Xcomponent888);

````
connet的第一个函数是获取store里面的值返回给组件(拿)
而第二个函数是定义一个方法给自身使用，而这个方法可以触发store里面的action(改)