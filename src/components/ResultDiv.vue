<template>
    <div>
        <!-- Tenho os dados vindos da api users do github monte um pagina boostrap com a renderização dos dados -->
        <!-- Faça um for dos dados que estão na proprieedade store -->
        <div class="card" style="width: 18rem;" v-if="iCamRender">
            <img :src="store.dataResponse.avatar_url" class="card-img-top" alt="...">
            <div class="card-body">
                <h5 class="card-title">{{ store.dataResponse.name }}</h5>
                <p class="card-text">{{ store.dataResponse.bio }}</p>
                <a :href="store.dataResponse.html_url" class="btn btn-primary">Go somewhere</a>
            </div>
        </div>
    </div>
</template>

<script>
import { store } from '../store.js'

export default {
    name: 'ResultDiv',
    data() {
        return {
            store,
            iCamRender : false
        }
    },
    watch: {
        store: {
            handler() {
                console.log(store.dataResponse.avatar_url)
                this.iCamRender = true
            },
            deep: true
        }
    }
}
</script>

<style></style>