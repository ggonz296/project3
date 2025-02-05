<script setup>
import { ref } from "vue";
//Global variables
const name = ref("");
const phone = ref("");
const selectedGender = ref("");
const selectType = ref("");
const contacts = ref([]);

//Generate Contact function
const addContact = () => {

    //validate inputs
    if (name === "" || phone === "" || selectType === ""|| selectedGender === "") {
        alert("Please enter name, phone number, contact type, and gender. Please click on the buttons.");
        return
    }

    //create a new list of contacts
    contacts.value.push({
      name: name.value,
      phone: phone.value,
      type: selectType.value,
      gender: selectedGender.value,
    });

    //starts adding contacts to the list
    document.getElementById("contactList").appendChild(li);

    //clear inputs
    name.value = "";
    phone.value = "";
    selectedGender.value = "";
    selectType.value = "";
  }
function setGender(gender) {
    selectedGender = gender;
    document.getElementById("maleButton");
    document.getElementById("femaleButton");
}
function setType(type){
    selectType = type;
    document.getElementById("personalButton");
    document.getElementById("workButton");
}
</script>

<template>
  <div class="content">
        
        <div>
        <h1 class="main-title">Generate a List of Contacts</h1>
        <h2>By Gabriel Gonzalez</h2>
        <h2>For CITP-4316</h2>
        <h2>Professor Perez</h2>
        </div>

        <div class="contactInput">
            <label for="name">Name:</label>
            <input type="text" id="name" placeholder="Pleae enter a name">
            <label for="phone">Phone:</label>
            <input type="tel" id="phone" placeholder="Please enter phonenumber">
            <button onclick="addContact()">Add Contact</button>
        </div>

        <div class="Contact-Type">
            <h3>Personal or Work Contact</h3>
            <button onclick="setType('Personal')" id="personalButton">Personal</button>
            <button onclick="setType('Work')" id="workButton">Work</button>
        </div>

        <div class = "Male-Female">
            <h3>Please Select Contact Gender</h3>
            <button onclick="setGender('Male')" id="maleButton">Male</button>
            <button onclick="setGender('Female')" id="femaleButton">Female</button>
        </div>

        <div class="ContactList">
            <div id="pending">
            <h2>Contact List</h2>
            <ul id="contactList">
            </ul>
            </div>
        </div>

    </div>
</template>