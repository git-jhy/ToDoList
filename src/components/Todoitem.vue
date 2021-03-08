<template>
  <li
  @click="handelClick"
  >{{content}}</li>
</template>

<script>
export default {
  props: {
    content: String,
    index: Number
  },
  methods: {
    // 点击删除
    handelClick: function () {
      if (confirm('Delete this item ?')) {
        this.$emit('delete', this.index)
      }
    }
  }
}
</script>

<style scoped>

li {
  width: 250px;
  height: 40px;
  margin: 15px 15px 15px 0;
  border-radius: 20px;
  border-radius: 20px;
  background-color: rgb(181, 235, 207);
  box-shadow: 0 0 6px 2px rgb(196, 224, 215);
  list-style: none;
  text-align: center;
  line-height: 36px;
  justify-content: center;
}

li:hover {
  background-color: rgb(135, 218, 176);
  box-shadow: 0 0 10px 2px rgb(133, 201, 178);
}

/* 鼠标浮动显示内容 */
li:after {
  display: flex;
  content: 'click to delete me';
  visibility: hidden;
  position: relative;
  left: 260px;
  top: -36px;
  color: rgb(184, 155, 76);
  font-size: 16px;
  align-items: center;
}

li:hover:after {
  visibility: visible;
}

</style>
