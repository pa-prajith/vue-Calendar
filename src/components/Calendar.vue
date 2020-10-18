<template>
  <header>
      <h1><i class="far fa-calendar-alt"></i> Calendar <i class="far fa-calendar-alt"></i></h1>
  </header>
  <div class="calendar-container">
      <div class="calendar-header">
          <span><h2>October</h2></span>
          <span><h2>2020</h2></span>
      </div>
        <div class="row">
            <div class="col"><h3>Sun</h3></div>
            <div class="col"><h3>Mon</h3></div>
            <div class="col"><h3>Tue</h3></div>
            <div class="col"><h3>Wen</h3></div>
            <div class="col"><h3>Thu</h3></div>
            <div class="col"><h3>Fri</h3></div>
            <div class="col"><h3>Sat</h3></div>
        </div>
        <div class="row">
            <div v-for="num in 31" class="col" :key="num">{{num}}</div>
        </div>
        <div class="calendar-footer">
            <span><i class="far fa-arrow-alt-circle-left"></i></span>
            <span><i class="far fa-arrow-alt-circle-right"></i></span>
        </div>
  </div>

</template>

<script>
export default {
    name: 'Calendar'
}
</script>

<style>
    header {
        text-align: center;
        margin-bottom: 50px;
    }

    .calendar-container {
        text-align: center;
        width: 35%;
        margin:0 auto;
    }

    .row {
        display: grid;
        grid-template-columns: repeat(7, 100px);
        column-gap: 5px;
        row-gap: 5px;
        justify-content: center;   
    }

    .col {
        padding: 15px;
    }

    .calendar-header {
        display: flex;
        justify-content: space-between;
    }

    .calendar-footer {
        display: flex;
        justify-content: space-between;
        font-size: 40px;
        margin: 10px 0;
    }
</style>