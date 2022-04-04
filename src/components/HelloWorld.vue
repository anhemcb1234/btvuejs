<template>
<div class="hello">
    <div v-for="(item, index) in listData" :key="item.id" v-bind:class="{none:item.quantity===0}" @mouseover="add(index)">
        <div class="img">
            <img :src="item.img" alt="">
        </div>
        <div class="content">
            Ten: {{item.name}}
            Thuong hieu: {{item.brand}}
            Gia: {{item.price}}
            Ngay SX: {{item.date}}
            So luong {{item.quantity}}
            Mau sac {{item.color}}
            <div v-if="item.hot">
                <p>San pham ban chay</p>
            </div>
            <div v-else>
                <p>San pham khong ban chay</p>
            </div>
            <button @click="hanlerBuy(index)">Mua</button>
        </div>
    </div>
    <div>
        <p>BAG</p>
        <h1>San pham da mua</h1>
        <div v-for="(item, index) in showBuy" :key="index">
           <div class="list">
              <div class="img">
                <img :src="item.img" alt="">
                <p :style="{background: hehe}">asdasd</p>
            </div>
            <div class="content">
                Ten: {{item.name}}
                Thuong hieu: {{item.brand}}
                Gia: {{item.price}}
                Ngay SX: {{item.date}}
                So luong {{item.quantity}}
                Mau sac {{item.color}}
            </div>
                So luong da mua {{item.quantityBuy}}
            <div>
                Tong so tien {{item.quantityBuy * item.price}}
            </div>
           </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: 'HelloWorld',
    data() {
        return {
            listData: [{
                    id: 1,
                    name: 'Do an',
                    price: '200',
                    date: '2018-01-01',
                    hot: true,
                    brand: 'Honda',
                    img: 'https://i.ex-cdn.com/mgn.vn/files/content/2021/11/03/toc-goku_1-2117.jpg',
                    color: 'red',
                    quantity: 100,
                    quantityBuy: 0

                },
                {
                    id: 2,
                    name: 'Do an 1',
                    price: '300',
                    date: '2018-01-01',
                    hot: true,
                    brand: 'Honda',
                    img: 'https://gamek.mediacdn.vn/133514250583805952/2020/8/6/rtd1-1596712458074488543564.jpg',
                    color: 'green',
                    quantity: 10,
                    quantityBuy: 0

                },
                {
                    id: 3,
                    name: 'Do an 2',
                    price: '400',
                    date: '2018-01-01',
                    hot: false,
                    brand: 'Honda',
                    img: 'https://i.pinimg.com/550x/5e/72/30/5e723090a8ed5a1818cbc937e5e97c2d.jpg',
                    color: 'blue',
                    quantity: 1,
                    quantityBuy: 0
                },
            ],
            bag: [],
            showBuy: [],

        }
    },
    methods: {
        add: function (index) {
            document.querySelector('.hello').children[index].style.backgroundColor = this.listData[index].color;
        },
        hanlerBuy(index) {
            this.bag.push(this.listData[index]);
            if (this.listData[index].quantity === 0) {
                alert("Het hang");
            }
            this.listData[index].quantityBuy++;
            this.listData[index].quantity--
            let a = new Set(this.bag);
            this.showBuy = a
        },
        hehe() {
          return document.querySelector('.list').style.backgroundColor = this.listData[index].color;
        }
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
h1,
h2 {
    font-weight: normal;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}
.bg {
  background-color: 'this.listData[index].color';
}
a {
    color: #42b983;
}

.none {
    opacity: 0.7;
    cursor: none;
}
.hehe {
  color: red;
}
</style>
