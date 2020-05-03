<template>
  <div class="container" id="app">
    <div class="">
      <titlr-tag :users="users" :selectUser="selectUser" :allPost="allPost"></titlr-tag>
    </div>
    <div class="row">
      <all-comm-tag :users="users" :name="nameFind" :like="like"></all-comm-tag>
      <add-tag :user="selectName" :select="select" :addPosts="addPosts"></add-tag>
    </div>
    
  </div>
</template>

<script>
import Title from './components/Title';
import AllComments from './components/CommentsAll';
import AddComm from './components/AddComm';
export default {
  name: 'app',
  data () {
    return {
      users:[
        {name:'Petya', posts:[
          {url:'https://image.shutterstock.com/image-photo/large-beautiful-drops-transparent-rain-260nw-668593321.jpg', text: 'Hellow World', liked: false}
        ]},
        {name:'Vasyya', posts:[
          {url:'https://image.shutterstock.com/image-photo/large-beautiful-drops-transparent-rain-260nw-668593321.jpg', text: 'Hellow World', liked: false}
        ]},
        {name:'Kolya', posts:[
          {url:'https://image.shutterstock.com/image-photo/large-beautiful-drops-transparent-rain-260nw-668593321.jpg', text: 'Hellow World', liked: true}
        ]}
      ],
      selectName : {},
      select: false,
      index: -1,
      nameFind:''
    }
  },
  components:{
    'titlr-tag':Title,
    'all-comm-tag': AllComments,
    'add-tag': AddComm
  },
  methods:{
    selectUser(user, index){
      this.select = true;
      this.selectName = user;
      this.index = index;
      this.nameFind = user.name;
      if(index == -1){
        this.nameFind = '';
        this.select = false
      }
    },
    addPosts(url, text){
            
      this.users[this.index].posts.push({url: url, text: text, liked: false});
    },
    allPost(){
      this.nameFind = '';
    },
    like(index, indexUser){
        let number;
            this.users.forEach((item, i)=>{
              if(item.name == indexUser){
                number = i;
              }
            });

            this.users[number].posts[index].liked = !this.users[number].posts[index].liked;
        }        
  }
}
</script>

