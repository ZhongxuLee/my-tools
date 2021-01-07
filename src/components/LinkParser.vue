<template>
  <div class="container-fluid link-parser-container">
    <div class="form-group">
      <label for="originalLink">原始链接</label>
      <input
        type="text"
        class="form-control"
        id="originalLink"
        placeholder="请输入您的链接"
        v-model="originalLink"
      />
    </div>
    <!-- <button type="submit" class="btn btn-primary" @click="handleClick">确定</button> -->
    <table class="table table-hover table-bordered">
      <thead class="thead-dark">
        <tr>
          <th scope="col">渠道</th>
          <th scope="col">链接</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th scope="row">微信小程序</th>
          <td v-text="wxLink"></td>
        </tr>
        <tr>
          <th scope="row">美团小程序</th>
          <td v-text="mtLink"></td>
        </tr>
        <tr>
          <th scope="row">优选App</th>
          <td v-text="appLink"></td>
        </tr>
      </tbody>
    </table>
    <div class="alert alert-info" role="alert">
      <p>链接生成规则：</p>
      <p>前缀 + encodeURIComponent 转译后的链接</p>
      <p>前缀分别是：</p>
      <p>微信小程序：igrocery://www.grocery.com/web?url=</p>
      <p>美团小程序：imeituan://www.meituan.com/web_knb?url=</p>
      <p>优选App：igrocery://www.grocery.com/web_knb?url=</p>
    </div>
  </div>
</template>

<script>
const WX_PREFIX = 'igrocery://www.grocery.com/web?url=';
const MT_PREFIX = 'imeituan://www.meituan.com/web_knb?url=';
const APP_PREFIX = 'igrocery://www.grocery.com/web_knb?url=';

export default {
  data() {
    return {
      originalLink: '',
    };
  },

  computed: {
    wxLink() {
      const { originalLink } = this;
      return `${WX_PREFIX}${encodeURIComponent(originalLink)}`;
    },

    mtLink() {
      const { originalLink } = this;
      return `${MT_PREFIX}${encodeURIComponent(originalLink)}`;
    },

    appLink() {
      const { originalLink } = this;
      return `${APP_PREFIX}${encodeURIComponent(originalLink)}`;
    },
  },

  // methods: {
  //   handleClick() {
  //     const { originalLink } = this;

  //   },
  // },
};
</script>

<style>
.link-parser-container {
  padding: 40px;
}
</style>
