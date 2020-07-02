# bpmnjs-custom-line-
  customize the color of the line and arrow of the whole flowchart
### bpmnjs自定义连线和箭头的颜色，有2种方式
* 第一种是改变全局的图和线条箭头的颜色
```js
const bpmnJS = new BpmnJS({
  bpmnRenderer: {
    defaultFillColor: 'green',
    defaultStrokeColor: 'yellow'
  }
});
```
* 第二种改变节点之间的连线颜色
```js
// 自定义连线和箭头的颜色
const drawConnection = bpmnRenderer.drawConnection
let customConnectionColor = function(visuals, connection){
    let res = drawConnection.call(bpmnRenderer, visuals, connection)
    let eleId = visuals.childNodes[0].style['marker-end'].split('"')[1]
    let marker = document.querySelector(eleId)
    marker.childNodes[0].style.fill = customLineAndArrowColor
    marker.childNodes[0].style.stroke = customLineAndArrowColor
    visuals.childNodes[0].style.stroke = customLineAndArrowColor
    return res
}
bpmnRenderer.drawConnection = customConnectionColor
```
具体的请参考代码[code](https://github.com/nobt/bpmnjs-custom-line)
