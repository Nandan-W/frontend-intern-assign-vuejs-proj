<template>
    <div class="question-section">
      <p class="question">{{ question }}</p>
      <div v-if="type === 'radio'" class="radio-group">
        <label v-for="(option, index) in options" :key="index"  >
          <input type="radio" :name="name" :value="option.value"  />
          {{ option.text }}
        </label>
      </div>
      <div v-if="type === 'dropdown'">
        <select class="dropdown" v-model="selectedDropdownValue" >
          <option disabled value="">Select Option</option>
          <option v-for="(option, index) in options" :key="index" :value="option.value">
            {{ option.text }}
          </option>
        </select>
      </div>
      <div v-if="type === 'checkbox'" class="checkbox-group">
        <label v-for="(option, index) in options" :key="index" :class="{'selected': selectedCheckboxes.includes(option.value)}" >
          <input type="checkbox" :name="name" :value="option.value" v-model="selectedCheckboxes" />
          {{ option.text }}
        </label>
      </div>
    </div>

    
  </template>
  
  
    <script>
    export default {
    name: 'QuestionSection',
    props: {
        question: String,
        type: String,
        options: Array,
        name: String
    },
    data() {
        return {
        selectedValue: '',
        selectedDropdownValue: '',
        selectedCheckboxes: []
        }
    }
}
</script>

  
  <style scoped>
  .question-section {
    margin: 20px 0;
    padding: 0 100px;
  }
  .question {
    font-size: 16px;
    margin-bottom: 10px;

    font-family: 'Roboto';
    font-style: normal;
    font-weight: 400;
    font-size: 20px;
    line-height: 24px;
    color: #455A64;

  }
  .radio-group, .checkbox-group {
    display: flex;
    flex-direction: column;
  }
  .radio-group label, .checkbox-group label {
    margin-bottom: 15px;
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 400;
    font-size: 16px;
    line-height: 19px;
    color: #455A64;
  }
  .radio-group > label > input:checked ,
  .checkbox-group > label > input:checked{
  background-color: #01818c;
}
  .selected{
    color:#01818c;
  }
  .dropdown {
    width: 100%;
    height: 45px;
    display: block;
    margin-top: 10px;
    padding: 10px;
    padding-left: 20px;
    background-color: white;

    box-sizing: border-box;
    border: 1px solid #C6C6C6;
    border-radius: 10px;

    font-family: 'Roboto';
    font-style: normal;
    font-weight: 400;
    font-size: 20px;
    line-height: 24px;
    color: #455A64;
  }
  .dropdown option:selected{
    color:#01818c;
  }
  </style>
  