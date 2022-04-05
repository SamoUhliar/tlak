<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 1</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 1</ion-title>
        </ion-toolbar>
      </ion-header>
      <ion-input v-model="sys" type="number" placeholder="SYS"></ion-input>
      <ion-input v-model="dia" type="number" placeholder="DIA"></ion-input>
      <ion-input v-model="pulz" type="number" placeholder="PULZ"></ion-input>
      <ion-datetime v-model="iosTime" style="margin:auto"></ion-datetime>
      <div style="margin-top:150px;display: flex;justify-content:center;">
        <ion-button>Pridat</ion-button>
      </div>  
    </ion-content>
  </ion-page>
</template>

<script>
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonDatetime, IonButton } from '@ionic/vue';

export default {
  name: 'Tab1Page',
  components: { IonHeader, IonToolbar, IonTitle, IonContent, IonPage, IonDatetime, IonButton },
  data() 
  {
    return {
      currentTime: undefined,
      iosTime: '',
      sys: undefined,
      dia: undefined,
      pulz: undefined,
    }
  },
  created() {
    this.currentTime = new Date(new Date().toLocaleString("en-US", {timeZone: "Europe/Bratislava"})) 
    this.iosTime = this.currentTime.toISOString()
    
  }
}
</script>
