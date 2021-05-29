<template>
  <ion-page>
    <!-- <ion-header :translucent="true"> </ion-header> -->
    <ion-toolbar class="ion-no-border">
      <ion-item class="ion-no-padding ion-no-border">
        <ion-avatar>
          <img
            src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ492AnNAAPJR3tuNh9iojWzyaVnyeQ3mApIw&usqp=CAU"
          />
        </ion-avatar>
      </ion-item>
    </ion-toolbar>
    <ion-content class="ion-padding">
      <ion-toolbar>
        <ion-title>
          <h3 class="title">Your Rv's</h3>
        </ion-title>
      </ion-toolbar>

      <!-- <ion-list v-for="rv in totalRvs" v-bind:key="rv._id">
        <ion-item>
          <ion-label>{{ rv.name }}</ion-label>
        </ion-item>
      </ion-list> -->
      <ion-list
        class="ion-padding-top"
        v-for="rv in totalRvs"
        v-bind:key="rv._id"
      >
        <ion-item class="ion-no-padding ion-margin-bottom" href="/room">
          <ion-avatar>
            <img
              src="https://st.depositphotos.com/1203257/1763/i/950/depositphotos_17637335-stock-photo-yellowstone-rv-trip.jpg"
            />
          </ion-avatar>

          <ion-label>{{ rv.name }}</ion-label>
          <ion-badge color="primary" class="ion-margin-end">10+</ion-badge>
          <div>
            <div class="circle">
              <ion-text color="light">
                <ion-icon src="/assets/icon/share.svg"></ion-icon>
              </ion-text>
            </div>
            <div class="small">Share</div>
          </div>
        </ion-item>
      </ion-list>
    </ion-content>
  </ion-page>
</template>

<script>
import { IonPage, IonTitle, IonToolbar, IonContent } from "@ionic/vue";

import axios from "axios";
export default {
  name: "Rv",
  component: {
    IonPage,
    IonToolbar,
    IonTitle,

    IonContent,
  },

  data() {
    return {
      totalRvs: [],
    };
  },
  async created() {
    await this.listOfRvs();
  },

  methods: {
    async listOfRvs() {
      const options = {
        method: "POST",
        url: "http://localhost:3000/Rv/search",
        headers: { "Content-Type": "application/json" },
        data: { creator: "507f1f77bcf86cd799439014", page: 7 },
      };
      const data = await axios.request(options);
      //console.log("DATA", data, this.totalRvs);
      this.totalRvs = data.data.data;
      console.log(this.totalRvs);
    },
  },
};
</script>

<style scoped></style>
