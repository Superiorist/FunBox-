<template>
  <div class="home">
    <div class="main__container">
      <h1 class="header__h1">Ты сегодня покормил кота?</h1>
      <div class="cards__container"> 
        <div class="card-flex" v-for="good,index in goods" :key="index" >
          <div class="cad-img" :style="{ backgroundImage: 'url('+ good.src+')' }"></div>
          <div class="background__border" 
              @click="!good.disabled? good.selected = !good.selected :good.selected = good.selected"
              @mouseover="good.hovered = true" 
              @mouseleave="good.hovered = false" 
              :class="{ 'swap-color__one':good.hovered,
                        'selected-one':good.selected,
                        'hover-two':good.selected && good.hovered,
                        'disabled-border':good.disabled}">
            <div class="good__container" :class="{ 
                        'disabled-pos':good.disabled}">
              <div class="flex__container"> 
                <p v-if="(!good.selected || good.hovered == false)" :class="{'disabled__txt':good.disabled}">{{good.transc}}</p>
                <p v-else-if="(good.selected && good.hovered)" :class="{'hover__p':good.selected && good.hovered}">{{good.quastion}}</p>
                <h1 class="main-title__h1" :class="{'disabled__txt':good.disabled}">{{good.title}}</h1>
                <h2 :class="{'disabled__txt':good.disabled}">{{good.with}}</h2>
                <a class="piece__a" :class="{'disabled__txt':good.disabled}" v-html="good.piece"></a>
                <div class="round" 
                  :class="{'swap-color__two':good.hovered, 
                         'selected-two':good.selected,
                         'hover-round-two':good.selected && good.hovered}">
                  <div class="killo">{{good.weight}}</div>
                  <h2 class="gramm">кг</h2>
                </div>
              </div>
            </div>
          </div>
           <a class="buy-sorry__a" v-if="(good.disabled)">{{good.sorry}}</a>
            <a class="buy-hover__a" v-else-if="(good.selected && good.hovered == true)">{{good.desc}}</a>
            <a class="buy-hover__a" v-else-if="(good.selected)">{{good.desc}}</a>
            <a class="buy__a" v-else>Чего сидишь? Порадуй котэ,<span class="buy-span__a">купи</span><span class="span__dot">.</span></a>
        </div>    
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'home',
  data() {
    return {
      goods: [
        { 
          selected:false,
          hovered:false,
          quastion:'Котэ не одобряет?',
          transc:'Сказочное заморское яство',
          title:'Нямушка', 
          with:'c фуа-гра',
          piece: '<b>10</b> порций <br>мышь в подарок',
          weight:'0,5',
          desc:'Печень утки разварная с артишоками.'
        },
         { 
          selected:true,
          hovered:false,
          quastion:'Котэ не одобряет?',
          transc:'Сказочное заморское яство',
          title:'Нямушка', 
          with:'c рыбой',
          piece:'<b>40</b> порций <br><b>2</b> мыши в подарок',
          weight:'2',
          desc:'Головы щучьи с чесноком да свежайшая сёмгушка.'
        },
         {
          disabled:true,
          selected:false,
          hovered:false,
          quastion:'Котэ не одобряет?',
          transc:'Сказочное заморское яство', 
          title:'Нямушка', 
          with:'c курицей',
          piece:'<b>100</b> порций <br><b>5</b> мышей в подарок<br>заказчик доволен',
          weight:'5',
          desc:'Филе из цыплят с трюфелями в бульоне.',
          sorry:'Печалька, с курой закончился.'
        },
      ],
      targetGood: -1
    }
  },
}
</script>


<style>
.main__container {
  background-image: url('../assets/img/pattern.png');
  width: 100%;
  background-size: cover;
  height: 100vh;
  background-repeat: no-repeat;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
    
}
.cards__container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 24px;
  gap: 80px;
  flex-wrap: wrap;
}
.background__border{
  width: 320px;
  height: 480px;
  padding: 4px;
  background: linear-gradient(135deg, transparent 33px, #1698D9 0);
  box-sizing: border-box;
  border-radius: 12px;
  cursor: pointer;
}
.good__container {
  width: 100%;
  height: 100%;
  padding: 0;
  background: #fff;
  background: url('../assets/img/cat.jpg'),linear-gradient(135deg, transparent 32px, #fff 0);
  border-radius: 8px;
  background-repeat: no-repeat;
  background-position: bottom;
  box-sizing: border-box;
  padding: 21px 51px;
  position: relative;
}
.flex__container {
  display: flex;
    flex-direction: column;
}
.main-title__h1 {
  margin-left: -2.5px;
  margin-top: 5px;
}
.piece__a {
  margin-top: 15px;
  font-size: 14px;
  line-height: 16px;
}
.header__h1 {
  color: #fff;
  font-family: "mainfont";
  text-align: center;
}
.round {
  background-color: #1698D9;
  border-radius: 50%;
  width: 80px;
  height: 80px;
  font-weight: 400;
  font-size: 42px;
  line-height: 22px;
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: absolute;
  bottom: 16px;
  right: 16px;
}
.killo {
  font-weight: 400;
  font-size: 42px;
  line-height: 41px;
  color: #fff;
  font-family: 'Trebuchet MS';
  font-style: normal;
}
.gramm {
  font-weight: 400;
  font-size: 21px;
  line-height: 22px;
  color: #fff;
}
.buy__a {
  color: #fff;
  display: flex;
  justify-content: center;
  margin-top: 14px;
}
.buy-span__a {
  color: #1698D9;
  border-bottom: 1px dashed;
}
.buy-hover__a {
  color: #fff;
}
.buy-sorry__a {
  color: #FFFF66;
  display: flex;
  justify-content: center;
  margin-top: 14px;
}
.buy-hover__a {
  color: #fff;
  display: flex;
  justify-content: center;
  margin-top: 14px;
  font-size: 13px;
  line-height: 15px;
  width: 313px;
}
.swap-color__one {
  width: 320px;
  height: 480px;
  padding: 4px;
  background: #58a;
  background: linear-gradient(135deg, transparent 33px, #2EA8E6 0);
  box-sizing: border-box;
  border-radius: 12px;
}
.swap-color__two {
  background-color: #2EA8E6;
  border-radius: 50%;
  width: 80px;
  height: 80px;
  font-weight: 400;
  font-size: 42px;
  line-height: 22px;
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: absolute;
  bottom: 16px;
  right: 16px;
}
.selected-one {
  width: 320px;
  height: 480px;
  padding: 4px;
  background: linear-gradient(135deg, transparent 33px, #D91667 0);
  box-sizing: border-box;
  border-radius: 12px;
}
.selected-two {
  background-color: #D91667;
  border-radius: 50%;
  width: 80px;
  height: 80px;
  font-weight: 400;
  font-size: 42px;
  line-height: 22px;
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: absolute;
  bottom: 16px;
  right: 16px;
}
.disabled-pos {
  filter: contrast(1) grayscale(0.9) saturate(1);
}
.disabled__txt {
  color: #B3B3B3;
}
.disabled-border {
  width: 320px;
  height: 480px;
  padding: 4px;
  background: linear-gradient(135deg, transparent 33px, #B3B3B3 0);
  box-sizing: border-box;
  border-radius: 12px;
  cursor: pointer;
}
.hover-round-two {
  background-color: #E52E7A;
  border-radius: 50%;
  width: 80px;
  height: 80px;
  font-weight: 400;
  font-size: 42px;
  line-height: 22px;
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: absolute;
  bottom: 16px;
  right: 16px;
}

.hover-two {
  background-color:#E52E7A ;
  width: 320px;
  height: 480px;
  padding: 4px;
  background: linear-gradient(135deg, transparent 33px, #E52E7A 0);
  box-sizing: border-box;
  border-radius: 12px;
}
.hover__p {
  color: #E52E7A
}
 
@media (min-width: 1220px) {
  .main__container {
   height: 100vh;
  }
}
@media (min-width: 820px) and (max-width:1260px) {
 .main__container {
    box-sizing: border-box;
    padding: 0 60px;
    height: 100vh;
  }
}
@media (min-width: 380px) and (max-width:788px) {
 .main__container {
    box-sizing: border-box;
    padding: 0 60px;
    height: 100%;
  }
  .cards__container {
    gap: 30px;
  }
}
</style>