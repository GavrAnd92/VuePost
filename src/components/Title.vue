<template>
    <div class="row">
            <a class="btn btn-dark col-3" href="#" role="button" v-for="(user, index) in users" :key="index"
                @click="selectUser(user,index)">
                {{user.name}}
            </a>
            <a class="btn btn-primary" @click="selectUser({}, -1)" href="#" role="button">All</a>
    </div>
</template>


<script>
export default {
        data () {
        return {

        }
    },
    props:['users', 'selectUser', 'allPost']    
}
</script>