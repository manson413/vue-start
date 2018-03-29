<template>
  <header class="header">
    <div class="header-wrapper">
      <div
         class="logo"
         @click="showMsg('dfgdsfgdsfg'); classActive = !classActive"
         :class="{active: classActive}"
      >
        <img src="../assets/logo.png" alt="">
      </div>
      <div class="search">
        <input type="search" placeholder="Поиск">
      </div>
      <div class="date" id="date">
        <p>{{date}}</p>
        <p>{{time}}</p>
      </div>
    </div>
  </header>
</template>

<script>
  import moment from 'moment';
  export default {
    data () {
      return {
        headerTest: 'test',
        time: '',
        date: '',
        classActive: false
      }
    },
    mounted() {
      this.getDate();
    },
    methods: {
      getDate(){
        setInterval(() => {
          this.date = moment().format('DD.MM.YYYY');
          this.time = moment().format('HH:mm:ss');
        }, 1000)
      },
      showMsg(val) {
        this.$emit('show-msg', val)
      }
    }
  }
</script>

<style lang="scss">
  * {
    margin: 0;
  }
  .header {
    height: 70px;
    box-shadow: 0 10px 10px -7px rgba(0,0,0,.3);
    &-wrapper {
      margin-left: 250px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      height: 100%;
      .logo {
        width: 50px;
        img {
          width: 100%;
          height: auto;
        }
      }
      .date {
        margin-right: 20px;
        text-align: right;
        font-size: 14px;
      }
    }
  }
  .active{
    background: #999;
  }
</style>
