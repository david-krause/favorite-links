<html>
<body>
<p>
  Add links to JSON file.
  Change "jsonsite" var in readme.md file to point to your json file.
</p>

<p id="links"></p>

<script>
var jsonsite="https://david-krause.github.io/favorite-links/links.json";
var jsnhttp = new XMLHttpRequest();

jsnhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    var jsnObj = JSON.parse(this.responseText);
    var i, n;
    for(i in jsnObj){n += "<a target=_blank href=" + jsnObj[i].url + ">" + jsnObj[i].title + "</a><br>"}
    	document.getElementById("links").innerHTML = n;
  }
};
jsnhttp.open("GET", jsonsite,true);
jsnhttp.send();

</script>
</body>
</html>
