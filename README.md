<html>
<body>
<p>
  Add links to JSON file using URL and Tags fields.<br>
</p>

<p id="links"></p>

<script>
var jsonsite="https://david-krause.github.io/favorite-links/links.json";
var jsnhttp = new XMLHttpRequest();

jsnhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    var jsnObj = JSON.parse(this.responseText);
    var i, n;
    for(i in jsnObj){n += jsnObj[i].title + " " + i + "<br>"}
    	document.getElementById("links").innerHTML = n;
  }
};
jsnhttp.open("GET", jsonsite,true);
jsnhttp.send();

</script>
</body>
</html>
