<template>
  <div class="passport">
    <h1>Паспорт</h1>
    <div class="passport__document-type">
      <label>
        Тип дркумента
        <select name="" id="" v-model="values.type">
          <option value="1">Паспорт</option>
          <option value="2">Свидетельство о рождении</option>
          <option value="3">Вод. удостоверение</option>
        </select>
        <div class="error" v-if="!$v.values.type.required">
          Обязательно для заполнения
        </div>
      </label>
    </div>
    <div class="passport__seria">
      <label>
        Серия
        <input
          type="text"
          v-model="values.seria"
          @input="handleChange(values.seria, $event)"
        />
      </label>
    </div>
    <div class="passport__number">
      <label>
        Номер
        <input
          type="number"
          v-model="values.number"
          @input="handleChange(values.number, $event)"
        />
      </label>
    </div>
    <div class="passport__department">
      <label>
        Кем выдан
        <input
          type="text"
          v-model="values.department"
          @input="handleChange(values.department, $event)"
        />
        <div class="error" v-if="!$v.values.department.minLength">
          Должно содержать минимум
          {{ $v.values.department.$params.minLength.min }} букв.
        </div>
      </label>
    </div>
    <div class="passport__date-of-issue">
      <label>
        Дата выдачи
        <input
          type="date"
          v-model="values.dateOfIssue"
          @input="handleChange(values.dateOfIssue, $event)"
        />
      </label>
      <div class="error" v-if="!$v.values.city.required">
        Обязательно для заполнения
      </div>
    </div>
  </div>
</template>

<script>
import { required, minLength } from "vuelidate/lib/validators";

export default {
  name: "Passport",
  props: ["values", "handleChange"],
  validations: {
    values: {
      city: {
        required,
      },

      type: {
        required,
      },
      department: {
        minLength: minLength(10),
      },
    },
  },
};
</script>

<style>
</style>