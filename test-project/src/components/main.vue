<template>
  <div id="main" class="main">
    <div class="main-wrapper">
      <div class="main-wrapper-title">Приходы{{msg}}</div>
      <div class="items">
        <div 
          class="item"
          v-for="order in orders"
          @click="showProducts(order)"
        >
          <div class="item-name">{{ order.title }}</div>
          <div class="item-qty">
              {{ productsInOrder(order) }} продукта
          </div>
          <div class="item-date">{{ order.date }}</div>
          <div class="item-price">
            <p class="price-usd">{{ getPrice(order)[0] }}</p>
            <p class="price-uah">{{ getPrice(order)[1] }}</p>
          </div>
        </div>
      </div>
    </div>
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
        orders: [
          {
            id: 1,
            title: 'Order 1',
            date: '2017-06-29 12:09:33',
            description: 'desc1'
            // get products () { return products }
          },
          {
            id: 2,
            title: 'Order 2',
            date: '2017-06-29 12:09:33',
            description: 'desc2'
            // get products () { return products }
          },
          {
            id: 3,
            title: 'Order 3',
            date: '2017-06-29 12:09:33',
            description: 'desc3'
            // get products () { return products }
          }
        ],
        products: [
          {
            id: 1,
            serialNumber: 1234,
            isNew: 1,
            photo: 'pathToFile.jpg',
            title: 'Product 1',
            type: 'Monitors',
            specification: 'Specification 1',
            guarantee: {
              start: '2017-06-29 12:09:33',
              end: '2017-06-29 12:09:33'
            },
            price: [
              {value: 100, symbol: 'USD', isDefault: 0},
              {value: 2000, symbol: 'UAH', isDefault: 1}
            ],
            order: 1,
            date: '2017-06-29 12:09:33'
          },
          {
            id: 4,
            serialNumber: 1234,
            isNew: 1,
            photo: 'pathToFile.jpg',
            title: 'Product 2',
            type: 'Monitors',
            specification: 'Specification 2',
            guarantee: {
              start: '2017-06-29 12:09:33',
              end: '2017-06-29 12:09:33'
            },
            price: [
              {value: 100, symbol: 'USD', isDefault: 0},
              {value: 2000, symbol: 'UAH', isDefault: 1}
            ],
            order: 1,
            date: '2017-06-29 12:09:33'
          },
          {
            id: 7,
            serialNumber: 1234,
            isNew: 1,
            photo: 'pathToFile.jpg',
            title: 'Product 7',
            type: 'Monitors',
            specification: 'Specification 3',
            guarantee: {
              start: '2017-06-29 12:09:33',
              end: '2017-06-29 12:09:33'
            },
            price: [
              {value: 100, symbol: 'USD', isDefault: 0},
              {value: 2000, symbol: 'UAH', isDefault: 1}
            ],
            order: 1,
            date: '2017-06-29 12:09:33'
          },
          {
            id: 2,
            serialNumber: 1234,
            isNew: 1,
            photo: 'pathToFile.jpg',
            title: 'Product 3',
            type: 'Monitors',
            specification: 'Specification 4',
            guarantee: {
              start: '2017-06-29 12:09:33',
              end: '2017-06-29 12:09:33'
            },
            price: [
              {value: 200, symbol: 'USD', isDefault: 0},
              {value: 4000, symbol: 'UAH', isDefault: 1}
            ],
            order: 1,
            date: '2017-06-29 12:09:33'
          },
          {
            id: 5,
            serialNumber: 1234,
            isNew: 1,
            photo: 'pathToFile.jpg',
            title: 'Product 4',
            type: 'Mouse',
            specification: 'Specification 5',
            guarantee: {
              start: '2017-06-29 12:09:33',
              end: '2017-06-29 12:09:33'
            },
            price: [
              {value: 200, symbol: 'USD', isDefault: 0},
              {value: 4000, symbol: 'UAH', isDefault: 1}
            ],
            order: 2,
            date: '2017-06-29 12:09:33'
          },
          {
            id: 3,
            serialNumber: 1234,
            isNew: 1,
            photo: 'pathToFile.jpg',
            title: 'Product 5',
            type: 'MFU',
            specification: 'Specification 6',
            guarantee: {
              start: '2017-06-29 12:09:33',
              end: '2017-06-29 12:09:33'
            },
            price: [
              {value: 300, symbol: 'USD', isDefault: 0},
              {value: 6000, symbol: 'UAH', isDefault: 1}
            ],
            order: 3,
            date: '2017-06-29 12:09:33'
          },
          {
            id: 6,
            serialNumber: 1234,
            isNew: 1,
            photo: 'pathToFile.jpg',
            title: 'Product 6',
            type: 'MFU',
            specification: 'Specification 7',
            guarantee: {
              start: '2017-06-29 12:09:33',
              end: '2017-06-29 12:09:33'
            },
            price: [
              {value: 300, symbol: 'USD', isDefault: 0},
              {value: 6000, symbol: 'UAH', isDefault: 1}
            ],
            order: 3,
            date: '2017-06-29 12:09:33'
          },
          {
            id: 8,
            serialNumber: 1234,
            isNew: 1,
            photo: 'pathToFile.jpg',
            title: 'Product 8',
            type: 'MFU',
            specification: 'Specification 8',
            guarantee: {
              start: '2017-06-29 12:09:33',
              end: '2017-06-29 12:09:33'
            },
            price: [
              {value: 300, symbol: 'USD', isDefault: 0},
              {value: 6000, symbol: 'UAH', isDefault: 1}
            ],
            order: 3,
            date: '2017-06-29 12:09:33'
          },
          {
            id: 9,
            serialNumber: 1234,
            isNew: 1,
            photo: 'pathToFile.jpg',
            title: 'Product 8',
            type: 'Mouse',
            specification: 'Specification 9',
            guarantee: {
              start: '2017-06-29 12:09:33',
              end: '2017-06-29 12:09:33'
            },
            price: [
              {value: 300, symbol: 'USD', isDefault: 0},
              {value: 6000, symbol: 'UAH', isDefault: 1}
            ],
            order: 2,
            date: '2017-06-29 12:09:33'
          }
        ]
      }
    },
    methods: {
      productsInOrder(order) {
        var count = 0;
          for (var i = 0; i < this.products.length; i++) {
            if (this.products[i].order === order.id) {
                count++;
            }
          }
          return count === 0 ? '' : count;
      },
      getPrice(order) {
        var price = [],
            usdTotal = 0,
            uahTotal = 0;
          for (var i = 0; i < this.products.length; i++) {
            if (this.products[i].order === order.id) {
                usdTotal += this.products[i].price[0].value;
                uahTotal += this.products[i].price[1].value;
            }
          }
          price[0] = usdTotal + " " + this.products[0].price[0].symbol;
          price[1] = uahTotal + " " + this.products[0].price[1].symbol
        return price;
      },
      showProducts(order) {
        var productsForShow = [];
        for (var i = 0; i < this.products.length; i++) {
            if (this.products[i].order === order.id) {
              productsForShow.push(this.products[i]);
            }
          }
        this.$emit('show-products', productsForShow);
        this.$emit('show-block');
      }
    },
    computed: {

    }
  }
</script>

<style lang="scss">
  .main {
    float: left;
    width: calc(60% - 250px);
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
        }
      }
    }
  }
</style>