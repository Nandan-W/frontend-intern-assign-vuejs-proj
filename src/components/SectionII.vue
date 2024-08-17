<template>
    <section class="section-II">
      <div class="section-II-header">
        <h1>SECTION II</h1>
      </div>

      <div class="dropdown-container">
        <div class="dropdown-content">
            <select class="dropdown" v-model="selectedOption" @change="fetchShows" >
                <option disabled value="">Select Show Keyword</option>
                <option v-for="(option, index) in dropdownOptions" :key="index" :value="option.value">
                {{ option.text }}
              </option>
            </select>
        </div>
      </div>
      
      <div class="results-container">
          <div v-for="(card, index) in resultCards" :key="index" class="outer-card" :class="card.className">
            <div class="card-type"><h2>{{ card.type }}</h2> </div>
            
            <div class="result-card">
                <div class="card-body">
                  <p class="product-name">{{ card.name }}</p>
                  <p class="product-description">{{ card.description }}</p>
                  <p class="rating">Rating:{{ card.rating }}</p>
                </div>
                <a :href="card.url" class="card-link" target="_blank">
                    <button class="card-button">Click</button>
                </a>
            </div>
        </div>
      </div>

      <div class="additional-options">
        <select class="dropdown">
          <option v-for="(option, index) in additionalOptions1" :key="index" :value="option.value">
            {{ option.text }}
          </option>
        </select>
        <select class="dropdown">
          <option v-for="(option, index) in additionalOptions2" :key="index" :value="option.value">
            {{ option.text }}
          </option>
        </select>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    name: 'SectionII',
    data() {
      return {
        dropdownOptions: [
          { value: "Cars", text: "Cars" },
          { value: "Books", text: "Books" },
          { value: "Computer", text: "Computer" },
          { value: "School", text: "School" },
          { value: "College", text: "College" }
        ],
        resultCards: [

        ],
        selectedOption:"",
        additionalOptions1: [
          { value: 1, text: 'Option 1' },
          { value: 2, text: 'Option 2' }
        ],
        additionalOptions2: [
          { value: 1, text: 'Option 1' },
          { value: 2, text: 'Option 2' }
        ]
      }
    },
    methods:{
        async fetchShows(){
            if( this.selectedOption ){
                try{
                    const response = await fetch(`https://api.tvmaze.com/search/shows?q=${encodeURIComponent(this.selectedOption)}`);
                    const data = await response.json();

                    // now we update results card
                    this.resultCards = data.slice(0,3).map( (item , index) => {
                        const maxDescriptionLength = 500;
                        const fullDescription = item.show.summary ? item.show.summary.replace(/<[^>]+>/g, '') : 'No description available';
                        const truncatedDescription = fullDescription.length > maxDescriptionLength ? fullDescription.substring(0, maxDescriptionLength) + '...': fullDescription;

                        return {
                            className: `card${index+1}`,
                            type: item.show.type,
                            name: item.show.name,
                            description: truncatedDescription,
                            rating: item.show.rating.average ? item.show.rating.average : "Rating Unavailable",
                            url: item.show.url
                        };
                    });
                }
                catch(err){
                    console.log("Error Fetching shows:" , err);
                }
            }
        }
    }
  }
  </script>
  
  <style scoped>
  .section-II {
    background-color: #fff;
    width:100%;
    margin-top:40px;
    padding:30px 0px;
  }
  .section-II-header {
    height: 100px;
    width:100%;
    display: flex;
    align-items: center;
    justify-content: center;


    font-family: 'Roboto';
    font-style: normal;
    font-weight: 400;
    font-size: 28px;
    line-height: 32px;
    text-align: center;
    color: #2B7397;

  }
  .section-II-header h1 {
    color: #007BFF;
  }
  .dropdown{
    margin:5px 25%;
  }
  .dropdown-container {
    margin-bottom: 30px;
}
select {
    margin-left:25%;
    width: 700px;
    height: 70px;
    border-radius: 6px;
    border:none;
    background: #F4FBFF;

    font-family: 'Roboto';
    font-style: normal;
    font-weight: 400;
    font-size: 20px;
    line-height: 24px;
    color: #455A64;
    
    padding-left: 20%
  }
  .results-container {
    display: flex;
    justify-content: space-between;
    width:100%;
    height:900px;
    background: #F7FBFD;
    padding:10px;
  }
  .outer-card{
      display: flex;
      flex-direction: column;
      width: 25%;
      height:100%;
      border-radius: 10px;
      padding: 0px 70px;
      margin: 0px 10px;
    }
  .card-type{
    display: flex;
    text-align:center;
    flex-direction: column;
    width:100%;
    height: 10%;
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 400;
    font-size: 20px;
    line-height: 24px;
    color: #455A64;
}
  .result-card {
    border: 2px solid;
    width:100%;
    height: 90%;
    margin:20px 0px;
    display:flex;
    flex-direction: column;
    align-items: center;
    border: 1px solid ;
    border-radius: 10px;
}
  
  .card-body {
    margin-top: 10px;
    width:100%;
    height:90%;
    display:flex;
    flex-direction: column;
    text-align:center;
    align-content: center;
    flex-direction: column;
  }
  .product-name{
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 400;
    font-size: 20px;
    line-height: 25px;
    text-align: center;
    color: #3B3019;
  }
  .product-description{
    font-family: 'Quicksand';
    font-style: normal;
    font-weight: 500;
    font-size: 20px;
    line-height: 25px;
    text-align: center;
    color: #455A64;
    height:90%;
    padding:20px;
  }
  .rating {
    height:10%;
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 400;
    font-size: 20px;
    line-height: 25px;
    text-align: center;
    color: #455A64;
  }
  .card-link{
    height: 10%;
    width:100%;
  }
  .card-button {
    width: 100%;
    height: 100%;
    border: 2px solid;
    padding: 0;
    border-radius: 5px;
    cursor: pointer;

    font-family: 'Roboto';
    font-style: normal;
    font-weight: 300;
    font-size: 20px;
    line-height: 25px;
    text-align: center;
    color: #FFF;
  }
  .card1 .card-button { border-color: #2B7397; background-color: #2B7397; }
  .card2 .card-button { border-color: #32959D; background-color: #32959D; }
  .card3 .card-button { border-color: #9C7777; background-color: #9C7777; }
  .additional-options {
    margin-top: 20px;
  }
  </style>
  