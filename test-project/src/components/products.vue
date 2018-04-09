<template>
  <div id="products" class="products">
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
</template>

<script>
  export default {
    props: {
      prods: {
        type: Array,
        default: ''
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
    float: left;
    width: 40%;
    &-wrapper {
      padding: 50px 20px;
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
          background-color: rgba(0,0,0,.1);
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
</style>