<template>
  <div>
    <v-button @click="randomStart()" class="btn">
    <img src="https://cdn.discordapp.com/attachments/392353546332405763/747437885476700160/pngegg_11.png"/>
    </v-button>
    <br />
    <button v-bind:disabled="end" @click="randomDamage()" @click.prevent="playSound('https://cdn.discordapp.com/attachments/392353546332405763/748744472472322048/PUNCH.mp3')" class="btn btn-info">Attack{{Label}}</button>
    <button v-bind:disabled="end" @click="randomSpDamage()" @click.prevent="playSound(player[chosenNumber1].spsound)"  class="btn btn-info">Special Attack{{Label}}</button>
    <button class="btn btn-warning btn-sm" @click.prevent="audio.isPlaying ? pause(audio) : play(audio)" v-for="audio in audios" :key="audio.id"><svg width="1em" height="1em" viewBox="0 0 16 16" class="bi bi-volume-up-fill" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
  <path d="M11.536 14.01A8.473 8.473 0 0 0 14.026 8a8.473 8.473 0 0 0-2.49-6.01l-.708.707A7.476 7.476 0 0 1 13.025 8c0 2.071-.84 3.946-2.197 5.303l.708.707z"/>
  <path d="M10.121 12.596A6.48 6.48 0 0 0 12.025 8a6.48 6.48 0 0 0-1.904-4.596l-.707.707A5.483 5.483 0 0 1 11.025 8a5.483 5.483 0 0 1-1.61 3.89l.706.706z"/>
  <path d="M8.707 11.182A4.486 4.486 0 0 0 10.025 8a4.486 4.486 0 0 0-1.318-3.182L8 5.525A3.489 3.489 0 0 1 9.025 8 3.49 3.49 0 0 1 8 10.475l.707.707z"/>
  <path fill-rule="evenodd" d="M6.717 3.55A.5.5 0 0 1 7 4v8a.5.5 0 0 1-.812.39L3.825 10.5H1.5A.5.5 0 0 1 1 10V6a.5.5 0 0 1 .5-.5h2.325l2.363-1.89a.5.5 0 0 1 .529-.06z"/>
</svg></button>
    <div class="row text-light">
      <div class="col-sm">
        <p>{{randomPlayer}}</p>
        <p>HP : {{hp1}}</p>
        <p>
          <img v-bind:style="{width : hp1 + 'px'}" :src="healthbar" alt height="25px" />
        </p>
        <img :src="imagePlayer" :height="hp1" />
      </div>

      <div class="col-sm text-danger">
        <h1 v-if="hp1 <= 0 & hp2 <=0">
          <br />
          <img src="https://cdn.discordapp.com/attachments/392353546332405763/748200974153154640/235-2359549_street-fighter-ko-png-ko-street-fighter-png.png">
          DRAW!
          
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
          <img v-bind:style="{width: hp2 + 'px'}" :src="healthbar" alt height="25px" />
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
      end: true,
      healthbar:
        "https://i.ppy.sh/bca61e3c2183a86ddb4c1d75914fab845e2b128f/687474703a2f2f692e696d6775722e636f6d2f6953766c5662432e706e67",
      audios: [
      {
        file: new Audio('https://cdn.discordapp.com/attachments/392353546332405763/748765378167046204/KId6eunoiWk.mp3'),
        isPlaying: false
      }],
      player: [
        {
          name: "Naruto",
          hp: 380,
          image1:
            "https://pa1.narvii.com/5999/831c04cee5973592fd427841a4e45d9d78e49cf2_00.gif",
          image2:
            "https://steamuserimages-a.akamaihd.net/ugc/273972713572251875/235FD90C716AE0A1550310AD5C78B601A721024E/",
          image3:
            "https://www.lordofthecraft.net/uploads/monthly_2019_05/narutoc200.gif.6e814768c713f8562adb7597054a1df1.gif",
          spsound:"https://cdn.discordapp.com/attachments/392353546332405763/748769494406660217/rasengan.mp3"
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
          spsound:"https://cdn.discordapp.com/attachments/392353546332405763/748775964149809202/attack.mp3"
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
          spsound:"https://cdn.discordapp.com/attachments/392353546332405763/748766381578780810/oraoraoraoraora-sound-effect.mp3"
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
          spsound:"https://cdn.discordapp.com/attachments/392353546332405763/748778292269547612/kamehameha_mp3cut.net.mp3"
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
          spsound:"https://cdn.discordapp.com/attachments/392353546332405763/748776646034718810/Bomb1.mp3"
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
    playSound (sound) {
      if(sound) {
        var audio = new Audio(sound);
        audio.play();
      }
    },
    play (audio) {
      audio.isPlaying = true;
      audio.file.play();
    },
    pause (audio) {
      audio.isPlaying = false;
      audio.file.pause();
    }
  },
};
</script>

<style>
</style>