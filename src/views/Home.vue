<template>
    <div class="ion-page">
        <ion-header>
          <ion-toolbar>
            <ion-title>ZipInfo</ion-title>
          </ion-toolbar>
        </ion-header>
        <ion-content class="ion-padding">
            <zip-search v-on:getZipHandler="getZipInfo" />
            <zip-info v-bind:info="info" />
            <clear-info :info="info" @clearInfoHandler="clearInfo" />
        </ion-content>
    </div>
</template>

<script>
/* eslint-disable */
import axios from 'axios';
import ZipSearch from '../components/ZipSearch.vue';
import ZipInfo from '../components/ZipInfo.vue';
import ClearInfo from '../components/ClearInfo.vue';
export default {
    name: 'home',
    components: {
        ZipSearch,
        ZipInfo,
        ClearInfo
    },
    data() {
        return {
            info: null
        }
    },
    methods: {
        getZipInfo(zip) {
            const url = `https://api.zippopotam.us/us/${zip}`;
            axios.get(url)
            .then((response) => {
                this.info = response.data;
            })
            .catch((error) => {
                this.showErrorAlert();
            });
        },
        clearInfo() {
            this.info = null;
        },
        showErrorAlert() {
            return this.$ionic.alertController
                .create({
                    header: 'Not Valid',
                    message: 'Please enter a valid US zipcode',
                    buttons: ['OK']
                })
                .then(a => a.present());
        }
    }
}
</script>