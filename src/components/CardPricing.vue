<template>
  <div class="card-pricing">
    <div class="container-slider">
      <div class="container-views-price">
        <p class="page-views">{{ isPageViews }} pageviews</p>
        <p class="price">
          ${{ isPrice }}.00
          <span class="time">/ {{ isTime }}</span>
        </p>
      </div>
      <input @input="handleStyle($event)"  type="range" name="price-slider" v-model="range" class="price-slider" min="1" max="5" step="1" aria-valuemin="1" aria-valuemax="5" aria-valuenow="3" label="price slider">
      <div class="container-billing">
        <p class="monthly-billing">Monthly Billing</p>
        <label class="switch">
          <input type="checkbox" class="interval-switch" aria-checked="false" aria-label="yearly payment switch">
          <span @click="toggleSlider" :class="{active: isYearly}" class="toggle-slider"></span>
        </label>
        <p class="yearly-billing">Yearly Billing</p>
        <p class="yearly-discount-lg">25% discount</p>
        <p class="yearly-discount-sm">-25%</p>
      </div>
    </div>
    <div class="container-description">
      <div class="benefits">
        <p class="benefit">Unlimited websites</p>
        <p class="benefit">100% data ownership</p>
        <p class="benefit">Email reports</p>
      </div>
      <div class="start">
        <button class="btn-trial">Start my trial</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isYearly: false,
      range: 3,
      prices: {
        1: {
          views: '10K',
          price: 8
        },
        2: {
          views: '50K',
          price: 12
        },
        3: {
          views: '100K',
          price: 16
        },
        4: {
          views: '500K',
          price: 24
        },
        5: {
          views: '1M',
          price: 36
        },
      }
    }
  },
  methods: {
    toggleSlider() {
      this.isYearly = !this.isYearly
    },
    handleStyle(e) {
      let range = e.target 
      let max = range.max
      let min = range.min
      let value = range.value
      const styleVal = (value - min) / (max - min) * 100
      range.style.background = 'linear-gradient(to right, hsl(174, 77%, 80%) 0%, hsl(174, 77%, 80%) ' + styleVal + '%, hsl(224, 65%, 95%) ' + styleVal + '%, hsl(224, 65%, 95%) 100%)'
    }
  },
  computed: {
    isPrice() {
      let price = this.prices[this.range].price
      return this.isYearly ? price * 9 : price
    },
    isTime() {
      return this.isYearly === true ? 'year' :  'month'
    },
    isPageViews() {
      return this.prices[this.range].views
    }
  }
}
</script>

<style>
.card-pricing {
  position: relative;
  margin: auto;
  margin-top: 90px;
  width: 540px;
  height: 400px;
  background-color: hsl(0, 0%, 100%);
  border-radius: 1rem;
  box-shadow: 0px 15px 15px 7px hsl(224deg, 65%, 95%);
}

.container-slider {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 260px;
  padding: 0px 40px;
}

.container-views-price {
  width: 100%;
  height: auto;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  align-items: center;
  position: absolute;
  top: 40px;
}

.container-views-price .page-views {
  position: relative;
  font-size: 0.93rem;
  color: var(--clr-grey-blue);
  letter-spacing: 0.1rem;
  text-transform: uppercase;
  white-space: nowrap;
  left: -30px;
}

.container-views-price .price {
  font-size: 2.6rem;
  font-weight: 800;
}

.container-views-price .price .time {
  font-size: 1rem;
  color: var(--clr-grey-blue);
  font-weight: 600;
}

.price-slider {
  position: relative;
  width: 100%;
  cursor: pointer;
  top: 15px;
}

.price-slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 40px;
  height: 40px;
  background-image: url(../assets/images/icon-slider.svg);
  background-repeat: no-repeat;
  background-position: center center;
  background-color: hsl(174, 86%, 45%);
  border-radius: 50%;
  cursor: pointer;
  box-shadow: 0px 10px 30px 2px hsl(174, 86%, 45%);
}

.price-slider::-webkit-slider-thumb:hover {
  opacity: 0.8;
  transition: linear 300ms;
} 

.price-slider::-moz-range-thumb {
  width: 40px;
  height: 40px;
  background-image: url(../assets/images/icon-slider.svg);
  background-repeat: no-repeat;
  background-position: center center;
  background-color: hsl(174, 86%, 45%);
  border-radius: 50%;
  cursor: pointer;
  box-shadow: 0px 15px 15px 7px hsl(174, 86%, 45%);
}

.price-slider::-moz-range-thumb:hover {
  opacity: 0.8;
  transition: linear 300ms; 
}

.container-billing {
  position: relative;
  width: 100%;
  height: auto;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  top: 75px;
  padding: 0 20px 0 0;
}

.container-billing > p {
  margin: 0 8px;
}

.container-billing .monthly-billing, .container-billing .yearly-billing {
  color: var(--clr-grey-blue);
  font-size: 0.86rem;
}

.switch {
  position: relative;
  display: inline-block;
  width: 43px;
  height: 22px;
}

.switch input {
  width: 43px;
  height: 22px;
}

.toggle-slider {
  position: absolute;
  cursor: pointer;
  inset: 0;
  background-color: hsl(223, 50%, 87%);
  transition: background-color 300ms ease-in-out;
  border-radius: 22px;
}

.toggle-slider:hover {
  background-color: hsl(174deg 70% 61%);
}

.toggle-slider::before {
  border-radius: 50%;
  position: absolute;
  content: "";
  height: 14px;
  width: 14px;
  left: 4px;
  bottom: 4px;
  background-color: hsl(0, 0%, 100%);
  transition: left 300ms ease-out;
}

.active::before {
  left: 24px;
  transition: left 300ms ease-out
}

.container-billing .yearly-discount-lg {
  background-color: hsl(14, 92%, 95%);
  color: var(--clr-light-red);
  font-size: 0.86rem;
  padding: 3px 5px;
  border-radius: 20px;
}

 .container-billing .yearly-discount-sm {
   display: none;
 }

.container-description {
  display: flex;
  width: 100%;
  height: 140px;
  border-top: 1px solid hsl(224, 65%, 95%);
}

.container-description .benefits {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  width: 50%;
  color: hsl(225, 20%, 60%);
  padding-left: 40px;
}

.container-description .benefits .benefit {
  font-size: 0.86rem;
  padding: 5px;
  background-image: url(../assets/images/icon-check.svg);
  background-repeat: no-repeat;
  background-size: 10px;
  padding-left: 20px;
  background-position: left center;
}

.container-description .start {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 50%;
}

.container-description .start .btn-trial {
  width: 170px;
  height: 42px;
  border-radius: 42px;
  color: hsl(226, 100%, 87%);
  background-color: hsl(227, 35%, 25%);
  border: none;
  cursor: pointer;
}

.container-description .start .btn-trial:hover {
  color: hsl(0, 0%, 100%);
   transition: color 300ms ease-out;
}

</style>