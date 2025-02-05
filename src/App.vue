<script setup>
import { ref } from "vue";
//Global variables
const name = ref("");
const phone = ref("");
const selectedGender = ref("");
const selectType = ref("");
const contacts = ref([]);

//Add Contact function
const addContact = () => {
    //validate inputs
    if (name.value.trim() === "" || phone.value.trim() === "" || selectType.value.trim() === ""|| selectedGender.value.trim() === "") {
        alert("Please enter name, phone number, contact type, and gender. Please click on the buttons.");
        return
    }

    //adds the contact to the list
    contacts.value.push({
      name: name.value,
      phone: phone.value,
      type: selectType.value,
      gender: selectedGender.value,
    });

    //clear inputs
    name.value = "";
    phone.value = "";
    selectedGender.value = "";
    selectType.value = "";
  }
//setGenderFunction
const setGender = (gender) => {
    selectedGender.value = gender
}
//set contact type
const setType = (type) => {
    selectType.value = type
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
            <input type="text" id="name" v-model="name" placeholder="Pleae enter a name"/>
            <label for="phone">Phone:</label>
            <input type="tel" id="phone" v-model="phone" placeholder="Please enter phonenumber">
            <button @click="addContact()">Add Contact</button>
        </div>

        <div class="Contact-Type">
            <h3>Is This Their Personal or Work Contact</h3>
            <button @click="setType('Personal')" :class="{active: selectType === 'Personal' }"> Personal </button>
            <button @click="setType('Work')" :class="{active: selectType === 'Work' }">Work</button>
        </div>

        <div class = "Male-Female">
            <h3>Please Select Contact Gender</h3>
            <button @click="setGender('Male')" :class="{active: selectType === 'Male' }">Male</button>
            <button @click="setGender('Female')" :class="{active: selectType === 'Female' }">Female</button>
        </div>

        <div class="ContactList">
            <div id="pending">
            <h2>Contact List</h2>
            <ul id="contactList">
              <li v-for="(contact, x) in contacts" :key="x">
                {{ `Name: ${contact.name} - Phone: ${contact.phone} - Contact Type: ${contact.type} - Gender: ${contact.gender}` }}
              </li>
            </ul>
            </div>
        </div>

    </div>
</template>