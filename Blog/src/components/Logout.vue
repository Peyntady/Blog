<template>
  <div>
    <button v-on:click="$emit('log-out')">Выход</button>
  </div>
</template>

<script>
  export default {
    name: "Logout"
  }
</script>

<style scoped>
  div {
    display: flex;
    justify-content: flex-end;
    font-size: 16px;
  }
  a {
    margin-right: 20px;
    font-size: 18px;
  }
  button {
    display: inline-block;
    font-family: arial,sans-serif;
    font-size: 13px;
    font-weight: bold;
    color: rgb(68,68,68);
    text-decoration: none;
    user-select: none;
    padding: .2em 1.2em;
    outline: none;
    border: 1px solid rgba(0,0,0,.1);
    border-radius: 2px;
    background: rgb(147, 171, 0) linear-gradient(#93ab00, #93ab00);
    transition: all .218s ease 0s;
    margin-right: 10px;
  }
  button:hover {
    color: rgb(24,24,24);
    border: 1px solid rgb(147, 171, 0);
    background: #f7f7f7 linear-gradient(#f7f7f7, #f1f1f1);
    box-shadow: 0 1px 2px rgba(0,0,0,.1);
  }
  button:active {
    color: rgb(51,51,51);
    border: 1px solid rgb(147, 171, 0);
    background: rgb(238,238,238) linear-gradient(rgb(238,238,238), rgb(224,224,224));
    box-shadow: 0 1px 2px rgba(0,0,0,.1) inset;
  }
</style>