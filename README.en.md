# iview-imgbox

[![AUR](https://img.shields.io/npm/v/iview-imgbox.svg)](https://www.npmjs.com/package/iview-imgbox)
[![](https://img.shields.io/badge/Author-poplanchong-orange.svg)](http://www.poplanchong.top)
[![GitHub stars](https://img.shields.io/github/stars/poplanchong123/iview-imgbox.svg?style=social&label=Stars)](https://github.com/poplanchong123/iview-imgbox)
[![GitHub forks](https://img.shields.io/github/forks/poplanchong123/iview-imgbox.svg?style=social&label=Fork)](https://github.com/poplanchong123/iview-imgbox)

> An Upload Picture Component on Vue Developed with iView

### Build Setup

```bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

```

### Screenshots Preview

![QQ截图20190605092410.png](https://i.loli.net/2019/06/05/5cf7194cbb04843451.png)

![QQ截图20190605092425.png](https://i.loli.net/2019/06/05/5cf7194cd78d213157.png)

#### Instructions

1.project dependence vue, iview, jquery

```html
<link
  rel="stylesheet"
  type="text/css"
  href="https://cdn.jsdelivr.net/npm/iview@3.4.2/dist/styles/iview.css"
/>
<script
  type="text/javascript"
  src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.min.js"
></script>
<script
  type="text/javascript"
  src="https://cdn.jsdelivr.net/npm/iview@3.4.2/dist/iview.min.js"
></script>
<script
  type="text/javascript"
  src="https://cdn.jsdelivr.net/npm/jquery@3.4.1/dist/jquery.min.js"
></script>
```

2. include iview-imgbox.js in index.js

```js
import iviewImgbox from 'iview-imgbox';
Vue.use(iviewImgbox);
```

3. usage

```html
<div id="app">
  <Card>
    <p slot="title">multiple</p>
    <div>
      <Row>
        <i-col span="12">
          <i-input placeholder="" disabled />
          <i-button slot="append" @click="multiple">select image</i-button>
        </i-col>
      </Row>
      <Row type="flex" justify="start" gutter="16" style="margin-top:10px;">
        <i-col>
          <div
            class="img-list"
            v-for="(img, index) in multiple_img_list"
            :key="img.id"
          >
            <img
              :src="img.url"
              onerror="this.src='./src/assets/nopic.jpg'; this.title='no pic.'; this.onerror=null;"
              width="150"
              class="img-responsive img-thumbnail"
            />
            <em
              class="close"
              style="position: absolute; top:0px; right:-14px;"
              title="delete this image"
              @click="deleteImage(index,multiple_img_list)"
              >×</em
            >
          </div>
        </i-col>
      </Row>
    </div>
  </Card>
</div>
```

```html
<script>
  var app = new Vue({
    el: '#app',
    data: function() {
      return {
        single_img_list: [],
        multiple_img_list: [],
        opts: {
          uploadParams: {
            url: '',
            data: {},
            headers: {}
          },
          listParams: {
            url: '',
            data: {},
            headers: {}
          },
          deleteParams: {
            url: '',
            data: {},
            headers: {}
          },
          multiple: true,
          enableUpload: true,
          maxSize: 2048,
          onSelect: img_list => {
            // selected image callback
            this.multiple_img_list = img_list;
          }
        }
      };
    },
    methods: {
      multiple: function() {
        this.$iviewImgbox(this.opts);
      },
      deleteImage(index, list) {
        list.splice(index, 1);
      }
    }
  });
</script>
```

> ps: Detailed reference items index.html
