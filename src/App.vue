<script setup>
import {ref} from 'vue'

const oldArray = ref([])
let newArray = []
const newArrayNumber = ref([])
const error = ref("")
const enter = ref("")


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
    newArrayNumber.value = input
  }else{
    const array = input.split(",");
    if(array.length > 30){
      error.value = "Maksimal panjang array 30"
      newArrayNumber.value = []
    }else {
      newArray = [];
      shuffleArray(array)
      for(let i = 0;  i < array.length; i++){
        newArray.push(array[i])
      }
      newArrayNumber.value = newArray;
      
    }  
  }
}





</script>

<template>

  <main>
    <div class="array">
      <div class="array-input">
        <label htmlFor="inputArray">Masukkan List Array (maks 30)</label>
        <textarea type="text" id="inputArray" class="inputArray" name="inputArray" v-model="oldArray" rows="5" cols="20"></textarea>
    </div>
    <div class="error">
      <p style="width: 150px;"></p>
      <div style="color:red; justify-content: center;">
          {{ error }}
        </div>
    </div>
    
    
    <div class="button-array">
        <button class="shuffle-button" @click="enterArray(oldArray)">Acak</button>
      
    </div>
    <div class="new-array">
        <p>Array lama : {{ oldArray }}</p>
        <p>Array baru : {{ newArrayNumber }}</p>
      </div>
    </div>
  </main>
</template>

<style scoped>
.array{
  height: 400px;
  width: 600px;
  background-color: paleturquoise;
  justify-content: start;

}

.array-input{
  margin: 5px;
  padding: 5px 10px 0 10px;
  color: red;
  display: flex;
  align-items: center;
  
}
.inputArray{

  font-size: 16px;
  padding: 10px;
  margin: 5px;

}

.error{
  display: flex;
  flex-direction: row;
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

.button-array{
  display: flex;
  flex-direction: column;
  align-items: center;
}
.new-array{
  margin: 10px;
  font-size: 16px;
  color:red;
}


</style>

