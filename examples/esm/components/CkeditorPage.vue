<template>
  <div>
    <h2>编辑器的基本使用</h2>
    <div>
      <p>这是刚开始的数据: {{ data1 }}</p>
      <button @click="get">获取内容</button><span v-show="subData">提交内容为：{{subData}}</span>
    </div>
    <br>
    <br>
    <em-ckeditor :id="editorId1" v-model="data1" :className="{'editor-page': true}"></em-ckeditor>
    <br>
    <br>
    <p>基本源码</p>
    <pre>
      &lt;em-ckeditor :id="editorId1" v-model="data1" :className="{'editor-page': true}"&gt;&lt;/em-ckeditor&gt;
    </pre>
    <br>
    <br>
    <h2>编辑器的扩展配置</h2>
    <em-ckeditor id="editor2" v-model="data2" :config="conf"></em-ckeditor>
    <br>
    <br>
    <p>扩展源码</p>
    <pre>
      &lt;em-ckeditor id="editor2" v-model="data2" :config="conf"&gt;&lt;/em-ckeditor&gt;
    </pre>
    <br>
    <br>
    <br>
    <h3>API</h3>
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
          <td>change</td>
          <td>改变内容触发</td>
          <td>Function</td>
          <td>-</td>
        </tr>
        <tr>
          <td>text</td>
          <td>默认内容</td>
          <td>String</td>
          <td>-</td>
        </tr>
        <tr>
          <td>className</td>
          <td>自定义的 class 名称。</td>
          <td>Object</td>
          <td>-</td>
        </tr>
        <tr>
          <td>id</td>
          <td>编辑器的 id</td>
          <td>String</td>
          <td>emeditor</td>
        </tr>
        <tr>
          <td>height</td>
          <td>编辑器的 height</td>
          <td>Number</td>
          <td>200</td>
        </tr>
        <tr>
          <td>cdnjs</td>
          <td>ckeditor 的 js 地址</td>
          <td>String</td>
          <td>https://unpkg.com/ckeditor@4.10.0/ckeditor.js</td>
        </tr>
        <tr>
          <td>cdncss</td>
          <td>ckeditor 的 css 地址</td>
          <td>String</td>
          <td>https://unpkg.com/ckeditor@4.10.0/contents.css</td>
        <tr>
          <td>config</td>
          <td>ckeditor 的 自定义配置</td>
          <td>Object</td>
          <td>-</td>
        </tr>
      </tbody>
    </table>
    <br>
    <h3>注册的方法</h3>
    <table>
      <thead>
        <tr>
          <th>事件名</th>
          <th>说明</th>
          <th>返回值</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>change</td>
          <td>改变触发的方法</td>
          <td>val</td>
        </tr>
        <tr>
          <td>inited</td>
          <td>ckeditor初始化完成，并设置完内容</td>
          <td>富文本id选择器选中的元素， ckeditor 对象， window.CKEDITOR</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data1: '<p>test</p>',
      data2: '<p>test data2</p>',
      editorId1: 'editor1',
      subData: '',
      conf: {
  			toolbarLocation: 'bottom',
  			removePlugins: 'elementspath,resize',
  		},
    };
  },
  methods: {
    get() {
      var editorElement = window.CKEDITOR.document.getById('editor');
      var data = window.CKEDITOR.instances[this.editorId1].getData();
      this.subData = data;
    },
  },
}
</script>

<style>
.editor-page {
  width: 60%;
  margin: 0 auto;
}
</style>
