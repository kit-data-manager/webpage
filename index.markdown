---
layout: home
breadcrumbs: /
---

<div id="myBtnContainer">
  <div id="example-select"></div>
  <button id="btn_all" class="btn rounded-lg shadow-lg"> Filter</button>
</div>

<div class="flex flex-wrap -m-3"> 


{% include card.html tags="data repository restful" 
target="base-repo/index.html" 
background="assets/images/disks.jpg"
title="base-repo"
subtitle="a place to be for your data"
content="The base-repo is a generic, general purpose research data repository service offering clear, machine-actionable RESTful interfaces for storing, retrieving and managing research data."
%}

{% include card.html tags="metadata repository restful"
target="metastore/index.html"
background="assets/images/metadata.jpg"
title="MetaStore"
subtitle="more fun with metadata"
content="Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quasi, tempore sapiente eveniet quibusdam ab ea, quaerat placeat numquam aspernatur, accusamus magnam neque."
%}

{% include card.html tags="restful"
target="collection-registry/index.html"
background="assets/images/collections.jpg"
title="Collection Registry"
subtitle="collect, organize, share"
content="Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quasi, tempore sapiente eveniet quibusdam ab ea, quaerat placeat numquam aspernatur, accusamus magnam neque."
%}

{% include card.html tags="ui"
target="metadata-editor/index.html"
background="assets/images/editor.png"
title="Metadata Editor"
subtitle="it's about filling in and out"
content="Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quasi, tempore sapiente eveniet quibusdam ab ea, quaerat placeat numquam aspernatur, accusamus magnam neque."
%}

</div>


<script>

var myOptions = [
  { label: 'Repository', value: 'repository' },
  { label: 'Data', value: 'data' },
  { label: 'Metadata', value: 'metadata' },
  { label: 'RESTful', value: 'restful' },
  { label: 'UI', value: 'ui' }
];

VirtualSelect.init({
  ele: '#example-select',
  options: myOptions,
  multiple: true
});

document.querySelector('#example-select').setValue(['repository', 'data', 'metadata', 'restful', 'ui']);
filterSelection(['repository', 'data', 'metadata', 'restful', 'ui']);

function filterSelection(values) {
  var x, i, j;
x = document.getElementsByClassName("filterDiv");
for (i = 0; i < x.length; i++) {
    w3RemoveClass(x[i], "show");
}

for (i = 0; i < x.length; i++) {
    for(j=0;j<values.length;j++){
        if (x[i].className.indexOf(values[j]) > -1) w3AddClass(x[i], "show");
    }
};
}

function w3AddClass(element, name) {
  var i, arr1, arr2;
  arr1 = element.className.split(" ");
  arr2 = name.split(" ");
  for (i = 0; i < arr2.length; i++) {
    if (arr1.indexOf(arr2[i]) == -1) {element.className += " " + arr2[i];}
  }
}

function w3RemoveClass(element, name) {
  var i, arr1, arr2;
  arr1 = element.className.split(" ");
  arr2 = name.split(" ");
  for (i = 0; i < arr2.length; i++) {
    while (arr1.indexOf(arr2[i]) > -1) {
      arr1.splice(arr1.indexOf(arr2[i]), 1);     
    }
  }
  element.className = arr1.join(" ");
}

var btnContainer = document.getElementById("myBtnContainer");
var btns = btnContainer.getElementsByClassName("btn");

btns[0].addEventListener("click", function(evt){ 
    filterSelection($('#example-select').val());
});

</script>

