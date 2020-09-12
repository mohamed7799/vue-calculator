<template>
  <div id="cal">
    <div id="cal_container">
      <div class="display">0</div>
      <div class="grid_item gray">C</div>
      <div class="grid_item gray">+/-</div>
      <div class="grid_item gray">%</div>
      <div class="grid_item orange">/</div>
      <div class="grid_item gray">7</div>
      <div class="grid_item gray">8</div>
      <div class="grid_item gray">9</div>
      <div class="grid_item orange">*</div>
      <div class="grid_item gray">4</div>
      <div class="grid_item gray">5</div>
      <div class="grid_item gray">6</div>
      <div class="grid_item orange">-</div>
      <div class="grid_item gray">1</div>
      <div class="grid_item gray">2</div>
      <div class="grid_item gray">3</div>
      <div class="grid_item orange">+</div>
      <div class="grid_item gray zero">0</div>
      <div class="grid_item gray">.</div>
      <div class="grid_item gray">=</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "calculator",
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
