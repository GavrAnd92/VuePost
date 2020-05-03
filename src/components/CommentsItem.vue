<template>
<div>
    <div v-for="(post, index) in user.posts" :key="index" class="col mt-md-3">
        <div  class="card" v-bind:class="{ like: post.liked}" @click="like(index,user.name)" style="width: 12rem;">
            <h5 class="card-title">{{user.name}}</h5>
            <img :src="post.url" class="card-img-top" alt="...">
            <div class="card-body">
                <p class="card-text">{{post.text}}</p>
            </div>
            <i class="fas fa-heart"></i>
        </div>
        
    </div>
</div>
</template>


<script>

export default {
        data () {
        return {
            isActive : false
        }
    },
    props:['user', 'like']   
}
</script>

<style>

.card .fa-heart {
    width: 35px;
    height: 35px;
    text-align: center;
    line-height: 35px;
    font-size: 16px;
    color: red;
    transition: 0.3s all;
    transform: translateX(30px);
    opacity: 0;
}



.card.like .fa-heart {
    opacity: 1;
    transform: translateX(0px);
}

</style>