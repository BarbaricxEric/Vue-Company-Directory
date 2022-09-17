<script setup>
import { faker } from '@faker-js/faker'
  
    const firstName = faker.name.firstName()
    const lastName = faker.name.lastName()
    const fullName = `${firstName} ${lastName}`

    const selectCard = () => {
        console.log(`${fullName} selected`)
    }
  
</script>

<template>
  <div class="card" @click ="selectCard">
    <div class="card-image">
    
        <img :src="faker.internet.avatar()" alt="" srcset="" />
    
    </div>
    <div class="card-details">
    <p class="card-details-name">{{ fullName }}</p>
    <p class="card-details-job" >{{faker.name.jobTitle()}}, {{faker.name.jobArea()}}</p>
    
    <p class="card-details-quote">"{{ faker.lorem.paragraph() }}"</p>
    </div>
  </div>
</template>

<style scoped lang ='postcss'>
    .card{
        @apply cursor-pointer overflow-hidden rounded-md bg-slate-100 p-8 shadow-lg
        hover:scale-105 transition duration-300 hover:shadow-slate-900;
        &-image{
            img{
                @apply mx-auto rounded-full object-contain
            }
        }
        &-details{
            @apply flex flex-col gap-2 pt-6 text-center;
            &-name{
                @apply text-3xl tracking-wider font-thin text-slate-900;
            }
            &-job{
                @apply text-xs font-bold text-blue-500;
            }
           
            &-quote{
                @apply pt-2 font-semibold italic text-slate-800
            }
        }
    }
</style>