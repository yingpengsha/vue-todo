<template>
  <div id="app">
    <div id="cover" />
    <HeaderView></HeaderView>
    <Todo></Todo>
    <FooterView></FooterView>
  </div>
</template>

<script>
import HeaderView from './views/todo/header.vue';
import FooterView from './views/todo/footer.jsx';
import Todo from './views/todo/todo.vue';

export default {
  name: 'app',
  data() {
    return {

    };
  },
  components: {
    HeaderView,
    FooterView,
    Todo,
  },
};
</script>


<style lang="less" scoped>
#app{
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
}
#cover{
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  background-color: #999;
  opacity: 0.5;
  z-index: -1;
}
</style>
