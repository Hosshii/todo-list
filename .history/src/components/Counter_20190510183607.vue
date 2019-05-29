<template>
    <div>
        <div>{{countMessage}} </div>
    </div>
    <button @click="count++">クリック</button>
    <button @click="count = 0">リセット</button>
</template>