<template>
  <div class="product">
    <div class="descr">
      <div class="title">
        <div class="title-main">{{title}}</div>
        <div class="title-additional"><span>{{subtitle}}</span></div>
      </div>
      <div class="tabs">
        <div class="tabs-btn">
          <ul class="tabs-buttons">
            <li v-for="item in tabs" :key='item.name' @click="changeTab(item.id)" :class="{ active: this.id === item.id}">{{item.name}}</li>
          </ul>
          <div class="underline"></div>
        </div>
        <div class="tabs-text">
          <div v-if="tabs[this.id].type === 'text'">{{tabs[id].descr}}</div>
          <div v-if="tabs[this.id].type === 'list'">
            <ul>
              <li v-for="item in tabs[this.id].descr" key="item">{{item}}</li>
            </ul>
          </div>
          <div v-if="tabs[this.id].type === 'table'">
            <div v-for="item in tabs[this.id].descr" key="item" class="table-item">
              <div class="row">
                <div class="column title">{{item.name}}</div>
                <div class="column descr">{{item.descr}}</div>
              </div>
              <div class="column-underline"></div>
            </div>
          </div>
          <div v-if="tabs[this.id].type === 'text-html'">
            <p v-for="item in tabs[this.id].descr" :key="item" v-html="item"></p>
          </div>
        </div>
      </div>
      <div class="price-section">
        <div class="left">
          <img src="../assets/icons/drugs-blue.svg" alt="drugs">
          <div class="amount">
            <span class="first">В упаковці:</span>
            <span class="second">{{ parameters.amount }} капсул по {{parameters.dose}} мг</span>
            <span class="third" v-if="parameters.months === 1">{{ parameters.months }} місяць прийому</span>
            <span v-if="parameters.months > 1 && parameters.months < 5">{{ parameters.months }} місяці прийому</span>
            <span v-if="parameters.months >= 5">{{ parameters.months }} місяців прийому</span>
          </div>
        </div>
        <div class="right">
          <div class="oldprice">{{parameters.oldprice}} ₴</div>
          <div class="price">{{parameters.price}} ₴</div>
        </div>
      </div>
      <div class="buttons">
        <div class="counter">
          <button class="decrement" @click="decrement">-</button>
          <div class="number">{{ this.count }}</div>
          <button class="increment" @click="increment">+</button>
        </div>
        <div class="cart-btn">До кошика</div>
      </div>
    </div>
    <div class="images">

    </div>
  </div>
</template>

<script>
export default {
  name: "Product",
  data() {
    return {
      id: 0,
      title: 'Омега-3 Тріска',
      subtitle: 'з вітамінами А і D3',
      tabs: [
        {id: 0, name: 'ОПИС', type: 'text', descr:
              'Комплекс EPA + DHA кислот і натуральних вітамінів А & D3 для здоров\'я твоєї шкіри, волосся, ' +
              'зору, сну, міцних кісток, суглобів та імунітету.'},
        {id: 1, name: 'КОРИСТЬ', type: 'list', descr: [
            'Покращують стан шкіри: борються з акне та сприяють її регенерації',
            'Зменшують випадіння волосся, стимулюють його ріст',
            'Підіймають настрій та полегшують симптоми депресії',
            'Зміцнюють імунітет: зменшують запальні процеси',
            'Поліпшують роботу гормонів, серця і ЦНС',
            'Зменшують болі в суглобах',
            'Покращують метаболізм і роботу ШКТ'
          ]},
        {id: 2, name: 'ІНГРЕДІЄНТИ', type: 'table', descr: [
            {name: 'Склад:', descr: '100% риб\'ячий жир з печінки тріски, желатин, гліцерин.'},
            {name: 'EPA / DHA', descr: '170 мг / 205 мг'},
            {name: 'Вітамін-А', descr: '656 мкг 2187 МО'},
            {name: 'Вітамін-D3', descr: '5.2 мкг 210 МО'},
          ]},
        {id: 3, name: 'СПОСІБ ЗАСТОСУВАННЯ', type: 'text-html', descr: [
              'Для профілактики, дорослим і дітям від 11 років – <b><i>4 капсули на день</i></b>, разом із їжею або одразу після. Бажано з іншими жирами <i>для кращого засвоєння.</i>',
              '<b>Курс прийому:</b> 2-3 місяці, після чого зробити перерву 1-2 місяці або перейти на Омега-3 із Тунця.'
          ]}
      ],
      parameters: {amount: 120, dose: 500, months: 1, price: 489, oldprice: 963},
      count: 1
    }
  },
  methods: {
    changeTab(id) {
      this.id = id;
    },
    increment() {
      this.count++;
    },
    decrement() {
      if (this.count > 1) {
        this.count--;
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.product {
  margin-top: 100px;
  .descr {
    max-width: 635px;
    .title {
      display: flex;
      justify-content: space-between;
      &-main {
        font-weight: 700;
        font-size: 40px;
        color: #00284F;
      }
      &-additional {
        display: flex;
        align-items: center;
        background: #FFFFFF;
        border-radius: 50px;
        span {
          font-weight: 500;
          font-size: 22px;
          line-height: 22px;
          color: #00284F;
          padding: 8px 52px;
        }
      }
    }
    .tabs {
      margin-top: 32px;
      &-btn {
        max-width: 580px;
        & .tabs-buttons {
          padding: 0;
          display: flex;
          justify-content: space-between;
          margin-bottom: 0;
          li {
            list-style-type: none;
            font-weight: 700;
            font-size: 17px;
            color: #00284F;
            opacity: 0.4;
            cursor: pointer;
            &.active {
              opacity: 1;
              border-bottom: 2px solid #00284F;
              padding-bottom: 5px;
            }
          }
        }
        .underline {
          width: 100%;
          height: 1px;
          background: darkblue;
        }
      }
      &-text {
        margin-top: 12px;
        font-size: 18px;
        line-height: 28px;
        color: #335371;
        & .table-item {
          .row {
            display: flex;
          }
          .column {
            flex: 50%;
            &.title {
              font-weight: 700;
              color: #00284F;
            }
            &.descr {
              color: #335371;
            }
            &-underline {
              width: 100%;
              background: #00284F;
              height: 1px;
            }
          }
        }
      }
    }
  }
}
.price-section {
  display: flex;
  justify-content: space-between;
  margin-top: 56px;
  & .left {
    display: flex;
    justify-content: center;
    & .amount {
      display: flex;
      flex-direction: column;
      margin-left: 32px;
      font-size: 18px;
      line-height: 23px;
      color: #00284F;
      & .first {
        font-weight: 700;
      }
      & .third {
        opacity: 0.5;
      }
    }
  }
  & .right {
    display: flex;
    align-items: center;
    & .price {
      font-weight: 700;
      font-size: 40px;
      line-height: 51px;
      color: #00284F;
    }
    & .oldprice {
      margin-right: 24px;
      font-weight: 900;
      font-size: 28px;
      line-height: 36px;
      color: rgba(0, 40, 79, 0.3);
      position: relative;
      &:before {
        content: "";
        border-bottom: 3px solid #00284F;
        position: absolute;
        width: 100%;
        height: 50%;
        transform: rotate(12deg);
      }
    }
  }
}
.buttons {
  display: flex;
  justify-content: space-between;
  margin-top: 64px;
  & .counter {
    display: flex;
    align-items: center;
    font-size: 28px;
    line-height: 35px;
    & .number {
      background: rgba(255, 255, 255, 0.7);
      padding: 5px 13px;
      border-radius: 7px;
      color: #00284F;
    }
    & .increment,
      .decrement {
      cursor: pointer;
      border: none;
      background: none;
      padding: 10px;
      font-size: 20px;
      color: rgba(0, 40, 79, 0.4);
    }
  }
  & .cart-btn {
    cursor: pointer;
    background: #69C522;
    border-radius: 40px;
    padding: 15px 170px;
    display: flex;
    align-items: center;
    font-weight: 500;
    font-size: 18px;
    line-height: 27px;
    color: #FFFFFF;
  }
}
</style>