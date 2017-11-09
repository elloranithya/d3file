  <template>
    <div class="container-fluid" style="height:auto;margin:0px;padding:0px;">
      <span style="display:none">{{checkcredentials()}}</span>
        <div class ="pattern" style="height:100px;text-align:center;  font-size:20px;bottom:2px -moz-box-orient: vertical;vertical-align: bottom;">
         <p class="col-xs-12 col-sm-12" style ="text-align:center;color:white;  font-size:20px; position:relative; margin-top:-10px;">Daily Report</p>
        </div>
        <md-tabs  class="md-transparent">
          <md-tab   id="Month" md-label="Summary">
          <md-tabs class="md-transparent"  >
          <md-tab md-label="collection">
            <div class ="col-md-12" style="min-height:450px;">
            <div class ="col-md-3">
            <p>Select Start Date:</p>
            <datepicker  @click="checkrequired('startpic_ct','startdateerror_ct')"  id = "startpic_ct" class= " startdatepic_ct" style="border:none;width:100%" :format="format"  v-model="today_ct" ref="datepicker">
            </datepicker>
            <p id="startdateerror_ct"  style= "display:none;color:#ff5722;">Kindly choose the start date </p> </div>
            <div class="col-md-3 enddate_ct">
            <p>Select End Date:</p>
           <datepicker @click="checkrequired('endpic_ct','enddateerror_ct')"  id = "endpic_ct" class= "enddatepic_ct" style="border:none;width:100%;" :format="format" v-model="today1_ct"   ref="datepicker">
           </datepicker>
           <p id="enddateerror_ct"  style= "display:none;color:#ff5722;">Kindly choose the end date </p>
           <p id= "startenddatlesserror_ct" style= "display:none;color:#ff5722;">End date should be greater than Start date</p>
       </div>
           <p id="facilityerror_ct" style="display:none; color:#ff5722;">Kindly select the facility</p>
           </div>
           </div> 
           <div class="col-md-3"  style="margin-top:9px;" >   
           <md-button   @click.native="passtable_ct()"  class="button" style="border:none; color:white; background-color:#33D4FF;font-size:15px;">Submit</md-button>
           </div>
          <div class="col-md-12">
          <br>
          <p style= "color:#39BF98;">CollectionSummary:</p>
         <div scoped> 
          <div id ='tab' ></div>
          </div>
          </div>
          </div>
          </md-tab>
          <md-tab md-label="visit">
          <div class ="col-md-12" style="min-height:450px;">
          <div class ="col-md-3">
          <p>Select Date:</p>
          <datepicker  id = date_cp class= " datepic" style="border:none;width:100%;" :format="format" v-model="today_cp"  placeholder="Select Date" ref="datepicker">
          </datepicker><p id="dateerror_cp"  style= "display:none;color:#ff5722;">Kindly choose the  date </p>
          </div>
          <div class="col-md-3 faciy">
          <p>Select Facility:</p>
          <select id="facility_cp" @focus="checkrequired('facility_cp','facilityerror_cp')"  style="width:100%;" v-model="selectedfacility_cp">
          <option  v-for="facility in facilityContent_cp"  v-bind:value="facility.facilityId">{{facility.facilityName}}
          </option>
          </select>
          <div>
          <p id="facilityerror_cp" style="display:none; color:#ff5722;"> Kindly select the facility</p>
          </div>
          </div> 


  <div class="col-md-3"  style="margin-top:9px;" >   

  <md-button   @click.native="passpie_cp()"  class="button" style="border:none; color:white; background-color:#33D4FF;font-size:15px;">Submit</md-button>
   </div>

    <div class="col-md-12">
    <br>
           
                <p style ="color:#39BF98;" >Visit Summary: </p>
                 <div id = "app" style="display:none;">No of Appointments: {{appointmentnum}}</div> 


            <br>
                <div id ='res' class="col-md-6 piegraph ">   

              </div> 

              <div class = "col-md-6" id="res1"></div>
    </div>
      </div>
  </md-tab>
  </md-tabs>

      </md-tab>
      <md-tab id="attendance" md-label="attendance">
   <md-tabs class="md-transparent"  >
    <md-tab  md-icon="view_comfy" md-label="table">
     <div class="col-md-12" style="min-height:450px;">
    <div class="col-md-3">
    <br>
    <p>Select Facility:</p>
    <select @focus="checkrequired('facility_at','facility_aterror')" id="facility_at" style="width:100%;" v-model="selectedfacility_at">
    <option v-for="facility_at in facilityContent_at" v-bind:value="facility_at.facilityId">{{facility_at.facilityName}}
    </option>

    </select>
    <div class="col-md-12">
     <p id="facility_aterror" style="display:none; color:#ff5722;"> Kindly select the facility</p>
     </div>
     </div>
    <div class ="col-md-3">
    <br>
    <p>Select Start Date:</p>
      <datepicker  @click="checkrequired('startpic','startdateerror')"  id = "startpic" class= " datepic" style="border:none;width:100%" :format="format"  v-model="today_at" ref="datepicker">
      </datepicker><p id="startdateerror"  style= "display:none;color:#ff5722;">Kindly choose the start date </p> </div>
      <div class="col-md-3">
      <br>
    <p>Select End Date:</p>
    <datepicker @click="checkrequired('endpic','enddateerror')"  id = "endpic" class= "datepic" style="border:none;width:100%;" :format="format" v-model="today1_at"   ref="datepicker">
      </datepicker><p id="enddateerror"  style= "display:none;color:#ff5722;">Kindly choose the end date </p>
            <p id= "startenddatlesserror_at" style= "display:none;color:#ff5722;">End date should be greater than Start date</p>
    </div>
    <br>
     <div class="col-md-3"  >
    <md-button @click.native="passtable_at()"  class="button_at" style="border:none; color:white; background-color: #33D4FF;font-size:15px;">Submit</md-button>
     </div>
    <br><br><br><br>
     <div   id="tab1" ></div>

    </div>

  </md-tab>
  <md-tab md-icon="track_changes" md-label="graph">
  <div class = "container">
  <div class = "row">
      <div class="col-md-2 ">


  <p>Select Facility:</p>
      <select id="facility_as" @focus="checkrequired('facility_as','facilityerror_as')"  v-on:change="passnursename()" style="width:100%;" v-model="selectedfacility_as"
      >
        <option  v-for="facility_as in facilityContent_as"  v-bind:value="facility_as.facilityId">{{facility_as.facilityName}}
        </option>
        </select>
        <div>
   <p id="facilityerror_as" style="display:none; color:#ff5722;"> Kindly select the facility</p>
   </div>
  </div> 
  <div class="col-md-2 employ">
  <p>Select Employee:</p>
      <select id="employ_as"   @focus="checkrequired('employ_as','employerror_as')"   style="width:100%;" v-model="selectedemploy_as"
      >
        <option  v-for="employ_as in employNurse_as"  v-bind:value="employ_as.employeeId">{{employ_as.name}}
        </option>
        </select>
        <div >
   <p id="employerror_as" style="display:none; color:#ff5722;"> Kindly select the employ</p>
   </div>
  </div> 

   <div class="col-md-2 year " >
   <p>Select Year:</p>
  <select @focus="checkrequired('year_as','yearerror_as')" style="width:100%;"  id = "year_as" v-model="newyear">
  <option value="year">Select year</option>
    <option value="2014">2014 </option>
    <option value="2015">2015</option>
    <option value="2016">2016</option>
    <option value="2017">2017</option>
      <option value="2018">2018 </option>
    <option value="2019">2019</option>
    <option value="2020">2020</option>
    <option value="2021">2021</option>
    <option value="2022">2022</option>
    <option value="2023">2023</option>
    <option value="2024">2024</option>
      <option value="2025">2025</option>
   </select>
     <div >
   <p id="yearerror_as" style="display:none; color:#ff5722;"> Kindly select the Month</p>
   </div>
  </div>

   <div class="col-md-2 month">
   <p>Select Month:</p>
  <select @focus="checkrequired('month_as','montherror_as')" style="width:100%;"   id= "month_as" v-model="newmonth">
  <option value="month">Select month</option>
    <option value="01" >January </option>
    <option value="02">February</option>
    <option value="03">March</option>
    <option value="04">April</option>
    <option value="05">May </option>
    <option value="06">June</option> 
     <option value="07">July</option>
    <option value="08">August</option>
    <option value="09">September</option>
    <option value="10">October</option>
    <option value="11">November</option>
    <option value="12">December</option>
   </select>
        <div>
   <p id="montherror_as" style="display:none; color:#ff5722;"> Kindly select the Month</p>
   </div>
   </div>

  <div class="col-md-2"  >
  <md-button @click.native="passsun_as()"  class="button_as" style="border:none; color:white; background-color: #33D4FF;font-size:15px;width:2px; height:3px;">Submit</md-button>
   </div>
   </div>
  </div>
  <div class="col-md-8"  id="sun">
   
  </div>

  </md-tab>
  </md-tabs>
   
      </md-tab>
          <md-tab id="inventory" md-label="inventory">
         <div class = "container">
  <div class = "row">
  <div class ="col-md-12" style="min-height:450px;">
      <div class="col-md-3 ">


  <p>Select Facility:</p>
      <select id="facility_it" @focus="checkrequired('facility_it','facilityerror_it')" style="width:100%;" v-model="selectedfacility_it"
      >
        <option  v-for="facility_it in facilityContent_it"  v-bind:value="facility_it.facilityId">{{facility_it.facilityName}}
        </option>
        </select>
        <div>
   <p id="facilityerror_it" style="display:none; color:#ff5722;"> Kindly select the facility</p>
   </div>
  </div>
    <div class ="col-md-3 date_it" >

    <p>Select Date:</p>
      <datepicker  @click="checkrequired('datepic_it','datepicerror_it')"  id = "datepic_it" class= " datepic_it" style="border:none;width:100%" :format="format"  v-model="today_it" ref="datepicker">
      </datepicker><p id="datepicerror_it"  style= "display:none;color:#ff5722;">Kindly choose the start date </p> </div>
  <div class="col-md-3"  >
  <md-button @click.native="passtree_it()"  class="button_as" style="border:none; color:white; background-color: #33D4FF;font-size:15px;width:2px; height:3px;">Submit</md-button>
   </div> 
  <div class="col-md-12"   id="invent">

   </div>
  </div>
  </div>
  </div>
   
  </md-tab>
      </md-tabs>
      </div>
    </template> 
    <script>
    /*eslint-disable*/
                  import * as firebase from 'firebase'
                  import Datepicker from 'vuejs-datepicker'
                  import moment from 'moment'
                  export default {
                    components: {
                    Datepicker
                    },
                      name:'res',
                      data () {
                          return {
                   newfacility_ct:'',
                   facilityContent_ct: '',
                   today_ct: moment(this.selectedDate).format('YYYY-MM-DD'),
                   today1_ct: moment(this.selectedDate1).format('YYYY-MM-DD'),
                   today_cp: moment(this.selectedDate).format('YYYY-MM-DD'),
                   today_at: moment(this.selectedDate1).format('YYYY-MM-DD'),
                   today1_at: moment(this.selectedDate).format('YYYY-MM-DD'),
                   today_it: moment(this.selectedDate1).format('YYYY-MM-DD'),
                   facilityContent_cp: '',
                   selectedfacility_cp: '',
                   selectedfacility_it:'',
                   format: 'dd-MM-yyyy',
                   appointmentnum: '',
                   dataformonth: [],
                   datafordate1:[],
                   selectedDate: new Date(),
                   newmonth: moment(this.selectedDate).format('MM'),            
                   newyear:moment(this.selectedDate).format('YYYY'),
                   dataforfacility:'', 
                   date:"2017-07-17",
                   selectedmonth: '',
                   selectedDate: '',
                   selectedDate1:'',
                   facilityContent_as:'',
                   selectedfacility_as:'',
                   selectedemploy_as:'',
                   employNurse_as:'',
                   selectedyear_as:'',
                   selectedmonth_as:'',
                   data_sun:'',
                   alldata:'',
                   facilityContent_it:'',
                   piedata: '',
                   data1:'',
                   data3: [],
                   data2:[],
                   haserror: '',
                   facilityContent_at: '',
                   selectedfacility_at: '',
                   format: 'dd-MM-yyyy',
                   dataformonth: [],
                   datafordate:[],
                   data_tree:'',
                   treeData:'',
                 }
              },
  mounted: function () {
          document.getElementById('doctor').style.display = 'inline'
          document.getElementById('patient').style.display = 'none'
          },
  created: function() {
      this.checkcredentials()
      console.log('WorkingHours created')
      var newid = localStorage.loggeduserid
      var id = localStorage.loggeduseremail
      this.doctorId = newid
          this.$http.get('https://app.ellorasystems.com/curie/calendar/appointment/getFacilities/'+this.doctorId)
                .then(function (response) {
                this.facilityContent_it = response.data
             for(var i = 0; i<this.facilityContent_it.length;i++)
                    {
                      this.selectedfacility_it =this.facilityContent_it[i].facilityId
                    }
   console.log('https://app.ellorasystems.com/curie/inventory/getInventory/'+   this.selectedfacility_it + '/' +this.today  )
      this.$http.get('https://app.ellorasystems.com/curie/inventory/getInventory/'+   this.selectedfacility_it + '/' +this.today  )
                 .then(function (response) {
                      this.data_tree=response.data
                      this.passtree_it()
      })
      })

      this.$http.get('https://app.ellorasystems.com/curie/calendar/appointment/getFacilities/'+this.doctorId)
            .then(function (response) {
                    this.facilityContent_ct = response.data
                    for(var i=0;i<this.facilityContent_ct.length;i++) {
                    this.newfacility_ct = this.facilityContent_ct[i].facilityId
                    }
       this.$http.get('https://app.ellorasystems.com/curie/doctor/getCollectionSummary/'+ this.doctorId + '/' + this.newfacility_ct + '/' +this.today_ct + '/' +this.today1_ct)
            .then(function (response) {
                  this.data1 = response.data
                  this.passtable_ct()
                 })
            })
      this.$http.get('https://app.ellorasystems.com/curie/calendar/appointment/getFacilities/'+this.doctorId)
            .then(function (response) {
             this.facilityContent_cp = response.data
             for(var i = 0; i<this.facilityContent_cp.length;i++)
                    {
                      this.selectedfacility_cp =this.facilityContent_cp[i].facilityId
                    }
             this.$http.get('https://app.ellorasystems.com/curie/doctor/getSickRatio/'+ this.doctorId + '/' +this.selectedfacility_cp + '/' +this.today_cp)
              .then(function (response) {
                     this.data2 = response.data
                     this.passpie_cp()
                  })
            })
      this.$http.get('https://app.ellorasystems.com/curie/calendar/appointment/getFacilities/'+this.doctorId)
                  .then(function (response) {
                    this.facilityContent_at = response.data
                    for(var i = 0; i<this.facilityContent_at.length;i++)
                    {
                      this.selectedfacility_at =this.facilityContent_at[i].facilityId
                    }
                    this.$http.get('https://app.ellorasystems.com/curie/attendance/getAllByDate/'+ this.selectedfacility_at + '/' +this.today + '/' +this.today1 )
                     .then(function (response) {
                        this.data3 = response.data
                        this.passtable_at()
                    })
                })
     this.$http.get('https://app.ellorasystems.com/curie/calendar/appointment/getFacilities/'+this.doctorId)
                .then(function (response) {
                  this.facilityContent_as = response.data
                    for(var i = 0; i<this.facilityContent_as.length;i++)
                    {
                      this.selectedfacility_as =this.facilityContent_as[i].facilityId
                 }
      this.$http.get('https://app.ellorasystems.com/curie/attendance/getNurse/'+this.selectedfacility_as)
                .then(function (response) {
                 this.employNurse_as = response.data
                  for(var i =0; i<this.employNurse_as.length;i++)
                  {
                    this.selectedemploy_as = this.employNurse_as[i].employeeId
                  }
      this.$http.get('https://app.ellorasystems.com/curie/attendance/getAttendance/'+ this.selectedfacility_as + '/' +this.selectedemploy_as+ '/' +this.newyear + '-' + this.newmonth)
             .then(function (response) {
                  this.alldata = response.data
                  this.passsun_as()
                })
      })
      })

     
  },
        
      methods: {
          checkcredentials: function () {
        var thisthis = this
          firebase.auth().onAuthStateChanged(function(user) {
          if (user) {
          firebase.database().ref('/users/' + user.uid).once('value').then(function(snapshot) {
         var username = snapshot.val().email;
         var id = snapshot.val().userId
         var role = snapshot.val().role_key
         var name = snapshot.val().name
         thisthis.$parent.userinitial = thisthis.getinitial(name)
         })
         } else {
        thisthis.$router.push('/app/doctorlogin')
         }
         })
        },
      getinitial(name) {
      for(var i=0;i<name.length;i++) {
      if(i+1 != name.length) {
      if(name[i+1] != "." && name[i+1] != " " && name[i] != "." && name[i] != " ") {
           return name[i].toUpperCase()
      }
      }
      }
      },
    checkrequired(fieldid, errorfield) {

      if (document.getElementById(fieldid).value.length < 1){
              document.getElementById(errorfield).style.display="none"
            } 
        },
      
      checkrequired_endate_ct:function()
      {
        alert('')
         if (document.getElementById("endpic_ct").value.length < 1){
              document.getElementById("startenddatlesserror_ct").style.display="none"
            } 
        

      },
        validatelessthanstartdatedate_ct:function()
        {
        this.today_ct = moment(this.today_ct).format('YYYY-MM-DD')
        this.today1_ct = moment(this.today1_ct).format('YYYY-MM-DD')
        if (this.today_ct>this.today1_ct) {
           document.getElementById("startenddatlesserror_ct").style.display ="block"
         }
         else if (this.today_ct<=this.today1_ct) {
     
           document.getElementById("startenddatlesserror_ct").style.display ="none"
         }
         },
            validatelessthanstartdatedate_at:function()
        {
        this.today_at = moment(this.today_at).format('YYYY-MM-DD')
        this.today1_at = moment(this.today1_at).format('YYYY-MM-DD')
        if (this.today_at>this.today1_at) {
           document.getElementById("startenddatlesserror_at").style.display ="block"
         }
         else if (this.today_at<=this.today1_at) {
     
           document.getElementById("startenddatlesserror_at").style.display ="none"
         }
         },
    validate_ct: function(){

      this.validatelessthanstartdatedate_ct()
      this.haserror ='false'
      if(document.getElementById("facility_ct").value.length< 1){
        document.getElementById("facilityerror_ct").style.display ="block"
        this.haserror ='true'
      }
      else
      {
        document.getElementById("facilityerror_ct").style.display ="none"
      }
      if(document.getElementById("startpic_ct").value.length< 1){
        document.getElementById("startdateerror_ct").style.display ="block"
        this.haserror ='true'
      }
      else
      {
        document.getElementById("startdateerror_ct").style.display ="none"
      }
           if(document.getElementById("endpic_ct").value.length< 1){
        document.getElementById("enddateerror_ct").style.display ="block"
        this.haserror ='true'
      }
      else
      {
        document.getElementById("enddateerror_ct").style.display ="none"
      }
    },
   passtable_ct:function()
      {

   this.today_ct = moment(this.today_ct).format('YYYY-MM-DD')
   this.today1_ct = moment(this.today1_ct).format('YYYY-MM-DD')
        this.validate_ct()
          if (this.haserror != 'true')
      {
        console.log('https://app.ellorasystems.com/curie/doctor/getCollectionSummary/'+ this.doctorId + '/' + this.newfacility_ct + '/' +this.today_ct + '/' +this.today1_ct)
        this.$http.get('https://app.ellorasystems.com/curie/doctor/getCollectionSummary/'+ this.doctorId + '/' + this.newfacility_ct + '/' +this.today_ct + '/' +this.today1_ct)
               .then(function (response) {
                 this.data1 = response.data
                       this.dataformonth = []
                       var temp =new Object()
                temp["totalNoPatients"] = this.data1.totalNoPatients
                temp["consultancy"] = this.data1.consultancy
                temp["totalCost"] = this.data1.totalCost
                temp["vaccination"] = this.data1.vaccination
                temp["pharmacy"] = this.data1.pharmacy
                temp["avgCost"] = this.data1.avgCost
               this.dataformonth.push(temp)
               this.tablegraph_ct(this.dataformonth)
         })
             }
      },
       tablegraph_ct: function (data1) {
          
         if(document.getElementById("app").style.display ="none"){

        document.getElementById("app").style.display ="block"
         }
         
          var list_tab = document.getElementById("tab")
           if (list_tab.childElementCount > 0) {
            list_tab.removeChild(list_tab.childNodes[0])  
          }
          var columns = ['totalNoPatients', 'consultancy',  'vaccination', 'pharmacy', 'totalCost','avgCost']

        var newColumns = ['Total No Of Patients',  'Consultancy', 'Vaccination',
        'Pharmacy','Total Cost','Average Consultancy Cost', ]
        var table = d3.select('#tab').append('table')
            .attr('class','table')
           .attr('border','1px solid black')
              var thead = table.append('thead')
              var tbody = table.append('tbody');

              // append the header row
              thead.append('tr')
                .selectAll('th')
                .data(newColumns).enter()
                .append('th')
                .attr('class','th')
               .style('text-align', 'center')

                .style('font-weight', 'normal')
                       .text(function (column) {      return column })
              // create a row for each object in the data
              var rows = tbody.selectAll('tr')
                .data(data1)
                .enter()
                .append('tr')


              var cells = rows.selectAll('td')
                .data(function (row) {
                  return columns.map(function (column) { 
                 /* if(column == "billed") {
                 
                     return { column: column, value: row[column]+"/"+ tablenewrow}
                  }       
                   
              
                   if(column == "totalBilledCost") {
                     return { column: column, value: row[column]+"/"+ tablenewrow1}
                  }*/
                  return { column: column, value: row[column] }
                })
                })
              .enter()
              .append('td')
                        .style('text-align', 'center')
                            .attr('data-th', function (d) {
          return d.column;

        })
                            .style('font-weight','normal')
                       
                                 //.attr('width' , function () { return '200px' })

               .text(function (d) { return d.value; });
            
            
          },
           validate_cp: function(){
      this.haserror ='false'
      if(document.getElementById("facility_cp").value.length< 1){
        document.getElementById("facilityerror_cp").style.display ="block"
        this.haserror ='true'
      }
      else
      {
        document.getElementById("facilityerror_cp").style.display ="none"
      }

        if(document.getElementById("date_cp").value.length< 1){
        document.getElementById("dateerror_cp").style.display ="block"
        this.haserror ='true'
      }
      else
      {
        document.getElementById("dateerror_cp").style.display ="none"
      }
      
    },
  passpie_cp: function (choosendate) {
              this.appointmentnum = 0
               this.today_cp = moment(this.today_cp).format('YYYY-MM-DD')

        this.validate_cp()
      if (this.haserror != 'true')
      {
           console.log('https://app.ellorasystems.com/curie/doctor/getSickRatio/'+ this.doctorId + '/' +this.selectedfacility_cp + '/' +this.today_cp)

               this.$http.get('https://app.ellorasystems.com/curie/doctor/getSickRatio/'+ this.doctorId + '/' +this.selectedfacility_cp + '/' +this.today_cp)
                    .then(function (response) {
                      this.data2 = response.data
                      this.datafordate = []
           for (var i=0; i<this.data2.length; i++) {
                        var temp = new Object() 

              temp["date"] = this.data2[i].date
              temp["reason"] = this.data2[i].reason
              temp["ratio"] = this.data2[i].ratio
              temp["numOfPatients"] = this.data2[i].numOfPatients
              this.appointmentnum = temp["numOfPatients"]
              this.datafordate.push(temp)
            }
  this.piegraph_cp(this.datafordate)

       })
    }
  },
    piegraph_cp: function (data2) {
       
     
          
                           var width = 700;
                    var  height = 800;
                     var outerRadius = Math.min(width,height)/2;
                     var innerRadius = (outerRadius/5)*4;
                     var legendRectSize = 15,
                       legendSpacing = 10;
            
           var radius = 200
      
       var color = d3.scaleOrdinal()
        .range(["#8dd3c7","#F0DB75","#bebada","#BC8F8F","#80b1d3","#fdb462","#b3de69","#fccde5","#536878","#A3C1AD","#befcff","#DEB887","#FFAEB9","#6495ED","#4EEE94",
          "#FFFF99",  

          "#B5A642","#FA8072", "#71C671", "#BFBFBF","#5F9EA0" ,"#00C78C","#FFEC8B","#EEA9B8","#AB82FF ","#6CA6CD","#FFEC8B",]);

            var list3 = document.getElementById("res")
         if (list3.childElementCount > 0) {
          list3.removeChild(list3.childNodes[0])  
        }
        var arc = d3.arc()
            .outerRadius(radius - 50)
            .innerRadius(0)

        var labelArc2 = d3.arc()
            .outerRadius(radius - 120)
            .innerRadius(radius - 70)
        
        var pie = d3.pie()
            .sort(null)
            .value(function(d) { return d.ratio })
        var svg = d3.select('#res').append("svg")
            .attr("width", width)
            .attr("height", height)

          .append("g")
            .attr("transform", "translate(" + width / 2 + "," + height / 3 + ")")
          
          var g = svg.selectAll(".arc")
              .data(pie(data2))
            .enter().append("g")
              .attr("class", "arc")
          g.append("path")
              .attr("d", arc)
              .style("fill", function(d) { return color(d.data.reason) })

           
          g.append("text")

       
             .attr('x', height/100)
             .attr('y', 200)
    /*.text(function(d) { return 'Total Appointments='+ d.data.numOfPatients })
       .style('font-size', '20')
    */

            var list4 = document.getElementById("res1")
         if (list4.childElementCount > 0) {
          list4.removeChild(list4.childNodes[0])  
        }
     var svg = d3.select('#res1').append("svg")
            .attr("width", width)
            .attr("height", height)
            .attr('viewBox','0 0 '+Math.min(width,height) +' '+Math.min(width,height) )
            .attr('preserveAspectRatio','xMinYMin')
          .append("g")
            .attr("transform", "translate(" + width/150 + "," + height/5 + ")")
     var legend = svg.selectAll('.legend')
      .data(color.domain())
      .enter()
      .append('g')
      .attr('class', 'legend')
      .attr('transform', function(d, i) {
        var height = legendRectSize + legendSpacing;
        var offset =  height * color.domain().length / 2;
        var horz = 2;
        var vert =  -150+i * height
        return 'translate(' + horz + ',' + vert + ')';
      });
      
    legend.append('rect')
      .attr('width', legendRectSize)
      .attr('height', legendRectSize)
        
      .style('fill', color)
      .style('stroke', color);
      legend.append('text')
      .data(data2)
      .attr('x',20)
      .attr('y', 12)
      .text(function(d) { return d.reason + " " + ":"+ " "  + d.ratio ; })
       .attr('viewBox','0 0 '+Math.min(width,height) +' '+Math.min(width,height) )
            .attr('preserveAspectRatio','xMinYMin')
      .style('font-size', '15')

            },
  validate_at: function(){
      this.haserror ='false'
      if(document.getElementById("startpic").value.length< 1){
        document.getElementById("startdateerror").style.display ="block"
        this.haserror ='true'
      }
      else
      {
        document.getElementById("startdateerror").style.display ="none"
      }
      if(document.getElementById("endpic").value.length< 1){
        document.getElementById("enddateerror").style.display ="block"
        this.haserror ='true'
      }
      else
      {
        document.getElementById("enddateerror").style.display ="none"
      }
        if(document.getElementById("facility_at").value.length< 1){
        document.getElementById("facility_aterror").style.display ="block"
        this.haserror ='true'
      }
      else
      {
        document.getElementById("facility_aterror").style.display ="none"
      }
    },
  passtable_at: function () {
  this.validatelessthanstartdatedate_at()
    this.today_at = moment(this.today_at).format('YYYY-MM-DD')
    this.today1_at = moment(this.today1_at).format('YYYY-MM-DD')

    this.validate_at()

       /* if(this.enddate.value==undefined)
        {
          this.enddate = this.startdate
        }
    else{
      this.enddate = this.enddate
    }*/
      if (this.haserror != 'true')
      {
    console.log('https://app.ellorasystems.com/curie/attendance/getAllByDate/'+ this.selectedfacility_at + '/' +this.today_at + '/' +this.today1_at)
    this.$http.get('https://app.ellorasystems.com/curie/attendance/getAllByDate/'+ this.selectedfacility_at + '/' +this.today_at + '/' +this.today1_at )

                    .then(function (response) {


        this.data3 = response.data


           this.datafordate1 = []


       
          
           for (var i=0; i<this.data3.length; i++) {
              var temp = new Object() 

                    temp["name"] = this.data3[i].name


          temp["numOfDaysPresent"] = this.data3[i].attendanceRatio.numOfDaysPresent
             temp["numOfDaysAbsent"] = this.data3[i].attendanceRatio.numOfDaysAbsent
          this.datafordate1.push(temp)

                  
           
        }
               this.tablegraph_at(this.datafordate1) 
               
      
            
        })
                  
                  }
                },    

             tablegraph_at: function (data3) {


           var list3 = document.getElementById("tab1")
           if (list3.childElementCount > 0) {
            list3.removeChild(list3.childNodes[0])  
          }
      var columns = ['name','numOfDaysPresent', 'numOfDaysAbsent']

      var newcolumns1 = ['Name', 'Days Present','Days Absent',  ]
      
          

         var table = d3.select('#tab1').append('table')
            .attr('class','table')
           .attr('border','1px solid black')
        var thead = table.append('thead')
        var tbody = table.append('tbody');

        // append the header row
        thead.append('tr')
          .selectAll('th')
          .data(newcolumns1).enter()
          .append('th')

            .text(function (column) { return column; })
            .style("font-weight", "normal")

        // create a row for each object in the data
        var rows = tbody.selectAll('tr')
          .data(data3)
          .enter()
          .append('tr');

        // create a cell in each row for each column
        var cells = rows.selectAll('td')
     
          .data(function (row) {
            return columns.map(function (column) {
              return { column: column, value: row[column]};

            });
          })
          .enter()
          .append('td')
             .attr('class', 'tdclass')
             .attr('width' , function () { return '200px' })
            .text(function (d) {  return d.value; });
              // set the dimensions and margins of the graph
            
          },
                passnursename:function()
  {
    this.$http.get('https://app.ellorasystems.com/curie/attendance/getNurse/'+this.selectedfacility_as)
                .then(function (response){

                  this.employNurse_as = response.data
                })
              
  },
  validate_as: function(){
    this.haserror ='false'

      if(document.getElementById("facility_as").value.length< 1){
      document.getElementById("facilityerror_as").style.display ="block"
      this.haserror ='true'
    }
    else
    {
      document.getElementById("facilityerror_as").style.display ="none"
    }
      if(document.getElementById("employ_as").value.length< 1){
      document.getElementById("employerror_as").style.display ="block"
      this.haserror ='true'
    }
    else
    {
      document.getElementById("employerror_as").style.display ="none"
    }

     if(document.getElementById("year_as").value.length<1){
      document.getElementById("yearerror_as").style.display ="block"
      this.haserror ='true'
    }
    else
    {
      document.getElementById("yearerror_as").style.display ="none"
    }
     if(document.getElementById("month_as").value.length< 1){
      document.getElementById("montherror_as").style.display ="block"
      this.haserror ='true'
    }
    else
    {
      document.getElementById("montherror_as").style.display ="none"
    }
  },
  passsun_as:function() {

       this.validate_as()
    if (this.haserror != 'true')
      {
  console.log('https://app.ellorasystems.com/curie/attendance/getAttendance/'+ this.selectedfacility_as + '/' +this.selectedemploy_as+ '/' +this.newyear + '-' + this.newmonth)
   this.$http.get('https://app.ellorasystems.com/curie/attendance/getAttendance/'+ this.selectedfacility_as + '/' +this.selectedemploy_as+ '/' +this.newyear + '-' + this.newmonth)

     .then(function (response) {

              this.alldata = response.data
        

              if(this.alldata!="")
              {
              
                            this.sunbrust(this.alldata)

            }
            else {
            
                       
                            this.sunbrust()


            }

            

       })

  }
  },

  sunbrust: function(data_sun) {
  var width = 960,
      height = 700,
      radius = (Math.min(width, height) / 2) 
  var formatNumber = d3.format(",d");
  var x = d3.scaleLinear()
      .range([0, 2 * Math.PI]);
  var y = d3.scaleLinear()
      .range([0, radius]);
  var color = d3.scaleOrdinal()
      .range(["#8dd3c7","#F0DB75","#bebada","#BC8F8F","#80b1d3","#fdb462","#b3de69","#fccde5","#d9d9d9","#c9c9ff","#befcff","#ffffb3"]);
          var list = document.getElementById("sun")
         if (list.childElementCount > 0) {
          list.removeChild(list.childNodes[0])  
        }
  var partition = d3.partition();
  var arc = d3.arc()
    var arc = d3.arc()
      .startAngle(function(d) { return Math.max(0, Math.min(2 * Math.PI, x(d.x0)));})
      .endAngle(function(d) { return Math.max(0, Math.min(2 * Math.PI, x(d.x1))); })
      .innerRadius(function(d) { return Math.max(0, y(d.y0)); })
      .outerRadius(function(d) { return Math.max(0, y(d.y1)); });
    
  var svg = d3.select("#sun").append("svg")
      .attr("width", width)
      .attr("height", height)
       .attr("viewBox", "0 0 "+ width +" " + height +"")
      .attr("preserveAspectRatio", "xMidYMid")
    .append("g")
      .attr("transform", "translate(" + width / 2 + "," + (height / 2) + ")");
    
  var text,
      path;
      
    var data2 = d3.hierarchy(data_sun);
    data2.sum(function(d) { console.log(d.size); return d.size; });
   
    svg.selectAll("path")
          .data(partition(data2).descendants())
          .enter().append("g").attr("class", "node")

    
    path = svg.selectAll(".node")
        .append("path")
    
        .attr("d", arc)
       .attr("stroke", "grey")
          .style("fill", function (d) {

            if (d.data.name=="Present")
            {
              return "#aaffc3"
            }
           else if (d.data.name == "Absent")
            {
              return "#ff9999" 
            }
            if(d.depth==2 && d.data.children[0].name == "Present")
            {
              return "#aaffc3"
            }
            else if(d.depth==2 && d.data.children[0].name == "Absent")
            {
                  return "#ff9999" 
            }
  return color((d.children ? d : d.parent).data.name);
            
      }).style("display", function(d) {
          if (d.depth > 2) {
            return "none"
          } 

          else {
            return "";
          }
        })
        .on("click", click)
     

    text = svg.selectAll(".node")
         .append("text")
            .attr("transform", function(d) { 
                 
     
  if (d.depth== 0) {
            return ""
          } 
                       
            return "rotate(" + computeTextRotation(d) + ")"; 
          
            })
                    .style("text-anchor", function(d) {
          if (d.depth== 0) {
            return "middle"
          } 
        })

            .style("font-size", function(d)
            {
              if(d.depth==0)
              {
                return 8
              }
            })
            .attr("x", function(d) { 
               return y(d.y0); 
            }).attr("dx", "6") // margin
            .attr("dy", ".35em")
            .text(function(d) {

  if(d.depth==0)
                      {
                        var depth0 =d.data.name.toUpperCase()
                        return  depth0
                      }
                return d.data.name 
            })

   .style("display", function(d) {
          if (d.depth > 2) {
            return "none"
          } 
         
            else {
            return "";
          }
        })  
             .on("click", click)
   
  function click(d) {
    
   console.log('d in 394 = >')
      console.log(d)
    //Hide text while Sunburst transitions
    text.transition().attr("opacity", 0);
    
    svg.transition()
        .duration(750)
        .tween("scale", function() {
          var xd = d3.interpolate(x.domain(), [d.x0, d.x1]),
              yd = d3.interpolate(y.domain(), [d.y0, 1]),
              yr = d3.interpolate(y.range(), [d.y0 ? 20 : 0, radius]);
          return function(t) { x.domain(xd(t)); y.domain(yd(t)).range(yr(t)); };
        })
      .selectAll("path")
   .style("display", function(d1) {
    console.log('d1'+ d1)
    
          if (d.depth ==0 && d1.depth > 2) {
            return "none"
          } 
           if (d.depth==1 && d1.depth>3) {
            return "none"
           }
             if(d.depth==2 && d1.depth>3) {
     
              
             return "none" 
           }
           
          else {
            return "";
          }
        })
    .attrTween("d", function(d) { return function() { return arc(d); }; })

      .on("end", function(e, i) {
            // check if the animated element's data e lies within the visible angle span given in d
            if ( e.x0 < d.x1) {
                // get a selection of the associated text element
                var arcText = d3.select(this.parentNode).select("text");


                // fade in the text element and recalculate positions
                arcText.transition().duration(750)
                    .attr("opacity", 1)
                    .attr("class", "visible")
                    .attr("transform", function(d) {
                     
             if(d.depth==0)
                      {
                        
                        return  ""
                      }
       /*              
                  if(d.depth==4 && d.parent.data.name=="Absent")
          {
            return ""
          } 
                       
          */
         
   /*       if(d.depth==4 && d.parent.data.name=="Absent")
          {
                   
            return ""
          }  */
          return "rotate(" + computeTextRotation(e) + ")" })
                    .attr("x", function(d) { return y(d.y0);})
                    .text(function(d) { 
                      if(d.depth==0)
                      {
                        var depth0 = d.data.name.toUpperCase()
                        return depth0
                      }

        if(d.depth == 4 && d.parent.data.name =="Present" )
              {
                             return d.data.intime+ "-"+ d.data.outtime 
              }
              if(d.depth==4 && d.parent.data.name=="Absent")
          {
            return d.data.leavecapture +":" +d.data.reason
          }


      
        return d.data.name
        } 
    )
             .style("display", function(d1) {

              console.log('d1.depth='+d1.depth)
              console.log('d.depth='+d.depth)
            
        
          if ( d.depth==3  && d1.depth==0 ){
             
                      return "none"
              }
                if (d.depth == 0 && d1.depth > 2) {
            return "none"
          } 
        if (d.depth==1 && d1.depth>3) {
            return "none"
           }
             if(d.depth==2 && d1.depth>3) {

              
             return "none"
           }
            if(d.depth==1 && d1.depth==0 )
     {

     return "none"

     }
          else {
            return "";
          }

        })  


            }
  });
  }
  function computeTextRotation(d) {
      
    return (x((d.x0 + d.x1)/2) - Math.PI / 2) / Math.PI * 180;
  }
  function computeTextRotation_center(d) {
      
    return (Math.PI / 100)
  }
  },
  validate_it: function(){
      this.haserror ='false'
      if(document.getElementById("facility_it").value.length< 1){
        document.getElementById("facilityerror_it").style.display ="block"
        this.haserror ='true'
      }
      else
      {
        document.getElementById("facilityerror_it").style.display ="none"
      }

       
    },
      passtree_it: function() {
      this.validate_it()

    this.today_it = moment(this.today_it).format('YYYY-MM-DD')


    this.$http.get('https://app.ellorasystems.com/curie/inventory/getInventory/'+ this.selectedfacility_it + '/' +this.today_it  )

                    .then(function (response) {
                      this.data_tree=response.data
                      this.treegraph_it(this.data_tree)
      


   
   })     

  },

  treegraph_it: function (treeData) {


    var list_tree= document.getElementById("invent")
           if (list_tree.childElementCount > 0) {
            list_tree.removeChild(list_tree.childNodes[0])  
          }

         
  var margin = {top: 20, right: 90, bottom: 30, left: 90},
       width = 1200,
      height = 800;


  var svg = d3.select("#invent").append("svg")
      .attr("width", width + margin.right + margin.left)
      .attr("height", height + margin.top + margin.bottom)
           .attr('viewBox','0 0 '+Math.min(width,height) +' '+Math.min(width,height) )
            .attr('preserveAspectRatio','xMinYMin')
    .append("g")
      .attr("transform", "translate("
            + margin.left + "," + margin.top + ")");


  var i = 0,
      duration = 750,
      root;

  // declares a tree layout and assigns the size
  var treemap = d3.tree().size([height, width]);

  // Assigns parent, children, height, depth
  root = d3.hierarchy(treeData, function(d) { console.log('children='+d.children) ;return d.children; });
  root.x0 = height / 2;
  root.y0 = 0;

  // Collapse after the second level
  root.children.forEach(collapse);

  update(root);

  // Collapse the node and all it's children
  function collapse(d) {
    if(d.children) {
      d._children = d.children
      d._children.forEach(collapse)
      d.children = null
    }
  }



  function update(source) {


    // Assigns the x and y position for the nodes
    var treeData = treemap(root);

    // Compute the new tree layout.
    var nodes = treeData.descendants(),
        links = treeData.descendants().slice(1);

    // Normalize for fixed-depth.
    nodes.forEach(function(d){ d.y = d.depth * 180});

    // ****************** Nodes section ***************************

    // Update the nodes...
    var node = svg.selectAll('g.node')
        .data(nodes, function(d) {return d.id || (d.id = ++i); });

    // Enter any new modes at the parent's previous position.
    var nodeEnter = node.enter().append('g')
        .attr('class', 'node')
        .attr("transform", function(d) {
          return "translate(" + source.y0 + "," + source.x0 + ")";
      })
      .on('click', click);

    // Add Circle for the nodes
    nodeEnter.append('circle')
        .attr('class', 'node')
        .attr("stroke", "rgb(51, 212, 255)")
        .attr('r', 1e-6)
        .style("fill", function(d) {
            return d._children ? "#39BF98" : "#fff";
        });

    // Add labels for the nodes
    nodeEnter.append('text')
        .attr("dy", ".35em")
        .attr("x", function(d) {
            return d.children || d._children ? -9 : -7;
        })
        .attr("y", function(d) { return d.children || d._children ? -25 : -20})
      
        .text(function(d) { 
   if(d.depth==3 && d.data.name=="rol")
    {
      return(d.data.name + ":"+d.data.size )
    }
     if(d.depth==3 && d.data.name=="quantity")
    {

      return( d.data.name + ":" +d.data.size )


    }
     if(d.depth==3 && d.data.name=="sellingPrice")
    {
      

      return(d.data.name + ":"+d.data.size )
    }
          return d.data.name; })
        .style("font-size" ,"12px")

    // UPDATE
    var nodeUpdate = nodeEnter.merge(node);

    // Transition to the proper position for the node
    nodeUpdate.transition()
      .duration(duration)
      .attr("transform", function(d) { 
          return "translate(" + d.y + "," + d.x + ")";
       });

    // Update the node attributes and style
    nodeUpdate.select('circle.node')
      .attr('r', 10)
      .style("stroke", "#33D4FF")
      .style("fill", function(d) {
          return d._children ? "rgb(57, 191, 152)" : "#fff";
      })
      .attr('cursor', 'pointer');
     

    // Remove any exiting nodes
    var nodeExit = node.exit().transition()
        .duration(duration)
        .attr("transform", function(d) {
            return "translate(" + source.y + "," + source.x + ")";
        })
        .remove();

    // On exit reduce the node circles size to 0
    nodeExit.select('circle')
        .style("stroke", "#33D4FF")

      .attr('r', 1e-6);

    // On exit reduce the opacity of text labels
    nodeExit.select('text')
      .style('fill-opacity', 1e-6);

    // ****************** links section ***************************

    // Update the links...
    var link = svg.selectAll('path.link')
        .data(links, function(d) { return d.id; });

    // Enter any new links at the parent's previous position.
    var linkEnter = link.enter().insert('path', "g")
        .attr("class", "link")
                  .attr('cursor', 'pointer')
       .style("fill","none")
         .style("stroke","#ccc")
         .style("stroke-width","1px")

        .attr("d", function(d) {
         return "M" + d.y + "," + d.x
           + "C" + (d.y + d.parent.y) / 2 + "," + d.x
           + " " + (d.y + d.parent.y) / 2 + "," + d.parent.x
           + " " + d.parent.y + "," + d.parent.x;
         });


    // UPDATE
    var linkUpdate = linkEnter.merge(link);

    // Transition back to the parent element position
    linkUpdate.transition()
        .duration(duration)
   .attr("d", function(d) {
         return "M" + d.y + "," + d.x
           + "C" + (d.y + d.parent.y) / 2 + "," + d.x
           + " " + (d.y + d.parent.y) / 2 + "," + d.parent.x
           + " " + d.parent.y + "," + d.parent.x;
         });

    // Remove any exiting links
    var linkExit = link.exit().transition()
        .duration(duration)
        .attr("d", function(d) {
         return "M" + d.y + "," + d.x
           + "C" + (d.y + d.parent.y) / 2 + "," + d.x
           + " " + (d.y + d.parent.y) / 2 + "," + d.parent.x
           + " " + d.parent.y + "," + d.parent.x;
         })

        .remove();

    // Store the old positions for transition.
    nodes.forEach(function(d){
      d.x0 = d.x;
      d.y0 = d.y;
    });


  var layoutRoot = svg
      .append("g")
      d3.select("g")
     /* .call(d3.drag()

          .on("drag", dragmove))*/
         .call(d3.zoom().on("zoom", function () {
          
              svg.attr("transform", d3.event.transform)
          }))

  /*function dragmove() {

      var x = d3.event.x;
      var y = d3.event.y;
      d3.select("g").attr("transform", "translate(" + x + "," + y + ")");
  }
  */


   
         



    // Toggle children on click.
    function click(d) {

      if (d.children) {

          d._children = d.children;
              

          d.children = d._children;
        } else {
         
          d.children = d._children;
          d._children = null;
        }
   if (d.parent) {
      d.parent.children.forEach(function(element) {
        if (d !== element) {
          collapse(element);
        }
      });
    }
      update(d);
    }
    
  }
  },

          }
          
          }
    </script> 
     
     
      
    <style scoped>



     /* 
       @media (max-width: 480px) {
            #res {
                position: relative;
                width: 100%;
          
                height: 100%;
                    

          }
      

      }*/
        @media only screen

      (max-width : 480px) {
            #tab{
           margin-top:20px;

      }
      }
   
      @media only screen and (max-width : 1220px) {

          #invent
          {
            width:280%;
         

          }
          .enddate_ct
          {
            margin-top:20px;
          }
  .date_it
  {
    margin-top:10px;

  }
   #tab
  {

   font-size:6.9px;
   margin-left:-44px;
  }
  #tab1
  {
    margin-top:-50px;
  }
  .faciy
  {
  margin-top:20px;
  }
  .button
  {
  margin-left:-2px;
  margin-top:20px;
  }
      .button_at
      {
  margin-left:-2px;
  margin-top:-8px;
      }
     .employ
      {
        margin-top:15px;
      }
      .year
      {
        margin-top:15px;

      }
      .month
      {
              margin-top:15px;

      }
   .button_as
      {
    margin-left:-2px;
      }

      }
  #res
  {
    margin-top:-80px;
  }
  #res1
  {
    margin-top:40px;
  }
  #sun{
  margin-top:20px;
  margin-left:180px;
  }

     
   
  

    
    td, th { 
      padding: 6px; 
      border: 1px solid #ccc; 
      text-align: left; 
    }
    
    th.des:after {
        content: "\21E9";
      }
      
      th.aes:after {
        content: "\21E7";
      }
    

    @media 
    only screen and (max-width: 760px),
    (min-device-width: 768px) and (max-device-width: 1024px)  {
    
     
      table, thead, tbody, th, td, tr { 
        display: block; 
      }
      
      thead tr { 
        position: absolute;
        top: -9999px;
        left: -9999px;
      }
      
      tr { border: 1px solid #ccc; }
      
      td { 
        border: none;
        border-bottom: 1px solid #eee; 
        position: relative;
        padding-left: 50%; 
      }
      
      td:before { 
        position: absolute;
        top: 6px;
        left: 6px;
        width: 45%; 
        padding-right: 10px; 
        white-space: nowrap;
      }
      
            td:before {
        content: attr(data-th) ": ";
            font-weight: bold;
            width: 6.5em;
            display: inline-block;
      }
    }
    
    @media only screen
    and (min-device-width : 320px)
    and (max-device-width : 480px) {
      body { 
        padding: 0; 
        margin: 0; 
        width: 320px; }
      }
    
    @media only screen and (min-device-width: 768px) and (max-device-width: 1024px) {
      body { 
        width: 495px; 
      }
    }
     @media (max-width: 480px) {
         
          #sun {
             
              width: 150%;
              margin-left:-80px;
              margin-top:20px;

              font-size:21px;
          }
          #res {

                width:290%;
                margin-left:-260px;
          }
                #res1 {
               position: relative;
                width: 280%;
               margin-top:-180px;
                margin-left:-55px;


          }
      }
      .button_at
      {
  margin-top:18px;
      }
     .button_as
      {
  margin-top:15px;
      }

  .pattern {
    background-color: #4FCEA2 ;
     background-image: url("../assets/pattern-min.png");
   background-blend-mode: multiply;
   filter: alpha(opacity=60);
   opacity: 1.0;
   }
   #invent
   {
  height:auto;
   }
  </style>
