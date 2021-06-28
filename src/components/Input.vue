<template>
  <div>
      <input
      type="text"
      placeholder="Enter Text to add"
      v-model="inputValue"
    />
    <button type="submit" @click="addvalue()">+</button>
  </div>
  <ul>
    <li v-for="inputValue in inputvalueArray" :key="inputValue">
      {{ inputValue }}
       <button type="submit" @click="deletevalue(inputValue)">-</button>
       <button type="submit" @click="editvalue(inputValue)">edit</button>
    </li>
  </ul>
</template>

<script>
export default {
  name: "Input",
  data() {
    return {
      inputValue: "",
      inputvalueArray: [],
      disabled: false,
      currentIndex: 0,
    };
  },
  methods: {
    addvalue() {
      this.inputvalueArray.push(this.inputValue);
      this.inputValue=" ";
      this.currentIndex++;
    },
    deletevalue(index) {
      // let index1 = this.inputvalueArray.indexOf(index);
      this.currentIndex = this.inputvalueArray.indexOf(index);
      this.inputvalueArray.splice(this.currentIndex, 1);
      this.currentIndex--;
    },
    editvalue(index){
     let index1 = this.inputvalueArray.indexOf(index);
     this.inputValue=this.inputvalueArray[index1];

    //  this.inputvalueArray.splice(index1, 1);
    //  this.inputvalueArray.push(this.inputValue);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
