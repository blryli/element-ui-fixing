## 基于elelemt-ui
#### 由于项目需要组件不能添加到body，而element-ui个别组件不支持 appendToBody 属性，因此做了如下优化 
- 优化 image-viewer 组件，默认不添加到body，如果需要添加到 body 可以通过设置 el-image 组件的 appendToBody 属性为 true 即可
- 优化 messageBox 组件，改造 setDefaults 方法，支持设置 appendTo 属性，指定组件渲染位置（原组件是写死添加到 body）
- 优化 message 组件，增加 setDefaults 方法，支持设置 appendTo、offset 等属性（下面为原组件默认值），指定组件渲染位置（原组件是写死添加到 body）
``` jsvascript
{
  visible: false,
  message: '',
  duration: 3000,
  type: 'info',
  iconClass: '',
  customClass: '',
  onClose: null,
  showClose: false,
  closed: false,
  verticalOffset: 20, // 这个值会被 options 的 offset 属性覆盖，因此 setDefaults 方法要设置 offset 属性
  timer: null,
  dangerouslyUseHTMLString: false,
  center: false
}
```
## Install
```shell
npm install element-ui-fixing -S
```

## Quick Start
``` javascript
import Vue from 'vue'
import Element from 'element-ui-fixing'

// 全局设置 message、messageBox 默认值
import { Message, MessageBox } from 'element-ui-fixing'
MessageBox.setDefaults({ appendTo: '.v-page' })
Message.setDefaults({ offset: 60, showClose: true })

Vue.use(Element)
```

## LICENSE
[MIT](LICENSE)
