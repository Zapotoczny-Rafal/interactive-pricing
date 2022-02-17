<template>
  <div class="circle-container"></div>
  <div class="main-container">
    <h1>Simple, traffic-based pricing</h1>
    <h2>Sign-up for our 30-day trial. No credit card required.</h2>
    <CardPricing />
  </div>
</template>

<script>
import CardPricing from './components/CardPricing'

export default {
  name: 'App',
  components: { CardPricing }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@600;800&display=swap');

:root {
  --clr-black: hsl(227, 35%, 25%);
  --clr-grey-blue: hsl(225, 20%, 60%);
  --clr-light-red: hsl(15, 100%, 70%);
  --clr-pale-blue: hsl(226, 100%, 87%);
}

* {
  margin: 0;
  padding: 0;
  list-style: none;
  box-sizing: border-box;
  -webkit-tap-highlight-color: transparent;
}

html {
  font-size: 15px;
}

html, body {
  width: 100%;
  height: 100%;
  background-color: hsl(230, 100%, 99%);
}

input[type=range] {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  height: 8px;
  background: linear-gradient(to right, hsl(174, 77%, 80%) 0%,
                                        hsl(174, 77%, 80%) 50%, 
                                        hsl(224, 65%, 95%) 50%,
                                        hsl(224, 65%, 95%) 100%);
  border-radius: 9px;
}

#app {
  font-family: 'Manrope', sans-serif;
  text-align: center;
  color: var(--clr-black);
  width: 100%;
  height: 100%;
  background-color: hsl(230, 100%, 99%);
  background-image: url(assets/images/bg-pattern.svg);
  background-position: left top;
  background-size: auto;
  background-repeat: no-repeat;
}

.circle-container {
  z-index: 0;
  position: absolute;
  width: 100%;
  height: 150px;
  background-image: url(assets/images/pattern-circles.svg);
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;
  top: 64px;
}

.main-container {
  position: relative;
  top: 105px; 
}

.main-container h1 {
  font-size: 2rem;
  font-weight: 800;
}
.main-container h2 {
  font-size: 1rem;
  font-weight: 600;
  color: var(--clr-grey-blue);
  margin-top: 11px;
}

@media screen and (min-width: 90em) {
  #app {
    background-image: url(assets/images/bg-pattern.svg), url(assets/images/bg-pattern.svg), url(assets/images/bg-pattern.svg);
    background-position: left top, 1250px top, 2500px top;
  }

  .container-billing .yearly-discount-sm {
    display: none;
  }
}

@media screen and (max-width: 41em) {
  #app {
    background-position: left -3em;
  }

  .container-billing .yearly-discount-lg {
    display: none;
  }

  .main-container h1 {
    font-size: 1.26rem;
    letter-spacing: 0.5px;
  }

  .main-container h2 {
    margin: auto;
    margin-top: 9px;
    font-size: 0.87rem;
    letter-spacing: 0.3px;
    width: 190px;
    line-height: 23px;
  }

  .card-pricing {
    width: 325px;
    height: 475px;
    margin-top: 65px;
  }

  .card-pricing .container-slider {
    padding: 0px 23px;
  }

  .container-views-price {
    display: flex;
    justify-content: center;
  }

  .container-views-price .price {
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    top: 95px;
    width: 100%;
    font-size: 2.13rem;
  }
  
  .container-views-price .price .time {
    margin-left: 5px;
  }

  .price-slider {
    width: 280px;
    position: absolute;
    top: 90px;
  }

  .container-views-price .page-views {
    font-size: 0.8rem;
    top: -15px;
    left: 0px;
    position: absolute;
    width: 100%;
  }

  .container-billing {
    padding: 0 5px 0 0;
    position: absolute;
    top: 200px;
  }

  .container-billing > p {
    margin: 3px;
  }

  .container-description {
    flex-direction: column;
    width: 100%;
    justify-content: center;
    align-items: center;
  }

  .container-description .benefits {
    flex-direction: row;
    flex-wrap: wrap;
    position: relative;
    top: 15px;
    right: 20px;
    width: 200px
  }

  .container-description .start {
    position: relative;
    top: 35px;
  }
}

</style>
