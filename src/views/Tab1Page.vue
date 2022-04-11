<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Pridať tlak</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-input @input="sys=$event.target.value" type="number" pattern="[0-9]" placeholder="SYS"></ion-input>
      <ion-input @input="dia=$event.target.value" type="number" pattern="[0-9]" placeholder="DIA"></ion-input>
      <ion-input @input="pulz=$event.target.value" type="number" pattern="[0-9]" placeholder="PULZ"></ion-input>
      <ion-datetime v-model="iosTime" style="margin:auto"></ion-datetime>
      <div style="margin-top:5px;display: flex;justify-content:center;">
        <ion-button @click="addTlak">Pridať tlak</ion-button>
      </div>  
    </ion-content>
  </ion-page>
</template>

<script>
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonDatetime, IonButton, IonInput} from '@ionic/vue';

export default {
  name: 'Tab1Page',
  components: { IonHeader, IonToolbar, IonTitle, IonContent, IonPage, IonDatetime, IonButton, IonInput},
  data() {
    return {
      iosTime: '',
      sys: 0,
      dia: 0,
      pulz: 0,
      dataTlaky: 0
    }
  },
  created() {
    let currentTime = new Date(new Date().toLocaleString('en-US', {timeZone: 'Etc/GMT-4'})) 
    this.iosTime = currentTime.toISOString()

    this.dataTlaky = JSON.parse(localStorage.getItem('tlaky'))
  },
  methods: {
    addTlak() {
      let time =new Date().toLocaleString('en-US', {timeZone: 'Etc/GMT-4'})

      this.dataTlaky.tlaky.push({time: time, sys: this.sys, dia: this.dia, pulz: this.pulz})

      localStorage.setItem('tlaky',JSON.stringify(this.dataTlaky))
    }
  }
}
</script>
