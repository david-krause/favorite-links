<html>
<body>
<p>
  Add links to JSON file using URL and Tags fields.<br>
  This html file will parse and alphbetize the JSON file.
</p>

<p id="demo"></p>

<script>
var jsonsite="https://david-krause.github.io/favorite-links/links.json";
var xmlhttp = new XMLHttpRequest();

xmlhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    var myObj = JSON.parse(this.responseText);
    var i, n;
    for(i in myObj){n += myObj[i].title + " " + i + "<br>"}
    	document.getElementById("demo").innerHTML = n;
  }
};
xmlhttp.open("GET", jsonsite,true);
xmlhttp.send();

</script>
</body>
</html>
