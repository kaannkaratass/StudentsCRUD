
<template>
   <div class="main">
      <div id="myDIV" class="header">
         <h2>STUDENT LIST</h2>
         <form @submit.prevent="addStudent()">
            <input v-model="newStudent">
            <button class="addBtn">Add</button>    
         </form>
      </div>
   </div>

   <ul id="MyUL">
    <li v-for="student in studentList" :key="student.id">
      {{ student.text }}
      <button class="Btnn" @click="removeStudent(student)">X</button>
    </li>
  </ul>
   
</template>
 
<script lang="ts" setup>
import { ref } from 'vue' ;
let id =0 ;
const newStudent = ref('') ;
const studentList = ref([
   {id : id++ , text : 'Messi '},
   {id : id++ , text : 'Ronaldo'},
   {id : id++ , text : 'Neymar'}
]);
const addStudent = () => {
   studentList.value.push({id : id++ , text : newStudent.value}) ;
   newStudent.value = '' ;  //Girdiğimiz yazı kaybolsun diye aldık.

}
function removeStudent(student: any) {
  studentList.value.filter((ar) => ar!==student);

}


      
</script>


<style>
@import url("https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/css/bootstrap.min.css" );
@import url(https://fonts.googleapis.com/icon?family=Material+Icons);

/* Include the padding and border in an element's total width and height */
* {
  box-sizing: border-box;
}

/* Remove margins and padding from the list */
ul {
  margin: 0;
  padding: 0;
}

/* Style the list items */
ul li {
  cursor: pointer;
  position: relative;
  padding: 12px 8px 12px 40px;
  background: #eee;
  font-size: 18px;
  transition: 0.2s;

  /* make the list items unselectable */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* Set all odd list items to a different color (zebra-stripes) */
ul li:nth-child(odd) {
  background: #f9f9f9;
}

/* Darker background-color on hover */
ul li:hover {
  background: #ddd;
}

/* When clicked on, add a background color and strike out text */
ul li.checked {
  background: #888;
  color: #fff;
  text-decoration: line-through;
}

/* Add a "checked" mark when clicked on */
ul li.checked::before {
  content: '';
  position: absolute;
  border-color: #fff;
  border-style: solid;
  border-width: 0 2px 2px 0;
  top: 10px;
  left: 16px;
  transform: rotate(45deg);
  height: 15px;
  width: 7px;
}

/* Style the close button */
.close {
  position: absolute;
  right: 0;
  top: 0;
  padding: 12px 16px 12px 16px;
}

.close:hover {
  background-color:blue;
  color: white;
}

/* Style the header */
.header {
  background-color:olive;
  padding: 30px 40px;
  color: white;
  text-align: center;
}

/* Clear floats after the header */
.header:after {
  content: "";
  display: table;
  clear: both;
}

/* Style the input */
input {
  margin: 0;
  border: none;
  border-radius: 0;
  width: 75%;
  padding: 10px;
  float: left;
  font-size: 16px;
}

/* Style the "Add" button */
.addBtn {
  padding: 9px;
  width: 25%;
  background: #d9d9d9;
  background-color: rgb(196, 228, 255);
  text-align: center;
  font-size: 16px;
  cursor: pointer;
  transition: 0.3s;
  border-radius: 0;
}

.addBtn:hover {
  background-color:darkgray;
}
.Btnn {
   text-align: center;
   cursor: pointer;
   background-color: coral;
   float: right;
   width: 10%;
   
}
.Btnn:hover {
   background-color: firebrick;
}

</style>