<template>
<div class="calculator-container">
  <header class="calculator-header">
      <h1 class="calculator-header__heading">Vcalc</h1>
      <section class="calculator-screen">
        <div class="calculator-screen-wrapper">
            <span class="calculator-screen-wrapper__all"> 7 + 8 + 9 </span>
           <span class="calculator-screen-wrapper__current">7</span>
        </div>
      </section>
  </header>
  <main class="calculator-operator">
    <button class="calculator-operator__item">%</button>
    <button class="calculator-operator__item">√</button>
    <button class="calculator-operator__item">x²</button>
    <button class="calculator-operator__item">1/x</button>
    <button class="calculator-operator__item">CE</button>
    <button class="calculator-operator__item">C</button>
    <button class="calculator-operator__item">←</button>
    <button class="calculator-operator__item">÷</button>
    <button class="calculator-operator__item">7</button>
    <button class="calculator-operator__item">8</button>
    <button class="calculator-operator__item">9</button>
    <button class="calculator-operator__item">x</button>
    <button class="calculator-operator__item">4</button>
    <button class="calculator-operator__item">5</button>
    <button class="calculator-operator__item">6</button>
    <button class="calculator-operator__item">-</button>
    <button class="calculator-operator__item">1</button>
    <button class="calculator-operator__item">2</button>
    <button class="calculator-operator__item">3</button>
    <button class="calculator-operator__item">+</button>
    <button class="calculator-operator__item">±</button>
    <button class="calculator-operator__item">0</button>
    <button class="calculator-operator__item">.</button>
    <button class="calculator-operator__item">=</button>
  </main>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {};
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.calculator-container {
  max-width: 400px;
  width: 100%;
  margin: 0 auto;
  box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
}

.calculator-header {
  padding: 4px 8px;
  margin-bottom: 8px;
  border-radius: 4px;
  &__heading {
    text-align: center;
    font-size: 24px;
    padding: 8px;
  }
}

.calculator-screen {
  display: flex;
  justify-content: flex-end;
  background: lighten( #000, 95) ;

  padding: 4px 8px;
  border-radius: 4px;
  .calculator-screen-wrapper {
    display: flex;
    flex-direction: column;
    &__all {
      text-align: right;

    }
    &__current {
      text-align: right;
      font-size: 32px;
      font-weight: bold;
    }
  }
}

.calculator-operator {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);

  &__item {
    padding: 16px 12px;
    width: calc(25% - 8px);
    margin: 4px;
    font-size: 20px;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
    &:hover {
      background-color: darken(#fff,10)
    }
  }
}
</style>
