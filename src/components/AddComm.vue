<template>
    <div class="col mt-md-3">
        <div class="border">
        <form class="mt-md-3 mb-md-3 ml-md-3 mr-md-3">
        <div class="form-group">
            <label v-if="select" for="exampleInputEmail1">{{user.name}}, напишіть щось</label>
            <label v-else for="exampleInputEmail1">Виберіть користувача</label>
            <input v-model="url" placeholder="URL зображення" type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
        </div>
        <div class="form-group">
            <textarea v-model="text" class="form-control" id="exampleFormControlTextarea1" rows="3" placeholder="Текст публікації"></textarea>
        </div>
        
        <button @click="addComm(url, text)" type="button" class="btn btn-primary">Відправити</button>
        </form>
        </div>
    </div>  
</template>


<script>
export default {
        data () {
        return {
            url:'',
            text:''
        }
    },
    props:['user', 'select', 'addPosts'],
    methods:{
        addComm(url, text){
            if(url !="" && text!=""){
                this.addPosts(url, text);
                this.url = '';
                this.text = '';
            }
        }
    }    
}
</script>