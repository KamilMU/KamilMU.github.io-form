<template>
  <div class="person-info">
    <h1>Личная информация</h1>
    <div class="person-info__surname">
      <label>
        Фамилия
        <input
          type="text"
          v-model="values.surname"
          @input="handleChange(values.surname, $event)"
        />
      </label>
      <div class="error" v-if="!$v.values.surname.required">
        Обязательно для заполнения
      </div>
      <div class="error" v-if="!$v.values.surname.minLength">
        Должно содержать минимум
        {{ $v.values.surname.$params.minLength.min }} букв.
      </div>
    </div>

    <div class="person-info__name-input">
      <label>
        Имя
        <input
          type="text"
          v-model="values.name"
          @input="handleChange(values.name, $event)"
        />
      </label>
      <div class="error" v-if="!$v.values.name.required">
        Обязательно для заполнения
      </div>
      <div class="error" v-if="!$v.values.name.minLength">
        Должно содержать минимум
        {{ $v.values.name.$params.minLength.min }} букв.
      </div>
    </div>

    <div class="person-info__patronymiс">
      <label>
        Отчество
        <input
          type="text"
          v-model="values.patronymiс"
          @input="handleChange(values.patronymiс, $event)"
        />
      </label>
      <div class="error" v-if="!$v.values.patronymiс.minLength">
        Должно содержать минимум
        {{ $v.values.patronymiс.$params.minLength.min }} букв.
      </div>
    </div>

    <div class="person-info__date-of-birth">
      <label>
        Дата рождения
        <input
          type="date"
          v-model="values.dateOfBirth"
          min="1900-01-01"
          max="2021-01-01"
          @input="handleChange(values.dateOfBirth, $event)"
        />
      </label>
      <div class="error" v-if="!$v.values.dateOfBirth.required">
        Обязательно для заполнения
      </div>
    </div>

    <div class="person-info__phone">
      <label>
        Номер телефона
        <input
          type="number"
          v-model="values.phoneNumber"
          @input="handleChange(values.phoneNumber, $event)"
        />
      </label>
      <div class="error" v-if="!$v.values.phoneNumber.minLength">
        Должно содержать минимум
        {{ $v.values.phoneNumber.$params.minLength.min }} цифр.
      </div>
    </div>

    <div class="person-info__sex">
      <label>
        Пол
        <input
          type="text"
          v-model="values.sex"
          @input="handleChange(values.sex, $event)"
        />
      </label>
      <div class="error" v-if="!$v.values.sex.setSex">М или Ж</div>
    </div>

    <div class="person-info__bottom">
      <label>
        Группа клиентов
        <select name="" id="" multiple>
          <option value="">VIP</option>
          <option value="">Проблемные</option>
          <option value="">ОМС</option>
        </select>
      </label>

      <label>
        Лечащий врач
        <select name="" id="">
          <option value="">Иванов</option>
          <option value="">Захаров</option>
          <option value="">Чернышева</option>
        </select>
      </label>

      <label class="person-info__checkbox">
        Не отправлять СМС
        <input type="checkbox" name="" id="" />
      </label>
    </div>
  </div>
</template>

<script>
import { required, minLength } from "vuelidate/lib/validators";

const setSex = (sex) => sex === "М" || sex === "Ж";

export default {
  name: "PersonalInfo",
  props: ["values", "handleChange"],
  validations: {
    values: {
      surname: {
        required,
        minLength: minLength(4),
      },
      name: {
        required,
        minLength: minLength(4),
      },
      patronymiс: {
        minLength: minLength(4),
      },
      dateOfBirth: {
        required,
      },
      phoneNumber: {
        minLength: minLength(11),
      },
      sex: {
        setSex,
      },
    },
  },
};
</script>

<style>
</style>