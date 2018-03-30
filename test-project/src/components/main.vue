<template>
  <div id="main" class="main">
    <div class="main-wrapper">
      <div class="main-wrapper-title">Приходы</div>
      <div class="items">
        <div 
          class="item"
          v-for="order in orders"
          @click="show(order)"
        >
          <div class="item-name">{{ order.title }}</div>
          <div
                  class="item-qty"

          >
              {{ productsInOrder(order) }}
          </div>
          <div class="item-date">{{ order.date }}</div>
          <div class="item-price">
            
          </div>
          <div 
            class="item-remove"
            @click="removeItem(order)"
            >
              x
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
        orderProducts: 0,
        orders: [
          {
            id: 1,
            title: 'Order 1',
            date: '2017-06-29 12:09:33',
            description: 'desc1',
            get products () { 
              return products 
            }
          },
          {
            id: 2,
            title: 'Order 2',
            date: '2017-06-29 12:09:33',
            description: 'desc2',
            get products () { return products }
          },
          {
            id: 3,
            title: 'Order 3',
            date: '2017-06-29 12:09:33',
            description: 'desc3',
            get products () { return products }
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
              {value: 2600, symbol: 'UAH', isDefault: 1}
            ],
            order: 1,
            date: '2017-06-29 12:09:33'
          },
          {
            id: 4,
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
              {value: 2600, symbol: 'UAH', isDefault: 1}
            ],
            order: 1,
            date: '2017-06-29 12:09:33'
          },
          {
            id: 2,
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
              {value: 2600, symbol: 'UAH', isDefault: 1}
            ],
            order: 2,
            date: '2017-06-29 12:09:33'
          },
          {
            id: 5,
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
              {value: 2600, symbol: 'UAH', isDefault: 1}
            ],
            order: 2,
            date: '2017-06-29 12:09:33'
          },
          {
            id: 3,
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
              {value: 2600, symbol: 'UAH', isDefault: 1}
            ],
            order: 3,
            date: '2017-06-29 12:09:33'
          },
          {
            id: 6,
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
              {value: 2600, symbol: 'UAH', isDefault: 1}
            ],
            order: 3,
            date: '2017-06-29 12:09:33'
          }
        ]
      }
    },
    methods: {
      removeItem(order) {
        this.orders.$remove(order);
      },
        productsInOrder(order) {
          var count = 0;
            for (var i = 0; i < this.products.length; i++) {
                if (this.products[i].order === order.id) {
                    count++;
                }
            }
            return count === 0 ? '' : count;
        },
        show(item) {
          console.log(item.title);
        }
    },
    computed: {

    }
  }
</script>

<style lang="scss">
  .main {
    float: right;
    width: calc(100% - 250px);
    &-wrapper {
      padding: 50px;
      &-title {
        font-size: 30px;
      }
      .items {
        .item {
          display: flex;
          justify-content: space-between;
          margin-top: 10px;
          padding: 10px;
          border-radius: 5px;
          background-color: rgba(0,0,0,.1);
        }
      }
    }
  }
</style>