<template>
  <main id="calculator">
    <div id="display">
      <!-- <div id="operation" class="color-nv3">3216 + 65415</div> -->
      <div id="typed" class="color-nv1">{{ current || '0' }}</div>
    </div>

    <div id="keyboard">
      <div class="keyboard-row">
        <div @click="clear" class="button color-extra bg-nv2">C</div>
        <div @click="sign" class="button color-nv2 bg-nv2">+/-</div>
        <div @click="percent" class="button color-nv2 bg-nv2">%</div>
        <div @click="division" class="button color-nv2 bg-nv2">/</div>
      </div>

      <div class="keyboard-row">
        <div @click="append('7')" class="button color-nv1 bg-nv1">7</div>
        <div @click="append('8')" class="button color-nv1 bg-nv1">8</div>
        <div @click="append('9')" class="button color-nv1 bg-nv1">9</div>
        <div @click="multiplication" class="button color-nv2 bg-nv2">*</div>
      </div>

      <div class="keyboard-row">
        <div @click="append('4')" class="button color-nv1 bg-nv1">4</div>
        <div @click="append('5')" class="button color-nv1 bg-nv1">5</div>
        <div @click="append('6')" class="button color-nv1 bg-nv1">6</div>
        <div @click="subtraction" class="button color-nv2 bg-nv2">-</div>
      </div>

      <div class="keyboard-row">
        <div @click="append('1')" class="button color-nv1 bg-nv1">1</div>
        <div @click="append('2')" class="button color-nv1 bg-nv1">2</div>
        <div @click="append('3')" class="button color-nv1 bg-nv1">3</div>
        <div @click="sum" class="button color-nv2 bg-nv2">+</div>
      </div>

      <div class="keyboard-row">
        <div @click="append('0')" id="btn-0" class="button color-nv1 bg-nv1">0</div>
        <div @click="dot" class="button color-nv2 bg-nv2">.</div>
        <div @click="equal" class="button color-nv2 bg-nv2">=</div>
      </div>

      <div style="clear:both;"></div>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      previous: null,
      current: '',
      operator: 'null',
      operatorClicked: false,
    };
  },
  methods: {
    clear() {
      this.current = '';
    },
    sign() {
      this.current = this.current.charAt(0) === '-' ? this.current.slice(1) : `-${this.current}`;
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`;
    },
    append(number) {
      if (this.operatorClicked) {
        this.current = '';
        this.operatorClicked = false;
      }
      this.current = `${this.current}${number}`;
    },
    dot() {
      if (this.current.indexOf('.') === -1) {
        this.append('.');
      }
    },
    setPrevious() {
      this.previous = this.current;
      this.operatorClicked = true;
    },
    division() {
      this.operator = (a, b) => a / b;
      this.setPrevious();
    },
    multiplication() {
      this.operator = (a, b) => a * b;
      this.setPrevious();
    },
    subtraction() {
      this.operator = (a, b) => a - b;
      this.setPrevious();
    },
    sum() {
      this.operator = (a, b) => a + b;
      this.setPrevious();
    },
    equal() {
      this.current = `${this.operator(
        parseFloat(this.current),
        parseFloat(this.previous),
      )}`;
      this.pre
    },
  },

};
</script>

<style scoped>
/*GERAL ==============================*/
body{
  font-family: 'Baloo Paaji 2', cursive;
}


/*CORES ==============================*/
.color-nv1 { color: #FFFFFF; }
.color-nv2 { color: #AEB3BA; }
.color-nv3 { color: #727B86; }
.color-extra { color: #D95D4E; }

.bg-nv1 { background-color: #425062; }
.bg-nv2 { background-color: #404D5E; }
.bg-nv1:hover, .bg-nv2:hover { background-color: #E0B612; }


/*CALCULADORA ==============================*/
#calculator{
  width: 340px;
  margin: 0 auto;

  display: block;

  background-color: #3A4655;
}

/*TELA ===============*/
#display{
  padding: 25px;
}

#operation{
  width: 100%;

  display: block;
  float: right;

  text-align: right;

  border-bottom: 1px dashed #727B86;
}

#typed{
  width: 100%;
  height: 88px;

  display: block;
  float: right;

  font-size: 50px;
  text-align: right;
}

/*TECLADO ===============*/
#keyboard{
  display: block;
  clear:both;
}

.keyboard-row{
  display: block;
}

.button{
  width: 81px;
  height: 81px;
  margin: 2px;

  display: inline-block;
  float: left;

  font-size: 35px;
  line-height: 81px;
  text-align: center;
}

#btn-0{
  width: 166px;
}

</style>
