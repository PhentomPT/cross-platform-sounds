<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>AT AD</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">AT AD</ion-title>
        </ion-toolbar>
      </ion-header>
    
      <div id="container">
        <template v-for="(item, index) in items" :key="index">
          <div class="button" @click="playAudio(item.audio)"><ion-img :src="`/assets/icon/audio/${item.img}`"></ion-img></div>
        </template>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonImg } from '@ionic/vue';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Home',
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    IonImg
  },
  data () {
    return {
      items: [
        { img: 'at-ad.png', audio: 'at-ad'},
        { img: 'nuclear.jpg', audio: 'nuclear'}
      ]
    }
  },
  methods: {
    playAudio (audio: string) {
      new Audio(`/assets/audio/${audio}.mp3`).play();
    }
  }
});
</script>

<style scoped>
#container {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container .button {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 120px;
  height: 120px;
  border-radius: 100%;
}

#container .button:hover {
  background: rgba(255, 255, 255, 0.1);
}

#container ion-img {
  height: 60px;
  width: 60px;
}
</style>