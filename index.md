<html>

  <head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>jQuery UI Datepicker - Default functionality</title>
  <link rel="stylesheet" href="//code.jquery.com/ui/1.12.1/themes/base/jquery-ui.css">
  <link rel="stylesheet" href="/resources/demos/style.css">
  <script src="https://code.jquery.com/jquery-1.12.4.js"></script>
  <script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>
  <script>
  $( function() {
    $( "#datepicker" ).datepicker({ dateFormat: 'dd-mm-yy' });
  } );
  </script>
  <style> 

.center {
  text-align:center;
  color:  #3F3F58;
  margin: auto;
  width: 30%;
  border: 2px;
  border-style: solid;
  border-color: #3F3F58; 
  border-radius: 20px; 
  padding: 10px;
}
.nest {
  text-align:left;
  margin: auto;
  width: 80%;
  border: 3px;
  padding: 10px;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 15px;
}
#channel{
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  box-sizing: border-box;
  border: none;
  border-radius: 4px;
  }
#content_type{
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  box-sizing: border-box;
  border: none;
  border-radius: 4px;
  }
#media_type{
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  box-sizing: border-box;
  border: none;
  border-radius: 4px;
  }
 #category{
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  box-sizing: border-box;
  border: none;
  border-radius: 4px;
  }
select {
  width: 100%;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  background-color: #f1f1f1;
}
input[type=text] {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  box-sizing: border-box;
  border: 3px solid #ccc;
  -webkit-transition: 0.5s;
  transition: 0.5s;
  outline: none;
  border-radius: 4px;
}
input[type=text]:focus {
  border: 3px solid #555;
  border-radius: 4px;
}
.button {
  width: 100%;
  background-color: #f1f1f1;
  border: #ffffff;
  border-radius: 4px;
  color: black;
  padding: 16px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  transition-duration: 0.4s;
  cursor: pointer;
}
.button:hover {
  width: 100%;
  background-color: #008CBA;
  color: white;
}
</style>
  </head>
  <body>
<div class="center">
<br>
<img src="https://mmi-analytics.github.io/Beta/lighthouse.png" alt="Girl in a jacket">
<div class="nest"> 
<br>
<span style = "font-size: 18px">URL BUILDER</span>
<br>
<br>
<span>Use this URL builder to generate a trackable link to use on social media channels. Traffic to these links will be surfaced in Google Analytics and in your Lighthouse dashboard.</span>
<br>
<br>
<br>
<label for="URL">Enter URL</label>
<br>
<input type="text" id="URL" name="URL" value="https://">
<br>
<p>Publish Date<input type="text" id="datepicker"></p>
<label for="channel">Select Social Channel</label>
<br>
  <select name="channel_select" id="channel">
    <option value=""></option>
  <option value="?utm_source=facebook.com">Facebook</option>
  <option value="?utm_source=l.instagram.com">Instagram</option>
  <option value="?utm_source=twitter.com">Twitter</option>
  <option value="?utm_source=linkedin.com">LinkedIn</option>
</select>
<br>
<br>
<label for="type">Select Media Type</label>
<br>
  <select name="media_type_select" id="media_type">
  <option value=""></option>
  <option value="&utm_medium=social">Organic</option>
  <option value="&utm_medium=paid_social">Paid</option>
</select>
<br>
<br>
<label for="type">Select Content Type</label>
<br>
  <select name="content_type_select" id="content_type">
  <option value=""></option>
  <option value="&social_content_type=Broad%20Reach">Broad Reach</option>
  <option value="&social_content_type=Informative">Informative</option>
  <option value="&social_content_type=Action%20Driver">Action Driver</option>
  <option value="&social_content_type=Engagement">Engagement</option>
  <option value="&social_content_type=Core">Core</option>
</select>
<br>
<br>
<label for="fname">Please enter an identifiable name for your campaign or post, i.e. "Ethiopia appeal video" or "Mother's day launch post".</label>
<br>
<input type="text" id="campaign_name" name="campaign_name" placeholder="Campaign or Post name">
<br>
<br>
<label for="fname">Generated Tracking Link</label>
<br>
<input type="text" id="output" name="output">
<br>
<br>
<button class="button" id="generate">Generate Tracking Link</button>
<button class="button" id="copy">Copy To Clipboard</button>
<button class="button" id="clear">Clear All</button>
</div>
<br>

</div>
<script>

document.getElementById("generate").addEventListener("click",linkBuild);
document.getElementById("copy").addEventListener("click",copyFunction);
document.getElementById("clear").addEventListener("click",clearFunction);

function linkBuild() {
var URL = document.getElementById("URL").value
var channel = document.getElementById("channel").value
var media_type = document.getElementById("media_type").value
var content_type = document.getElementById("content_type").value
var campaign_name = document.getElementById("campaign_name").value
var campaign_name_replaced = campaign_name.split(' ').join('%20');
var campaign_name_lowercase = campaign_name_replaced.toLowerCase();
var campaign = campaign_name_lowercase.charAt(0).toUpperCase() + campaign_name_lowercase.slice(1);
var publish_date= document.getElementById("datepicker").value
var publish_date_cleaned = publish_date.split('/').join('-');

document.getElementById("output").value =URL+channel+media_type+"&utm_campaign="+campaign+"&social_publish_date="+publish_date_cleaned+content_type;
document.getElementById("output").style.color = "green";
document.getElementById("generate").innerHTML = "Generate Again";
}

function copyFunction() {
  /* Get the text field */
  var copyText = document.getElementById("output");

  /* Select the text field */
  copyText.select();
  copyText.setSelectionRange(0, 99999); /* For mobile devices */

  /* Copy the text inside the text field */
  document.execCommand("copy");

  /* Alert the copied text */
  alert("Copied to Clipboard");
}

function clearFunction() {
  document.getElementById("output").value = "";
  document.getElementById("URL").value = "https://";
  document.getElementById("content_type").value = "";
  document.getElementById("media_type").value = "";
  document.getElementById("campaign_name").value = "";
  document.getElementById("campaign_name").placeholder = "Please enter a name for you campaign or post";
  document.getElementById("datepicker").value ="";
}
</script>

  </body>
</html>
