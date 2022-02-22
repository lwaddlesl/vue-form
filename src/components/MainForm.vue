<template>
  <div class="container">
    <form @submit.prevent="formHandler">
      <div class="form__item">
        <label for="first-name">
          Имя
          <span class="require">*</span>
        </label>
        <input
          :class="status($v.form.firstName)"
          v-model.trim="form.firstName"
          id="first-name"
          type="text"
        />
        <p
          class="required-field"
          v-if="$v.form.firstName.$dirty && !$v.form.firstName.required"
        >
          Обязательное поле
        </p>
      </div>
      <div class="form__item">
        <label for="last-name">
          Фамилия
          <span class="require">*</span>
        </label>
        <input
          :class="status($v.form.lastName)"
          v-model.trim="form.lastName"
          id="last-name"
          type="text"
        />
        <p
          class="required-field"
          v-if="$v.form.lastName.$dirty && !$v.form.lastName.required"
        >
          Обязательное поле
        </p>
      </div>
      <div class="form__item">
        <label for="patronymic">Отчество</label>
        <input v-model.trim="form.patronymic" id="patronymic" type="text" />
      </div>
      <div class="form__item">
        <label for="birth-date">
          Дата рождения
          <span class="require">*</span>
        </label>
        <input
          :class="status($v.form.birthDate)"
          v-model.trim="form.birthDate"
          id="birth-date"
          type="text"
        />
        <p
          class="required-field"
          v-if="$v.form.birthDate.$dirty && !$v.form.birthDate.required"
        >
          Обязательное поле
        </p>
      </div>
      <div class="form__item">
        <label for="phone-number">
          Номер телефона
          <span class="require">*</span>
        </label>
        <input
          :class="status($v.form.phoneNumber)"
          v-model.trim="form.phoneNumber"
          id="phone-number"
          type="text"
        />
        <p
          class="required-field"
          v-if="$v.form.phoneNumber.$dirty && !$v.form.phoneNumber.required"
        >
          Обязательное поле
        </p>
        <p
          class="required-field"
          v-if="$v.form.phoneNumber.$dirty && !$v.form.phoneNumber.numeric"
        >
          Номер должен содержать только цифры
        </p>
        <p
          class="required-field"
          v-if="
            $v.form.phoneNumber.$dirty &&
            !$v.form.phoneNumber.startWithSeven &&
            form.phoneNumber
          "
        >
          Номер должен начинаться с 7
        </p>
        <p
          class="required-field"
          v-if="
            $v.form.phoneNumber.$dirty &&
            !$v.form.phoneNumber.ellevenDigits &&
            form.phoneNumber
          "
        >
          Номер должен содержать 11 цифр
        </p>
      </div>
      <div class="form__item">
        <label for="gender">Пол</label>
        <input v-model.trim="form.gender" id="gender" type="text" />
      </div>

      <div class="form__item">
        <label for="clients">
          Группа клиентов
          <span class="require">*</span>
        </label>
        <select
          :class="status($v.form.clients)"
          multiple
          v-model.trim="form.clients"
          id="clients"
        >
          <option value="VIP">VIP</option>
          <option value="Проблемные">Проблемные</option>
          <option value="ОМС">ОМС</option>
        </select>
        <p
          class="required-field"
          v-if="$v.form.birthDate.$dirty && !$v.form.birthDate.required"
        >
          Обязательное поле
        </p>
      </div>
      <div class="form__item">
        <label for="doctor-label">Лечащий врач</label>
        <select v-model.trim="form.doctor" id="doctor-label">
          <option>Выберите</option>
          <option value="Ivanov">Иванов</option>
          <option value="Zaharov">Захаров</option>
          <option value="Chernyshova">Чернышева</option>
        </select>
      </div>
      <div class="form__item">
        <label for="no-sms">Не отправлять</label>
        <input type="checkbox" v-model.trim="form.sms" id="no-sms" />
      </div>
      <strong> Адрес </strong>
      <div class="form__item">
        <label for="index-input">Индекс</label>
        <input v-model.trim="form.index" id="index-input" type="text" />
      </div>
      <div class="form__item">
        <label for="country-input">Страна</label>
        <input v-model.trim="form.country" id="country-input" type="text" />
      </div>
      <div class="form__item">
        <label for="region-input">Область</label>
        <input v-model.trim="form.region" id="region-input" type="text" />
      </div>
      <div class="form__item">
        <label for="city-input">
          Город
          <span class="require">*</span>
        </label>
        <input
          :class="status($v.form.city)"
          v-model.trim="form.city"
          id="city-input"
          type="text"
        />
        <p
          class="required-field"
          v-if="$v.form.city.$dirty && !$v.form.city.required"
        >
          Обязательное поле
        </p>
      </div>
      <div class="form__item">
        <label for="street-input">Улица</label>
        <input v-model.trim="form.street" id="street-input" type="text" />
      </div>
      <div class="form__item">
        <label for="home-input">Дом</label>
        <input v-model.trim="form.home" id="home-input" type="text" />
      </div>
      <strong> Паспорт </strong>
      <div class="form__item">
        <label for="document-type">
          Тип документа
          <span class="require">*</span>
        </label>
        <select
          :class="status($v.form.documentType)"
          v-model.trim="form.documentType"
          id="document-type"
          type="text"
        >
          <option value="pasport">Паспорт</option>
          <option value="birth certificate">Свидетельство о рождении</option>
          <option value="driving licence">Вод. удостоверение</option>
        </select>
        <p
          class="required-field"
          v-if="$v.form.documentType.$dirty && !$v.form.documentType.required"
        >
          Обязательное поле
        </p>
      </div>
      <div class="form__item">
        <label for="series-pasport-input">Серия</label>
        <input
          v-model.trim="form.series"
          id="series-pasport-input"
          type="text"
        />
      </div>
      <div class="form__item">
        <label for="number-pasport-input">Номер</label>
        <input
          v-model.trim="form.passportNumber"
          id="number-pasport-input"
          type="text"
        />
      </div>
      <div class="form__item">
        <label for="issued-pasport-input">Кем выдан</label>
        <input
          v-model.trim="form.issued"
          id="issued-pasport-input"
          type="text"
        />
      </div>
      <div class="form__item">
        <label for="issue-date-passport-input">
          Дата выдачи
          <span class="require">*</span>
        </label>
        <input
          :class="status($v.form.issueDate)"
          v-model.trim="form.issueDate"
          id="issue-date-passport-input"
          type="text"
        />
        <p
          class="required-field"
          v-if="$v.form.issueDate.$dirty && !$v.form.issueDate.required"
        >
          Обязательное поле
        </p>
      </div>
      <button type="submit">Отправить</button>
    </form>
    <button @click="$v.$reset">Обновить</button>
  </div>
</template>
<script>
import { required, numeric } from "vuelidate/lib/validators";
export default {
  validations: {
    form: {
      firstName: { required },
      lastName: { required },
      birthDate: { required },
      phoneNumber: {
        required,
        numeric,
        startWithSeven(value) {
          return value[0] == 7;
        },
        ellevenDigits(value) {
          return value.length == 11;
        },
      },
      clients: { required },
      city: { required },
      documentType: { required },
      issueDate: { required },
    },
  },
  data() {
    return {
      form: {
        firstName: "",
        lastName: "",
        patronymic: "",
        birthDate: "",
        phoneNumber: "",
        gender: "",
        clients: [],
        doctor: "",
        sms: false,
        //Adress
        index: "",
        country: "",
        region: "",
        city: "",
        street: "",
        home: "",
        //Pasport
        documentType: "",
        series: "",
        passportNumber: "",
        issued: "",
        issueDate: "",
      },
    };
  },
  methods: {
    formHandler() {
      this.$v.form.$touch();
      if (!this.$v.form.$error) {
        alert("Новый клиент успешно создан");
        this.form = {
          firstName: "",
          lastName: "",
          patronymic: "",
          birthDate: "",
          phoneNumber: "",
          gender: "",
          clients: [],
          doctor: "",
          sms: false,
          //Adress
          index: "",
          country: "",
          region: "",
          city: "",
          street: "",
          home: "",
          //Pasport
          documentType: "",
          series: "",
          passportNumber: "",
          issued: "",
          issueDate: "",
        };
        this.$v.$reset();
      } else {
        console.log("validation error");
      }
    },
    status(validation) {
      return {
        error: validation.$error,
        dirty: validation.$dirty,
      };
    },
  },
};
</script>
<style lang="scss" scoped>
.container {
  width: 50vw;
  background-color: rgb(134, 160, 167);
  margin: auto;
  text-align: center;
  .form__item {
    padding: 10px;
    text-align: right;
    margin-right: 20%;
  }
  strong {
    font-size: 20px;
  }
  label {
    margin-right: 10px;
  }
  input,
  select,
  button {
    border: 1px solid rgb(158, 154, 154);
    border-radius: 4px;
    padding: 5px 10px;
    width: 200px;
    background-color: rgba(206, 206, 206, 0.5);
    &:hover {
      box-shadow: 0px 5px 10px 2px rgba(34, 60, 80, 0.2);
    }
  }
  button {
    margin: 5px;
  }

  select {
    width: 220px;
  }
  select[multiple] {
    overflow: hidden;
    padding-top: 20px;
  }
  input[type="checkbox"] {
    width: 220px;
    height: 18px;
    &:hover {
      box-shadow: 0px 5px 10px 2px rgba(255, 255, 255, 0);
    }
  }
  .dirty {
    border-color: #5a5;
    background: #efe;
  }

  .dirty:focus {
    outline-color: #8e8;
  }

  .error {
    border-color: red;
    background: #fdd;
  }

  .error:focus {
    outline-color: #f99;
  }
  .required-field,
  .require {
    margin-top: 4px;
    color: rgb(253, 67, 67);
    font-size: 14px;
    font-style: italic;
    font-weight: 100;
  }
}
@media screen and (max-width: 1023px) {
  .container {
    width: 70vw;
  }
}
@media screen and (max-width: 768px) {
  .container {
    width: 100vw;
  }
}
@media screen and (max-width: 500px) {
  .container {
    width: 100vw;
    label {
      display: block;
    }
    .form__item {
      padding: 10px;
      text-align: center;
      margin-right: 0%;
    }
  }
}
</style>