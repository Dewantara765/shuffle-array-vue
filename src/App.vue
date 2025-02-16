<script setup>
import {ref} from 'vue'

const oldArray = ref([])
const newArray = ref([])
const error = ref("")


function shuffleArray (array){
 for (let i = array.length - 1; i > 0; i--) {
  let j = Math.floor(Math.random() * (i + 1));
                  
    let temp = array[i];
    array[i] = array[j];
    array[j] = temp;
  
 }
 return array
}

function enterArray(input){
  if(!input.includes(",")) {
    error.value = "Gunakan koma sebagai pemisah"
  }else{
    const array = input.split(",");
   if(array.length > 30){
    error.value = "Maksimal panjang array 30"
   }else{
     shuffleArray(array)
     newArray.value = array;
   }
   
  }
 
  
}




</script>

<template>

  <main>
  <div class="array">
      <div class="array-input">
        <label htmlFor="inputArray">Masukkan List Array</label>
        <input type="text" id="inputArray" class="inputArray" name="inputArray" v-model="oldArray"/>
        <div style="color:red;">
          {{ error }}
        </div>
      
      <div class="button">
        <button class="shuffle-button" @click="enterArray(oldArray)">Acak</button>
      </div>
      <div class="new-array">
        <p>Array lama : {{ oldArray }}</p>
        <p>Array baru : {{ newArray }}</p>
      </div>
    </div>
  </div>
  </main>
</template>

<style scoped>
.array{
  height: 400px;
  width: 300px;
  background-color: paleturquoise;
  display: flex;
  flex-direction: row;


}

.array-input{
  margin: 20px;
  padding: 20px;
  
}
.inputArray{
  font-size: 16px;
  padding: 10px;
  color: red;

}
.button{
  margin:10px;
}

.shuffle-button{
font-size: 16px;
background-color: aqua;
border: none;
cursor: pointer;
border-radius: 4px;
padding: 10px;
border : 1px solid;

}
.new-array{
  margin: 10px;
  font-size: 16px;
  color: red;
}


</style>
