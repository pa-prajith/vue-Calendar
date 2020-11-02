<template>
  <header>
      <h1><i class="far fa-calendar-alt"></i> Calendar <i class="far fa-calendar-alt"></i></h1>
  </header>
  <div class="calendar-container">
      <div class="calendar-header">
          <span><h2>{{selectedMonth}}</h2></span>
          <span><h2>{{selectedYear}}</h2></span>
      </div>
        <div class="row">
            <div v-for="day in weekDays" class="col" :key="day"><h3>{{day}}</h3></div>
        </div>
        <div class="row">
            <div v-for="num1 in selectedFirstDay" class="col" :key="num1"></div>
            <div v-for="num in lastDayOfMonth" class="col"  :class="IsToday(num) ? 'today' : ''" :key="num">{{num}}</div>
        </div>
        <div class="calendar-footer">
            <span>
                <i @click="prevYearHandler" class="fas fa-arrow-alt-circle-left"></i>
                <i @click="prevMonthHandler" class="far fa-arrow-alt-circle-left"></i>
            </span>
            <span>
                <i @click="nextMonthHandler" class="far fa-arrow-alt-circle-right"></i>
                <i @click="nextYearHandler" class="fas fa-arrow-alt-circle-right"></i>
            </span>
        </div>
  </div>

</template>

<script>
export default {
    name: 'Calendar',

    data() {
        let selectedDate = new Date();
        const today = new Date().toLocaleDateString('en-US', {day: 'numeric'});
        let selectedMonth = new Date().toLocaleString('en-US', {month: 'long'});
        let selectedYear = new Date().toLocaleString('en-US', {year: 'numeric'});
        let selectedFirstDay = new Date().getDay();
        let lastDayOfMonth = new Date(new Date().getFullYear(), new Date().getMonth() + 1, 0).getDate();
        const weekDays = ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'];
        return {
            today,
            selectedMonth,
            selectedYear,
            selectedFirstDay,
            lastDayOfMonth,
            selectedDate,
            weekDays
        };
    },

    methods: {
        prevMonthHandler() {
            this.getSelectedDate();
            this.selectedDate.setMonth(this.selectedDate.getMonth() - 1);
            this.setCalenderData()
        },

        nextMonthHandler() {
            this.getSelectedDate();
            this.selectedDate.setMonth(this.selectedDate.getMonth() + 1);
            this.setCalenderData()
        },

        prevYearHandler() {
            this.getSelectedDate();
            this.selectedDate.setFullYear(this.selectedDate.getFullYear() - 1); 
            this.setCalenderData()
        },

        nextYearHandler() {
            this.getSelectedDate();
            this.selectedDate.setFullYear(this.selectedDate.getFullYear() + 1);
            this.setCalenderData()
        },

        getSelectedDate() {
            this.selectedDate = new Date(this.selectedDate.getFullYear(), this.selectedDate.getMonth(), 1);
        },

        setCalenderData() {
            this.selectedMonth = this.selectedDate.toLocaleString('en-US', {month: 'long'});
            this.selectedYear = this.selectedDate.toLocaleString('en-US', {year: 'numeric'});
            this.selectedFirstDay = this.selectedDate.getDay();
            this.lastDayOfMonth = new Date(this.selectedDate.getFullYear(), this.selectedDate.getMonth() + 1, 0).getDate(); 
        },

        IsToday(d) {
            return (this.selectedDate.getFullYear() === new Date().getFullYear() && this.selectedDate.getMonth() === new Date().getMonth() && +this.today === d)? true : false;
        }
    }

}
</script>

<style>
    header {
        text-align: center;
        margin-bottom: 50px;
    }

    .calendar-container {
        text-align: center;
        width: 45%;
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
        justify-content: center;
    }

    .calendar-header span {
        margin-left: 20px;
    }

    .calendar-footer {
        display: flex;
        justify-content: center;
        font-size: 40px;
        margin: 10px 20px;
    }

    .calendar-footer i {
        margin-right: 50px;
    }

    .today {
        color: red;
        font-weight:900;
    }
</style>