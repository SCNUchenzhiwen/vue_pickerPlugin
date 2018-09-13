# pickerPlugin

# 自实现惯性滚动picker_demo

组件默认为日期选择，可通过传入selType标识同时传入对应的数据实现地区选择

* picker组件 @auth chenzhiwen
* @prop {String} [selType='date'] - 选择类型，默认为日期选择
* @prop {Array} [data] - 默认为生成当前时间前后50年数据，当selType不为date时有效
* @prop {Boolean} value - 控制显示隐藏时期插件，通过v-model实现双向绑定
* @emit pickerData - 点击确认按钮传递的选择结果数组

# 效果图
![s]()

传入地区选择示例格式，在App.vue文件的data定义，理论上应该抽取出来引入的。
###        [{
###          "child": [{
###            "child": [{"code": "110101", "value": "东城区"}, {
###              "code": "110102",
###              "value": "西城区"
###            }, {"code": "110105", "value": "朝阳区"}, {"code": "110106", "value": "丰台区"}, {
###              "code": "110107",
###              "value": "石景山区"
###            }, {"code": "110108", "value": "海淀区"}, {"code": "110109", "value": "门头沟区"}, {
###              "code": "110111",
###              "value": "房山区"
###            }, {"code": "110112", "value": "通州区"}, {"code": "110113", "value": "顺义区"}, {
###              "code": "110114",
###              "value": "昌平区"
###            }, {"code": "110115", "value": "大兴区"}, {"code": "110116", "value": "怀柔区"}, {
###              "code": "110117",
###              "value": "平谷区"
###            }, {"code": "110118", "value": "密云区"}, {"code": "110119", "value": "延庆区"}],
###            "code": "110100",
###            "id": "0",
###            "value": "北京市"
###          }], "code": "110000", "id": "1", "value": "北京"
###        }]

# 滚动原理
##  1、当手指离开时根据touchstart到touchend所耗时间和位移获取滚动初速度。通过requestAnimationFrame执行滚动动画。
##  2、边界判断，根据子元素个父元素高度获取最大滚动边界进行判断。
##  3、越界回弹。越界一段距离后改变速度方向，在固定时间内回到边界位置。根据越界距离和时间计算加速度，修改每一个16.7ms的位移实现匀减速。
##  4、滚动结束自动滚动到某个最近的选择结果。

使用直接下载components/pickerPlugin文件即可


> pickerPlugin

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
