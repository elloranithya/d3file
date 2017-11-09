  <template>
       <div class="container-fluid" style="height:auto;margin:0px;padding:0px;">
       <span style="display:none"></span>
       <div class ="pattern" style="height:100px;text-align:center;  font-size:20px;bottom:2px;padding:60px 0 0;
            -moz-box-orient: vertical;
            vertical-align: bottom;width:500%">

            </div>
<span class="col-xs-12 col-sm-12" style ="text-align:center;color:white;  font-size:20px; position:relative; bottom:55px;">Attendance Report
                       </span>
<div class="col-md-12">
<div class="row">
<div class="col-md-3">
<p>Select Facility:</p>
<select   class ="col-md-8"  >
<option>
</option>

</select>
<div class="col-md-12">
 <p id="activefacilityerror" style="display:none; color:#ff5722;"> Kindly select the facility</p>
 </div>
 </div>
<div class="col-md-3">

<p>Select Month:</p>
<select class ="col-md-8"  name="cars">
  <option value="jan">jan </option>
  <option value="feb">feb</option>
  <option value="march">march</option>
  <option value="april">april</option>
    <option value="may">may </option>
  <option value="june">june</option>
  <option value="aug">aug</option>
  <option value="sep">sep</option>
  <option value="oct">oct</option>
  <option value="nov">nov</option>
  <option value="dec">dec</option>
 
</select>

 </div>
<div class ="col-md-3">

<p>Select Year:</p>
<select  class ="col-md-8"  name="cars">
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
</div>
 <div class="col-md-3"  >
<md-button @click.native="passurl()"  class="button" style="border:none; color:white; background-color: #33D4FF;font-size:19px; ">Submit</md-button>
 </div>
 <div class="col-md-12" id="sun"></div>
</div>
</div>
</div>

</template>
<script>
       /*eslint-disable*/
export default {
 data () {
   return {

        data:   {
      
 "name": "anu",
 "children": [
  {
     "name": "Week1",
     "children": [
     {"name": "days1",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
   } ,
    {"name": "days2",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
{"name": "days3",
     "children":[
     {"name":"intime", "size":9,},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},   {"name": "days4",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
   {"name": "days5",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
   {"name": "days6",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
    {"name": "days7",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]

},
     ]
    },
      {
     "name": "Week2",
     "children": [
     {"name": "days1",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
   } ,
    {"name": "days2",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9,  },
{"name":"leavecapture", "size":9},
     ]
},
{"name": "days3",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 
     ]
},   {"name": "days4",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
   {"name": "days5",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
   {"name": "days6",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
    {"name": "days7",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
     ]
    },
     {
     "name": "Week3",
     "children": [
     {"name": "days1",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
   } ,
    {"name": "days2",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
{"name": "days3",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},   {"name": "days4",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
   {"name": "days5",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
   {"name": "days6",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
    {"name": "days7",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
     ]
    },
    {
     "name": "Week4",
     "children": [
     {"name": "days1",
     "children":[
     {"name":"intime", "size":9, "time":23},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
   } ,
    {"name": "days2",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
{"name": "days3",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},   {"name": "days4",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
   {"name": "days5",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
   {"name": "days6",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
    {"name": "days7",
     "children":[
     {"name":"intime", "size":9},
 {"name":"outtime", "size":9},
 {"name":"leave", "size":9},
{"name":"leavecapture", "size":9},
     ]
},
     ]
    }
   ]
}
        }
},
	

mounted:function() {
	
	this.sunbrust(this.data)
},
	methods: {

		
sunbrust: function(data) {



var width = 960,
    height = 700,
    radius = Math.min(width, height) / 2;

var x = d3.scale.linear()
    .range([0, 2 * Math.PI]);

var y = d3.scale.linear()
    .range([0, radius]);

var color = d3.scale.category20c();

var svg = d3.select("body").append("svg")
    .attr("width", width)
    .attr("height", height)
  .append("g")
    .attr("transform", "translate(" + width / 2 + "," + (height / 2 + 10) + ")");

var partition = d3.layout.partition()
    .value(function(d) { return d.size; });

var arc = d3.svg.arc()
    .startAngle(function(d) { return Math.max(0, Math.min(2 * Math.PI, x(d.x))); })
    .endAngle(function(d) { return Math.max(0, Math.min(2 * Math.PI, x(d.x + d.dx))); })
    .innerRadius(function(d) { return Math.max(0, y(d.y)); })
    .outerRadius(function(d) { return Math.max(0, y(d.y + d.dy)); });

  var g = svg.selectAll("g")
      .data(partition.nodes(data))
    .enter().append("g");

  var path = g.append("path")
    .attr("d", arc)
    .style("fill", function(d) { return color((d.children ? d : d.parent).name); })
    .on("click", click);

  var text = g.append("text")
    .attr("transform", function(d) { return "rotate(" + computeTextRotation(d) + ")"; })
    .attr("x", function(d) { return y(d.y); })
    .attr("dx", "6") // margin
    .attr("dy", ".35em") // vertical-align
    .text(function(d) { return d.name; });

  function click(d) {
    // fade out all text elements
    text.transition().attr("opacity", 0);

    path.transition()
      .duration(750)
      .attrTween("d", arcTween(d))
      .each("end", function(e, i) {
          // check if the animated element's data e lies within the visible angle span given in d
          if (e.x >= d.x && e.x < (d.x + d.dx)) {
            // get a selection of the associated text element
            var arcText = d3.select(this.parentNode).select("text");
            // fade in the text element and recalculate positions
            arcText.transition().duration(750)
              .attr("opacity", 1)
              .attr("transform", function() { return "rotate(" + computeTextRotation(e) + ")" })
              .attr("x", function(d) { return y(d.y); });
          }
      });
  }


d3.select(self.frameElement).style("height", height + "px");

// Interpolate the scales!
function arcTween(d) {
  var xd = d3.interpolate(x.domain(), [d.x, d.x + d.dx]),
      yd = d3.interpolate(y.domain(), [d.y, 1]),
      yr = d3.interpolate(y.range(), [d.y ? 20 : 0, radius]);
  return function(d, i) {
    return i
        ? function(t) { return arc(d); }
        : function(t) { x.domain(xd(t)); y.domain(yd(t)).range(yr(t)); return arc(d); };
  };
}

function computeTextRotation(d) {
  return (x(d.x + d.dx / 2) - Math.PI / 2) / Math.PI * 180;
}



		}
	}
}
</script>
<style scoped >
path {
  stroke: black;
    fill-rule: evenodd;
}

</style>
