<template>
  <div>
    
    <button @click="randomStart()" class="btn btn-danger">Start{{Label}}</button>
    <div class="row">
      <div class="col-12">
        <button @click="randomDamage()" class="btn btn-info">Attack{{Label}}</button>
        <button @click="randomSpDamage()" class="btn btn-info">Special Attack{{Label}}</button>
      </div>
    </div>
    
    <p v-if="hp1 <= -1 ">
      <img src="https://cdn.discordapp.com/attachments/392353546332405763/746076980524613713/pngegg.png"/>
    </p>
    <p v-else-if="hp2 <= -1 ">
      <img src="https://cdn.discordapp.com/attachments/392353546332405763/746080751300247642/pngegg_2.png" height="500" width="700"/>
    </p>
    
    

    <div class="row">
      <div class="col-4 ">
        <p>{{randomPlayer}}</p>
        <p>HP : {{hp1}}</p> 
        <img :src="image1">
      </div>
      
      <div class="col-4">
        <br><br><br><br>
        <img src="https://cdn.discordapp.com/attachments/392353546332405763/746090155282006126/pngegg_6.png">
      </div>

      <div class="col-4">
        <p>{{randomMonster}}</p>
        <p>HP : {{hp2}}</p>
        <img :src="image2">
      </div>
      
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      randomPlayerAttack: "",
      randomMonsterAttack: "",
      randomSpAttack: "",
      image1:"",
      image2:"",
      hp1:" ",
      hp2:" ",
      
      player: [
        { name: "Naruto", hp: 160, image: "https://cdn.discordapp.com/attachments/709406382134263882/745700630621978634/pngegg_18.png" },
        { name: "Luffy", hp: 170, image: "https://cdn.discordapp.com/attachments/709406382134263882/745699838108106912/pngegg_16.png" },
        { name: "Jotaro", hp: 180, image: "https://cdn.discordapp.com/attachments/709406382134263882/745698358089351298/pngegg_11.png" },
        { name: "Goku", hp: 190, image: "https://cdn.discordapp.com/attachments/709406382134263882/745701713880809493/pngegg_21.png" },
      ],
      randomPlayer: "",
      //ค่าพลังของ ตัวละคร เข้าถึงโดย player[1].hp -= 20
      monster: [
        { name: "Majin Buu", hp: 250, image: "https://cdn.discordapp.com/attachments/709406382134263882/745697479609155594/pngegg_10.png" },
        { name: "Dr. Ottoput", hp: 220, image: "https://cdn.discordapp.com/attachments/709406382134263882/745701419905974412/pngegg_20.png" },
        { name: "Death Gun", hp: 210, image: "https://cdn.discordapp.com/attachments/709406382134263882/745691551497191525/pngegg_1.png" },
        { name: "Dio", hp: 200, image: "https://cdn.discordapp.com/attachments/709406382134263882/745698736616767508/pngegg_12.png" },
      ],
      randomMonster: "",
    };
  },

  props: {
    Label: String,
  },

  methods: {
    randomStart: function () {
      var chosenNumber1 = Math.floor(Math.random() * this.player.length);
      this.randomPlayer = this.player[chosenNumber1].name;
      this.hp1=this.player[chosenNumber1].hp;
      this.image1=this.player[chosenNumber1].image;

      var chosenNumber2 = Math.floor(Math.random() * this.monster.length);
      this.randomMonster = this.monster[chosenNumber2].name;
      this.hp2=this.monster[chosenNumber2].hp;
      this.image2=this.monster[chosenNumber2].image;

    },

    randomDamage: function () {
      this.randomPlayerAttack = Math.max(Math.floor(Math.random() * 10) + 1, 3);
      this.hp2 -= this.randomPlayerAttack

      this.randomMonsterAttack = Math.max(Math.floor(Math.random() * 15) + 1, 5);
      this.hp1 -= this.randomMonsterAttack    
      
      
    },

    randomSpDamage: function () {
      this.randomPlayerAttack = Math.max(Math.floor(Math.random() * 20) + 1, 10);
      this.hp2 -= this.randomPlayerAttack

      this.randomMonsterAttack = Math.max(Math.floor(Math.random() * 15) + 1, 5);
      this.hp1 -= this.randomMonsterAttack 
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