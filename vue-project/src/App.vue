<script setup lang="ts">
  import {faker } from "@faker-js/faker/locale/ru";

  const items:{isSale: boolean, cost: number, saleCost: number, name: String}[]=[];
  let iterator=0;
  while(iterator<8) {
    items.push({isSale: Math.random()>0.5 ? true : false, cost: Math.round(Math.random()*10000), saleCost: Math.round(Math.random()*10000), name: faker.commerce.productName() })
    iterator++
  }

</script>

<template>
  <section>
    <div class="header-wrapper-up base-wrapper">
      <ul>
        <li>Доставка и оплата</li>
        <li>Гарантия и возврат</li>
        <li>EN</li>
      </ul>
    </div>
    <div class="header-wrapper-down base-wrapper">
      <img class="logo" src="@/assets/images/logo.svg"/>
      <ul>
        <li>КAТАЛОГ</li>
        <li>О КОМПАНИИ</li>
        <li>КОНТАКТЫ</li>
      </ul>
      <div class="header-wrapper-down-buttons-section">
        <div class="buttons-section-input-icon-group">
          <input placeholder="Какой то текст"/>
          <img src="@/assets/images/search.svg">
        </div>
        <button class="basket-button">
          <img src="@/assets/images/basket.svg">
          <p>Корзина</p>
          <div class="basket-badge">
            3
          </div>
        </button>
      </div>
    </div>
  </section>
  <section  class='base-wrapper'>
    <div class="content-wrapper">
      <h1>Результаты поиска</h1>
      <div class="content-block-wrapper">
        <div v-for="(item, index) in items" class="item">
          <img src="@/assets/images/item.png"/>
          <p class="item-name">{{item.name}}</p>
          <div class="typography-wrapper">
            <p class="sale-cost" v-if="item.isSale">{{`${item.saleCost} ₽`}}</p>
            <p class="base-cost" v-if="!item.isSale">{{`${item.cost} ₽`}}</p>
            <p class="base-cost-underline" v-if="item.isSale">{{`${item.cost} ₽`}}</p>
          </div>
          <div v-if="item.isSale" class="item-sale-block">
            <p>Акция</p>
          </div>
        </div>
      </div>
    </div>
  </section>
  <section class='base-wrapper footer-wrapper'>
    <div>
      <img class="footer-logo" src="@/assets/images/logoFooter.svg"/>
      <p class="text-politic">Этот сайт защищен от спама службой reCAPTCHA Google. Политика конфиденциальности/Условия предоставления услуг</p>
    </div>
    <div >
      <div class="info-footer-block">
        <p class="footer-text-title">Адрес</p>
        <span>Текст, Текст, Текст</span>
      </div>
      <div class="info-footer-block">
        <p class="footer-text-title">Контакты</p>
        <p>Email: urban.dwelling@yandex.com</p>
        <p>Телефон: 8 (999) 999-99-99</p>
      </div>
    </div>
    <div class="services-footer-block-wrapper">
      <p class="footer-text-title">Услуги</p>
      <p>Каталог</p>
      <p>Контакты</p>
      <p>Доставка и оплата</p>
      <p>Гарантия и возврат</p>
    </div>
    <div class="card-footer-block-wrapper" >
      <p>Публичная оферта</p>
      <p>Политика персональных данных</p>
      <div class="card-footer-card-icon">
        <img src="@/assets/images/mir.svg" />
        <img src="@/assets/images/visa.svg" />
        <img src="@/assets/images/masterCard.svg" />
      </div>
    </div>
  </section>
</template>

<style scoped>
.header-wrapper-up{
  background: #231815;
  height: 40px;
  display: flex;
  justify-content: flex-end;
}

.header-wrapper-up ul{
  color: white;
  display: flex;
  align-items: center;
  gap: 70px;
  list-style-type: none;
  height: 100%;
}
.logo{
  margin-right:242px;
}
.header-wrapper-down{
  padding-top: 12px !important;
  height: 80px;
  display: flex;
  align-items: center;
}

.header-wrapper-down ul{
  color: black;
  margin-right: 132px;
  font-family: Lato;
  font-size: 16px;
  font-weight: 600;
  line-height: 16px;
  text-align: left;
  display: flex;
  align-items: center;
  gap: 100px;
  list-style-type: none;
  height: 100%;
}
.header-wrapper-down-buttons-section{
  display: flex;
  gap: 20px;
}
.buttons-section-input-icon-group{
  display: flex;
  padding: 10px 16px;
  width: 170px;
  height: 40px;
  border: 1px solid #F5F5F5;
  border-radius: 20px;
}

.buttons-section-input-icon-group input{
  border: none;
  outline:none;
  width: 90%;
}
.card-footer-block-wrapper{
  text-align: end;
  color: #808080;
}
.basket-button{
  gap: 12px;
  display: flex;
  align-items: center;
  position: relative;
  width: 140px;
  height: 40px;
  padding: 4px 20px;
  background: black;
  border: none;
  color: white;
  border-radius: 20px;
}
.content-wrapper{
  padding-top: 40px;
  padding-bottom: 60px;
}
.content-block-wrapper{
  display: grid;
  grid-template-columns:25% 25% 25% 25%;
  grid-row-gap: 50px;
  grid-column-gap: 30px;

}
.footer-text-title{
  font-family: Lato;
  font-size: 18px;
  font-weight: 700;
  line-height: 18px;
  text-align: left;
  color: #FFFFFF;

}
.card-footer-card-icon{
  margin-top: 72px;
  display: flex;
  gap: 33px;
  justify-content: end;
}
.basket-badge{
  background: white;
  color: black;
  position: absolute;
  width: 18px;
  border-radius: 10px;
  top: 6px;
  left: 30px;
}
.item{
  position: relative;
}
.item img{
  object-fit: contain;
  width: 100%;
  border-radius: 20px;
  max-width: 320px;
  max-height: 477px;
}
.item-name{
  font-family: Lato;
  font-size: 18px;
  font-weight: 700;
  line-height: 25.2px;
  text-align: left;
  color: #231815;
}
.item-sale-block{
  position: absolute;
  width: 126px;
  height: 38px;
  background: black;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 20px;
  top:10px;
  left: 10px;
}
.info-footer-block p{
 margin-bottom: 10px;
}
.info-footer-block{
  margin-bottom: 40px;
}

.base-cost{
  font-family: Lato;
  font-size: 22px;
  font-weight: 700;
  line-height: 30.8px;
  text-align: left;
}
.base-cost-underline{
  font-family: Lato;
  font-size: 22px;
  font-weight: 700;
  line-height: 30.8px;
  text-align: left;
  text-decoration-line: line-through;
}
.typography-wrapper{
  display: flex;
  gap: 10px;
}
.sale-cost{
  font-family: Lato;
  font-size: 22px;
  font-weight: 600;
  line-height: 30.8px;
  text-align: left;
  color: #E45302;
}
.footer-wrapper{
  padding-top: 60px !important;
  padding-bottom: 60px !important;
  background: black;
  display: flex;
  gap: 110px;
 color: #F5F5F5;
}
.footer-logo{
  margin-bottom: 53px;
}
.services-footer-block-wrapper p{
  margin-bottom: 20px;
}
.text-politic{
  width: 322px;
  font-family: Roboto;
  font-size: 16px;
  font-weight: 400;
  line-height: 20.8px;
  text-align: left;
  color: #808080;
}
.base-wrapper{
  padding: 0 260px;
}
</style>
