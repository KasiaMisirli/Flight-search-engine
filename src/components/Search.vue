<template>
  <div>
    <h4 class="search-below">{{search}}</h4>

    <form class="search-form" v-on:submit="getFlightsVueResource" >
      <label class="origin ">origin:</label>
      <select v-model="newFlight.origin">
        <option v-for="option in options" v-bind:value="option">
          {{option}}
        </option>
      </select>
      <label class="destination">destination:</label>
      <select v-model="newFlight.destination">
          <option v-for="option in options" v-bind:value="option">
             {{option}}
          </option>
        </select>

      <label class="year">year:</label>
      <input v-model="newFlight.year" type="number" min="2018" max="2018">
      <label class="month">month:</label>
      <input v-model="newFlight.month" type="number" min="7" max="12">
      <label class="day">day:</label>
      <input v-model="newFlight.day" type="number" min="1" max="31">
      <input type="submit" value="Submit" class="submit-btn" >
    </form>
    <div class="flight-proposed" v-if="returnedResponse">
      Origin:{{bestFlight.origin}} Destination: {{bestFlight.destination}}
      Date: {{bestFlight.year}}.{{bestFlight.month}}.{{bestFlight.day}}
      Time: {{bestFlight.hour}}.{{bestFlight.minute}}
      Price:<span class="price1"> {{bestFlight.price}}</span>
      Currency: {{bestFlight.currency}}

    </div>
  </div>
</template>

<script>
export default {
  name: 'flights',
  data(){
    return {
      search: 'search below',
      newFlight: {
        origin: 'Please select',
        destination: 'Please select',
        year: '',
        month: '',
        day:''
      },
      bestFlight: [
        {
          origin: '',
          destination: '',
          day: null,
          month: null,
          year: null,
          price: null,
          currency: '',
          hour: null,
          minute: null
        }
      ],
      options:["Please select", "Melbourne","Sydney","Darwin","Canberra","Newcastle","Perth","Brisbane","Adelaide","Gold Coast","Hobart"],
      returnedResponse: false
    }
  },
  methods: {
    getFlightsVueResource: function(){
      var flightOrigin = this.newFlight.origin
      var flightDest = this.newFlight.destination
      var flightYear = this.newFlight.year
      var flightMonth= this.newFlight.month
      var flightDay = this.newFlight.day
      axios.get("https://flight-api-mbynoyjqmf.now.sh/flights&origin="+flightOrigin+"&destination="+flightDest+"&year="+flightYear+"&month="+flightMonth+"&day="+flightDay)
        .then(response => {
          this.bestFlight = response.data
          this.returnedResponse = true
        })
    }
  }
}

</script>
<style scoped>
.search-below{
  background: rgb(206, 157, 157);
  color:rgb(123, 73, 173);
}
.search-form {
  background:rgb(180, 154, 199);
  color: rgb(120, 44, 44);
  font-weight: 700;
  height: 50px;
  padding-top: 10px;
}
.flight-proposed {
  font-size: 1em;
  color: rgb(35, 35, 150);
  background-color: lightblue;
  font-weight: 700;
  padding-top: 10px;
  height: 50px;
}
input {
  border-radius: 5px;
  width: 90px;
}
.origin {
  display: inline;
}
.destination {
  display: inline;
}
.year {
  display: inline;
}
.month {
  display: inline;
}
.day {
  display: inline;
}
.submit-btn {
  background-color: #458062;
  color:blanchedalmond;
  font-weight:700;
}
</style>
