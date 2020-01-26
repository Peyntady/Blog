<template>
  <div class="b-popup">
    <div class="b-popup-content">
      <form @submit.prevent="onSubmit">
        <button type="submit">Zakroi</button>
        <br>
        <textarea v-model="text"> </textarea>
      </form>
    </div>
  </div>
</template>

<script>
  export default {
    name: "WindowEdit",
    data(){
      return{
        textId: require('@/data-post.json').idNow,
        text: require('@/data-post.json').posts[require('@/data-post.json').idNow].content
      }
    },
    methods: {
      onSubmit(){
        /*
        При нажатии на кнопку берется значение из поле
        textarea и передается в файл. После окно закрывается
         */
        const post = require('@/data-post.json');
        post.posts[this.textId].content = this.text;
        // eslint-disable-next-line no-console
        console.log(this.text);
        this.$emit('close-edit');
      }
    },
  }
</script>

<style scoped>
  *{
    font-family: Areal;
  }
  textarea{
    width: 99.4%;
    height: 240%;
    font-family: 'Merriweather', serif;
  }
  .b-popup{
    width:100%;
    min-height:100%;
    background-color: rgba(0,0,0,0.5);
    overflow:hidden;
    position:fixed;
    top:0px;
  }
  .b-popup .b-popup-content{
    margin:40px auto 0px auto;
    width:1000px;
    height: 400px;
    padding:10px;
    background-color: rgba(147, 171, 0, 0.49);
    border-radius:3px;
    box-shadow: 0px 0px 10px #000;
  }
  .b-popup-content {
    display: flex;
    flex-direction: column;
  }
  button {
    text-align:center;
    font-size:13px;
    text-decoration: none;
    font-weight: 700;
    padding: 3px 6px;
    background: #93ab00;
    display:block;
    width:60px;
    margin: 20px auto;
    background-image: linear-gradient(rgba(0,0,0,0), rgba(0,0,0,.1));
    border-radius: 3px;
    color: rgba(0,0,0,.6);
    text-shadow: 0 1px 1px rgba(147, 171, 0, 0.7);
    box-shadow: 0 0 0 1px rgba(0,0,0,.2), 0 1px 2px rgba(0,0,0,.2), inset 0 1px 2px rgba(147, 171, 0, 0.7);
  }
  button:hover, button.hover {
    background: #93ab00;
  }
  button:active, button.active {
    background: #93ab00;
    background-image: linear-gradient(rgba(0,0,0,.1), rgba(0,0,0,0));
    box-shadow: inset 0 0 2px rgba(0,0,0,.2), inset 0 2px 5px rgba(0,0,0,.2), 0 1px rgba(255,255,255,.2);
  }
</style>