<template>
    <div>
        <div>{{countMessage}} </div>
    </div>
    <button @click="count++"></button>
    <button @click="count = 0"></button>
</template>