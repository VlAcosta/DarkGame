<template>
  <div>
    <div class="base">
      <img src="../assets/fon_rent.png" />
      <a href="/">
        <img id="logo" src="../assets/logo_rent.svg" />
      </a>
      <div class="form_rent">
        <span id="user_name">Имя</span>
        <input type="text" id="name_input" placeholder="Ваше Имя" />
        <span id="user_phone">Номер телефона</span>
        <input type="text" id="phone_input" placeholder="+7(123)456-78-90" />
        <span id="user_email">Электронная почта</span>
        <input type="text" id="email_input" placeholder="Example@gamedark.ru" />
        <span id="type_room">Тип игрового зала</span>
        <div class="radio_room">
          <input
            type="radio"
            name="room"
            class="custom_radio"
            id="standart_room"
          />
          <span id="standart_span">Standart</span>
          <input type="radio" name="room" class="custom_radio" id="vip_room" />
          <span id="vip_span">Premium</span>
          <input
            type="radio"
            name="room"
            class="custom_radio"
            id="console_room"
          />
          <span id="console_span">Console</span>
        </div>
        <span id="time_game">Время брони</span>
        <input type="time" id="time_game_start" />
        <input type="time" id="time_game_end" />
        <div class="place">
          <!--<span id="place">Выберите место</span>-->
        </div>
      </div>
    </div>
    <foot />
  </div>
</template>

<script>
import foot from "../components/footer.vue";
import axios from "axios";

export default {
  components: {
    foot,
  },
  data: {
    return: {
      books: [],
      addBooking: {
        Name: "",
        Number: "",
        Email: "",
        Type: "",
      },
    },
  },

  methods: {
    addBook(payload) {
      const path = "";
      axios
        .post(path, payload)
        .then(() => {
          console.log("Пост запрос выполнен");
        })
        .catch((error) => {
          // eslint-отключение следующей строки
          console.log(error);
        });
    },
    initForm() {
      this.Name = "";
      this.Number = "";
      (this.Email = ""), (this.Type = "");
    },
    onSubmit(evt) {
      evt.preventDefault();
      this.$refs.addBookModal.hide();
      let read = false;
      if (this.addBookForm.read[0]) read = true;
      const payload = {
        Name: this.Name,
        Number: this.Number,
        Email: this.Email,
        occude: this.Type,
      };
      this.addBook(payload);
      this.initForm();
    },
  },
};
</script>

<style  scoped>
body {
  height: 1080px;
}
.base {
  width: 100%;
}
#logo {
  position: absolute;
  left: 7.03%;
  top: 10.02%;
}
.form_rent {
  position: absolute;
  width: 62%;
  height: 110%;
  top: 43.6%;
  left: 20.5%;
}
#user_name,
#user_phone,
#user_email,
#type_room,
#time_game,
#place {
  position: absolute;
  width: 100%;
  font-family: "Roboto" sans-serif;
  font-style: normal;
  font-weight: bold;
  font-size: 37px;
  line-height: 43px;
  display: flex;
  align-items: center;

  color: #ffffff;
}
#user_name {
  left: 2.5%;
}
#user_phone {
  top: 21%;
  left: 2.5%;
}
#user_email {
  top: 42.5%;
  left: 2.5%;
}

#time_game {
  top: 90%;
}

.place {
  position: relative;
  width: 100%;
  top: 110%;
}
input[type="time"] {
  position: absolute;
  top: 95%;
}

#time_game_start {
  left: 0%;
}
#time_game_end {
  left: 10%;
}

input[type="text"] {
  position: absolute;
  width: 100%;
  height: 66px;
  background: rgba(0, 0, 0, 0.35);
  border: 1px solid rgba(255, 255, 255, 0.09);
  border-radius: 6px;
  color: #ffffff;
  font-size: 37px;
  padding-left: 1.5%;
}

#name_input {
  top: 4%;
}

#phone_input {
  top: 25%;
  left: 0%;
}

#email_input {
  top: 46.5%;
}

#type_room {
  top: 63%;
}
.radio_room {
  position: absolute;
  width: 100%;
  top: 70%;
}

input[type="radio"] {
  position: absolute;
  width: 38px;
  height: 38px;
}

#standart_room {
  left: 2%;
}

#standart_span {
  left: 7%;
}

#vip_room {
  left: 42%;
}

#vip_span {
  left: 47%;
}

#console_room {
  left: 82%;
}

#console_span {
  left: 87%;
}

#standart_span,
#vip_span,
#console_span {
  position: absolute;
  font-family: "Roboto" sans-serif;
  font-style: normal;
  font-weight: bold;
  font-size: 37px;
  line-height: 43px;
  display: flex;
  align-items: center;

  color: #ffffff;
}

#place_standart {
  position: absolute;
  width: 42%;
  height: 47.5%;
  left: 28%;

  background: rgba(0, 0, 0, 0.1);
}
::-webkit-input-placeholder {
  position: absolute;
  top: 20%;
  left: 1.5%;

  font-family: "Roboto" sans-serif;
  font-style: normal;
  font-weight: 500;
  font-size: 33px;
  line-height: 39px;

  color: rgba(255, 255, 255, 0.17);
}
::-moz-placeholder {
  position: absolute;
  top: 20%;
  left: 1.5%;

  font-family: "Roboto" sans-serif;
  font-style: normal;
  font-weight: 500;
  font-size: 33px;
  line-height: 39px;

  color: rgba(255, 255, 255, 0.17);
} /* Firefox 19+ */
:-moz-placeholder {
  position: absolute;
  top: 20%;
  left: 1.5%;

  font-family: "Roboto" sans-serif;
  font-style: normal;
  font-weight: 500;
  font-size: 33px;
  line-height: 39px;

  color: rgba(255, 255, 255, 0.17);
} /* Firefox 18- */
:-ms-input-placeholder {
  position: absolute;
  left: 1.5%;
  top: 10%;

  font-family: "Roboto" sans-serif;
  font-style: normal;
  font-weight: 500;
  font-size: 33px;
  line-height: 39px;

  color: rgba(255, 255, 255, 0.17);
}


@media screen and (max-width: 1280px) {
  #user_name,
  #user_phone,
  #user_email,
  #type_room,
  #time_game,
  #place {
    font-size: 24px;
  }

  #vip_span {
    left: 55%;
    font-size: 20px;
  }
  #standart_span {
    left: 15%;
    font-size: 20px;
  }
  #console_span {
    left: 95%;
    font-size: 20px;
  }
  #time_game_end {
    left: 20%;
  }

  @media screen and (min-width: 601px) {
  }
  @media screen and (max-width: 600px) {
    ::-webkit-input-placeholder {
      font-size: 18px;
    }
  }
  @media screen and (min-width: 401px) {
  }

  @media screen and (max-width: 400px) {
    #console_span,
    #standart_span,
    #vip_span {
      font-size: 16px;
    }
    .radio_room span {
      top: -5px;
    }
    input[type="radio"] {
      position: absolute;
      width: 20px;
      height: 20px;
    }
    #time_game_end {
      left: 50%;
    }
  }
}
</style>