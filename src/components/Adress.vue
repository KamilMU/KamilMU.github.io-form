<template>
  <div class="adress">
    <h1>Адрес</h1>
    <div class="adress__index">
      <label>
        Индекс
        <input
          type="number"
          v-model="values.index"
          @input="handleChange(values.index, $event)"
        />
        <div class="error" v-if="!$v.values.index.minLength">
          Должно содержать минимум
          {{ $v.values.index.$params.minLength.min }} цифр.
        </div>
      </label>
    </div>
    <div class="adress__country">
      <label>
        Страна
        <input
          type="text"
          v-model="values.country"
          @input="handleChange(values.country, $event)"
        />
        <div class="error" v-if="!$v.values.country.minLength">
          Должно содержать минимум
          {{ $v.values.country.$params.minLength.min }} букв.
        </div>
      </label>
    </div>
    <div class="adress__region">
      <label>
        Область
        <input
          type="text"
          v-model="values.region"
          @input="handleChange(values.region, $event)"
        />
        <div class="error" v-if="!$v.values.region.minLength">
          Должно содержать минимум
          {{ $v.values.region.$params.minLength.min }} букв.
        </div>
      </label>
    </div>
    <div class="adress__city">
      <label>
        Город
        <input
          type="text"
          v-model="values.city"
          @input="handleChange(values.city, $event)"
        />
        <div class="error" v-if="!$v.values.city.minLength">
          Должно содержать минимум
          {{ $v.values.city.$params.minLength.min }} букв.
        </div>
        <div class="error" v-if="!$v.values.city.required">
          Обязательно для заполнения
        </div>
      </label>
    </div>
    <div class="adress__street">
      <label>
        Улица
        <input
          type="text"
          v-model="values.street"
          @input="handleChange(values.street, $event)"
        />
        <div class="error" v-if="!$v.values.street.minLength">
          Должно содержать минимум
          {{ $v.values.street.$params.minLength.min }} букв.
        </div>
      </label>
    </div>
    <div class="adress__house">
      <label>
        Дом
        <input
          type="number"
          v-model="values.house"
          @input="handleChange(values.house, $event)"
        />
      </label>
    </div>
  </div>
</template>

<script>
import { required, minLength } from "vuelidate/lib/validators";

export default {
  name: "Adress",
  props: ["values", "handleChange"],
  validations: {
    values: {
      city: {
        required,
        minLength: minLength(3),
      },
      index: {
        minLength: minLength(4),
      },
      country: {
        minLength: minLength(8),
      },
      region: {
        minLength: minLength(8),
      },
      street: {
        minLength: minLength(8),
      },
    },
  },
};
</script>

<style>
</style>