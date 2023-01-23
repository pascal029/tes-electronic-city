<script>
export default {
  data(){
    return {
      isActive : true,
      activeTab : 'Check In',
      day : new Date (Date.now())

    }
  },
  created (){
  },
  methods : {
    toggleClass (e) {
      this.isActive = !this.isActive
      this.activeTab = e.currentTarget.id
    }
  }
}
</script>

<template>
  <div class="mt-2 mx-2 my-2 ">
    <div class="w-full rounded-lg" id="head">
      <div class="flex">
        <div>
          <span id="iconUser">
            <i  class="fa-regular fa-user"></i>
          </span>
        </div>
        <div class="ml-5 mt-2">
          <p id="username">Hello Username</p>
          <p id="position">Head of front end developer</p>
        </div>
      </div>
    </div>
    <div class="mt-8 ml-2">
      <p id="live" class="text-bold">Live Attendance</p>  
    </div>
    <div class="w-full ml-2 ">
      <div class="flex border border-1 mr-4">
        <div v-bind:class="[isActive ? 'active' : 'inactive']" id="CHECK IN" @click="toggleClass" class="flex flex-1 w-32 justify-center">
          <p class="mt-1">Check In</p>
        </div>
        <div v-bind:class="[isActive ? 'inactive' : 'active']" id="CHECK OUT" @click="toggleClass" class="flex flex-1 w-32 justify-center ">
          <p class="mt-1">Check Out</p>
        </div>
      </div>
    </div>
    <div class="mt-4 ml-2 mr-2">
      <div class="box">
        <div class="flex flex-col">
          <p id="today" class="mx-5 my-5">{{ day.toLocaleDateString(undefined, { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' }) }}</p>
          <div class="flex">
            <div class="ml-5">TIME</div>
            <div class="ml-10">:</div>
            <div class="ml-5">{{ day.getHours() < 10 ? '0' + day.getHours() : day.getHours()}}:{{ day.getMinutes() < 10 ? '0' + day.getMinutes() : day.getMinutes() }}</div>
          </div>
          <div class="flex mt-5">
            <div class="ml-5 ">LOCATION</div>
            <div class=" ml-5">:</div>
          </div>
          <div class="flex mt-10 ml-5">
            <button type="submit" class="btn w-full max-w-xs mt-2" id="buttonAbsence">{{ activeTab }}</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>

#head {
  background-color: #0019FB;
  height: 75px;
}
#iconUser{
  font-size: 3em;
  color: #DCDCDC;
  margin-left: 10px;
}
#username {
  font-size: 18px;
  color : #F9F9F9
}
#position{
  font-size: 16px;
  color : #989898
}
#live {
  font-size: 36px;
  color : #0019FB
}
.active{
  background-color: #F1F1F1;
  color : #0019FB;
  font-weight: bold;
}

.inactive {
  color : #ACACAC
}
.box {
  height : 250px;
  width : 100%;
  background-color: #F1F1F1;
}
#today {
  color : #2E47C7
}

#buttonAbsence {
  background-color : #0019FB
}
</style>