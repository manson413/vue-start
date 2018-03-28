<template>
  <div>
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
          {{date}} - {{time}}
        </div>
      </div>
    </header>

  </div>
</template>

<script>
  import moment from 'moment';
  export default {
    mounted() {
      this.getDate();
    },
    data () {
      return {
        headerTest: 'test',
        time: '',
        date: '',
        classActive: false
      }
    },
    methods: {
      getDate(){
        setInterval(() => {
          this.time = moment().format('HH:mm:ss');
          this.date = moment().format('YYYY.MM.DD');
        }, 1000)
      },
      showMsg(val) {
        this.$emit('show-msg', val)
      }
    }
  }
//  function getDate(){
//    var date = new Date();
//    var hours = date.getHours();
//    var minutes = date.getMinutes();
//    var seconds = date.getSeconds();
//    if(seconds < 10){
//        seconds = '0' + seconds;
//    }
//    document.getElementById('date').innerHTML = hours + ':' + minutes + ':' + seconds;
//  }
//  setInterval(getDate, 0);

</script>

<style lang="scss">
  .header {
    height: 70px;
    box-shadow: 0 10px 10px -7px rgba(0,0,0,.5);
    &-wrapper {
      margin-left: 250px;
      display: flex;
      justify-content: space-between;
      .logo {
      width: 50px;
      img {
        width: 100%;
        height: auto;
        margin-top: 10px;
      }
    }
    }
  }
  .active{
    background: #999;
  }
</style>
