<template>
    <div class="container-fluid">
        <div class="row w-100">
            <div class="col-12 m-3 d-flex align-items-center">
                <p class="text-start text-success">tilsonmateus@teckyame: </p>
                <p class="text-start">~/home/tilsonmateus$ :</p>
                <InputComand class="input-margin" />
            </div>

            <ResultDivVue class="col-md-12"/>
        </div>
    </div>
</template>

<script>
import InputComand from './InputComand.vue'
import ResultDivVue from './ResultDiv.vue'

export default {
    name: 'MainDiv',
    components: {
        InputComand,
        ResultDivVue
    }
}
</script>

<style>
* {
    background-color: #282a36;
    color: #f8f8f2;
}

.input-margin {
    margin-top: -15px;
}
</style>