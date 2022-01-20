<template>
  <div class="form">
    <form action="" v-if="!newClient">
      <h1>Ваши данные:</h1>
      <div class="form-atributes">
        <div class="form-atributes__item">
          <div class="form-atributes__item-data">
            <label for="surname"> Фамилия*</label>
            <input v-model="surname" id="surname" type="text" />
          </div>
          <div
            class="form-atributes__item-validation"
            v-if="!$v.surname.required"
          >
            **Поле обязательное для заполнения.*
          </div>
        </div>

        <div class="form-atributes__item">
          <div class="form-atributes__item-data">
            <label for="name"> Имя*</label>
            <input v-model="name" id="name" type="text" />
          </div>

          <div class="form-atributes__item-validation" v-if="!$v.name.required">
            **Поле обязательное для заполнения.*
          </div>
        </div>
        <div class="form-atributes__item">
          <div class="form-atributes__item-data">
            <label for="patronymic"> Отчество</label>
            <input id="patronymic" type="text" />
          </div>
        </div>
        <div class="form-atributes__item">
          <div class="form-atributes__item-data">
            <label for="birthday"> Дата рождения*</label>
            <input v-model="birthday" id="birthday" type="text" />
          </div>
        </div>
        <div class="form-atributes__item">
          

          <div class="form-atributes__item-data">
            <label for="phone"> Номер телефона* </label>
            <div class="phone-wrapper">
              <span>+7</span> <input v-model="phone" id="phone" type="number" />
            </div>
          </div>

          <div class="form-atributes__item-validation">
            <div class="surname-validation" v-if="!$v.phone.minLength">
              Должно быть 11 цифр.
            </div>

            <div class="surname-validation" v-if="!$v.phone.maxLength">
              Должно быть 11 цифр.
            </div>

            <div class="surname-validation" v-if="!$v.phone.required">
              **Поле обязательное для заполнения.*
            </div>
          </div>
        </div>
        <div class="form-atributes__item">
          <div class="form-atributes__item-data">
            <label for="gender"> Пол</label> <input id="gender" type="text" />
          </div>
        </div>
      </div>

      <div class="form-atributes__item">
        <div class="form-atributes__item-data">
          <p>Группа клиентов*</p>
          <select multiple v-model="group" id="group">
            <option>VIP</option>
            <option>Проблемные</option>
            <option>ОМС</option>
          </select>
        </div>

        <div class="form-atributes__item-validation" v-if="!$v.group.required">
          **Поле обязательное для заполнения.*
        </div>
      </div>

      <div class="form-atributes__item">
        <div class="form-atributes__item-data">
          <p>Лечащий врач</p>
          <select multiple>
            <option>Иванов</option>
            <option>Захаров</option>
            <option>Чернышева</option>
          </select>
        </div>
      </div>

      <div class="form-atributes__item">
        <div class="form-atributes__item-data">
          <p>
            <input type="checkbox" name="option5" value="a5" />Не отправлять СМС
          </p>
        </div>
      </div>

      <h1>Адрес:</h1>

      <div class="form-adress">
        <div class="form-adress__item">
          <div class="form-adress__item-data">
            <label for="index"> Индекс</label> <input id="index" type="text" />
          </div>
        </div>

        <div class="form-adress__item">
          <div class="form-adress__item-data">
            <label for="country"> Страна</label>
            <input id="country" type="text" />
          </div>
        </div>
        <div class="form-adress__item">
          <div class="form-adress__item-data">
            <label for="region"> Область</label>
            <input id="region" type="text" />
          </div>
        </div>
        <div class="form-adress__item">
          <div class="form-adress__item-data">
            <label for="city"> Город*</label>
            <input v-model="city" id="city" type="text" />
          </div>

          <div class="form-adress__item-validation">
            <div class="surname-validation" v-if="!$v.city.required">
              **Поле обязательное для заполнения.*
            </div>
          </div>
        </div>

        <div class="form-adress__item">
          <div class="form-adress__item-data">
            <label for="street"> Улица</label> <input id="street" type="text" />
          </div>
        </div>
        <div class="form-adress__item">
          <div class="form-adress__item-data">
            <label for="home"> Дом</label> <input id="home" type="text" />
          </div>
        </div>
      </div>

      <h1>Паспорт:</h1>

      <div class="form-document">
        <div class="form-document__item">
          <div class="form-document__item-data">
            <p>Тип документа*</p>
            <select multiple v-model="dtype" id="dtype">
              <option>Паспорт</option>
              <option>Свидетельство о рождении</option>
              <option>Вод. удостоверение</option>
            </select>
          </div>

          <div class="form-document__item-validation">
            <div class="surname-validation" v-if="!$v.dtype.required">
              **Поле обязательное для заполнения.*
            </div>
          </div>
        </div>

        <div class="form-document__item">
          <div class="form-document__item-data"><label for="password-series"> Серия</label>
          <input id="password-series" type="text" /></div>
          
        </div>
        <div class="form-document__item">
          <div class="form-document__item-data"><label for="password-number"> Номер паспорта</label>
          <input id="password-number" type="text" /></div>
          
        </div>
        <div class="form-document__item">
          <div class="form-document__item-data"><label for="issued"> Кем выдан</label>
          <input id="issued" type="text" /></div>
          
        </div>

        <div class="form-document__item">
          <div class="form-document__item-data">
            <label for="dissued"> Дата выдачи*</label>
            <input v-model="dissued" id="dissued" type="text" />
          </div>

          <div class="form-document__item-validation">
            <div class="surname-validation" v-if="!$v.dissued.required">
              **Поле обязательное для заполнения.*
            </div>
          </div>
        </div>
        
      </div>

      

      <input @click="createClient" value="Отправить" :disabled="$v.$invalid" />
    </form>
    <div class="new-client" v-if="newClient">
      <h1>новый клиент успешно создан</h1>
    </div>
  </div>
</template>

<script>
import { required, minLength, maxLength } from "vuelidate/lib/validators";

export default {
  name: "vForm",
  data() {
    return {
      surname: "",
      name: "",
      phone: "",
      group: [],
      city: "",
      dtype: [],
      dissued: "",
      birthday: "",
      newClient: false,
    };
  },
  methods: {
    createClient() {
      this.newClient = true;
    },
  },
  validations: {
    surname: {
      required,
    },
    name: {
      required,
    },
    phone: {
      required,
      minLength: minLength(10),
      maxLength: maxLength(10),
    },
    group: {
      required,
    },
    city: {
      required,
    },
    dtype: {
      required,
    },
    dissued: {
      required,
    },
  },
};
</script>


<style lang="scss">
.form {
  width: 465px;
}

.form-atributes {
  display: flex;
  flex-direction: column;
}

.form-atributes__item {
  display: flex;
  flex-direction: row;
}

.form-atributes__item-data {
  display: flex;
  flex-direction: column;
}

.form-adress {
  display: flex;
  flex-direction: column;
}

.form-document {
  display: flex;
  flex-direction: column;
}

.form-adress__item{
  display: flex;
}

.form-adress__item-data{
  display: flex;
  flex-direction: column;
}

.form-document__item{
  display: flex;
}

.form-document__item-data{
  display: flex;
  flex-direction: column;
}

.form-atributes__item-validation{
  display: flex;
  align-items: center;
}

.form-adress__item-validation{
  display: flex;
  align-items: center;
}

.form-document__item-validation{
  display: flex;
  align-items: center;
}


</style>
