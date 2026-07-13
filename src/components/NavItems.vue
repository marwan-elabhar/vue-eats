<script setup>
import {useCurrentUser, useFirebaseAuth} from "vuefire"
import {signOut} from "firebase/auth"
import BaseButton from './base/BaseButton.vue'

const user = useCurrentUser()
const auth = useFirebaseAuth()

async function signOutOfFirebase() {
  signOut(auth).then(() => {
    console.log("User signed out successfully.")
  }).catch((error) => {
    console.log(error)
  })
}


</script>

<template>
  <nav class="pr-4">
    <BaseButton to="/">Home</BaseButton>
    <BaseButton to="/new">New</BaseButton>
    <BaseButton v-if="user?.email" @click="signOutOfFirebase">Sign Out</BaseButton>
    <BaseButton to="/sign-in" v-else>Sign-In</BaseButton>
  </nav>
</template>

<style></style>
