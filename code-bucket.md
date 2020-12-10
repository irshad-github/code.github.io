# **CODE BUCKET**

### Close pop up when click outside of it

```javascript
if ($(e.target).closest(".container").length === 0) { 
    // rest code here 
} 
```

### To stop document function
```javascript
e.stopPropagation();
```

### Check size and display uploaded file name

```javascript
$("#file-upload").change(function (){
    $.each(this.files,function (index,file) {
        if (file.size > 20971520)
        {
            $("#file-upload").val("");
            alert("File size should not be more 20MB");
            return false;
	 }
    });
    var files = $(this).prop("files");
    var names = $.map(files, function(val) { return val.name });
    $('#feedback').text(names.join(", ")).show();
});
```
### dynamic text change with typewriter effect
```html
<script>
    var entry = "Math Homework Help.,Statistics Homework Help.,Physics Homework Help.,Chemistry Homework Help.,Biology Homework Help.,Engineering Homework Help.,English Homework Help.,Essay Writing Help.,History Homework Help.,Accounting Homework Help.,Economics Homework Help.,Science Homework Help.,Lab Report Help.,Project Report Help.,Get Live Tutor Help.,";
    var _CONTENT = entry.split(",");
</script>
<span id="text" class="line1"></span>
<!-- script -->
<script>
    $(document).ready(function ()
    {
        var t, n = 0,
        a = 0,
        o = document.querySelector("#text");
        function i()
        {
            var e;
            null != o && (e = _CONTENT[n].substring(0, a + 1), o.innerHTML = e, a++, e === _CONTENT[n] && (clearInterval(t), setTimeout(function ()
            {
                t = setInterval(r, 50)
            }, 1e3)))
        }

        function r()
        {
            var e;
            null != o && (e = _CONTENT[n].substring(0, a - 1), o.innerHTML = e, a--, "" === e && (clearInterval(t), n == _CONTENT.length - 1 ? n = 0 : n++, a = 0, setTimeout(function ()
            {
                t = setInterval(i, 50)
            }, 200)))
        }
        t = setInterval(i, 100)
    });
</script>
```
### Custom file validation error
```html
<!--add this at input field for error message oninvalid="this.setCustomValidity('Please Enter valid email') -->

<input type="text" oninvalid="this.setCustomValidity('Please Enter valid email')" oninput="setCustomValidity('')">

<!--add this for remove message while typing oninput="setCustomValidity('')"-->
```

### Responsive flex box
```css
.parent {
  display: flex;
  flex-wrap: wrap;
}

.child {
  flex: 1;
  min-width: 25%;
}

/*
  for laptops,desktop
  boxes divided by 1/4
  
*/

@media (min-width: 650px) and (max-width: 1200px) {
  .child {
    min-width: 33%;
  }
}


/*
  for mobile devices
  boxes divided by 1/2 
*/

@media (max-width: 649px) {
  .child {
    min-width: 50%;
  }
}
```

### Background gradient animation

```css
.body {
  background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
  background-size: 400% 400%;
  animation: gradient 15s linear infinite;
}

@keyframes gradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
```

### DataTable pagination/sorting/ordering

```javascript
var tab=$('.table').DataTable({
            // information
            "info":false,
            // pagination
            "paging": false,
            // table size
            "lengthChange": false,
            // column customisation class wise no sorting
            "aoColumnDefs": [{
            'bSortable': false,
            'aTargets': ['nosort']
        }]
});
```
### AJAX call with multipart/form-data

```javascript
$.ajax({
    url: "{% url 'tutor:tprogress_bar_upload' atutor.assignment_id %}",
    method:"POST",
    cache: false,
    contentType: false,
    processData: false,
    type: 'POST',
    data: new FormData($("form")[0]),
    success:function(data){
        console.log(data);
    }
});
```

### Fontawesome CDN
```html
 <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.6.3/css/all.css">
```

### Change Scroll Bar

```css
::-webkit-scrollbar-thumb {
    border-radius: 10px;
    background-image: -webkit-gradient(linear,left bottom,left top,color-stop(0.44, rgb(72 196 255)),color-stop(0.72, rgb(0 177 255)),color-stop(0.86, rgb(0 160 255)));
}
::-webkit-scrollbar-track {
    -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3);
    background-color: #F5F5F5;
    border-radius: 10px;
}
::-webkit-scrollbar {
    width: 6px;
    background-color: #F5F5F5;
}
```

### Move image in 3D space
```css
{
        will-change: transform;
        transform: perspective(1000px) rotateX(0deg) rotateY(192deg) scale3d(1, 1, 1);
}
```
### FallBack Image using javascript
```html
<img src="foo.jpg" onerror="if (this.src != 'error.jpg') this.src = 'error.jpg';">
```
### set / get / erase cookies
```javascript
function setCookie(name,value,days) {
    var expires = "";
    if (days) {
        var date = new Date();
        date.setTime(date.getTime() + (days*24*60*60*1000));
        expires = "; expires=" + date.toUTCString();
    }
    document.cookie = name + "=" + (value || "")  + expires + "; path=/";
}
function getCookie(name) {
    var nameEQ = name + "=";
    var ca = document.cookie.split(';');
    for(var i=0;i < ca.length;i++) {
        var c = ca[i];
        while (c.charAt(0)==' ') c = c.substring(1,c.length);
        if (c.indexOf(nameEQ) == 0) return c.substring(nameEQ.length,c.length);
    }
    return null;
}
function eraseCookie(name) {   
    document.cookie = name +'=; Path=/; Expires=Thu, 01 Jan 1970 00:00:01 GMT;';
}
```
### Responsive table
```html
<style>
body {
  font-family: "Open Sans", sans-serif;
  line-height: 1.25;
}

table {
  border: 1px solid #ccc;
  border-collapse: collapse;
  margin: 0;
  padding: 0;
  width: 100%;
  table-layout: fixed;
}

table caption {
  font-size: 1.5em;
  margin: .5em 0 .75em;
}

table tr {
  background-color: #f8f8f8;
  border: 1px solid #ddd;
  padding: .35em;
}

table th,
table td {
  padding: .625em;
  text-align: center;
}

table th {
  font-size: .85em;
  letter-spacing: .1em;
  text-transform: uppercase;
}

@media screen and (max-width: 600px) {
  table {
    border: 0;
  }

  table caption {
    font-size: 1.3em;
  }
  
  table thead {
    border: none;
    clip: rect(0 0 0 0);
    height: 1px;
    margin: -1px;
    overflow: hidden;
    padding: 0;
    position: absolute;
    width: 1px;
  }
  
  table tr {
    border-bottom: 3px solid #ddd;
    display: block;
    margin-bottom: .625em;
  }
  
  table td {
    border-bottom: 1px solid #ddd;
    display: block;
    font-size: .8em;
    text-align: right;
  }
  
  table td::before {
    /*
    * aria-label has no advantage, it won't be read inside a table
    content: attr(aria-label);
    */
    content: attr(data-label);
    float: left;
    font-weight: bold;
    text-transform: uppercase;
  }
  
  table td:last-child {
    border-bottom: 0;
  }
}
</style>
<table>
  <caption>Statement Summary</caption>
  <thead>
    <tr>
      <th scope="col">Account</th>
      <th scope="col">Due Date</th>
      <th scope="col">Amount</th>
      <th scope="col">Period</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td data-label="Account">Visa - 3412</td>
      <td data-label="Due Date">04/01/2016</td>
      <td data-label="Amount">$1,190</td>
      <td data-label="Period">03/01/2016 - 03/31/2016</td>
    </tr>
    <tr>
      <td scope="row" data-label="Account">Visa - 6076</td>
      <td data-label="Due Date">03/01/2016</td>
      <td data-label="Amount">$2,443</td>
      <td data-label="Period">02/01/2016 - 02/29/2016</td>
    </tr>
    <tr>
      <td scope="row" data-label="Account">Corporate AMEX</td>
      <td data-label="Due Date">03/01/2016</td>
      <td data-label="Amount">$1,181</td>
      <td data-label="Period">02/01/2016 - 02/29/2016</td>
    </tr>
    <tr>
      <td scope="row" data-label="Acount">Visa - 3412</td>
      <td data-label="Due Date">02/01/2016</td>
      <td data-label="Amount">$842</td>
      <td data-label="Period">01/01/2016 - 01/31/2016</td>
    </tr>
  </tbody>
</table>
```
### Flip clock CSS - JS only
```html
<style>

.countdown {
  display: flex;
  width: 70%;
  justify-content: center;
}
.countdown .bloc-time {
  float: left;
  text-align: center;
}
.countdown .bloc-time:last-child {
  margin-right: 0;
}
.countdown .count-title {
  display: block;
  margin-bottom: 15px;
  font-size: clamp(.7em,2vw,.9em);
  color: $muted;
  text-transform: uppercase;
}
.countdown .figure {
  position: relative;
  float: left;
  height: clamp(27px, 3vw, 74px);
  width: clamp(25px, 3vw, 74px);
  margin-right: 10px;
  background-color: #fff;
  border-radius: 8px;
  -moz-box-shadow: 0 3px 4px 0 rgba(0, 0, 0, 0.2), inset 2px 4px 0 0 rgba(255, 255, 255, 0.08);
  -webkit-box-shadow: 0 3px 4px 0 rgba(0, 0, 0, 0.2), inset 2px 4px 0 0 rgba(255, 255, 255, 0.08);
  box-shadow: 0 3px 4px 0 rgba(0, 0, 0, 0.2), inset 2px 4px 0 0 rgba(255, 255, 255, 0.08);
}
.countdown .figure:last-child {
  margin-right: 0;
}
.countdown .figure > span {
  position: absolute;
  left: 0;
  right: 0;
  margin: auto;
  font-size:clamp(1.2em, 2vw, 3em);
  font-weight: 700;
  color: #de4848;
}
.countdown .figure .top:after, .countdown .figure .bottom-back:after {
  content: "";
  position: absolute;
  z-index: -1;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 100%;
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
}
.countdown .figure .top {
  z-index: 3;
  background-color: #f7f7f7;
  transform-origin: 50% 100%;
  -webkit-transform-origin: 50% 100%;
  -moz-border-radius-topleft: 10px;
  -webkit-border-top-left-radius: 10px;
  border-top-left-radius: 10px;
  -moz-border-radius-topright: 10px;
  -webkit-border-top-right-radius: 10px;
  border-top-right-radius: 10px;
  -moz-transform: perspective(200px);
  -ms-transform: perspective(200px);
  -webkit-transform: perspective(200px);
  transform: perspective(200px);
}
.countdown .figure .bottom {
  z-index: 1;
}
.countdown .figure .bottom:before {
  content: "";
  position: absolute;
  display: block;
  top: 0;
  left: 0;
  width: 100%;
  height: 50%;
  background-color: rgba(0, 0, 0, 0.02);
}
.countdown .figure .bottom-back {
  z-index: 2;
  top: 0;
  height: 50%;
  overflow: hidden;
  background-color: #f7f7f7;
  -moz-border-radius-topleft: 10px;
  -webkit-border-top-left-radius: 10px;
  border-top-left-radius: 10px;
  -moz-border-radius-topright: 10px;
  -webkit-border-top-right-radius: 10px;
  border-top-right-radius: 10px;
}
.countdown .figure .bottom-back span {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  margin: auto;
}
.countdown .figure .top, .countdown .figure .top-back {
  height: 50%;
  overflow: hidden;
  -moz-backface-visibility: hidden;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}
.countdown .figure .top-back {
  z-index: 4;
  bottom: 0;
  background-color: #fff;
  -webkit-transform-origin: 50% 0;
  transform-origin: 50% 0;
  -moz-transform: perspective(200px) rotateX(180deg);
  -ms-transform: perspective(200px) rotateX(180deg);
  -webkit-transform: perspective(200px) rotateX(180deg);
  transform: perspective(200px) rotateX(180deg);
  -moz-border-radius-bottomleft: 10px;
  -webkit-border-bottom-left-radius: 10px;
  border-bottom-left-radius: 10px;
  -moz-border-radius-bottomright: 10px;
  -webkit-border-bottom-right-radius: 10px;
  border-bottom-right-radius: 10px;
}
.countdown .figure .top-back span {
  position: absolute;
  top: -100%;
  left: 0;
  right: 0;
  margin: auto;
}

</style>
 <div class="wrap mb-4">
                <h4 class="text-muted">Deadline in</h4>
                <div class="countdown" id="assignment">
                    <div class="bloc-time days mx-auto d-time" data-init-value="0">
                        <span class="count-title">Days</span>

                        <div class="figure days days-1">
                            <span class="top">0</span>
                            <span class="top-back">
                                 <span>0</span>
                                 </span>
                            <span class="bottom">0</span>
                            <span class="bottom-back">
                                 <span>0</span>
                                </span>
                        </div>

                        <div class="figure hours days-2">
                            <span class="top">0</span>
                            <span class="top-back">
                                     <span>0</span>
                                      </span>
                            <span class="bottom">0</span>
                            <span class="bottom-back">
                                     <span>0</span>
                                    </span>
                        </div>
                    </div>
                    <div class="bloc-time hours mx-auto h-time" data-init-value="0">
                        <span class="count-title">Hours</span>

                        <div class="figure hours hours-1">
                            <span class="top">0</span>
                            <span class="top-back">
                                 <span>0</span>
                                 </span>
                            <span class="bottom">0</span>
                            <span class="bottom-back">
                                 <span>0</span>
                                </span>
                        </div>

                        <div class="figure hours hours-2">
                            <span class="top">0</span>
                            <span class="top-back">
                                     <span>0</span>
                                      </span>
                            <span class="bottom">0</span>
                            <span class="bottom-back">
                                     <span>0</span>
                                    </span>
                        </div>
                    </div>

                    <div class="bloc-time min mx-auto m-time" data-init-value="0">
                        <span class="count-title">Minutes</span>

                        <div class="figure min min-1">
                            <span class="top">0</span>
                            <span class="top-back">
                                <span>0</span>
                            </span>
                            <span class="bottom">0</span>
                            <span class="bottom-back">
                                <span>0</span>
                            </span>
                        </div>

                        <div class="figure min min-2">
                            <span class="top">0</span>
                            <span class="top-back">
                                <span>0</span>
                            </span>
                            <span class="bottom">0</span>
                            <span class="bottom-back">
                                <span>0</span>
                            </span>
                        </div>
                    </div>

                    <div class="bloc-time sec mx-auto s-time " data-init-value="0">
                        <span class="count-title">Seconds</span>

                        <div class="figure sec sec-1">
                            <span class="top">0</span>
                            <span class="top-back">
                                <span>0</span>
                            </span>
                            <span class="bottom">0</span>
                            <span class="bottom-back">
                                <span>0</span>
                            </span>
                        </div>

                        <div class="figure sec sec-2">
                            <span class="top">0</span>
                            <span class="top-back">
                                <span>0</span>
                            </span>
                            <span class="bottom">0</span>
                            <span class="bottom-back">
                                <span>0</span>
                            </span>
                        </div>
                    </div>
                </div>
            </div>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/latest/TweenMax.min.js"></script>
<script>

    // Create Countdown
    var Countdown = {

        // Backbone-like structure
        $el: $('.countdown'),

        // Params
        countdown_interval: null,
        total_seconds     : 0,

        // Initialize the countdown
        init: function() {

            // DOM
            this.$ = {
                days  : this.$el.find('.bloc-time.days .figure'),
                hours  : this.$el.find('.bloc-time.hours .figure'),
                minutes: this.$el.find('.bloc-time.min .figure'),
                seconds: this.$el.find('.bloc-time.sec .figure')
            };

            // Init countdown values
            this.values = {
                days  : this.$.days.parent().attr('data-init-value'),
                hours  : this.$.hours.parent().attr('data-init-value'),
                minutes: this.$.minutes.parent().attr('data-init-value'),
                seconds: this.$.seconds.parent().attr('data-init-value'),
            };
            console.log(this.values.days);
            // Initialize total seconds
            this.total_seconds = this.values.hours * 60 * 60 + (this.values.minutes * 60) + this.values.seconds;

            // Animate countdown to the end
            this.count();
        },

        count: function() {

            var that    = this,
                $days_1 = this.$.days.eq(0),
                $days_2 = this.$.days.eq(1),
                $hour_1 = this.$.hours.eq(0),
                $hour_2 = this.$.hours.eq(1),
                $min_1  = this.$.minutes.eq(0),
                $min_2  = this.$.minutes.eq(1),
                $sec_1  = this.$.seconds.eq(0),
                $sec_2  = this.$.seconds.eq(1);

            this.countdown_interval = setInterval(function() {

                if(that.total_seconds > 0) {

                    --that.values.seconds;

                    if(that.values.minutes >= 0 && that.values.seconds < 0) {

                        that.values.seconds = 59;
                        --that.values.minutes;
                    }

                    if(that.values.hours >= 0 && that.values.minutes < 0) {

                        that.values.minutes = 59;
                        if (this.values.hours > 0)
                        {
                            --that.values.hours;s
                        }
                    }
                    if(that.values.hours < 0 && that.values.days > 0 && that.values.minutes < 0 ) {
                        --that.values.days;
                        console.log("days reduced");
                    }

                    // Update DOM values
                    that.checkHour(that.values.days, $days_1, $days_2);
                    // Hours
                    that.checkHour(that.values.hours, $hour_1, $hour_2);

                    // Minutes
                    that.checkHour(that.values.minutes, $min_1, $min_2);

                    // Seconds
                    that.checkHour(that.values.seconds, $sec_1, $sec_2);

                    --that.total_seconds;
                }
                else {
                    clearInterval(that.countdown_interval);
                }
            }, 1000);
        },

        animateFigure: function($el, value) {

            var that         = this,
                $top         = $el.find('.top'),
                $bottom      = $el.find('.bottom'),
                $back_top    = $el.find('.top-back'),
                $back_bottom = $el.find('.bottom-back');

            // Before we begin, change the back value
            $back_top.find('span').html(value);

            // Also change the back bottom value
            $back_bottom.find('span').html(value);

            // Then animate
            TweenMax.to($top, 0.8, {
                rotationX           : '-180deg',
                transformPerspective: 300,
                ease                : Quart.easeOut,
                onComplete          : function() {

                    $top.html(value);

                    $bottom.html(value);

                    TweenMax.set($top, { rotationX: 0 });
                }
            });

            TweenMax.to($back_top, 0.8, {
                rotationX           : 0,
                transformPerspective: 300,
                ease                : Quart.easeOut,
                clearProps          : 'all'
            });
        },

        checkHour: function(value, $el_1, $el_2) {

            var val_1       = value.toString().charAt(0),
                val_2       = value.toString().charAt(1),
                fig_1_value = $el_1.find('.top').html(),
                fig_2_value = $el_2.find('.top').html();

            if(value >= 10) {

                // Animate only if the figure has changed
                if(fig_1_value !== val_1) this.animateFigure($el_1, val_1);
                if(fig_2_value !== val_2) this.animateFigure($el_2, val_2);
            }
            else {

                // If we are under 10, replace first figure with 0
                if(fig_1_value !== '0') this.animateFigure($el_1, 0);
                if(fig_2_value !== val_1) this.animateFigure($el_2, val_1);
            }
        }
    };

    // Let's go !
    Countdown.init();


    // close sidenav bar
    function closeSideNav() {
        $("#sidebar").toggleClass('close-nav');
        $("#nav-icon").toggleClass('down');
    }

    // #upload funtion was written in base_v7.js
</script>
```
### Responsive Grid
```css
.auto-grid {
  --auto-grid-min-size: 303px;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(var(--auto-grid-min-size), 1fr));
  grid-gap: 1rem;
}
```
### ESLINT Config
```shell script
eslint --ext .js,.vue --ignore-path .gitignore . "--fix"
```
### Open several times multiple file input without losing earlier selected files
```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
<button value="See what's in there" id="seebtn">see</button>
<form id='upload-form' action='' method='post' enctype='multipart/form-data'>

    <input id='myFileInput' class='file-input' type='file' name='file[]' onclick="myFunction(this)" multiple='multiple' />
    
</form>
<div id="displayFileNames"></div>

<script>
  $("#seebtn").click(function(e) {
      $('#displayFileNames').html('');
      var domArray = document.getElementsByClassName('file-input');
      for (var i = 0; i < domArray.length; i++) {
         var files =  domArray[i].files;
       
        for (var j = 0; j < files.length; j++){
        $('#displayFileNames').append(files[j].name + '</br>');
      }
      };
      

      // Send data with AJAX.
    });
 function myFunction(obj) {
  $(obj).hide();
  $("#upload-form").append("<input class='file-input' type='file' onclick='myFunction(this)' name='file[]' multiple='multiple' />");
    }
</script>
```
### vertical scroll effect
```html
<style>
body {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.scrolling-words-container {
  display: flex;
  align-items: center;
  font-size: 2rem;
  font-weight: 600;
}

.scrolling-words-box {
  height: 3rem;
  margin: auto;
  overflow: hidden;
}
.scrolling-words-box ul {
  margin: 0 0.625rem;
  padding: 0;
  animation: scrollUp 4s infinite;
}
.scrolling-words-box ul li {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  height: 3rem;
  list-style: none;
}

@keyframes scrollUp {
  15%, 25% {
    transform: translateY(-20%);
  }
  40%, 50% {
    transform: translateY(-40%);
  }
  65%, 75% {
    transform: translateY(-60%);
  }
  90%, 100% {
    transform: translateY(-80%);
  }
}
</style>
<div class="scrolling-words-container">
  <div class="scrolling-words-box">
    <ul>
      <li style="color: #ea4335">Code</li>
      <li style="color: #4285f4">Build</li>
      <li style="color: #34a853">Create</li>
      <li style="color: #fbbc04">Design</li>
      <li style="color: #ea4335">Code</li>
    </ul>
  </div>
  <span style="color: #5f6368">for everyone</span>
</div>
```
### card tag
```scss
tag {
  display: block;
  padding: 8px 14px;
  position: absolute;
  right: -14px;
  top: 20px;
  background-color: darkblue;
  color: dodgerblue;
  border-top-right-radius: 7px;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.3);

  &::after {
    display: block;
    content: "";
    height: 14px;
    width: 14px;
    position: absolute;
    background-color: dodgerblue;
    right: 0;
    bottom: -14px;
    border-bottom-right-radius: 14px;
  }
}

```
### only numbers validation in input[type="text"]
```html
<input type="text" onkeyup="this.value=this.value.replace(/[^\d]/,'')">
```
### Re-animate element using javascript
```javascript
 function reAnimate() {
        document.querySelectorAll('.shake').forEach((el)=>{
            let newNode = el.cloneNode(true);
            el.parentNode.replaceChild(newNode, el);
        });
    }
```
### password toggle
```html
<style>
.toggle-password{
  float: right;
  position: relative;
  top: -30px;
  right: 11px;
  color: #0077ff;
}
</style>
 <i class="fa fa-fw fa-eye field-icon toggle-password"></i>
<script >
 $(function (){
        $(".toggle-password").click(function() {
            $(this).toggleClass("fa-eye fa-eye-slash");
            var input = $($(this).siblings("input"));
            console.log(input)
            if (input.attr("type") == "password") {
                input.attr("type", "text");
            } else {
                input.attr("type", "password");
            }
        });
    });
</script>
```
### OTP field
```html
 <div class="d-flex digit-input">
                <input type="text" maxlength="1" class="form-control" oninput="this.value = this.value.replace(/[^0-9.]/g, '').replace(/(\..*)\./g, '$1');"  maxLength="1" size="1" min="0" max="9" pattern="[0-9]{1}" autocomplete="off" >
                <input type="text" maxlength="1" class="form-control" oninput="this.value = this.value.replace(/[^0-9.]/g, '').replace(/(\..*)\./g, '$1');"  maxLength="1" size="1" min="0" max="9" pattern="[0-9]{1}" autocomplete="off" >
                <input type="text" maxlength="1" class="form-control" oninput="this.value = this.value.replace(/[^0-9.]/g, '').replace(/(\..*)\./g, '$1');"  maxLength="1" size="1" min="0" max="9" pattern="[0-9]{1}" autocomplete="off" >
                <input type="text" maxlength="1" class="form-control" oninput="this.value = this.value.replace(/[^0-9.]/g, '').replace(/(\..*)\./g, '$1');"  maxLength="1" size="1" min="0" max="9" pattern="[0-9]{1}" autocomplete="off" >
            </div>
<script >
    $(function (){
        $('.digit-input input').on('keyup change', function(e){
            $t = $(this);
            if (e.keyCode === 8 || e.keyCode === 37){
                $t.prev().val('').focus();
            }
            else if($t.val().length > 0) {
                $t.next().val('').focus();
            }
        });
    });
</script>
```
### Truncate string using css
```html
<style>
.truncate{
display: block;
max-width: 220px;
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
}
</style>
<p class="truncate">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Laboriosam, recusandae.</p>
```
### A numeric keyboard in input[type='text']
```html
<input type="text" inputmode="numeric" pattern="[0-9]*">
```
