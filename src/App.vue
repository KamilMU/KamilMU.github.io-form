<template>
  <div id="app">
    <form @submit.prevent="submit">
      <PersonalInfo v-bind="{ values: values, handleChange: handleChange }" />
      <Adress v-bind="{ values: values, handleChange: handleChange }" />
      <Passport v-bind="{ values: values, handleChange: handleChange }" />
      <Button v-bind="{ submitStatus: submitStatus }" />
    </form>
  </div>
</template>

<script>
import PersonalInfo from "./components/PersonalInfo";
import Adress from "./components/Adress";
import Passport from "./components/Passport";
import Button from "./components/Button";
import { required, minLength } from "vuelidate/lib/validators";

const setSex = (sex) => sex === "м" || sex === "ж";

export default {
  name: "App",
  components: {
    PersonalInfo,
    Adress,
    Passport,
    Button,
  },
  data() {
    return {
      values: {
        surname: "",
        name: "",
        patronymiс: "",
        dateOfBirth: "",
        phoneNumber: "",
        sex: "",

        index: "",
        country: "",
        house: "",
        region: "",
        stree: "",
        city: "",

        type: "",
        seria: "",
        number: "",
        department: "",
        dateOfIssue: "",
      },
      submitStatus: null,
    };
  },
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
  methods: {
    handleChange(inputValue, v) {
      this.values[inputValue] = v.target.value;
    },
    submit() {
      this.$v.$touch();
      console.log(this.$v.$error, "submit!");

      if (this.$v.$invalid) {
        this.submitStatus = "ERROR";
      } else {
        // do your submit logic here
        this.submitStatus = "PENDING";
        setTimeout(() => {
          this.submitStatus = "OK";
        }, 500);
      }
    },
  },
};
</script>

<style lang="sass">
body
  font-family: 'Roboto', sans-serif

  form
    margin: 0 auto
    padding: 10px 25px
    box-shadow: 0 0 10px rgba(0,0,0,0.5)

    @media (max-width: 778px)
      width: 80%

    @media (min-width: 779px)
      width: 50%

    label
      display: flex
      flex-direction: column
      font-weight: bold
      margin-top: 10px

      @media (max-width: 368px)
        font-size: 16px

      @media (min-width: 369px)
        font-size: 14px

    .person-info
      display: flex
      flex-direction: column
      justify-content: space-between

      &__bottom
        display: flex
        flex-direction: column
        flex-wrap: wrap
        justify-content: space-between
        width: 100%

      &__checkbox
        flex-direction: row
        align-items: center
        justify-content: space-between

    .adress
      @extend .person-info

    .passport
      @extend .person-info

    input[type="checkbox"]
      cursor: pointer
      margin-top: 12px

    input[type="text"],
    input[type="number"],
    input[type="date"]
      padding: 10px
      color: black
      box-sizing: border-box
      margin-top: 12px
      width: 100%

      &:focus
        outline: none !important
        border: 1px solid black
        box-shadow: 0 0 12px #505050

    h1
      @media (max-width: 368px)
        font-size: 18px

      @media (min-width: 369px)
        font-size: 20px

    .error
      font-size: 12px
      color: rgb(224, 61, 61)
      font-weight: bold
      margin-top: 5px

    select
      height: 40px
      margin-top: 12px

    button
      cursor: pointer
      padding: 10px
      margin-top: 10px
</style>
