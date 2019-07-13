<html>
<body>
<p>
  Add links to JSON file using URL and Tags fields.<br>
  This html file will parse and alphbetize the JSON file.
</p>

<p id="links"></p>

<script>
var jsonsite="https://david-krause.github.io/favorite-links/links.json";
var jsndata = new XMLHttpRequest();
jsndata.onreadystatechange = function() {
  if (this.status==200 && this.readyState == 4) {
    var jsnobj = JSON.parse(this.responseText);
    var i, n;
    for (i in jsnobj) {n += jsnobj[i].title}
        document.getElementById("links").innerHTML = n;
    }
};
xmlhttp.open("GET", jsonsite,true);
xmlhttp.send();

</script>

</body>
</html>
