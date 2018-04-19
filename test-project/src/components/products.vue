<template>
  <transition name="show">
    <div id="products" class="products" v-show="block">
      <div class="products-wrapper">
        <div class="products-wrapper-title">Продукты</div>
          <div class="items">
            <div
              class="item"
              v-for="prod in prods"
            >
              <div class="item-name">{{ prod.title }}</div>
              <div class="item-name">{{ prod.type }}</div>
              <div class="item-name">{{ prod.specification }}</div>
              <div class="item-name">
                <p class="price-usd">{{ prod.price[0].value+prod.price[0].symbol }}</p>
                <p class="price-uah">{{ prod.price[1].value+prod.price[1].symbol }}</p>
              </div>
              <div 
                class="item-remove"
                @click="removeItem(prod)"
                >
                X
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
  export default {
    props: {
      prods: {
        type: Array,
        default: ''
      },
      block: {
        type: Boolean,
        default: false
      }
    },
    data () {
      return {
        
      }
    },
    methods: {
      removeItem(prod) {
        for (var i = 0; i < this.prods.length; i++) {
          if (this.prods[i].id == prod.id) {
            this.prods.splice(i, 1);
          }
        }
      }
    }
  }
</script>

<style lang="scss">
  .products {
    width: 100%;
    &-wrapper {
      background: url(../assets/skyscraper.png) center;
      background-size: cover;
      padding: 20px 20px;
      margin: 30px 20px 0 0;
      border: 1px solid #999;
      border-radius: 10px;
      &-title {
        font-size: 20px;
      }
      .items {
        .item {
          display: flex;
          justify-content: space-between;
          align-items: center;
          margin-top: 10px;
          padding: 10px;
          border-radius: 5px;
          background-color: rgba(220,220,220,.7);
          box-shadow: 2px 2px 7px -2px #555;
          font-size: 10px;
          &-remove {
            width: 20px;
            height: 20px;
            background-color: #bbb;
            cursor: pointer;
            text-align: center;
            line-height: 20px;
          }
        }
      }
    }
  }
  .show-enter-active, .show-leave-active {
    transition: all .3s ease .1s;
  }
  .show-enter, .show-leave-to {
    display: block;
    width: 0;
    transform: scale(0);
  }
</style>