<template>
    <div class="col-8">
        <div class="row">
            <teg-comm-item v-for="(user, index) of searchUser" :user="user" :key="index" :like="like" ></teg-comm-item>
        </div>
    </div>
</template>


<script>
import CommItem from './CommentsItem'
export default {
        data () {
        return {

        }
    },
    components:{
        'teg-comm-item': CommItem
    },
    props:['users', 'name', 'like'],
    computed:{
        searchUser(){
            return this.users.filter(user => user.name.startsWith(this.name))
        }
    }    
}
</script>