<template>
  <div>
    <div class="row">
    <button @click="randomStart()" class="btn btn-info">Start{{Label}}</button>
    <p>{{randomChar}}</p>
    <button @click="randomDamage()" class="btn btn-info">Actack{{Label}}</button>
    <p>{{randomAct}}</p>      
    </div>

  </div>
</template>

<script>
export default {
  data: function () {
    return {
      randomAct: "",
      counter: 0,
      fsize: 20,
      player: [
        { name: "Kirito", hp: 150, image: "" },
        { name: "Luffy", hp: 150, image: "" },
        { name: "Asuna", hp: 150, image: "" },
        { name: "Goku", hp: 150, image: "" },

      ],
      randomChar: "",

      //ค่าพลังของ ตัวละคร เข้าถึงโดย player[1].hp -= 20
      monster: [
        { name: "Jason", hp: 150, image: "" },
        { name: "Fizzer", hp: 150, image: "" },
      ],
    };
  },

  props: {
    Label: String,
  },

  methods: {
    randomStart: function () {
      var chosenNumber = Math.floor(Math.random() * this.player.length);
      this.randomChar = this.player[chosenNumber];
    },
    randomDamage: function () {
      this.randomAct = Math.floor(Math.random() * (10 - 1 + 1)) + 1;
    },

    /* randomStart: function () {
      this.randomChar = Math.floor(Math.random() * (10 - 1 + 1)) + 1
    },
    randomDamage: function () {
      this.randomAct = Math.floor(Math.random() * (10 - 1 + 1)) + 1
    },*/
  },
};
</script>

<style>
</style>