---
layout: home breadcrumbs: /
---

<div id="myBtnContainer">
  <button class="btn rounded-lg shadow-lg active" onclick="filterSelection('all')"> Show all</button>
  <button class="btn rounded-lg shadow-lg" onclick="filterSelection('repository')"> Repository</button>
  <button class="btn rounded-lg shadow-lg" onclick="filterSelection('data')"> Data</button>
  <button class="btn rounded-lg shadow-lg" onclick="filterSelection('metadata')"> Metadata</button>
  <button class="btn rounded-lg shadow-lg" onclick="filterSelection('RESTful')"> RESTful</button>
  <button class="btn rounded-lg shadow-lg" onclick="filterSelection('ui')"> UI</button>
</div>

<div class="flex flex-wrap -m-3"> 

{% include card.html title="base-repo"
subtitle="a place to be for your data"
tags="repository data RESTful"
background="assets/images/disks.jpg"
content="Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quasi, tempore sapiente eveniet quibusdam ab ea,
quaerat placeat numquam aspernatur, accusamus magnam neque."
target="base-repo/index.html" %}

{% include card.html title="MetaStore"
subtitle="more fun with metadata"
tags="repository metadata RESTful"
background="assets/images/metadata.jpg"
content="Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quasi, tempore sapiente eveniet quibusdam ab ea,
quaerat placeat numquam aspernatur, accusamus magnam neque."
target="metastore.html" %}

{% include card.html title="Collection Registry"
subtitle="the data squirrel"
tags="metadata RESTful"
background="assets/images/collections.jpg"
content="Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quasi, tempore sapiente eveniet quibusdam ab ea,
quaerat placeat numquam aspernatur, accusamus magnam neque."
target="collection-registry.html" %}

{% include card.html title="Metadata Editor"
subtitle="it's about filling in and out"
tags="ui"
background="assets/images/editor.png"
content="Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quasi, tempore sapiente eveniet quibusdam ab ea,
quaerat placeat numquam aspernatur, accusamus magnam neque.."
target="metadata-editor.html" %}

</div>

<script>
//$.urlParam = function (name) {
 //   let results = new RegExp('[\?&]' + name + '=([^&#]*)')
  //                    .exec(window.location.search);

    //return (results !== null) ? results[1] || 0 : false;
//};

//let params = $.urlParam('filter').split(",");
//for (i = 0; i < params.length; i++) {
 //   filterSelection(params[i]);
//}

filterSelection("all");
function filterSelection(c) {
  let x, i;
  x = document.getElementsByClassName("filterDiv");
  if (c == "all") c = "";
  for (i = 0; i < x.length; i++) {
    w3RemoveClass(x[i], "show");
    if (x[i].className.indexOf(c) > -1) w3AddClass(x[i], "show");
  }
}

function w3AddClass(element, name) {
  let i, arr1, arr2;
  arr1 = element.className.split(" ");
  arr2 = name.split(" ");
  for (i = 0; i < arr2.length; i++) {
    if (arr1.indexOf(arr2[i]) == -1) {element.className += " " + arr2[i];}
  }
}

function w3RemoveClass(element, name) {
  let i, arr1, arr2;
  arr1 = element.className.split(" ");
  arr2 = name.split(" ");
  for (i = 0; i < arr2.length; i++) {
    while (arr1.indexOf(arr2[i]) > -1) {
      arr1.splice(arr1.indexOf(arr2[i]), 1);     
    }
  }
  element.className = arr1.join(" ");
}

// Add active class to the current button (highlight it)
var btnContainer = document.getElementById("myBtnContainer");
var btns = btnContainer.getElementsByClassName("btn");
for (var i = 0; i < btns.length; i++) {
  btns[i].addEventListener("click", function(){
    var current = document.getElementsByClassName("active");
    current[0].className = current[0].className.replace(" active", "");
    this.className += " active";
  });
}
</script>

