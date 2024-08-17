<template>
    <section class="section-heading">
      <h1>SECTION I</h1>
    </section>

    <main>
      <QuestionSection
        question="Lorem ipsum dolor sit amet, consectetur adipiscing elit."
        type="radio"
        :options="radioOptions"
        name="q1"
      />
      <QuestionSection
        question="Lorem ipsum dolor sit amet, consectetur adipiscing elit."
        type="dropdown"
        :options="dropdownOptions"
      />
      <QuestionSection
        question="Lorem ipsum dolor sit amet, consectetur adipiscing elit."
        type="checkbox"
        :options="checkboxOptions"
        name="q2"
      />
      
    </main>

    <div class="submit-container">
        <button type="submit" class="submit-button">SUBMIT</button>
    </div>
  </template>
  
  <script>
import QuestionSection from './QuestionSection.vue';

  export default {
    name: 'SectionI',
    components:{
        QuestionSection
    },
  data() {
    return {
      radioOptions: [
        { value: 1, text: 'Option 1' },
        { value: 2, text: 'Option 2' },
        { value: 3, text: 'Option 3' },
        { value: 4, text: 'Option 4' }
      ],
      dropdownOptions: [
        { value: 1, text: 'Option 1' },
        { value: 2, text: 'Option 2' },
        { value: 3, text: 'Option 3' },
        { value: 4, text: 'Option 4' },
        { value: 5, text: 'Option 5' }
      ],
      checkboxOptions: [
        { value: 1, text: 'Option 1' },
        { value: 2, text: 'Option 2' },
        { value: 3, text: 'Option 3' },
        { value: 4, text: 'Option 4' }
      ]
    }
  }
  }
  </script>
  
  <style scoped>
  .section-heading {
    height: 200px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #fff;

    font-family: 'Roboto';
    font-style: normal;
    font-weight: 500;
    font-size: 30px;
    line-height: 35px;
    text-align: center;
    color: #01818C;
  }
  .section-heading h1 {
    color: #007BFF;
  }

  .submit-container{
    display: flex;
    flex-direction: column;
    align-items: center;
    

    width: 100%;
    height: 50px;
    
}
.submit-button{
    width:140px;
    height:50px;
    background: #01818C;
    border-radius: 4px;
    
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 700;
    font-size: 16px;
    line-height: 18px;
    text-align: center;
    color: #FFFFFF;
  }
  </style>
  