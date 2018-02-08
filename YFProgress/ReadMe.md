# Vue-YFPrgress 二级嵌套进度条组件


#### 属性

<table>
    <thead>
        <tr>
            <th>属性</th> 
            <th>说明</th> 
            <th>类型</th> 
            <th>默认值</th>
        </tr>
    </thead> 
    <tbody>
        <tr>
            <td>total</td>
            <td>总数</td>
            <td>Number</td>
            <td>0</td>
        </tr>
        <tr>
            <td>done</td>
            <td>已提交</td>
            <td>Number</td>
            <td>0</td>
        </tr>
        <tr>
            <td>modify</td>
            <td>已修改</td>
            <td>Number</td>
            <td>0</td>
        </tr>
        <tr>
            <td>tip</td>
            <td>提示文字和样式</td>
            <td>Array</td>
            <td>[
            {
                text: "未提交X人",
                fillStyle: "#ccc",
            }, {
                text: "已提交X人",
                fillStyle: "#9c3",
            }, {
                text: "已批改X人",
                fillStyle: "#080"
            }
        ]</td>
        </tr>
    </tbody>
</table>

