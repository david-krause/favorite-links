<html>
<body>

<h2>Favorites</h2>

<p id="links"></p>

<script>
var JSN = '{"URL":"https://github.com}';
var Obj = JSON.parse(JSN);
document.getElementById("links").innerHTML = Obj.URL;
</script>

</body>
</html>
