<template>
    <ion-card v-if="info">

        <ion-card-header>
            <ion-card-subtitle>
                {{info['post code']}}
            </ion-card-subtitle>
            <ion-card-title>
                {{info['places'][0]['place name']}}
            </ion-card-title>
        </ion-card-header>

        <ion-card-content>
            <ion-list>
                <ion-item>
                    <ion-lable>
                        <strong>State:</strong>
                        {{info['places'][0]['state']}} ({{info['places'][0]['state abbreviation']}})
                    </ion-lable>
                </ion-item>
                <ion-item>
                    <ion-lable>
                        <strong>Latitude:</strong>
                        {{info['places'][0]['latitude']}}
                    </ion-lable>
                </ion-item>
                <ion-item>
                    <ion-lable>
                        <strong>Longitude:</strong>
                        {{info['places'][0]['longitude']}}
                    </ion-lable>
                </ion-item>
            </ion-list>
        </ion-card-content>

    </ion-card>
</template>

<script>
// NOTE: info['post code']
// NOTE: since object key contains a space character, the proper way to access its value is to call it as an array key
export default {
    name: 'ZipInfo',
    props: {
        info: {
            type: Object
        }
    }
}
</script>