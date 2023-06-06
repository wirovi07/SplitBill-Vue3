<script setup>

import {store, getGrandTotal } from '../store/store';
import Label from "./Label.vue";
import personView from './personView.vue';

</script>

<template>

    <div class="no-item" v-if="store.people.length === 0">No Items</div>      
    <div class="people-view" v-if="store.people.length > 0">
        <div class="header">
            <div>
                <Label title="Total + Tip: " :value="getGrandTotal()"></Label>
            </div>
            <div>
                <Label title="Remaining: " :value="store.params.remaining"></Label>
            </div>
        </div>

        <div class="people-container">
            <personView
            v-for="person in store.people" :key="person.id"
            :id="person.id"
            :number-of-person="person.numberOfPerson"
            :total-per-person="person.totalPerPerson" 
            :paid="person.paid">
            </personView>
        </div>
    </div>
</template>

<style scoped>

    .no-item{
        width: 100%;
        height: 100vh;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 28px;
    }
    .people-view{
        margin: 0 auto;
        display: flex;
        align-items: center;
        flex-direction: column;
    }
    .people-container{
        width: 700px;
        margin: 0 auto;
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-template-rows: auto;
        gap: 10px;
    }
    .header{
        /**color: white;**/
        font-weight: bolder;
        padding: 20px 0;
        font-size: 28px;
        display: flex;
        justify-content: space-between;
        gap: 10px;
        flex-direction: column;
    }
</style>