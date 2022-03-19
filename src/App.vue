<script>
//import { RouterLink, RouterView } from 'vue-router'
export default{
  name: 'App',  
  mounted(){
      var c = this.$refs['canvas'];
      var ctx = c.getContext("2d");    
      var image = this.$refs["person"]
      console.log(image)
      // ctx.fillStyle = 'rgb(200, 0, 0)';
      // ctx.fillRect(10, 10, 50, 50);      
      // ctx.fillStyle = 'rgba(0, 0, 200, 0.5)';
      // ctx.fillRect(30, 30, 50, 50);
      // ctx.fillStyle = "red";
      // ctx.fillText("#TreatLongCovid",40,80);
      // c.width = image.width;
      // c.height = image.height;   
      ctx.drawImage(image, 0, 0);
  
      // ctx.font = "36pt Arial";
      // ctx.clearRect(0,0,c.width,c.height);
      // ctx.drawImage(image, 0, 0);
      // ctx.fillStyle = "red";
      // ctx.fillText("#TreatLongCovid",40,80);
      // console.log(c)

    

  },
  methods:{
    generateImage(e){      
      var c = this.$refs['canvas'];
      var ctx = c.getContext("2d");          
      
      const file = e.target.files[0];
      var url = URL.createObjectURL(file);      
      console.log(url)
      var image = new Image()
      image.src = url
      //this.$refs["teste"].append(image)
      // this.$refs["person2"].src = url
      // console.log(image)

      // c.width = image.width;
      // c.height = image.height;      
      
      ctx.clearRect(0,0,c.width,c.height);
      ctx.drawImage(image, 0, 0);
      // ctx.font = "36pt Arial";
      // ctx.fillStyle = "red";
      // ctx.fillText("#TreatLongCovid",40,80);      
    }
  },
  
}


</script>

<template>
  <div class="flex justify-center space-x-4 align-middle p-4 h-screen bg-gray">
    <div class="w-full m-auto h-full bg-white border shadow-md">
      <div class="max-w-3xl px-6 py-16 mx-auto text-center">
            <h1 class="text-3xl font-semibold text-black">#TreatLongCovid</h1>
            <p class="max-w-md mx-auto mt-5 text-gray-500">Upload your image:</p>

            <div class="flex flex-col mt-8  justify-center mx-auto">
              <label class=" text-gray-500 justify-center">Click on Upload
                <input @change="generateImage" ref="new-image" type="file" class="px-4 py-2 text-sm rounded-md ">                  
              </label>                
            </div>
            <p class="max-w-md mx-auto mt-5 text-gray-500 dark:text-gray-400">This image won't be stored in the server, however you can always generate another one</p>
            <div class="flex flex-col mt-8 space-y-3 sm:space-y-0 sm:flex-row sm:justify-center sm:-mx-2">                
                <button @click="generateImage" class="px-4 py-2 text-sm font-medium tracking-wide text-white capitalize transition-colors duration-200 transform bg-blue-700 rounded-md sm:mx-2 hover:bg-blue-600 focus:outline-none focus:bg-blue-600">
                    Generate
                </button>
            </div>
        </div>
      
    </div>
    <div class="w-full h-full bg-white border shadow-md grid grid-cols-2 ">      
      <div class="m-auto">
        <img style="display:block;" id="person" ref="person" src="./assets/person.jpeg" class="">                   
      </div>
      <div class="m-auto bg-blue-50" ref="teste">
        <canvas style="" ref="canvas" class="">          
        </canvas> 
        <!-- <img style="display:block;" id="person2" ref="person2" src="./assets/person.jpeg" class="">                    -->
      </div>

    </div>
  </div>
</template>

<style>

</style>
