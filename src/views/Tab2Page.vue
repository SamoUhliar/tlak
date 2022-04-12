
<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tabuľka tlakov</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-grid v-if="dataTlaky != undefined">
        <ion-row>
          <ion-col>
            Čas
          </ion-col>
          <ion-col>
            SYS/DIA
          </ion-col>
          <ion-col>
            Pulz
          </ion-col>
          <ion-col>
             
          </ion-col>
        </ion-row>
        <ion-row v-for="(tlak, index) in dataTlaky.tlaky" :key="tlak">
          <ion-col>
            {{tlak.time}}
          </ion-col>
          <ion-col>
            {{tlak.sys}}/{{tlak.dia}}
          </ion-col>
          <ion-col>
            {{tlak.pulz}}
          </ion-col>
          <ion-col>
            <ion-button @click="deleteItem(index)">🗑️</ion-button>
          </ion-col>
        </ion-row>
      </ion-grid>
    </ion-content>
  </ion-page>
</template>

<script>
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonCol, IonGrid, IonRow } from '@ionic/vue';

export default {
  name: 'Tab2Page',
  components: { IonHeader, IonToolbar, IonTitle, IonContent, IonPage, IonCol, IonGrid, IonRow },
  data() {
    return {
      dataTlaky: undefined
    }
  },
  ionViewWillEnter() {
    this.dataTlaky = JSON.parse(localStorage.getItem('tlaky'))
  },
  methods: {
    deleteItem(index) {
      this.dataTlaky.tlaky.splice(index,1)
      localStorage.setItem('tlaky',JSON.stringify(this.dataTlaky))
    }
  }
}
</script>
