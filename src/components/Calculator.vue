<template>
<div class="calculator-container">
  <header class="calculator-header">
      <h1 class="calculator-header__heading">Vcalc</h1>
      <section class="calculator-screen">
        <div class="calculator-screen-wrapper">
           <span v-if="memory" class="calculator-screen-wrapper__all"> {{memory}} </span>
           <span v-else class="calculator-screen-wrapper__all"> ... </span>
           <span v-if="!isOperation" class="calculator-screen-wrapper__current">{{current}}</span>
            <span v-else class="calculator-screen-wrapper__current">{{calculated}}</span>
        </div>
      </section>
  </header>
  <main class="calculator-operator">
    <button @click="onPress" name="%" class="calculator-operator__item">%</button>
    <button @click="onPress" name="√" class="calculator-operator__item">√</button>
    <button @click="onPress" name="x²" class="calculator-operator__item">x²</button>
    <button @click="onPress" name="1/x" class="calculator-operator__item">1/x</button>
    <button @click="onPress" name="CE" class="calculator-operator__item">CE</button>
    <button @click="onPress" name="C" class="calculator-operator__item">C</button>
    <button @click="onPress" name="←" class="calculator-operator__item">←</button>
    <button @click="onPress" name="÷" class="calculator-operator__item">÷</button>
    <button @click="onPress" name="7" class="calculator-operator__item">7</button>
    <button @click="onPress" name="8" class="calculator-operator__item">8</button>
    <button @click="onPress" name="9" class="calculator-operator__item">9</button>
    <button @click="onPress" name="x" class="calculator-operator__item">x</button>
    <button @click="onPress" name="4" class="calculator-operator__item">4</button>
    <button @click="onPress" name="5" class="calculator-operator__item">5</button>
    <button @click="onPress" name="6" class="calculator-operator__item">6</button>
    <button @click="onPress" name="-" class="calculator-operator__item">-</button>
    <button @click="onPress" name="1" class="calculator-operator__item">1</button>
    <button @click="onPress" name="2" class="calculator-operator__item">2</button>
    <button @click="onPress" name="3" class="calculator-operator__item">3</button>
    <button @click="onPress" name="+" class="calculator-operator__item">+</button>
    <button @click="onPress" name="±" class="calculator-operator__item">±</button>
    <button @click="onPress" name="0" class="calculator-operator__item">0</button>
    <button @click="onPress" name="." class="calculator-operator__item">.</button>
    <button @click="onPress" name="=" class="calculator-operator__item">=</button>
  </main>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      current: "",
      memory: "",
      isOperation: false,
      numerals: ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9"]
    };
  },
  methods: {
    onPress(event) {
      let key = event.target.name;

      if (this.isOperation) {
        this.current = "";
      }

      if (this.numerals.includes(key)) {
        this.current += key;
        this.isOperation = false;
      } else {
        if (this.isOperation) {
          if (key == "=") {
            this.current = this.calculated;
            this.memory = "";
            this.isOperation = false;
          } else {
            return;
          }
        }

        switch (key) {
          case "+":
          case "-":
            if (this.current == "") return;
            this.memory += ` ${this.current} ${key}`;
            this.isOperation = true;
            break;
          case "x":
            if (this.current == "") return;
            key = "*";
            this.memory += ` ${this.current} ${key}`;
            this.isOperation = true;
            break;
          case "÷":
            if (this.current == "") return;
            key = "/";
            this.memory += ` ${this.current} ${key}`;
            this.isOperation = true;
            break;
          case "=":
            if (this.memory == "") return;
            this.memory += ` ${this.current} ${key}`;
            this.current = this.calculated;
            this.memory = "";
            this.isOperation = false;
            break;
          case "←":
            this.current = String(this.current);
            let removedOne = this.current.trim().slice(0, -1);
            this.current = removedOne;
            break;
          case "CE":
            this.current = "";
            break;
          case "C":
            this.current = "";
            this.memory = "";
            break;
          case "±":
            this.current = String(this.current);
            if (this.current == "") return;

            if (this.current.slice(0, 1) == "-") {
              this.current = this.current.substring(1, this.current.length);
            } else {
              this.current = "-" + this.current;
            }
            break;
          case "x²":
            if (this.current == "") return;
            this.current = Number(this.current);
            this.current = Math.pow(this.current, 2);
            break;
          case "√":
            if (this.current == "") return;
            this.current = Number(this.current);
            this.current = Math.sqrt(this.current);
            break;
          case "1/x":
            if (this.current == "") return;
            this.current = Number(this.current);
            this.current = 1 / this.current;
            break;
          case ".":
            this.current = String(this.current);
            if (
              this.current == "" ||
              Number(this.current) % 1 != 0 ||
              this.current.slice(0, -1) == "."
            )
              return;

            this.current = this.current + ".";
        }
      }
    }
  },
  computed: {
    calculated() {
      return eval(
        this.memory
          .trim()
          .slice(0, -1)
          .trim()
      );
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.calculator-container {
  max-width: 400px;
  width: 100%;
  margin: 0 auto;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
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
  background: lighten(#000, 95);
  width: 100%;
  height: 64px;
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
      background-color: darken(#fff, 10);
    }
  }
}
</style>
