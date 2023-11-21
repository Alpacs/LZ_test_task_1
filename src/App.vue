<template>
  <div class="main-page">
    <div class="img-block">
      <div class="text-block">
        <h1>Lorem Ipsum is simply</h1>
        <p>Lorem Ipsum is simply</p>
      </div>
    </div>
    <div class="forms-block">
      <h1>Welcome to lorem..!</h1>
      <!-- Переключатель форм -->
      <div class="switch-form">
        <button @click="activeLoginForm()" :style="'color:' + cssRuleButtonLogin.colorFont + '; background-color: ' + cssRuleButtonLogin.colorBG" class="button-switch-form">Login</button>
        <button @click="activeRegisterForm()" :style="'color:' + cssRuleButtonReg.colorFont + '; background-color: ' + cssRuleButtonReg.colorBG" class="button-switch-form">Register</button>
      </div>
      <!-- Форма логина -->
      <form 
        autocomplete="on"
        method="POST"
        action="/Login"
        v-if="cssRuleButton.login.colorBG === '#9E896A'" class="login-form-block forms"
        >
        <h1>Lorem Ipsum is simply dummy text of the printing and typesetting industry.</h1>
        <div class="input-username-block">
          <label for="Name">User name</label>
          <input placeholder="Enter your User name (2-30 sign)" type="text" name="name" required minlength="2" maxlength="30">
        </div>
        <div class="input-password-block">
          <label for="password">Password</label>
          <div class="wrapper-input-password">
            <span @click="hidePass=!hidePass" :class="{active: hidePass}" class="hide-pass"></span>
          <input placeholder="Enter your Password (8-30 sign)" :type="typeOfinput" name="password" required minlength="8" maxlength="30">
          </div>
        </div>
        <p>Forgot Password ?</p>
        <button>Login</button>
      </form>

      <!-- Форма регистрации -->
      <form 
        autocomplete="on"
        method="POST"
        action="/Register"
        v-if="cssRuleButton.reg.colorBG === '#9E896A'" class="reg-form-block forms"
        >
        <h1>Lorem Ipsum is simply dummy text of the printing and typesetting industry.</h1>

        <div class="input-email-block">
          <label for="email">Email Adress</label>
          <input placeholder="Enter your Email Address" type="email" name="email">
        </div>

        <div class="input-username-block">
          <label for="Name">User name</label>
          <input placeholder="Enter your User name (2-30 sign)" type="text" name="name" required minlength="2" maxlength="30">
        </div>

        <div class="input-password-block">
          <label for="password">Password</label>
          <div class="wrapper-input-password">
            <span @click="hidePass=!hidePass" :class="{active: hidePass}" class="hide-pass"></span>
          <input placeholder="Enter your Password (8-30 sign)" :type="typeOfinput" name="password" required minlength="8" maxlength="30">
          </div>
        </div>
        
        <button class="register-button">Register</button>
      </form>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      cssRuleButton: {
        login: {
          colorFont: 'white',
          colorBG: '#9E896A'
        },
        reg: {
          colorFont: '#9E896A',
          colorBG: '#F8EDDD'
        }
      },
      hidePass: true
    }
  },
  computed: {
      cssRuleButtonLogin() {
        return {
          colorFont: this.cssRuleButton.login.colorFont,
          colorBG: this.cssRuleButton.login.colorBG
        }
      },
      cssRuleButtonReg() {
        return {
          colorFont: this.cssRuleButton.reg.colorFont,
          colorBG: this.cssRuleButton.reg.colorBG
        }
      },
      typeOfinput() {
        if(this.hidePass) {
          return 'password'
        }
        return 'text'
      }
  },
  methods: {
    activeLoginForm() {
      this.cssRuleButton.login.colorFont = 'white'
      this.cssRuleButton.login.colorBG = '#9E896A'
      this.cssRuleButton.reg.colorFont = "#9E896A"
      this.cssRuleButton.reg.colorBG = '#F8EDDD'
    },
    activeRegisterForm() {
      this.cssRuleButton.reg.colorFont = 'white'
      this.cssRuleButton.reg.colorBG = '#9E896A'
      this.cssRuleButton.login.colorFont = '#9E896A'
      this.cssRuleButton.login.colorBG = '#F8EDDD'
    }
  }
}
</script>

<style lang="scss">

// Добавление шрифта
@import url('https://fonts.googleapis.com/css2?family=PT+Sans:wght@400;700&display=swap');

// обнуление стилей
html,body,div,span,applet,object,iframe,h1,h2,h3,h4,h5,h6,p,blockquote,pre,a,abbr,acronym,address,big,cite,code,del,dfn,em,img,ins,kbd,q,s,samp,small,strike,strong,sub,sup,tt,var,b,u,i,center,dl,dt,dd,ol,ul,li,fieldset,form,label,legend,table,caption,tbody,tfoot,thead,tr,th,td,article,aside,canvas,details,embed,figure,figcaption,footer,header,hgroup,menu,nav,output,ruby,section,summary,time,mark,audio,video{margin:0;padding:0;border:0;font-size:100%;font:inherit;vertical-align:baseline}
article,aside,details,figcaption,figure,footer,header,hgroup,menu,nav,section{display:block}
html{height:100%}
body{line-height:1}
ol,ul{list-style:none}
blockquote,q{quotes:none}
blockquote:before,blockquote:after,q:before,q:after{content:'';content:none}
table{border-collapse:collapse;border-spacing:0}


.main-page {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  max-width: 100%;

  box-sizing: border-box;
  padding: 38px 97px 37px 41px;

  .img-block {
    display: flex;
    align-items: end;

    width: calc(100%/1.766);
    height: 825px;
    border-radius: 29px;

    background: linear-gradient(180deg, rgba(151, 118, 68, 0.35) 0%, rgba(0, 0, 0, 0.35) 100%),
      url('./assets/cat.png');
    background-size: cover;
    background-position: center;

    .text-block {
      margin-bottom: 55px;
      margin-left: 69px;
      h1 {
        color: white;
        font-family: Poppins, sans-serif;
        font-size: 37px;
        font-style: normal;
        font-weight: 700;
        line-height: normal;
      }
      p {
        color: white;
        font-family: Poppins, sans-serif;
        font-size: 25px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
      }
    }
  }

  .forms-block {
    width: calc(100%/2.867);
    h1 {
      color: #000;
      font-family: Poppins, sans-serif;
      font-size: 16px;
      font-style: normal;
      font-weight: 400;
      line-height: normal;
      margin-bottom: 24px;
      text-align: center;
    }
    .switch-form {
      display: flex;
      width: 329px;
      position: relative;
      margin: 0 auto 52px; 
      box-sizing: border-box;
      padding: 0 13px;
      justify-content: space-between;
      align-items: center;
      border-radius: 33px;
      background-color: #F8EDDD;
      height: 59px;
      .button-switch-form {
        display: block;
        width: 146px;
        height: 40px;
        background: #9E896A;
        border-radius: 33px;
        border: 0;
        cursor: pointer;

        color: #FFF;
        font-family: Poppins, sans-serif;
        font-size: 16px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
      }
    }
    .login-form-block, .forms{
      h1 {
        width: 95.8%;
        margin-bottom: 42px;
        text-align: justify;
        color: #5B5B5B;
        font-family: Poppins, sans-serif;
        font-size: 16px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
      }
      label {
        display: block;
        margin-bottom: 12px;
        color: #000;
        font-family: Poppins, sans-serif;
        font-size: 16px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
        }
      input {
        width: 95.8%;
        height: 54px;
        box-sizing: border-box;
        padding-left: 31px;
        border-radius: 40px;
        border: 1px solid #9E896A;
        background: #FFF;

        color: #000;
        font-family: Poppins, sans-serif;
        font-size: 16px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
      }
      .input-email-block {
        margin-bottom: 30px ;
      }
      .input-username-block {
        input {
          margin-bottom: 30px;
        }
      }
      .input-password-block {
        .wrapper-input-password {
          position: relative;
          display: flex;
          align-items: center;
          .hide-pass {
            position: absolute;
            right: 47px;
            display: block;
            background-size: contain;
            cursor: pointer;
            width: 18px;
            height: 18px;
            background-image: url('./assets/eye.png');
          }
          .hide-pass.active {
            background-image: url('./assets/eyeClosed.png');
          }
        }
      }
      p {
        margin-top: 22px;
        margin-right: 19px;
        text-align: right;
        color: #000;
        font-family: Poppins, sans-serif;
        font-size: 12px;
        font-style: normal;
        font-weight: 300;
        line-height: normal;
      }
      button {
        width: 232px;
        height: 49px;
        border: 0;
        border-radius: 36px;
        background: #9E896A;

        margin-top: 62px;
        margin-right: 19px;
        float: right;
        color: #FFF;
        font-family: Poppins, sans-serif;
        font-size: 16px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
      }
      .register-button {
        background-color: #553E19;
        margin-top: 55px;
      }
    }
  }
}


@media (max-width: 1000px) {
  .main-page {
    padding: 133px 18px 0 26px;
    .img-block {
      display: none;
    }
    .forms-block {
      width: 100%;
    }
  }
}
</style>
