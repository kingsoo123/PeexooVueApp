<template>
 <div id="app">
        <div class="wrapper row pl-0 pr-0">
                <div class="sideBar col-md-3 col-sm-12 d-flex flex-column align-items-center pt-4 pr-0">
                    <div class="brand">
                        <h1>LOGO</h1>
                    </div>
                    <div class="navigate d-flex flex-column align-items-center">
                        <div class="sideMenu"><span class="lnr lnr-chart-bars"></span>  Dashboard</div>
                        <div class="sideMenu"><span class="lnr lnr-user"></span>  Profile</div>
                        <div class="sideMenu"><span class="lnr lnr-inbox font-large"></span>  Pricing Package</div>
                        <div class="sideMenu active"><span class="lnr lnr-license font-large"></span>  Availablity</div>
                        <div class="sideMenu"><span class="lnr lnr-camera font-large"></span>  Bookings</div>
                        <div class="sideMenu"><span class="lnr lnr-briefcase font-large"></span>  Portfolio</div>
                        <div class="sideMenu"><span class="lnr lnr-picture font-large"></span>  Albums</div>
                        <div class="sideMenu"><span class="lnr lnr-laptop font-large"></span>  Subscription</div>
                        <div class="sideMenu"><span class="lnr lnr-select font-large"></span>  Payment</div>
                        <div class="sideMenu"><span class="lnr lnr-cog font-large"></span>  Settings</div>
                        
                        
                    </div>
                    <p>&copy; 2019 Peexoo Technologies</p>
        
                </div>
                <div class="container col-md-9 col-sm-12 d-flex flex-column  pl-0">
                    <div class="containerMenu">
                        <ul class="d-flex"><li>Explore Photos</li> <li>Find a photographer</li> 
                            <li><span class="lnr lnr-calendar-full font-large"></span></li>
                            <li><span class="lnr lnr-envelope font-large"></span></li>
                            <li><span class="lnr lnr-alarm font-large"></span></li>
                            <li><img src="./assets/img.jpg" alt="profile image" class="user-img" /></li>
                            <li><span class="user-name">Kingsley Bossli</span></li>
                            <li><span class="lnr lnr-chevron-down"></span></li></ul>
                    </div>

                    <div class="row p-4">
                        <div class="col-md-12 mt-4">
                            <h4 class="font-bold">Availablity</h4>
                        </div>
                        <div class="col-md-12">
                            <div class="view-type d-flex justify-content-between font-small">
                                <ul class="d-flex list-style-none p-0 text-primary">
                                    <li><span class="lnr lnr-calendar-full font-large"></span> Calendar view</li>
                                    <li class="ml-4"><span class="lnr lnr-list"></span> List view</li>
                                </ul>
                                <div class="search-schedule">
                                        <div class="form-group has-search">
                                                <span class="lnr lnr-magnifier form-control-feedback "></span>
                                                <input type="text" class="form-control" placeholder="Search">
                                              </div>
                                    <button class="btn btn-primary ml-2" data-toggle="modal" data-target="#newModal"><span class="lnr lnr-plus-circle font-large"></span>  ADD SCHEDULE</button>
                                </div>
                            </div>
                            <div class="schedule-form"></div>
                        </div>
                    <TestCalendar :events="events"></TestCalendar>
                    </div>
                </div>
            </div>

            <div class="modal fade " id="newModal">
               <div class="modal-dialog">
                   <div class="modal-content">
                        <div class="modal-body">
                           <div class="form-group">
                               <label for="title">Event Title</label>
                               <input type="text" name="eventTitle" id="title" class="form-control" placeholder="Enter event title" v-model="form.title">
                            </div> 
                            <div class="form-group">
                                <label for="title">Event Start Date</label>
                               <input type="date" name="start" id="start" class="form-control" v-model="form.start">
                            </div> 
                            <div class="form-group">
                                <label for="end">Event End Date </label>
                               <input type="date" name="end" id="end" class="form-control" v-model="form.end">
                            </div> 
                            <button class="btn btn-primary w-100" @click="addSchedule"><span class="lnr lnr-plus-circle font-large"></span>  ADD SCHEDULE</button>
                        </div>
                   </div>
                </div> 
                
            </div>
    </div>
</template>

<script>
import TestCalendar from './TestCalendar.vue';
export default {
  name: 'app',
  components: {
    TestCalendar
  },
  data(){
      return{
           events : [
            { title: `Mrs Steven daughter's wedding photography`, date: '2019-09-02' },
            { title: `Mrs Peter daughter's wedding photography`, start: '2019-09-09',  end: '2019-09-12'  }
      ],
      form : {
          title : '',
          start : '',
          end : '',
      }
      }
  },
  methods : {
      addSchedule: function(){
          this.events.push(this.form);
      }
  }
}
</script>
<style>
body{
    padding: 0px;
    margin: 0px;
    max-width: 100vw;
    overflow-x: hidden;
    font-family: 'Raleway', sans-serif !important;
}
.font-bold{
    font-weight: bold;
}
.font-small{
    font-size: 0.8em;
}
.text-primary{
    color:hsla(43, 100%, 37%, 1) !important;
}
.list-style-none{
    list-style: none;
}
.btn-primary{
    background-color: #FFB500;
    border-color: #FFB500;
}
.has-search{
    display: inline-block;
    position: relative;
}
.has-search .form-control {
    padding-right: 2.375rem;
}

.has-search .form-control-feedback {
    position: absolute;
    right: 0px;
    z-index: 2;
    display: block;
    width: 2.375rem;
    height: 2.375rem;
    line-height: 2.375rem;
    text-align: center;
    pointer-events: none;
    color: #aaa;
}
.search-schedule .span, .search-schedule button, .search-schedule input{
    font-size: 1em;
}
.wrapper{
    min-height: 100vh;
    background: #FFFDF7;
}
.view-type>ul>li{
    cursor: pointer;
}
.sideBar{
    background: #4D4D4D;
    height: 1100px;
    color: #C1C1C1;
}
.sideBar p{
    margin-top: 160px;
}
.container{
    background: #FFFDF7;
    height: 750px;
}
.brand{
    height: 80px;
    width: 200px;
}
.brand h1{
    color: #FFB500;
    font-weight: bolder;
    letter-spacing: 7px;    
}
.navigate{
    width: 100%;
    height: 800px;
    color: #C1C1C1;
}

.sideMenu{
    padding: 25px;
    width: 100%;
}
.sideMenu.active{
    border-left: 9px solid #ffb500;
    background-color: #5C5C5C;
    color:#ffb500
}
.containerMenu ul{
    list-style: none;
    height: 100%;
    align-items: center;
    justify-content: flex-end;
    margin-right: 15px;
}
.containerMenu ul>li{
    padding: 10px;
    font-size: 0.8em;
    font-weight: 600;

}
.containerMenu ul>li>span.lnr{
    font-size: 1em;
}
.containerMenu ul>li>span.font-large{
    font-size: 1.3em;
}
.containerMenu ul>li>img.user-img{
    max-width: 40px;
    border-radius: 50%;
}
.containerMenu{
    width: 100%;
    box-shadow: 1px 1px 2px #C1C1C1;
}
/**
* overirde css
*/
.form-control:focus {
    color: #495057;
    background-color: #fff;
    border-color: #ffb50061;
    outline: 0;
    box-shadow: 0 0 0 0.1rem rgba(255, 181, 0, 0.14);
}

.btn-primary.focus, .btn-primary:focus{
    box-shadow: 0 0 0 0.1rem rgba(255, 181, 0, 0.14);
}
.btn-primary:not(:disabled):not(.disabled).active,
 .btn-primary:not(:disabled):not(.disabled):active, 
 .show>.btn-primary.dropdown-toggle,
.btn-primary:hover {
    color: #fff;
    background-color: hsla(43, 100%, 63%, 1);
    border-color: hsla(43, 100%, 63%, 1);;
}
</style>

