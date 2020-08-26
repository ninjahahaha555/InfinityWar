<template>
  <div>
    <v-button @click="randomStart()" class="btn">
      <img
        src="https://cdn.discordapp.com/attachments/392353546332405763/747437885476700160/pngegg_11.png"
      />
    </v-button>
    <br />
    <button v-bind:disabled="end" @click="randomDamage()" class="btn btn-info">Attack{{Label}}</button>
    <button v-bind:disabled="end" @click="randomSpDamage()" class="btn btn-info">Special Attack{{Label}}</button>

    <div class="row text-light ">
      <div class="col-sm">
        <p>{{randomPlayer}}</p>
        <p>HP : {{hp1}}</p>
        <p>
          <img v-bind:style="{width : hp1 + 'px'}" :src="healthbar1" alt height="25px" />
        </p>
        <img :src="imagePlayer" :height="hp1" />
      </div>

      <div class="col-sm text-danger">
        <h1 v-if="hp1 <= 0 & hp2 <=0">
          <br />
          <img src="https://cdn.discordapp.com/attachments/392353546332405763/748200974153154640/235-2359549_street-fighter-ko-png-ko-street-fighter-png.png">
          DRAW
        </h1>
        <h1 v-else-if="hp2 <= 0 ">
          <br />
          <img src="https://cdn.discordapp.com/attachments/392353546332405763/748200974153154640/235-2359549_street-fighter-ko-png-ko-street-fighter-png.png">
          {{randomPlayer}} WIN
        </h1>
        <h1 v-else-if="hp1 <= 0 ">
          <br />
          <img src="https://cdn.discordapp.com/attachments/392353546332405763/748200974153154640/235-2359549_street-fighter-ko-png-ko-street-fighter-png.png">
          {{randomMonster}} WIN
        </h1>
        <br /><br /><br />
        <p v-if="hp1!=0 & hp2!=0">
          <img
            src="https://cdn.discordapp.com/attachments/392353546332405763/746090155282006126/pngegg_6.png"
          />
        </p>
      </div>

      <div class="col-sm">
        <p>{{randomMonster}}</p>
        <p>HP : {{hp2}}</p>
        <p>
          <img v-bind:style="{width: hp2 + 'px'}" :src="healthbar2" alt height="25px" />
        </p>
        <img :src="imageMonster" :height="hp2" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      randomPlayer: "",
      randomMonster: "",
      randomPlayerAttack: "",
      randomMonsterAttack: "",
      chosenNumber1:"",
      chosenNumber2:"",
      imagePlayer: "",
      imageMonster: "",
      hp1: "1",
      hp2: "1",
      end: false,
      healthbar1:
        "https://i.ppy.sh/bca61e3c2183a86ddb4c1d75914fab845e2b128f/687474703a2f2f692e696d6775722e636f6d2f6953766c5662432e706e67",
      healthbar2:
        "https://i.ppy.sh/bca61e3c2183a86ddb4c1d75914fab845e2b128f/687474703a2f2f692e696d6775722e636f6d2f6953766c5662432e706e67",

      player: [
        {
          name: "Naruto",
          hp: 380,
          image1:
            "https://pa1.narvii.com/5999/831c04cee5973592fd427841a4e45d9d78e49cf2_00.gif",
          image2:
            "https://steamuserimages-a.akamaihd.net/ugc/273972713572251875/235FD90C716AE0A1550310AD5C78B601A721024E/",
          image3:
            "https://www.lordofthecraft.net/uploads/monthly_2019_05/narutoc200.gif.6e814768c713f8562adb7597054a1df1.gif"
        },
        {
          name: "Spiderman",
          hp: 360,
          image1:
            "https://pa1.narvii.com/7636/10cd8a5295c4c7ed8d857577a9401398d390b3c7r1-200-200_00.gif",
          image2:
            "https://www.fightersgeneration.com/characters3/spidey-upper.gif",
          image3:
            "https://www.fightersgeneration.com/characters3/spidey-standingattax.gif",
        },
        {
          name: "Jotaro",
          hp: 390,
          image1:
            "https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/i/8b438fb8-4b3d-4adc-9679-e7c3ba060401/d5b41aj-af8b0a3a-a865-46f0-93f5-a900da7845ad.gif",
          image2:
            "https://cdn.discordapp.com/attachments/392353546332405763/747693531371536394/jotaropunc.gif",
          image3:
            "https://pa1.narvii.com/6087/583c1a9308bb9025612a44d3cab4539ebb9c8be0_00.gif",
        },
        {
          name: "Goku",
          hp: 350,
          image1:
            "https://www.andersonkenya1.net/uploads/monthly_2017_08/0.thumb.gif.88cfc11795b1ade54b18dda55b41a6d0.gif",
          image2:
            "https://i.gifer.com/origin/8f/8f07b22f9b33e306b65d051ef2fabbb4_w200.webp",
          image3:
            "https://vignette.wikia.nocookie.net/liberproeliis/images/3/3e/037d55b01bb3adecb88fcdff5b594465.gif/revision/latest/scale-to-width-down/340?cb=20191116172934",
        },
        {
          name: "Captain American",
          hp: 360,
          image1:
            "https://i.pinimg.com/originals/17/a4/0d/17a40d4465ae6c523a6376efcbe58ad4.gif",
          image2:
            "https://www.fightersgeneration.com/characters/captainamerica-chargingstar.gif",
          image3:
            "https://i.kym-cdn.com/photos/images/original/000/709/072/e1f.gif",
        },
      ],
      monster: [
        {
          name: "Majin Buu",
          hp: 430,
          image1:
            "https://cdn.discordapp.com/attachments/392353546332405763/747688200516141056/buuevo.gif",
          image2:
            "https://cdn.discordapp.com/attachments/392353546332405763/747689281098743899/buupunch.gif",
        },
        {
          name: "Freezer",
          hp: 420,
          image1:
            "https://cdn.discordapp.com/attachments/392353546332405763/747719492217602128/fizzzzzzzzzz.gif",
          image2:
            "https://cdn.discordapp.com/attachments/392353546332405763/747717126663700510/fezzerrr.gif",
        },
        {
          name: "Venom",
          hp: 400,
          image1:
            "https://cdn.discordapp.com/attachments/392353546332405763/747774972889661450/m-venomdd.gif",
          image2:
            "https://cdn.discordapp.com/attachments/392353546332405763/747774450799476756/Z8Du.gif",
        },
        {
          name: "Dio",
          hp: 410,
          image1:
            "https://thumbs.gfycat.com/FaithfulPointedBushsqueaker-size_restricted.gif",
          image2:
            "https://cdn.discordapp.com/attachments/392353546332405763/747690217900736552/diopu.gif",
        },
      ],
    };
  },

  props: {
    Label: String,
  },

  methods: {
    randomStart: function () {
      this.chosenNumber1 = Math.floor(Math.random() * this.player.length);
      this.randomPlayer = this.player[this.chosenNumber1].name;
      this.hp1 = this.player[this.chosenNumber1].hp;
      this.imagePlayer = this.player[this.chosenNumber1].image1;

      this.chosenNumber2 = Math.floor(Math.random() * this.monster.length);
      this.randomMonster = this.monster[this.chosenNumber2].name;
      this.hp2 = this.monster[this.chosenNumber2].hp;
      this.imageMonster = this.monster[this.chosenNumber2].image1;
      this.end = false;
    },

    randomDamage: function () {
      this.randomPlayerAttack = Math.max(Math.floor(Math.random() * 10) + 1, 3);
      this.hp2 -= this.randomPlayerAttack;
      this.imagePlayer = this.player[this.chosenNumber1].image2;      
      
      this.randomMonsterAttack = Math.max(Math.floor(Math.random() * 15) + 1,5);
      this.hp1 -= this.randomMonsterAttack;
      this.imageMonster = this.monster[this.chosenNumber2].image2;

      if (this.hp1 <= 0 & this.hp2 <=0) {
        this.hp1 = 0;
        this.hp2 = 0;
        this.end = true;             
      }
      else if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.end = true;
        this.imageMonster = this.monster[this.chosenNumber2].image1;
      }
      else if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.end = true;
        this.imagePlayer = this.player[this.chosenNumber1].image1;
      }
    },

    randomSpDamage: function () {
      this.randomPlayerAttack = Math.max(Math.floor(Math.random() * 20) + 1,10);
      this.hp2 -= this.randomPlayerAttack;
      this.imagePlayer = this.player[this.chosenNumber1].image3;      

      this.randomMonsterAttack = Math.max(Math.floor(Math.random() * 15) + 1,5);
      this.hp1 -= this.randomMonsterAttack;
      this.imageMonster = this.monster[this.chosenNumber2].image2;    

      if (this.hp1 <= 0 & this.hp2 <=0) {
        this.hp1 = 0;
        this.hp2 = 0;
        this.end = true;             
      }
      else if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.end = true;
        this.imageMonster = this.monster[this.chosenNumber2].image1
      }
      else if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.end = true;
        this.imagePlayer = this.player[this.chosenNumber1].image1;
      }
    },
  },
};
</script>

<style>
</style>