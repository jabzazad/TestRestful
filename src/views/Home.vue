<template id="main">
  <div class="home">
    <div class="container">
        <button class="button button1">
            <img src="../image/Android_robot.png" width="30" height="30" class="d-inline-block align-top" alt="" style=" margin-right:10px">Application</button>
    </div>
    <div class="container">
        <div class="row">
            <div class="col-6 col-md-4">
                <div class="dropdown">
                    <button class="btn btn-light dropdown-toggle" type="button" data-toggle="dropdown">Categories
                        <span class="caret"></span></button>
                    <ul class="dropdown-menu">
                        <li><a href="#">GAME</a></li>
                        <li><a href="#">Application</a></li>
                        <li><a href="#">Movie</a></li>
                    </ul>
                </div>
            </div>
            <div class="col-6 col-md-4">
                <button type="button" class="btn btn-outline-secondary">HOME</button> </div>
            <div class="col-6 col-md-4">
                <button type="button" class="btn btn-outline-dark">Top Charts</button> </div>
        </div>
    </div>
    <br>
     
 <b-carousel id="carousel1" 
 style="text-shadow: 1px 1px 2px #333;"
                controls
                indicators
                background="#ababab"
                :interval="3000"
                >
    <b-carousel-slide>
        <img slot="img" class="img-fluid" 
             src="../image/1.jpg" alt="image slot">
      </b-carousel-slide>
      <b-carousel-slide>
        <img slot="img" class="img-fluid" 
             src="../image/2.jpg" alt="image slot">
      </b-carousel-slide>
      <b-carousel-slide>
        <img slot="img" class="img-fluid" 
             src="../image/3.jpg" alt="image slot">
      </b-carousel-slide>
      <b-carousel-slide>
        <img slot="img" class="img-fluid" 
             src="../image/4.jpg" alt="image slot">
      </b-carousel-slide>
 </b-carousel>
 
    <div class="container">
        <h1>Recommended For you</h1>
        <div class="row">
            <div class="col-md-4">
                <div class="thumbnail">
                    <a href="detail.html" target="_blank">
                        <img src="#" alt="photo editor" style="width:100%">
                        <div class="caption">
                            <p></p>
                        </div>
                    </a>
                </div>
            </div>
            <div class="col-md-4">
                <div class="thumbnail">
                    <a href="#" target="_blank">
                        <img src="../image/photo editor.png" alt="coloring book" style="width:100%">
                        <div class="caption">
                            <p></p>
                        </div>
                    </a>
                </div>
            </div>
            <div class="col-md-4">
                <div class="thumbnail">
                    <a href="#" target="_blank">
                        <img src="#" alt="U Launcher Lite" style="width:100%">
                        <div class="caption">
                            <p></p>
                        </div>
                    </a>
                </div>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios'
export default {
  name: 'home',
  components: {
    HelloWorld
  },  
   data(){
        return{
        message:"project1"
        ,products:[],
        pageSize:10,
        pageIndex:1,
        fields:[
        {key:'app',sortable:true},
        {key:'size',sortable:true},
        {key:'rating',sortable:true,variant:'danger'},
        {key:'type',sortable:true},
        {key:'content',sortable:true},
        {key:'current',sortable:true}
        ]
        }
        },
  mounted() {
          var instance = this;
       var xhr=new XMLHttpRequest();
        xhr.open("GET","http://localhost:8080/api/All",false)
        xhr.setRequestHeader("Authorization","Basic "+btoa("myuser"+":"+"password"))
        xhr.send()
if(xhr.readyState===4&&xhr.status==200){
   var result=xhr.responseText;
   console.log(result)
instance.products=result.data
}

   
  }
}
</script>
<style>
.button {
    background-color: #4CAF50; /* Green */
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin: 4px 2px;
    cursor: pointer;
}
.button1 { 
    width: 100%;
    margin-top: 30px
}
.dropdown{
margin-top: 20px;
margin-left: 50px;
}
.btn-light{
    width: 250px;
}
.btn-outline-secondary{
    width: 250px;
    margin-top: 20px;
   margin-left: 60px;
}
.btn-outline-dark{
    width: 250px;
    margin-top: 20px;
   margin-left: 50px;
}
.mySlides { 
    display:none;
}
.star-rating {
    line-height:32px;
    font-size:1.25em;
  }
  .star-rating .fa-star{   
    color: yellow;
}
  .w3-left, .w3-right, .w3-badge {
    cursor:pointer
}
.w3-badge {
    height:13px;width:13px;padding:0
}
.w3-container{
margin-top: 50px;
text-align: center;
}
</style>
