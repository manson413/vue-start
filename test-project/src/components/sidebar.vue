<template>
  <div id="sidebar" class="sidebar">
    {{ msg }}
    <div class="sidebar-user-icon"></div>
    <ul class="sidebar-list">
      <li v-for="item in items">
        <a href="#">{{ item.text }}</a>
      </li>
    </ul>
  
  </div>
</template>

<script>
  export default {
    props: {
      msg: {
        type: String,
        default: ''
      }
    },
    data () {
      return {
        items: [
          { text: 'Приход' },
          { text: 'Группы' },
          { text: 'Продукты' },
          { text: 'Пользователи' },
          { text: 'Настройки' }
        ]
      }
    }
  }
</script>

<style lang="scss">
  .sidebar {
    float: left;
    width: 250px;
    background-color: rgba(0,0,0,.1);
    min-height: calc(100vh - 70px);
    padding-top: 50px;
    &-user-icon {
      width: 80px;
      height: 80px;
      background: #bbb;
      border: 2px solid rgba(0,0,0,.3);
      border-radius: 50%;
      margin: 0 auto 50px;
      cursor: pointer;
    }
    &-list {
      margin-left: 70px;
      li {
        display: block;
        margin-top: 10px;
        a {
          text-decoration: none;
          color: #000;
        }
      }
    }
  }
</style>