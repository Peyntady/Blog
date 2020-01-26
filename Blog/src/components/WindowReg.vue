<template>
  <div class="b-popup">
    <div class="b-popup-content">
      <form @submit.prevent="onSubmit">
        <button type="submit">Зарегистрировать</button>
        <h3>Введите логин</h3>
        <input type="text" placeholder="Введите ваш логин" v-model="login">
        <h3>Введите пароль</h3>
        <input type="password" placeholder="Ваш пароль" v-model="password">
      </form>
    </div>
  </div>
</template>

<script>
  export default {
    name: "WindowReg",
    data(){
      return {
        login: '',
        password: ''
      }
    },
    methods: {
      onSubmit(){
        /*При нажатии на кнопку данные сверяются с данными
        из data-user и если такого логина нет, то данные добавляются
         */
        const users = require('@/data-user.json');
        var bool = true;
        for(let i = 0; i < users.numbUser; i++){
          if(this.login === users.dataUser[i].name){bool = false;}}
        if(bool && this.login.trim() !== '' && this.password.trim() !== '') {
          const user = {
            name: this.login,
            password: this.password
          };
          users.dataUser.push(user);
          users.numbUser++;
          // eslint-disable-next-line no-console
          console.log(users);
          this.$emit('success-reg');
          alert("Успешная регистрацияя");
          this.password = '';
          this.login = ''
        }
        this.$emit('success-reg');
        alert("Вы не зарегестрированы")
      }
    }
  }
</script>

<style scoped>
  .b-popup{
    width:100%;
    min-height:100%;
    background-color: rgba(0,0,0,0.5);
    overflow:hidden;
    position:fixed;
    top:0px;
  }
  .b-popup .b-popup-content{
    margin:100px auto 0px auto;
    width:400px;
    height: 200px;
    padding:10px;
    background-color: rgba(171, 169, 0, 0.62);
    border-radius:3px;
    box-shadow: 0px 0px 10px #000;
  }
  .b-popup-content {
    display: flex;
    flex-direction: column;
  }
  input {
    width: 200px;
    font-size: 13px;
    padding: 6px 0 4px 10px;
    border: 1px solid #93ab00;
    background: #F6F6f6;
    border-radius: 8px;
    margin-right: 10px;
  }
  button {
    display: inline-block;
    font-family: arial,sans-serif;
    font-size: 11px;
    font-weight: bold;
    color: rgb(68,68,68);
    text-decoration: none;
    user-select: none;
    padding: .2em 1.2em;
    outline: none;
    border: 1px solid rgba(0,0,0,.1);
    border-radius: 2px;
    background: rgb(245,245,245) linear-gradient(#f4f4f4, #f1f1f1);
    transition: all .218s ease 0s;
  }
  button:hover {
    color: rgb(24,24,24);
    border: 1px solid rgb(171, 169, 0);
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