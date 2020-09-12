<template>
  <div id="cal">
    <div id="cal_container">
      <div class="display">{{ display || "0" }}</div>
      <div @click="clear" class="grid_item gray">C</div>
      <div @click="nagv" class="grid_item gray">+/-</div>
      <div @click="precent" class="grid_item gray">%</div>
      <div @click="div" class="grid_item orange">/</div>
      <div @click="append('7')" class="grid_item gray">7</div>
      <div @click="append('8')" class="grid_item gray">8</div>
      <div @click="append('9')" class="grid_item gray">9</div>
      <div @click="mul" class="grid_item orange">*</div>
      <div @click="append('4')" class="grid_item gray">4</div>
      <div @click="append('5')" class="grid_item gray">5</div>
      <div @click="append('6')" class="grid_item gray">6</div>
      <div @click="sub" class="grid_item orange">-</div>
      <div @click="append('1')" class="grid_item gray">1</div>
      <div @click="append('2')" class="grid_item gray">2</div>
      <div @click="append('3')" class="grid_item gray">3</div>
      <div @click="add" class="grid_item orange">+</div>
      <div @click="append('0')" class="grid_item gray zero">0</div>
      <div @click="dot" class="grid_item gray">.</div>
      <div @click="equal" class="grid_item gray">=</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "calculator",
  data() {
    return {
      prev: "",
      display: "",
      opClicked: false,
      op: null,
    };
  },
  methods: {
    clear() {
      this.display = "";
    },
    nagv() {
      console.log(this.display.charAt(0));
      this.display =
        this.display.charAt(0) === "-"
          ? this.display.slice(1)
          : `-${this.display}`;
    },
    precent() {
      if (this.display !== "0") {
        this.display = `${parseFloat(this.display) / 100}`;
      }
    },
    append(num) {
      if (this.opClicked) {
        this.display = "";
        this.opClicked = false;
      }
      if (this.display !== "" || num !== "0") {
        if (this.display === "0") {
          this.display = num;
        } else {
          this.display = `${this.display}${num}`;
        }
      }
    },
    dot() {
      if (this.display.indexOf(".") === -1) {
        this.append(".");
      }
    },
    setPrev() {
      this.prev = this.display;
      this.opClicked = true;
    },
    add() {
      this.op = (a, b) => {
        return a + b;
      };
      this.setPrev();
    },
    div() {
      this.op = (a, b) => {
        return a / b;
      };
      this.setPrev();
    },
    mul() {
      this.op = (a, b) => {
        return a * b;
      };
      this.setPrev();
    },
    sub() {
      this.op = (a, b) => {
        return a - b;
      };
      this.setPrev();
    },
    equal() {
      this.display = `${this.op(
        parseFloat(this.prev),
        parseFloat(this.display)
      )}`;
      this.prev = "";
    },
  },
};
</script>

<style lang="scss" scoped>
#cal {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 1.5rem;
}

#cal_container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: minmax(50px, auto);
  grid-gap: 1px;
  background-color: #797979;
  box-shadow: 0 0 10px 5px #d2cece;
}
.display {
  background-color: #2c2c2c;
  grid-column: 1/5;
  color: white;
  display: flex;
  align-items: center;
  flex-direction: row-reverse;
  padding: 1rem 1.5rem;
}
.grid_item {
  cursor: pointer;
  justify-self: stretch;
  align-self: center;
  padding: 1rem;
  display: flex;
  justify-content: center;
}
.zero {
  grid-column: 1/3;
}

.orange {
  background-color: rgb(255, 177, 60);
  color: white;
}
.gray {
  background-color: rgb(201, 201, 201);
}
</style>
